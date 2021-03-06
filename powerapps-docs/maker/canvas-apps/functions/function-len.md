---
title: Функция Len | Документация Майкрософт
description: Справочные сведения, включая синтаксис и примеры, для функции LEN в Power Apps
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
ms.openlocfilehash: 07b706d9cc0a61e204669646734cdcaf7fc50946
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730636"
ms.PowerAppsDecimalTransform: true
---
# <a name="len-function-in-power-apps"></a>Функция Len в Power Apps
Возвращает длину текстовой строки.

## <a name="description"></a>Description
Если в качестве аргумента указать одну строку, функция вернет длину в виде числа.  Если указать [таблицу](../working-with-tables.md) из одного столбца, содержащую строки, функция вернет таблицу из одного столбца с длинами каждой из строк. Таблицу с несколькими столбцами можно преобразовать в таблицу с одним столбцом, как описано в статье об [использовании таблиц](../working-with-tables.md).

Если указать [пустую](function-isblank-isempty.md) строку, функция **Len** возвращает значение 0.

## <a name="syntax"></a>Синтаксис
**Len**(*строка*)

* *Строка* — обязательный аргумент. Строка, длину которой требуется определить.

**Len**(*таблица_из_одного_столбца*)

* *SingleColumnTable* — обязательный аргумент. Таблица из одного столбца со строками, длины которых нужно определить.

## <a name="examples"></a>Примеры
### <a name="single-string"></a>Одна строка
Во всех примерах этого раздела в качестве [источника данных](../working-with-data-sources.md) используется элемент управления для ввода текста под названием **Author** (Автор), содержащий строку "E. И. Иванов".

| Формула | Description | Возвращаемый результат |
| --- | --- | --- |
| **Len(Author.Text)** |Определяет длину строки в поле **Author**. |14 |
| **Len( "" )** |Определяет длину пустой строки. |0 |

### <a name="single-column-table"></a>Для таблицы с одним столбцом
В первом примере этого раздела используется источник данных под названием **People** (Люди), содержащий указанные ниже значения.

![](media/function-len/people-table.png)

| Формула | Description | Возвращаемый результат |
| --- | --- | --- |
| **Len(ShowColumns(&nbsp;People;&nbsp;"Address"&nbsp;))** |В [столбце](../working-with-tables.md#columns) **Address** (Адрес) таблицы **People** (Люди):<br><ul><li>Определяет длину каждой строки.</li><li>Возвращает таблицу из одного столбца, содержащего длины каждой из строк.</li> |<style> img { max-width: none } </style> ![](media/function-len/people-table-len.png) |
| **Len(["Hello"; "to the"; "World"; ""])** |В столбце **[Value](function-value.md)** (Значение) встроенной таблицы:<br><ul><li>Определяет длину каждой строки.</li><li>Возвращает таблицу из одного столбца, содержащего длины каждой из строк.</li> |![](media/function-len/people-table-len-inline.png) |

