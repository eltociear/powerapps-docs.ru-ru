---
title: Функции DateValue, TimeValue и DateTimeValue | Документация Майкрософт
description: Справочные сведения о функциях DateValue, TimeValue и DateTimeValue в PowerApps, включая описание синтаксиса и примеры.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c1f11be30f56859ede0950feebc27dd1be39d011
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61551199"
ms.PowerAppsDecimalTransform: true
---
# <a name="datevalue-timevalue-and-datetimevalue-functions-in-powerapps"></a>Функции DateValue, TimeValue и DateTimeValue в PowerApps
Преобразует дату, время или оба этих параметра в строке в значение даты и времени.

## <a name="description"></a>Описание
Функция **DateValue** преобразует строку даты (например "10/01/2014") в значение даты и времени.

Функция **TimeValue** преобразует строку времени (например "12:15 PM") в значение даты и времени.

Функция **DateTimeValue** преобразует строку даты и времени (например "January 10, 2013 12:13 AM") в значение даты и времени.

Функция **DateValue** игнорирует любые сведения о времени в строке даты, а функция **TimeValue** игнорирует любые сведения о дате в строке времени.

По умолчанию используется язык текущего пользователя, но это значение можно переопределить, чтобы строки интерпретировались правильно. Например, для "en" строка "10/1/1920" интерпретируется как 1<sup>ое</sup> октября, а для "fr" — как 10<sup>ое</sup> января.

Даты должны быть указаны в одном из следующих форматов:

* ММ/ДД/ГГГГ
* ДД/ММ/ГГГГ
* ДД Мес ГГГГ
* Месяц ДД, ГГГГ

Ознакомьтесь с функциями **[Date](function-date-time.md)** и **[Time](function-date-time.md)**, чтобы преобразовать числовые компоненты (дата, месяц, год, час, минута и секунда).

Ознакомьтесь также с дополнительными сведениями в статье о [работе с датами и временем](../show-text-dates-times.md).

Чтобы преобразовать числа, см. статью о функции **[Value](function-value.md)**.

## <a name="syntax"></a>Синтаксис
**DateValue**( *Строка* [; *Язык* ])<br>**DateTimeValue**( *Строка* [; *Язык* ])<br>**TimeValue**( *Строка* [; *Язык* ])

* *строка* — обязательный аргумент.  Текстовая строка, которая содержит дату, время или комбинированное значение даты и времени.
* *Язык* — необязательный аргумент.  Строка языка, такая как возвращается первыми двумя знаками из функции **[Language](function-language.md)**.  Если этот аргумент не указан, то используется язык клиента текущего пользователя.  

## <a name="examples"></a>Примеры
### <a name="datevalue"></a>DateValue
Если вы ввели **10/11/2014** в элемент управления для ввода текста с именем **Startdate**, а затем задали свойству **[Text](../controls/properties-core.md)** метки такое значение функции:

* **Text(DateValue(Startdate.Text); DateTimeFormat.LongDate)**
  
    Метка отобразит **Saturday, October 11, 2014**, если на компьютере выбран языковой стандарт **en**.
  
    > [!NOTE]
  > С параметром **DateTimeFormat** можно использовать несколько вариантов, отличных от **LongDateTime**. Чтобы отобразить список этих вариантов, в поле функции введите параметр, а сразу за ним поставьте восклицательный знак.
* **Text(DateValue(Startdate.Text; "fr"); DateTimeFormat.LongDate)**
  
    Метка отобразит **Monday, November 10, 2014**.

Если вы сделали то же самое для даты **October 20, 2014**:

* **DateDiff(DateValue(Startdate.Text); Today())**
  
    Если на компьютере выбран языковой стандарт **en**, то метка отобразит **9**, что означает количество дней между 11 октября и 20 октября. Функция **[DateDiff](function-dateadd-datediff.md)** также может показывать разницу в месяцах, кварталах или годах.

### <a name="datetimevalue"></a>DateTimeValue
Если вы ввели **10/11/2014 1:50:24.765 PM** в элемент управления для ввода текста с именем **Start**, а затем задали свойству **[Text](../controls/properties-core.md)** метки такое значение функции:

* **Text(DateTimeValue(Start.Text); DateTimeFormat.LongDateTime)**
  
    Метка отобразит **Saturday, October 11, 2014 1:50:24 PM**, если на компьютере выбран языковой стандарт "en".
  
    > [!NOTE]
  > С параметром **DateTimeFormat** можно использовать несколько вариантов, отличных от **LongDateTime**. Чтобы отобразить список этих вариантов, в поле функции введите параметр, а сразу за ним поставьте восклицательный знак.
* **Text(DateTimeValue(Start.Text; "fr"); DateTimeFormat.LongDateTime)**
  
    Метка отобразит **Monday, November 10, 2014 1:50:24 PM**.
* **Text(DateTimeValue(Start.Text); "dddd, mmmm dd, yyyy hh:mm:ss.fff AM/PM")**
  
    Метка отобразит **Saturday, October 11, 2014 01:50:24:765 PM**, если на компьютере выбран языковой стандарт **en**.
  
    Вы также можете указать формат **hh:mm:ss.f** или **hh:mm:ss.ff**, чтобы округлять значение времени до ближайшей десятой или сотой доли секунды.

### <a name="timevalue"></a>TimeValue
Назовите элемент управления для ввода текста **FinishedAt** и задайте свойству **[Text](../controls/properties-core.md)** метки такое значение функции:

**If(TimeValue(FinishedAt.Text)<TimeValue("5:00:00.000 PM"); "You made it!"; "Too late!")**

* Если ввести **4:59:59.999 PM** в элемент управления **FinishedAt**, то метка отобразит "You made it!".
* Если ввести **5:00:00.000 PM** в элемент управления **FinishedAt**, то метка отобразит "Too late!".

