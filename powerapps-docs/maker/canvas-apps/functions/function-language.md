---
title: "Функция Language | Документация Майкрософт"
description: "Справочные сведения о функции Language в PowerApps, в том числе описание синтаксиса и примеры"
services: 
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/16/2016
ms.author: gregli
ms.openlocfilehash: 35f6b462a57a29e6989d6a635425c981b705eaaf
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2018
---
# <a name="language-function-in-powerapps"></a>Функция Language в PowerApps
Эта функция возвращает тег языка текущего пользователя.

## <a name="description"></a>Описание
Функция **Language** возвращает язык, скрипт и регион текущего пользователя в качестве тега языка.

Используйте сведения о языке для настройки приложения в разных языковых стандартах.  Например, если вы создаете приложение, которое будет использоваться в Италии и Франции, функцию **Language** можно задать таким образом, чтобы для пользователей в этих регионах автоматически отображались строки на итальянском и французском языке. 

### <a name="language-tags"></a>Теги языка
*Тег языка* может быть в одном из трех форматов:

| Возвращаемое значение | Описание |
| --- | --- |
| **"*lg&#8209;RE*"** |*lg* — это двухсимвольное сокращенное название языка, а *RE* — региона.  Это самый распространенный тип возвращаемого значения.  Например, для Великобритании возвращается "en-GB". |
| **"*lg*"** |*lg* — это двухсимвольное сокращенное название языка.  Этот формат используется, когда PowerApps содержит сведения о языке, но не об определенном регионе. |
| **"*lg&#8209;scrp&#8209;RE*"** |*lg* — это двухсимвольное сокращенное название языка, *scrp* — сокращенное название скрипта, состоящее из четырех символов, а *RE* — двухсимвольное сокращение названия региона. |

PowerApps использует формат [тега языка IETF BCP-47](https://tools.ietf.org/html/bcp47).  

Чтобы увидеть список поддерживаемых тегов языка, введите в строке формул или в расширенном представлении команду **Value( "1", )** и изучите список языковых обозначений, которые будут предложены в качестве значений для второго аргумента.  

Функции **[Text](function-text.md)** и **[Value](function-value.md)** также используют теги языка.  Используйте эти функции для преобразования содержимого в текстовые строки и наоборот в повсеместно известном формате.  При передаче тега языка этим функциям, когда регион ни на что не влияет, можно использовать только языковую часть тега.

## <a name="syntax"></a>Синтаксис
**Language**()

## <a name="examples"></a>Примеры
### <a name="users-locale"></a>Языковой стандарт пользователя
Предполагается, что основная операционная система или браузер используют для расположения языковой стандарт по умолчанию.

| Формула | Расположение | Возвращаемое значение |
| --- | --- | --- |
| **Language()** |Лиссабон, Португалия |"pt-PT" |
| **Language()** |Рио-де-Жанейро, Бразилия |"pt-BR" |
| **Language()** |Атланта, США |"en-US" |
| **Language()** |Манчестер, Соединенное Королевство |"en-GB" |
| **Language()** |Париж, Франция |"fr-FR" |
| **Language()** |Розо, Доминика |"en" |
| **Language()** |Белград, Сербия |"sr-cyrl-RS" или "sr-latn-RS" в зависимости от системных параметров пользователя |

### <a name="localization-table"></a>Таблица локализации
Простой подход к локализации — создать электронную таблицу Excel, которая сопоставляет автора, определяемого **TextID**, с переведенным текстом для языка пользователя.  Несмотря на то что вы можете использовать коллекцию или любой другой источник данных для этой таблицы, мы выбрали Excel, так как в этом формате переводчики могут легко редактировать текст и управлять им вне приложения.

1. Создайте следующую таблицу в Excel: 
   
    ![](media/function-language/loc-table.png)
   
    Запись с *пустым значением* в столбце **Language** будет использоваться по умолчанию, если для данного языка отсутствует определенная текстовая строка. Эта запись должна отображаться после всех других записей для данного **TextID**.
   
    В этой статье мы рассматриваем только язык, а не регион.  Если бы регион имел значение, мы бы добавили полное значение тега языка в приведенную выше таблицу. 
2. Чтобы сделать это в соответствующей таблице Excel, на ленте **Вставка** выберите команду **Таблица**.  По умолчанию таблица получит имя **Table1**, но его можно изменить на любое другое с помощью ленты **Работа с таблицами/Конструктор** и текстового поля **Имя таблицы:** в левой области.
3. Сохраните файл Excel в локальной файловой системе.   
4. В PowerApps на панели справа откройте вкладку **Источники данных**, а затем щелкните **Добавить источник данных**.
5. Выберите **Добавить статические данные для приложения**, укажите сохраненный файл Excel и щелкните **Открыть**.
6. Выберите созданную таблицу, а затем щелкните **Подключиться**.

В приложении вместо текста **Hello**, который использовался ранее, вставьте следующую формулу:

* **LookUp( Table1, TextID = "Hello" && (LanguageTag = Left( Language(), 2 ) || IsBlank( LanguageTag ))).LocalizedText**  

Эта формула выполнит поиск соответствующего значения **LocalizedText** для языка пользователя. Если его не удастся обнаружить, будет возвращена *пустая строка* по умолчанию. 

Имейте в виду, что длина строк, переведенных на другие языки, может существенно отличаться по сравнению с исходным языком.  Во многих случаях метки и другие элементы, отображающие строки в пользовательском интерфейсе, могут оказаться шире после локализации.

### <a name="translation-service"></a>Служба перевода
Вы можете перевести текст по запросу с помощью службы перевода, такой как Microsoft Translator.  

1. В PowerApps на панели справа откройте вкладку **Источники данных**, а затем щелкните **Добавить источник данных**.
2. Щелкните **Microsoft Translator**.

В приложении вместо текста **Hello**, который использовался ранее, вставьте следующую формулу:

* **MicrosoftTranslator.Translate( "Hello", Language() )**

Служба Microsoft Translator использует те же теги языка, которые возвращаются функцией **Language**.

Этот подход имеет некоторые недостатки по сравнению с предыдущим примером, в котором использовалась предварительно переведенная таблица текстовых строк.

* Процесс перевода займет некоторое время в связи с обращением к службе через сеть.  Таким образом, вы сможете увидеть переведенный текст в приложении только через некоторое время. 
* Перевод будет машинным, не лучшего качества и не лучшим вариантом перевода для вашего приложения.
