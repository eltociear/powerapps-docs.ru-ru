---
title: Создание и обновление коллекции в приложение на основе холста | Документация Майкрософт
description: Создание коллекции в приложение на основе холста, добавление элементов в коллекцию и удалять одну или все элементы
author: aftowen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/28/2019
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: aca1b78262ac359689d66f687f902103740fa3a6
ms.sourcegitcommit: 826bde1eab3dd32d7bf9fa3f43ea069694845597
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/30/2019
ms.locfileid: "57800314"
---
# <a name="create-and-update-a-collection-in-a-canvas-app"></a>Создание и обновление коллекции в приложение на основе холста

Используйте коллекцию для хранения данных, пользователи могут управлять в вашем приложении. Коллекция — это группа элементов, находящихся как, например продукты в списке продуктов. Дополнительные сведения о различных типов переменных, такие как коллекции: [Общие сведения о переменных приложений на основе холста](working-with-variables.md).

## <a name="prerequisites"></a>Технические условия

- [Зарегистрируйтесь](../signup-for-powerapps.md) в PowerApps, а затем [войдите в систему](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), указав учетные данные, использованные при регистрации.
- Создайте приложение в PowerApps или откройте уже существующее.
- Узнайте, как [настроить элемент управления](add-configure-controls.md) в PowerApps.

## <a name="create-a-multicolumn-collection"></a>Создать коллекцию по нескольким столбцам

1. В PowerApps Studio, добавьте **ввода текста** элемента управления.

    ![Вставить элемент управления для ввода текста](./media/create-update-collection/add-textbox.png)

1. Переименуйте элемент управления, выбрав кнопку с многоточием в левой области навигации, выбрав **Переименовать**и введя **ProductName**.

    ![Переименование элемента управления](./media/create-update-collection/rename-textbox.png)

1. Добавить **раскрывающийся список** элемента управления.

    ![Добавление раскрывающегося списка](./media/create-update-collection/add-dropdown.png)

1. Переименуйте **раскрывающийся список** управления **цвета**и убедитесь, что **элементы** было выбрано свойство в списке свойств.

    ![Свойство Items](./media/create-update-collection/items-property.png)

1. В строке формул замените **DropDownSample** такое выражение:

    `["Red","Green","Blue"]`

1. Добавить **кнопку** , назначьте его **текст** свойства **«Добавить»** и задайте его **OnSelect** следующую формулу:

    ```powerapps-dot
    Collect(
        ProductList,
        {
            Product: ProductName.Text,
            Color: Colors.Selected.Value
        }
    )
    ```

1. Нажмите клавишу F5, введите текст в **ProductName**, выберите параметр в **цвета**, а затем выберите **добавить**.

    ![Предварительная версия приложения](./media/create-update-collection/preview-add.png)

1. Повторите предыдущий шаг, по крайней мере два раза и нажмите клавишу Esc.

1. На **файл** меню, выберите **коллекций** для отображения коллекции, что вы создали.

    ![Показать коллекции](./media/create-update-collection/show-collection.png)

## <a name="show-a-collection"></a>Показать коллекции

1. Добавьте вертикальный **коллекции** элемента управления.

    ![Добавление вертикальной коллекции](./media/create-update-collection/add-gallery.png)

1. Укажите для ее **элементы** свойства **ProductList**.

1. В **данных** области, значение поля подзаголовка **цвет**и установите в поле title **продукта**.

    ![Задайте свойства Items коллекции и измените поля, он показывает](./media/create-update-collection/configure-gallery.png)

1. Закрыть **данных** панели, а также набор **макета** поле **заголовок и подзаголовок**.

    ![Задайте свойства Items коллекции и измените поля, он показывает](./media/create-update-collection/change-layout.png)

    Экран выглядит следующим образом:

    ![Первый пример экрана](./media/create-update-collection/screen-example1.png)

## <a name="remove-one-or-all-items"></a>Удалить один или все элементы

1. Выберите шаблон коллекции, щелкните или коснитесь в нижней части галереи и затем нажав значок карандаша в левом верхнем углу.

    ![Выберите шаблон коллекции](./media/create-update-collection/select-template.png)

1. Добавить **корзины** значок шаблон коллекции.

    ![Добавить значок корзины](./media/create-update-collection/trash-icon.png)

1. Значок **OnSelect** следующую формулу:

    `Remove(ProductList, ThisItem)`

1. За пределами коллекции, добавьте кнопку, задайте его **текст** свойства **«Clear»** и задайте его **OnSelect** следующую формулу:

    `Clear(ProductList)`

1. Удерживая нажатой клавишу Alt, выберите **корзины** значок Удалить элемент из коллекции, или выберите элемент **Очистить** кнопку, чтобы удалить все элементы из коллекции.

## <a name="put-a-sharepoint-list-into-a-collection"></a>Помещение списка SharePoint в коллекцию

1. [Создайте подключение к списку SharePoint](connect-to-sharepoint.md).

1. Добавьте кнопку и установите для ее свойства **[OnSelect](controls/properties-core.md)** эту функцию, заменив *ListName* именем вашего списка SharePoint:<br>

    `Collect(MySPCollection, ListName)`

    Эта функция создает коллекцию с именем **MySPCollection**, которая содержит те же данные, что и ваш список SharePoint.

1. Удерживая нажатой клавишу ALT, нажмите на эту кнопку.

1. (необязательно) Для предварительного просмотра созданной коллекции, выберите **коллекций** на **файл** меню.

Сведения о том, как отображение данных из списка SharePoint (например, даты, варианты и пользователи) в коллекции: [Отображение данных в коллекции](connections/connection-sharepoint-online.md#show-data-in-a-gallery). Сведения о том, как отобразить данные в форме (с помощью раскрывающихся списков выбора даты и средства выбора данных сотрудников): [Изменение формы и элементы управления отображением формы](controls/control-form-detail.md).

## <a name="next-steps"></a>Дальнейшие действия

- Просмотрите [справочном разделе](functions/function-clear-collect-clearcollect.md) для **собирать** функции.
- Узнайте, как обработка данных в коллекции с помощью [AddColumns, DropColumns, RenameColumns и ShowColumns](functions/function-table-shaping.md) функции.
