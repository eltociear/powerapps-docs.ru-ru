---
title: Настройка карточки в приложении Canvas | Документация Майкрософт
description: Изменение элемента управления по умолчанию, который отображается в карточке в форме сведений или редактирования в приложении Canvas
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/18/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5bcf1515f72bdce0872f91c64b5ac4fe5028ee2c
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "71985925"
---
# <a name="customize-a-card-in-a-canvas-app"></a>Настройка карточки в приложении Canvas

Выполните основную настройку (без разблокировки карточки), например измените элемент управления. Выполните дополнительную настройку, разблокировав карточку и, например, добавив элемент управления, недоступный по умолчанию для этой карточки.

Общие сведения см. в статье [Общие сведения о карточках данных](working-with-cards.md).

## <a name="prerequisites"></a>Технические условия

- Узнайте, как [добавлять и настраивать элементы управления](add-configure-controls.md).
- Вы можете ознакомиться с этим разделом только по основным понятиям или выполнить шаг по шагам, если сначала выполнить процедуры, описанные в следующих разделах:

    1. [Создание приложения](data-platform-create-app.md)
    1. [Настройка коллекции](customize-layout-sharepoint.md)
    1. [Настройка форм](customize-forms-sharepoint.md)

## <a name="customize-a-locked-card"></a>Настройка заблокированной карточки

В этой процедуре вы замените элемент управления для **[ввода текста](controls/control-text-input.md)** на **[Slider] (Controls/Control-Slider. md** , не разблокируя карту.

1. В созданном и настроенном приложении выберите **EditForm1** на левой панели навигации, а затем выберите **изменить поля** на вкладке **Свойства** правой панели.

1. В списке полей щелкните стрелку вниз рядом с полем **число сотрудников**, а затем откройте список под **элементом тип элемента управления**.

    > [!div class="mx-imgBorder"]
    > ![раскрывающийся список параметров для карточки номера](./media/customize-card/card-selector.png)

1. Выберите **изменить ползунок**.

    Изменения отразятся на экране.

    > [!div class="mx-imgBorder"]
    > ![EditForm1 с элементом управления "ползунок"](./media/customize-card/add-slider.png)

## <a name="unlock-and-customize-a-card"></a>Разблокировка и настройка карточки

В этой процедуре вы разблокируете карточку и обновляете свойство **Max** только что добавленного элемента управления **Slider** .

1. В **EditForm1**выберите элемент управления **Slider** в карточке **число сотрудников** .

    > [!div class="mx-imgBorder"]
    > ![выберите ползунок](./media/customize-card/select-slider.png)

1. На вкладке **Дополнительно** на правой панели щелкните значок замка, чтобы разблокировать карточку.

    > [!div class="mx-imgBorder"]
    > ![разблокировать карту](./media/customize-card/lock-icon.png)

1. Установите свойство **Max** элемента управления **Slider** в значение 10 000.

    > [!div class="mx-imgBorder"]
    > ![свойство Max на вкладке "Дополнительно"](./media/customize-card/max-property.png)

    Элемент управления " **ползунок** " показывает более точное значение.

    > [!div class="mx-imgBorder"]
    > диапазон ползунка ![: 0-10000](./media/customize-card/final-slider.png)

## <a name="next-steps"></a>Дальнейшие действия

Теперь, когда у вас есть общее представление о том, как создавать приложения и настраивать коллекции, формы и карточки, вы можете [разработать собственное приложение с нуля](data-platform-create-app-scratch.md).