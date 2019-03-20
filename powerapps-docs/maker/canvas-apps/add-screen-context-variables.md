---
title: Добавление и переключение экранов в приложении на основе холста | Документы Майкрософт
description: Добавление экрана в приложение на основе холста и переход между экранами с помощью стрелок вперед и назад в PowerApps
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
ms.openlocfilehash: b6f83d21b2964dac7c4925d45efdf11a3a1e6b02
ms.sourcegitcommit: 7f67cd28c781a48f6a211ed82c2c861ae3acf1a5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/04/2019
ms.locfileid: "57800728"
---
# <a name="add-a-screen-to-a-canvas-app-and-navigate-between-screens"></a>Добавление и переключение экранов в приложении на основе холста

Создайте приложение на основе холста с несколькими экранами и предоставьте пользователям возможность перемещаться между ними.

## <a name="add-and-rename-a-screen"></a>Добавление и переименование экрана

1. На **Главная** выберите **новый экран**, а затем выберите тип создаваемого экрана, который вы хотите добавить.

    ![Команда добавления экрана на вкладке Home (Главная)](./media/add-screen-context-variables/add-screen.png)

2. На панели справа выберите имя экрана (непосредственно над **свойства** вкладку), а затем введите **источника**.

    ![Переименование экрана по умолчанию](./media/add-screen-context-variables/name-source-screen.png)

3. Добавьте еще один экран под названием **Target** (Назначение).

    ![Два экрана на панели навигации слева](./media/add-screen-context-variables/two-screens-in-nav.png)

## <a name="reorder-screens"></a>Изменить порядок экранов

На панели навигации слева, наведите указатель мыши на экран, на котором вы хотите переместить вверх или вниз, выберите кнопку с многоточием, который отображается, а затем выберите **вверх** или **вниз**.

![Изменение порядка экране](./media/add-screen-context-variables/reorder-screen.png)

> [!NOTE]
> При открытии приложения экрана в верхней части иерархического списка элементов управления обычно отображаются первыми. Но можно указать другой экран, задав **[OnStart](controls/control-screen.md)** формулу, которая включает **[Navigate](functions/function-navigate.md)** функции.

## <a name="add-navigation"></a>Добавление элементов навигации

1. С **источника** экрана выбран, откройте **вставить** выберите **значки**, а затем выберите **стрелку "Далее"**.  

    ![Shapes (Фигуры) на вкладке Insert (Вставка)](./media/add-screen-context-variables/add-next-arrow.png)

2. Необязательно: переместите стрелку в правый нижний угол экрана.

3. С помощью стрелки все еще выбран, выберите **действие** , а затем выберите **Navigate**.

    Для свойства **[OnSelect](controls/properties-core.md)** стрелки будет автоматически выбрана функция **Navigate** (Навигация).

    ![Для свойства OnSelect выбрана функция Navigate (Навигация)](./media/add-screen-context-variables/onselect-default.png)

    Когда пользователь выбирает стрелку, **целевой** отчетливее экрана.

4. На экране **Target** добавьте элемент **Back arrow** (Стрелка "Назад") и установите для ее свойства **[OnSelect](controls/properties-core.md)** следующую формулу:

    `Navigate(Source, ScreenTransition.Fade)`

5. Удерживая нажатой клавишу Alt, переключение между экранами, щелкнув стрелку на каждом экране.

## <a name="more-information"></a>Дополнительные сведения

[Ссылки на элемент управления экрана](controls/control-screen.md)