---
title: Функция Distinct | Документация Майкрософт
description: Справочные сведения о функции Distinct в PowerApps, включая описание синтаксиса и примеры.
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
ms.openlocfilehash: 17a2f2cfca16c5589f74ac434b36326037146b16
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61551222"
ms.PowerAppsDecimalTransform: true
---
# <a name="distinct-function-in-powerapps"></a>Функция Distinct в PowerApps
Эта функция вычисляет итоговые значения для [записей](../working-with-tables.md#records) [таблицы](../working-with-tables.md), удаляя дубликаты.

## <a name="description"></a>Описание
Функция **Distinct** вычисляет формулу для каждой записи таблицы. Функция **Distinct** возвращает таблицу с одним столбцом, содержащую результаты без повторяющихся значений.  

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

## <a name="syntax"></a>Синтаксис
**Distinct**( *Таблица*; *Формула* )

* *Table* — обязательный аргумент.  Таблица для оценки.
* *Formula* — обязательный аргумент.  Формула, вычисляемая для каждой записи.

## <a name="example"></a>Пример
Если бы у вас была таблица **Employees**, содержащая столбец **Department**, то приведенная ниже функция вывела бы список уникальных названий отделов в этом столбце, независимо от того, сколько раз каждое название в нем указано.

**Distinct(Employees; Department)**

