---
title: Общие сведения о подключении "Пользователи Office 365" | Документация Майкрософт
description: Узнайте, как подключиться к "Пользователи Office 365", просмотрите некоторые примеры и все функции
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/07/2016
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 507bac0b57cdc1e348bd384d5544d7b664a3e0f5
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61557383"
---
# <a name="connect-to-office-365-users-connection-from-powerapps"></a>Подключение к подключению "Пользователи Office 365" из PowerApps
![Пользователи Office 365](./media/connection-office365-users/office365icon.png)

Подключение "Пользователи Office 365" позволяет получить доступ к профилям пользователей в вашей организации с помощью учетной записи Office 365. Вы можете выполнять различные действия, например получить свой профиль, профиль пользователя, руководителя или подчиненных пользователя.

Эти сведения можно отобразить в метке приложения. Вы можете отобразить одну или несколько функций либо даже комбинировать различные функции. Например, можно создать выражение, которое объединяет поля "Имя пользователя" и "Номер телефона", а затем отобразить эти сведения в приложении.

В этой статье разъясняется, как добавлять "Пользователи Office 365" в качестве подключения и источника данных в приложение, а также как использовать данные таблицы в элементе управления "Коллекция".

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

## <a name="add-a-connection"></a>Добавление подключения
1. [Добавьте подключение данных](../add-data-connection.md) и выберите **Пользователи Office 365**:  

    ![Подключение к Office 365](./media/connection-office365-users/add-office.png)
2. Выберите **Подключиться** и при появлении запроса на вход введите данные своей рабочей учетной записи.

Подключение "Пользователи Office 365" создано и добавлено в приложение. Теперь оно готово к использованию.

## <a name="use-the-connection-in-your-app"></a>Использование подключения в приложении
### <a name="show-information-about-the-current-user"></a>Отображение сведений о текущем пользователе
1. В меню **Вставка** выберите пункт **Метка**.
2. В строке функции задайте для свойства **[Текст](../controls/properties-core.md)** одну из следующих формул:

    `Office365Users.MyProfile().Department`  
    `Office365Users.MyProfile().DisplayName`  
    `Office365Users.MyProfile().GivenName`  
    `Office365Users.MyProfile().Id`  
    `Office365Users.MyProfile().JobTitle`  
    `Office365Users.MyProfile().Mail`  
    `Office365Users.MyProfile().MailNickname`  
    `Office365Users.MyProfile().Surname`  
    `Office365Users.MyProfile().TelephoneNumber`  
    `Office365Users.MyProfile().UserPrincipalName`  
    `Office365Users.MyProfile().AccountEnabled`  

В метке отображаются введенные сведения о текущем пользователе.

### <a name="show-information-about-another-user"></a>Отображение сведений о другом пользователе
1. В меню **Вставка** выберите **Текст**, а затем — **Ввод текста**. Измените имя поля на **InfoAbout**:  

    ![Переименование элемента управления](./media/connection-office365-users/renameinfoabout.png)
2. В **InfoAbout** введите или вставьте адрес электронной почты пользователя в организации. Например, введите *ваше_имя*@*ваша_компания.com*.
3. Добавьте **Метка** (меню **Вставка**) и задайте для свойства **[Text](../controls/properties-core.md)** одну из следующих формул:

   * Отображение сведений о другом пользователе:  

       `Office365Users.UserProfile(InfoAbout.Text).Department`  
       `Office365Users.UserProfile(InfoAbout.Text).DisplayName`  
       `Office365Users.UserProfile(InfoAbout.Text).GivenName`  
       `Office365Users.UserProfile(InfoAbout.Text).Id`  
       `Office365Users.UserProfile(InfoAbout.Text).JobTitle`  
       `Office365Users.UserProfile(InfoAbout.Text).Mail`  
       `Office365Users.UserProfile(InfoAbout.Text).MailNickname`  
       `Office365Users.UserProfile(InfoAbout.Text).Surname`  
       `Office365Users.UserProfile(InfoAbout.Text).TelephoneNumber`  
       `Office365Users.UserProfile(InfoAbout.Text).UserPrincipalName`  
       `Office365Users.UserProfile(InfoAbout.Text).AccountEnabled`  
   * Отображение сведений о руководителе другого пользователя:  

       `Office365Users.Manager(InfoAbout.Text).Department`  
       `Office365Users.Manager(InfoAbout.Text).DisplayName`  
       `Office365Users.Manager(InfoAbout.Text).GivenName`  
       `Office365Users.Manager(InfoAbout.Text).Id`  
       `Office365Users.Manager(InfoAbout.Text).JobTitle`  
       `Office365Users.Manager(InfoAbout.Text).Mail`  
       `Office365Users.Manager(InfoAbout.Text).MailNickname`  
       `Office365Users.Manager(InfoAbout.Text).Surname`  
       `Office365Users.Manager(InfoAbout.Text).TelephoneNumber`  
       `Office365Users.Manager(InfoAbout.Text).UserPrincipalName`  
       `Office365Users.Manager(InfoAbout.Text).AccountEnabled`  

В метке отображаются введенные сведения об указанном пользователе или его руководителе.

> [!NOTE]
> Если вы разрабатываете в Common Data Service приложение, основанное на сущности, можно указать пользователя на основе идентификатора, а не адреса электронной почты.

Например, вы можете [автоматически создать приложение](../data-platform-create-app.md), добавить экран, содержащий элемент управления **Метка**, и задать для свойства **Text** эту формулу:
<br>**Office365Users.UserProfile(BrowseGallery1.Selected.CreatedByUser).DisplayName**

Если создать контакт и выбрать его на экране обзора приложения, в элементе управления **Метка** появится отображаемое имя.

### <a name="show-the-direct-reports-of-another-user"></a>Отображение подчиненных другого пользователя
1. Добавьте элемент управления **Ввод текста** (меню **Вставка** > **Текст**) и переименуйте его на **InfoAbout**.
2. В **InfoAbout** введите адрес электронной почты пользователя в организации. Например, введите *имя_вашего_руководителя*@*ваша_компания.com*
3. Добавьте коллекцию **С текстом** (меню **Вставка** > **Коллекция**) и задайте для свойства **[Items](../controls/properties-core.md)** следующую формулу:

    `Office365Users.DirectReports(InfoAbout.Text)`

    В коллекции отображаются введенные сведения о подчиненных пользователя.

    Если выбрать коллекцию, в правой области отобразятся ее параметры.
4. Во втором списке выберите **JobTitle**. В третьем списке выберите **DisplayName**. Коллекция обновляется для отображения этих значений.  

> [!NOTE]
> Первое поле является элементом управления "Изображение". Если изображение отсутствует, можно удалить элемент управления "Изображение" и добавить вместо него метку. В статье [Add and configure controls](../add-configure-controls.md) (Добавление и настройка элементов управления) представлено много полезных сведений.

### <a name="search-for-users"></a>Поиск пользователей
1. Добавьте элемент управления **Ввод текста** (меню **Вставка** > **Текст**) и переименуйте его на **SearchTerm**. Введите имя для поиска. Например, введите свое имя.
2. Добавьте коллекцию **С текстом** (меню **Вставка** > **Коллекция**) и задайте для свойства **[Items](../controls/properties-core.md)** следующую формулу:

    `Office365Users.SearchUser({searchTerm: SearchTerm.Text})`

    В коллекции отобразятся пользователи, имена которых содержат введенный текст для поиска.

    Если выбрать коллекцию, в правой области отобразятся ее параметры.
3. Во втором списке выберите **Mail**. В третьем списке выберите **DisplayName**.

    Вторая и третья метки в коллекции будут обновлены.

## <a name="view-the-available-functions"></a>Просмотр доступных функций
Это подключение включает следующие функции:

| Имя функции | Описание |
| --- | --- |
| [MyProfile](connection-office365-users.md#myprofile) |Извлекает профиль для текущего пользователя |
| [UserProfile](connection-office365-users.md#userprofile) |Извлекает профиль конкретного пользователя |
| [Manager](connection-office365-users.md#manager) |Извлекает профиль пользователя для руководителя указанного пользователя |
| [DirectReports](connection-office365-users.md#directreports) |Возвращает профили подчиненных для указанного пользователя |
| [SearchUser](connection-office365-users.md#searchuser) |Извлекает результаты поиска профилей пользователей |

### <a name="myprofile"></a>MyProfile
Получите Мой профиль: Извлекает профиль для текущего пользователя.

#### <a name="input-properties"></a>Входные свойства
Нет.

#### <a name="output-properties"></a>Выходные свойства

| Имя свойства | Тип | Описание |
| --- | --- | --- |
| Department |строка |Отдел пользователя |
| DisplayName |строка |Отображаемое имя пользователя |
| GivenName |строка |Заданное имя пользователя |
| Id (Идентификатор) |строка |Идентификатор пользователя |
| JobTitle |строка |Должность пользователя |
| Почта |строка |Идентификатор электронной почты пользователя |
| MailNickname |строка |Псевдоним пользователя |
| Surname |строка |Фамилия пользователя |
| TelephoneNumber |строка |Номер телефона пользователя |
| UserPrincipalName |строка |Имя участника-пользователя |
| AccountEnabled |логическое значение |Флаг активации учетной записи |

### <a name="userprofile"></a>UserProfile
Получение профиля пользователя: Извлекает профиль конкретного пользователя.

#### <a name="input-properties"></a>Входные свойства

| Имя | Тип данных | Требуется | Описание |
| --- | --- | --- | --- |
| Id (Идентификатор) |строка |да |Имя участника-пользователя или идентификатор адреса электронной почты пользователя |

#### <a name="output-properties"></a>Выходные свойства

| Имя свойства | Тип | Описание |
| --- | --- | --- |
| Department |строка |Отдел пользователя |
| DisplayName |строка |Отображаемое имя пользователя |
| GivenName |строка |Заданное имя пользователя |
| Id (Идентификатор) |строка |Идентификатор пользователя |
| JobTitle |строка |Должность пользователя |
| Почта |строка |Идентификатор электронной почты пользователя |
| MailNickname |строка |Псевдоним пользователя |
| Surname |строка |Фамилия пользователя |
| TelephoneNumber |строка |Номер телефона пользователя |
| UserPrincipalName |строка |Имя участника-пользователя |
| AccountEnabled |логическое значение |Флаг активации учетной записи |

### <a name="manager"></a>Manager
Получение manager: Извлекает профиль пользователя для руководителя указанного пользователя

#### <a name="input-properties"></a>Входные свойства

| Имя | Тип данных | Требуется | Описание |
| --- | --- | --- | --- |
| Id (Идентификатор) |строка |да |Имя участника-пользователя или идентификатор адреса электронной почты пользователя |

#### <a name="output-properties"></a>Выходные свойства

| Имя свойства | Тип | Описание |
| --- | --- | --- |
| Department |строка |Отдел пользователя |
| DisplayName |строка |Отображаемое имя пользователя |
| GivenName |строка |Заданное имя пользователя |
| Id (Идентификатор) |строка |Идентификатор пользователя |
| JobTitle |строка |Должность пользователя |
| Почта |строка |Идентификатор электронной почты пользователя |
| MailNickname |строка |Псевдоним пользователя |
| Surname |строка |Фамилия пользователя |
| TelephoneNumber |строка |Номер телефона пользователя |
| UserPrincipalName |строка |Имя участника-пользователя |
| AccountEnabled |логическое значение |Флаг активации учетной записи |

### <a name="directreports"></a>DirectReports
Получение подчиненных: Получение подчиненных

#### <a name="input-properties"></a>Входные свойства

| Имя | Тип данных | Требуется | Описание |
| --- | --- | --- | --- |
| Id (Идентификатор) |строка |да |Имя участника-пользователя или идентификатор адреса электронной почты пользователя |

#### <a name="output-properties"></a>Выходные свойства

| Имя свойства | Тип | Описание |
| --- | --- | --- |
| Department |строка |Отдел пользователя |
| DisplayName |строка |Отображаемое имя пользователя |
| GivenName |строка |Заданное имя пользователя |
| Id (Идентификатор) |строка |Идентификатор пользователя |
| JobTitle |строка |Должность пользователя |
| Почта |строка |Идентификатор электронной почты пользователя |
| MailNickname |строка |Псевдоним пользователя |
| Surname |строка |Фамилия пользователя |
| TelephoneNumber |строка |Номер телефона пользователя |
| UserPrincipalName |строка |Имя участника-пользователя |
| AccountEnabled |логическое значение |Флаг активации учетной записи |

### <a name="searchuser"></a>SearchUser
Поиск пользователей: Извлекает результаты поиска профилей пользователей

#### <a name="input-properties"></a>Входные свойства

| Имя | Тип данных | Требуется | Описание |
| --- | --- | --- | --- |
| searchTerm |строка |нет |Строка поиска. Область применения: отображаемое имя, заданное имя, фамилия, почта, почтовый псевдоним и имя участника-пользователя. |

#### <a name="output-properties"></a>Выходные свойства

| Имя свойства | Тип | Описание |
| --- | --- | --- |
| Department |строка |Отдел пользователя |
| DisplayName |строка |Отображаемое имя пользователя |
| GivenName |строка |Заданное имя пользователя |
| Id (Идентификатор) |строка |Идентификатор пользователя |
| JobTitle |строка |Должность пользователя |
| Почта |строка |Идентификатор электронной почты пользователя |
| MailNickname |строка |Псевдоним пользователя |
| Surname |строка |Фамилия пользователя |
| TelephoneNumber |строка |Номер телефона пользователя |
| UserPrincipalName |строка |Имя участника-пользователя |
| AccountEnabled |логическое значение |Флаг активации учетной записи |

## <a name="helpful-links"></a>Полезные ссылки
* Сведения о всех доступных подключениях см. [здесь](../connections-list.md).
* Узнайте, как [добавлять подключения](../add-manage-connections.md) в приложения.

