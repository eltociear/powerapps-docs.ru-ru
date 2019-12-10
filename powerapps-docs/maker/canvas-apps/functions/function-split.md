---
title: Функция Split | Документация Майкрософт
description: Справочные сведения, включая синтаксис и примеры, для функции Split в Power Apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm tapanm
ms.date: 09/14/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d58c4b64f558ec2a9348a9a9433b9a55f69419db
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730110"
ms.PowerAppsDecimalTransform: true
---
# <a name="split-function-in-power-apps"></a>Функция Split в Power Apps
Разбивает строку текста на таблицу с подстроками.

## <a name="description"></a>Description
Функция **Split** разбивает строку текста на таблицу с подстроками.  Используйте функцию **Split**, чтобы разбивать списки с разделителями-запятыми, даты с косой чертой, а также другие элементы с четко определенными разделителями.  

Строка разделителя используется для разбивки текстовой строки.  Разделитель может содержать ноль, один или несколько символов, которые в текстовой строке обрабатываются как одно целое.  Если используется *пустая* строка или строка нулевой длины, будет разделен каждый символ.  Соответствующие строки разделители не возвращаются в результатах.  Если соответствующий разделитель не найден, вся строка текста возвращается как один результат.

Используйте функцию **[concat](function-concatenate.md)** , чтобы Пересоединить строку без разделителей. 
 
Используйте функцию **[MatchAll](function-ismatch.md)** для разделения строки с помощью регулярного выражения.

В примерах показано, как можно использовать **разбиение** с **[первой](function-first-last.md)** и **[последней](function-first-last.md)** функцией для извлечения одной подстроки с разделителями.  Функция **[Match](function-ismatch.md)** часто является более кратким и мощным выбором для тех, кто знаком с регулярными выражениями.

## <a name="syntax"></a>Синтаксис
**Split**( *Text*; *Separator* )

* *Text* — обязательный аргумент.  Разбиваемый текст.
* *Separator* — обязательный аргумент.  Разделитель, используемый для разбивки строки.  Может включать ноль, один или несколько символов.

## <a name="examples"></a>Примеры

### <a name="basic-usage"></a>Базовое использование

| Формула | Description | Возвращаемый результат |
| --- | --- | --- |
| `Split( "Apples, Oranges, Bananas"; "," )` |Разбивает определения фруктов, используя в качестве разделителя запятую.  Пробел за запятой в состав разделителя не входит, поэтому в результате возвращаются подстроки "&nbsp;Oranges" и "&nbsp;Bananas". |<style> img { max-width: none; } </style> ![](media/function-split/fruit1.png) |
| `TrimEnds( Split( "Apples, Oranges, Bananas"; "," ) )` |Пример, аналогичный предыдущему. Но здесь пробел удаляется с помощью [функции **TrimEnds**](function-trim.md), которая обрабатывает столбец таблицы, созданных функцией **Split**. Мы также можно использовать разделитель **",&nbsp;"** , который включает пробел после запятой, но такая конфигурация не будет работать правильно, если пробел будет отсутствовать или будет двойным. |<style> img { max-width: none; } </style> ![](media/function-split/fruit2.png) |
| `Split( "08/28/17"; "/" )` |Разбивает элементы даты, используя в качестве разделителя косую черту. |<style> img { max-width: none; } </style> ![](media/function-split/date.png) |

### <a name="different-delimiters"></a>Разные разделители

| Формула | Description | Возвращаемый результат |
| --- | --- | --- |
| `Split( "Hello, World"; "," )` |Разбивает слова, используя в качестве разделителя запятую.  Вторая подстрока начинается с пробела, так как этот символ следует после запятой. |<style> img { max-width: none; } </style> ![](media/function-split/comma.png) |
| `Split( "Hello, World"; "o" )` |Разбивает строку, используя в качестве разделителя символ o. |<style> img { max-width: none; } </style> ![](media/function-split/o.png) |
| `Split( "Hello, World"; "l" )` |Разбивает строку, используя в качестве разделителя символ l. Так как между двумя символами **l** в слове **Hello** ничего нет, возвращается *пустое* значение. |<style> img { max-width: none; } </style> ![](media/function-split/l.png) |
| `Split( "Hello, World"; "ll" )` |Разбивает строку, используя в качестве разделителя символы ll. |<style> img { max-width: none; } </style> ![](media/function-split/ll.png) |
| `Split( "Hello, World"; "%" )` |Разбивает строку, используя в качестве разделителя символ %. Так как этого разделителя в строке нет, возвращается целая строка. |<style> img { max-width: none; } </style> ![](media/function-split/percent.png) |
| `Split( "Hello, World"; "" )` |Разбивает строку, используя в качестве разделителя пустую строку (0 знаков). Строка будет разбита посимвольно. |<style> img { max-width: none; } </style> ![](media/function-split/none.png) |

### <a name="substring-extraction"></a>Извлечение подстроки

| Формула | Description | Возвращаемый результат |
| --- | --- | --- |
| `First( Split( Last( Split( "Bob Jones <bob.jones@contoso.com>"; "<" ) ).Result; ">" ) ).Result` | Разделяет строку на основе открывающего разделителя (<) и извлекает строку справа от разделителя с **последним**.  Затем формула разделяет этот результат на основе закрывающего разделителя (>) и извлекает строку слева от разделителя с **правым**. | "bob.jones@contoso.com" |
| `Match( "Bob Jones <bob.jones@contoso.com>"; "<(?<email>.+)>" ).email` | Выполняет то же извлечение, основанное на разделителе, что и в последнем примере, но использует функцию **Match** и регулярное выражение. | "bob.jones@contoso.com" |

