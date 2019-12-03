---
title: Настройка формы в приложении на основе холста | Документы Майкрософт
description: В Power Apps укажите, какие данные следует отображать в форме Canvas-App, в которой они должны отображаться и в каких элементах управления.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/17/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6732dabea803cd7680ef618e4e8d1c4e88f7afe5
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678633"
---
# <a name="customize-a-canvas-app-form-in-powerapps"></a>Настройка формы в приложении на основе холста в PowerApps

В приложении на основе холста вы можете настроить элементы управления **Форма отображения** и **Форма редактирования** для показа наиболее важных данных в интуитивно понятном порядке. Это сделает их более понятными пользователям и упростит их редактирование.

Каждая форма содержит одну или несколько карточек, в которых отображаются данные из определенного столбца в источнике данных. Следуя инструкциям в этой статье, вы научитесь указывать, какие карточки должны отображаться в форме, перемещать карточки вверх и вниз в пределах формы.

Если вы не знакомы с Canvas-PPS, см. статью [что такое приложения Canvas?](getting-started.md).

## <a name="prerequisites"></a>Технические условия

[Создайте приложение](data-platform-create-app.md) из Common Data Service, а затем [настройте коллекцию](customize-layout-sharepoint.md) в этом приложении.

## <a name="show-and-hide-cards"></a>Отображение и скрытие карточек

1. Войдите в [PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), а затем Откройте созданное и настроенное приложение.

1. В левой панели навигации введите или вставьте **D** в строке поиска, чтобы отфильтровать список элементов, а затем выберите **DetailForm1**.

    > [!div class="mx-imgBorder"]
    > ![экран "Выбор сведений"](./media/customize-forms-sharepoint/select-detailform.png)

1. На вкладке **Свойства** на панели справа выберите **Изменить поля**, чтобы открыть панель **Поля**.

    > [!div class="mx-imgBorder"]
    > ![открыть область полей](./media/customize-forms-sharepoint/edit-fields.png)

1. Скройте поле, например **Описание**, наведя на него указатель мыши, нажав кнопку с многоточием (...), а затем выбрав **Удалить**.

    > [!div class="mx-imgBorder"]
    > ![список полей](./media/customize-forms-sharepoint/hide-fields.png)

1. Чтобы отобразить поле, выберите **Добавить поле**, введите или вставьте первые несколько букв имени поля в поле поиска, установите флажок поля и нажмите кнопку **Добавить**.

    > [!div class="mx-imgBorder"]
    > ![список полей](./media/customize-forms-sharepoint/show-field.png)

## <a name="reorder-the-cards"></a>Изменение порядка карточек

1. В области **поля** перетащите поле **имя учетной записи** в верхнюю часть списка полей.

    Карты в **DetailForm1** отражая изменение.

    > [!div class="mx-imgBorder"]
    > ![переупорядоченные карточки](./media/customize-forms-sharepoint/reordered-card.png)

1. используемых Переупорядочивайте другие карточки в следующую последовательность:

    - Имя учетной записи
    - Количество сотрудников
    - Годовой доход
    - Основной телефон
    - Адрес 1: улица 1
    - Адрес 1: улица 2
    - Адрес 1: город
    - Адрес 1: почтовый индекс

1. На панели навигации слева введите или вставьте **ED** в строке поиска, а затем выберите **EditForm1** , чтобы выбрать его.

1. Повторите действия, описанные в предыдущей процедуре, и данное действие, чтобы поля в **EditForm1** соответствовали полям в **DetailForm1**.

## <a name="run-the-app"></a>Запуск приложения

1. На панели навигации слева введите или вставьте **br** в строке поиска, а затем выберите **BrowseScreen1** , чтобы выбрать его.

1. Откройте режим предварительного просмотра, нажав клавишу F5 (или выбрав значок **предварительного просмотра** в правом верхнем углу).

    > [!div class="mx-imgBorder"]
    > значок предварительного просмотра ![](./media/customize-forms-sharepoint/open-preview.png)

1. В правом верхнем углу щелкните значок "плюс", чтобы добавить запись в **EditScreen1**.

    > [!div class="mx-imgBorder"]
    > ![добавить](./media/customize-forms-sharepoint/add-record.png) записи

1. Добавьте необходимые данные, а затем щелкните значок флажка в правом верхнем углу, чтобы сохранить изменения и вернуться в **BrowseScreen1**.

    > [!div class="mx-imgBorder"]
    > ![сохранить](./media/customize-forms-sharepoint/save-record.png) записи

1. Выберите стрелку для элемента, который вы только что создали, чтобы отобразить сведения об этом элементе в **DetailScreen1**.

    > [!div class="mx-imgBorder"]
    > ![стрелка вправо](./media/customize-forms-sharepoint/right-arrow.png)

1. В правом верхнем углу страницы щелкните значок редактирования, чтобы обновить запись в **EditScreen1**.

    > [!div class="mx-imgBorder"]
    > ![изменить](./media/customize-forms-sharepoint/edit-record.png) записи

1. Измените данные в одном или нескольких полях, а затем установите флажок в правом верхнем углу, чтобы сохранить изменения и вернуться к **DetailScreen1**.

    > [!div class="mx-imgBorder"]
    > ![сохранить изменения](./media/customize-forms-sharepoint/save-record.png)

1. В правом верхнем углу экрана щелкните значок Корзина-можно удалить только что обновленную запись и вернуться к **BrowseScreen1**.

    > [!div class="mx-imgBorder"]
    > ![удалить запись](./media/customize-forms-sharepoint/delete-record.png)

1. Закройте режим предварительного просмотра, нажав клавишу ESC (или щелкнув значок Закрыть в левом верхнем углу).

## <a name="next-steps"></a>Дальнейшие действия

- [Сохраните и опубликуйте](save-publish-app.md) приложение.
- [Настройте карточку](customize-card.md) в приложении.