---
title: Функция Distinct | Документация Майкрософт
description: Справочные сведения о функции Distinct в PowerApps, включая описание синтаксиса и примеры.
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
ms.openlocfilehash: 7d9ae4df7a4ad11a49b2a25ae78330d0cd807c9b
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "71985251"
---
# <a name="distinct-function-in-powerapps"></a>Функция Distinct в PowerApps
Эта функция вычисляет итоговые значения для [записей](../working-with-tables.md#records) [таблицы](../working-with-tables.md), удаляя дубликаты.

## <a name="description"></a>Описание
Функция **DISTINCT** вычисляет формулу для каждой записи таблицы и возвращает таблицу с одним столбцом результатов с удаленными повторяющимися значениями.  Имя столбца является **результатом**.  

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

[!INCLUDE [delegation-no-one](../../../includes/delegation-no-one.md)]

## <a name="syntax"></a>Синтаксис
**Distinct**( *Таблица*, *Формула* )

* *Table* — обязательный аргумент.  Таблица для оценки.
* *Formula* — обязательный аргумент.  Формула, вычисляемая для каждой записи.

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
    > Коллекция ![CityPopulations, показанная в представлении результатов @ no__t-1

1. Вставьте элемент управления [**таблицы данных**](../controls/control-data-table.md) и задайте для его свойства **Items** значение этой формулы:

    ```powerapps-dot
    Distinct( CityPopulations, Country )
    ```

    Результат этой формулы можно просмотреть в строке формул, выбрав всю формулу:

    > [!div class="mx-imgBorder"]
    > ![Output из функции distinct, показанной в представлении результатов @ no__t-1

1. Используйте ссылку **изменить поля** в области свойств таблицы данных, чтобы добавить столбец **результатов** .

    > [!div class="mx-imgBorder"]
    > ![Output из функции distinct, показанной в таблице данных @ no__t-1

1. Вставьте элемент управления [**Label**](../controls/control-text-box.md) и задайте в качестве его свойства **Text** формулу:

    ```powerapps-dot
    First( Sort( Distinct( CityPopulations, Country ), Result ) ).Result
    ```

    Эта формула сортирует результаты из **DISTINCT** с помощью функции [**Sort**](function-sort.md) , принимает первую запись из результирующей таблицы [**первой**](function-first-last.md) функцией и извлекает **результирующее** поле, чтобы получить только название страны.

    > [!div class="mx-imgBorder"]
    > ![Output из функции distinct, показывающей первую страну по имени @ no__t-1

     
