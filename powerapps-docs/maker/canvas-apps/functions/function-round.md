---
title: Функции Round, RoundDown и RoundUp | Документация Майкрософт
description: Справочные сведения о функциях Round, RoundDown и RoundUp в PowerApps, включая описание синтаксиса
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8480d66949994ba59f5ab84aef7999ab36a20b51
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "71983986"
ms.PowerAppsDecimalTransform: true
---
# <a name="round-rounddown-and-roundup-functions-in-powerapps"></a>Функции Round, RoundDown и RoundUp в PowerApps
Округление чисел.

## <a name="description"></a>Описание
Функции **Round**, **RoundDown** и **RoundUp** округляют число до указанного количества знаков после запятой (десятичных разрядов).

* Функция **Round** округляет число в большую сторону, если следующая цифра после запятой больше или равна 5. В противном случае число округляется в меньшую сторону.
* Функция **RoundDown** всегда округляет число в меньшую сторону — до предыдущего (меньшего) числа.
* Функция **RoundUp** всегда округляет число в большую сторону — до следующего (большего) числа.

При передаче одного числа возвращаемое значение является округленной версией такого числа.  При передаче [таблицы](../working-with-tables.md), содержащей один столбец с числами, возвращаемое значение представляет таблицу из одного столбца с округленными числами. Таблицу с несколькими столбцами можно преобразовать в таблицу с одним столбцом, как описано в статье об [использовании таблиц](../working-with-tables.md).

## <a name="syntax"></a>Синтаксис
**Round**( *Number*; *DecimalPlaces* )<br>**RoundDown**( *Number*; *DecimalPlaces* )<br>**RoundUp**( *Number*; *DecimalPlaces* )

* *Number* — обязательный аргумент. Число, которое нужно округлить.
* *DecimalPlaces* — обязательный аргумент.  Количество знаков после запятой, до которого нужно округлить число.  Используйте 0, если необходимо округлить до целого числа.  

