---
title: Добавление и переключение экранов в приложении на основе холста | Документы Майкрософт
description: Добавление экрана в приложение Canvas и использование кнопок "Далее" и "назад" для перехода между экранами в Power Apps
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 02/03/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: cbe6173c94f001874b126a5b8ecb1bdf9ad21b70
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74724424"
ms.PowerAppsDecimalTransform: true
---
# <a name="add-a-screen-to-a-canvas-app-and-navigate-between-screens"></a>Добавление и переключение экранов в приложении на основе холста

Создайте приложение на основе холста с несколькими экранами и предоставьте пользователям возможность перемещаться между ними.

## <a name="add-and-rename-a-screen"></a>Добавление и переименование экрана

1. На вкладке **Главная** выберите **создать экран**, а затем выберите тип экрана, который требуется добавить.

    ![Команда добавления экрана на вкладке Home (Главная)](./media/add-screen-context-variables/add-screen.png)

2. На правой панели выберите имя экрана (непосредственно над вкладкой **Свойства** ), а затем введите **Source**.

    ![Переименование экрана по умолчанию](./media/add-screen-context-variables/name-source-screen.png)

3. Добавьте еще один экран под названием **Target** (Назначение).

    ![Два экрана на панели навигации слева](./media/add-screen-context-variables/two-screens-in-nav.png)

## <a name="reorder-screens"></a>Переупорядочить экраны

На панели навигации слева наведите указатель мыши на экран, который требуется переместить вверх или вниз, нажмите появившуюся кнопку, а затем выберите **вверх или вниз** **.**

![Переупорядочить экран](./media/add-screen-context-variables/reorder-screen.png)

> [!NOTE]
> Когда приложение открывается, экран в верхней части иерархического списка элементов управления обычно отображается первым. Но можно указать другой экран, задав для свойства **[OnStart](controls/control-screen.md)** формулу, включающую функцию **[navigate](functions/function-navigate.md)** .

## <a name="add-navigation"></a>Добавление элементов навигации

1. Выбрав **Исходный** экран, откройте вкладку **Вставка** , выберите **значки**, а затем щелкните **стрелку далее**.  

    ![Shapes (Фигуры) на вкладке Insert (Вставка)](./media/add-screen-context-variables/add-next-arrow.png)

2. Необязательно: переместите стрелку в правый нижний угол экрана.

3. Выбрав стрелку, перейдите на вкладку **действие** и выберите пункт **Переход**.

    Для свойства **[OnSelect](controls/properties-core.md)** стрелки будет автоматически выбрана функция **Navigate** (Навигация).

    ![Для свойства OnSelect выбрана функция Navigate (Навигация)](./media/add-screen-context-variables/onselect-default.png)

    Когда пользователь выбирает стрелку, **целевой** экран постепенно исчезает.

4. На экране **Target** добавьте элемент **Back arrow** (Стрелка "Назад") и установите для ее свойства **[OnSelect](controls/properties-core.md)** следующую формулу:

    `Navigate(Source; ScreenTransition.Fade)`

5. Удерживая нажатой клавишу Alt, переключитесь между экранами, щелкнув стрелку на каждом экране.

## <a name="more-information"></a>Дополнительные сведения

[Справочник по элементу управления экраном](controls/control-screen.md)