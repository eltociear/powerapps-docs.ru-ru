---
title: Функция Shuffle | Документация Майкрософт
description: Справочные сведения, включая синтаксис и пример, для функции Shuffle в PowerApps
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
ms.openlocfilehash: 3fd93ce6cf9703e9e9fbf69c5826213d9aa78e02
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61519186"
---
# <a name="shuffle-function-in-powerapps"></a>Функция Shuffle в PowerApps
Случайным образом изменяет порядок [записей](../working-with-tables.md#records) в [таблице](../working-with-tables.md).

## <a name="description"></a>Описание
Функция **Shuffle** изменяет порядок записей в таблице (перемешивает таблицу).

Функция **Shuffle** возвращает таблицу, в которой столько же [столбцов](../working-with-tables.md#columns) и строк, сколько в таблице-аргументе.

## <a name="syntax"></a>Синтаксис
**Shuffle**( *таблица* )

* *Table* — обязательный аргумент.  Таблица для перемешивания.

## <a name="example"></a>Пример
Если вы храните информацию об игральных картах в [коллекции](../working-with-data-sources.md#collections) с именем **Deck**, то эта формула вернет копию коллекции, которая будет перемешана случайным образом.

**Shuffle(Deck)**

