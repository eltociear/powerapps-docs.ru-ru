---
title: Справочник по шаблону экрана собрания для приложений Canvas | Документация Майкрософт
description: Сведения о том, как шаблон экрана собрания для приложений Canvas работает в PowerApps
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/03/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 104225e61e986c4e91563945c4b09f2d83ef1a35
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2019
ms.locfileid: "74675061"
ms.PowerAppsDecimalTransform: true
---
# <a name="reference-information-about-the-meeting-screen-template-for-canvas-apps"></a>Справочные сведения о шаблоне экрана собрания для приложений Canvas

Для приложений Canvas в Power Apps необходимо понимать, как каждый важный элемент управления в шаблоне экрана совещания влияет на общую функциональность экрана по умолчанию. Этот подробный обзор содержит формулы поведения и значения других свойств, определяющих реакцию элементов управления на вводимые пользователем данные. Подробное описание функций этого экрана по умолчанию см. в [обзоре экрана совещания](meeting-screen-overview.md).

В этом разделе описываются некоторые важные элементы управления и объясняются выражения или формулы, в которых задаются различные свойства (например, **элементы** и **OnSelect**) этих элементов управления.

* [Вкладка "пригласить" (Лблинвитетаб)](#invite-tab)
* [Вкладка "Расписание" (Лблсчедулетаб)](#schedule-tab)
* [Поле поиска текста](#text-search-box)
* [Значок "Добавить" (Аддикон)](#add-icon)
* [Галерея обзора пользователей](#people-browse-gallery) (+ дочерние элементы управления)
* [Коллекция людей для собраний](#meeting-people-gallery) (+ дочерние элементы управления)
* [Средство выбора даты собрания (Митингдатеселект)](#meeting-date-picker)
* [Раскрывающийся список длительности собрания (Митингдуратионселект)](#meeting-duration-drop-down)
* [Коллекция "Поиск значений времени собрания](#find-meeting-times-gallery) " (+ дочерние элементы управления)
* [Галерея обзора комнаты](#room-browse-gallery) (+ дочерние элементы управления)
* [Значок "назад" (румсбаккнав)](#back-chevron) (может не отображаться, если у клиента нет списков комнат)
* [Значок отправки](#send-icon)

## <a name="prerequisite"></a>Необходимое условие

Знакомство с добавлением и настройкой экранов и других элементов управления при [создании приложения в PowerApps](../data-platform-create-app-scratch.md).

## <a name="invite-tab"></a>Вкладка "пригласить"

   ![Элемент управления Лблинвитетаб](media/meeting-screen/meeting-invite-text.png)

* Свойство: **Цвет**<br>
    Значение: `If( _showDetails; LblRecipientCount.Color; RectQuickActionBar.Fill )`

    **_showDetails** — это переменная, используемая для определения того, выбран ли элемент управления **лблинвитетаб** или **лблсчедулетаб** . Если значение **_showDetails** равно **true**, выбирается **лблсчедулетаб** ; Если значение равно **false**, то выбирается **лблинвитетаб** . Это означает, что если значение **_showDetails** равно **true** (Эта вкладка *не* выбрана), то цвет табуляции соответствует значению параметра **лблреЦипиенткаунт**. В противном случае он соответствует значению Fill параметра **ректкуиккактионбар**.

* Свойство: **OnSelect**<br> 
    Значение: `Set( _showDetails; false )`

    Присваивает переменной **_showDetails** **значение false**, что означает, что содержимое вкладки приглашение видимо, а содержимое вкладки **Расписание** скрыто.

## <a name="schedule-tab"></a>Вкладка "Расписание"

   ![Элемент управления Лблинвитетаб](media/meeting-screen/meeting-schedule-text.png)

* Свойство: **Цвет**<br>
    Значение: `If( !_showDetails; LblRecipientCount.Color; RectQuickActionBar.Fill )`

    **_showDetails** — это переменная, используемая для определения того, выбран ли элемент управления **лблинвитетаб** или **лблсчедулетаб** . Если это так, **лблсчедулетаб** выбрано; Если значение равно false, **лблинвитетаб** имеет значение. Это означает, что если **_showDetails** имеет значение true ( *Эта вкладка* выбрана), то цвет вкладки соответствует значению заливки **ректкуиккактионбар**. В противном случае он соответствует значению цвета **лблреЦипиенткаунт**.

* Свойство: **OnSelect**<br>
    Значение: `Set( _showDetails; true )`

    Задает для переменной **_showDetails** **значение true**, что означает, что содержимое вкладки расписание отображается, а содержимое вкладки приглашение скрыто.

## <a name="text-search-box"></a>Текстовое поле поиска

   ![Элемент управления Текстсеарчбокс](media/meeting-screen/meeting-search-box.png)

<!--Include description of text search box control?-->

Некоторые другие элементы управления на экране имеют зависимость от этого элемента:

* Если пользователь начинает вводить текст, **пеоплебровсегаллери** станет видимым.
* Если пользователь вводит допустимый адрес электронной почты, **аддикон** станет видимым.
* Когда пользователь выбирает пользователя в **пеоплебровсегаллери** , содержимое поиска сбрасывается.

## <a name="add-icon"></a>Значок добавления

   ![Элемент управления Аддикон](media/email-screen/email-add-icon.png)

Этот элемент управления позволяет пользователям добавлять пользователей, не существующих в Организации, в список участников для собранного собрания.

* Свойство: **Visible**<br>
    Значение: три логические проверки, которые должны иметь значение **true** , чтобы элемент управления был видим:

    ```powerapps-comma
    !IsBlank( TextSearchBox.Text ) &&
        IsMatch( TextSearchBox.Text; Match.Email ) &&
        Not( Trim( TextSearchBox.Text ) in MyPeople.UserPrincipalName )
    ```

  Построчно, этот блок кода говорит, что элемент управления **аддикон** является видимым только в том случае, если:

  * **Текстсеарчбокс** содержит текст.
  * Текст в **текстсеарчбокс** является допустимым адресом электронной почты.
  * Текст в **текстсеарчбокс** еще не существует в коллекции **мипеопле** .

* Свойство: **OnSelect**<br> 
    Value: Инструкция " **собирающий** " для добавления пользователя в список участников, другой — для обновления времени собрания и нескольких переключений переменных:

    ```powerapps-comma
    Collect( MyPeople;
        { 
            DisplayName: TextSearchBox.Text; 
            UserPrincipalName: TextSearchBox.Text; 
            Mail: TextSearchBox.Text
        }
    );;
    Concurrent(
        Reset( TextSearchBox );
        Set( _showMeetingTimes; false );
        UpdateContext( { _loadMeetingTimes: true } );
        Set( _selectedMeetingTime; Blank() );
        Set( _selectedRoom; Blank() );
        Set( _roomListSelected; false );
        ClearCollect( MeetingTimes; 
            AddColumns(
                'Office365'.FindMeetingTimes(
                    { 
                        RequiredAttendees: Concat(MyPeople; UserPrincipalName & ";")
                        MeetingDuration: MeetingDurationSelect.Selected.Minutes;
                        Start: Text( DateAdd( MeetingDateSelect.SelectedDate; 8; Hours ); UTC );
                        End: Text( DateAdd( MeetingDateSelect.SelectedDate; 17; Hours ); UTC );
                        MaxCandidates: 15; 
                        MinimumAttendeePercentage:1; 
                        IsOrganizerOptional: false; 
                        ActivityDomain: "Work"
                    }
                ).MeetingTimeSuggestions;
                "StartTime"; MeetingTimeSlot.Start.DateTime; 
                "EndTime"; MeetingTimeSlot.End.DateTime
            )
        )
    );;
    UpdateContext( { _loadingMeetingTimes: false } );;
    Set( _showMeetingTimes; true )
    ```

  При выборе этого элемента управления добавляется допустимый адрес электронной почты (отображается только при вводе допустимого адреса электронной почты в **текстсеарчбокс**) в коллекцию **мипеопле** (Эта коллекция является списком участников), а затем обновляет доступное время собрания с помощью новой записи пользователя.

  На низком уровне этот блок кода:
  1. Собирает адрес электронной почты в коллекцию **мипеопле** , собирая адрес электронной почты в полях **DisplayName**, **userPrincipalName**и **mail** .
  1. Сбрасывает содержимое элемента управления **текстсеарчбокс** .
  1. Присваивает переменной **_showMeetingTimes** **значение false**. Эта переменная управляет видимостью **финдмитингтимесгаллери**, которая отображает время открытия для выбранных участников.
  1. Задает для переменной контекста **_loadMeetingTimes** **значение true**. Эта переменная задает состояние загрузки, которое переключает видимость элементов управления "состояние загрузки", таких как **_LblTimesEmptyState** , чтобы указать пользователю на то, что их данные загружаются.
  1. Задает для _selectedMeetingTime **пустое значение ()** . **_selectedMeetingTime** — это выбранная запись из элемента управления **финдмитингтимесгаллери** . Он пуст, так как добавление другого участника может означать, что предыдущее определение **_selectedMeetingTime** недоступно для этого участника.
  1. Задает для _selectedRoom **пустое значение ()** . **_selectedRoom** выбрана запись комнаты из **румбровсегаллери**. Доступности комнаты определяется по значению **_selectedMeetingTime**. Если это значение пустое, **_selectedRoom** значение больше не является допустимым, поэтому оно должно быть пустым.
  1. Задает для _roomListSelected **значение false**. Эта строка может быть неприменима для всех. В Office комнаты можно группировать по разным "спискам помещений". Если у вас есть списки помещений, на этом экране учетные записи, позволяющие сначала выбрать список помещений перед выбором комнаты в этом списке. Значение **_roomListSelected** определяет, будет ли пользователь (в клиенте с только списками помещений) просматривать комнаты в списке помещений или наборе списков помещений. Он имеет значение **false** , чтобы заставить пользователей повторно выбрать новый список помещений.
  1. Использует операцию [Office 365. финдмитингтимес](https://docs.microsoft.com/connectors/office365/#find-meeting-times) , чтобы определить и получить доступное время собрания для участников. Эта операция передается:
      * Значение **userPrincipalName** каждого выбранного пользователя в параметре *рекуиредаттендис* .
      * **Митингдуратионселект**. Выбранные минуты в параметре *митингдуратион* .
      * Митингдатеселект. SelectedDate + 8 часов в параметре *Start* . Добавлено восемь часов, так как по умолчанию полные значения даты и времени для элемента управления Calendar выделены в 12:00 AM. Вы, вероятно, захотите получить доступности в нормальных рабочих часах. Обычное время работы — 8:00 AM.
      * **Митингдатеселект**. SelectedDate + 17 часов в параметр *End* . 17 часов добавлены, так как 12:00 AM + 17 = 5:00 PM. Обычное рабочее время — 5:00 PM.
      * *15* в параметр *макскандидатес* . Это означает, что операция возвращает только 15 лучших доступных времени для выбранной даты. Это имеет смысл, так как в 8-часовом рабочем дне осталось только 16 30-минутных фрагментов, а 30-минутное собрание — это минимальное значение, которое может быть задано на этом экране.
      * *1* в параметр *минимуматтендиперцентаже* . По сути, если ни один из участников не доступен, извлекается время собрания.
      * **false** в параметре *исорганизероптионал* . Пользователь приложения не является необязательным участником этого собрания.
      * "Работать" в параметре *активитидомаин* . Это означает, что полученные времена являются только в пределах обычного периода рабочего времени.
  1. Функция **клеарколлект** также добавляет два столбца: "StartTime" и "endtime". Это упрощает возвращаемые данные. 
  Поле, содержащее доступное время начала и окончания, является полем **митингтимеслот** . Это поле представляет собой запись, содержащую начальную и конечную записи, которая сами по себе содержит значения **DateTime** и **TimeZone** соответствующего предложения. Вместо того чтобы пытаться получить вложение записей, Добавление столбцов «StartTime» и «EndTime» в коллекцию **митингтимес** приводит к получению значений **Start > datetime** и **End > DateTime** на поверхность коллекции.
  1. После завершения всех этих функций **_loadingMeetingTimes** переменной присваивается **значение false**, удаляется состояние загрузки, а **_showMeetingTimes** — значение **true**, отображая **финдмитингтимесгаллери**.

## <a name="people-browse-gallery"></a>Галерея просмотра людей

   ![Элемент управления Пеоплебровсегаллери](media/meeting-screen/meeting-browse-gall.png)

* Свойство: **элементы**<br>
    Значений 
    ```powerapps-comma
    If( !IsBlank( Trim( TextSearchBox.Text ) ); 
        'Office365Users'.SearchUser( { searchTerm: Trim(TextSearchBox.Text); top: 15 } )
    )
    ```

Элементы этой коллекции заполняются результатами поиска из операции [Office 365. сеарчусер](https://docs.microsoft.com/connectors/office365users/#searchuser) . Операция принимает текст в `Trim(**TextSearchBox**)` в качестве условия поиска и возвращает 15 лучших результатов, основанных на этом поиске.
  
**Текстсеарчбокс** заключен в функцию **Trim** , так как поиск пользователя в пробелах является недопустимым. Операция `Office365Users.SearchUser` упаковывается в функцию `If(!IsBlank(Trim(TextSearchBox.Text)) ... )`, так как получение результатов поиска перед поиском пользователем не приводит к потере производительности.

### <a name="people-browse-gallery-title"></a>Заголовок коллекции людей

   ![Элемент управления "заголовок Пеоплебровсегаллери"](media/meeting-screen/meeting-browse-gall-title.png)

* Свойство: **текст**<br>
    Значение: `ThisItem.DisplayName`

    Отображает отображаемое имя пользователя из профиля Office 365.

* Свойство: **OnSelect**<br>
    Value: Инструкция " **собирающий** " для добавления пользователя в список участников, другой — для обновления времени собрания и нескольких переключений переменных:

    ```powerapps-comma
    Concurrent(
        Reset( TextSearchBox );
        Set( _selectedUser; ThisItem );
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ); 
            Collect( MyPeople; ThisItem );; 
            Concurrent(
                Set( _showMeetingTimes; false );
                UpdateContext( { _loadMeetingTimes: true } );
                Set( _selectedMeetingTime; Blank() );
                Set( _selectedRoom; Blank() );
                Set( _roomListSelected; false );
                ClearCollect( MeetingTimes; 
                    AddColumns(
                        'Office365'.FindMeetingTimes(
                            {
                                RequiredAttendees: Concat( MyPeople; UserPrincipalName & ";" );
                                MeetingDuration: MeetingDurationSelect.Selected.Minutes;
                                Start: Text( DateAdd( MeetingDateSelect.SelectedDate; 8; Hours ); UTC );
                                End: Text( DateAdd( MeetingDateSelect.SelectedDate; 17; Hours ); UTC );
                                MaxCandidates: 15; 
                                MinimumAttendeePercentage: 1; 
                                IsOrganizerOptional: false; 
                                ActivityDomain: "Work"
                            }
                        ).MeetingTimeSuggestions;
                        "StartTime"; MeetingTimeSlot.Start.DateTime; 
                        "EndTime"; MeetingTimeSlot.End.DateTime
                    )
                )
            );;
            UpdateContext( { _loadingMeetingTimes: false } );;
            Set( _showMeetingTimes; true )
        )
    )
    ```

    На высоком уровне выбор этого элемента управления добавляет пользователя в коллекцию **мипеопле** (хранилище приложения в списке участников) и обновляет доступное время собрания на основе нового добавления пользователя.

    Выбор этого элемента управления очень похож на выбор элемента управления **аддикон** ; Единственное отличие состоит в том, что оператор `Set(_selectedUser; ThisItem)` и порядок выполнения операций. Таким образом, это обсуждение будет не так глубоко. Для получения более подробного объяснения ознакомьтесь с разделом [Управление аддикон](#add-icon) .

    Выбор этого элемента управления приводит к сбросу **текстсеарчбокс**. Затем, если выделенный фрагмент отсутствует в коллекции **мипеопле** , элемент управления:
    1. Задает для **_loadMeetingTimes** состояния **значение true** , а **для _showMeetingTimes** состояние **— значение false**, пустые значения переменных **_selectedMeetingTime** и **_SelectedRoom** и обновление коллекции **митингтимес** с новым дополнением к коллекции **мипеопле** . 
    1. Присваивает **_loadMeetingTimesу** состояние **false**и задает для **_showMeetingTimes** **значение true**. Если выделенный фрагмент уже находится в коллекции **мипеопле** , он сбрасывает только содержимое **текстсеарчбокс**.

## <a name="meeting-people-gallery"></a>Коллекция людей для собраний

   ![Элемент управления Митингпеоплегаллери](media/meeting-screen/meeting-people-gall.png)

* Свойство: **элементы**<br>
    Значение: `MyPeople`

    Коллекция **мипеопле** — это коллекция людей, инициализированных или добавленных в, путем выбора элемента управления **заголовка пеоплебровсегаллери** .

* Свойство: **Высота**<br>
    Значение: логика, обеспечивающая рост коллекции до максимальной высоты 350:

    ```powerapps-comma
    Min( 
        76 * RoundUp( CountRows( MeetingPeopleGallery.AllItems ) / 2; 0 );
        350
    )
    ```

  
   Высота этой коллекции корректируется на число элементов в коллекции до максимальной высоты 350. Формула принимает 76 в качестве высоты одной строки **митингпеоплегаллери**, а затем умножает ее на число строк. Свойство **врапкаунт** имеет значение 2, поэтому число истинных строк равно `RoundUp(CountRows(MeetingPeopleGallery.AllItems) / 2; 0)`.

* Свойство: **шовскроллбар**<br>
    Значение: `MeetingPeopleGallery.Height >= 350`

    При достижении максимальной высоты коллекции (350) полоса прокрутки становится видимой.

### <a name="meeting-people-gallery-title"></a>Заголовок коллекции людей для собраний

   ![Элемент управления "заголовок Митингпеоплегаллери"](media/meeting-screen/meeting-people-gall-title.png)

* Свойство: **OnSelect**<br>
    
    Значение: `Set(_selectedUser; ThisItem)`
    
    Задает **_selectedUser** переменную для элемента, выбранного в **митингпеоплегаллери**.

### <a name="meeting-people-gallery-iconremove"></a>Коллекция людей для собраний Иконремове

   ![Элемент управления Митингпеоплегаллери Иконремове](media/meeting-screen/meeting-people-gall-delete.png)

* Свойство: **OnSelect**<br>
    Значение: Инструкция **Remove** , чтобы удалить пользователя из списка участников, инструкцию " **получить** ", чтобы обновить доступное время собрания, и несколько переключений переменных:

    ```powerapps-comma
    Remove( MyPeople; LookUp( MyPeople; UserPrincipalName = ThisItem.UserPrincipalName ) );;
    Concurrent(
        Reset( TextSearchBox );
        Set( _showMeetingTimes; false );
        UpdateContext( { _loadMeetingTimes: true } );
        Set( _selectedMeetingTime; Blank() );
        Set( _selectedRoom; Blank() );
        Set( _roomListSelected; false );
        ClearCollect( MeetingTimes; 
            AddColumns(
                'Office365'.FindMeetingTimes(
                    {
                        RequiredAttendees: Concat( MyPeople; UserPrincipalName & ";" ); 
                        MeetingDuration: MeetingDurationSelect.Selected.Minutes;
                        Start: Text( DateAdd( MeetingDateSelect.SelectedDate; 8; Hours ); UTC ); 
                        End: Text( DateAdd( MeetingDateSelect.SelectedDate; 17; Hours ); UTC );
                        MaxCandidates: 15; 
                        MinimumAttendeePercentage: 1; 
                        IsOrganizerOptional: false; 
                        ActivityDomain: "Work"
                    }
                ).MeetingTimeSuggestions;
                "StartTime"; MeetingTimeSlot.Start.DateTime; 
                "EndTime"; MeetingTimeSlot.End.DateTime
            )
        )
    );;
    UpdateContext( { _loadingMeetingTimes: false } );;
    Set( _showMeetingTimes; true )
    ```

  На высоком уровне выбор этого элемента управления удаляет пользователя из списка участников и обновляет доступное время собрания на основе удаления этого пользователя.

  После первой строки предыдущего кода выбор этого элемента управления почти аналогичен выбору элемента управления **аддикон** . Таким образом, это обсуждение не будет таким же глубоким. Для получения более подробного объяснения ознакомьтесь с [разделом Управление аддикон](#add-icon).

  В первой строке кода выбранный элемент удаляется из коллекции **мипеопле** . Затем код:
  1. Сбрасывает **текстсеарчбокс**, а затем удаляет выделенный фрагмент из коллекции **мипеопле** . 
  1. Задает для **_loadMeetingTimes** состояния **значение true** , а **для _showMeetingTimes** состояние **— значение false**, пустые значения переменных **_selectedMeetingTime** и **_SelectedRoom** и обновление коллекции **митингтимес** с новым дополнением к коллекции **мипеопле** . 
  1. Присваивает **_loadMeetingTimesу** состояние **false**и задает для **_showMeetingTimes** **значение true**.

## <a name="meeting-date-picker"></a>Средство выбора даты собрания

   ![Элемент управления Митингдатеселект](media/meeting-screen/meeting-datepicker.png)

* Свойство: **DisplayMode**<br>
    Значение: `If( IsEmpty(MyPeople); DisplayMode.Disabled; DisplayMode.Edit )`

    Невозможно выбрать дату собрания, пока в коллекцию **мипеопле** не будет добавлено по крайней мере один участник.

* Свойство: **onChange**<br>
    Значение: `Select( MeetingDateSelect )`

    Изменение выбранной даты активирует выполнение кода в свойстве **OnSelect** этого элемента управления.

* Свойство: **OnSelect**<br>
    Значение: Инструкция **собирающая** для обновления времени собрания и несколько переключений переменных:
  
    ```powerapps-comma
    Concurrent(
        Reset( TextSearchBox );
        Set( _showMeetingTimes; false );
        UpdateContext( { _loadingMeetingTimes: true } );
        Set( _selectedMeetingTime; Blank() );
        Set( _selectedRoom; Blank() );
        Set( _roomListSelected; false );
        ClearCollect( MeetingTimes; 
            AddColumns(
                'Office365'.FindMeetingTimes(
                    {
                        RequiredAttendees: Concat( MyPeople; UserPrincipalName & ";" ); 
                        MeetingDuration: MeetingDurationSelect.Selected.Minutes;
                        Start: Text( DateAdd( MeetingDateSelect.SelectedDate; 8; Hours ); UTC ); 
                        End: Text( DateAdd( MeetingDateSelect.SelectedDate; 17; Hours ); UTC );
                        MaxCandidates: 15; 
                        MinimumAttendeePercentage: 1; 
                        IsOrganizerOptional: false; 
                        ActivityDomain: "Work"
                    }
                ).MeetingTimeSuggestions;
                "StartTime"; MeetingTimeSlot.Start.DateTime; 
                "EndTime"; MeetingTimeSlot.End.DateTime
            )
        )
    );;
    UpdateContext( { _loadingMeetingTimes: false } );;
    Set( _showMeetingTimes; true )
    ```

  На высоком уровне выбор этого элемента управления обновляет доступное время собрания. Это полезно, поскольку если пользователь изменяет дату, доступное время собрания должно быть изменено, чтобы отразить доступности участников в этот день.

  За исключением **первоначальной** инструкции, она идентична функции **OnSelect** элемента управления **аддикон** . Таким образом, это обсуждение не будет таким же глубоким. Для получения более подробного объяснения ознакомьтесь с разделом [Управление аддикон](#add-icon) .

  Выбор этого элемента управления приводит к сбросу **текстсеарчбокс**. Затем: 
  1. Задает для **_loadMeetingTimes** состояния **значение true** , а для **_showMeetingTimes** состояние **— значение false**, пустые значения переменных **_selectedMeetingTime** и **_selectedRoom** и обновление коллекции **митингтимес** с выбором новой даты. 
  1. Присваивает **_loadMeetingTimesу** состояние **false**и задает для **_showMeetingTimes** **значение true**.

## <a name="meeting-duration-drop-down"></a>Раскрывающийся список длительности собрания

   ![Элемент управления Митингдатеселект](media/meeting-screen/meeting-timepicker.png)

* Свойство: **DisplayMode**<br>
    Значение: `If( IsEmpty(MyPeople); DisplayMode.Disabled; DisplayMode.Edit )`

    Длительность собрания не может быть выбрана до тех пор, пока в коллекцию **мипеопле** не будет добавлено по крайней мере один участник.

* Свойство: **onChange**<br>
    Значение: `Select(MeetingDateSelect1)`

    Изменение выбранной длительности активирует код в свойстве **OnSelect** элемента управления **митингдатеселект** для выполнения.

## <a name="find-meeting-times-gallery"></a>Коллекция времени поиска собраний

   ![Элемент управления Финдмитингтимесгаллери](media/meeting-screen/meeting-time-gall.png)

* Свойство: **элементы**<br>
    Значение: `MeetingTimes`

    Коллекция возможных значений времени собрания, полученных из операции [Office 365. финдмитингтимес](https://docs.microsoft.com/connectors/office365/#find-meeting-times) .

* Свойство: **Visible**<br>
    Значение: `_showMeetingTimes && _showDetails && !IsEmpty( MyPeople )`

    Галерея отображается только в том случае, если **_showMeetingTimes** имеет значение **true**, пользователь выбрал элемент управления **лблсчедулетаб** и на собрание добавлен хотя бы один участник.

### <a name="find-meeting-times-gallery-title"></a>Заголовок коллекции значений времени собрания

   ![Элемент управления "заголовок Финдмитингтимесгаллери"](media/meeting-screen/meeting-time-gall-title.png)

* Свойство: **текст**<br>
    Значение: преобразование времени начала, которое должно отображаться в местном времени пользователя:

    ```powerapps-comma
    Text(
        DateAdd(
            DateTimeValue( ThisItem.StartTime );
            - TimeZoneOffset(); 
            Minutes
        );
        DateTimeFormat.ShortTime
    )
    ```

  Полученное значение **StartTime** имеет формат UTC. Для [преобразования из формата UTC в местное время](../functions/function-dateadd-datediff.md#converting-from-utc)применяется функция **DateAdd** .
  [Текстовая функция](../functions/function-text.md#datetime) принимает дату и время в качестве первого аргумента и форматирует ее на основе второго аргумента. Вы передадите ему локальное преобразование времени **сиситем. StartTime**и выводите его как **DateTimeFormat. шорттиме**.

* Свойство: **OnSelect**<br>
    Значение: несколько инструкций **сбора** для сбора данных о конференциях и их предлагаемых доступности, а также несколько переключений переменных:

    ```powerapps-comma
    Set( _selectedMeetingTime; ThisItem );;
    UpdateContext( { _loadingRooms: true } );;
    If( IsEmpty( RoomsLists );
        ClearCollect( RoomsLists; 'Office365'.GetRoomLists().value) );;
    If( CountRows( RoomsLists ) <= 1;
        Set( _noRoomLists; true );;
        ClearCollect( AllRooms; 'Office365'.GetRooms().value );;
        Set( _allRoomsConcat; Concat( FirstN( AllRooms; 20 ); Address & ";" ) );;
        ClearCollect( RoomTimeSuggestions; 
            'Office365'.FindMeetingTimes(
                {
                    RequiredAttendees: _allRoomsConcat; 
                    MeetingDuration: MeetingDurationSelect.Selected.Minutes;
                    Start: _selectedMeetingTime.StartTime & "Z"; 
                    End: _selectedMeetingTime.EndTime & "Z"; 
                    MinimumAttendeePercentage: "1";
                    IsOrganizerOptional: "false"; 
                    ActivityDomain: "Unrestricted"
                }
            ).MeetingTimeSuggestions
        );;
        ClearCollect( AvailableRooms; 
            AddColumns(
                AddColumns(
                    Filter( 
                        First( RoomTimeSuggestions ).AttendeeAvailability;
                        Availability="Free"
                    ); 
                    "Address"; Attendee.EmailAddress.Address
                ); 
                "Name"; LookUp( AllRooms; Address = Attendee.EmailAddress.Address ).Name 
            )
        );;
        ClearCollect( AvailableRoomsOptimal; 
            DropColumns(
                DropColumns( AvailableRooms; "Availability" ); 
                "Attendee" 
            )
        );
        Set( _roomListSelected; false) 
    );;
    UpdateContext( {_loadingRooms: false} )
    ```

  На высоком уровне этот блок кода собирает доступные комнаты для пользователей, не имеющих списков помещений, на основе выбранных даты и времени для собрания. В противном случае он просто извлекает списки помещений.

  На низком уровне этот блок кода:
  1. Задает **_selectedMeetingTime** выбранному элементу. Это позволяет найти, какие комнаты доступны в течение этого времени.
  1. Задает для переменной состояния загрузки **_loadingRooms** **значение true**, переключив состояние загрузки на.
  1. Если коллекция **румслистс** пуста, она извлекает списки тенант'с комнаты пользователя и сохраняет их в коллекции **румслистс** .
  1. Если у пользователя нет списка помещений или одного списка помещений:
      1. Переменная **норумлистс** имеет значение **true**, и эта переменная используется для определения элементов, отображаемых в элементе управления **румбровсегаллери** .
      1. Операция `Office365.GetRooms()` используется для получения первых 100 комнат в своем клиенте. Они хранятся в коллекции **аллрумс** .
      1. Переменной **_allRoomsConcat** присваивается строка с разделителями-точкой с запятой из первых 20 адресов электронной почты комнат в коллекции **аллрумс** . Это обусловлено тем, что [Office 365. финдмитингтимес](https://docs.microsoft.com/connectors/office365/#find-meeting-times) может искать только доступное время для 20 объектов Person за одну операцию.
      1. Коллекция **румтимесугжестионс** использует [Office 365. финдмитингтимес](https://docs.microsoft.com/connectors/office365/#find-meeting-times) для получения доступности первых 20 комнат в коллекции **аллрумс** на основе значений времени из переменной **_selectedMeetingTime** . Обратите внимание, что `& "Z"` используется для правильного форматирования значения **DateTime** .
      1. Создается коллекция **аваилаблерумс** . Это просто коллекция **румтимесугжестионс** доступности, в которую добавлены два дополнительных столбца: "Address" и "Name". "Адрес" — это адрес электронной почты комнаты, а "Name" — имя комнаты.
      1. Затем создается коллекция **аваилаблерумсоптимал** . Это просто коллекция **аваилаблерумс** с удаленными столбцами "доступность" и "участник". Это соответствует схемам **аваилаблерумсоптимал** и **аллрумс**. Это позволяет использовать обе коллекции в свойстве **Items** объекта **румбровсегаллери**.
      1. **_roomListSelected** имеет значение **false**.
  1. Состояние загрузки, **_loadingRooms**, задается равным **false** по завершении выполнения остального.

## <a name="room-browse-gallery"></a>Коллекция просмотра комнаты

   ![Элемент управления Румбровсегаллери](media/meeting-screen/meeting-rooms-gall.png)

* Свойство: **элементы**<br>
    Значение: логически устанавливаются две внутренние коллекции идентичной схемы в зависимости от того, выбрал ли пользователь список помещений или содержит список комнат в своем клиенте:

    ```powerapps-comma
    Search(
        If( _roomListSelected || _noRoomLists; AvailableRoomsOptimal; RoomsLists );
        Trim(TextMeetingLocation1.Text); 
        "Name"; 
        "Address"
    )
    ```

  Эта коллекция отображает коллекцию **аваилаблерумсоптимал** , если **_roomListSelected** или **_noRoomLists** имеет **значение true**. В противном случае отображается коллекция **румслистс** . Это можно сделать, поскольку схема этих коллекций идентична.

* Свойство: **Visible**<br>
    Значение: ```_showDetails && !IsBlank( _selectedMeetingTime ) && !_loadingRooms```

    Коллекция видна только в том случае, если три предшествующих оператора имеют **значение true**.

### <a name="roombrowsegallery-title"></a>Заголовок Румбровсегаллери

   ![Элемент управления "заголовок Румбровсегаллери"](media/meeting-screen/meeting-rooms-gall-title.png)

* Свойство: **OnSelect**<br>
    Значение: набор **логически привязанных** инструкций и инструкции **Set** , которые могут или не запускаться в зависимости от того, просматривают ли пользователь списки помещений или комнаты:

    ```powerapps-comma
    UpdateContext( { _loadingRooms: true } );;
    If( !_roomListSelected && !noRoomLists;
        Set( _roomListSelected; true );;
        Set( _selectedRoomList; ThisItem.Name );;
        ClearCollect( AllRooms; 'Office365'.GetRoomsInRoomList( ThisItem.Address ).value );;
        Set( _allRoomsConcat; Concat( FirstN( AllRooms; 20 ); Address & ";" ) );;
        ClearCollect( RoomTimeSuggestions; 
            'Office365'.FindMeetingTimes(
                {
                    RequiredAttendees: _allRoomsConcat; 
                    MeetingDuration: MeetingDurationSelect.Selected.Minutes;
                        Start: _selectedMeetingTime.StartTime & "Z"; 
                    End: _selectedMeetingTime.EndTime & "Z"; 
                    MinimumAttendeePercentage: "1";
                    IsOrganizerOptional: "false"; 
                    ActivityDomain: "Unrestricted"
                }
            ).MeetingTimeSuggestions
        );;
        ClearCollect( AvailableRooms; 
            AddColumns(
                AddColumns(
                    Filter(
                        First( RoomTimeSuggestions ).AttendeeAvailability; 
                        Availability = "Free"
                    );
                    "Address"; Attendee.EmailAddress.Address 
                ); 
                "Name"; LookUp( AllRooms; Address = Attendee.EmailAddress.Address ).Name
            )
        );;
        ClearCollect( AvailableRoomsOptimal; 
            DropColumns(
                DropColumns( AvailableRooms; "Availability" )
            ); 
            "Attendee" )
        );
        Set( _selectedRoom; ThisItem )
    );;
    UpdateContext( {_loadingRooms: false} )
    ```

  Действия, выполняемые при выборе этого элемента управления, зависят от того, просматривается ли пользователь в настоящий момент набор списков комнаты или набор комнат. Если это первый, то выбор этого элемента управления повлечет за собой доступ к комнатам, доступным в выбранное время из списка выбранных помещений. Если это последний, то при выборе этого элемента управления задается **_selectedRoomая** переменная для выбранного элемента. Предыдущая инструкция очень похожа на инструкцию **SELECT** для [**заголовка финдмитингтимесгаллери**](#find-meeting-times-gallery).

  На низком уровне приведенный выше блок кода:
  1. Включает состояние загрузки для комнат, установив **_loadingRooms** в **значение true**.
  1. Проверяет, выбран ли список помещений и есть ли у клиента списки мест. Если это так:
      1. Задает **_roomListSelected** **значение true** и задает **_selectedRoomList** выбранному элементу.
      1. Переменной **_allRoomsConcat** присваивается строка с разделителями-точкой с запятой из первых 20 адресов электронной почты комнат в коллекции **аллрумс** . Это обусловлено тем, что операция [Office 365. финдмитингтимес](https://docs.microsoft.com/connectors/office365/#find-meeting-times) ограничена поиском доступного времени в 20 объектов Person за одну операцию.
      1. Коллекция **румтимесугжестионс** использует операцию [Office 365. финдмитингтимес](https://docs.microsoft.com/connectors/office365/#find-meeting-times) для получения доступности первых 20 комнат в коллекции **аллрумс** на основе значений времени из переменной **_selectedMeetingTime** . Обратите внимание, что `& "Z"` используется для правильного форматирования значения **DateTime** .
      1. Создается коллекция **аваилаблерумс** . Это просто коллекция **румтимесугжестионс** доступности, в которую добавлены два дополнительных столбца: "Address" и "Name". "Адрес" — это адрес электронной почты комнаты, а "Name" — имя комнаты.
      1. Затем создается коллекция **аваилаблерумсоптимал** . Это просто коллекция **аваилаблерумс** с удаленными столбцами "доступность" и "участник". Это соответствует схемам **аваилаблерумсоптимал** и **аллрумс**. Это позволяет использовать обе коллекции в свойстве **Items** объекта **румбровсегаллери**.
      1. **_roomListSelected** имеет значение **false**.
  1. Состояние загрузки, **_loadingRooms**, задается равным **false** по завершении выполнения остального.

## <a name="back-chevron"></a>Значок "назад"

   ![Элемент управления Румсбаккнав](media/meeting-screen/meeting-back.png)

* Свойство: **Visible**<br>
    Значение: `_roomListSelected && _showDetails`

    Этот элемент управления отображается только в том случае, если выбраны оба списка помещений и выбрана вкладка **Расписание** .

* Свойство: **OnSelect**<br>
    Значение: `Set( _roomListSelected; false )`

    Если **_roomListSelected** имеет значение **false**, он изменяет элемент управления **румбровсегаллери** для вывода элементов из коллекции **румслистс** .

## <a name="send-icon"></a>Значок отправки

   ![Элемент управления Иконсендитем](media/meeting-screen/meeting-send-icon.png)

* Свойство: **DisplayMode**<br>
    Значение: логика для принудительного ввода пользователем определенных сведений о собрании, прежде чем значок станет доступным для редактирования.
    
    ```powerapps-comma
    If( Len( Trim( TextMeetingSubject1.Text ) ) > 0
        && !IsEmpty( MyPeople ) && !IsBlank( _selectedMeetingTime );
        DisplayMode.Edit; DisplayMode.Disabled
    )
    ```
  Этот значок доступен для выбора только в том случае, если тема собрания заполнена, имеется хотя бы один участник собрания и выбрано время собрания. В противном случае он будет отключен.

* Свойство: **OnSelect**<br>

    Значение: код для отправки приглашения на собрание выбранным участникам и очистки всех полей ввода:

    ```powerapps-comma
    Set( _myCalendarName; LookUp( 'Office365'.CalendarGetTables().value; DisplayName = "Calendar" ).Name );;
    Set( _myScheduledMeeting; 
        'Office365'.V2CalendarPostItem( _myCalendarName;
            TextMeetingSubject1.Text; 
            Text(DateAdd(DateTimeValue( _selectedMeetingTime.StartTime); -TimeZoneOffset(); Minutes) );
            Text(DateAdd(DateTimeValue( _selectedMeetingTime.EndTime); -TimeZoneOffset(); Minutes) );
            {
                RequiredAttendees: Concat( MyPeople; UserPrincipalName & ";" ) & _selectedRoom.Address; 
                Body: TextMeetingMessage1.Text; 
                Location: _selectedRoom.Name; 
                Importance: "Normal"; 
                ShowAs: "Busy"; 
                ResponseRequested: true
            }
        )
    );;
    Concurrent(
        Reset( TextMeetingLocation1 );
        Reset( TextMeetingSubject1 );
        Reset( TextMeetingMessage1 );
        Clear( MyPeople );
        Set( _selectedMeetingTime; Blank() );
        Set( _selectedRoomList; Blank() );
        Set( _selectedRoom; Blank() );
        Set( _roomListSelected; false )
    )
    ```
  
  На низком уровне этот блок кода:
  1. Задает **_myCalendarName** для календаря в операции [Office 365. календаржеттаблес ()](https://docs.microsoft.com/connectors/office365/#get-calendars) с **отображаемым именем** "Calendar".
  1. Планирует встречу со всеми входными значениями из различных выборов, сделанных пользователем на экране с помощью операции [Office 365. V2CalendarPostItem](https://docs.microsoft.com/connectors/office365/#create-event--v2-) .
  1. Сбрасывает все поля ввода и переменные, используемые при создании собрания.

> [!NOTE]
> В зависимости от региона у вас может не быть отображаемого имени календаря. Перейдите в Outlook, чтобы узнать, что такое заголовок календаря, и внесите соответствующие изменения в приложение.

## <a name="next-steps"></a>Дальнейшие действия

* [Дополнительные сведения об этом экране](./meeting-screen-overview.md)
* [Дополнительные сведения о соединителе Office 365 Outlook в PowerApps](../connections/connection-office365-outlook.md)
* [Дополнительные сведения о соединителе пользователей Office 365 в PowerApps](../connections/connection-office365-users.md)
