---
title: Справочник по шаблон экрана календаря для приложений на основе холста | Документация Майкрософт
description: Понимание деталей того, как работает шаблон экрана календаря для приложений на основе холста в PowerApps.
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
ms.openlocfilehash: e3d5f40a604d2cbfa074ed5973d599c40a6c5c05
ms.sourcegitcommit: 647e183c070c2159b790c7813a7be1d60b2551bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2019
ms.locfileid: "58765590"
---
# <a name="reference-information-about-the-calendar-screen-template-for-canvas-apps"></a>Справочные сведения о шаблоне экран календарь для приложений на основе холста

Для приложений на основе холста в PowerApps Узнайте, как каждого значительные элемента управления в шаблоне экран календарь помогает реализовать экран общую функциональность по умолчанию. Этот видеокурс представляется формулах поведения и значения других свойств, которые определяют, каким образом элементы управления реагирует на действия пользователя. Обзорное обсуждение функциональные возможности по умолчанию на этом экране, см. в разделе [Обзор экрана календаря](calendar-screen-overview.md).

В этом разделе представлены некоторые существенные элементы управления и описываются выражения или формулы для различных свойства (такие как **элементы** и **OnSelect**) из этих элементов управления заданы:

- [Раскрывающийся календарь (dropdownCalendarSelection)](#calendar-drop-down)
- [Значок календаря (iconCalendar)](#calendar-icon)
- [Предыдущий месяц шеврон (iconPrevMonth)](#previous-month-chevron)
- [Next-month chevron (iconNextMonth)](#next-month-chevron)
- [Коллекции календаря (MonthDayGallery) (+ дочерние элементы управления)](#calendar-gallery)
- [Коллекция событий (CalendarEventsGallery)](#events-gallery)

## <a name="prerequisite"></a>Необходимое условие

Знакомство с тем, как добавить и настроить экраны и другие элементы управления, как вы [Создание приложения в PowerApps](../data-platform-create-app-scratch.md).

## <a name="calendar-drop-down"></a>Выберите в раскрывающемся календаре

![элемент управления dropdownCalendarSelection](media/calendar-screen/calendar-dropdown.png)

- Свойство: **Элементы**<br>
    Значение: `Office365.CalendarGetTables().value`

    Это значение является операцией соединитель, который извлекает календари Outlook пользователя приложения. Вы увидите [значение](https://docs.microsoft.com/connectors/office365/#entitylistresponse[table]) , эта операция получает.

- Свойство: **OnChange**<br>Значение: `Select(dropdownCalendarSelection)`

    Когда пользователь выбирает параметр в списке, функцию элемента управления **OnSelect** свойство запусков.

- Свойство: **OnSelect**<br>
    Значение: **Если** функцию, которая отображается в следующем блоке кода и несколько дополнительных функций, которые отображаются в блоке кода, после которых.

   Эта часть выполняется формула только в первый раз, что пользователь выбирает параметр в раскрывающемся списке после открытия приложения:

    ```powerapps-dot
    If( IsBlank( _userDomain ),
        UpdateContext( {_showLoading: true} );
        Set( _userDomain, Right( User().Email, Len( User().Email ) - Find( "@", User().Email ) ) );
        Set( _dateSelected, Today() );
        Set( _firstDayOfMonth, DateAdd( Today(), 1 - Day( Today() ), Days ) );  
        Set( _firstDayInView, DateAdd( _firstDayOfMonth, -(Weekday(_firstDayOfMonth) - 1), Days ) );
        Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) )  
    );
    ```

    Предыдущий код определяет следующие переменные:
    
  - **\_userDomain**: Домен компании пользователя приложения, как показано в адресе электронной почты пользователя.
  - **\_dateSelected**: Сегодняшняя дата (по умолчанию). Календарь коллекции представлены этой даты, и в коллекции событий отображаются события, которые запланированы для данной даты.
  - **\_firstDayOfMonth**: Первый день текущего месяца. Так как `(Today + (1 - Today)) = Today - Today + 1 = 1`, этот **DateAdd** функция всегда возвращает первый день месяца.
  - **\_firstDayInView**: Первый день, можно показать коллекции календаря. Это значение отличается от первого дня месяца, если месяц начинается в воскресенье. Чтобы предотвратить отображение целую неделю прошлого месяца, а значение  **\_firstDayInView** является `_firstDayOfMonth - Weekday(_firstDayOfMonth) + 1`.
  - **\_lastDayOfMonth**: Последний день текущего месяца, который является таким же, как первый день следующего месяца, минус один день.

   Функции после **Если** функция выполняться каждый раз, когда пользователь выбирает параметр в списке раскрывающегося календаря (не только в первый раз пользователь открывает приложение):

    ```powerapps-dot
    Set( _calendarVisible, false );
    UpdateContext( {_showLoading: true} );
    Set( _myCalendar, dropdownCalendarSelection2.Selected );
    Set( _minDate, 
        DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days )
    );
    Set(_maxDate, 
        DateAdd(
            DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days ), 
            40, 
            Days
        )
    );
    ClearCollect( MyCalendarEvents, 
        'Office365'.GetEventsCalendarViewV2( _myCalendar.Name, 
            Text( _minDate, UTC ), 
            Text( _maxDate, UTC )
        ).value
    );
    UpdateContext( {_showLoading: false} );
    Set( _calendarVisible, true )
    ```

    Предыдущий код определяет эти переменные и одна коллекция:

    - **\_calendarVisible**: Значение **false** , чтобы календарь не отображалось при загрузке нового выделения.
    - **\_showLoading**: Значение **true** так, чтобы отображались индикаторы загрузка нового выделения во время загрузки.
    - **\_myCalendar**: Присваивается текущее значение **раскрывающийся календарь** управления, чтобы события в календаре правильный получаются.
    - **\_minDate**: Значение совпадает со значением  **\_firstDayInView**. Эта переменная определяет, какие события будут уже получены из Outlook и кэшируются в приложении.
    - **\_maxDate**: Значение можно просмотреть последний день в календаре. Формула `_firstDayInView + 40`. В календаре отображается более 41 день, поэтому  **\_maxDate** переменной всегда отражает последний день можно просмотреть и определяет, какие события будут уже получены из Outlook и кэшируются в приложении.
    - **MyCalendarEvents**: Значение коллекцию событий пользователя в выбранном календаре, в диапазоне от  **\_minDate** для  **\_maxDate**.
    - **\_showLoading**: Значение **false**;  **\_calendarVisible** присваивается **true** после загрузки все остальное.

## <a name="calendar-icon"></a>Значок календаря

![элемент управления iconCalendar](media/calendar-screen/calendar-today-icon.png)

- Свойство: **OnSelect**<br>
    Значение: Четыре **задать** функций, которые сбрасываются коллекции календаря на сегодняшнюю дату:

    ```powerapps-dot
    Set( _dateSelected, Today() );
    Set( _firstDayOfMonth, DateAdd( Today(), 1 - Day( Today() ), Days) );
    Set( _firstDayInView, DateAdd(_firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days));
    Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) )
    ```

    Приведенный выше код сбрасывает все переменные даты, которые необходимы для отображения представления правильное календаря:

    - **\_dateSelected** сбрасывается на сегодня.
    - **\_firstDayOfMonth** сбрасывается в первый день текущего месяца.
    - **\_firstDayInView** сбрасывается в первый день можно просмотреть, если выбран текущий месяц.
    - **\_lastDayOfMonth** сбрасывается в последний день текущего месяца.

    [ **Раскрывающийся календарь** ](#calendar-drop-down) этого раздела объясняется эти переменные более подробно.

## <a name="previous-month-chevron"></a>Шеврон предыдущий месяц

![элемент управления iconPrevMonth](media/calendar-screen/calendar-back.png)

- Свойство: **OnSelect**<br>Значение: Четыре **задать** функции и **Если** функция, которая Показать прошлого месяца в календаре коллекции:

    ```powerapps-dot
    Set( _firstDayOfMonth, DateAdd( _firstDayOfMonth, -1, Months ) );
    Set( _firstDayInView, 
        DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days )
    );
    Set( _lastDayOfMonth, DateAdd(DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) );
    If( _minDate > _firstDayOfMonth,
        Collect( MyCalendarEvents,
            'Office365'.GetEventsCalendarViewV2( _myCalendar.Name,
                Text( _firstDayInView, UTC ), 
                Text( DateAdd( _minDate, -1, Days ), UTC )
            ).value
        );
        Set( _minDate, _firstDayInView )
    )
    ```

    > [!NOTE]
    > Определения для  **\_firstDayOfMonth**,  **\_firstDayInView**, и  **\_lastDayOfMonth** практически идентичны тем, в [раскрывающийся календарь](#calendar-drop-down) этого раздела.

    Первые три строки приведенного выше кода запуска всякий раз, когда пользователь выбирает значок шеврона предыдущего месяца. Код задает переменные, которые необходимы для отображения представления правильное календаря. Оставшийся код выполняется только в том случае, если пользователь не выбрал ранее в этом месяце для выбранного календаря.

    Если это так,  **\_minDate** будет первый день, отображаемый при отображении предыдущего месяца. Прежде чем пользователь щелкнет значок  **\_minDate** имеет минимальное возможное значение 23-й текущего месяца. (После 1 марта приходится на субботу,  **\_firstDayInView** для марта — 23 февраля.) Это означает, что если пользователь еще не выбран, в этом месяце  **\_minDate** больше, чем новый  **\_firstDayOfMonth**и **Если** Возвращает **true**. Обновляются запуском кода и коллекцию и переменную:

    - **MyCalendarEvents** получает события из выбранного календаря с [Office365.GetEventsCalendarViewV2](https://docs.microsoft.com/connectors/office365/#get-calendar-view-of-events--v2-) операции. Диапазон дат — от  **\_firstDayInView** даты и  **\_minDate** - 1. Так как **MyCalendarEvents** уже содержит события на  **\_minDate** даты, 1 вычитается из этой даты для максимального значения в этот новый диапазон дат.

    - **\_minDate** установлено равным текущему  **\_firstDayInView** так, как это первая дата, для которого были извлечены события. Если пользователь возвращается к этой даты, выбрав значок шеврона прошлого месяца, **Если** возвращает **false**; код не запускается, так как события для этого представления, уже кэшируются в  **MyCalendarEvents**.

## <a name="next-month-chevron"></a>Шеврон следующего месяца

![элемент управления iconNextMonth](media/calendar-screen/calendar-forward.png)

- Свойство: **OnSelect**<br>
    Значение: Четыре **задать** функции и **Если** функция, отображаемых в галерее календаря следующего месяца:

    ```powerapps-dot
    Set( _firstDayOfMonth, DateAdd( _firstDayOfMonth, 1, Months ) );
    Set( _firstDayInView, 
        DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days ) );
    Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) );
    If( _maxDate < _lastDayOfMonth,
        Collect( MyCalendarEvents, 
            'Office365'.GetEventsCalendarViewV2( _myCalendar.Name, 
                Text( DateAdd( _maxDate, 1, Days ), UTC ), 
                DateAdd( _firstDayInView, 40, Days )
            ).value
        );
        Set( _maxDate, DateAdd( _firstDayInView, 40, Days) )    
    )
    ```

    > [!NOTE]
    > Определения для  **\_firstDayOfMonth**,  **\_firstDayInView**, и  **\_lastDayOfMonth** практически идентичны тем, в [раскрывающийся календарь](#calendar-drop-down) этого раздела.

    Первые три строки приведенного выше кода, которые выполняются, когда пользователь выбирает значок шеврона следующего месяца, задайте переменные, которые необходимы для отображения представления правильное календаря. Оставшийся код выполняется только в том случае, если пользователь не выбрал ранее в этом месяце для выбранного календаря.

    В этом случае  **\_maxDate** последний день, отображаемый при отображении предыдущего месяца. Прежде чем пользователь выбирает значок шеврона следующего месяца,  **\_maxDate** имеет максимально возможное значение 13-й день следующего месяца. (Когда 1 февраля попадает на - високосном году воскресенье,  **\_maxDate** — 13 марта, который является  **\_firstDayInView** + 40 дней.) Это означает, что если пользователь еще не выбран, в этом месяце  **\_maxDate** больше, чем новый  **\_lastDayOfMonth**и **Если** функция Возвращает **true**. Обновляются запуском кода и коллекцию и переменную:

    - **MyCalendarEvents** получает события из выбранного календаря с [Office365.GetEventsCalendarViewV2](https://docs.microsoft.com/connectors/office365/#get-calendar-view-of-events--v2-) операции. Диапазон дат — от  **\_maxDate** + 1 day и  **\_firstDayInView** + 40 дней. Так как **MyCalendarEvents** уже содержит события на  **\_minDate** дату, к этой даты для минимального значения в этом диапазоне новую дату добавляется 1. **\_firstDayInView** + 40 — это формула для  **\_maxDate**, поэтому второй даты в диапазоне является только новые  **\_maxDate**.

    - **\_maxDate** присваивается  **\_firstDayInView** + 40 дней так, как это будет последний день для события, для которых были извлечены. Если пользователь возвращается к этой даты, выбрав значок шеврона следующего месяца, **Если** возвращает **false**; код не запускается, так как события для этого представления, уже кэшируются в  **MyCalendarEvents**.

## <a name="calendar-gallery"></a>Коллекции календаря

![Элемент управления MonthDayGallery](media/calendar-screen/calendar-month-gall.png)

- Свойство: **Элементы**<br>
    Значение: `[0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,
    20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41]`
  
  Набор от 0 до 41 используется для элементов в коллекции календаря, поскольку в худшем случае, будет иметь представления календаря для отображения 42 полных дней. Это происходит, когда возникает первого дня месяца на субботу, а последний месяц на воскресенье. В этом случае календарь показывает шесть дней из прошлого месяца в строки, содержащей первое число месяца и шесть дней из следующего месяца, в строку с последнего месяца. Это 42 уникальные значения, из которых являются 30 для выбранного месяца.

- Свойство: **WrapCount**<br>
    Значение: `7`

  Это значение отражает семь дней недели.

### <a name="title-control-in-the-calendar-gallery"></a>Заголовок элемента управления в коллекции календаря

![Элемент управления MonthDayGallery заголовок](media/calendar-screen/calendar-month-text.png)

- Свойство: **Текст**<br>
    Значение: `Day( DateAdd( _firstDayInView, ThisItem.Value, Days ) )`

    Помните, что  **\_firstDayInView** определяется как (**\_firstDayOfMonth** -его значение дня недели) + 1. Это означает, что  **\_firstDayInView** всегда воскресенье и  **\_firstDayOfMonth** всегда находится в первой строке **MonthDayGallery**. Из-за эти обстоятельства  **\_firstDayInView** всегда находится в очень первой ячейке **MonthDayGallery**. **ThisItem.Value** — номер для этой ячейки в **MonthDayGallery** свойство элемента. Таким образом, используя  **\_firstDayInView** качестве отправной точки, каждая ячейка отображает шаг  **\_firstDayInView** + его значение соответствующие ячейки.

- Свойство: **Заливка**<br>
    Значение: Один **Если** функции:

    ```powerapps-dot
    If( DateAdd( _firstDayInView, ThisItem.Value ) = Today() && 
                DateAdd( _firstDayInView, ThisItem.Value ) = _dateSelected, 
            RGBA( 0, 0, 0, 0 ),
        DateAdd( _firstDayInView, ThisItem.Value) = Today(), 
            ColorFade( Subcircle.Fill, 0.67 ),
        Abs( Title.Text - ThisItem.Value) > 10,
            RGBA( 200, 200, 200, 0.3 ),
        RGBA( 0, 0, 0, 0 )
    )
    ```

  Как уже говорилось в описании **текст** свойство, `DateAdd(_firstDayInView, ThisItem.Value)` представляет день в ячейке отображается. Учитывая это, приведенный выше код выполняет эти сравнения:
  1. Если значение ячейки является сегодняшнюю дату, и данная ячейка эквивалентно  **\_dateSelected**, не предоставляют значение заполнения.
  1. Если значение ячейки является текущей даты, но не эквивалентно  **\_dateSelected**, предоставляют **ColorFade** заливки.
  1. Последнего сравнения не является открытым. Это сравнение значение фактического текста в ячейке и значение элемента ячейки (номер на дисплее) и номер элемента.<br>

      Чтобы лучше понять это, попробуйте сентября 2018 г., месяц, который начинается на субботу и заканчивается в воскресенье. В этом случае отображаются 26-й до 31 августа и 1 сентября в первой строке и `Abs(Title.Text - ThisItem.Value) = 26` до 1 сентября. Затем `Abs(Title.Text - ThisItem.Value) = 5`. Он будет оставаться на 5 до последней строки в календаре, который отображает 30 сентября и 1 октября через 6-й. В том, что `Abs(Title.Text - ThisItem.Value)` по-прежнему будет 5 для 30 сентября, но будет 35 дней октября.<br>

      Это шаблон: Для отображения из прошлого месяца, дней `Abs(Title.Text - ThisItem.Value)` будет всегда равно `Title.Text` значение первого дня на экране. Для дней, отображаемых в течение месяца `Abs(Title.Text - ThisItem.Value)` будет всегда равно **MonthDayGallery** значение первой ячейки этого месяца (в данном случае 1 октября) минус 1 элемента. И, самое главное для дней, отображаемых в выбранном месяце `Abs(Title.Text - ThisItem.Value)` также всегда будет равно значению первого элемента этого месяца минус 1 и не больше 5, как показано в предыдущем примере. Поэтому вполне формулу как `Abs(Title.Text - ThisItem.Value) > 5`.

      Эта инструкция проверяет, является ли значение даты за пределами текущего выбранного месяца. Если это так, **заполнения** частично прозрачных серый.

    > [!NOTE]
    > Можно проверить действительность этого последнего сравнения самостоятельно, вставив **метка** элемента управления в коллекции и задав его **текст** следующее значение:<br>`Abs(Title.Text - ThisItem.Value)`.

- Свойство: **Видимым**<br>
    Значение:

    ```powerapps-dot
    !(
        DateAdd( _firstDayInView, ThisItem.Value, Days ) - 
            Weekday( DateAdd( _firstDayInView, ThisItem.Value,Days ) ) + 1 
        > _lastDayOfMonth
    )
    ```

    Предыдущая инструкция проверяет, находится ли ячейка в строке, где происходит не дни месяца, выбранного. Вспомним, что вычитания значения дня недели любой день, от его значения даты и прибавляет 1 всегда возвращает первый элемент в строке этот день живет в. Поэтому эта инструкция проверяет, является ли первый день в строке после последнего дня месяца, можно просмотреть. Если это так, он не будет отображаться, так как вся строка содержит дней следующего месяца.

- Свойство: **OnSelect**<br>
    Значение: Объект **задать** функция, устанавливающая  **\_dateSelected** переменной к дате выбранной ячейки:

    ```powerapps-dot
    Set( _dateSelected, DateAdd( _firstDayInView, ThisItem.Value, Days ) )
    ```

### <a name="circle-control-in-the-calendar-gallery"></a>Элемент управления Circle в галерее календаря

![Элемент управления MonthDayGallery Circle](media/calendar-screen/calendar-month-event.png)

- Свойство: **Видимым**<br>
    Значение: Формула, определяет ли запланированные события для выбранной даты и **Subcircle** и **Title** отображаются элементы управления:

    ```powerapps-dot
    CountRows(
        Filter( MyCalendarEvents, 
            DateValue( Text( Start ) ) = DateAdd( _firstDayInView, ThisItem.Value, Days )
        )
    ) > 0 && !Subcircle.Visible && Title.Visible
    ```

    **Круг** элемент управления является видимым при **запустить** поле для любого события, эквивалентный значению даты ячейки, если **Title** элемент управления является видимым и если  **Subcircle** не отображается. Другими словами этот элемент управления является видимым, когда по крайней мере одно событие происходит в этот день, и этот день не выбрана. Если он выбран, события за этот день отображаются в **CalendarEventsGallery** элемента управления.

### <a name="subcircle-control-in-the-calendar-gallery"></a>Элемент управления subcircle в галерее календаря

![Элемент управления MonthDayGallery Subcircle](media/calendar-screen/calendar-month-selected.png)

- Свойство: **Видимым**<br>
    Значение:

    ```powerapps-dot
    DateAdd( _firstDayInView, ThisItem.Value ) = _dateSelected && Title.Visible
    ```

  **Subcircle** элемент управления является видимым, когда  **\_dateSelected** эквивалентен Дата ячейки и **Title** элемент управления является видимым. Другими словами появляется этот элемент управления, если ячейка находится в текущей выбранной даты.

## <a name="events-gallery"></a>Коллекция событий

![Элемент управления CalendarEventsGallery](media/calendar-screen/calendar-events-gall.png)

- Свойство: **Элементы**<br>
    Значение: Формула, сортировки и фильтрации событий коллекции.

    ```powerapps-dot
    SortByColumns(
        Filter( MyCalendarEvents,
            Text( Start, DateTimeFormat.ShortDate ) = Text( _dateSelected, DateTimeFormat.ShortDate )
        ),
        "Start"
    )
    ```

   **MyCalendarEvents** коллекция содержит все события между  **\_minDate** и  **\_maxDate**. Чтобы отобразить события для только выбранная дата, фильтр применяется на **MyCalendarEvents** для отображения событий, эквивалентное дате начала **\ _dateSelected**. Затем элементы сортируются по датам начала, они должны быть размещены в последовательном порядке.

## <a name="next-steps"></a>Дальнейшие действия

- [Дополнительные сведения об этом экране](./calendar-screen-overview.md)
- [Дополнительные сведения о соединителе Office 365 Outlook в PowerApps](../connections/connection-office365-outlook.md)
- [Дополнительные сведения о соединителе Office 365 пользователи в PowerApps](../connections/connection-office365-users.md)
