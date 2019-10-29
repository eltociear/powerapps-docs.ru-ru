---
title: Функции Concat и Concatenate | Документация Майкрософт
description: Справочные сведения о функциях Concat и Concatenate в PowerApps, включая описание синтаксиса и примеры.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0a56230539990ce51cc9270f71d8c2b7c9a1db73
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/29/2019
ms.locfileid: "71992887"
---
# <a name="concat-and-concatenate-functions-in-powerapps"></a>Функции Concat и Concatenate в PowerApps

Объединяют отдельные строки текста и строки в [таблицах](../working-with-tables.md).

## <a name="description"></a>Description

Функция **Concatenate** объединяет сочетание отдельных строк и таблицу из одного столбца со строками. При использовании этой функции с отдельными строками она эквивалентна использованию [оператора](operators.md) **&** .

Функция **Concat** объединяет результат формулы, примененной ко всем [записям](../working-with-tables.md#records) таблицы, в результате чего получается одна строка. Используйте эту функцию для объединения строк таблицы, как функция **[Sum](function-aggregates.md)** делает с числами.

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

Используйте функцию [**Split**](function-split.md) или [**MatchAll**](function-ismatch.md) для разделения строки на таблицу подстрок.

## <a name="syntax"></a>Синтаксис

**Concat**( *Table*, *Formula* )

- *Table* — обязательный аргумент.  Таблица, с которой выполняются операции.
- *Formula* - обязательный аргумент.  Формула, которую необходимо применить к записям таблицы.

**Concatenate**( *Строка1* [, *Строка2*, ...] )

- *Строка* — обязательные аргументы.  Сочетание отдельных строк или таблица из одного столбца со строками.

## <a name="examples"></a>Примеры

В примерах в этом разделе используются следующие глобальные переменные:

- **FirstName** = "Мария"
- **LastName** = "Петров"
- **Продукты** = ![таблицы с двумя столбцами и четырьмя строками](media/function-concatenate/products.png)

Чтобы создать эти глобальные переменные в приложении, вставьте элемент управления [**Button**](../controls/control-button.md) и задайте для его свойства **OnSelect** значение этой формулы:

```powerapps-dot
Set( FirstName, "Jane" ); Set( LastName, "Doe" );
Set( Products,
    Table(
        { Name: "Violin", Type: "String" },
        { Name: "Cello", Type: "String" },
        { Name: "Trumpet", Type: "Wind" }
    )
)
```

Нажмите кнопку (щелкнув ее, удерживая нажатой клавишу Alt).

### <a name="concatenate-function-and-the--operator"></a>Функция СЦЕПИТЬ и оператор &

Для этих примеров задайте для свойства **Text** элемента управления [**Label**](../controls/control-text-box.md) формулу из первого столбца следующей таблицы.

| Формула | Description | Возвращаемый результат |
|---------|-------------|--------|
| **Сцепление (&nbsp;LastName, &nbsp; ", &nbsp;", &nbsp;FirstName &nbsp;)** | Сцепляет значение в **LastName**, строку **","** (запятую, за которой следует пробел) и значение в поле **FirstName**. | "Петров, &nbsp;Jane" |
| **LastName &nbsp; & &nbsp; ", &nbsp;" &nbsp; &** | То же, что и в предыдущем примере, за исключением использования оператора **&** , а не функции. | "Петров, &nbsp;Jane" |
| **Сцепление (&nbsp;FirstName, &nbsp; "&nbsp;", &nbsp;LastName &nbsp;)** | Сцепляет значение в **FirstName**, строку **""** (один пробел) и значение в **LastName**. | Мария &nbsp;Doeа |
| **FirstName &nbsp; & &nbsp; "&nbsp;" &nbsp; & &nbsp;LastName** | То же, что и в предыдущем примере, вместо функции используется оператор **&** . | Мария &nbsp;Doeа |

### <a name="concatenate-with-a-single-column-table"></a>Объединение с таблицей с одним столбцом

В этом примере добавьте пустой, вертикальный элемент управления [**коллекции**](../controls/control-gallery.md) , задайте для его свойства **Items** значение формула в следующей таблице, а затем добавьте метку в шаблоне коллекции.

| Формула | Description | Возвращаемый результат |
|---------|-------------|--------|
| **СЦЕПИТЬ ("имя: &nbsp;", &nbsp;Products. Name, ", &nbsp;Type: &nbsp;", &nbsp;Products. Type)** | Для каждой записи в таблице **Products** объединяет строку **"имя:"** , имя продукта, строку **", тип:"** и тип продукта.  | ![Таблица продуктов](media/function-concatenate/single-column.png) |

### <a name="concat-function"></a>Concat, функция

Для этих примеров задайте для свойства **Text** метки формулу из первого столбца следующей таблицы.

| Формула | Description | Возвращаемый результат |
|---------|-------------|--------|
| **Concat (Products, Name & ",")** | Вычисляет **имя выражения & ","** для каждой записи **продуктов** и объединяет результаты в одну текстовую строку.  | "Скрипка, &nbsp;Cello, &nbsp;Trumpet, &nbsp;" |
| **Concat (Filter (&nbsp;Products, &nbsp;Type &nbsp; = &nbsp; строку &nbsp;), Name & ",")** | Оценивает **имя формулы & ","** для каждой записи **продуктов** , удовлетворяющей **типу фильтра = "String"** , и объединяет результаты в одну текстовую строку.   | "Скрипка, &nbsp;Cello, &nbsp;" |

### <a name="trimming-the-end"></a>Обрезка конца

Последние два примера содержат дополнительный символ "," в конце результата. Функция добавляет запятую и пробел в значение **имени** каждой записи в таблице, включая последнюю запись.

В некоторых случаях эти дополнительные символы не имеют значения. Например, разделитель одинарного пробела не отображается, если результат отображается в метке. Если вы хотите удалить эти дополнительные символы, используйте функцию [**Left**](function-left-mid-right.md) или [**Match**](function-ismatch.md) .

Для этих примеров задайте для свойства **Text** метки формулу из первого столбца следующей таблицы.

| Формула | Description | Возвращаемый результат |
|---------|-------------|--------|
| **Left (Concat (&nbsp;Products,&nbsp;Name&nbsp;&&nbsp;",&nbsp;"&nbsp;), len (&nbsp;Concat (&nbsp;Products,&nbsp;Name&nbsp;&&nbsp;" ,&nbsp;"&nbsp;)&nbsp;)&nbsp;-&nbsp;2)** | Возвращает результат **concat** , но удаляет последние два символа, которые формируют лишний разделитель. | "Скрипка, &nbsp;Cello, &nbsp;Trumpet" |
| **Match (Concat (&nbsp;Products,&nbsp;Name&nbsp;&&nbsp;",&nbsp;"&nbsp;")," ^ (?&lt;обрезать&gt;. *),&nbsp;$ "). Trim** | Возвращает символы **concat** от начала текстовой строки (^) до конца ($), но не включает нежелательную запятую и пробел в конце. | "Скрипка, &nbsp;Cello, &nbsp;Trumpet" |

### <a name="split-and-matchall"></a>Разделение и MatchAll

Если вы использовали **concat** с разделителем, операцию можно отменить, объединив функции **Split** и **MatchAll** .

Для этих примеров Добавьте пустую вертикальную галерею, задайте для свойства **Items** значение формулы в следующей таблице, а затем добавьте метку в шаблон коллекции.

| Формула | Description | Возвращаемый результат |
|---------|-------------|--------|
| **Split (Concat (&nbsp;Products, &nbsp;Name &nbsp; & &nbsp; ", &nbsp;" &nbsp; "),", ")** | Разделяет текстовую строку с помощью разделителя **","** . Строка заканчивается запятой и пробелом, поэтому последняя строка в результате представляет собой пустую строку.  | ![Table](media/function-concatenate/split.png) |
| **MatchAll (Concat (&nbsp;Products,&nbsp;Name&nbsp;&&nbsp;",&nbsp;"&nbsp;")," [^ \s,] + "). фуллматч** | Разделяет текстовую строку на основе символов, не являющихся пробелами или запятыми. Эта формула удаляет лишнюю запятую и пробел в конце строки. | ![Table](media/function-concatenate/matchall.png)