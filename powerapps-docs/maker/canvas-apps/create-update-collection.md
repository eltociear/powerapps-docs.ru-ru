---
title: Создание и обновление коллекции в приложении Canvas | Документация Майкрософт
description: Создание коллекции в приложении Canvas, добавление элементов в коллекцию и удаление одного или всех элементов из него.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/28/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 375c4f19ed7715eed662c8456c539d5590c9f1ec
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "71993211"
---
# <a name="create-and-update-a-collection-in-a-canvas-app"></a>Создание и обновление коллекции в приложении Canvas

Используйте коллекцию для хранения данных, которыми могут управлять пользователи в приложении. Коллекция — это группа элементов, которые похожи, например продукты в списке продуктов. Дополнительные сведения о различных типах переменных, таких как коллекции: [Общие сведения о переменных приложения Canvas](working-with-variables.md).

## <a name="prerequisites"></a>Технические условия

- [Зарегистрируйтесь](../signup-for-powerapps.md) в PowerApps, а затем [войдите в систему](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), указав учетные данные, использованные при регистрации.
- Создайте приложение в PowerApps или откройте уже существующее.
- Узнайте, как [настроить элемент управления](add-configure-controls.md) в PowerApps.

## <a name="create-a-multicolumn-collection"></a>Создание многостолбцовой коллекции

1. В PowerApps Studio добавьте элемент управления **Ввод текста** .

    ![Вставка элемента управления вводом текста](./media/create-update-collection/add-textbox.png)

1. Переименуйте элемент управления, щелкнув многоточие в левой области навигации, выбрав **Переименовать**, а затем введя **ProductName**.

    ![Переименование элемента управления](./media/create-update-collection/rename-textbox.png)

1. Добавьте элемент управления "раскрывающийся **список** ".

    ![Добавить раскрывающийся список](./media/create-update-collection/add-dropdown.png)

1. Переименуйте **раскрывающиеся** **цвета**элемента управления и убедитесь, что свойство **Items** выбрано в списке свойств.

    ![Свойство Items](./media/create-update-collection/items-property.png)

1. В строке формул замените **дропдовнсампле** следующим выражением:

    `["Red","Green","Blue"]`

1. Добавьте элемент управления **Button** , присвойте его свойству **Text** значение **Add**и задайте для его свойства **OnSelect** значение этой формулы:

    ```powerapps-dot
    Collect(
        ProductList,
        {
            Product: ProductName.Text,
            Color: Colors.Selected.Value
        }
    )
    ```

1. Нажмите клавишу F5, введите текст в поле " **ProductName**", выберите нужный параметр в списке **цветов**и нажмите кнопку **добавить**.

    ![Предварительный просмотр приложения](./media/create-update-collection/preview-add.png)

1. Повторите предыдущий шаг по крайней мере два раза, а затем нажмите клавишу ESC.

1. В меню **файл** выберите **коллекции** , чтобы отобразить созданную коллекцию.

    ![Отобразить коллекцию](./media/create-update-collection/show-collection.png)

## <a name="show-a-collection"></a>Отображение коллекции

1. Добавление вертикального элемента управления " **коллекция** ".

    ![Добавление вертикальной коллекции](./media/create-update-collection/add-gallery.png)

1. Присвойте свойству **Items** коллекции значение **ProductList**.

1. В области **данных** задайте для поля подзаголовок значение **Цвет**и задайте для поля Заголовок значение **Product**.

    ![Задайте свойство Items коллекции и измените поля, которые она показывает.](./media/create-update-collection/configure-gallery.png)

1. Закройте панель **данных** , выберите коллекцию, а затем задайте в поле **макета** **заголовок и подзаголовок**.

    ![Задайте свойство Items коллекции и измените поля, которые она показывает.](./media/create-update-collection/change-layout.png)

    Ваш экран напоминает следующий пример:

    ![Пример первого экрана](./media/create-update-collection/screen-example1.png)

## <a name="remove-one-or-all-items"></a>Удаление одного или всех элементов

1. Выберите шаблон коллекции, щелкнув или коснувшись в нижней части коллекции, а затем щелкнув значок карандаша рядом с верхним левым углом.

    ![Выбор шаблона коллекции](./media/create-update-collection/select-template.png)

1. Добавьте значок **корзины** в шаблон коллекции.

    ![Добавить значок корзины](./media/create-update-collection/trash-icon.png)

1. Задайте в качестве значения свойства " **OnSelect** " значка следующую формулу:

    `Remove(ProductList, ThisItem)`

1. За пределами коллекции добавьте кнопку, задайте для ее свойства **Text** значение **"Clear"** и задайте для его свойства **OnSelect** значение этой формулы:

    `Clear(ProductList)`

1. Удерживая нажатой клавишу Alt, выберите значок **корзины** для элемента, чтобы удалить его из коллекции, или нажмите кнопку **clear (очистить** ), чтобы удалить все элементы из коллекции.

## <a name="put-a-sharepoint-list-into-a-collection"></a>Помещение списка SharePoint в коллекцию

1. [Создайте подключение к списку SharePoint](connections/connection-sharepoint-online.md#create-a-connection).

1. Добавьте кнопку и установите для ее свойства **[OnSelect](controls/properties-core.md)** эту функцию, заменив *ListName* именем вашего списка SharePoint:<br>

    `Collect(MySPCollection, ListName)`

    Эта функция создает коллекцию с именем **MySPCollection**, которая содержит те же данные, что и ваш список SharePoint.

1. Удерживая нажатой клавишу ALT, нажмите на эту кнопку.

1. используемых Чтобы просмотреть созданную коллекцию, выберите **коллекции** в меню **файл** .

Сведения о том, как отображать данные из списка SharePoint (например, даты, варианты выбора и людей) в коллекции: [Отображение столбцов списка в коллекции](connections/connection-sharepoint-online.md#show-list-columns-in-a-gallery). Сведения о том, как отображать данные в форме (с раскрывающимися списками, выбора даты и лицами, которые выбираются людьми): [Изменение формы и отображение элементов управления формы](controls/control-form-detail.md).

## <a name="next-steps"></a>Дальнейшие действия

- Ознакомьтесь с [справочным разделом](functions/function-clear-collect-clearcollect.md) по функции " **собранные** ".
- Сведения о формировании данных в коллекции с помощью функций [AddColumns, дропколумнс, RenameColumns и шовколумнс](functions/function-table-shaping.md) .
