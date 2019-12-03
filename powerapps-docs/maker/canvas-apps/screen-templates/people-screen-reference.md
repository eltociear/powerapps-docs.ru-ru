---
title: Справочник по шаблонам экрана для людей | Документация Майкрософт
description: Сведения о том, как шаблон экрана "люди" для приложений Canvas работает в PowerApps
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 1/2/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ab4b7683d4ea550ebe5704cb7e5580ccbae48deb
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2019
ms.locfileid: "74674975"
ms.PowerAppsDecimalTransform: true
---
# <a name="reference-information-about-the-people-screen-template-for-canvas-apps"></a>Справочные сведения о шаблоне "люди — экран" для приложений Canvas

Для приложений Canvas в Power Apps необходимо понимать, как каждый важный элемент управления в шаблоне "люди" влияет на общую функциональность экрана по умолчанию. В этом подробном обзоре представлены формулы поведения и значения других свойств, определяющих реакцию элементов управления на вводимые пользователем данные. Подробное описание функциональных возможностей этого экрана по умолчанию см. в разделе [Общие сведения о людях](people-screen-overview.md).

В этом разделе описываются некоторые важные элементы управления и объясняются выражения или формулы, в которых задаются различные свойства (например, **элементы** и **OnSelect**) этих элементов управления.

* [Поле поиска текста](#text-search-box)
* [Галерея просмотра пользователей](#user-browse-gallery) (+ дочерние элементы управления)
* [Коллекция добавленных пользователей](#people-added-gallery) (+ дочерние элементы управления)

## <a name="prerequisite"></a>Необходимое условие

Знакомство с добавлением и настройкой экранов и других элементов управления при [создании приложения в PowerApps](../data-platform-create-app-scratch.md).

## <a name="text-search-box"></a>Текстовое поле поиска

![Элемент управления Текстсеарчбокс](media/people-screen/people-search-box.png)

Несколько других элементов управления взаимодействуют или имеют зависимость от текстового поля поиска:

* Если пользователь начинает вводить текст, **усербровсегаллери** станет видимым.
* Когда пользователь выбирает пользователя в **усербровсегаллери**, содержимое поиска сбрасывается.

## <a name="user-browse-gallery"></a>Галерея для просмотра пользователей

![Элемент управления Усербровсегаллери](media/people-screen/people-browse-gall.png)

* Свойство: **элементы**<br>
    Значение: логика для поиска пользователей, когда пользователь начинает вводить:
    
    ```powerapps-comma
    If( !IsBlank( Trim( TextSearchBox.Text ) ); 
        'Office365Users'.SearchUser(
            {
                searchTerm: Trim( TextSearchBox.Text ); 
                top: 15
            }
        )
    )
    ```
    
Элементы этой коллекции заполняются результатами поиска из операции [Office 365. сеарчусер](https://docs.microsoft.com/connectors/office365users/#searchuser) . Операция принимает текст в `Trim(TextSearchBox)` в качестве условия поиска и возвращает 15 лучших результатов, основанных на этом поиске. **Текстсеарчбокс** заключен в функцию `Trim()`, так как поиск пользователя в пробелах является недопустимым.

Операция `Office365Users.SearchUser` упаковывается в функцию `If(!IsBlank(Trim(TextSearchBox.Text)) ... )`, так как необходимо вызвать операцию только тогда, когда поле поиска содержит введенный пользователем текст. Это повышает производительность.

### <a name="userbrowsegallery-title-control"></a>Элемент управления "заголовок Усербровсегаллери"

![Элемент управления "заголовок Усербровсегаллери"](media/people-screen/people-browse-gall-title.png)

* Свойство: **текст**<br>Значение: `ThisItem.DisplayName`

  Отображает отображаемое имя пользователя из профиля Office 365.

* Свойство: **OnSelect**<br>
    Значение: код для добавления пользователя в коллекцию уровня приложения, а затем выберите пользователя:

    ```powerapps-comma
    Concurrent(
        Set( _selectedUser; ThisItem );
        Reset( TextSearchBox );
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ); 
            Collect( MyPeople; ThisItem )
        )
    )
    ```
Выбор этого элемента управления делает три вещи одновременно:

   * Задает\_переменную **селектедусер** для выбранного элемента.
   * Сбрасывает условие поиска в **текстсеарчбокс**.
   * Добавляет выбранный элемент в коллекцию **мипеопле** , коллекцию всех пользователей, выбранных пользователем приложения.

### <a name="userbrowsegallery-profileimage-control"></a>Элемент управления Усербровсегаллери ProfileImage

![Элемент управления Усербровсегаллери ProfileImage](media/people-screen/people-browse-gall-image.png)

* Свойство: **изображение**<br>
    Значение: логика для получения фотографии профиля пользователя.

    ```powerapps-comma
    If( !IsBlank( ThisItem.Id ) && 
            'Office365Users'.UserPhotoMetadata( ThisItem.Id ).HasPhoto;
        'Office365Users'.UserPhoto( ThisItem.Id )
    )
    ```

Элемент управления **Image** извлекает изображение пользователя с помощью операции [Office365Users. усерфото](https://docs.microsoft.com/connectors/office365users/#get-user-photo--v1-) . Однако перед этим он проверяет наличие двух вещей:
  
   * Указывает, является ли поле идентификатора пустым или непустым. Это предотвращает попытку элемента управления **изображением** получить фотографию пользователя, прежде чем коллекция будет заполнена результатами поиска.
   * Имеет ли пользователь фотографию (с операцией [Office365Users. усерфотометадата](https://docs.microsoft.com/connectors/office365users/#get-user-photo-metadata) ). Это предотвращает возврат исключения `Office365Users.UserPhoto` уточняющего запроса, если у пользователя нет изображения профиля.

Обратите внимание, что если изображение не извлекается, элемент управления **изображения** остается пустым, а вместо него отображается элемент управления **иконусер** .

## <a name="people-added-gallery"></a>Коллекция, добавленная пользователями

![Элемент управления Пеоплеаддедгаллери](media/people-screen/people-people-gall.png)

* Свойство: **элементы**<br>
    Значение: `MyPeople`

Это коллекция пользователей, инициализированных или добавленных в, путем выбора элемента управления **заголовка усербровсегаллери** .

### <a name="peopleaddedgallery-title-control"></a>Элемент управления "заголовок Пеоплеаддедгаллери"

![Элемент управления "заголовок Пеоплеаддедгаллери"](media/people-screen/people-people-gall-title.png)

* Свойство: **OnSelect**<br>
    Значение: `Set( _selectedUser; ThisItem )`

Задает **_selectedUser** переменную для элемента, выбранного в **емаилпеоплегаллери**.

### <a name="peopleaddedgallery-iconremove-control"></a>Элемент управления Пеоплеаддедгаллери Иконремове

![Элемент управления Пеоплеаддедгаллери Иконремове](media/people-screen/people-people-gall-delete.png)

* Свойство: **OnSelect**<br>
    Значение: `Remove( MyPeople; LookUp( MyPeople; UserPrincipalName = ThisItem.UserPrincipalName ) )`

Выполняет поиск записи в коллекции **мипеопле** , где **userPrincipalName** соответствует **userPrincipalName** выбранного элемента, а затем удаляет эту запись из коллекции.

## <a name="next-steps"></a>Дальнейшие действия

* Дополнительные [сведения об этом экране](./people-screen-overview.md).
* Дополнительные [сведения о соединителе Office 365 Outlook](../connections/connection-office365-outlook.md).
* Дополнительные [сведения о соединителе пользователей Office 365](../connections/connection-office365-users.md).
