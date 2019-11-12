---
title: Создание с нуля приложения на основе холста с помощью Common Data Service | Документация Майкрософт
description: Создание в PowerApps приложения на основе холста для добавления, обновления и удаления записей в Common Data Service.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/21/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: bec8524ac6afc265eba5d9a6edf381c5ebf2c340
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73540369"
ms.PowerAppsDecimalTransform: true
---
# <a name="create-a-canvas-app-from-scratch-using-common-data-service"></a>Создание с нуля приложения на основе холста с помощью Common Data Service

Вы можете создать приложение на основе холста для управления данными, хранящимися в службе Common Data Service, с использованием стандартных (встроенных) и (или) настраиваемых (созданных вашей организацией) сущностей.

При создании приложения на основе службы Common Data Service не требуется создавать подключение из PowerApps, как в случае с источниками данных, например SharePoint, Dynamics 365 и Salesforce. Требуется только указать сущности, которые необходимо отобразить или которыми необходимо управлять в приложении.

## <a name="prerequisites"></a>Технические условия

- Прежде чем создавать приложение с нуля, ознакомьтесь с основами PowerApps, [создав приложение](data-platform-create-app.md), а затем настроив его [коллекцию](customize-layout-sharepoint.md), [формы](customize-forms-sharepoint.md) и [карточки](customize-card.md).
- [Перейдите в среду](working-with-environments.md), в которой был создан образец базы данных. Если у вас есть соответствующая лицензия, вы можете [создать среду](../../administrator/create-environment.md) с этой целью.
- Для создания приложения вам должна быть назначена роль безопасности [Создатель среды](https://docs.microsoft.com/power-platform/admin/database-security#predefined-security-roles).

## <a name="open-a-blank-app"></a>Пустое приложение

1. Войдите в [PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

1. В разделе **Создание собственного приложения** выберите **Приложение на основе холста с нуля**.

    ![Плитка пустого приложения](./media/data-platform-create-app-scratch/blank-app.png)

1. Укажите имя приложения, выберите **Телефон**, а затем выберите **Создать**.

    Вы можете с нуля создавать приложения для планшетов, но в этом разделе показан процесс создания приложения для телефонов.

## <a name="specify-an-entity"></a>Указание сущности

1. В центре экрана выберите **подключение к данным**.

1. На панели **Данные** выберите **Common Data Service**, установите флажок **Учетные записи**, а затем выберите **Подключить**.

1. Закройте область **Данные**, нажав значок закрытия в правом верхнем углу.

## <a name="add-a-list-screen"></a>Добавление окна списка

1. На вкладке **Главная** щелкните стрелку вниз рядом с элементом **Новый экран**, а затем выберите **Список**.

    ![Добавление окна списка](./media/data-platform-create-app-scratch/list-screen.png)

1. На панели навигации слева выберите пункт **BrowseGallery1**, а затем в качестве значения свойства **Items** укажите следующую формулу:

    `SortByColumns(Search(Accounts; TextSearchBox1.Text; "name"); "name"; If(SortDescending1; SortOrder.Descending; SortOrder.Ascending))`

    Согласно этой формуле:

   - в коллекции должны отображаться данные из сущности **Учетные записи**;
   - данные должны сортироваться в порядке возрастания, пока пользователь не изменит порядок сортировки, нажав кнопку сортировки;
   - если пользователь введет или вставит в поле поиска один или несколько символов (**TextSearchBox1**), в списке будут отображаться только те учетные записи, поле **имени** которых содержит эти символы.

     Вы можете использовать [эти и многие другие функции](formula-reference.md) для настройки внешнего вида и поведения приложения.

     ![Задание свойства Items коллекции](./media/data-platform-create-app-scratch/gallery-items.png)

1. Настройте макет коллекции так, чтобы отображалось только имя каждой учетной записи, а заголовок настройте так, чтобы отображалось слово **Обзор**, как описано в статье [Настройка коллекции](customize-layout-sharepoint.md).

    ![Экран обзора](./media/data-platform-create-app-scratch/final-browse.png)

1. На панели навигации слева наведите курсор на окно **Screen1**, нажмите на кнопку с многоточием (…), а затем выберите **Удалить**.

1. На панели навигации слева наведите курсор на окно **Screen2**, нажмите на кнопку с многоточием (…), а затем выберите **Переименовать**.

1. Введите или вставьте слово **BrowseScreen**, а затем измените имя коллекции в этом окне на **BrowseGallery**.

    ![Переименование окна обзора, коллекция](./media/data-platform-create-app-scratch/rename-browse.png)

## <a name="add-a-form-screen"></a>Добавление окна формы

1. Повторите первое действие из предыдущей процедуры, но добавьте окно **формы** вместо окна **списка**.

1. На вкладке **Дополнительно** в области справа присвойте свойству **DataSource** формы значение **Учетные записи**, а ее свойству **Item** — значение **BrowseGallery.Selected**.

    ![Задание свойств Datasource и Item формы](./media/data-platform-create-app-scratch/form-datasource.png)

1. На вкладке **Свойства** правой панели выберите **изменить поля** , чтобы открыть панель **поля** .

1. Выберите **Добавить поле**, а затем установите флажки для этих полей:

    - **Имя учетной записи**
    - **Адрес 1: улица 1**
    - **Адрес 1: город**
    - **Адрес 1. почтовый индекс**
    - **Количество сотрудников**
    - **Годовой доход**

    > [!NOTE]
    > За пределами этого сценария можно создать настраиваемое поле, выбрав **новое поле**, указав необходимые сведения, а затем выбрав **Готово**. Дополнительные сведения: [Создание поля](../common-data-service/create-edit-field-portal.md#create-a-field).<br><br>![](media/data-platform-create-app-scratch/choose-or-add-fields.png "Select and add a field")

1. Нажмите кнопку **Добавить**.

1. Задайте для свойства **Text** заголовка значение **Создание или изменение**.

    Изменения отразятся на экране.

    ![Задание свойств Datasource и Item формы](./media/data-platform-create-app-scratch/field-list.png)

1. Измените имя экрана на **FormScreen**.

## <a name="configure-icons"></a>Настройка значков

1. Задайте в качестве значения свойства **OnSelect** круглого значка, расположенного в верхней части окна **BrowseScreen**, следующую формулу:

    `Refresh(Accounts)`

    ![Значок обновления](./media/data-platform-create-app-scratch/refresh-icon.png)

1. Задайте в качестве значения свойства **OnSelect** значка плюса следующую формулу:

    `NewForm(EditForm1);; Navigate(FormScreen; ScreenTransition.None)`

    ![Значок добавления](./media/data-platform-create-app-scratch/plus-icon.png)

1. Задайте в качестве значения свойства **OnSelect** первой стрелки, направленной вправо, следующую формулу:

    `EditForm(EditForm1);; Navigate(FormScreen; ScreenTransition.None)`

    ![Значок "Далее"](./media/data-platform-create-app-scratch/next-icon.png)

1. В окне **FormScreen** задайте в качестве значения свойства **OnSelect** значка отмены следующую формулу:

    `ResetForm(EditForm1);;Navigate(BrowseScreen; ScreenTransition.None)`

    ![Значок отмены](./media/data-platform-create-app-scratch/cancel-icon.png)

1. Задайте в качестве значения свойства **OnSelect** значка флажка следующую формулу:

    `SubmitForm(EditForm1);; Navigate(BrowseScreen; ScreenTransition.None)`

    ![Значок с галочкой](./media/data-platform-create-app-scratch/checkmark-icon.png)

1. На вкладке **Вставка** выберите **Значки**, а затем — значок **мусорной корзины**.

1. Задайте для свойства **Color** значка **Корзина** значение **White**, а в качестве значения свойства **OnSelect** укажите следующую формулу:

    `Remove(Accounts; BrowseGallery.Selected);; Navigate(BrowseScreen; ScreenTransition.None)`

    ![Значок корзины](./media/data-platform-create-app-scratch/trash-icon.png)

## <a name="test-the-app"></a>Тестирование приложения

1. На панели навигации слева выберите окно **BrowseScreen**, а затем откройте режим предварительного просмотра, нажав клавишу F5 (либо нажав значок воспроизведения в правом верхнем углу).

    ![Открытие режима предварительного просмотра](./media/data-platform-create-app-scratch/open-preview.png)

1. Переключитесь между порядками сортировки по возрастанию и по убыванию и отфильтруйте список, введя один или несколько символов, входящих в имя учетной записи.

1. Добавьте учетную запись, измените ее, начните обновлять ее, но отмените изменения, а затем удалите учетную запись.

## <a name="next-steps"></a>Дальнейшие действия

- [Связать это приложение с решением](add-app-solution.md), чтобы можно было, например, развернуть его в другой среде или опубликовать его в AppSource.
- [Откройте один или несколько примеров приложений](open-and-run-a-sample-app.md) и ознакомьтесь с различными типами приложений, которые можно создавать.
