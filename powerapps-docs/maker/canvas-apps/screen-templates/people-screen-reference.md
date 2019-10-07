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
ms.openlocfilehash: 0a1626583300e6fe696415a91de68ff08596f081
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "71989384"
---
# <a name="reference-information-about-the-people-screen-template-for-canvas-apps"></a>Справочные сведения о шаблоне "люди — экран" для приложений Canvas

Для приложений Canvas в PowerApps изучите, как каждый важный элемент управления в шаблоне "люди" влияет на общую функциональность по умолчанию на экране. В этом подробном обзоре представлены формулы поведения и значения других свойств, определяющих реакцию элементов управления на вводимые пользователем данные. Подробное описание функциональных возможностей этого экрана по умолчанию см. в разделе [Общие сведения о людях](people-screen-overview.md).

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

* Свойства **Файлов**<br>
    Значений Логика для поиска пользователей, когда пользователь начинает вводить:
    
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
    
Элементы этой коллекции заполняются результатами поиска из операции [Office 365. сеарчусер](https://docs.microsoft.com/connectors/office365users/#searchuser) . Операция принимает текст в `Trim(TextSearchBox)` в качестве условия поиска и возвращает 15 лучших результатов, основанных на этом поиске. **Текстсеарчбокс** заключен в функцию `Trim()`, так как поиск пользователя в пробелах является недопустимым.

Операция `Office365Users.SearchUser` заключается в функции `If(!IsBlank(Trim(TextSearchBox.Text)) ... )`, так как вам нужно вызвать операцию только тогда, когда поле поиска содержит введенный пользователем текст. Это повышает производительность.

### <a name="userbrowsegallery-title-control"></a>Элемент управления "заголовок Усербровсегаллери"

![Элемент управления "заголовок Усербровсегаллери"](media/people-screen/people-browse-gall-title.png)

* Свойства **Текст**<br>Значение: `ThisItem.DisplayName`

  Отображает отображаемое имя пользователя из профиля Office 365.

* Свойства **OnSelect**<br>
    Значений Код, чтобы добавить пользователя в коллекцию уровня приложения, а затем выберите пользователя:

    ```powerapps-dot
    Concurrent(
        Set( _selectedUser, ThisItem ),
        Reset( TextSearchBox ),
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ), 
            Collect( MyPeople, ThisItem )
        )
    )
    ```
Выбор этого элемента управления делает три вещи одновременно:

   * Задает переменную **\_selectedUser** для выбранного элемента.
   * Сбрасывает условие поиска в **текстсеарчбокс**.
   * Добавляет выбранный элемент в коллекцию **мипеопле** , коллекцию всех пользователей, выбранных пользователем приложения.

### <a name="userbrowsegallery-profileimage-control"></a>Элемент управления Усербровсегаллери ProfileImage

![Элемент управления Усербровсегаллери ProfileImage](media/people-screen/people-browse-gall-image.png)

* Свойства **Изображение**<br>
    Значений Логика для получения фотографии профиля пользователя.

    ```powerapps-dot
    If( !IsBlank( ThisItem.Id ) && 
            'Office365Users'.UserPhotoMetadata( ThisItem.Id ).HasPhoto,
        'Office365Users'.UserPhoto( ThisItem.Id )
    )
    ```

Элемент управления **Image** извлекает изображение пользователя с помощью операции [Office365Users. усерфото](https://docs.microsoft.com/connectors/office365users/#get-user-photo--v1-) . Однако перед этим он проверяет наличие двух вещей:
  
   * Указывает, является ли поле идентификатора пустым или непустым. Это предотвращает попытку элемента управления **изображением** получить фотографию пользователя, прежде чем коллекция будет заполнена результатами поиска.
   * Имеет ли пользователь фотографию (с операцией [Office365Users. усерфотометадата](https://docs.microsoft.com/connectors/office365users/#get-user-photo-metadata) ). Это предотвратит возврат исключения `Office365Users.UserPhoto`, если у пользователя нет изображения профиля.

Обратите внимание, что если изображение не извлекается, элемент управления **изображения** остается пустым, а вместо него отображается элемент управления **иконусер** .

## <a name="people-added-gallery"></a>Коллекция, добавленная пользователями

![Элемент управления Пеоплеаддедгаллери](media/people-screen/people-people-gall.png)

* Свойства **Файлов**<br>
    Значение: `MyPeople`

Это коллекция пользователей, инициализированных или добавленных в, путем выбора элемента управления **заголовка усербровсегаллери** .

### <a name="peopleaddedgallery-title-control"></a>Элемент управления "заголовок Пеоплеаддедгаллери"

![Элемент управления "заголовок Пеоплеаддедгаллери"](media/people-screen/people-people-gall-title.png)

* Свойства **OnSelect**<br>
    Значение: `Set( _selectedUser, ThisItem )`

Задает переменную **_selectedUser** для элемента, выбранного в **емаилпеоплегаллери**.

### <a name="peopleaddedgallery-iconremove-control"></a>Элемент управления Пеоплеаддедгаллери Иконремове

![Элемент управления Пеоплеаддедгаллери Иконремове](media/people-screen/people-people-gall-delete.png)

* Свойства **OnSelect**<br>
    Значение: `Remove( MyPeople, LookUp( MyPeople, UserPrincipalName = ThisItem.UserPrincipalName ) )`

Выполняет поиск записи в коллекции **мипеопле** , где **userPrincipalName** соответствует **userPrincipalName** выбранного элемента, а затем удаляет эту запись из коллекции.

## <a name="next-steps"></a>Дальнейшие действия

* Дополнительные [сведения об этом экране](./people-screen-overview.md).
* Дополнительные [сведения о соединителе Office 365 Outlook](../connections/connection-office365-outlook.md).
* Дополнительные [сведения о соединителе пользователей Office 365](../connections/connection-office365-users.md).
