---
title: Функции Abs, Exp, Ln, Power и Sqrt | Документация Майкрософт
description: Справочные сведения, включая синтаксис и примеры, для ABS, sqrt и других функций в Power Apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/13/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 925297a8e1a3f4c454cb8bbb09f75a87419cf5cb
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730484"
ms.PowerAppsDecimalTransform: true
---
# <a name="abs-exp-ln-power-and-sqrt-functions-in-power-apps"></a>Функции ABS, exp, LN, Power и sqrt в Power Apps
Вычисление абсолютного значения, натурального логарифма и квадратного корня, возведение *e* или любого числа в указанную степень.

## <a name="description"></a>Description
Функция **Abs** возвращает абсолютное значение полученного аргумента. Если передается отрицательное число, функция **Abs** возвращает противоположное ему положительное число.

Функция **Exp** возвращает число *e*, возведенное в указанную степень.  Трансцендентное число *e* начинается так: 2,7182818...

Функция **Ln** возвращает натуральный логарифм (по основанию *e*) от полученного аргумента.

Функция **Power** возвращает число, возведенное в указанную степень.  Эта функция эквивалентна [оператору **^** ](operators.md).

Функция **Sqrt** возвращает число, квадрат которого равен полученному аргументу.

Если передать одно число, возвращается один результат, соответствующий вызванной функции.  Если передать [таблицу](../working-with-tables.md) с одним столбцом, содержащим числовые значения, возвращается таблица с одним столбцом, содержащим результаты вычислений — по одному результату для каждой записи в таблице аргументов. Таблицу с несколькими столбцами можно преобразовать в таблицу с одним столбцом, как описано в статье об [использовании таблиц](../working-with-tables.md).  

Если для аргумента не определено значение функции, возвращается *пустое* значение.  (Например, при попытке получить квадратный корень или логарифм от отрицательного числа.)

## <a name="syntax"></a>Синтаксис
**Abs**( *Number* )<br>**Exp**( *Number* )<br>**Ln**( *Number* )<br>**Sqrt**( *Number* )

* *Number* — обязательный аргумент. Число, для которого нужно выполнить операцию.

**Power**( *Base*; *Exponent* )

* *Base* — обязательный аргумент. Число, которое нужно возвести в степень.
* *Exponent* — обязательный аргумент. Показатель степени, в которую нужно возвести число.

**Abs**( *SingleColumnTable* )<br>**Exp**( *SingleColumnTable* )<br>**Ln**( *SingleColumnTable* )<br>**Sqrt**( *SingleColumnTable* )

* *SingleColumnTable* — обязательный аргумент. Таблица с одним столбцом, для значений в котором нужно выполнить операцию.

## <a name="examples"></a>Примеры
### <a name="single-number"></a>Для одного числа

| Формула | Description | Возвращаемый результат |
| --- | --- | --- |
| **Abs( -55 )** |Возвращает число без знака "минус". |55 |
| **Exp( 2 )** |Возвращает *e* в степени 2, то есть *e* \* *e*. |7,389056... |
| **Ln( 100 )** |Возвращает натуральный логарифм (по основанию *e*) от числа 100. |4,605170... |
| **Power( 5; 3 )** |Возвращает 5 в степени 3, то есть 5 \* 5 \* 5. |125 |
| **Sqrt( 9 )** |Возвращает число, квадрат которого равен числу 9. |3 |

### <a name="single-column-table"></a>Для таблицы с одним столбцом
В примерах этого раздела используется [источник данных](../working-with-data-sources.md) с именем **ValueTable**, который содержит такие данные:

![](media/function-numericals/values.png)

| Формула | Description | Возвращаемый результат |
| --- | --- | --- |
| **Abs(&nbsp;ValueTable&nbsp;)** |Возвращает абсолютное значение для каждого числа из таблицы. |<style> img { max-width: none } </style> ![](media/function-numericals/values-abs.png) |
| **Exp(&nbsp;ValueTable&nbsp;)** |Возвращает число *e*, возведенное в указанную степень для каждого числа из таблицы. |<style> img { max-width: none } </style> ![](media/function-numericals/values-exp.png) |
| **Ln(&nbsp;ValueTable&nbsp;)** |Возвращает натуральный логарифм для каждого числа из таблицы. |<style> img { max-width: none } </style> ![](media/function-numericals/values-ln.png) |
| **Sqrt(&nbsp;ValueTable&nbsp;)** |Возвращает квадратный корень для каждого числа из таблицы. |![](media/function-numericals/values-sqrt.png) |

### <a name="step-by-step-example"></a>Пошаговый пример
1. Добавьте элемент управления **[Текстовое поле](../controls/control-text-input.md)** и назовите его **Source**.
2. Добавьте элемент управления **Метка** и задайте в качестве значения свойства **[Text](../controls/properties-core.md)** следующую формулу:
   <br>
   **Sqrt( Value( Source.Text ) )**
3. Введите число в элемент **Source** и убедитесь, что в элементе управления **Метка** отображается квадратный корень введенного числа.

