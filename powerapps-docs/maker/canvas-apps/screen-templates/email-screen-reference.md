---
title: Справочник по шаблон экрана электронной почты для приложения на основе холста | Документация Майкрософт
description: Понимание деталей того, как работает шаблон экрана электронной почты для приложения на основе холста в PowerApps
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/31/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8f77fe1194ace2f8cb5abeb3f9657cc76aab263a
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61538825"
ms.PowerAppsDecimalTransform: true
---
# <a name="reference-information-about-the-email-screen-template-for-canvas-apps"></a>Справочные сведения о шаблоне экрана электронной почты для приложения на основе холста

Для приложений на основе холста в PowerApps Узнайте, как каждого значительные элемента управления в шаблоне экрана электронной почты помогает реализовать экран общую функциональность по умолчанию. Этот видеокурс представляется формулах поведения и значения других свойств, которые определяют, каким образом элементы управления реагирует на действия пользователя. Обзорное обсуждение функциональные возможности по умолчанию на этом экране, см. в разделе [Обзор экрана электронной почты](email-screen-overview.md).

В этом разделе представлены некоторые существенные элементы управления и описываются выражения или формулы для различных свойства (такие как **элементы** и **OnSelect**) из этих элементов управления заданы:

* [Текстовое поле поиска](#text-search-box)
* [Значок добавления](#add-icon)
* [Обзор коллекции пользователей](#people-browse-gallery)
* [Коллекции пользователей по электронной почте](#email-people-gallery) (+ дочерние элементы управления)
* [Значок почты](#mail-icon)

## <a name="prerequisite"></a>Необходимое условие

Знакомство с тем, как добавить и настроить экраны и другие элементы управления, как вы [Создание приложения в PowerApps](../data-platform-create-app-scratch.md).

## <a name="text-search-box"></a>Текстовое поле поиска

   ![Элемент управления TextSearchBox](media/email-screen/email-search-box.png)

Несколько других элементов управления на экране с зависимостями от **текстовое поле поиска** управления:

* Если пользователь начинает вводить любой текст, **PeopleBrowseGallery** отображается.
* Если пользователь вводит out допустимый адрес электронной почты, **AddIcon** отображается.
* Когда пользователь выбирает пользователе **PeopleBrowseGallery**, поиска содержимого, будут заменены.

## <a name="add-icon"></a>Значок добавления

   ![Элемент управления AddIcon](media/email-screen/email-add-icon.png)

**Значок добавления** элемент управления позволяет добавить пользователей, которые не существуют в их организации в список получателей электронной почты, для которого формируются пользователям приложения.

* Свойство: **Видимым**<br>
    Значение: Логика для отображения элемента управления, только в том случае, когда пользователь вводит адрес электронной почты в поле поиска:

    ```powerapps-comma
    !IsBlank( TextSearchBox.Text ) &&
        IsMatch( TextSearchBox.Text; Match.Email ) &&
        Not( Trim( TextSearchBox.Text ) in MyPeople.UserPrincipalName )
    ```
  Построчно, приведенного выше кода говорится, что **значок добавления** управления будут видны только если:

    * **TextSearchBox** содержит текст.
    * Текст в **TextSearchBox** — это адрес электронной почты.
    * Текст в **TextSearchBox** еще не существует в **MyPeople** коллекции.

* Свойство: **OnSelect**<br>
    Значение: При выборе этого добавляет допустимый адрес электронной почты для **MyPeople** коллекции. Эта коллекция используется на экране как список получателей:

    ```powerapps-comma
    Collect( MyPeople;
        { 
            DisplayName: TextSearchBox.Text; 
            UserPrincipalName: TextSearchBox.Text; 
            Mail: TextSearchBox.Text
        }
    );;
    Reset( TextSearchBox )
    ```
  
  Этот блок кода добавляет строку к **MyPeople** коллекцию и заполняет три поля с текстом в **TextSearchBox**. Эти три поля представляют собой **DisplayName**, **UserPrincipalName**, и **Mail**. Затем он сбрасывает содержимое **TextSearchBox**.

## <a name="people-browse-gallery"></a>Обзор коллекции пользователей

   ![Элемент управления PeopleBrowseGallery](media/email-screen/email-browse-gall.png)

* Свойство: **Элементы**<br>
    Значение: Результаты поиска 15 первых поиска текста, введенного в **TextSearchBox** управления:
    
    ```powerapps-comma
    If( !IsBlank( Trim(TextSearchBox.Text ) ); 
        'Office365Users'.SearchUser( {searchTerm: Trim( TextSearchBox.Text ); top: 15} )
    )
    ```

  Элементы этой коллекции, заполняются путем результаты поиска из [Office365.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) операции. Операция принимает текст `Trim(TextSearchBox)` как поиск термина и возвращает результаты 15 первых на основе поиска.
  
  **TextSearchBox** упаковывается в `Trim()` работать, поскольку поиск пользователей в пространствах является недопустимым. `Office365Users.SearchUser` Операции упаковывается в `If(!IsBlank(Trim(TextSearchBox.Text)) ... )` функцию, которая означает, что операция выполняется только в том случае, если поле поиска содержит текст, введенный пользователем. Это повышает производительность. 

### <a name="people-browse-gallery-title-control"></a>Люди Обзор элемента управления заголовка коллекции

   ![Элемент управления PeopleBrowseGallery заголовок](media/email-screen/email-browse-gall-title.png)

* Свойство: **Текст**<br>
    Значение: `ThisItem.DisplayName`

  Отображает имя пользователя из профиля Office 365.

* Свойство: **OnSelect**<br>
    Значение: Код, чтобы добавить пользователя в коллекцию уровня приложения, а затем выберите пользователя:

    ```powerapps-comma
    Concurrent(
        Set( _selectedUser; ThisItem );
        Reset( TextSearchBox );
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ); 
            Collect( MyPeople; ThisItem )
        )
    )
    ```
Выбор этого элемента управления параллельно выполняет три действия:

   * Наборы **_selectedUser** переменной для выбранного элемента.
   * Сбрасывает искомый текст в **TextSearchBox**.
   * Добавляет выбранный элемент в **MyPeople** коллекцию, коллекцию всех выбранных пользователей, которые использует на экране по электронной почте в качестве набора получателей.

## <a name="email-people-gallery"></a>Коллекции пользователей по электронной почте

   ![Элемент управления EmailPeopleGallery](media/email-screen/email-people-gall.png)

* Свойство: **Элементы**<br>
    Значение: `MyPeople`

  Это коллекция пользователей инициализируется или добавить, выбрав **PeopleBrowseGallery Title** элемента управления.

* Свойство: **Высота**<br>
    Значение: Алгоритм для установки высоту на основе количества элементов, находящихся в коллекции:

    ```powerapps-comma
    Min( 
        ( EmailPeopleGallery.TemplateHeight + EmailPeopleGallery.TemplatePadding * 2) *
            RoundUp(CountRows(EmailPeopleGallery.AllItems) / 2; 0 );
        304
    )
    ```

  Число элементов в коллекции, с максимальную высоту 304 подстраивается высота элемента коллекции.
  
  Он принимает `TemplateHeight + TemplatePadding * 2` как общую высоту одной строки **EmailPeopleGallery**, умножает его на число строк. Так как `WrapCount = 2`, число строк, значение true — `RoundUp(CountRows(EmailPeopleGallery.AllItems) / 2; 0)`.

* Свойство: **ShowScrollbar**<br>
    Значение: `EmailPeopleGallery.Height >= 304`
  
  По достижении 304 высоту элемента коллекции полоса прокрутки является видимым.

### <a name="email-people-gallery-title-control"></a>Коллекции пользователей по электронной почте заголовок элемента управления

   ![Элемент управления EmailPeopleGallery заголовок](media/email-screen/email-people-gall-text.png)

* Свойство: **OnSelect**<br>
    Значение: `Set(_selectedUser; ThisItem)`

  Наборы **_selectedUser** переменных для элемента, выбранного в **EmailPeopleGallery**.

### <a name="email-people-gallery-iconremove-control"></a>Элемент управления iconRemove галереи людей по электронной почте

   ![Элемент управления MonthDayGallery заголовок](media/email-screen/email-people-gall-delete.png)

* Свойство: **OnSelect**<br>
    Значение: `Remove( MyPeople; LookUp( MyPeople; UserPrincipalName = ThisItem.UserPrincipalName ) )`

  Ищет запись в **MyPeople** коллекции, где **UserPrincipalName** соответствует **UserPrincipalName** выбранного элемента и удаляет записи из Коллекция.

## <a name="mail-icon"></a>Значок почты

* Свойство: **OnSelect**<br>
    Значение: Логики для отправки сообщения электронной почты пользователя:

    ```powerapps-comma
    Set( _emailRecipientString; Concat( MyPeople; Mail & ";" ) );;
    'Office365'.SendEmail( _emailRecipientString; 
        TextEmailSubject.Text;  
        TextEmailMessage.Text; 
        { Importance:"Normal" }
    );;
    Reset( TextEmailSubject );;
    Reset( TextEmailMessage );;
    Clear( MyPeople )
    ```

  Отправка сообщения электронной почты требуется строка разделенных точкой с запятой адресов электронной почты. В приведенном выше коде:
  1. Первая часть кода принимает **Mail** из всех строк в **MyPeople** коллекции, объединяет их в одну строку адреса электронной почты, разделенных точкой с запятой и задает **_ emailRecipientString** строковое значение переменной.

  1. Затем он использует [Office365.SendEmail](https://docs.microsoft.com/connectors/office365/#sendemail) операцию отправки сообщения электронной почты получателей.
    Операция имеет три обязательных параметров, **для**, **субъекта**, и **текст**и один необязательный параметр--**важности**. В приведенном выше коде это **_emailRecipientString**, **TextEmailSubject**. Текст, **TextEmailMessage**. Текст, и **обычный**, соответственно.
  1. Наконец, он сбрасывает **TextEmailSubject** и **TextEmailMessage** элементы управления и очищает **MyPeople** коллекции.

* Свойство: **DisplayMode**<br>
    Значение: `If( Len( Trim( TextEmailSubject.Text ) ) > 0 && !IsEmpty( MyPeople ); DisplayMode.Edit; DisplayMode.Disabled )` Для отправки сообщения электронной почты, текст, а получатель должен иметь строку темы электронного сообщения (**MyPeople**) коллекция не должна быть пустой.

## <a name="next-steps"></a>Дальнейшие действия

* [Дополнительные сведения об этом экране](./email-screen-overview.md)
* [Дополнительные сведения о соединителе Office 365 Outlook в PowerApps](../connections/connection-office365-outlook.md)
* [Дополнительные сведения о соединителе Office 365 пользователи в PowerApps](../connections/connection-office365-users.md)
