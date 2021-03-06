---
title: Справочник по шаблону "Календарь-экран" для приложений Canvas | Документация Майкрософт
description: Сведения о том, как шаблон экрана календаря для приложений Canvas работает в Power Apps.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/31/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: adcdc2b14bdc393b69f467f123418c87bb5cca9e
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732667"
ms.PowerAppsDecimalTransform: true
---
# <a name="reference-information-about-the-calendar-screen-template-for-canvas-apps"></a>Справочные сведения о шаблоне "Календарь-экран" для приложений Canvas

Для приложений Canvas в Power Apps необходимо понять, как каждый важный элемент управления в шаблоне календаря влияет на общую функциональность по умолчанию на экране. Этот подробный обзор содержит формулы поведения и значения других свойств, определяющих реакцию элементов управления на вводимые пользователем данные. Подробное описание функциональных возможностей этого экрана по умолчанию см. в разделе [Обзор календаря](calendar-screen-overview.md).

В этом разделе описываются некоторые важные элементы управления и объясняются выражения или формулы, в которых задаются различные свойства (например, **элементы** и **OnSelect**) этих элементов управления.

- [Раскрывающийся список календаря (Дропдовнкалендарселектион)](#calendar-drop-down)
- [Значок календаря (Иконкалендар)](#calendar-icon)
- [Шеврон предыдущего месяца (Иконпревмонс)](#previous-month-chevron)
- [Шеврон следующего месяца (Иконнекстмонс)](#next-month-chevron)
- [Коллекция календарей (Монсдайгаллери) (+ дочерние элементы управления)](#calendar-gallery)
- [Коллекция событий (Календаревентсгаллери)](#events-gallery)

## <a name="prerequisite"></a>Необходимое условие

Знакомство с добавлением и настройкой экранов и других элементов управления при [создании приложения в Power Apps](../data-platform-create-app-scratch.md).

## <a name="calendar-drop-down"></a>Раскрывающийся список календаря

![элемент управления Дропдовнкалендарселектион](media/calendar-screen/calendar-dropdown.png)

- Свойство: **элементы**<br>
    Значение: `Office365.CalendarGetTables().value`

    Это операция соединителя, которая получает календари Outlook пользователя приложения. Вы видите [значение](https://docs.microsoft.com/connectors/office365/#entitylistresponse[table]) , получаемое этой операцией.

- Свойство: **onChange**<br>Значение: `Select(dropdownCalendarSelection)`

    Когда пользователь выбирает параметр в списке, выполняется функция в свойстве **OnSelect** элемента управления.

- Свойство: **OnSelect**<br>
    Value: функция **If** , которая отображается в следующем блоке кода, и несколько дополнительных функций, которые появляются в блоке кода после этого.

   Эта часть формулы выполняется только в первый раз, когда пользователь выбирает параметр в раскрывающемся списке после открытия приложения.

    ```powerapps-comma
    If( IsBlank( _userDomain );
        UpdateContext( {_showLoading: true} );;
        Set( _userDomain; Right( User().Email; Len( User().Email ) - Find( "@"; User().Email ) ) );;
        Set( _dateSelected; Today() );;
        Set( _firstDayOfMonth; DateAdd( Today(); 1 - Day( Today() ); Days ) );;  
        Set( _firstDayInView; DateAdd( _firstDayOfMonth; -(Weekday(_firstDayOfMonth) - 1); Days ) );;
        Set( _lastDayOfMonth; DateAdd( DateAdd( _firstDayOfMonth; 1; Months ); -1; Days ) )  
    );;
    ```

    Приведенный выше код определяет следующие переменные:
    
  - **\_доменпользователя**: домен компании пользователя приложения, как отражено в адресе электронной почты пользователя.
  - **\_датеселектед**: сегодняшняя дата (по умолчанию). Эта дата выделена в коллекции календарей, и в галерее событий отображаются события, запланированные на эту дату.
  - **\_фирстдайофмонс**: первый день текущего месяца. Поскольку `(Today + (1 - Today)) = Today - Today + 1 = 1`, функция **DateAdd** всегда возвращает первый день месяца.
  - **\_фирстдайинвиев**: первый день, в котором коллекция Calendar может быть отображена. Это значение не совпадает с первым днем месяца, если только месяц не начинается с воскресенья. Чтобы предотвратить показ целой недели предыдущего месяца, значение **\_фирстдайинвиев** равно `_firstDayOfMonth - Weekday(_firstDayOfMonth) + 1`.
  - **\_ластдайофмонс**: последний день текущего месяца, который совпадает с первым днем следующего месяца, минус один день.

   Функции после функции **If** выполняются каждый раз, когда пользователь выбирает параметр в раскрывающемся списке календаря (а не только при первом открытии приложения пользователем):

    ```powerapps-comma
    Set( _calendarVisible; false );;
    UpdateContext( {_showLoading: true} );;
    Set( _myCalendar; dropdownCalendarSelection2.Selected );;
    Set( _minDate; 
        DateAdd( _firstDayOfMonth; -(Weekday( _firstDayOfMonth ) - 2 + 1); Days )
    );;
    Set(_maxDate; 
        DateAdd(
            DateAdd( _firstDayOfMonth; -(Weekday( _firstDayOfMonth ) - 2 + 1); Days ); 
            40; 
            Days
        )
    );;
    ClearCollect( MyCalendarEvents; 
        'Office365'.GetEventsCalendarViewV2( _myCalendar.Name; 
            Text( _minDate; UTC ); 
            Text( _maxDate; UTC )
        ).value
    );;
    UpdateContext( {_showLoading: false} );;
    Set( _calendarVisible; true )
    ```

    Приведенный выше код определяет эти переменные и одну коллекцию:

    - **\_календарвисибле**: задайте значение **false** , чтобы календарь не отображался при загрузке нового выделения.
    - **\_шовлоадинг**: задайте значение **true** , чтобы индикаторы загрузки отображались во время загрузки нового выделения.
    - **\_микалендар**: задайте текущее значение раскрывающегося элемента управления **Calendar** , чтобы получить события из нужного календаря.
    - **\_minDate**: задайте то же значение, что и для **\_фирстдайинвиев**. Эта переменная определяет, какие события уже были получены из Outlook и кэшированы в приложении.
    - **\_maxDate**: задает последний отображаемый день в календаре. Формула `_firstDayInView + 40`. В календаре отображается не более 41 дней, поэтому **\_переменная maxDate** всегда отражает последний отображаемый день и определяет, какие события уже были получены из Outlook и кэшированы в приложении.
    - **Микалендаревентс**: задайте коллекцию событий пользователя из выбранного календаря в диапазоне от **\_MinDate** до **\_maxDate**.
    - **\_шовлоадинг**: задано **значение false**; **\_календарвисибле** имеет значение **true** после загрузки всех остальных элементов.

## <a name="calendar-icon"></a>Значок календаря

![элемент управления Иконкалендар](media/calendar-screen/calendar-today-icon.png)

- Свойство: **OnSelect**<br>
    Значение: четыре функции **набора** , которые сбрасывают коллекцию календарей до сегодняшней даты:

    ```powerapps-comma
    Set( _dateSelected; Today() );;
    Set( _firstDayOfMonth; DateAdd( Today(); 1 - Day( Today() ); Days) );;
    Set( _firstDayInView; DateAdd(_firstDayOfMonth; -(Weekday( _firstDayOfMonth ) - 2 + 1); Days));;
    Set( _lastDayOfMonth; DateAdd( DateAdd( _firstDayOfMonth; 1; Months ); -1; Days ) )
    ```

    Приведенный выше код сбрасывает все переменные даты, необходимые для отображения правильного представления календаря:

    - **\_датеселектед** сбрасывается до сегодняшнего дня.
    - **\_фирстдайофмонс** сбрасывается до первого дня текущего месяца.
    - **\_фирстдайинвиев** сбрасывается до первого дня, отображаемого при выборе текущего месяца.
    - **\_ластдайофмонс** сбрасывается до последнего дня текущего месяца.

    В [**раскрывающемся списке Календарь**](#calendar-drop-down) этого раздела более подробно описаны эти переменные.

## <a name="previous-month-chevron"></a>Шеврон предыдущего месяца

![элемент управления Иконпревмонс](media/calendar-screen/calendar-back.png)

- Свойство: **OnSelect**<br>Значение: четыре функции **Set** и функция **If** , которая показывает предыдущий месяц в коллекции календарей:

    ```powerapps-comma
    Set( _firstDayOfMonth; DateAdd( _firstDayOfMonth; -1; Months ) );;
    Set( _firstDayInView; 
        DateAdd( _firstDayOfMonth; -(Weekday( _firstDayOfMonth ) - 2 + 1); Days )
    );;
    Set( _lastDayOfMonth; DateAdd(DateAdd( _firstDayOfMonth; 1; Months ); -1; Days ) );;
    If( _minDate > _firstDayOfMonth;
        Collect( MyCalendarEvents;
            'Office365'.GetEventsCalendarViewV2( _myCalendar.Name;
                Text( _firstDayInView; UTC ); 
                Text( DateAdd( _minDate; -1; Days ); UTC )
            ).value
        );;
        Set( _minDate; _firstDayInView )
    )
    ```

    > [!NOTE]
    > Определения для **\_фирстдайофмонс**, **\_Фирстдайинвиев**и **\_ластдайофмонс** практически идентичны тем, которые находятся в раскрывающемся разделе [календаря](#calendar-drop-down) этого раздела.

    Первые три строки предыдущего кода выполняются каждый раз, когда пользователь выбирает Шеврон предыдущего месяца. Этот код задает переменные, необходимые для отображения соответствующего представления календаря. Оставшийся код выполняется, только если пользователь ранее не выбрал этот месяц для выбранного календаря.

    В этом случае **\_minDate** — первый день, который отображается при отображении предыдущего месяца. Прежде чем пользователь выберет значок, **\_minDate** имеет минимальное возможное значение 23-го текущего месяца. (Когда 1 марта попадает в субботу, **\_фирстдайинвиев** за Март — 23 февраля). Это означает, что если пользователь еще не выбрал этот месяц, **\_minDate** больше, чем новый **\_фирстдайофмонс**, а функция **If** возвращает **значение true**. Код выполняется, а коллекция и переменная обновляются:

    - **Микалендаревентс** извлекает события из выбранного календаря с помощью операции [Office 365. GetEventsCalendarViewV2](https://docs.microsoft.com/connectors/office365/#get-calendar-view-of-events--v2-) . Диапазон дат находится в диапазоне от **\_фирстдайинвиев** date до **\_minDate** -1. Так как **микалендаревентс** уже содержит события на дату **\_minDate** , 1 вычитается из этой даты для максимального значения в этом новом диапазоне дат.

    - **\_minDate** задано текущее **\_фирстдайинвиев** , так как это первая Дата получения событий. Если пользователь возвращается к этой дате, выбирая Шеврон прошлого месяца, функция **If** возвращает **значение false**. код не выполняется, так как события для этого представления уже кэшированы в **микалендаревентс**.

## <a name="next-month-chevron"></a>Шеврон следующего месяца

![элемент управления Иконнекстмонс](media/calendar-screen/calendar-forward.png)

- Свойство: **OnSelect**<br>
    Значение: четыре функции **Set** и функция **If** , которая показывает следующий месяц в коллекции календарей:

    ```powerapps-comma
    Set( _firstDayOfMonth; DateAdd( _firstDayOfMonth; 1; Months ) );;
    Set( _firstDayInView; 
        DateAdd( _firstDayOfMonth; -(Weekday( _firstDayOfMonth ) - 2 + 1); Days ) );;
    Set( _lastDayOfMonth; DateAdd( DateAdd( _firstDayOfMonth; 1; Months ); -1; Days ) );;
    If( _maxDate < _lastDayOfMonth;
        Collect( MyCalendarEvents; 
            'Office365'.GetEventsCalendarViewV2( _myCalendar.Name; 
                Text( DateAdd( _maxDate; 1; Days ); UTC ); 
                DateAdd( _firstDayInView; 40; Days )
            ).value
        );;
        Set( _maxDate; DateAdd( _firstDayInView; 40; Days) )    
    )
    ```

    > [!NOTE]
    > Определения для **\_фирстдайофмонс**, **\_Фирстдайинвиев**и **\_ластдайофмонс** практически идентичны тем, которые находятся в раскрывающемся разделе [календаря](#calendar-drop-down) этого раздела.

    Первые три строки предыдущего кода, которые выполняются, когда пользователь выбирает Шеврон следующего месяца, устанавливают переменные, необходимые для отображения соответствующего представления календаря. Оставшийся код выполняется, только если пользователь ранее не выбрал этот месяц для выбранного календаря.

    В этом случае **\_maxDate** — последний день, отображаемый при отображении предыдущего месяца. Прежде чем пользователь выбрал Шеврон следующего месяца, **\_maxDate** имеет максимально возможное значение 13-го числа следующего месяца. (Когда 1 февраля попадает в воскресенье, не являющийся високосным годом, **\_maxDate** — 13 марта, то есть **\_фирстдайинвиев** + 40 дней.) Это означает, что если пользователь еще не выбрал этот месяц, **\_maxDate** больше, чем новый **\_ластдайофмонс**, а функция **If** возвращает **значение true**. Код выполняется, а коллекция и переменная обновляются:

    - **Микалендаревентс** извлекает события из выбранного календаря с помощью операции [Office 365. GetEventsCalendarViewV2](https://docs.microsoft.com/connectors/office365/#get-calendar-view-of-events--v2-) . Диапазон дат находится в диапазоне от **\_maxDate** + 1 день до **\_фирстдайинвиев** + 40 дней. Так как **микалендаревентс** уже содержит события на дату **\_minDate** , 1 добавляется к этой дате для минимального значения в этом новом диапазоне дат. **\_фирстдайинвиев** + 40 — это формула для **\_maxDate**, поэтому вторая дата в диапазоне — это просто новый **\_maxDate**.

    - **\_maxDate** имеет значение **\_фирстдайинвиев** + 40 дней, так как это последний день, для которого были получены события. Если пользователь возвращается к этой дате, выбирая Шеврон в следующем месяце, функция **If** возвращает **значение false**. код не выполняется, так как события для этого представления уже кэшированы в **микалендаревентс**.

## <a name="calendar-gallery"></a>Коллекция календарей

![Элемент управления Монсдайгаллери](media/calendar-screen/calendar-month-gall.png)

- Свойство: **элементы**<br>
    Значение: `[0;1;2;3;4;5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;
    20;21;22;23;24;25;26;27;28;29;30;31;32;33;34;35;36;37;38;39;40;41]`
  
  Для элементов в коллекции календарей используется набор от 0 до 41, поскольку в худшем случае в представлении календаря необходимо отобразить 42 полных дней. Это происходит, когда первый месяц происходит в субботу, а последний — в воскресенье. В этом случае в календаре отображается шесть дней предыдущего месяца в строке, содержащей первый месяц, и шесть дней из следующего месяца в строке, содержащей последний месяц. Это 42 уникальных значения, из которых 30 относятся к выбранному месяцу.

- Свойство: **врапкаунт**<br>
    Значение: `7`

  Это значение отражает семь дней недели.

### <a name="title-control-in-the-calendar-gallery"></a>Элемент управления "заголовок" в коллекции календарей

![Элемент управления "заголовок Монсдайгаллери"](media/calendar-screen/calendar-month-text.png)

- Свойство: **текст**<br>
    Значение: `Day( DateAdd( _firstDayInView; ThisItem.Value; Days ) )`

    Помните, что **\_фирстдайинвиев** определяется как ( **\_фирстдайофмонс** — значение дня недели) + 1. Это говорит о том, что **\_фирстдайинвиев** всегда является воскресеньем, а **\_фирстдайофмонс** всегда находится в первой строке **монсдайгаллери**. Из-за этих двух фактов **\_фирстдайинвиев** всегда находится в первой ячейке **монсдайгаллери**. **Сиситем. Value** — это номер ячейки в свойстве элемента **монсдайгаллери** . Таким образом, **\_фирстдайинвиев** в качестве отправной точки, в каждой ячейке отображается шаг **\_фирстдайинвиев** + + соответствующее значение ячейки.

- Свойство: **Fill**<br>
    Значение: одна функция **If** :

    ```powerapps-comma
    If( DateAdd( _firstDayInView; ThisItem.Value ) = Today() && 
                DateAdd( _firstDayInView; ThisItem.Value ) = _dateSelected; 
            RGBA( 0; 0; 0; 0 );
        DateAdd( _firstDayInView; ThisItem.Value) = Today(); 
            ColorFade( Subcircle.Fill; 0,67 );
        Abs( Title.Text - ThisItem.Value) > 10;
            RGBA( 200; 200; 200; 0,3 );
        RGBA( 0; 0; 0; 0 )
    )
    ```

  Как обсуждалось в описании свойства **Text** , `DateAdd(_firstDayInView; ThisItem.Value)` представляет день в видимой ячейке. Принимая во внимание, приведенный выше код выполняет следующие сравнения:
  1. Если ячейка имеет значение сегодняшней даты, а эта ячейка эквивалентна **\_датеселектед**, не следует указывать значение Fill.
  1. Если значение ячейки является сегодняшней датой, но не эквивалентно **\_датеселектед**, укажите **колорфаде** заливку.
  1. Последнее сравнение не так ясно. Это сравнение фактического текстового значения в ячейке и значения элемента ячейки (число на экране и номер элемента).<br>

      Чтобы лучше понять это, рассмотрим 2018 сентября, месяц, который начинается в субботу и заканчивается воскресеньем. В этом случае календарь отображает 26th до 31 августа и 1 сентября в первой строке и `Abs(Title.Text - ThisItem.Value) = 26` до 1 сентября. Затем `Abs(Title.Text - ThisItem.Value) = 5`. Она будет оставаться в 5 до последней строки в календаре, которая отображает 30 сентября и 1 октября до 6-го. В этом `Abs(Title.Text - ThisItem.Value)` по-прежнему будет иметь значение 5 сентября, но будет 35 для дат октября.<br>

      Это шаблон: для дней, отображаемых за предыдущий месяц, `Abs(Title.Text - ThisItem.Value)` всегда будет равно `Title.Text`ному значению первого дня на экране. Для дней, отображаемых в следующем месяце, `Abs(Title.Text - ThisItem.Value)` всегда будет равно значению элемента **монсдайгаллери** первой ячейки месяца (в данном случае 1 октября) минус 1. И, что самое важное, для дней, отображаемых в текущем выбранном месяце, `Abs(Title.Text - ThisItem.Value)` также всегда равно значению первого элемента в этом месяце минус 1 и никогда не будет превышать 5, как показано в предыдущем примере. Поэтому вполне допустимо писать формулу как `Abs(Title.Text - ThisItem.Value) > 5`.

      Эта инструкция проверяет, находится ли значение даты за пределами текущего выбранного месяца. Если это так, то **Fill** является частично непрозрачным серым цветом.

    > [!NOTE]
    > Чтобы проверить действительность этого последнего сравнения, вставьте элемент управления **Label** в коллекцию и присвоив его свойству **Text** значение this:<br>`Abs(Title.Text - ThisItem.Value)`.

- Свойство: **Visible**<br>
    Значений

    ```powerapps-comma
    !(
        DateAdd( _firstDayInView; ThisItem.Value; Days ) - 
            Weekday( DateAdd( _firstDayInView; ThisItem.Value;Days ) ) + 1 
        > _lastDayOfMonth
    )
    ```

    Предыдущая инструкция проверяет, находится ли ячейка в строке, где нет дней текущего выбранного месяца. Помните, что вычитание значения дня недели из значения даты и сложения 1 всегда возвращает первый элемент в строке, в которой живет день. Поэтому эта инструкция проверяет, находится ли первый день в строке после последнего дня в отображаемом месяце. Если это так, он не будет отображаться, так как вся строка содержит дни следующего месяца.

- Свойство: **OnSelect**<br>
    Value: функция **Set** , которая задает\_переменную **датеселектед** в качестве даты выбранной ячейки:

    ```powerapps-comma
    Set( _dateSelected; DateAdd( _firstDayInView; ThisItem.Value; Days ) )
    ```

### <a name="circle-control-in-the-calendar-gallery"></a>Элемент управления Circle в коллекции календарей

![Элемент управления Circle Монсдайгаллери](media/calendar-screen/calendar-month-event.png)

- Свойство: **Visible**<br>
    Значение: формула, которая определяет, запланированы ли какие-либо события для выбранной даты, и отображаются ли элементы управления " **подокружность** " и " **заголовок** ".

    ```powerapps-comma
    CountRows(
        Filter( MyCalendarEvents; 
            DateValue( Text( Start ) ) = DateAdd( _firstDayInView; ThisItem.Value; Days )
        )
    ) > 0 && !Subcircle.Visible && Title.Visible
    ```

    Элемент управления **Circle** отображается, если поле **Start** для любого события эквивалентно дате этой ячейки, если элемент управления " **заголовок** " является видимым, и если элемент управления " **подокружность** " не является видимым. Иными словами, этот элемент управления отображается, когда в этот день происходит хотя бы одно событие, и этот день не выбран. Если этот параметр выбран, события для этого дня отображаются в элементе управления **календаревентсгаллери** .

### <a name="subcircle-control-in-the-calendar-gallery"></a>Элемент управления "подокружность" в коллекции календарей

![Монсдайгаллери, элемент управления "подокружность"](media/calendar-screen/calendar-month-selected.png)

- Свойство: **Visible**<br>
    Значений

    ```powerapps-comma
    DateAdd( _firstDayInView; ThisItem.Value ) = _dateSelected && Title.Visible
    ```

  Элемент управления " **подокружность** " отображается, когда **\_датеселектед** эквивалентен дате ячейки, а элемент управления " **заголовок** " является видимым. Иными словами, этот элемент управления отображается, когда ячейка является текущей выбранной датой.

## <a name="events-gallery"></a>Коллекция событий

![Элемент управления Календаревентсгаллери](media/calendar-screen/calendar-events-gall.png)

- Свойство: **элементы**<br>
    Значение: формула, которая сортирует и фильтрует коллекцию событий:

    ```powerapps-comma
    SortByColumns(
        Filter( MyCalendarEvents;
            Text( Start; DateTimeFormat.ShortDate ) = Text( _dateSelected; DateTimeFormat.ShortDate )
        );
        "Start"
    )
    ```

   Коллекция **микалендаревентс** содержит все события между **\_MinDate** и **\_maxDate**. Чтобы отобразить события только для выбранной даты, к **микалендаревентс** применяется фильтр, чтобы отобразить события с датой начала, эквивалентной **\ _dateSelected**. Затем элементы сортируются по датам начала, чтобы их можно было последовательно разместить.

## <a name="next-steps"></a>Дальнейшие действия

- [Дополнительные сведения об этом экране](./calendar-screen-overview.md)
- [Дополнительные сведения о соединителе Office 365 Outlook в Power Apps](../connections/connection-office365-outlook.md)
- [Дополнительные сведения о соединителе пользователей Office 365 в Power Apps](../connections/connection-office365-users.md)
