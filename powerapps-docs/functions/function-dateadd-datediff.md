---
title: "Функции DateAdd, DateDiff и TimeZoneOffset | Документация Майкрософт"
description: "Справочные сведения о функциях DateAdd, DateDiff и TimeZoneOffset в PowerApps, включая описание синтаксиса и примеры."
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
ms.date: 05/23/2017
ms.author: gregli
ms.openlocfilehash: 9fdae99e280e088139882271db7328490b3d4fcc
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2018
---
# <a name="dateadd-datediff-and-timezoneoffset-functions-in-powerapps"></a>Функции DateAdd, DateDiff и TimeZoneOffset в PowerApps
Добавление значения даты и времени или поиск разницы в значениях даты и времени, а также преобразование между местным временем и временем в формате UTC.

## <a name="description"></a>Описание
Функция **DateAdd** добавляет указанное число единиц измерения к значению даты и времени. Результатом является новое значение даты и времени. Можно также вычесть число единиц измерения из значения даты и времени, указав отрицательное значение.

Функция **DateDiff** возвращает разницу между двумя значениями даты и времени. Результатом является число единиц измерения.

Возможные единицы измерения, используемые в обеих функциях: **Milliseconds**, **Seconds**, **Minutes**, **Hours**, **Days**, **Months**, **Quarters** или **Years**.  По умолчанию обе функции в качестве единиц используют **Days**.

Функция **TimeZoneOffset** возвращает число минут между местным временем пользователя и временем в формате UTC.   

Можно совмещать функции **DateAdd** и **TimeZoneOffset**, чтобы выполнять преобразование между местным временем пользователя и временем в формате UTC.  Добавляя результат **TimeZoneOffset**, можно преобразовать местное время в формат UTC, а вычитая его (добавляя отрицательное значение), можно преобразовать время в формате UTC в местное время.

Ознакомьтесь также с дополнительными сведениями в статье о [работе с датами и временем](../show-text-dates-times.md).

## <a name="syntax"></a>Синтаксис
**DateAdd**( *Дата_и_время*, *Величина* [, *Единицы* ] )

* *Дата_и_время* — обязательный аргумент. Значение даты и времени, для которого необходимо выполнить операцию.
* *Величина* — обязательный аргумент. Число, добавляемое к значению *Дата_и_время*, в единицах *Единицы*.
* *Единицы* — необязательный аргумент. Возможный тип аргумента *Единицы*: **Milliseconds**, **Seconds**, **Minutes**, **Hours**, **Days**, **Months**, **Quarters** или **Years**.  Если значение не указано, используются единицы **Days**.

**DateDiff**( *Начальная_дата_и_время*, *Конечная_дата_и_время* [, *Единицы* ] )

* *Начальная_дата_и_время* — обязательный аргумент. Начальное значение даты и времени.
* *Конечная_дата_и_время* — обязательный аргумент. Конечное значение даты и времени.
* *Единицы* — необязательный аргумент. Возможный тип аргумента *Единицы*: **Milliseconds**, **Seconds**, **Minutes**, **Hours**, **Days**, **Months**, **Quarters** или **Years**.  Если значение не указано, используются единицы **Days**.

**TimeZoneOffset**( [ *Дата_и_время* ] )

* *Дата_и_время* — необязательный аргумент.  Значение даты и времени, для которого возвращается смещение.  По умолчанию используются текущие дата и время.

## <a name="examples"></a>Примеры
Во всех примерах предполагается, что текущие дата и время — **13:02 15 июля 2013 года**.

### <a name="simple-dateadd"></a>Простой пример для функции DateAdd
| Формула | Описание | Возвращаемый результат |
| --- | --- | --- |
| **Text( DateAdd( Now(), 3 ),<br>"dd-mm-yyyy hh:mm" )** |Добавляет три дня (единицы измерения по умолчанию) к текущему значению даты и времени. |"18-07-2013 13:02" |
| **Text( DateAdd( Now(), 4, Hours ),<br>"dd-mm-yyyy hh:mm" )** |Добавляет четыре часа к текущему значению даты и времени. |"15-07-2013 17:02" |
| **Text( DateAdd( Today(), 1, Months ),<br>"dd-mm-yyyy hh:mm" )** |Добавляет один месяц к текущему значению даты без указания времени, так как **Today** не возвращает составляющую времени. |"15-08-2013 00:00" |
| **Text( DateAdd( Now(), &#8209;30, Minutes ),<br>"dd-mm-yyyy hh:mm" )** |Вычитает 30 минут из текущего значения даты и времени. |"15-07-2013 12:32" |

### <a name="simple-datediff"></a>Простой пример для функции DateDiff
| Формула | Описание | Возвращаемый результат |
| --- | --- | --- |
| **DateDiff( Now(), DateValue("1/1/2014") )** |Возвращает разницу между двумя значениями в **днях**, являющихся единицами измерения по умолчанию. |170 |
| **DateDiff( Now(), DateValue("1/1/2014"), Months )** |Возвращает разницу между двумя значениями в **месяцах**. |6 |
| **DateDiff( Now(), Today(), Minutes )** |Возвращает разницу между текущим значением даты и времени и текущей датой (без указания времени) в минутах.  Так как значение **Now** следует после значения **Today**, то результат будет отрицательным. |–782 |

### <a name="converting-to-utc"></a>Преобразование в формат UTC
Чтобы выполнить преобразование в формат UTC, добавьте значение **TimeZoneOffset** для заданного времени.  

Например, представьте, что сейчас **13:02 15 июля 2013 года** по летнему тихоокеанскому времени США (UTC-7).  Чтобы определить текущее время в формате UTC, используйте следующую команду:

* **DateAdd( Now(), TimeZoneOffset(), Minutes )**

По умолчанию **TimeZoneOffset** вычисляется для текущего времени, поэтому его не требуется передавать как аргумент.

Чтобы увидеть результат, используйте функцию **Text** в формате *дд-мм-гггг чч:мм*. Она вернет **15-07-2013 20:02**.

### <a name="converting-from-utc"></a>Преобразование из формата UTC
Чтобы преобразовать время из формата UTC в местное время, следует вычесть значение **TimeZoneOffset** (то есть добавить отрицательное значение) из заданного времени.

Для примера предположим, что значение даты и времени в формате UTC, **20:02:00 15 июля 2013 года**, хранится в переменной **StartTime**. Чтобы настроить время в соответствии с текущим часовым поясом пользователя, используйте следующую команду:

* **DateAdd( StartTime, -TimeZoneOffset( StartTime ), Minutes )**

Обратите внимание, на знак минус перед **TimeZoneOffset**, который позволяет вычесть смещение, а не добавить его.

Чтобы увидеть результат, используйте функцию **Text** в формате *дд-мм-гггг чч:мм*. Она вернет **15-07-2013 13:02**, если вы находитесь в часовом поясе тихоокеанского времени США (лето).
