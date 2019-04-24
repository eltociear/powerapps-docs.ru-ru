---
title: Шаблон экрана календаря | Документация Майкрософт
description: Понять, как работает шаблон экрана календаря для приложений на основе холста, изменение экрана и расширять его как часть приложения
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/28/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 745b4232a43a06c46866e83ca2452f8a55afeddf
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61536226"
---
# <a name="overview-of-the-calendar-screen-template-for-canvas-apps"></a>Общие сведения о шаблоне экран календарь для приложений на основе холста

В приложение на основе холста добавьте экран календарь, показывает пользователей предстоящие события из учетной записи Office 365 Outlook. Пользователи могут выбирать дату из календаря и прокрутите список событий в этот день. Можно выбрать, какие сведения отображаются в списке, добавьте второй экран, на котором представлены дополнительные сведения о каждом событии, Показать список участников, для каждого события и выполните другие настройки.

Вы также можете добавить другие экраны на базе шаблона, такие как отображение различных данных из Office 365, [электронной почты](email-screen-overview.md), [людей](people-screen-overview.md) в организации, и [доступности](meeting-screen-overview.md) людей пользователей может потребоваться приглашения на собрание.

В этом обзоре показано:
> [!div class="checklist"]
> * Инструкции по использованию экрана календаря по умолчанию.
> * Как изменить его.
> * Как интегрировать его в приложение.

Подробные сведения о функции по умолчанию этот экран, см. в разделе [календаря экранах](calendar-screen-reference.md).

## <a name="prerequisite"></a>Необходимое условие

Знакомство с тем, как добавить и настроить экраны и другие элементы управления, как вы [Создание приложения в PowerApps](../data-platform-create-app-scratch.md).

## <a name="default-functionality"></a>Стандартная функциональность

Добавление экрана календаря на основе шаблона:

1. [Войдите в](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) в PowerApps, для создания приложения или откройте существующее приложение в PowerApps Studio.

    В этом разделе показано приложение для телефона, но те же принципы применимы к приложение для планшета.

1. На **Главная** вкладке на ленте выберите **новый экран** > **календаря**.

    По умолчанию экран выглядит примерно так:

    ![Экран календарь](media/calendar-screen/calendar-initial.png)

1. Чтобы отобразить данные, выберите параметр в раскрывающемся списке в верхней части экрана.

    ![Экран календарь по завершении загрузки](./media/calendar-screen/calendar-screen.png)

Несколько полезные примечания:

* Сегодняшняя дата выбирается по умолчанию, и можно легко вернуться к ней, выбрав значок календаря в правом верхнем углу.
* Если выбрать другую дату, круг вокруг него должна быть и светлый прямоугольник (синий, если применяется тема по умолчанию) заключает сегодняшнюю дату.
* Если по крайней мере одно событие запланирована для определенной даты, небольшой цветного кружка появится в разделе этой даты в календаре.
* Если выбрать дату, для которых запланированы одно или несколько событий, события отображаются в списке календаря.

## <a name="modify-the-screen"></a>Изменение экрана

Функции по умолчанию этот экран можно изменить в несколько распространенных способов:

* [Укажите календарь](calendar-screen-overview.md#specify-the-calendar).
* [Отображение различных сведений о событии](calendar-screen-overview.md#show-different-details-about-an-event).
* [Скрыть неблокирующем события](calendar-screen-overview.md#hide-nonblocking-events).

Если вы хотите изменить дальнейшей экрана, используйте [календаря экранах](./calendar-screen-reference.md) по.

### <a name="specify-the-calendar"></a>Укажите календарь

Если вы уже знаете, какой календарь, следует просмотреть пользователей, вы можете упростить экрана, указав этот календарь, прежде чем публиковать приложение. Это изменение устраняет потребность в раскрывающемся списке календарей, поэтому его можно удалить.

1. Задайте **[OnStart](../controls/control-screen.md)** свойства экрана по умолчанию в приложении следующую формулу:

    ```powerapps-dot
    Set( _userDomain, Right( User().Email, Len( User().Email ) - Find( "@", User().Email ) ) );
    Set( _dateSelected, Today() );
    Set( _firstDayOfMonth, DateAdd( Today(), 1 - Day( Today() ), Days ) );
    Set( _firstDayInView, 
        DateAdd( _firstDayOfMonth, -( Weekday( _firstDayOfMonth) - 2 + 1 ), Days )
    );
    Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) );
    Set( _calendarVisible, false );
    Set( _myCalendar, 
        LookUp( Office365.CalendarGetTables().value, DisplayName = "{YourCalendarNameHere}" )
    );
    Set( _minDate, 
        DateAdd( _firstDayOfMonth, -( Weekday(_firstDayOfMonth) - 2 + 1 ), Days )
    );
    Set( _maxDate, 
        DateAdd(
            DateAdd( _firstDayOfMonth, -( Weekday(_firstDayOfMonth) - 2 + 1 ), Days ),
            40, 
            Days 
        )
    );
    ClearCollect( MyCalendarEvents, 
        Office365.GetEventsCalendarViewV2( _myCalendar.Name, 
            Text( _minDate, UTC ), 
            Text( _maxDate, UTC ) 
        ).value
    );
    Set( _calendarVisible, true )
    ```

    > [!NOTE]
    > Эта формула немного изменяется со значения по умолчанию из **OnSelect** свойство из раскрывающегося списка для выбора календаря. Дополнительные сведения об элементе управления, см. в статье раздела в [календаря экранах](./calendar-screen-reference.md#calendar-drop-down).

1. Замените `{YourCalendarNameHere}`, включая фигурные скобки, с именем календаря, который вы хотите отобразить (например, **календаря**).

    > [!IMPORTANT]
    > Следующие шаги предполагают, что вы добавили только один экран календарь в приложение. Если вы добавили несколько, имена элементов управления (такие как **iconCalendar1**) будет заканчиваться другой номер, и вам нужно будет соответствующим образом изменить формулы.

1. Задайте **Y** свойство **iconCalendar1** управления следующее выражение:

    `RectQuickActionBar1.Height + 20`

1. Задайте **Y** свойство **LblMonthSelected1** управления следующее выражение:

    `iconCalendar1.Y + iconCalendar1.Height + 20`

1. Задайте **текст** свойство **LblNoEvents1** управления такое значение:

    `"No events scheduled"`

1. Задайте **Visible** свойство **LblNoEvents1** следующую формулу:

    `CountRows(CalendarEventsGallery1.AllItems) = 0 && _calendarVisible`

1. Удалите эти элементы управления:

    - **dropdownCalendarSelection1**
    - **LblEmptyState1**
    - **iconEmptyState1**

1. Если экран календарь не экрана по умолчанию, добавление кнопки, которая переходит на экране по умолчанию на экран календарь, можно протестировать приложение.

    Например, добавьте кнопку на **Screen1** , осуществляющий переход к **Screen2** при добавлении приложения, созданный из пустого экрана календаря.

1. Сохраните приложение и проверьте его в браузере или на мобильном устройстве.

### <a name="show-different-details-about-an-event"></a>Отображение различных сведений о событии

По умолчанию в коллекции. в разделе календаря, с именем **CalendarEventsGallery**, показывает время начала, длительности, субъекта и расположение каждого события. Можно настроить коллекции, чтобы отобразить любое поле (например, организатор), [соединителя Office 365](https://docs.microsoft.com/connectors/office365/#calendareventclientreceive) поддерживает.

1. В **CalendarEventsGallery**, задайте **текст** свойство новую или существующую метку для `ThisItem` последующей точкой.

    IntelliSense перечисляет поля, которые можно выбрать.

1. Выберите нужное поле.

    В метке отображаются тип данных, который вы указали.

### <a name="hide-nonblocking-events"></a>Скрыть неблокирующем события

В многих офисах члены команды отправки приглашений на уведомлять друг с другом, когда будут отображаться за пределами офиса. Чтобы избежать блокировки общего расписания, лицо, отправляющее запрос задает его доступность **бесплатный**. Можно скрыть эти события в календаре и коллекции, обновив несколько свойств.

1. Задайте **элементы** свойство **CalendarEventsGallery** следующую формулу:

    ```powerapps-dot
    SortByColumns(
        Filter(
            MyCalendarEvents,
            Text( Start, DateTimeFormat.ShortDate ) = 
                Text( _dateSelected, DateTimeFormat.ShortDate ),
            ShowAs <> "Free"
        ),
        "Start"
    )
    ```

    В этой формуле **фильтра** функция скрывает не только те события, которые запланированы для даты, отличном от того, выбран, но события, для которых имеет значение доступность **бесплатный**.

1. В календаре, задайте **Visible** свойство **круг** управления следующую формулу:

    ```powerapps-dot
    CountRows(
        Filter(
            MyCalendarEvents,
            DateValue( Text(Start) ) = DateAdd( _firstDayInView, ThisItem.Value, Days ),
            ShowAs <> "Free"
        )
    ) > 0 && !Subcircle1.Visible && Title2.Visible
    ```
    Эта формула содержит те же фильтры как указанной выше формуле. Таким образом, элемент управления circle индикатор событий отображается под даты, только в том случае, если он имеет один или более событий, которые находятся в выбранной даты, а также для доступности не так **бесплатный**.

## <a name="integrate-the-screen-into-an-app"></a>Интеграция экрана в приложение

Экран календарь представляет собой мощный набор элементов управления в сам по себе, но обычно выполняет лучшие как часть большего размера, более универсальное приложение. Этот экран можно интегрировать в приложение большего размера несколькими способами, включая добавление этих параметров:

* [Просмотр сведений о событии](calendar-screen-overview.md#view-event-details).
* [Показать участников мероприятия](calendar-screen-overview.md#show-event-attendees).

### <a name="view-event-details"></a>Просмотр сведений о событии

Если пользователь выбирает события в **CalendarEventsGallery**, можно открыть другой экран, который показывает Дополнительные сведения об этом событии.

> [!NOTE]
> Эта процедура показывает подробные сведения о событии в коллекции с динамическим содержимым, но аналогичные результаты можно получить, выполнив других подходов. Например можно получить больший контроль разработки с помощью ряда меток, вместо этого.

1. Добавьте пустой экран, с именем **EventDetailsScreen**, содержащий кнопку, которая переходит на экран календарь и пустой коллекции изменяющаяся высота.

1. В галерее изменяющаяся высота добавить **метка** управления и **HTML-текст** и задать **AutoHeight** свойства обоих для **true** .

    > [!NOTE]
    > PowerApps извлекает текста сообщения для каждого события как HTML-текст, поэтому вам нужно показать содержимое в **HTML-текст** элемента управления.

1. Задайте **Y** свойство **HTML-текст** управления следующее выражение:

    `Label1.Y + Label1.Height + 20`

1. Настройте дополнительные свойства при необходимости в соответствии с потребностями стиля.

    Например, может потребоваться добавить разделитель **HTML-текст** элемента управления.

1. Задайте **элементы** свойство изменяющаяся высота коллекции следующую формулу:

    ```powerapps-dot
    Table(
        { Title: "Subject", Value: _selectedCalendarEvent.Subject },
        { 
            Title: "Time", 
            Value: _selectedCalendarEvent.Start & " - " & _selectedCalendarEvent.End 
        },
        { Title: "Body", Value: _selectedCalendarEvent.Body }
    )
    ```

    Эта формула создает коллекцию динамических данных, которой присваивается значений полей **_selectedCalendarEvent**, которое задается каждый раз при выборе события в **CalendarEventsGallery** элемента управления. Вы можете расширить этот коллекции для включения дополнительных полей путем добавления в него дополнительные метки, но этот набор служит хорошей отправной точкой.

1. Элементы коллекции в месте, установите **текст** свойство **метка** управления `ThisItem.Title`и **HtmlText** свойство **HTML-текст**  управления `ThisItem.Value`.

1. В **CalendarEventsGallery**, задайте **OnSelect** свойство **Title** управления следующую формулу:

    ```powerapps-dot
    Set( _selectedCalendarEvent, ThisItem );
    Navigate( EventDetailsScreen, None )
    ```

    > [!Note]
    > Вместо использования **_selectedCalendarEvent** переменных, можно использовать **CalendarEventsGallery**. Выбран.

### <a name="show-event-attendees"></a>Показать участников мероприятия

`Office365.GetEventsCalendarViewV2` Операция возвращает разные поля для каждого события, включая набор обязательных и необязательных участников разделенный точками с запятой. В этой процедуре будет анализировать каждый набор участников, выяснить, какие участники в вашей организации и извлечения любого, кто профили Office 365.

1. Если приложение не содержит соединителя пользователи Office 365, [добавляется](../add-data-connection.md).

1. Для получения Office 365 профили участников собрания, набора **OnSelect** свойство **Title** контролировать **CalendarEventsGallery** следующую формулу:

    ```powerapps-dot
    Set( _selectedCalendarEvent, ThisItem );
    ClearCollect( AttendeeEmailsTemp,
        Filter(
            Split( ThisItem.RequiredAttendees & ThisItem.OptionalAttendees, ";" ),
            !IsBlank( Result )
        )
    );
    ClearCollect( AttendeeEmails,
        AddColumns( AttendeeEmailsTemp, 
            "InOrg",
            Upper( _userDomain ) = Upper( Right( Result, Len( Result ) - Find( "@", Result ) ) )
        )
    );
    ClearCollect( MyPeople,
        ForAll( AttendeeEmails, If( InOrg, Office365Users.UserProfile( Result ) ) ) 
    );
    Collect( MyPeople,
        ForAll( AttendeeEmails,
            If( !InOrg, 
                { DisplayName: Result, Id: "", JobTitle: "", UserPrincipalName: Result }
            )
        )
    )
    ```

Этот список обсуждение о том, что **ClearCollect** операция включает:

- ClearCollect(AttendeeEmailsTemp)
    ```powerapps-dot
    ClearCollect( AttendeeEmailsTemp,
        Filter(
            Split( ThisItem.RequiredAttendees & ThisItem.OptionalAttendees, ";" ), 
            !IsBlank( Result)
        )
    );
    ```

    Эта формула объединяет обязательные и необязательные участники в одну строку и затем разделяет эту строку на отдельные адреса в каждой точке с запятой. Формула, а затем отфильтровывает пустых значений из этого набора и добавляет другие значения в коллекцию с именем **AttendeeEmailsTemp**.

- ClearCollect(AttendeeEmails)
    ```powerapps-dot
    ClearCollect( AttendeeEmails,
        AddColumns( AttendeeEmailsTemp, 
            "InOrg",
            Upper( _userDomain ) = Upper( Right( Result, Len(Result) - Find("@", Result) ) )
        )
    );
    ```
    Эта формула примерно определяет, является ли участник в вашей организации. Определение **_userDomain** просто домена URL-адрес в адрес электронной почты пользователя, запустившего приложение. Эта строка создает дополнительный столбец true или false, с именем **InOrg**в **AttendeeEmailsTemp** коллекции. Этот столбец содержит **true** Если **userDomain** эквивалентен URL-адрес домена адреса электронной почты в определенной строки из **AttendeeEmailsTemp**.

    Этот подход не всегда точна, но он получает довольно закрыть. Например, некоторые участники в вашей организации есть адрес электронной почты, например Jane@OnContoso.com, тогда как **_userDomain** — Contoso.com. Пользователь приложения и Мария могут работать в той же компании, но с небольшими вариациями вводят адреса электронной почты. Для подобных случаях можно использовать следующую формулу:

    `Upper(_userDomain) in Upper(Right(Result, Len(Result) - Find("@", Result)))`

    Тем не менее, эта формула совпадает с адресами электронной почты, например Jane@NotTheContosoCompany.com с **_userDomain** как Contoso.com, а также других пользователей не работают в той же компании.

- ClearCollect(MyPeople)

    ```powerapps-dot
    ClearCollect( MyPeople,
        ForAll( AttendeeEmails, 
            If( InOrg, 
                Office365Users.UserProfile( Result )
            )
        )
    );
    Collect( MyPeople,
        ForAll( AttendeeEmails,
            If( !InOrg, 
                { 
                    DisplayName: Result, 
                    Id: "", 
                    JobTitle: "", 
                    UserPrincipalName: Result
                }
            )
        )
    );
    ```
    Чтобы получить профили Office 365, необходимо использовать [Office365Users.UserProfile](https://docs.microsoft.com/connectors/office365users/#userprofile) или [Office365Users.UserProfileV2](https://docs.microsoft.com/connectors/office365users/#userprofile) операции. Эти операции сначала собрать все профили Office 365 для участников, которых нет пользователя организации. Операции, затем добавить несколько полей для участников из за пределами организации. Разделить эти два элемента на отдельные операции, так как **ForAll** цикл не гарантирует порядок. Таким образом **ForAll** сначала может собирать от участника за пределами организации. В данном случае схема для **MyPeople** содержит только **DisplayName**, **идентификатор**, **JobTitle**, и **UserPrincipalName** . Тем не менее операции UserProfile получить гораздо более подробные данные, чем. Поэтому вы принудительно **MyPeople** коллекции для добавления профилей Office 365 перед другими профилями.

    > [!NOTE]
    > Можно добиться того же результата с единственным **ClearCollect** функции:

    ```powerapps-dot
    ClearCollect( MyPeople, 
        ForAll(
            AddColumns(
                Filter(
                    Split(
                        ThisItem.RequiredAttendees & ThisItem.OptionalAttendees, 
                        ";"
                    ), 
                    !IsBlank( Result )
                ), 
                "InOrg", _userDomain = Right( Result, Len( Result ) - Find( "@", Result ) )
            ), 
            If( InOrg, 
                Office365Users.UserProfile( Result ), 
                { 
                    DisplayName: Result, 
                    Id: "", 
                    JobTitle: "", 
                    UserPrincipalName: Result, 
                    Department: "", 
                    OfficeLocation: "", 
                    TelephoneNumber: ""
                }
            )
        )
    )
    ```

Для завершения этого упражнения:

1. Добавить экран, содержащий коллекцию, для которого **элементы** свойству **MyPeople**.

1. В **OnSelect** свойство **Title** контролировать **CalendarEventsGallery**, добавьте **Navigate** работать на экран, создан на предыдущем шаге.

## <a name="next-steps"></a>Дальнейшие действия

* [Для этого экрана справочной документации по](calendar-screen-reference.md).
* [Дополнительные сведения о соединителе Office 365 Outlook](../connections/connection-office365-outlook.md).
* [Дополнительные сведения о соединителе пользователи Office 365](../connections/connection-office365-users.md).
