---
title: Функции, сигналы и перечисления | Документация Майкрософт
description: Справочные сведения о функциях, сигналах и перечислениях в PowerApps.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 08/15/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e0f40e6c04b776d2e8efb41353e0da8ced6fc7c5
ms.sourcegitcommit: 07a0fcda31557ddbafba0ca0362765229ee2fdad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/23/2019
ms.locfileid: "70008973"
---
# <a name="formula-reference-for-powerapps"></a>Справочник формул для PowerApps
Формулы объединяют множество элементов.  Ниже перечислены следующие элементы:

* **Функции** принимают параметры, выполняют операцию и возвращают значение. Например, **Sqrt(25)** возвращает значение **5**. Функции построены по принципу функций Microsoft Excel.  Некоторые функции вызывают побочные действия, такие как **SubmitForm**, что должно происходить только в [формуле поведения](working-with-formulas-in-depth.md), такой как **Button.OnSelect**.
* **Сигналы** возвращают сведения о среде. Например, **[Location](functions/signals.md)** возвращает текущие GPS-координаты устройства. Сигналы не принимают параметры и не вызывают побочные действия.
* **Перечисления** возвращают предопределенные постоянные значения. Например, **[Color](functions/function-colors.md)** является перечислением с предопределенными значениями, такими как **Color.Red**, **Color.Blue** и т. д.  Здесь приводятся общие перечисления, а описания перечислений для конкретных функций приводятся в описаниях самих функций.
* **Именованные операторы**, такие как **[ThisItem](functions/operators.md#thisitem-operator)** и **[Parent](functions/operators.md#parent-operator)** , предоставляют доступ к сведениям из контейнера.

К другим элементам относятся:

* [все операторы](functions/operators.md);
* [элементы управления и их свойства](reference-properties.md).
* [Типы данных](functions/data-types.md)

## <a name="a"></a>А
**[Abs](functions/function-numericals.md)** — абсолютное значение числа.  

**[Acceleration](functions/signals.md)** — считывает данные с датчика ускорения на устройстве.

**[Acos](functions/function-trig.md)** — возвращает арккосинус числа (в радианах).

**[Acot](functions/function-trig.md)** — возвращает арккотангенс числа (в радианах).

**[AddColumns](functions/function-table-shaping.md)** — возвращает таблицу с добавленными [столбцами](working-with-tables.md#columns).

**[And](functions/function-logicals.md)** — логическая функция AND.  Возвращает значение **true**, если все аргументы принимают значение **true**.  Также можно использовать [оператор **&&** ](functions/operators.md).

**[Приложение](functions/object-app.md)** — предоставляет сведения о работающем в настоящее время приложении и контроле поведения приложения.

**[Asin](functions/function-trig.md)** — возвращает арксинус числа (в радианах).

**[Астипе](functions/function-astype-istype.md)** — обрабатывает ссылку на запись как конкретный тип сущности.

**[Atan](functions/function-trig.md)** — возвращает арктангенс числа (в радианах).

**[Atan2](functions/function-trig.md)** — возвращает арктангенс на основе координаты (*x*,*y*) (в радианах).

**[Average](functions/function-aggregates.md)** — вычисляет среднее значение табличного выражения или набора аргументов.

## <a name="b"></a>B
**[Back](functions/function-navigate.md)** — отображает предыдущий экран.  

**[Blank](functions/function-isblank-isempty.md)**  — возвращает *пустое* значение, которое может использоваться для вставки значения NULL в источник данных.

## <a name="c"></a>C
**[Calendar](functions/function-clock-calendar.md)** — извлекает календарные данные для текущего значения языкового стандарта.

**[Char](functions/function-char.md)** — преобразует код знака в строку.

**[Choices](functions/function-choices.md)**  — возвращает таблицу из возможных значений для столбца подстановки.

**[Clear](functions/function-clear-collect-clearcollect.md)** — удаляет все данные из [коллекции](working-with-data-sources.md#collections).

**[ClearCollect](functions/function-clear-collect-clearcollect.md)** — удаляет все данные из коллекции, а затем добавляет набор [записей](working-with-tables.md#records).

**[Clock](functions/function-clock-calendar.md)** — извлекает сведения о времени для текущего значения языкового стандарта.

**[Coalesce](functions/function-isblank-isempty.md)**  — заменяет *пустые* значения, оставляя не*пустые* значения без изменений.

**[Collect](functions/function-clear-collect-clearcollect.md)** — создает коллекцию или добавляет данные в источник данных.

**[Color](functions/function-colors.md)** — задает свойство для встроенного значения цвета.

**[ColorFade](functions/function-colors.md)** — изменяет значение цвета, делая его более светлым или темным.

**[ColorValue](functions/function-colors.md)** — преобразует имя цвета CSS или шестнадцатеричный код в значение цвета.  

**[Compass](functions/signals.md)** — возвращает направление по компасу.

**[Concat](functions/function-concatenate.md)** — объединяет строки в источнике данных.  

**[Concatenate](functions/function-concatenate.md)** — объединяет строки.

**[Concurrent](functions/function-concurrent.md)**  — оценивает несколько формул одновременно. 

**[Connection](functions/signals.md)** — возвращает сведения о сетевом подключении.

**[Count](functions/function-table-counts.md)** — подсчитывает количество записей в таблице, которые содержат числа.

**[Cos](functions/function-trig.md)** — возвращает косинус угла, указанного в радианах.

**[Cot](functions/function-trig.md)** — возвращает котангенс угла, указанного в радианах.

**[CountA](functions/function-table-counts.md)** — подсчитывает количество записей в таблице, которые не являются [пустыми](functions/function-isblank-isempty.md).

**[CountIf](functions/function-table-counts.md)** — подсчитывает количество записей в таблице, удовлетворяющих определенному условию.  

**[CountRows](functions/function-table-counts.md)** — подсчитывает количество записей в таблице.   

## <a name="d"></a>D
**[DataSourceInfo](functions/function-datasourceinfo.md)** — предоставляет сведения об источнике данных.

**[Date](functions/function-date-time.md)** — возвращает значение даты и времени на основе значений **Year**, **Month** и **Day**.  

**[DateAdd](functions/function-dateadd-datediff.md)** — добавляет к значению даты и времени дни, месяцы, кварталы или года.

**[DateDiff](functions/function-dateadd-datediff.md)** — вычитает два значения даты и показывает результат в днях, месяцах, кварталах или годах.

**[DateTimeValue](functions/function-datevalue-timevalue.md)** — преобразует строку даты и времени в значение даты и времени.

**[DateValue](functions/function-datevalue-timevalue.md)** — преобразует строку формата ''только дата'' в значение даты и времени.

**[Day](functions/function-datetime-parts.md)** — извлекает сведения о дате из значения даты и времени.  

**[Defaults](functions/function-defaults.md)** — возвращает значения по умолчанию для источника данных.

**[Degrees](functions/function-trig.md)** — преобразует радианы в градусы.

**[Disable](functions/function-enable-disable.md)** — отключает сигнал, например **[Location](functions/signals.md)** для считывания GPS-координат.

**[Distinct](functions/function-distinct.md)** — вычисляет итоговые значения для записей таблицы, удаляя дубликаты.  

**[Download](functions/function-param.md)** — скачивает файл из Интернета на локальное устройство.

**[DropColumns](functions/function-table-shaping.md)** — возвращает таблицу, удаляя из нее один или несколько столбцов.

## <a name="e"></a>E
**[EditForm](functions/function-form.md)** — сбрасывает элемент управления формы для редактирования элемента.

**[Enable](functions/function-enable-disable.md)** — включает сигнал, например **[Location](functions/signals.md)** для считывания GPS-координат.

**[EndsWith](functions/function-startswith.md)** — проверяет, заканчивается ли одна текстовая строка другой.

**[Errors](functions/function-errors.md)** — предоставляет сведения об ошибках для предыдущих изменений источника данных.

**[EncodeUrl](functions/function-encode-decode.md)** — кодирует специальные символы с помощью кодировки URL.

**[Exit](functions/function-exit.md)** — выполняет выход из запущенного приложения.

**[Exp](functions/function-numericals.md)** — возвращает *e*, возведенное в указанную степень.

## <a name="f"></a>C
**[Filter](functions/function-filter-lookup.md)** — возвращает таблицу, отфильтрованную на основе одного или нескольких критериев.

**[Find](functions/function-find.md)** — проверяет, находится ли одна строка внутри другой, и возвращает расположение.

**[First](functions/function-first-last.md)** — возвращает первую запись таблицы.

**[FirstN](functions/function-first-last.md)** — возвращает первый набор записей (N записей) таблицы.

**[ForAll](functions/function-forall.md)** — вычисляет значения и выполняет действия для всех записей в таблице.

## <a name="g"></a>G
**[GroupBy](functions/function-groupby.md)** — возвращает таблицу со сгруппированными записями.

**[GUID](functions/function-guid.md)**  — преобразует строку GUID в значение GUID или создает новое значение GUID.

## <a name="h"></a>H
**[HashTags](functions/function-hashtags.md)** — извлекает из строки хэш-теги (#strings).

**[Hour](functions/function-datetime-parts.md)** — возвращает данные времени в часах из значения даты и времени.

## <a name="i"></a>I
**[If](functions/function-if.md)** — возвращает одно значение, если условие выполняется, и другое, если то же условие не выполняется. 

**[IfError](functions/function-iferror.md)** — обнаруживает ошибки и предоставляет альтернативное значение или выполняет действие. 

**[IsBlank](functions/function-isblank-isempty.md)** — проверяет наличие значений [blank](functions/function-isblank-isempty.md) (пусто).

**[IsEmpty](functions/function-isblank-isempty.md)** — проверяет наличие пустых таблиц.

**[IsMatch](functions/function-ismatch.md)** — проверяет строку на соответствие определенному шаблону.  Можно использовать регулярные выражения.

**[IsNumeric](functions/function-isnumeric.md)** — проверяет, является ли значение числовым.

**[IsToday](functions/function-now-today-istoday.md)** — проверяет, не попадает ли значение даты и времени на сегодняшний день.

IsReference **[— проверяет](functions/function-astype-istype.md)** , ссылается ли ссылка на запись на конкретный тип сущности.

## <a name="j"></a>J
**[JSON](functions/function-json.md)** — создает текстовую строку JSON для таблицы, записи или значения.

## <a name="l"></a>L
**[Language](functions/function-language.md)** — возвращает тег языка текущего пользователя.

**[Last](functions/function-first-last.md)** — возвращает последнюю запись таблицы.

**[LastN](functions/function-first-last.md)** — возвращает последний набор записей (N записей) таблицы.

**[Launch](functions/function-param.md)** — запускает веб-адрес или приложение.

**[Left](functions/function-left-mid-right.md)** — возвращает левую часть строки.

**[Len](functions/function-len.md)** — возвращает длину строки.

**[Ln](functions/function-numericals.md)** — возвращает натуральный логарифм.

**[LoadData](functions/function-savedata-loaddata.md)** — загружает коллекцию из частного хранилища PowerApps.

**[Location](functions/signals.md)** — возвращает расположение в виде координат на карте, используя глобальную навигационную спутниковую систему (GPS) и другие сведения.

**[LookUp](functions/function-filter-lookup.md)** — выполняет поиск одной записи в таблице, основываясь на одном или нескольких критериях.

**[Lower](functions/function-lower-upper-proper.md)** — преобразует буквы текстовой строки во все строчные.

## <a name="m"></a>M
**[Match](functions/function-ismatch.md)** — Извлекает подстроку на основе шаблона.  Можно использовать регулярные выражения.

**[MatchAll](functions/function-ismatch.md)** — извлекает несколько подстрок на основе шаблона.  Можно использовать регулярные выражения.

**[Max](functions/function-aggregates.md)** — максимальное значение табличного выражения или набора аргументов.

**[Mid](functions/function-left-mid-right.md)** — возвращает среднюю часть строки.

**[Min](functions/function-aggregates.md)** — минимальное значение табличного выражения или набора аргументов.

**[Minute](functions/function-datetime-parts.md)** — возвращает данные времени в минутах из значения даты и времени.  

**[Mod](functions/function-mod.md)** — возвращает остаток от деления одного числа на другое.

**[Month](functions/function-datetime-parts.md)** — извлекает сведения о месяце из значения даты и времени.

## <a name="n"></a>N
**[Navigate](functions/function-navigate.md)** — изменяет отображаемый экран.

**[NewForm](functions/function-form.md)** — сбрасывает элемент управления формы для создания элемента.

**[Not](functions/function-logicals.md)** — логическая функция NOT.  Возвращает значение **true**, если ее аргумент принимает значение **false**, и возвращает **false**, если ее аргумент принимает значение **true**.  Также можно использовать [оператор **!** ](functions/operators.md).

**[Notify](functions/function-showerror.md)**  — отображает баннер с сообщением для пользователя.

**[Now](functions/function-now-today-istoday.md)** — возвращает текущее значение даты и времени.

## <a name="o"></a>O
**[Or](functions/function-logicals.md)** — логическая функция OR.  Возвращает значение **true**, если хотя бы один из ее аргументов принимает значение **true**.  Также можно использовать [оператор **||** ](functions/operators.md).

## <a name="p"></a>P
**[Param](functions/function-param.md)** — предоставляет доступ к параметрам, переданным в приложение при его открытии пользователем.

**[Parent](functions/operators.md#parent-operator)** — предоставляет доступ к свойствам элемента управления контейнера.

**[Patch](functions/function-patch.md)** — изменяет или создает запись в источнике данных или объединяет записи вне источника данных.

**[Pi](functions/function-trig.md)** — возвращает значение числа &pi;.

**[PlainText](functions/function-encode-decode.md)** — удаляет из строки HTML- и XML-теги.

**[Power](functions/function-numericals.md)** — возвращает число, возведенное в степень.  Также можно использовать [оператор **^** ](functions/operators.md).

**[Proper](functions/function-lower-upper-proper.md)** — преобразует в строке первую букву каждого слова в прописную, а остальные буквы преобразует в строчные.

## <a name="r"></a>R
**[Radians](functions/function-trig.md)** — преобразует градусы в радианы.

**[Rand](functions/function-rand.md)** — возвращает псевдослучайное число.

**[Refresh](functions/function-refresh.md)** — обновляет записи источника данных.

**[Связь — связывает](functions/function-relate-unrelate.md)** записи двух сущностей через связь «один ко многим» или «многие ко многим».

**[Remove](functions/function-remove-removeif.md)** — удаляет одну или несколько указанных записей из источника данных.

**[RemoveIf](functions/function-remove-removeif.md)** — удаляет записи из источника данных, если выполняется определенное условие.

**[RenameColumns](functions/function-table-shaping.md)** — переименовывает столбцы в таблице.

**[Replace](functions/function-replace-substitute.md)** — заменяет часть строки другой строкой, используя начальную позицию строки.

**[Reset](functions/function-reset.md)** — сбрасывает элемент управления вводом до значения по умолчанию и отменяет все изменения, внесенные пользователем.

**[ResetForm](functions/function-form.md)** — сбрасывает элемент управления формы для редактирования существующего элемента.

**[Revert](functions/function-revert.md)** — перезагружает содержимое и удаляет ошибки для записей в источнике данных.

**[RGBA](functions/function-colors.md)** — возвращает значение цвета для модели RGBA (набор из красного, зеленого, синего и альфа-фактора).

**[Right](functions/function-left-mid-right.md)** — возвращает правую часть строки.

**[Round](functions/function-round.md)** — округляет до ближайшего числа.

**[RoundDown](functions/function-round.md)** — округляет до ближайшего числа в меньшую сторону.

**[RoundUp](functions/function-round.md)** — округляет до ближайшего числа в большую сторону.

## <a name="s"></a>S
**[SaveData](functions/function-savedata-loaddata.md)** — сохраняет коллекцию в частном хранилище PowerApps.

**[Search](functions/function-filter-lookup.md)** — находит записи в таблице, содержащие строку в одном из столбцов.  

**[Second](functions/function-datetime-parts.md)** — возвращает данные времени в секундах из значения даты и времени.

**[Select](functions/function-select.md)**  — имитирует действие выбора элемента управления, активируя вычисление формулы **OnSelect**.

**[Set](functions/function-set.md)** — задает значение глобальной переменной.

**[SetFocus](functions/function-setfocus.md)** — перемещение фокуса ввода на конкретный элемент управления.

**[ShowColumns](functions/function-table-shaping.md)** — возвращает таблицу только с выбранными столбцами.

**[Shuffle](functions/function-shuffle.md)** — случайным образом изменяет порядок записей в таблице.

**[Sin](functions/function-trig.md)** — возвращает синус угла, указанного в радианах.

**[Sort](functions/function-sort.md)** — возвращает таблицу, отсортированную на основе формулы.

**[SortByColumns](functions/function-sort.md)** — возвращает таблицу, отсортированную по одному или нескольким столбцам.

**[Split](functions/function-split.md)** — эта функция разбивает строку текста в таблицу с подстроками.

**[Sqrt](functions/function-numericals.md)** — возвращает квадратный корень числа.

**[StartsWith](functions/function-startswith.md)** — проверяет, начинается ли одна текстовая строка с другой.

**[StdevP](functions/function-aggregates.md)** — возвращает стандартное отклонение своих аргументов.  

**[Substitute](functions/function-replace-substitute.md)** — заменяет часть строки другой строкой, используя совпадение строк.

**[SubmitForm](functions/function-form.md)** — сохраняет элемент из элемента управления формы в источнике данных.

**[Sum](functions/function-aggregates.md)** — вычисляет сумму табличного выражения или набора аргументов.  

**[Switch](functions/function-if.md)**  — выполняет сопоставление с набором значений, а затем вычисляет соответствующую формулу.

## <a name="t"></a>T
**[Table](functions/function-table.md)** — создает временную таблицу.  

**[Tan](functions/function-trig.md)** — возвращает тангенс угла, указанного в радианах.

**[Text](functions/function-text.md)** — преобразует любое значение и форматирует число или значение даты и времени в строку текста.

**[ThisItem](functions/operators.md#thisitem-operator)** — в коллекции или форме возвращает данные для текущего элемента из контейнера.

**[Time](functions/function-date-time.md)** — возвращает значение даты и времени на основе значений **Hour**, **Minute** и **Second**.  

**[TimeValue](functions/function-datevalue-timevalue.md)** — преобразует строку формата ''только время'' в значение даты и времени.

**[TimeZoneOffset](functions/function-dateadd-datediff.md)**  — возвращает разницу между временем в формате UTC и местным временем пользователя в минутах.

**[Today](functions/function-now-today-istoday.md)** — возвращает текущее значение даты и времени.

**[Trim](functions/function-trim.md)** — удаляет лишние пробелы по краям и внутри текстовой строки.

**[TrimEnds](functions/function-trim.md)** — удаляет лишние пробелы только по краям текстовой строки.

## <a name="u"></a>U
**[Ungroup](functions/function-groupby.md)** — удаляет группирование.

**[Unrelate](functions/function-relate-unrelate.md)** — отменяет связь между записями двух сущностей со связью "один ко многим" или "многие ко многим".

**[Update](functions/function-update-updateif.md)** — заменяет запись в источнике данных.

**[UpdateContext](functions/function-updatecontext.md)** — задает значение одной или нескольких [переменных контекста](working-with-variables.md#use-a-context-variable) на текущем экране.

**[UpdateIf](functions/function-update-updateif.md)** — изменяет набор записей в источнике данных, если выполняется определенное условие.

**[Upper](functions/function-lower-upper-proper.md)** — преобразует буквы текстовой строки во все прописные.

**[User](functions/function-user.md)** — возвращает сведения о текущем пользователе.

## <a name="v"></a>V
**[Validate](functions/function-validate.md)** — проверяет, являются ли значения одного столбца или всей записи допустимыми для источника данных.

**[Value](functions/function-value.md)** — преобразует строку в число.

**[VarP](functions/function-aggregates.md)** — возвращает расхождение своих аргументов.  

**[ViewForm](functions/function-form.md)** — сбрасывает элемент управления формой для просмотра существующего элемента.

## <a name="w"></a>W
**[Weekday](functions/function-datetime-parts.md)** — извлекает сведения о дне недели из значения даты и времени.

**[With](functions/function-with.md)** — вычисляет значения и выполняет действия для одной записи, включая встроенные записи именованных значений.

## <a name="y"></a>Y
**[Year](functions/function-datetime-parts.md)** — извлекает сведения о годе из значения даты и времени.  

