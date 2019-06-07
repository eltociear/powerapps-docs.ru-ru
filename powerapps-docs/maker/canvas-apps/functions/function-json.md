---
title: Функция JSON | Документация Майкрософт
description: Справочные сведения, включая описание синтаксиса, функции JSON в PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/02/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 74e10a5b073e16ba9f35139441c94e9911446a0f
ms.sourcegitcommit: 2084789802fc5134dbeb888e759cced46019a017
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66736406"
---
# <a name="json-function-in-powerapps"></a>Функции JSON в PowerApps

Создает строку текста JSON для таблицы, записи или значение.

## <a name="description"></a>Описание

**JSON** функция возвращает представление JavaScript Object Notation (JSON) структуру данных в виде текста, чтобы он подходит для сохранения или передачи по сети. [ECMA-404](http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf) и [IETF RFC 8259](https://tools.ietf.org/html/rfc8259) описание формата, который широко используется JavaScript и других языках программирования.

Поддержка приложений на основе холста [типы данных](data-types.md) , в таблице ниже перечислены с подробными сведениями об их текстовое представление:

| Тип данных | Описание | Пример результата |
|-----------|-------------|---------|
| **Логическое значение** | *значение true,* или *false*. | `true` |
| **Цвет** | Строка, содержащая из 8 цифр шестнадцатеричное представление для цвета. Это представление имеет формат #*rrggbbaa*, где *rr* является красного компонента *gg* имеет зеленый цвет, *bb* — синий и *aa* является альфа-канала. Для альфа-канала **00** является полностью прозрачным, и **ff** — полностью непрозрачный. Можно передать строку, чтобы [ **ColorValue** ](function-colors.md) функции.  | `"#102030ff"` |
| **Валюта** | Номер соответствующего десятичного разделителя для языка пользователя. Экспоненциальное представление чисел используется при необходимости. | `1.345` |
| **Дата** | Строка, содержащая дату в формате ISO 8601 **гггг мм дд** формат. | `"2019-03-31"` |
| **Даты и времени** | Строка, которая содержит файл ISO 8601 даты и времени. Даты и времени значения, в формате UTC, указывает конечный «Z».  | `"2019-03-31T22:32:06.822Z"`  |
| **ИДЕНТИФИКАТОР GUID** | Строка, содержащая значение идентификатора GUID. Буквы нижнего регистра. | `"751b58ac-380e-4a04-a925-9f375995cc40"`
| **Изображения, мультимедиа** | Если **IncludeBinaryData** задан, файлы мультимедиа, кодируются в строке. Веб-ссылки, которые используют http: или https: Схема URL-адреса не изменяются. Ссылки на двоичные данные в памяти, кодируются с помощью [«данных:*mimetype*; base64,...»](https://en.wikipedia.org/wiki/Data_URI_scheme) формат. В памяти данные включают в себя образы, включающие пользователей с помощью [ **камеры** ](../controls/control-camera.md) управления и всех остальных ссылок с appres: и BLOB-объектов: Схемы URL-адресов.| `"data:image/jpeg;base64,/9j/4AA..."` |
| **номер** | Номер соответствующего десятичного разделителя для языка пользователя. Экспоненциальное представление чисел используется при необходимости. | `1.345` |
| **Параметр&nbsp;значение** | Задать числовое значение параметра, не метку, которая используется для отображения. Численное значение используется в том случае, так как он является независимой от языка.  | `1001` |
| **время** | Строка, содержащая ISO 8601 *чч:мм:сс.мс* формат.  | `"23:12:49.000"` |
| **Запись** | Разделенный запятыми список, между **{** и **}** , полей и их значения. Эти обозначения похоже, для записей в приложениях на основе холста, но имя всегда выполняется между двойные кавычки. Этот формат не поддерживает записи, которые основаны на связях многие к одному.  | `{ "First Name": "Fred", "Age": 21 }` |
| **Таблицы** | Разделенный запятыми список, между **[** и **]** , записей. Этот формат не поддерживает таблицы, основанные на отношениях один ко многим.  | `[ { "First Name": "Fred", "Age": 21 }, { "First Name": "Jean", "Age": 20 } ]` |
| **Два&nbsp;параметр** | Логическое значение два параметра, *true* или *false*, не метка, которая используется для отображения. Логическое значение, которое используется в том случае, поскольку он является независимой от языка. | `false` |
| **Гиперссылку, текст** | Строка в двойных кавычках. Функция экранирует embedded двойные кавычки обратную косую черту, заменяет символы новой строки «\n» и другие стандартные замены JavaScript. | `"This is a string."` |

Укажите необязательное *формат* аргументом, задающим, как для чтения результат — и как неподдерживаемые и двоичные типы данных обрабатываются. По умолчанию выходные данные — максимально без ненужные пробелы или символы новой строки компактным и неподдерживаемые типы данных и двоичных данных не допускаются. Можно объединить несколько форматов при указании **&** оператор.

| Перечисление JSONFormat | Описание |
|-----------------|-------------|
| **Compact** | Значение по умолчанию.  Результатом является компактным максимально без добавлены пробелы или символы новой строки. |
| **IndentFour** | Для повышения удобочитаемости, результат содержит символ новой строки для каждого столбца и уровня вложенности и использует четыре пробелы для каждого уровня отступа. |
| **IncludeBinaryData** | Результат включает в себя столбцы изображений, видео и аудио клипа. Этот формат может значительно увеличить размер результатов и привести к снижению производительности приложения. |
| **IgnoreBinaryData** | Результат не включает столбцы изображений, видео или аудио клипа. Если не указать **IncludeBinaryData** , ни **IgnoreBinaryData**, функция выводит сообщение об ошибке при обнаружении двоичных данных. |
| **IgnoreUnsupportedTypes** | Неподдерживаемые типы данных допускаются, но они не войдут результат. По умолчанию неподдерживаемые типы данных создают ошибку. |

Используйте [ **ShowColumns** и **DropColumns** ](function-table-shaping.md) функции для управления отображаемыми данными, то результат включает и удалите неподдерживаемые типы данных.

Так как **JSON** может быть памяти и вычислений с большим объемом, его можно использовать только в функции [поведение функции](../working-with-formulas-in-depth.md). Можно записать в результате **JSON** в [переменной](../working-with-variables.md), который затем можно использовать в потоке данных.

Если столбец содержит отображаемое имя и логическое имя, результат содержит логическое имя. Отображаемые имена отражают язык приложения пользователем и, следовательно, подходят для передачи данных в общую службу.

## <a name="syntax"></a>Синтаксис

**JSON**( *DataStructure* [, *формат* ])

* *DataStructure* — обязательный. Структура данных, преобразуемый в JSON.  Таблицы, записи и примитивные значения поддерживаются, произвольно вложенными.
* *Формат* — необязательный.  **JSONFormat** значение перечисления. Значение по умолчанию — **Compact**, который не добавляет новые строки или пробелы и блокирует двоичные данные и неподдерживаемые столбцы.

## <a name="examples"></a>Примеры

### <a name="hierarchical-data"></a>Иерархические данные

1. Вставить [ **кнопку** ](../controls/control-button.md) и задать его **OnSelect** следующую формулу.

    ```powerapps-dot
    ClearCollect( CityPopulations,
        { City: "London",    Country: "United Kingdom", Population: 8615000 },
        { City: "Berlin",    Country: "Germany",        Population: 3562000 },
        { City: "Madrid",    Country: "Spain",          Population: 3165000 },
        { City: "Hamburg",   Country: "Germany",        Population: 1760000 },
        { City: "Barcelona", Country: "Spain",          Population: 1602000 },
        { City: "Munich",    Country: "Germany",        Population: 1494000 }
    );
    ClearCollect( CitiesByCountry, GroupBy( CityPopulations, "Country", "Cities" ) )
    ```

1. Нажмите кнопку, удерживая нажатой клавишу Alt.

    **CitiesByCountry** коллекция создается со следующей структурой данных, который можно отобразить, выбрав **коллекций** на **файл** меню и выбрав имя Коллекция.

    > [!div class="mx-imgBorder"]
    > ![CitiesByCountry коллекции](media/function-json/cities-grouped.png)

    Вы также можете отобразить эту коллекцию, выбрав **файл** > **параметры приложения** > **Дополнительные параметры**  >   **Включить строку представление результатов формул**, выбрав имя коллекции в строке формул, а затем выбрав стрелку вниз рядом с именем коллекции в строке формул.

    > [!div class="mx-imgBorder"]
    > ![Коллекции в представление результатов в строке формул](media/function-json/cities-grouped-resultview.png)

1. Вставьте еще одну кнопку и задайте его **OnSelect** следующую формулу:

    ```powerapps-dot
    Set( CitiesByCountryJSON, JSON( CitiesByCountry ) )
    ```

    Эта формула задает глобальную переменную **CitiesByCountryJSON** представление JSON для **CitiesByCountry**.

1. Нажмите кнопку, удерживая нажатой клавишу Alt.

1. Вставить [ **метка** ](../controls/control-text-box.md) и задать его **текст** значение этой переменной.

    ```powerapps-dot
    CitiesByCountryJSON
    ```

    Метка отображается результат, все в одной строке без пробелов, подходящий для передачи по сети:

    ```json
    [{"Cities":[{"City":"London","Population":8615000}],"Country":"United Kingdom"},{"Cities":[{"City":"Berlin","Population":3562000},{"City":"Hamburg","Population":1760000},{"City":"Munich","Population":1494000}],"Country":"Germany"},{"Cities":[{"City":"Madrid","Population":3165000},{"City":"Barcelona","Population":1602000}],"Country":"Spain"}]
    ```

1. Измените формулу второй кнопки, чтобы сделать выходные данные более удобочитаемым.

    ```powerapps-dot
    Set( CitiesByCountryJSON, JSON(CitiesByCountry, JSONFormat.IndentFour ))
    ```

1. Выберите второй кнопки, удерживая нажатой клавишу Alt.

    В метке отображаются более удобном для чтения результат.

    ```json
    [
        {
            "Cities": [
                {
                    "City": "London",
                    "Population": 8615000
                }
            ],
            "Country": "United Kingdom"
        },
        {
            "Cities": [
                {
                    "City": "Berlin",
                    "Population": 3562000
                },
                {
                    "City": "Hamburg",
                    "Population": 1760000
                },
                {
                    "City": "Munich",
                    "Population": 1494000
                }
            ],
            "Country": "Germany"
        },
        {
            "Cities": [
                {
                    "City": "Madrid",
                    "Population": 3165000
                },
                {
                    "City": "Barcelona",
                    "Population": 1602000
                }
            ],
            "Country": "Spain"
        }
    ]
    ```

### <a name="images-and-media-in-base64"></a>Изображения и мультимедиа в base64

1. Добавить [ **изображение** ](../controls/control-image.md) элемента управления.

    Этот элемент управления обеспечивает **SampleImage** с ним.

1. Добавить [ **кнопку** ](../controls/control-button.md) и задать его **OnSelect** следующую формулу.

    ```powerapps-dot
    Set( ImageJSON, JSON( SampleImage, JSONFormat.IncludeBinaryData ) )
    ```

1. Нажмите кнопку, удерживая нажатой клавишу Alt.

1. Добавьте метку и задайте его **текст** значение этой переменной.

    ```powerapps-dot
    ImageJSON
    ```

1. Размер элемента управления и уменьшить размер шрифта, необходимыми для показана большая часть результата.

    В метке текстовая строка, **JSON** функция захвата.

    ```json
    "data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4NCjxzdmcgdmVyc2lvbj0iMS4xIg0KCSB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIiB4bWxuczphPSJodHRwOi8vbnMuYWRvYmUuY29tL0Fkb2JlU1ZHVmlld2VyRXh0ZW5zaW9ucy8zLjAvIg0KCSB4PSIwcHgiIHk9IjBweCIgd2lkdGg9IjI3MHB4IiBoZWlnaHQ9IjI3MHB4IiBlbmFibGUtYmFja2dyb3VuZD0ibmV3IDAgMCAyNzAgMjcwIiB4bWw6c3BhY2U9InByZXNlcnZlIj4NCgk8ZyBjbGFzcz0ic3QwIj4NCgkJPHJlY3QgeT0iMC43IiBmaWxsPSIjRTlFOUU5IiB3aWR0aD0iMjY5IiBoZWlnaHQ9IjI2OS4zIi8+DQoJCTxwb2x5Z29uIGZpbGw9IiNDQkNCQ0EiIHBvaW50cz0iMjc3LjksMTg3LjEgMjQ1LDE0My40IDE4OC42LDIwMi44IDc1LDgwLjUgLTQuMSwxNjUuMyAtNC4xLDI3MiAyNzcuOSwyNzIiLz4NCgkJPGVsbGlwc2UgZmlsbD0iI0NCQ0JDQSIgY3g9IjIwMi40IiBjeT0iODQuMSIgcng9IjI0LjQiIHJ5PSIyNC4zIi8+DQoJPC9nPg0KPC9zdmc+"
    ```
