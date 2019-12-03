---
title: Функции Round, RoundDown и RoundUp | Документация Майкрософт
description: Справочные сведения, включая синтаксис, для функций Round, RoundDown и RoundUp в Power Apps
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
ms.openlocfilehash: 3b319f831291b1d0d21f3ed4699a144beb023611
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730285"
---
# <a name="round-rounddown-and-roundup-functions-in-power-apps"></a>Функции Round, RoundDown и RoundUp в Power Apps
Округление чисел.

## <a name="description"></a>Description
Функции **Round**, **RoundDown** и **RoundUp** округляют число до указанного количества знаков после запятой (десятичных разрядов).

* Функция **Round** округляет число в большую сторону, если следующая цифра после запятой больше или равна 5. В противном случае число округляется в меньшую сторону.
* Функция **RoundDown** всегда округляет число в меньшую сторону — до предыдущего (меньшего) числа.
* Функция **RoundUp** всегда округляет число в большую сторону — до следующего (большего) числа.

При передаче одного числа возвращаемое значение является округленной версией такого числа.  При передаче [таблицы](../working-with-tables.md), содержащей один столбец с числами, возвращаемое значение представляет таблицу из одного столбца с округленными числами. Таблицу с несколькими столбцами можно преобразовать в таблицу с одним столбцом, как описано в статье об [использовании таблиц](../working-with-tables.md).

## <a name="syntax"></a>Синтаксис
**Round**( *Number*, *DecimalPlaces* )<br>**RoundDown**( *Number*, *DecimalPlaces* )<br>**RoundUp**( *Number*, *DecimalPlaces* )

* *Number* — обязательный аргумент. Число, которое нужно округлить.
* *DecimalPlaces* — обязательный аргумент.  Количество знаков после запятой, до которого нужно округлить число.  Используйте 0, если необходимо округлить до целого числа.  

