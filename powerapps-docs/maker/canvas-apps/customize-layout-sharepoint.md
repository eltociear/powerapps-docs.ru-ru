---
title: Учебник по настройке коллекции | Документы Майкрософт
description: В этом учебнике вы настроите окно обзора по умолчанию, включая коллекцию, для приложения, создаваемого в PowerApps.
services: ''
suite: powerapps
documentationcenter: na
author: AFTOwen
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/11/2018
ms.author: anneta
ms.openlocfilehash: 30ec6be11b40e01dddfe09cf0ac8af0ed3a8a437
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="tutorial-customize-a-gallery-in-powerapps"></a>Учебник. Настройка коллекции в PowerApps
В этом учебнике вы настроите окно обзора по умолчанию, включая коллекцию, для приложения, создаваемого в PowerApps. Вы можете управлять данными с помощью приложения по умолчанию, не настраивая его, однако с ним будет гораздо проще и эффективнее работать, если внести следующие изменения:

> [!div class="checklist"]
> * изменить макета;
> * Изменение отображаемых данных
> * настроить фильтрацию и сортировку столбцов;
> * протестировать фильтрацию и сортировку;
> * изменить заголовок;
> * включить полосу прокрутки.

В этом учебнике рассматривается приложение, создаваемое на основе [Common Data Service для приложений](../common-data-service/data-platform-intro.md), однако те же принципы относятся к приложениям, создаваемым на основе SharePoint, Excel и других источников данных. 

Если у вас нет лицензии на PowerApps, вы можете [зарегистрироваться для получения бесплатной версии](../signup-for-powerapps.md).

## <a name="prerequisites"></a>Технические условия
Прежде чем приступать к работе с этим учебником, [создайте приложение](data-platform-create-app.md) на основе Common Data Service для приложений.

## <a name="open-the-generated-app"></a>Открытие созданного приложения
1. Войдите в [PowerApps](https://web.powerapps.com) и выберите элемент **Приложения** у левого края экрана.

    ![Домашняя страница PowerApps](./media/customize-layout-sharepoint/sign-in.png)

1. Найдите созданное приложение и нажмите значок многоточия (**...**) у правого края экрана.

    ![Список приложений](./media/customize-layout-sharepoint/open-for-edit.png)

1. В появившемся меню выберите команду изменения приложения. 

## <a name="customize-the-gallery"></a>Настройка коллекции
1. В окне обзора выберите любой элемент, кроме первого, в списке учетных записей.

    В этом шаге выбирается элемент управления **Коллекция**, который отображает список учетных записей.

    ![Выбранная коллекция](./media/customize-layout-sharepoint/select-gallery.png)

1. В правой области нажмите **Учетные записи** справа от надписи **Данные**.

    ![Открытие области **Данные**](./media/customize-layout-sharepoint/open-data-pane.png)

1. В области **Данные** нажмите стрелку вниз в разделе **Макет**, чтобы открыть список вариантов.

    ![Открытие вариантов макета](./media/customize-layout-sharepoint/show-layouts.png)

1. В списке выберите вариант, содержащий только заголовок.

    ![Выбор макета, содержащего только заголовок](./media/customize-layout-sharepoint/choose-layout.png)

1. В области **Данные** нажмите стрелку вниз, чтобы открыть список вариантов заголовка.

    ![Выбор макета, содержащего только заголовок](./media/customize-layout-sharepoint/show-title-options.png)

1. В списке вариантов выберите окно **name**, чтобы соответствующие данные отображались в элементе управления **Коллекция**.

    ![Окончательная версия коллекции](./media/customize-layout-sharepoint/final-gallery.png)


## <a name="set-the-sort-and-search-columns"></a>Настройка столбцов для поиска и сортировки
1. Выберите элемент управления **Коллекция**, как описано в предыдущем разделе.

    ![Выбор коллекции](./media/customize-layout-sharepoint/select-gallery-title.png)

2. Убедитесь, что возле левого верхнего угла в списке свойств отображается **Items**.

    ![Свойство Items](./media/customize-layout-sharepoint/items-property.png)

    Значение этого свойства отображается в строке формул и определяет не только источник данных для коллекции, но и столбцы для фильтрации и сортировки.

1. В строке формул замените оба экземпляра **emailaddress1** на **name**, оставив двойные кавычки.

    Формула должна выглядеть так, как показано в следующем примере:

    ![Формула для свойства Items](./media/customize-layout-sharepoint/items-value.png)

    Первый экземпляр **name** указывает, что пользователь может фильтровать список. При этом в нем будут отображаться только учетные записи, в именах которых содержится текст, введенный пользователем в поле поиска. Второй экземпляр **name** указывает, что пользователь может сортировать список по именам учетных записей в алфавитном порядке. Дополнительные сведения об этих и других функциях приведены в [справочнике формул](formula-reference.md).

## <a name="test-sorting-and-searching"></a>Тестирование функций поиска и сортировки
1. Откройте режим предварительного просмотра, нажав клавишу F5 (или нажав кнопку воспроизведения в правом верхнем углу).

    ![Открытие режима предварительного просмотра](./media/customize-layout-sharepoint/open-preview.png)

1. В правом верхнем углу окна обзора нажмите значок сортировки один или несколько раз для изменения порядка сортировки по возрастанию или по убыванию.

    ![Тестирование работы значка сортировки](./media/customize-layout-sharepoint/sort-button.png)

1. В поле поиска введите букву **k**, чтобы просмотреть только те учетные записи, в именах которых она есть.

    ![Тестирование строки поиска](./media/customize-layout-sharepoint/test-filter.png)

1. Удалите весь текст в строке поиска, а затем закройте режим предварительного просмотра, нажав клавишу ESC (либо щелкните значок закрытия или коснитесь его *в* строке заголовка PowerApps).

## <a name="change-the-title-of-the-screen"></a>Изменение заголовка экрана
1. Щелкните заголовок экрана или коснитесь его.

    ![Выбор заголовка экрана](./media/customize-layout-sharepoint/select-title.png)

1. Убедитесь в том, что в списке свойств отображается **Text**, а затем введите слово **Обзор**, заключенное в двойные кавычки, в строке формул.

    ![Обновление заголовка экрана](./media/customize-layout-sharepoint/change-screen-title.png)

    Изменения отразятся на экране.

    ![Новый заголовок экрана](./media/customize-layout-sharepoint/new-screen-title.png)

## <a name="show-a-scroll-bar"></a>Включение полосы прокрутки
Если на устройствах пользователей может не быть сенсорных экранов или колесика мыши, настройте элемент управления **Коллекция** так, чтобы при наведении на него указателя мыши появлялась полоса прокрутки. Благодаря этому пользователи смогут просматривать все учетные записи, даже если они не помещаются на экране одновременно.

1. Выберите элемент управления **Коллекция**, как описано в первой процедуре.

    ![Выбор коллекции](./media/customize-layout-sharepoint/select-gallery-sorted.png)

1. На вкладке **Коллекция** нажмите **Показывать полосу прокрутки** и убедитесь в том, что значение этого свойства поменялось на **true**. 

    ![Показывать полосу прокрутки](./media/customize-layout-sharepoint/show-scrollbar.png)

## <a name="next-steps"></a>Дальнейшие действия
В этом учебнике вы настроили элемент управления **Коллекция** и заголовок окна обзора по умолчанию для созданного приложения. Вы также можете настроить окна по умолчанию для отображения подробных сведений и создания или обновления учетных записей. Эти окна содержат элемент управления **Форма просмотра** и элемент управления **Форма редактирования**. Вы можете изменить, помимо прочего, отображаемые в них типы данных и порядок их отображения.

> [!div class="nextstepaction"]
> [Настройка форм](customize-forms-sharepoint.md)