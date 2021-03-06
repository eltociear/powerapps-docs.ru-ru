---
title: Функция Text | Документация Майкрософт
description: Справочные сведения, включая синтаксис и примеры, для функции Text в Power Apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/14/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: cc27232ea4a6c153b57ab5ce5f94a49f96ef5996
ms.sourcegitcommit: 7d3caf698d367a56af9e16c43af8005adb9f87cd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987208"
ms.PowerAppsDecimalTransform: true
---
# <a name="text-function-in-power-apps"></a>Текстовая функция в Power Apps
Преобразует любое значение и форматирует число или значение даты и времени в строку текста.

## <a name="description"></a>Описание
Функция **Text** форматирует число или значение даты и времени на основе аргументов следующих типов.

* Стандартный формат даты и времени, который указывается с помощью перечисления **DateTimeFormat**. Для дат и времени этот подход предпочтителен, так как он автоматически корректируется на язык и регион каждого пользователя.
* Настраиваемый формат, который состоит из строки заполнителей, определяющих, например,, показывать ли числа десятичные разделители, а даты Показывать полное название месяца, месяц в виде аббревиатуры или месяц в виде числа. Power Apps поддерживает подмножество заполнителей, которые делает Microsoft Excel. В этой строке заполнитель языка определяет язык, на котором следует интерпретировать другие заполнители. Если пользовательский формат содержит точку, например, заполнитель языкового формата указывает, является ли точка десятичным разделителем (ja-JP) или разделителями тысяч (ES-ES).

Подробнее см. статью о [работе с датами и временем](../show-text-dates-times.md).

Функция **Text** также может преобразовать любой тип данных в текстовое представление, используя формат по умолчанию. Используйте его для передачи нетекстовых значений в текстовые функции, такие как [**Len**](function-len.md), [**right**](function-left-mid-right.md)и [**Match**](function-ismatch.md).

### <a name="predefined-datetime-formats"></a><a name="predefined-datetime-formats"></a> Предопределенные форматы даты и времени

В этих примерах используется дата и время, вторник, 7 апреля, 2020 8:26:59.180 PM в часах часового пояса UTC-7.
 
| Перечисление DateTimeFormat | Описание | Примеры (с использованием **en-US**) |
| --- | --- | --- |
| **лонгдате** |Год из четырех цифр, название месяца, день месяца и день недели. Названия месяца и дня недели не сокращаются. | "Вторник, 7 апреля, 2020" |
| **лонгдатетиме** |Год с четырьмя цифрами, название месяца, день месяца и день недели, плюс час (12-часовой формат), минуты, секунды и обозначение AM/PM. Названия месяца и дня недели не сокращаются. | "Вторник, 7 апреля, 2020 8:26:59 PM" |
| **LongDateTime24** |Год с четырьмя цифрами, месяц, день месяца и день недели, плюс час (24-часовой формат), минуты и секунды. Названия месяца и дня недели не сокращаются. | "Вторник, 7 апреля, 2020 20:26:59" |
| **Давнего** |Часы (в 12-часовом формате), минуты, секунды и обозначение AM/PM.  | "8:26:59 PM" |
| **LongTime24** |Часы (в 24-часовом формате), минуты и секунды.  | "20:26:59" | 
| **шортдате** |Год из четырех цифр с числовым месяцем и днем месяца. | "4/7/2020" | 
| **шортдатетиме** |Год из четырех цифр с числовым месяцем и днем месяца, плюс час (12-часовой формат), минуты и обозначение AM/PM. | "4/7/2020 8:26 PM" |
| **ShortDateTime24** |Год из четырех цифр с числовым месяцем и днем месяца, плюс час (24-часовой формат) и минуты. | "4/7/2020 20:26" |
| **шорттиме** |Час (12-часовое время), минуты и обозначение AM/PM.   | "8:26 PM" |
| **ShortTime24** |Час (24-часовое время) и минуты.   | "20:26" |
| **ФОРМАТА** |Значение даты и времени преобразуется в формат UTC на основе часового пояса для текущего пользователя и форматируется в соответствии со стандартом ISO 8601. | "2020-04-08T03:26:59.180 Z" |

### <a name="number-placeholders"></a>Заполнители для чисел

| Заместитель | Описание |
| --- | --- |
| **0** (*ноль*) |Отображает незначащие нули, если число имеет меньше разрядов, чем количество нулей в строке форматирования. Например, формат **#.00** позволяет отобразить значение **8,9** как **8,90**. |
| **#** |Работает так же, как **0** (ноль). Но в этом случае функция **Text** не возвращает дополнительные нули, если число имеет слева или справа от десятичного разделителя меньше цифр, чем количество символов # в строке форматирования. Например, число **8,9** при использовании формата **#.##** будет отображаться как **8,9**. |
| **.** (*точка*) |Отображает символ десятичного разделителя. Зависит от языка пользовательского формата; Дополнительные сведения см. в разделе [глобальные приложения](#global-apps) . |
| **,** (*запятая*) |Отображает символ разделителя разрядов, обычно отделяющий значения тысяч. Функция **Text** разделяет число запятыми, если в строке форматирования есть запятая между символами номера ( **#** ) или нулями. Зависит от языка пользовательского формата; Дополнительные сведения см. в разделе [глобальные приложения](#global-apps) . |

Если число имеет больше разрядов справа от десятичного разделителя, чем количество заполнителей в строке форматирования, число округляется до стольких десятичных разрядов, сколько указано заполнителей. Если число имеет больше разрядов слева от десятичного разделителя, чем количество заполнителей в строке форматирования, отображаются все дополнительные цифры. Если в строке форматирования слева от десятичной запятой указаны только символы номера (#), числа меньше 1 начинаются с десятичного разделителя (например, **.47**).

### <a name="date-and-time-placeholders"></a>Заполнители даты и времени

|   Заместитель    |   Описание                                                  |
|------------------|----------------------------------------------------------------|
|  **m**   |   Отображает месяц в виде числа без нуля в начале.               |
|  **mm**  |   Отображает месяц в виде числа с нулем в начале, если требуется. |
|  **mmm** |   Отображает сокращенное название месяца (от **янв** до **дек**).          |
|                                                                                                   **mmmm**                                                                                                   |                                                                          Отображает полное название месяца (от **января** до **декабря**).                                                                           |
|                                                                                                    **d**                                                                                                     |                                                                                Отображает день месяца в виде числа без нуля в начале.                                                                                 |
|                                                                                                    **dd**                                                                                                    |                                                                         Отображает день месяца в виде числа с нулем в начале, если требуется.                                                                          |
|                                                                                                   **ddd**                                                                                                    |                                                                              Отображает сокращенное название дня недели (от **вс** до **сб**).                                                                              |
|                                                                                                   **dddd**                                                                                                   |                                                                            Отображает полное название дня недели (от **воскресенья** до **субботы**).                                                                            |
|                                                                                                    **yy**                                                                                                    |                                                                                      Отображает год в виде двузначного числа.                                                                                       |
|                                                                                                   **yyyy**                                                                                                   |                                                                                      Отображает год в виде четырехзначного числа.                                                                                      |
|                                                                                                    **h**                                                                                                     |                                                                                Отображает время в виде числа без нуля в начале.                                                                                |
|   **hh** | Отображает часы в виде числа с нулем в начале, если требуется. Если строка форматирования содержит обозначения **AM** или **PM**, часы отображаются в 12-часовом формате. В противном случае часы отображаются в 24-часовом формате. | 
|  **m**   |   Отображает минуты в виде числа без нуля в начале.<br><br>Этот заполнитель должен располагаться сразу после кода **h** или **HH** или непосредственно перед кодом **SS** ; в противном случае **текст** Возвращает месяц, а не минуты.  |    
| **mm**   | Отображает минуты в виде числа с нулем в начале, если требуется.<br><br>Этот заполнитель должен располагаться сразу после заполнителя **h** или **HH** или непосредственно перед заполнителем **SS** . В противном случае **текст** Возвращает месяц, а не минуты. |                                                                                                                   
| **s**   |  Отображает секунды в виде числа без нуля в начале.  |
| **ss**  | Отображает секунды в виде числа с нулем в начале, если требуется.                                                                        |
|                                                                                                    **f**                                                                                                     |                                                                                         Отображает доли секунды.                                                                                          |
|                                                                                    **AM/PM**, **a/p**                                                                                    |               Отображает часы в 12-часовом формате. **Текст** ВОЗВРАЩАЕТ "AM" или "a" для времени с полуночи до полудня и "p" для времени от полудня до полуночи                |

### <a name="literal-placeholders"></a>Литеральные заполнители
В строку форматирования можно включить также перечисленные ниже символы.  Функция **Text** будет отображать их без изменения. Остальные символы зарезервированы для новых заполнителей, поэтому их не следует использовать.

| Символ | Описание |
| --- | --- |
| Любой символ валюты |Знак доллара, знак центов, знак евро, и т. д. |
| **+** |Знак "плюс" |
| **(** |Левая круглая скобка |
| **:** |Двоеточие |
| **^** |Диакритический знак циркумфлекс (курсор) |
| **'** |Апостроф |
| **{** |Левая фигурная скобка |
| **<** |Знак "меньше" |
| **=** |Знак "равно" |
| **-** |Знак "минус" |
| **/** |Косая черта |
| **)** |Правая круглая скобка |
| **&** |Амперсанд |
| **~** |Тильда |
| **}** |Правая фигурная скобка |
| **>** |Знак "больше" |
| &nbsp; |Символ пробела |

## <a name="global-apps"></a>Глобальные приложения
Функция **Text** учитывает региональные форматы. Во многих языках она используется для правильного оформления дат, времени, валют и чисел. Чтобы сделать все правильно, ей нужны два блока информации.

* **Язык пользовательского формата:** Как следует интерпретировать пользовательский формат для руководителей? Знаки разделителей ( **.** и **,** ) имеют разные значения в разных языках. Если задан пользовательский формат, можно включить заполнитель языка или использовать значение по умолчанию, которое отражает язык, на котором установлено устройство. Еще проще можно использовать один из [стандартных форматов даты и времени](#predefined-datetime-formats), которые не зависят от языка.
* **Язык результата:** Для пользователей, на каком языке должен отображаться результат функции? Названия месяцев и дней недели должны быть на соответствующем языке для пользователя приложения, который можно указать, добавив третий, необязательный аргумент в функцию **Text** . 

Для обоих языков указывается язык с помощью [тега языка](function-language.md#language-tags). Чтобы просмотреть список поддерживаемых языков, введите **текст (1234, "",)** в строке формул или на вкладке **Дополнительно** на правой панели, а затем прокрутите список языков, предлагаемых для третьего аргумента.

### <a name="language-placeholder"></a>Заполнитель языка
Чтобы указать язык пользовательского формата, используйте следующий синтаксис.

| Заместитель | Описание |
| --- | --- |
| **[$-*LanguageTag*]** |Здесь *LanguageTag* обозначает тег языка, возвращаемый функцией **Language**. Он может указать только язык (например, **[$-en]** для английского языка) или указать регион (например, **[$-en-GB]** для дальнейшей настройки Великобритании). |

Заполнитель с указанием языка может находиться в любом месте пользовательской строки форматирования, но должен встречаться только один раз.

Если вы указали пользовательский формат без заполнителя языка и формат неоднозначен с глобальной точки зрения, то тег языка для текущего языка вставляется автоматически.  

**[$-en-US]** предполагается, если этот заполнитель отсутствует при запуске приложения. 

> [!NOTE]
> В следующей версии синтаксис этого заполнителя может измениться, чтобы избежать путаницы с похожим, но отличающимся заполнителем, поддерживаемым Excel.

### <a name="result-language-tag"></a>Тег для языка результата
Результат **текста** включает переведенные строки для месяцев, дней недели и обозначений AM/PM, а также соответствующие группы и десятичные разделители.

По умолчанию функция **Text** использует язык пользователя, запустившего приложение. Функция **Language** возвращает тег языка для текущего пользователя. Это значение по умолчанию можно переопределить, указав тег языка для третьего аргумента в **тексте**.

## <a name="syntax"></a>Синтаксис
**Text**( *нумберордатетиме*; *датетимеформатенум* [; *ресултлангуажетаг* ])

* *Нумберордатетиме* — обязательный. Числовое значение или значение даты и времени, которое нужно отформатировать.
* *DateTimeFormat* — обязательный аргумент.  Значение из списка **DateTimeFormat**.
* *ResultLanguageTag* — необязательный аргумент. Тег языка для форматирования результата. По умолчанию используется язык текущего пользователя.

**Text**( *нумберордатетиме*; *CustomFormat* [; *ресултлангуажетаг* ])

* *Number* — обязательный аргумент. Числовое значение или значение даты и времени, которое нужно отформатировать.
* *CustomFormat* — обязательный аргумент. Один или несколько заполнителей, заключенные в двойные кавычки.
* *ResultLanguageTag* — необязательный аргумент. Тег языка для форматирования результата. По умолчанию используется язык текущего пользователя.

**Текст**( *анивалуе* )

* *Анивалуе* — обязательный. Значение для преобразования в текстовое представление. Используется формат по умолчанию.

## <a name="examples"></a>Примеры
Если не указано иное, пользователь, выполняющий эти формулы, находится в США и в качестве языка выбран английский язык.  Функция **Language** возвращает значение "en-US".

### <a name="number"></a>число;

| Формула | Описание | Возвращаемый результат |
| --- | --- | --- |
| **Text(&nbsp;1234,59;&nbsp;"####.#"&nbsp;)** |Форматирует число с одним знаком после десятичного разделителя. |"1234.6" |
| **Text(&nbsp;8,9;&nbsp;"#.000"&nbsp;)** |Дополняет десятичную часть числа замыкающими нулями, если потребуется. |"8.900" |
| **Text(&nbsp;0,631;&nbsp;"0.#"&nbsp;)** |Дополняет целую часть числа ведущими нулями, если потребуется. |"0.6" |
| **Text(&nbsp;12;&nbsp;"#.0#"&nbsp;)**<br>**Text(&nbsp;1234,568;&nbsp;"#.0#"&nbsp;)** |Дополняет десятичную часть числа нулями до одного десятичного разряда, но использует два десятичных разряда, если они предоставлены. |"12.0"<br>"1234.57" |
| **Text(&nbsp;12000;&nbsp;"$ #,###"&nbsp;)**<br>**Text(&nbsp;1200000;&nbsp;"$&nbsp;#,###"&nbsp;)** |Добавляет разделитель разрядов после каждых трех цифр целой части числа, а также добавляет символ валюты. |"$&nbsp;12,000"<br>"$&nbsp;1,200,000" |

### <a name="datetime"></a>Дата и время
* Результаты по состоянию на **14:37:47** в **понедельник, 23 ноября 2015 г.**
* (тихоокеанское стандартное время (UTC-8))

| Формула | Описание | Возвращаемый результат |
| --- | --- | --- |
| **Text( Now(); DateTimeFormat.LongDate )** |Форматирует как длинную строку даты с соблюдением языка и языковых стандартов текущего пользователя. |"Monday, November 23, 2015" |
| **Text( Now(); DateTimeFormat.LongDateTime )** |Форматирует как длинную строку даты и времени с соблюдением языка и языковых стандартов текущего пользователя и временем в 12-часовом формате. |"Monday, November 23, 2015 2:37:47 PM" |
| **Text( Now(); DateTimeFormat.LongTime24 )** |Форматирует как длинную строку времени в 24-часовом формате. |"14:37:47" |
| **Text( Now(); DateTimeFormat.ShortDate )** |Форматирует как короткую строку даты с соблюдением языка и языковых стандартов текущего пользователя. |"11/23/2015" |
| **Text( Now(); "d-mmm-yy" )** |Форматирует в соответствии с переданными заполнителями: <ul><li>**d** заменяется одной или двумя цифрами, обозначающими номер месяца.<li>**-** передается напрямую в результат, как литеральный символ.<li>**mmm** заменяется трехбуквенным сокращением для месяца.<li>**-** также передается напрямую в результат.<li>**yy** заменяется двузначным номером года.</ul> |"23-Nov-15" |
| **Текст (1448318857 * 1000, Ммм. дд, гггг (чч: мм: сс AM/PM) ")** | Показывает значение даты и времени Unix в удобочитаемом формате, если значение источника умножается на 1 000. | "Ноя 23, 2015 (02:47:37 PM)" |

### <a name="global-apps"></a>Глобальные приложения

| Формула | Описание | Возвращаемый результат |
| --- | --- | --- |
| **Text (1234567,89; "[$-fr-FR] # # # #, # # &euro;"; "fr-FR")** | Показывает пробел в качестве разделителя группирования, запятую в качестве десятичного разделителя и **&euro;** как символ валюты. |"1&nbsp;234&nbsp;567, 89 &euro;" |
| **Текст (1234567; 89;; "[$-fr-FR] # # # #, # # &euro;")** | Если исходные данные следуют за французским запятыми в качестве десятичного разделителя, необходимо изменить языковой стандарт на французский и разделяйте аргументы точкой с запятой, а не запятой, чтобы получить тот же результат, как показано выше. |"1&nbsp;234&nbsp;567, 89 &euro;" |
| **Text( Date(2016;1;31); "dddd mmmm d" )** |Возвращает день недели, месяц и день месяца на языке текущего пользователя. Так как все эти заполнители не зависят от языка, указывать тега языка в строке форматирования не требуется. |"Суббота&nbsp;Январь&nbsp;31" |
| **Text( Date(2016;1;31); "dddd mmmm d"; "es-ES" )** |Возвращает день недели, месяц и день месяца на языке "es-ES". |"-Доминго&nbsp;енеро&nbsp;31" |

### <a name="converting-values-to-text"></a>Преобразование значений в текст

| Формула | Описание | Возвращаемый результат |
| --- | --- | --- |
| **Текст (&nbsp;1234567,89&nbsp;)** | Преобразует число в строку. Нет разделителей тысяч или контроль над количеством цифр до или после десятичного разделителя; для большего контроля укажите число заполнителей в качестве второго аргумента. | "1234567,89" |
| **Текст (&nbsp;Датетимевалуе (&nbsp;"01/04/2003"&nbsp;)&nbsp;)** | Преобразует значение даты и времени в строку текста. Чтобы управлять преобразованием, предоставьте либо член перечисления DateTimeFormat, либо строку пользовательского формата. | "1/4/2003 12:00 AM" |
| **Текст (&nbsp;true&nbsp;)** | Преобразует логическое значение в строку. | "true" |
| **Text (&nbsp;GUID ()&nbsp;)** | Преобразует созданное значение GUID в строку.  | "f8b10550-0f12-4f08-9aa3-bb10958bc3ff" |
| **Left (&nbsp;Text (&nbsp;GUID ()&nbsp;),&nbsp;4&nbsp;)** | Возвращает первые четыре символа созданного GUID. | "2d9c" | 
