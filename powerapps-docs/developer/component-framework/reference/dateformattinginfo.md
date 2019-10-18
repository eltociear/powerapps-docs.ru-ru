---
title: DateFormattingInfo | Документация Майкрософт
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4e7d43fb-b6b7-4f1d-89e3-0b8157c9d2d9
ms.openlocfilehash: fb6dc5c67cc0ea031ab4e264d282458163ee46a0
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72344837"
---
# <a name="dateformattinginfo"></a>DateFormattingInfo

[!INCLUDE [context-description](includes/dateformattinginfo-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="properties"></a>Свойства

### <a name="abbreviateddaynames"></a>abbreviatedDayNames

{"Sun", "Пн", "Вторник", "среда", "четверг", "Пятница", "Кот"}

**Тип**: `string`

### <a name="abbreviatedmonthgenitivenames"></a>аббревиатедмонсженитивенамес

{"Jan", "Фев", "Мар", "Апр", "Май", "Июн", "Jul", "Авг", "Sep", "Oct", "Ноя", "Дек", ""}

**Тип**: `string[]`

### <a name="abbreviatedmonthnames"></a>abbreviatedMonthNames

{"Jan", "Фев", "Мар", "Апр", "Май", "Июн", "Jul", "Авг", "Sep", "Oct", "Ноя", "Дек", ""}

**Тип**: `string[]`

### <a name="amdesignator"></a>amDesignator

ПОЛЬЗУЮСЬ

**Тип**: `string`

### <a name="calendar"></a>Календар

**Тип**: `object`

Объект `calendar` содержит следующие свойства:

|Имя|Тип|Description|
|--|--|--|
|`algorithmType`|`number`|1|
|`calendarType`|`number`|1|
|`maxSupportedDateTime`|`Date`|"/Дате (253402300799999)/"|
|`minSupportedDateTime`|`Date`|"/Дате (-62135568000000)/"|
|`twoDigitYearMax`|`number`|2029|

### <a name="calendarweekrule"></a>календарвикруле

**Тип**: `number`

### <a name="dateseparator"></a>датесепаратор

"/"

**Тип**: `string`

### <a name="daynames"></a>dayNames

{"Воскресенье", "понедельник", "Вторник", "среда", "четверг", "Пятница", "Суббота"}

**Тип**: `string[]`

### <a name="firstdayofweek"></a>firstDayOfWeek

**Тип**: `number`

Свойству `firstDayOfWeek` может быть присвоено одно из следующих значений:

|Value|А|
|--|--|
|0|Воскресенье|
|1|Понедельник|
|2|Вторник|
|3|Среда|
|4|Четверг|
|5|Пятница|
|6|Суббота|

### <a name="fulldatetimepattern"></a>fullDateTimePattern

"dddd, MMMM d, yyyy чч: СС TT"

**Тип**: `string`

### <a name="longdatepattern"></a>longDatePattern

дддд, мммм d, гггг "

**Тип**: `string`

### <a name="longtimepattern"></a>longTimePattern

"чч: мм: СС TT"

**Тип**: `string`

### <a name="monthdaypattern"></a>monthDayPattern

"Мммм дд"

**Тип**: `string`

### <a name="monthgenitivenames"></a>монсженитивенамес

{"Январь", "Февраль", "Март",...  "Декабрь", ""}

**Тип**: `string[]`

### <a name="monthnames"></a>monthNames

{"Январь", "Февраль", "Март",...  "Декабрь", ""}

**Тип**: `string[]`

### <a name="pmdesignator"></a>pmDesignator

PM

**Тип**: `string`

### <a name="shortdatepattern"></a>shortDatePattern

"M/d/гггг"

**Тип**: `string`

### <a name="shorttimepattern"></a>shortTimePattern

"ч TT"

**Тип**: `string`

### <a name="shortestdaynames"></a>шортестдайнамес

{"Su", "Mo", "tu", "мы", "th", "fr", "SA"}

**Тип**: `string[]`

### <a name="sortabledatetimepattern"></a>sortableDateTimePattern

yyyy'-'MM'-'dd'T'HH ': ' mm ': ' SS '

**Тип**: `string`

### <a name="timeseparator"></a>тимесепаратор

":"

**Тип**: `string`

### <a name="universalsortabledatetimepattern"></a>universalSortableDateTimePattern

"yyyy'-'MM'-'дд чч ': ' mm ': ' Сс'з '"

**Тип**: `string`

### <a name="yearmonthpattern"></a>yearMonthPattern

"Мммм гггг"

**Тип**: `string`


### <a name="related-topics"></a>Связанные статьи

[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)