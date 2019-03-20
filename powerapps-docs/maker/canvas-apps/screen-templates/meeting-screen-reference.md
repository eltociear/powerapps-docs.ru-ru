---
title: Справочник по шаблон экрана собрания для приложений на основе холста | Документация Майкрософт
description: Понимание деталей того, как работает шаблон экрана собрания для приложений на основе холста в PowerApps
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/03/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a7559f84b43d3c0372dea71d49c35461ba9d4e57
ms.sourcegitcommit: 5e15a1033a68289781f8092fb65c57432501f911
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54459535"
---
# <a name="reference-information-about-the-meeting-screen-template-for-canvas-apps"></a>Справочные сведения о шаблоне собрания экрана для приложений на основе холста

Для приложений на основе холста в PowerApps Узнайте, как каждый значительные элемент управления в шаблоне собрания экрана помогает реализовать экран общую функциональность по умолчанию. Этот видеокурс представляется формулах поведения и значения других свойств, которые определяют, каким образом элементы управления реагирует на действия пользователя. Обзорное обсуждение функциональные возможности по умолчанию на этом экране, см. в разделе [Обзор экрана собрания](meeting-screen-overview.md).

В этом разделе представлены некоторые существенные элементы управления и описываются выражения или формулы для различных свойства (такие как **элементы** и **OnSelect**) из этих элементов управления заданы:

* [Invite tab (LblInviteTab)](#invite-tab)
* [Вкладка "Расписание" (LblScheduleTab)](#schedule-tab)
* [Текстовое поле поиска](#text-search-box)
* [Добавить значок (AddIcon)](#add-icon)
* [Люди найти в коллекции](#people-browse-gallery) (+ дочерние элементы управления)
* [Коллекции пользователей собрания](#meeting-people-gallery) (+ дочерние элементы управления)
* [Выбор даты собрания (MeetingDateSelect)](#meeting-date-picker)
* [Раскрывающегося списка продолжительность собрания (MeetingDurationSelect)](#meeting-duration-drop-down)
* [Найти время собрания коллекции](#find-meeting-times-gallery) (+ дочерние элементы управления)
* [Комнаты обзор коллекции](#room-browse-gallery) (+ дочерние элементы управления)
* [Назад шеврон (RoomsBackNav)](#back-chevron) (не может быть видимым в том случае, если у клиента нет комнат списки)
* [Значок "Отправить"](#send-icon)

## <a name="prerequisite"></a>Необходимое условие

Знакомство с тем, как добавить и настроить экраны и другие элементы управления, как вы [Создание приложения в PowerApps](../data-platform-create-app-scratch.md).

## <a name="invite-tab"></a>Пригласить вкладку

   ![Элемент управления LblInviteTab](media/meeting-screen/meeting-invite-text.png)

* Свойство: **Цвет**<br>
    Значение: `If( _showDetails, LblRecipientCount.Color, RectQuickActionBar.Fill )`

    **_showDetails** является переменная, используемая для определения ли **LblInviteTab** управления или **LblScheduleTab** выборе элемента управления. Если значение **_showDetails** — **true**, **LblScheduleTab** установлен; Если значение равно **false**, **LblInviteTab**  выбран. Это означает, что если значение **_showDetails** — **true** (на этой вкладке *не* выбранного), цвета вкладки соответствие **LblRecipientCount**. В противном случае оно совпадает со значением fill **RectQuickActionBar**.

* Свойство: **OnSelect**<br> 
    Значение: `Set( _showDetails, false )`

    Наборы **_showDetails** переменной **false**, это означает, что содержимое вкладки приглашение являются видимыми, а содержимое **расписание** вкладки скрыты.

## <a name="schedule-tab"></a>Вкладка "Расписание"

   ![Элемент управления LblInviteTab](media/meeting-screen/meeting-schedule-text.png)

* Свойство: **Цвет**<br>
    Значение: `If( !_showDetails, LblRecipientCount.Color, RectQuickActionBar.Fill )`

    **_showDetails** является переменная, используемая для определения ли **LblInviteTab** управления или **LblScheduleTab** выборе элемента управления. Если это значение равно true, **LblScheduleTab** установлен; Если значение равно false, **LblInviteTab** является. Это означает, что если **_showDetails** имеет значение true (на этой вкладке *—* выбранного), цвета вкладки совпадает со значением fill **RectQuickActionBar**. В противном случае оно совпадает со значением цвета **LblRecipientCount**.

* Свойство: **OnSelect**<br>
    Значение: `Set( _showDetails, true )`

    Наборы **_showDetails** переменной **true**, что означает содержимое вкладка "Расписание" являются видимыми, а содержимое вкладки приглашение скрыты.

## <a name="text-search-box"></a>Текстовое поле поиска

   ![Элемент управления TextSearchBox](media/meeting-screen/meeting-search-box.png)

<!--Include description of text search box control?-->

Несколько других элементов управления на экране имеют зависимость от такой:

* Если пользователь начинает вводить любой текст, **PeopleBrowseGallery** становится видимым.
* Если пользователь вводит допустимый адрес электронной почты, **AddIcon** становится видимым.
* Когда пользователь выбирает пользователе **PeopleBrowseGallery** поиска содержимого, будут заменены.

## <a name="add-icon"></a>Значок добавления

   ![Элемент управления AddIcon](media/email-screen/email-add-icon.png)

Этот элемент управления позволяет пользователям добавлять людей, которые не существуют в их организации в список участников, для которого формируются собрания.

* Свойство: **Видимым**<br>
    Значение: Три логических проверяет, что все они должны возвращать для **true** для элемента управления должен отображаться:

    ```powerapps-dot
    !IsBlank( TextSearchBox.Text ) &&
        IsMatch( TextSearchBox.Text, Match.Email ) &&
        Not( Trim( TextSearchBox.Text ) in MyPeople.UserPrincipalName )
    ```

  Построчно, этот блок кода говорится, что **AddIcon** элемент управления является видимым только если:

  * **TextSearchBox** содержит текст.
  * Текст в **TextSearchBox** — это адрес электронной почты.
  * Текст в **TextSearchBox** еще не существует в **MyPeople** коллекции.

* Свойство: **OnSelect**<br> 
    Значение: Объект **собирать** список инструкцию, чтобы добавить пользователя для этого участника, другой, чтобы обновить доступные встреч и несколько переменных переключатели:

    ```powerapps-dot
    Collect( MyPeople,
        { 
            DisplayName: TextSearchBox.Text, 
            UserPrincipalName: TextSearchBox.Text, 
            Mail: TextSearchBox.Text
        }
    );
    Concurrent(
        Reset( TextSearchBox ),
        Set( _showMeetingTimes, false ),
        UpdateContext( { _loadMeetingTimes: true } ),
        Set( _selectedMeetingTime, Blank() ),
        Set( _selectedRoom, Blank() ),
        Set( _roomListSelected, false ),
        ClearCollect( MeetingTimes, 
            AddColumns(
                'Office365'.FindMeetingTimes(
                    { 
                        RequiredAttendees: Concat(MyPeople, UserPrincipalName & ";")
                        MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                        Start: Text( DateAdd( MeetingDateSelect.SelectedDate, 8, Hours ), UTC ),
                        End: Text( DateAdd( MeetingDateSelect.SelectedDate, 17, Hours ), UTC ),
                        MaxCandidates: 15, 
                        MinimumAttendeePercentage:1, 
                        IsOrganizerOptional: false, 
                        ActivityDomain: "Work"
                    }
                ).MeetingTimeSuggestions,
                "StartTime", MeetingTimeSlot.Start.DateTime, 
                "EndTime", MeetingTimeSlot.End.DateTime
            )
        )
    );
    UpdateContext( { _loadingMeetingTimes: false } );
    Set( _showMeetingTimes, true )
    ```

  Выбор этого элемента управления добавляет допустимый адрес электронной почты (отображается только в том случае, если допустимый адрес электронной почты, введенного в **TextSearchBox**) для **MyPeople** коллекции, (данной коллекции в список участников) и затем обновляет доступных встреч с новой записью пользователя.

  На низком уровне, этот блок кода:
  1. Получает значение адреса электронной почты в **MyPeople** коллекции, сбор адрес электронной почты в **DisplayName**, **UserPrincipalName**, и **почты**  поля.
  1. Сбрасывает содержимое **TextSearchBox** элемента управления.
  1. Наборы **_showMeetingTimes** переменной **false**. Эта переменная определяет видимость **FindMeetingTimesGallery**, который отображает откройте раз для выбранных участников в соответствии с.
  1. Наборы **_loadMeetingTimes** переменной контекста для **true**. Эта переменная задает состояние загрузки, который переключает видимость для загрузки состояния элементов управления, как **_LblTimesEmptyState** чтобы указать пользователю на загрузку данных.
  1. Наборы **_selectedMeetingTime** для **Blank()**. **_selectedMeetingTime** является выбранной записи из **FindMeetingTimesGallery** элемента управления. Он отключается здесь потому, что Добавление участника означает, что предыдущее определение **_selectedMeetingTime** будет недоступен для данного участника.
  1. Наборы **_selectedRoom** для **Blank()**. **_selectedRoom** , является записью выбранного места **RoomBrowseGallery**. Сведения о доступности места определяются, исходя из значения **_selectedMeetingTime**. С этим значением произведено запирание лучевой трубки **_selectedRoom** значение больше не является допустимым, поэтому он должен производиться.
  1. Наборы **_roomListSelected** для **false**. Нельзя использовать для всех пользователей этой строки. В Office, можно группировать в комнатах разными «списки помещений.» Если у вас есть список помещений, этот экран учетных записей для этого, теперь вы можете сначала выберите список помещений перед выбором комнаты из списка. Значение **_roomListSelected** определяет, может ли пользователь (в клиенте с помощью только список помещений) будут видеть комнаты в списке помещений или набор списков помещений. Ему будет присвоено **false** заставить пользователей, чтобы повторно выбрать новый список помещений.
  1. Использует [Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) операции для определения и сбора доступны встреч для участников. Эта операция проходит успешно:
      * **UserPrincipalName** каждого выбранного пользователя в *RequiredAttendees* параметра.
      * **MeetingDurationSelect**. Selected.Minutes в *MeetingDuration* параметра.
      * MeetingDateSelect.SelectedDate + 8 часов в *запустить* параметра. Восемь часов добавляется в том случае, поскольку по умолчанию полный формат даты/времени для элемента управления calendar — 12:00 AM от выбранной даты. Скорее всего, нужно получить сведения о доступности в обычное рабочее время. Время начала нормальной работы будет 8:00 AM.
      * **MeetingDateSelect**. SelectedDate + 17 часов в *окончания* параметра. 17 ч добавляется, так как 12:00 AM + 17 = 17:00:00. Время окончания обычной рабочей бы 17:00:00.
      * *15* в *MaxCandidates* параметра. Это означает, что операция возвращает только первые 15 доступное время для выбранной даты. Это разумно, так как в 8 часов рабочего дня имеется только шестнадцать блоки 30-минутные и 30-минутные собрания — минимальный, можно установить на этом экране.
      * *1* в *MinimumAttendeePercentage* параметра. По сути Если ни один из участников недоступны, извлекается время собрания.
      * **false** в *IsOrganizerOptional* параметра. Пользователь приложения не Необязательный участник собрания.
      * «Работа» в *ActivityDomain* параметра. Это означает, что время получения отображаются только в обычное рабочее время период.
  1. **ClearCollect** функция также добавляет два столбца: «StartTime» и «EndTime». Это упрощает возвращаемых данных. 
  — Поле, содержащее доступные время начала и окончания **MeetingTimeSlot** поля. Это поле представляет запись, содержащую начала и окончания записи, которые в свою очередь содержат **DateTime** и **часовой пояс** значения их соответствующих предложений. Не пытается получить такого вложения записей, добавление столбцов «StartTime» и «EndTime» для **MeetingTimes** коллекции переводит их **Пуск > даты и времени** и **окончания > DateTime** значения в область коллекции.
  1. По завершении этих функций все **_loadingMeetingTimes** переменной присваивается **false**, удаление состояния загрузки и **_showMeetingTimes** присваивается **true**, отображение **FindMeetingTimesGallery**.

## <a name="people-browse-gallery"></a>Обзор коллекции пользователей

   ![Элемент управления PeopleBrowseGallery](media/meeting-screen/meeting-browse-gall.png)

* Свойство: **Элементы**<br>
    Значение: 
    ```powerapps-dot
    If( !IsBlank( Trim( TextSearchBox.Text ) ), 
        'Office365Users'.SearchUser( { searchTerm: Trim(TextSearchBox.Text), top: 15 } )
    )
    ```

Элементы этой коллекции, заполняются путем результаты поиска из [Office365.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) операции. Операция принимает текст `Trim(**TextSearchBox**)` как поиск термина и возвращает результаты 15 первых на основе поиска.
  
**TextSearchBox** упаковывается в **Trim** работать, поскольку является недопустимой, поиск пользователей на пробелы. `Office365Users.SearchUser` Операции упаковывается в `If(!IsBlank(Trim(TextSearchBox.Text)) ... )` работать, поскольку получение результатов поиска, прежде чем поиск пользователя — к повышенному расходу производительности.

### <a name="people-browse-gallery-title"></a>Обзор коллекции людей Title

   ![Элемент управления PeopleBrowseGallery заголовок](media/meeting-screen/meeting-browse-gall-title.png)

* Свойство: **Текст**<br>
    Значение: `ThisItem.DisplayName`

    Отображает имя пользователя из профиля Office 365.

* Свойство: **OnSelect**<br>
    Значение: Объект **собирать** список инструкцию, чтобы добавить пользователя для этого участника, другой, чтобы обновить доступные встреч и несколько переменных переключатели:

    ```powerapps-dot
    Concurrent(
        Reset( TextSearchBox ),
        Set( _selectedUser, ThisItem ),
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ), 
            Collect( MyPeople, ThisItem ); 
            Concurrent(
                Set( _showMeetingTimes, false ),
                UpdateContext( { _loadMeetingTimes: true } ),
                Set( _selectedMeetingTime, Blank() ),
                Set( _selectedRoom, Blank() ),
                Set( _roomListSelected, false ),
                ClearCollect( MeetingTimes, 
                    AddColumns(
                        'Office365'.FindMeetingTimes(
                            {
                                RequiredAttendees: Concat( MyPeople, UserPrincipalName & ";" ),
                                MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                                Start: Text( DateAdd( MeetingDateSelect.SelectedDate, 8, Hours ), UTC ),
                                End: Text( DateAdd( MeetingDateSelect.SelectedDate, 17, Hours ), UTC ),
                                MaxCandidates: 15, 
                                MinimumAttendeePercentage: 1, 
                                IsOrganizerOptional: false, 
                                ActivityDomain: "Work"
                            }
                        ).MeetingTimeSuggestions,
                        "StartTime", MeetingTimeSlot.Start.DateTime, 
                        "EndTime", MeetingTimeSlot.End.DateTime
                    )
                )
            );
            UpdateContext( { _loadingMeetingTimes: false } );
            Set( _showMeetingTimes, true )
        )
    )
    ```

    На высоком уровне, выбор этого элемента управления добавляет пользователю **MyPeople** коллекции (хранилище приложение из списка участников) и обновления доступных встреч основаны на добавление нового пользователя.

    Выбор этого элемента управления очень похожа на выбор **AddIcon** управления; единственная разница в том, `Set(_selectedUser, ThisItem)` инструкции и порядок выполнения операций. Таким образом данного обсуждения будет секрет. Дополнительные сведения, прочитайте [AddIcon управления](#add-icon) раздел.

    Выбор этого элемента управления сбрасывает **TextSearchBox**. Затем, если выделение не находится в **MyPeople** коллекции, элемент управления:
    1. Наборы **_loadMeetingTimes** состояние **true** и **_showMeetingTimes** состояние **false**, пустые значения **_ selectedMeetingTime** и **_selectedRoom** переменных и обновляет **MeetingTimes** коллекции с новым дополнением к **MyPeople** коллекции. 
    1. Задает **_loadMeetingTimes** состояние **false**и задает **_showMeetingTimes** для **true**. Если выделение уже **MyPeople** коллекции, он сбрасывает только содержимое **TextSearchBox**.

## <a name="meeting-people-gallery"></a>Коллекции пользователей собрания

   ![Элемент управления MeetingPeopleGallery](media/meeting-screen/meeting-people-gall.png)

* Свойство: **Элементы**<br>
    Значение: `MyPeople`

    **MyPeople** коллекция является коллекцией людей инициализируется или добавить, выбрав **PeopleBrowseGallery Title** элемента управления.

* Свойство: **Высота**<br>
    Значение: Логика, позволяющая увеличится до максимальной высоты 350 коллекции:

    ```powerapps-dot
    Min( 
        76 * RoundUp( CountRows( MeetingPeopleGallery.AllItems ) / 2, 0 ),
        350
    )
    ```

  
   К числу элементов в коллекции, до максимальной высоты 350 подстраивается высота элемента коллекции. Формула принимает в качестве высоту одной строки 76 **MeetingPeopleGallery**, умножает его на число строк. **WrapCount** свойство имеет значение 2, поэтому число строк, значение true, `RoundUp(CountRows(MeetingPeopleGallery.AllItems) / 2, 0)`.

* Свойство: **ShowScrollbar**<br>
    Значение: `MeetingPeopleGallery.Height >= 350`

    При достижении максимальную высоту элемента коллекции (350) полоса прокрутки является видимым.

### <a name="meeting-people-gallery-title"></a>Коллекции пользователей собрания Title

   ![Элемент управления MeetingPeopleGallery заголовок](media/meeting-screen/meeting-people-gall-title.png)

* Свойство: **OnSelect**<br>
    
    Значение: `Set(_selectedUser, ThisItem)`
    
    Наборы **_selectedUser** переменных для элемента, выбранного в **MeetingPeopleGallery**.

### <a name="meeting-people-gallery-iconremove"></a>IconRemove коллекции людей собрания

   ![Элемент управления iconRemove MeetingPeopleGallery](media/meeting-screen/meeting-people-gall-delete.png)

* Свойство: **OnSelect**<br>
    Значение: Объект **удалить** инструкцию, чтобы удалить пользователя из списка участников, **собирать** инструкцию, чтобы обновить доступные встреч и несколько переменных переключатели:

    ```powerapps-dot
    Remove( MyPeople, LookUp( MyPeople, UserPrincipalName = ThisItem.UserPrincipalName ) );
    Concurrent(
        Reset( TextSearchBox ),
        Set( _showMeetingTimes, false ),
        UpdateContext( { _loadMeetingTimes: true } ),
        Set( _selectedMeetingTime, Blank() ),
        Set( _selectedRoom, Blank() ),
        Set( _roomListSelected, false ),
        ClearCollect( MeetingTimes, 
            AddColumns(
                'Office365'.FindMeetingTimes(
                    {
                        RequiredAttendees: Concat( MyPeople, UserPrincipalName & ";" ), 
                        MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                        Start: Text( DateAdd( MeetingDateSelect.SelectedDate, 8, Hours ), UTC ), 
                        End: Text( DateAdd( MeetingDateSelect.SelectedDate, 17, Hours ), UTC ),
                        MaxCandidates: 15, 
                        MinimumAttendeePercentage: 1, 
                        IsOrganizerOptional: false, 
                        ActivityDomain: "Work"
                    }
                ).MeetingTimeSuggestions,
                "StartTime", MeetingTimeSlot.Start.DateTime, 
                "EndTime", MeetingTimeSlot.End.DateTime
            )
        )
    );
    UpdateContext( { _loadingMeetingTimes: false } );
    Set( _showMeetingTimes, true )
    ```

  На высоком уровне Выбор этого элемента управления удаляет пользователя из списка участников и обновляет доступных собрания моменты, основываясь на удаление этого пользователя.

  После выполнения предыдущего кода первой строки, выбор этого элемента управления практически идентичен выбрав **AddIcon** элемента управления. Таким образом это обсуждение не будет секрет. Дополнительные сведения, прочитайте [раздел управления AddIcon](#add-icon).

  В первой строке кода, выбранный элемент удаляется из **MyPeople** коллекции. Затем код:
  1. Сбрасывает **TextSearchBox**и затем отменяет выбор в **MyPeople** коллекции. 
  1. Наборы **_loadMeetingTimes** состояние **true** и **_showMeetingTimes** состояние **false**, пустые значения **_ selectedMeetingTime** и **_selectedRoom** переменных и обновляет **MeetingTimes** коллекции с новым дополнением к **MyPeople** коллекции. 
  1. Задает **_loadMeetingTimes** состояние **false**и задает **_showMeetingTimes** для **true**.

## <a name="meeting-date-picker"></a>Выбор даты собрания

   ![Элемент управления MeetingDateSelect](media/meeting-screen/meeting-datepicker.png)

* Свойство: **DisplayMode**<br>
    Значение: `If( IsEmpty(MyPeople), DisplayMode.Disabled, DisplayMode.Edit )`

    Нельзя выбрать дату собрания, пока не будет добавлен хотя бы один участник **MyPeople** коллекции.

* Свойство: **OnChange**<br>
    Значение: `Select( MeetingDateSelect )`

    Изменение выбранной даты запускает код в **OnSelect** свойство данного элемента управления для запуска.

* Свойство: **OnSelect**<br>
    Значение: Объект **собирать** инструкцию, чтобы обновить доступные встреч и несколько переменных переключатели:
  
    ```powerapps-dot
    Concurrent(
        Reset( TextSearchBox ),
        Set( _showMeetingTimes, false ),
        UpdateContext( { _loadingMeetingTimes: true } ),
        Set( _selectedMeetingTime, Blank() ),
        Set( _selectedRoom, Blank() ),
        Set( _roomListSelected, false ),
        ClearCollect( MeetingTimes, 
            AddColumns(
                'Office365'.FindMeetingTimes(
                    {
                        RequiredAttendees: Concat( MyPeople, UserPrincipalName & ";" ), 
                        MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                        Start: Text( DateAdd( MeetingDateSelect.SelectedDate, 8, Hours ), UTC ), 
                        End: Text( DateAdd( MeetingDateSelect.SelectedDate, 17, Hours ), UTC ),
                        MaxCandidates: 15, 
                        MinimumAttendeePercentage: 1, 
                        IsOrganizerOptional: false, 
                        ActivityDomain: "Work"
                    }
                ).MeetingTimeSuggestions,
                "StartTime", MeetingTimeSlot.Start.DateTime, 
                "EndTime", MeetingTimeSlot.End.DateTime
            )
        )
    );
    UpdateContext( { _loadingMeetingTimes: false } );
    Set( _showMeetingTimes, true )
    ```

  На высоком уровне Выбор этого элемента управления обновляет доступных встреч. Поэтому важно потому, что если пользователь изменит дату, время доступные собрания следует выполнить обновление до отражают сведения о доступности участников за этот день.

  За исключением первоначального **собирать** инструкции, этот подход аналогичен **OnSelect** функциональных возможностей **AddIcon** элемента управления. Таким образом это обсуждение не будет секрет. Дополнительные сведения, прочитайте [AddIcon управления](#add-icon) раздел.

  Выбор этого элемента управления сбрасывает **TextSearchBox**. И она затем: 
  1. Наборы **_loadMeetingTimes** состояние **true** и **_showMeetingTimes** состояние **false**, пустые значения **_ selectedMeetingTime** и **_selectedRoom** переменных и обновляет **MeetingTimes** коллекции с выбором даты. 
  1. Задает **_loadMeetingTimes** состояние **false**и задает **_showMeetingTimes** для **true**.

## <a name="meeting-duration-drop-down"></a>Продолжительность собрания раскрывающегося списка

   ![Элемент управления MeetingDateSelect](media/meeting-screen/meeting-timepicker.png)

* Свойство: **DisplayMode**<br>
    Значение: `If( IsEmpty(MyPeople), DisplayMode.Disabled, DisplayMode.Edit )`

    Нельзя выбрать продолжительность собрания, пока не будет добавлен хотя бы один участник **MyPeople** коллекции.

* Свойство: **OnChange**<br>
    Значение: `Select(MeetingDateSelect1)`

    Изменить выбранный период времени запускает код в **OnSelect** свойство **MeetingDateSelect** элемент управления будет работать.

## <a name="find-meeting-times-gallery"></a>Найти время собрания коллекции

   ![Элемент управления FindMeetingTimesGallery](media/meeting-screen/meeting-time-gall.png)

* Свойство: **Элементы**<br>
    Значение: `MeetingTimes`

    Коллекция возможных встреч полученные из [Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) операции.

* Свойство: **Видимым**<br>
    Значение: `_showMeetingTimes && _showDetails && !IsEmpty( MyPeople )`

    Коллекции отображается только если **_showMeetingTimes** имеет значение **true**, пользователь выбрал **LblScheduleTab** элемента управления и имеется по крайней мере один участник добавлен собрания.

### <a name="find-meeting-times-gallery-title"></a>Найти время собрания коллекции Title

   ![Элемент управления FindMeetingTimesGallery заголовок](media/meeting-screen/meeting-time-gall-title.png)

* Свойство: **Текст**<br>
    Значение: Преобразование времени начала для отображения в локальное время пользователя:

    ```powerapps-dot
    Text(
        DateAdd(
            DateTimeValue( ThisItem.StartTime ),
            - TimeZoneOffset(), 
            Minutes
        ),
        DateTimeFormat.ShortTime
    )
    ```

  Извлеченное значение из **StartTime** представлено в формате UTC. Чтобы [преобразовать из формата UTC в местное время](../functions/function-dateadd-datediff.md#converting-from-utc), **DateAdd** применяется функция.
  [Функция Text](../functions/function-text.md#datetime) принимает даты и времени в качестве первого аргумента и форматы, оно зависит от второго аргумента. Передайте его для преобразования местного времени **ThisItem.StartTime**и отображает его как **DateTimeFormat.ShortTime**.

* Свойство: **OnSelect**<br>
    Значение: Несколько **собирать** инструкций для сбора помещений для собраний и их предлагаемые сведения о доступности, а также несколько переменных переключатели:

    ```powerapps-dot
    Set( _selectedMeetingTime, ThisItem );
    UpdateContext( { _loadingRooms: true } );
    If( IsEmpty( RoomsLists ),
        ClearCollect( RoomsLists, 'Office365'.GetRoomLists().value) );
    If( CountRows( RoomsLists ) <= 1,
        Set( _noRoomLists, true );
        ClearCollect( AllRooms, 'Office365'.GetRooms().value );
        Set( _allRoomsConcat, Concat( FirstN( AllRooms, 20 ), Address & ";" ) );
        ClearCollect( RoomTimeSuggestions, 
            'Office365'.FindMeetingTimes(
                {
                    RequiredAttendees: _allRoomsConcat, 
                    MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                    Start: _selectedMeetingTime.StartTime & "Z", 
                    End: _selectedMeetingTime.EndTime & "Z", 
                    MinimumAttendeePercentage: "1",
                    IsOrganizerOptional: "false", 
                    ActivityDomain: "Unrestricted"
                }
            ).MeetingTimeSuggestions
        );
        ClearCollect( AvailableRooms, 
            AddColumns(
                AddColumns(
                    Filter( 
                        First( RoomTimeSuggestions ).AttendeeAvailability,
                        Availability="Free"
                    ), 
                    "Address", Attendee.EmailAddress.Address
                ), 
                "Name", LookUp( AllRooms, Address = Attendee.EmailAddress.Address ).Name 
            )
        );
        ClearCollect( AvailableRoomsOptimal, 
            DropColumns(
                DropColumns( AvailableRooms, "Availability" ), 
                "Attendee" 
            )
        ),
        Set( _roomListSelected, false) 
    );
    UpdateContext( {_loadingRooms: false} )
    ```

  На высоком уровне этот блок кода, собирает доступные комнаты для пользователей, у которых нет комнат списки в зависимости от выбранной даты и времени собрания. В противном случае он просто извлекает списки помещений.

  На низком уровне, этот блок кода:
  1. Наборы **_selectedMeetingTime** к выбранному элементу. Это позволяет найти какие комнаты доступны в течение этого времени.
  1. Задает загрузку переменной состояния **_loadingRooms** для **true**, Включение состояния загрузки.
  1. Если **RoomsLists** , возвращается пустая коллекция, он извлекает списки помещений клиента пользователя и сохраняет их в **RoomsLists** коллекции.
  1. Если пользователь не имеет список комнаты или списке помещений один:
      1. **NoRoomLists** переменной присваивается **true**, и эта переменная используется для определения элементов, отображаемых в **RoomBrowseGallery** элемента управления.
      1. `Office365.GetRooms()` Операция используется для получения первых 100 комнаты в своих клиентах. Эти значения хранятся в **AllRooms** коллекции.
      1. **_AllRoomsConcat** переменной присваивается разделенный точками с запятой строка первого 20 электронные адреса помещения в **AllRooms** коллекции. Это обусловлено [Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) ограничена поиск доступное время 20 объектов person, в рамках одной операции.
      1. **RoomTimeSuggestions** использует коллекцию [Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) извлекаемого наличий первые 20 комнаты в **AllRooms** сбора, основываясь на по значениям времени от **_selectedMeetingTime** переменной. Обратите внимание, что `& "Z"` используется правильно отформатировать **DateTime** значение.
      1. **AvailableRooms** создания коллекции. Это просто **RoomTimeSuggestions** коллекцию участников наличий два дополнительных столбца добавляются в него: «Address» и «Name». «Адрес» — это адрес электронной почты комнаты и имя комнаты составляет «Name».
      1. Затем **AvailableRoomsOptimal** создания коллекции. Это просто **AvailableRooms** коллекции со столбцами «Доступность» и «Участник» удален. Это соответствует схем **AvailableRoomsOptimal** и **AllRooms**. Это позволяет использовать обе коллекции в **элементы** свойство **RoomBrowseGallery**.
      1. **_roomListSelected** присваивается **false**.
  1. Состояние загрузки **_loadingRooms**, имеет значение **false** все остальное по завершении выполнения.

## <a name="room-browse-gallery"></a>Обзор коллекции комнаты

   ![Элемент управления RoomBrowseGallery](media/meeting-screen/meeting-rooms-gall.png)

* Свойство: **Элементы**<br>
    Значение: Логически задайте два внутренних коллекциях одинаковые схемы, в зависимости от ли пользователь выбрал список помещений, или имеет списки помещений в своих клиентах:

    ```powerapps-dot
    Search(
        If( _roomListSelected || _noRoomLists, AvailableRoomsOptimal, RoomsLists ),
        Trim(TextMeetingLocation1.Text), 
        "Name", 
        "Address"
    )
    ```

  Эта галерея содержит **AvailableRoomsOptimal** коллекции Если **_roomListSelected** или **_noRoomLists** — **true**. В противном случае он отображает **RoomsLists** коллекции. Это можно сделать, поскольку схема этих коллекций являются идентичными.

* Свойство: **Видимым**<br>
    Значение: ```_showDetails && !IsBlank( _selectedMeetingTime ) && !_loadingRooms```

    Коллекции отображается только в том случае, если предыдущие три инструкции возвращают значение **true**.

### <a name="roombrowsegallery-title"></a>Заголовок RoomBrowseGallery

   ![Элемент управления RoomBrowseGallery заголовок](media/meeting-screen/meeting-rooms-gall-title.png)

* Свойство: **OnSelect**<br>
    Значение: Набор логически связанных **собирать** и **задать** инструкции, которые могут или может не активироваться, в зависимости от того, является ли пользователь просматривает список помещений или комнаты:

    ```powerapps-dot
    UpdateContext( { _loadingRooms: true } );
    If( !_roomListSelected && !noRoomLists,
        Set( _roomListSelected, true );
        Set( _selectedRoomList, ThisItem.Name );
        ClearCollect( AllRooms, 'Office365'.GetRoomsInRoomList( ThisItem.Address ).value );
        Set( _allRoomsConcat, Concat( FirstN( AllRooms, 20 ), Address & ";" ) );
        ClearCollect( RoomTimeSuggestions, 
            'Office365'.FindMeetingTimes(
                {
                    RequiredAttendees: _allRoomsConcat, 
                    MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                        Start: _selectedMeetingTime.StartTime & "Z", 
                    End: _selectedMeetingTime.EndTime & "Z", 
                    MinimumAttendeePercentage: "1",
                    IsOrganizerOptional: "false", 
                    ActivityDomain: "Unrestricted"
                }
            ).MeetingTimeSuggestions
        );
        ClearCollect( AvailableRooms, 
            AddColumns(
                AddColumns(
                    Filter(
                        First( RoomTimeSuggestions ).AttendeeAvailability, 
                        Availability = "Free"
                    ),
                    "Address", Attendee.EmailAddress.Address 
                ), 
                "Name", LookUp( AllRooms, Address = Attendee.EmailAddress.Address ).Name
            )
        );
        ClearCollect( AvailableRoomsOptimal, 
            DropColumns(
                DropColumns( AvailableRooms, "Availability" )
            ), 
            "Attendee" )
        ),
        Set( _selectedRoom, ThisItem )
    );
    UpdateContext( {_loadingRooms: false} )
    ```

  Действий, возникающих при выборе этого элемента управления зависят от того, является ли пользователь просматривает в настоящее время набор списков помещений или набор комнаты. Если это первое из них, выбрав этот элемент управления извлекает аудиторий, которые доступны в выбранное время из списка выбранных комнаты. Если это последний, выбор этого элемента управления задает **_selectedRoom** переменной к выбранному элементу. Предыдущая инструкция — очень похоже на **выберите** инструкции для [ **FindMeetingTimesGallery Title**](#find-meeting-times-gallery).

  На низком уровне, приведенного выше кода:
  1. Включение состояния загрузки для помещений, задав **_loadingRooms** для **true**.
  1. Проверяет, если был выбран список помещений, и в том случае, если у клиента есть комнаты перечислены. Если это так:
      1. Задает **_roomListSelected** для **true** и задает **_selectedRoomList** к выбранному элементу.
      1. **_AllRoomsConcat** переменной присваивается разделенный точками с запятой строка первого 20 электронные адреса помещения в **AllRooms** коллекции. Это обусловлено [Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) ограничивается поиск доступное время 20 объектов person, в рамках одной операции.
      1. **RoomTimeSuggestions** использует коллекцию [Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) операцию по получению наличий первые 20 комнаты в **AllRooms** коллекции, на основе времени значений из **_selectedMeetingTime** переменной. Обратите внимание, что `& "Z"` используется правильно отформатировать **DateTime** значение.
      1. **AvailableRooms** создания коллекции. Это просто **RoomTimeSuggestions** коллекцию участников наличий два дополнительных столбца добавляются в него: «Address» и «Name». «Адрес» — это адрес электронной почты комнаты и имя комнаты составляет «Name».
      1. Затем **AvailableRoomsOptimal** создания коллекции. Это просто **AvailableRooms** коллекции со столбцами «Доступность» и «Участник» удален. Это соответствует схем **AvailableRoomsOptimal** и **AllRooms**. Это позволяет использовать обе коллекции в **элементы** свойство **RoomBrowseGallery**.
      1. **_roomListSelected** присваивается **false**.
  1. Состояние загрузки **_loadingRooms**, имеет значение **false** все остальное по завершении выполнения.

## <a name="back-chevron"></a>Шеврон назад

   ![Элемент управления RoomsBackNav](media/meeting-screen/meeting-back.png)

* Свойство: **Видимым**<br>
    Значение: `_roomListSelected && _showDetails`

    Этот элемент управления виден только в том случае, если был выбран как список помещений и **расписание** выделенной вкладки.

* Свойство: **OnSelect**<br>
    Значение: `Set( _roomListSelected, false )`

    Когда **_roomListSelected** присваивается **false**, он изменяет **RoomBrowseGallery** управления для отображения элементов из **RoomsLists** Коллекция.

## <a name="send-icon"></a>Значок "Отправить"

   ![Элемент управления IconSendItem](media/meeting-screen/meeting-send-icon.png)

* Свойство: **DisplayMode**<br>
    Значение: Логика для принудительного пользователю вводить некоторые сведения о встрече, прежде чем значок становится доступным для редактирования.
    
    ```powerapps-dot
    If( Len( Trim( TextMeetingSubject1.Text ) ) > 0
        && !IsEmpty( MyPeople ) && !IsBlank( _selectedMeetingTime ),
        DisplayMode.Edit, DisplayMode.Disabled
    )
    ```
  Значок, можно выбрать только в том случае, если заполняется теме собрания, имеется по крайней мере один участник собрания и выбрал время собрания. В противном случае он будет отключен.

* Свойство: **OnSelect**<br>

    Значение: Код, чтобы отправить приглашение к участникам выбранных и очистить все поля ввода:

    ```powerapps-dot
    Set( _myCalendarName, LookUp( 'Office365'.CalendarGetTables().value, DisplayName = "Calendar" ).Name );
    Set( _myScheduledMeeting, 
        'Office365'.V2CalendarPostItem( _myCalendarName,
            TextMeetingSubject1.Text, 
            Text(DateAdd(DateTimeValue( _selectedMeetingTime.StartTime), -TimeZoneOffset(), Minutes) ),
            Text(DateAdd(DateTimeValue( _selectedMeetingTime.EndTime), -TimeZoneOffset(), Minutes) ),
            {
                RequiredAttendees: Concat( MyPeople, UserPrincipalName & ";" ) & _selectedRoom.Address, 
                Body: TextMeetingMessage1.Text, 
                Location: _selectedRoom.Name, 
                Importance: "Normal", 
                ShowAs: "Busy", 
                ResponseRequested: true
            }
        )
    );
    Concurrent(
        Reset( TextMeetingLocation1 ),
        Reset( TextMeetingSubject1 ),
        Reset( TextMeetingMessage1 ),
        Clear( MyPeople ),
        Set( _selectedMeetingTime, Blank() ),
        Set( _selectedRoomList, Blank() ),
        Set( _selectedRoom, Blank() ),
        Set( _roomListSelected, false )
    )
    ```
  
  На низком уровне, этот блок кода:
  1. Наборы **_myCalendarName** в календарь [Office365.CalendarGetTables()](https://docs.microsoft.com/connectors/office365/#get-calendars) операцию с **DisplayName** «Календарь».
  1. Расписания собрания со всеми ввода значений из различных вариантов, пользователем время на экран с помощью [Office365.V2CalendarPostItem](https://docs.microsoft.com/connectors/office365/#create-event--v2-) операции.
  1. Сбрасывает все входные поля и переменные, используемые при создании собрания.

> [!NOTE]
> В зависимости от вашего региона нужного календаря отсутствует отображаемое имя «Calendar». Перейдите к Outlook, чтобы увидеть, каково название календаря и внести необходимые изменения в приложении.

## <a name="next-steps"></a>Дальнейшие действия

* [Дополнительные сведения об этом экране](./meeting-screen-overview.md)
* [Дополнительные сведения о соединителе Office 365 Outlook в PowerApps](../connections/connection-office365-outlook.md)
* [Дополнительные сведения о соединителе Office 365 пользователи в PowerApps](../connections/connection-office365-users.md)
