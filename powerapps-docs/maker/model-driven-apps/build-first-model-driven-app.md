---
title: Создание первого управляемого моделью приложения с нуля с помощью Power Apps | Microsoft Docs
description: Узнайте, как создать простое управляемое моделью приложение.
documentationcenter: ''
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 02/05/2019
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4c404c8aab419fa4b0445a392d7440c2ab3f099b
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2020
ms.locfileid: "3136159"
---
# <a name="build-your-first-model-driven-app-from-scratch"></a>Создание первого управляемого моделью приложения с нуля
Разработка управляемого моделью приложения — это основанный на компонентах подход к разработке приложений. В этом разделе можно упростить создание управляемого моделью приложения с помощью одной из стандартных сущностей, доступных в среде Power Apps.

> [!TIP]
> Дополнительные сведения о создании управляемых моделью приложений см. в разделе [Общие сведения о компонентах управляемых моделью приложений](model-driven-app-components.md). 

## <a name="sign-in-to-power-apps"></a>Выполнить вход в Power Apps
Выполните вход в [Power Apps](https://make.powerapps.com/). Если у вас еще нет учетной записи [!INCLUDE [powerapps](../../includes/powerapps.md)], выберите **Начать работу бесплатно** на сайте. 

## <a name="create-your-model-driven-app"></a>Создание управляемого моделью приложения

1.    Выберите требуемую среду или перейдите в [центр администрирования Power Apps](https://admin.powerapps.com/), чтобы создать новую.

2.  На странице **Главная** выберите **Управляемое моделью приложение с нуля**.

    > [!div class="mx-imgBorder"] 
    > <img src="media/build-first-model-driven-app/start-from-blank-model-driven.png" alt="Start from blank model" height="429" width="673">

3.  Выберите **Создать**.

3.    На странице **Создать приложение** введите следующие сведения, затем нажмите **Готово**. 
  - **Имя**: введите имя приложения, например *Мое первое приложение*. 
  - **Уникальное имя**: по умолчанию уникальное имя использует имя, указанное в поле **Имя** без пробелов, перед которым указывается префикс издателя и символ подчеркивания (_). Например, *crecf_Myfirstapp*. Дополнительные сведения: [Изменение префикса издателя решения](../common-data-service/change-solution-publisher-prefix.md)
  - **Описание**: введите краткое описание того, что представляет из себя приложение или что оно делает, например *Это мое первое приложение*.
Сведения о дополнительных свойствах приложения см. в разделе [Создание приложения](create-edit-app.md#create-an-app).

  > [!div class="mx-imgBorder"] 
  > ![Создание нового приложения](media/create-new-app.png "Создание нового приложения")

## <a name="add-components-to-your-app"></a>Добавление компонентов в приложение
В конструкторе приложений добавьте компоненты в приложение.
1.    Выберите кнопку редактирования **Открыть конструктор карты сайта**, чтобы открыть конструктор карты сайта.

      > [!div class="mx-imgBorder"] 
      > ![Создание карты сайта](media/build-first-model-driven-app/new-sitemap.png "Конструктор карты сайта")

2.    В конструкторе карты сайта выберите **Создать дочернюю область**, в правой области перейдите на вкладку **Свойства**, и затем выберите следующие свойства.
  - **Тип**: сущность
  - **Сущность**: организация

    > [!div class="mx-imgBorder"] 
    > ![Добавление компонентов на карту сайта](media/build-first-model-driven-app/sitemap.png "Создать дочернюю область")

3.    Выберите **Сохранить и закрыть**.
4.    На холсте в конструкторе приложений выберите **Формы** и в право области в группе **Основные формы** выберите форму **Организация**.

      > [!div class="mx-imgBorder"] 
      > ![Основная форма организации](media/build-first-model-driven-app/main-form.png "Формы приложений")

5.    На холсте конструктора приложений выберите **Представления**, затем выберите представления **Активные организации**, **Все организации** и **Мои активные организации**.<!-- All checkbox seems to be selected by default -->

      > [!div class="mx-imgBorder"] 
      > ![Представления "Организация"](media/build-first-model-driven-app/views.png "Представления приложений")

6. На холсте конструктора приложений выберите **Диаграммы**, затем выберите диаграмму **Организации по отрасли**.
7. На панели инструментов конструктора приложений выберите **Сохранить**.

      > [!div class="mx-imgBorder"] 
      > ![Сохранение панели инструментов конструктора приложений](media/build-first-model-driven-app/app-designer-toolbar.png "Сохраните приложение")
 
<!-- ##  Validate your app
This step checks for component dependencies that are required for the app to work, but haven't yet been added to the app. 

1. On the app designer canvas, select the component that indicates a dependency, such as the **Forms** component. Then, on the right-pane select the **Required** tab, expand **Entity Dependencies** and then select all required dependencies. 

    ![Add dependencies](media/build-first-model-driven-app/resolve-dependencies.png)

2. Select **Add Dependencies**.
3. On the app designer toolbar, select **Save**.  -->

## <a name="publish-your-app"></a>Публикация приложения
На панели инструментов конструктора приложений выберите **Опубликовать**.

После публикации приложения оно будет готово к выполнению совместному использованию с другими пользователями.

  > [!div class="mx-imgBorder"] 
  > ![Простое приложение сущности организации](media/build-first-model-driven-app/accounts-quickstart-app.png "Выполнить приложение")

## <a name="next-steps"></a>Дальнейшие действия
В этом разделе вы создали простое управляемое моделью приложение. 
- Чтобы узнать, как выглядит ваше приложение при выполнении, см. раздел [Запуск приложения, управляемого моделью, на мобильном устройстве](../../user/run-app-client-model-driven.md).
- Чтобы узнать, как предоставить общий доступ к приложению, см. раздел [Общий доступ к управляемому моделью приложению](share-model-driven-app.md).
- Чтобы начать работу и получить дополнительные сведения о создании управляемых моделью приложений, см. раздел [Общие сведения о компонентах управляемых моделью приложений](model-driven-app-components.md).
