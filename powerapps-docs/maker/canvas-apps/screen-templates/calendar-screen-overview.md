---
title: Шаблон на экране календаря | Документация Майкрософт
description: Узнайте, как работает шаблон экрана календаря для приложений Canvas, изменяйте экран и расширяйте его как часть приложения.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/28/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9ca7e5f14508a2dcd70967e77b29989819bfe7ba
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541598"
---
# <a name="overview-of-the-calendar-screen-template-for-canvas-apps"></a>Общие сведения о шаблоне "Календарь-экран" для приложений Canvas

В приложении Canvas добавьте экран календаря, который показывает пользователям предстоящие события из их учетных записей Office 365 Outlook. Пользователи могут выбрать дату в календаре и прокручивать список событий этого дня. Можно изменить отображаемые сведения в списке, добавить второй экран с дополнительными сведениями о каждом событии, показать список участников для каждого события и внести другие настройки.

Можно также добавить другие экраны на основе шаблонов, которые показывают различные данные из Office 365, такие как [Электронная почта](email-screen-overview.md), [Пользователи](people-screen-overview.md) в Организации, а также [доступность](meeting-screen-overview.md) пользователей, которые могут пригласить на встречу.

В этом обзоре описывается:
> [!div class="checklist"]
> * Использование экрана календаря по умолчанию.
> * Как изменить его.
> * Как интегрировать его в приложение.

Более подробные сведения о функциональных возможностях этого экрана по умолчанию см. в [справочнике по календарю](calendar-screen-reference.md).

## <a name="prerequisite"></a>Необходимое условие

Знакомство с добавлением и настройкой экранов и других элементов управления при [создании приложения в PowerApps](../data-platform-create-app-scratch.md).

## <a name="default-functionality"></a>Функциональные возможности по умолчанию

Чтобы добавить экран календаря из шаблона, выполните следующие действия.

1. [Войдите](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) в PowerApps, а затем создайте приложение или откройте существующее приложение в PowerApps Studio.

    В этом разделе показано приложение для телефона, но те же принципы применимы к планшетному приложению.

1. На вкладке ленты **Главная** выберите **Новый экран** > **Календарь**.

    По умолчанию экран выглядит примерно так:

    ![Экран календаря](media/calendar-screen/calendar-initial.png)

1. Чтобы отобразить данные, выберите параметр в раскрывающемся списке в верхней части экрана.

    ![Экран календаря после загрузки завершен](./media/calendar-screen/calendar-screen.png)

Некоторые полезные Примечания:

* Текущая дата выбирается по умолчанию, и вы можете легко вернуться к ней, щелкнув значок календаря в правом верхнем углу.
* Если выбрать другую дату, круг окружает ее, а цветовой прямоугольник (синий — при применении темы по умолчанию) будет заключаться в текущую дату.
* Если по крайней мере одно событие запланировано на определенную дату, под этой датой в календаре появляется небольшой цветной круг.
* При выборе даты, для которой запланировано одно или несколько событий, события отображаются в списке под календарем.

## <a name="modify-the-screen"></a>Изменение экрана

Функциональные возможности по умолчанию этого экрана можно изменить несколькими распространенными способами.

* [Укажите календарь](calendar-screen-overview.md#specify-the-calendar).
* [Отображение различных сведений о событии](calendar-screen-overview.md#show-different-details-about-an-event).
* [Скрыть неблокирующие события](calendar-screen-overview.md#hide-nonblocking-events).

Если вы хотите изменить экран еще дальше, воспользуйтесь ссылкой на [экран календаря](./calendar-screen-reference.md) в качестве инструкции.

### <a name="specify-the-calendar"></a>Укажите календарь

Если вы уже знакомы с тем, какой календарь пользователи должны просматривать, можно упростить экран, указав этот календарь перед публикацией приложения. Это изменение устраняет необходимость в раскрывающемся списке календарей, поэтому вы можете удалить его.

1. Задайте для свойства **[OnStart](../controls/control-screen.md)** экрана по умолчанию в приложении следующую формулу:

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
    > Эта формула немного редактируется из значения по умолчанию свойства **OnSelect** раскрывающегося списка для выбора календаря. Дополнительные сведения об этом элементе управления см. в разделе ссылки на [экран календаря](./calendar-screen-reference.md#calendar-drop-down).

1. Замените `{YourCalendarNameHere}`, включая фигурные скобки, на имя календаря, который требуется отобразить (например, **Calendar**).

    > [!IMPORTANT]
    > В следующих шагах предполагается, что вы добавили в приложение только один экран календаря. Если добавлено более одного имени элемента управления (например, **iconCalendar1**), оно будет заканчиваться другим числом, и необходимо соответствующим образом скорректировать формулы.

1. Задайте для свойства **Y** элемента управления **iconCalendar1** следующее выражение:

    `RectQuickActionBar1.Height + 20`

1. Задайте для свойства **Y** элемента управления **LblMonthSelected1** следующее выражение:

    `iconCalendar1.Y + iconCalendar1.Height + 20`

1. Задайте для свойства **Text** элемента управления **LblNoEvents1** это значение:

    `"No events scheduled"`

1. Задайте для свойства **Visible** объекта **LblNoEvents1** следующую формулу:

    `CountRows(CalendarEventsGallery1.AllItems) = 0 && _calendarVisible`

1. Удалите эти элементы управления:

    - **dropdownCalendarSelection1**
    - **LblEmptyState1**
    - **iconEmptyState1**

1. Если экран календаря не является экраном по умолчанию, добавьте кнопку, которая переходит с экрана по умолчанию на экран календаря, чтобы можно было протестировать приложение.

    Например, добавьте кнопку в **Screen1** , которая переходит к **Screen2** , если вы добавили экран календаря в приложение, созданное из пустого окна.

1. Сохраните приложение, а затем протестируйте его в браузере или на мобильном устройстве.

### <a name="show-different-details-about-an-event"></a>Отображение различных сведений о событии

По умолчанию в галерее в календаре с именем **календаревентсгаллери**отображается время начала, длительность, тема и расположение каждого события. В галерее можно настроить отображение любого поля (например, организатора), поддерживаемого [соединителем Office 365](https://docs.microsoft.com/connectors/office365/#calendareventclientreceive) .

1. В **календаревентсгаллери**задайте для свойства **Text** новой или существующей метки значение `ThisItem`, за которым следует точка.

    IntelliSense перечисляет поля, которые можно выбрать.

1. Выберите нужное поле.

    Метка показывает тип указанной информации.

### <a name="hide-nonblocking-events"></a>Скрыть неблокирующие события

Во многих офисах участники группы отправляют приглашения на собрание, чтобы уведомить друг друга о том, что они будут находиться за пределами офиса. Чтобы предотвратить блокирование расписаний всех пользователей, пользователь, отправляющий запрос, устанавливает его доступность для **бесплатной**работы. Вы можете скрыть эти события из календаря и коллекции, обновив несколько свойств.

1. Задайте для свойства **Items** элемента **календаревентсгаллери** следующую формулу:

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

    В этой формуле функция **Filter** скрывает не только те события, которые запланированы на дату, отличную от выбранной, но также события, для которых для параметра доступность задано значение **Free**.

1. В календаре задайте для свойства **Visible** элемента управления **Circle** следующую формулу:

    ```powerapps-dot
    CountRows(
        Filter(
            MyCalendarEvents,
            DateValue( Text(Start) ) = DateAdd( _firstDayInView, ThisItem.Value, Days ),
            ShowAs <> "Free"
        )
    ) > 0 && !Subcircle1.Visible && Title2.Visible
    ```
    Эта формула содержит те же фильтры, что и Предыдущая формула. Таким образом, окружность индикатора событий отображается под датой только в том случае, если у нее есть одно или несколько событий, которые относятся к выбранной дате и для которых уровень доступности не равен **Free**.

## <a name="integrate-the-screen-into-an-app"></a>Интеграция экрана в приложение

Экран календаря — это мощный набор элементов управления в своем собственном расположении, но он обычно работает как часть более крупного, более универсального приложения. Этот экран можно интегрировать в крупное приложение несколькими способами, включая добавление следующих параметров:

* [Просмотр сведений о событии](calendar-screen-overview.md#view-event-details).
* [Показывать участников события](calendar-screen-overview.md#show-event-attendees).

### <a name="view-event-details"></a>Просмотр сведений о событии

Если пользователь выберет событие в **календаревентсгаллери**, можно открыть другой экран с дополнительными сведениями об этом событии.

> [!NOTE]
> Эта процедура показывает сведения о событиях в галерее с динамическим содержимым, но вы можете добиться аналогичных результатов, используя другие подходы. Например, можно получить дополнительный контроль над конструктором, используя вместо этого ряд меток.

1. Добавьте пустой экран с именем **евентдетаилсскрин**, который содержит пустую коллекцию гибкой высоты и кнопку, которая перейдет к экрану календаря.

1. В коллекции гибких высот добавьте элемент управления **Label** и **HTML Text** и установите для свойства **автовысота** **значение true**.

    > [!NOTE]
    > PowerApps извлекает текст сообщения каждого события в виде текста HTML, поэтому необходимо отобразить это содержимое в **HTML-** элементе управления "текст".

1. Задайте для свойства **Y** **HTML Text** элемента управления следующее выражение:

    `Label1.Y + Label1.Height + 20`

1. При необходимости настройте дополнительные свойства в соответствии с потребностями стиля.

    Например, может потребоваться добавить разделительную линию под элементом управления **HTML Text** .

1. Задайте для свойства **Items** коллекции гибкой высоты следующую формулу:

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

    Эта формула создает коллекцию динамических данных, для которой заданы значения полей **_selectedCalendarEvent**, которые устанавливаются каждый раз, когда пользователь выбирает событие в элементе управления **календаревентсгаллери** . Вы можете расширить эту галерею, включив в нее дополнительные поля, добавив в нее дополнительные метки, но этот набор обеспечивает хорошую отправную точку.

1. Заполнив элементы коллекции, задайте для свойства **Text** элемента управления **Label** значение `ThisItem.Title`, а для свойства «текст **» элемента** управления **HTML Text** — значение `ThisItem.Value`.

1. В **календаревентсгаллери**задайте для свойства **OnSelect** элемента управления **Title** следующую формулу:

    ```powerapps-dot
    Set( _selectedCalendarEvent, ThisItem );
    Navigate( EventDetailsScreen, None )
    ```

    > [!Note]
    > Вместо использования переменной **_selectedCalendarEvent** можно использовать **календаревентсгаллери**. Выбрать.

### <a name="show-event-attendees"></a>Показывать участников мероприятия

Операция `Office365.GetEventsCalendarViewV2` извлекает различные поля для каждого события, включая набор обязательных и необязательных участников, разделенных точкой с запятой. В этой процедуре вы проанализируете каждый набор участников, определяете, какие участники в вашей организации и получаете ли они профили Office 365.

1. Если приложение не содержит соединитель пользователей Office 365, [добавьте его](../add-data-connection.md).

1. Чтобы получить профили Office 365 участников встречи, задайте для свойства **OnSelect** элемента управления **Title** в **календаревентсгаллери** следующую формулу:

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

В этом списке описывается, что делает каждая операция **клеарколлект** :

- Клеарколлект (Аттендиемаилстемп)
    ```powerapps-dot
    ClearCollect( AttendeeEmailsTemp,
        Filter(
            Split( ThisItem.RequiredAttendees & ThisItem.OptionalAttendees, ";" ), 
            !IsBlank( Result)
        )
    );
    ```

    Эта формула объединяет обязательные и необязательные участники в одну строку, а затем разделяет эту строку на отдельные адреса с каждой точкой с запятой. Затем формула отфильтровывает пустые значения из этого набора и добавляет другие значения в коллекцию с именем **аттендиемаилстемп**.

- Клеарколлект (Аттендиемаилс)
    ```powerapps-dot
    ClearCollect( AttendeeEmails,
        AddColumns( AttendeeEmailsTemp, 
            "InOrg",
            Upper( _userDomain ) = Upper( Right( Result, Len(Result) - Find("@", Result) ) )
        )
    );
    ```
    Эта формула приблизительно определяет, находится ли участник в вашей организации. Определение **_userDomain** — это просто URL-адрес домена в адресе электронной почты пользователя, запустившего приложение. Эта строка создает дополнительный столбец true/false с именем **инорг**в коллекции **аттендиемаилстемп** . Этот столбец содержит **значение true** , если **доменпользователя** эквивалентен URL-адресу домена адреса электронной почты в этой конкретной строке **аттендиемаилстемп**.

    Этот подход не всегда точен, но он довольно близок. Например, некоторые участники Организации могут иметь адрес электронной почты, например Jane@OnContoso.com, а **_userDomain** — contoso.com. Пользователь приложения и Мария могут работать в одной компании, но иметь небольшие вариации в своих адресах электронной почты. В таких случаях может потребоваться использовать следующую формулу:

    `Upper(_userDomain) in Upper(Right(Result, Len(Result) - Find("@", Result)))`

    Однако эта формула соответствует адресам электронной почты, таким как Jane@NotTheContosoCompany.com, с **_userDomain** , например contoso.com, и эти люди не работают в одной компании.

- Клеарколлект (Мипеопле)

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
    Чтобы получить профили Office 365, необходимо использовать операцию [Office365Users. UserProfile](https://docs.microsoft.com/connectors/office365users/#userprofile) или [Office365Users. UserProfileV2](https://docs.microsoft.com/connectors/office365users/#userprofile) . Эти операции сначала собирают все профили Office 365 для участников, которые находятся в организации пользователя. Затем операции добавляют несколько полей для участников за пределами Организации. Вы разделяете эти два элемента на разные операции, так как цикл **ForAll** не гарантирует порядок. Таким образом, **ForAll** может сначала получить участника, находящегося за пределами Организации. В этом случае схема для **мипеопле** содержит только **DisplayName**, **ID**, **JobTitle**и **userPrincipalName**. Однако операции UserProfile извлекают намного более широкие данные, чем это. Поэтому вы принудительно добавляете в коллекцию **мипеопле** профили Office 365 перед другими профилями.

    > [!NOTE]
    > Тот же результат можно получить только с одной функцией **клеарколлект** :

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

Чтобы завершить это упражнение:

1. Добавьте экран, содержащий коллекцию, для которой свойство **Items** имеет значение **мипеопле**.

1. В свойстве **OnSelect** элемента управления **Title** в **календаревентсгаллери**добавьте функцию **navigate** на экран, созданный на предыдущем шаге.

## <a name="next-steps"></a>Дальнейшие действия

* [Просмотрите справочную документацию по этому экрану](calendar-screen-reference.md).
* Дополнительные [сведения о соединителе Office 365 Outlook](../connections/connection-office365-outlook.md).
* Дополнительные [сведения о соединителе пользователей Office 365](../connections/connection-office365-users.md).
