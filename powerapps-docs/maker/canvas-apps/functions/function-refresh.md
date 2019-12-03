---
title: Функция Refresh | Документация Майкрософт
description: Справочные сведения, включая синтаксис и пример для функции обновления в Power Apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/21/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8376d21117c286a540ca8b873c7e91b07d53d607
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730387"
---
# <a name="refresh-function-in-power-apps"></a>Функция обновления в Power Apps
Обновляет [записи](../working-with-tables.md#records) [источника данных](../working-with-data-sources.md).

## <a name="description"></a>Description
Функция **Refresh** получает свежую копию источника данных.  Вы сможете увидеть изменения, внесенные другими пользователями.

Функция **Refresh** не возвращает никакого значения, и ее можно использовать только в [формулах управления поведением](../working-with-formulas-in-depth.md).

## <a name="syntax"></a>Синтаксис
**Refresh**( *источник_данных* )

* *Источник_данных* — обязательный аргумент. Это источник данных, который требуется обновить.

## <a name="example"></a>Пример
В этом примере обновляется источник данных под названием **IceCream**, который начинается с таких значений:

![](media/function-refresh/icecream.png)

Пользователь на другом устройстве изменяет значение **Quantity** в записи **Strawberry** на **400**.  Вы не увидите этого изменения, пока не будет выполнена следующая формула:

**Refresh(IceCream)**

После ее выполнения в коллекциях, связанных с источником данных **IceCream**, появится обновленное значение **Strawberry**:

![](media/function-refresh/icecream-after.png)

