---
title: Общие сведения о подключении "Пользователи Office 365" | Документация Майкрософт
description: Узнайте, как подключиться к "Пользователи Office 365", просмотрите некоторые примеры и все функции
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/07/2016
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: aacb19180fc41cc52a9d292fd9d3282f19cc649f
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74723768"
---
# <a name="connect-to-office-365-users-connection-from-power-apps"></a>Подключение пользователей Office 365 к подключению из Power Apps
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

   `Office365Users.MyProfile().City`  
   `Office365Users.MyProfile().CompanyName`  
   `Office365Users.MyProfile().Country`  
   `Office365Users.MyProfile().Department`  
   `Office365Users.MyProfile().DisplayName`  
   `Office365Users.MyProfile().GivenName`  
   `Office365Users.MyProfile().Id`  
   `Office365Users.MyProfile().JobTitle`  
   `Office365Users.MyProfile().Mail`  
   `Office365Users.MyProfile().MailNickname`  
   `Office365Users.MyProfile().mobilePhone`  
   `Office365Users.MyProfile().OfficeLocation`  
   `Office365Users.MyProfile().PostalCode`  
   `Office365Users.MyProfile().Surname`  
   `Office365Users.MyProfile().TelephoneNumber`  
   `Office365Users.MyProfile().UserPrincipalName`  
   `Office365Users.MyProfile().AccountEnabled`  
   `Office365Users.MyProfile().BusinessPhones`

В метке отображаются введенные сведения о текущем пользователе.

### <a name="show-information-about-another-user"></a>Отображение сведений о другом пользователе
1. В меню **Вставка** выберите **Текст**, а затем — **Ввод текста**. Измените имя поля на **InfoAbout**:  

    ![Переименование элемента управления](./media/connection-office365-users/renameinfoabout.png)
2. В **InfoAbout** введите или вставьте адрес электронной почты пользователя в организации. Например, введите *ваше_имя*@*ваша_компания.com*.
3. Добавьте **Метка** (меню **Вставка**) и задайте для свойства **[Text](../controls/properties-core.md)** одну из следующих формул:

   * Отображение сведений о другом пользователе:  

     `Office365Users.UserProfile(InfoAbout.Text).City`  
     `Office365Users.UserProfile(InfoAbout.Text).CompanyName`  
     `Office365Users.UserProfile(InfoAbout.Text).Country`  
     `Office365Users.UserProfile(InfoAbout.Text).Department`  
     `Office365Users.UserProfile(InfoAbout.Text).DisplayName`  
     `Office365Users.UserProfile(InfoAbout.Text).GivenName`  
     `Office365Users.UserProfile(InfoAbout.Text).Id`  
     `Office365Users.UserProfile(InfoAbout.Text).JobTitle`  
     `Office365Users.UserProfile(InfoAbout.Text).Mail`  
     `Office365Users.UserProfile(InfoAbout.Text).MailNickname`  
     `Office365Users.UserProfile(InfoAbout.Text).mobilePhone`  
     `Office365Users.UserProfile(InfoAbout.Text).OfficeLocation`  
     `Office365Users.UserProfile(InfoAbout.Text).PostalCode`  
     `Office365Users.UserProfile(InfoAbout.Text).Surname`  
     `Office365Users.UserProfile(InfoAbout.Text).TelephoneNumber`  
     `Office365Users.UserProfile(InfoAbout.Text).UserPrincipalName`  
     `Office365Users.UserProfile(InfoAbout.Text).AccountEnabled`  
     `Office365Users.UserProfile(InfoAbout.Text).BusinessPhones`

   * Отображение сведений о руководителе другого пользователя:  

     `Office365Users.Manager(InfoAbout.Text).City`  
     `Office365Users.Manager(InfoAbout.Text).CompanyName`  
     `Office365Users.Manager(InfoAbout.Text).Country`  
     `Office365Users.Manager(InfoAbout.Text).Department`  
     `Office365Users.Manager(InfoAbout.Text).DisplayName`  
     `Office365Users.Manager(InfoAbout.Text).GivenName`  
     `Office365Users.Manager(InfoAbout.Text).Id`  
     `Office365Users.Manager(InfoAbout.Text).JobTitle`  
     `Office365Users.Manager(InfoAbout.Text).Mail`  
     `Office365Users.Manager(InfoAbout.Text).MailNickname`  
     `Office365Users.Manager(InfoAbout.Text).mobilePhone`  
     `Office365Users.Manager(InfoAbout.Text).OfficeLocation`  
     `Office365Users.Manager(InfoAbout.Text).PostalCode`  
     `Office365Users.Manager(InfoAbout.Text).Surname`  
     `Office365Users.Manager(InfoAbout.Text).TelephoneNumber`  
     `Office365Users.Manager(InfoAbout.Text).UserPrincipalName`  
     `Office365Users.Manager(InfoAbout.Text).AccountEnabled`  
     `Office365Users.Manager(InfoAbout.Text).BusinessPhones`

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

| Имя функции | Description |
| --- | --- |
| [DirectReports](connection-office365-users.md#directreports) |Возвращает непосредственные подчиненные для указанного пользователя. |
| [Manager](connection-office365-users.md#manager) |Получает профиль пользователя для диспетчера указанного пользователя. |
| [MyProfile](connection-office365-users.md#myprofile) |Извлекает профиль для текущего пользователя. |
| [SearchUser](connection-office365-users.md#searchuser) |Возвращает результаты поиска профилей пользователей. |
| [UserProfile](connection-office365-users.md#userprofile) |Извлекает конкретный профиль пользователя. |

### <a name="myprofile"></a>MyProfile
Получение профиля: извлекает профиль для текущего пользователя.

#### <a name="input-properties"></a>Входные свойства
Нет.

#### <a name="output-properties"></a>Выходные свойства

| Имя свойства | Тип | Description |
| --- | --- | --- |
| город | строка |Город пользователя. |
| Название | строка |Компания пользователя. |
| Стран | строка |Страна пользователя. |
| Department |строка |Отдел пользователя. |
| DisplayName |строка |Отображаемое имя пользователя |
| GivenName |строка |Заданное имя пользователя |
| Id (Идентификатор) |строка |Идентификатор пользователя. |
| JobTitle |строка |Должность пользователя. |
| Почта |строка |Идентификатор электронной почты пользователя |
| MailNickname |строка |Псевдоним пользователя |
| mobilePhone | строка |Мобильный телефон пользователя. |
| оффицелокатион | строка |Расположение пользователя в офисе.|
| Почтовый | строка |Почтовый код пользователя.|
| Surname |строка |Фамилия пользователя |
| TelephoneNumber |строка |Номер телефона пользователя |
| UserPrincipalName |строка |Имя участника-пользователя |
| AccountEnabled |логическое значение |Флаг активации учетной записи |
| бусинессфонес | строка |Номер телефона компании пользователя.|

### <a name="userprofile"></a>UserProfile
Получение профиля пользователя: извлекает профиль конкретного пользователя.

#### <a name="input-properties"></a>Входные свойства

| Имя | Тип данных | Требуется | Description |
| --- | --- | --- | --- |
| Id (Идентификатор) |строка |да |Имя участника-пользователя или идентификатор электронной почты. |

#### <a name="output-properties"></a>Выходные свойства

| Имя свойства | Тип | Description |
| --- | --- | --- |
| город | строка |Город пользователя. |
| Название | строка |Компания пользователя. |
| Стран | строка |Страна пользователя. |
| Department |строка |Отдел пользователя. |
| DisplayName |строка |Отображаемое имя пользователя |
| GivenName |строка |Заданное имя пользователя |
| Id (Идентификатор) |строка |Идентификатор пользователя. |
| JobTitle |строка |Должность пользователя. |
| Почта |строка |Идентификатор электронной почты пользователя |
| MailNickname |строка |Псевдоним пользователя |
| Surname |строка |Фамилия пользователя |
| TelephoneNumber |строка |Номер телефона пользователя |
| UserPrincipalName |строка |Имя участника-пользователя |
| AccountEnabled |логическое значение |Флаг активации учетной записи |
| бусинессфонес | строка |Номер телефона компании пользователя.|

### <a name="manager"></a>Manager
Получить диспетчер: получает профиль пользователя для руководителя указанного пользователя.

#### <a name="input-properties"></a>Входные свойства

| Имя | Тип данных | Требуется | Description |
| --- | --- | --- | --- |
| Id (Идентификатор) |строка |да |Имя участника-пользователя или идентификатор электронной почты. |

#### <a name="output-properties"></a>Выходные свойства

| Имя свойства | Тип | Description |
| --- | --- | --- |
| город | строка |Город пользователя. |
| Название | строка |Компания пользователя. |
| Стран | строка |Страна пользователя. |
| Department |строка |Отдел пользователя. |
| DisplayName |строка |Отображаемое имя пользователя |
| GivenName |строка |Заданное имя пользователя |
| Id (Идентификатор) |строка |Идентификатор пользователя. |
| JobTitle |строка |Должность пользователя. |
| Почта |строка |Идентификатор электронной почты пользователя |
| MailNickname |строка |Псевдоним пользователя |
| mobilePhone | строка |Мобильный телефон пользователя. |
| оффицелокатион | строка |Расположение пользователя в офисе.|
| Почтовый | строка |Почтовый код пользователя.|
| Surname |строка |Фамилия пользователя |
| TelephoneNumber |строка |Номер телефона пользователя |
| UserPrincipalName |строка |Имя участника-пользователя |
| AccountEnabled |логическое значение |Флаг активации учетной записи |
| бусинессфонес | строка |Номер телефона компании пользователя.|

### <a name="directreports"></a>DirectReports
Получение прямых подчиненных: получение прямых отчетов.

#### <a name="input-properties"></a>Входные свойства

| Имя | Тип данных | Требуется | Description |
| --- | --- | --- | --- |
| Id (Идентификатор) |строка |да |Имя участника-пользователя или идентификатор электронной почты. |

#### <a name="output-properties"></a>Выходные свойства

| Имя свойства | Тип | Description |
| --- | --- | --- |
| город | строка |Город пользователя. |
| Название | строка |Компания пользователя. |
| Стран | строка |Страна пользователя. |
| Department |строка |Отдел пользователя. |
| DisplayName |строка |Отображаемое имя пользователя |
| GivenName |строка |Заданное имя пользователя |
| Id (Идентификатор) |строка |Идентификатор пользователя. |
| JobTitle |строка |Должность пользователя. |
| Почта |строка |Идентификатор электронной почты пользователя |
| MailNickname |строка |Псевдоним пользователя |
| mobilePhone | строка |Мобильный телефон пользователя. |
| оффицелокатион | строка |Расположение пользователя в офисе.|
| Почтовый | строка |Почтовый код пользователя.|
| Surname |строка |Фамилия пользователя |
| TelephoneNumber |строка |Номер телефона пользователя |
| UserPrincipalName |строка |Имя участника-пользователя |
| AccountEnabled |логическое значение |Флаг активации учетной записи |
| бусинессфонес | строка |Номер телефона компании пользователя.|

### <a name="searchuser"></a>SearchUser
Поиск пользователей: получает результаты поиска профилей пользователей.

#### <a name="input-properties"></a>Входные свойства

| Имя | Тип данных | Требуется | Description |
| --- | --- | --- | --- |
| searchTerm |строка |нет |Строка поиска. Область применения: отображаемое имя, имя, фамилия, адрес электронной почты, псевдоним электронной почты и имя участника-пользователя. |

#### <a name="output-properties"></a>Выходные свойства

| Имя свойства | Тип | Description |
| --- | --- | --- |
| город | строка |Город пользователя. |
| Название | строка |Компания пользователя. |
| Стран | строка |Страна пользователя. |
| Department |строка |Отдел пользователя. |
| DisplayName |строка |Отображаемое имя пользователя |
| GivenName |строка |Заданное имя пользователя |
| Id (Идентификатор) |строка |Идентификатор пользователя. |
| JobTitle |строка |Должность пользователя. |
| Почта |строка |Идентификатор электронной почты пользователя |
| MailNickname |строка |Псевдоним пользователя |
| mobilePhone | строка |Мобильный телефон пользователя. |
| оффицелокатион | строка |Расположение пользователя в офисе.|
| Почтовый | строка |Почтовый код пользователя.|
| Surname |строка |Фамилия пользователя |
| TelephoneNumber |строка |Номер телефона пользователя |
| UserPrincipalName |строка |Имя участника-пользователя |
| AccountEnabled |логическое значение |Флаг активации учетной записи |
| бусинессфонес | строка |Номер телефона компании пользователя.|

## <a name="helpful-links"></a>Полезные ссылки
* Сведения о всех доступных подключениях см. [здесь](../connections-list.md).
* Узнайте, как [добавлять подключения](../add-manage-connections.md) в приложения.

