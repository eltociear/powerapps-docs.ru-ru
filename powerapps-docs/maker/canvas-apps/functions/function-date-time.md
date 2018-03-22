---
title: "Функции Date и Time | Документация Майкрософт"
description: "Справочные сведения о функциях Date и Time в PowerApps, включая описание синтаксиса и примеры."
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
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: bed2bc9b13b4d167d6852b7029e4e69d54d50413
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2018
---
# <a name="date-and-time-functions-in-powerapps"></a>Функции Date и Time в PowerApps
Преобразуют компоненты даты и времени в значение даты и времени.

## <a name="description"></a>Описание
Функция **Date** преобразует отдельные значения Year (Год), Month (Месяц) и Day (День) в единое значение даты и времени.  В качестве времени в этом значении указывается полночь.

* Если значение аргумента Year находится в диапазоне от 0 до 1899 (включительно), то функция прибавляет это значение к числу 1900 и вычисляет год.  **70** превращается в **1970**.
* Если значение аргумента Month меньше 1 или больше 12, то результат вычитает это значение или добавляет его от начала указанного года.
* Если значение аргумента Day превышает количество дней в указанном месяце, то функция добавляет это значение к первому дню месяца и возвращает соответствующую дату из следующего месяца.  Если значение аргумента Day меньше 1, то функция вычитает это значение, плюс 1 день, от первого дня указанного месяца.

Функция **Time** преобразует отдельные значения Hour (Час), Minute (Минута) и Second (Секунда) в единое значение даты и времени.  Результат не содержит связанной с ним даты.

Ознакомьтесь с описанием функций **[DateValue](function-datevalue-timevalue.md)**, **[TimeValue](function-datevalue-timevalue.md)** и **[DateTimeValue](function-datevalue-timevalue.md)** для получения сведений о преобразовании строки в значение.  

Ознакомьтесь также с дополнительными сведениями в статье о [работе с датами и временем](../show-text-dates-times.md).

## <a name="syntax"></a>Синтаксис
**Date**( *Год*, *Месяц*, *День* )

* *Год* — обязательный аргумент.  Числа больше 1899 интерпретируются как абсолютные (1980 интерпретируется как 1980), а числа в диапазоне от 0 до 1899 интерпретируются как относительные по отношению к 1900. (Например, 80 интерпретируется как 1980.)
* *Месяц* — обязательный аргумент.  Число в диапазоне от 1 до 12.
* *День* — обязательный аргумент. Число в диапазоне от 1 до 31.

**Time**( *Часы*, *Минуты*, *Секунды* )

* *Часы* — обязательный аргумент.  Число в диапазоне от 0 (12:00 AM) до 23 (11:00 PM).
* *Минуты* — обязательный аргумент. Число в диапазоне от 0 до 59.
* *Секунды* — обязательный аргумент. Число в диапазоне от 0 до 59.

## <a name="examples"></a>Примеры
### <a name="date"></a>Дата
Если пользователь ввел **1979** в элемент управления для ввода текста с именем **HireYear**, а также ввел **3** — в **HireMonth** и **17** — в **HireDay**, то эта функция должна вернуть значение **3/17/1979**:

**Date(Value(HireYear.Text), Value(HireMonth.Text), Value(HireDay.Text))**

### <a name="time"></a>Time
Если пользователь ввел **14** в элемент управления для ввода текста с именем **BirthHour**, а также ввел **50** — в **BirthMinute** и **24** — в **BirthSecond**, то эта функция должна вернуть значение **02:50:24 p**.

**Text(Time(Value(BirthHour.Text), Value(BirthMinute.Text), Value(BirthSecond.Text)), "hh:mm:ss a/p")**
