---
title: Справочник по шаблонам людей экран | Документация Майкрософт
description: Понимание деталей того, как работает шаблон экрана пользователей для приложений на основе холста в PowerApps
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 1/2/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 09b92a1e2bc87ac6f4e2ec651aa67a845e0f07b1
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61540780"
---
# <a name="reference-information-about-the-people-screen-template-for-canvas-apps"></a>Справочные сведения о шаблоне экрана пользователей для приложений на основе холста

Для приложений на основе холста в PowerApps Узнайте, как каждый значительные элемент управления в шаблоне людей экрана помогает реализовать экран общую функциональность по умолчанию. Этот видеокурс представляется формулах поведения и значения других свойств, которые определяют, каким образом элементы управления реагирует на действия пользователя. Обзорное обсуждение функциональные возможности по умолчанию на этом экране, см. в разделе [Обзор экрана людей](people-screen-overview.md).

В этом разделе представлены некоторые существенные элементы управления и описываются выражения или формулы для различных свойства (такие как **элементы** и **OnSelect**) из этих элементов управления заданы:

* [Текстовое поле поиска](#text-search-box)
* [Обзор пользователей коллекции](#user-browse-gallery) (+ дочерние элементы управления)
* [Пользователи добавлены коллекции](#people-added-gallery) (+ дочерние элементы управления)

## <a name="prerequisite"></a>Необходимое условие

Знакомство с тем, как добавить и настроить экраны и другие элементы управления, как вы [Создание приложения в PowerApps](../data-platform-create-app-scratch.md).

## <a name="text-search-box"></a>Текстовое поле поиска

![Элемент управления TextSearchBox](media/people-screen/people-search-box.png)

Несколько других элементов управления взаимодействуют или с зависимостями в текстовом поле поиска:

* Если пользователь начинает вводить любой текст, **UserBrowseGallery** становится видимым.
* Когда пользователь выбирает пользователе **UserBrowseGallery**, поиска содержимого, будут заменены.

## <a name="user-browse-gallery"></a>Обзор пользователей коллекции

![Элемент управления UserBrowseGallery](media/people-screen/people-browse-gall.png)

* Свойство: **Элементы**<br>
    Значение: Логику для поиска пользователей, когда пользователь начинает ВВОД:
    
    ```powerapps-dot
    If( !IsBlank( Trim( TextSearchBox.Text ) ), 
        'Office365Users'.SearchUser(
            {
                searchTerm: Trim( TextSearchBox.Text ), 
                top: 15
            }
        )
    )
    ```
    
Элементы этой коллекции, заполняются путем результаты поиска из [Office365.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) операции. Операция принимает текст `Trim(TextSearchBox)` как поиск термина и возвращает результаты 15 первых на основе поиска. **TextSearchBox** упаковывается в `Trim()` работать, поскольку поиск пользователей в пространствах является недопустимым.

`Office365Users.SearchUser` Операции упаковывается в `If(!IsBlank(Trim(TextSearchBox.Text)) ... )` работать, поскольку необходимо вызвать операцию, если введенный пользователем текст содержит поле поиска. Это повышает производительность.

### <a name="userbrowsegallery-title-control"></a>Элемент управления UserBrowseGallery заголовок

![Элемент управления UserBrowseGallery заголовок](media/people-screen/people-browse-gall-title.png)

* Свойство: **Текст**<br>Значение: `ThisItem.DisplayName`

  Отображает имя пользователя из профиля Office 365.

* Свойство: **OnSelect**<br>
    Значение: Код, чтобы добавить пользователя в коллекцию уровня приложения, а затем выберите пользователя:

    ```powerapps-dot
    Concurrent(
        Set( _selectedUser, ThisItem ),
        Reset( TextSearchBox ),
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ), 
            Collect( MyPeople, ThisItem )
        )
    )
    ```
Выбор этого элемента управления параллельно выполняет три действия:

   * Наборы  **\_selectedUser** переменной для выбранного элемента.
   * Сбрасывает искомый текст в **TextSearchBox**.
   * Добавляет выбранный элемент в **MyPeople** коллекции, коллекции всех людей выбрал пользователь приложения.

### <a name="userbrowsegallery-profileimage-control"></a>Элемент управления UserBrowseGallery ProfileImage

![Элемент управления UserBrowseGallery ProfileImage](media/people-screen/people-browse-gall-image.png)

* Свойство: **Изображение**<br>
    Значение: Логика для извлечения фотографию профиля пользователя.

    ```powerapps-dot
    If( !IsBlank( ThisItem.Id ) && 
            'Office365Users'.UserPhotoMetadata( ThisItem.Id ).HasPhoto,
        'Office365Users'.UserPhoto( ThisItem.Id )
    )
    ```

**Изображение** элемент управления получает пользовательский образ с [Office365Users.UserPhoto](https://docs.microsoft.com/connectors/office365users/#get-user-photo--v1-) операции. Однако перед этим, он проверяет наличие две вещи:
  
   * Является ли поле ID пуст или не является пустым. Это предотвращает **изображение** управления пытался получить фотографию пользователя до заполнения коллекции с результатами поиска.
   * Имеет ли пользователь фотографию (с [Office365Users.UserPhotoMetadata](https://docs.microsoft.com/connectors/office365users/#get-user-photo-metadata) операции). Это предотвращает `Office365Users.UserPhoto` Уточняющий запрос возвращал исключение, если у пользователя нет фотографию профиля.

Обратите внимание, что, если изображение не извлекаются, **изображение** элемент управления является пустым и **iconUser** вместо этого элемент управления является видимым.

## <a name="people-added-gallery"></a>Добавить людей коллекции

![Элемент управления PeopleAddedGallery](media/people-screen/people-people-gall.png)

* Свойство: **Элементы**<br>
    Значение: `MyPeople`

Это коллекция пользователей инициализируется или добавить, выбрав **UserBrowseGallery Title** элемента управления.

### <a name="peopleaddedgallery-title-control"></a>Элемент управления PeopleAddedGallery заголовок

![Элемент управления PeopleAddedGallery заголовок](media/people-screen/people-people-gall-title.png)

* Свойство: **OnSelect**<br>
    Значение: `Set( _selectedUser, ThisItem )`

Наборы **_selectedUser** переменных для элемента, выбранного в **EmailPeopleGallery**.

### <a name="peopleaddedgallery-iconremove-control"></a>Элемент управления iconRemove PeopleAddedGallery

![Элемент управления iconRemove PeopleAddedGallery](media/people-screen/people-people-gall-delete.png)

* Свойство: **OnSelect**<br>
    Значение: `Remove( MyPeople, LookUp( MyPeople, UserPrincipalName = ThisItem.UserPrincipalName ) )`

Ищет запись в **MyPeople** коллекции, где **UserPrincipalName** соответствует **UserPrincipalName** выбранного элемента, а затем удаляет записи из Коллекция.

## <a name="next-steps"></a>Дальнейшие действия

* [Дополнительные сведения об этом экране](./people-screen-overview.md).
* [Дополнительные сведения о соединителе Office 365 Outlook](../connections/connection-office365-outlook.md).
* [Дополнительные сведения о соединителе пользователи Office 365](../connections/connection-office365-users.md).
