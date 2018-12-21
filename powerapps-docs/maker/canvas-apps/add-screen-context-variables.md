---
title: Добавление и переключение экранов в приложении на основе холста | Документы Майкрософт
description: Добавление экрана в приложение на основе холста и переход между экранами с помощью стрелок вперед и назад в PowerApps
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 07/10/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c0c4e14b2f4a7db81dcdd51dd75a45d3cac4da68
ms.sourcegitcommit: 6851486b8a44d76b6d87837952b7a7f38a8752b6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2018
ms.locfileid: "53570358"
---
# <a name="add-a-screen-to-a-canvas-app-and-navigate-between-screens"></a>Добавление и переключение экранов в приложении на основе холста

Создайте приложение на основе холста с несколькими экранами и предоставьте пользователям возможность перемещаться между ними.

## <a name="prerequisites"></a>Технические условия

* Узнайте, как [настроить элемент управления](add-configure-controls.md).
* Создайте или откройте приложение.

## <a name="add-and-rename-a-screen"></a>Добавление и переименование экрана

1. На вкладке **Home** (Главная) щелкните или нажмите **New screen** (Создать экран).

    ![Команда добавления экрана на вкладке Home (Главная)](./media/add-screen-context-variables/add-screen.png)

2. На панели справа щелкните имя экрана (прямо над вкладкой **Свойства**) и введите новое имя **источника**.

    ![Переименование экрана по умолчанию](./media/add-screen-context-variables/name-source-screen.png)

3. Добавьте еще один экран под названием **Target** (Назначение).

    ![Два экрана на панели навигации слева](./media/add-screen-context-variables/two-screens-in-nav.png)

## <a name="add-navigation"></a>Добавление элементов навигации
1. Выбрав экран **Source**, откройте вкладку **Insert** (Вставка), щелкните или нажмите **Icons** (Значки), а затем — **Next arrow** (Стрелка "Далее").  

    ![Shapes (Фигуры) на вкладке Insert (Вставка)](./media/add-screen-context-variables/add-next-arrow.png)

2. Необязательно: переместите стрелку в правый нижний угол экрана.

3. Выбрав стрелку, откройте вкладку **Action** (Действие) и щелкните или нажмите **Navigate** (Навигация).

    Для свойства **[OnSelect](controls/properties-core.md)** стрелки будет автоматически выбрана функция **Navigate** (Навигация).  

    ![Для свойства OnSelect выбрана функция Navigate (Навигация)](./media/add-screen-context-variables/onselect-default.png)

    Когда пользователь щелкнет стрелку или нажмет на нее, появится экран **Target**.

4. На экране **Target** добавьте элемент **Back arrow** (Стрелка "Назад") и установите для ее свойства **[OnSelect](controls/properties-core.md)** следующую формулу:
   <br>**Navigate(Source, ScreenTransition.Fade)**

5. Откройте режим предварительного просмотра (![](./media/add-screen-context-variables/preview.png) или клавиша F5) и проверьте, как работает перемещение между экранами с помощью добавленных вами стрелок.

6. Чтобы вернуться в рабочую область по умолчанию, нажмите клавишу **ESC**.
