---
title: Функция Find | Документация Майкрософт
description: Справочные сведения о функции Find в PowerApps, включая описание синтаксиса и примеры.
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
ms.openlocfilehash: fbdd29ed1757301f076ab6bebea548fcd7a963cc
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "71984956"
---
# <a name="find-function-in-powerapps"></a>Функция Find в PowerApps
Находит текстовую строку, если она существует, в другой строке.

## <a name="description"></a>Описание
Функция **Find** выполняет поиск строки в другой строке и учитывает регистр. Чтобы не учитывать регистр, сначала примените к аргументам функцию **[Lower](function-lower-upper-proper.md)** .

Функция **Find** возвращает начальную позицию найденной строки.  Позиция 1 — это первый знак строки. Функция **Find** возвращает значение *blank* (пусто), если строка, в которой выполняется поиск, не содержит искомой строки.

## <a name="syntax"></a>Синтаксис
**Find**( *Искомая_строка*, *Строка* [, *Начальная_позиция* ] )

* *Искомая_строка* — обязательный аргумент.  Строка, которую требуется найти.
* *Строка* — обязательный аргумент.  Строка, в которой требуется выполнить поиск.
* *Начальная_позиция* — необязательный аргумент.  Начальная позиция, с которой необходимо начать поиск.  Позиция 1 — это первый знак.

