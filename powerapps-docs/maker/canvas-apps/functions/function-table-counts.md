---
title: Функции Count, CountA, CountIf и CountRows | Документация Майкрософт
description: Справочные сведения, включая синтаксис и пример, для функций Count, CountA, CounfIf и CountRows в PowerApps
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
ms.openlocfilehash: 717baab028b480063f76b799a1267155464d8ac3
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61543526"
ms.PowerAppsDecimalTransform: true
---
# <a name="count-counta-countif-and-countrows-functions-in-powerapps"></a>Функции Count, CountA, CountIf и CountRows в PowerApps
Подсчитывает все [записи](../working-with-tables.md#records) в [таблице](../working-with-tables.md) или подсчитывает количество записей, удовлетворяющих условию.

## <a name="description"></a>Описание
Функция **Count** подсчитывает количество содержащих число записей в таблице из одного столбца.

Функция **CountA** подсчитывает количество *непустых* записей в таблице из одного столбца. При подсчете учитываются [пустые](function-isblank-isempty.md) текстовые строки ("").

Функция **CountIf** подсчитывает количество записей в таблице, которые возвращают значение **true** в результате вычисления логической формулы.  Формула может ссылаться на [столбцы](../working-with-tables.md#columns) таблицы.

Функция **CountRows** подсчитывает количество записей в таблице.

Каждая из этих функций возвращает число.

[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>Синтаксис
**Count**( *таблица_из_одного_столбца* )<br>
**CountA**( *SingleColumnTable* )

* *SingleColumnTable* — обязательный аргумент.  Столбец записей для подсчета.  

**CountIf**( *таблица*; *логическая_формула* )

* *Table* — обязательный аргумент.  Таблица с записями для подсчета.
* *Логическая_формула* — обязательный аргумент.  Формула для вычисления для каждой записи таблицы.  Учитываются записи, возвращающие по этой формуле значение **true**.  Формула может ссылаться на столбцы таблицы.

**CountRows**( *таблица* )

* *Table* — обязательный аргумент.  Таблица с записями для подсчета.

## <a name="example"></a>Пример
1. Импортируйте или создайте [коллекцию](../working-with-data-sources.md#collections) с именем **Inventory**, как описано в первом шаге описания [показа текста и изображений в коллекции](../show-images-text-gallery-sort-filter.md).
2. Добавьте метку и установите в ее свойстве **[Text](../controls/properties-core.md)** формулу:
   
    **CountIf(Inventory; UnitsInStock < 30)**
   
    Метка показывает **2**, так как по двум продуктам (Ganymede и Callisto) на складе меньше 30 единиц.
3. Добавьте другую метку и установите в ее свойстве **[Text](../controls/properties-core.md)** формулу:
   
    **CountA(Inventory.UnitsInStock)**
   
    Метка показывает **5**, так как это количество непустых ячеек в столбце **UnitsInStock**.
4. Добавьте другую метку и установите в ее свойстве **[Text](../controls/properties-core.md)** формулу:
   
    **CountRows(Inventory)**
   
    Метка показывает **5**, так как коллекция содержит пять строк.

