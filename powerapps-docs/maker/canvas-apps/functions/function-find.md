---
title: Функция Find | Документация Майкрософт
description: Справочные сведения, включая синтаксис и примеры, для функции поиска в Power Apps
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
ms.openlocfilehash: 62254bf46836ffc8ed5fa5b7685561b611db49a7
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730977"
ms.PowerAppsDecimalTransform: true
---
# <a name="find-function-in-power-apps"></a>Функция поиска в Power Apps
Находит текстовую строку, если она существует, в другой строке.

## <a name="description"></a>Description
Функция **Find** выполняет поиск строки в другой строке и учитывает регистр. Чтобы не учитывать регистр, сначала примените к аргументам функцию **[Lower](function-lower-upper-proper.md)** .

Функция **Find** возвращает начальную позицию найденной строки.  Позиция 1 — это первый знак строки. Функция **Find** возвращает значение *blank* (пусто), если строка, в которой выполняется поиск, не содержит искомой строки.

## <a name="syntax"></a>Синтаксис
**Find**( *Искомая_строка*; *Строка* [; *Начальная_позиция* ] )

* *Искомая_строка* — обязательный аргумент.  Строка, которую требуется найти.
* *Строка* — обязательный аргумент.  Строка, в которой требуется выполнить поиск.
* *Начальная_позиция* — необязательный аргумент.  Начальная позиция, с которой необходимо начать поиск.  Позиция 1 — это первый знак.

