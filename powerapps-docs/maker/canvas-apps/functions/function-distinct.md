---
title: Функция Distinct | Документация Майкрософт
description: Справочные сведения, включая синтаксис и примеры, для функции DISTINCT в Power Apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/14/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b77cdf452250fc30e1b8c61867f82e5f109fff49
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731248"
---
# <a name="distinct-function-in-power-apps"></a>Функция DISTINCT в Power Apps
Эта функция вычисляет итоговые значения для [записей](../working-with-tables.md#records) [таблицы](../working-with-tables.md), удаляя дубликаты.

## <a name="description"></a>Description
Функция **DISTINCT** вычисляет формулу для каждой записи таблицы и возвращает таблицу с одним столбцом результатов с удаленными повторяющимися значениями.  Имя столбца является **результатом**.  

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

[!INCLUDE [delegation-no-one](../../../includes/delegation-no-one.md)]

## <a name="syntax"></a>Синтаксис
**Distinct**( *Таблица*, *Формула* )

* *Table* — обязательный аргумент.  Таблица для оценки.
* *Formula* - обязательный аргумент.  Формула, вычисляемая для каждой записи.

## <a name="example"></a>Пример

1. Вставьте элемент управления [ **"Кнопка"** ](../controls/control-button.md) и задайте для его свойства **OnSelect** значение этой формулы.

    ```powerapps-dot
    ClearCollect( CityPopulations,
        { City: "London",    Country: "United Kingdom", Population: 8615000 },
        { City: "Berlin",    Country: "Germany",        Population: 3562000 },
        { City: "Madrid",    Country: "Spain",          Population: 3165000 },
        { City: "Hamburg",   Country: "Germany",        Population: 1760000 },
        { City: "Barcelona", Country: "Spain",          Population: 1602000 },
        { City: "Munich",    Country: "Germany",        Population: 1494000 }
    );
    ```

1. Нажмите кнопку, удерживая клавишу ALT.

    Формула выводится и создается коллекция **Цитипопулатионс** , которую можно отобразить, выбрав **Цитипопулатионс** в строке формул:

    > [!div class="mx-imgBorder"]
    > Коллекция ![Цитипопулатионс, показанная в представлении результатов](media/function-distinct/citypopulations-create.png)

1. Вставьте элемент управления [**таблицы данных**](../controls/control-data-table.md) и задайте для его свойства **Items** значение этой формулы:

    ```powerapps-dot
    Distinct( CityPopulations, Country )
    ```

    Результат этой формулы можно просмотреть в строке формул, выбрав всю формулу:

    > [!div class="mx-imgBorder"]
    > ![вывод из функции distinct, отображаемой в представлении результатов](media/function-distinct/citypopulations-distinct.png)

1. Используйте ссылку **изменить поля** в области свойств таблицы данных, чтобы добавить столбец **результатов** .

    > [!div class="mx-imgBorder"]
    > ![вывод из функции distinct, отображаемой в таблице данных](media/function-distinct/citypopulations-datatable.png)

1. Вставьте элемент управления [**Label**](../controls/control-text-box.md) и задайте в качестве его свойства **Text** формулу:

    ```powerapps-dot
    First( Sort( Distinct( CityPopulations, Country ), Result ) ).Result
    ```

    Эта формула сортирует результаты из **DISTINCT** с помощью функции [**Sort**](function-sort.md) , принимает первую запись из результирующей таблицы [**первой**](function-first-last.md) функцией и извлекает **результирующее** поле, чтобы получить только название страны.

    > [!div class="mx-imgBorder"]
    > ![вывод из функции distinct, отображающей первую страну по имени](media/function-distinct/citypopulations-first.png)

     
