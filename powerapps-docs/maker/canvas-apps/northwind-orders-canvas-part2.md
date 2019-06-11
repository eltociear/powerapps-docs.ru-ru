---
title: Создание сводки формы в приложение на основе холста | Документация Майкрософт
description: Создание сводки формы в приложение для управления данными для Northwind Traders на основе холста
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/25/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5c40cb030241d142a2ee2a68d32f7fb839a350ff
ms.sourcegitcommit: 55bc11ac6a964f22301c9fdadb06ee34e1399f83
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66806741"
ms.PowerAppsDecimalTransform: true
---
# <a name="create-a-summary-form-in-a-canvas-app"></a>Создание сводки формы в приложение на основе холста

Выполните пошаговые инструкции для создания сводки формы в приложение на основе холста для управления вымышленные данные в базе данных Northwind Traders. Этот раздел является частью серии, в которой объясняется, как создать бизнес-приложения на реляционных данных в Common Data Service. Для получения наилучших результатов изучите следующие разделы в этой последовательности:

1. [Как создать галерею с порядок](northwind-orders-canvas-part1.md).
2. Создание сводки формы (**в этом разделе**).
3. [Создать галерею подробно](northwind-orders-canvas-part3.md).

> [!div class="mx-imgBorder"]
> ![Определение области экрана](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>Технические условия

1. [Установка приложения и базы данных Northwind Traders](northwind-install.md).
1. Просмотрите [Обзор приложения на основе холста](northwind-orders-canvas-overview.md) для Northwind Traders.
1. [Создание коллекции порядок](northwind-orders-canvas-part1.md) самостоятельно, либо открыть **Northwind Orders (холст) — часть 2 начать** приложение, которое уже содержит этой коллекции.

## <a name="add-a-title-bar"></a>Добавление строки заголовка

В верхней части приложения создайте заголовок окна, которая будет содержать кнопки действий в конце этого раздела.

1. В **представление в виде дерева** области выберите **Screen1** чтобы убедиться, что вы не добавляйте случайно элемент управления в коллекцию порядок:

    > [!div class="mx-imgBorder"]
    > ![Выберите Screen1 в области представления дерева](media/northwind-orders-canvas-part2/titlebar-01.png)

1. На **вставить** выберите **метка** вставляемый [ **метка** ](controls/control-text-box.md) управления:

    > [!div class="mx-imgBorder"]
    > ![Добавить метку](media/northwind-orders-canvas-part2/titlebar-02.png)

    Новая метка должна появляться только один раз, над коллекцией. Если он отображается в каждом элементе коллекции, удалите первый экземпляр метки, убедитесь, что экрана выбран (как описано в предыдущем шаге) и затем снова вставить метку.

1. Перемещение и изменение размеров новую метку для охвата верхней части экрана:

    > [!div class="mx-imgBorder"]
    > ![Перемещение и изменение размера метки](media/northwind-orders-canvas-part2/titlebar-03.png)

1. Дважды щелкните текст метки, а затем введите **Northwind Orders**.

    Кроме того, изменить **текст** свойства в строке формул для достижения такого же результата:

    > [!div class="mx-imgBorder"]
    > ![Измените текст в строке заголовка](media/northwind-orders-canvas-part2/titlebar-04.png)

1. На **Главная** вкладке, форматировать метки:
    - Увеличьте размер шрифта, размер 24 пункта.
    - Выделите текст полужирным шрифтом.
    - Задание белого текста.
    - Выравнивание текста по центру.
    - Добавьте заливку Темно синий фон.

    > [!div class="mx-imgBorder"]
    > ![Параметры форматирования на вкладке "Главная"](media/northwind-orders-canvas-part2/titlebar-05.png)

## <a name="add-an-edit-form-control"></a>Добавьте элемент управления формы для редактирования

В этом разделе вы добавите элементы управления, чтобы показать сводную информацию любого заказа, выбранного пользователем в коллекции.

1. На **вставить** вкладке, вставить [ **форма редактирования** ](controls/control-form-detail.md) управления:

    > [!div class="mx-imgBorder"]
    > ![Добавьте элемент управления формы для редактирования](media/northwind-orders-canvas-part2/form-01.png)

    По умолчанию формы отображается в левом верхнем углу, где другие элементы управления может быть сложно найти:

    > [!div class="mx-imgBorder"]
    > ![Изменение элемента управления формы в расположение по умолчанию](media/northwind-orders-canvas-part2/form-02.png)

1. Перемещение и изменение размера формы, чтобы охватить в правом верхнем углу экрана под строкой заголовка:

    > [!div class="mx-imgBorder"]
    > ![Перемещение и изменение размеров элемента управления формы редактирования](media/northwind-orders-canvas-part2/form-03.png)

1. В строке формул задайте **DataSource** свойства формы, чтобы это значение:

    ```powerapps-comma
    Orders
    ```

    > [!div class="mx-imgBorder"]
    > ![Задайте свойство DataSource элемента управления формы](media/northwind-orders-canvas-part2/form-04.png)

    То же свойство можно задать **свойства** вкладке рядом с правым краем, но этот подход добавляет поля, которые не используются в форму. Если вы используете строку формул, форма остается пустой.

## <a name="add-and-arrange-fields"></a>Добавление и размещение полей

1. В **свойства** вкладка рядом с правым краем выберите **изменить поля** открыть **поля** области:

    > [!div class="mx-imgBorder"]
    > ![Откройте панель "поля"](media/northwind-orders-canvas-part2/form-05.png)

1. В **поля** области выберите **добавить поле**и затем установите флажки для **клиента** и **сотрудника** поля.

    > [!div class="mx-imgBorder"]
    > ![Добавьте в форму элемент управления редактирования поля клиентов и сотрудников](media/northwind-orders-canvas-part2/form-06.png)

1. Прокрутите вниз, пока эти поля отображаются и затем установите их флажки:

    - **Примечания**
    - **Дата заказа**
    - **Номер заказа**
    - **Состояние заказа**
    - **Дата оплаты**

    > [!div class="mx-imgBorder"]
    > ![Добавьте пять дополнительных полей в форму элемент управления редактирования](media/northwind-orders-canvas-part2/form-07.png)

1. В нижней части **поля** области выберите **добавить**, а затем закройте **поля** области.

    В форме будет представлена семь полей:

    > [!div class="mx-imgBorder"]
    > ![Элемент управления формы редактирования отображает семь полей](media/northwind-orders-canvas-part2/form-08.png)

    > [!NOTE]
    > Если любое поле отображается красный значок ошибки, может возникла проблема при извлечения данных из источника. Чтобы устранить эту ошибку, обновите данные:
    >
    > 1. На вкладке **Вид** выберите **источники данных**.
    > 1. В **данных** области выберите **источников данных**.
    > 1. Рядом с полем **заказы**, нажмите кнопку с многоточием (...), выберите **обновить**и закройте **данных** области.
    >
    > Если поле со списком для имени клиентов или сотрудников по-прежнему отображается ошибка, проверьте **основной текст** и **SearchField** каждого поля, выбрав его и затем открыв **данных** область. Для окна клиента оба поля должно быть присвоено **nwind_company**. Для поля employee, оба поля должно быть присвоено **nwind_lastname**.

1. Выбрав форму, измените число столбцов в форме от 3 до 12 в **свойства** вкладка рядом с правым краем.

    На этом шаге добавляется гибкость, так как вы упорядочите поля:

    > [!div class="mx-imgBorder"]
    > ![Затем измените число столбцов в элементе управления формы](media/northwind-orders-canvas-part2/form-08b.png)

    Многие модели пользовательского интерфейса полагаться на 12 колонкой, поскольку они равномерно способна выдержать строки 1, 2, 3, 4, 6 и 12 элементов управления. В этом разделе вы создадите строк, содержащих 1, 2 или 4 элементов управления.

1. Перемещение и изменение размера полей, перетаскивая их обрабатывает, так же, как любой другой элемент управления, таким образом, чтобы каждая строка содержит карты эти данные в указанном порядке:

    - Первая строка: **Номер заказа**, **Order Status**, **Order Date**, и **платные даты**
    - Второй строки: **Клиент** и **сотрудника**
    - Третья строка: **Примечания**

    > [!NOTE]
    > Может оказаться проще расширить **заметки**, **клиента**, и **сотрудника** данных карты, прежде чем упорядочить их.

    > [!div class="mx-imgBorder"]
    > ![Перемещение и изменение размера поля](media/northwind-orders-canvas-part2/form-rearrange.gif)

    Дополнительные сведения о том, как расположение полей в форме: [Общие сведения о макетах форм данных для приложений на основе холста](working-with-form-layout.md).

## <a name="hide-time-controls"></a>Скрытие элементов управления времени

В этом примере нет необходимости части поля дат по времени, так как этот уровень детализации может отвлечь пользователя. Если вы удалите их, может вызвать проблемы в формулах, которые зависят от этих элементов управления для обновления значений даты или определения позиции другого элемента управления в карточке данных. Вместо этого будет скрывать элементы управления времени, задав их **Visible** свойство.

1. В **представление в виде дерева** области выберите **Дата заказа** Карточка данных.

    Карточка может иметь другое имя, но содержит **Дата заказа**.

1. Удерживая нажатой клавишу Shift, выберите час, минуту и двоеточие элементы управления в **Дата заказа** Карточка данных.

    > [!div class="mx-imgBorder"]
    > ![Выберите время элементы управления в карточке Дата заказа](media/northwind-orders-canvas-part2/form-09.png)

1. Настройка элементов управления **Visible** свойства **false**.

    Все выбранные элементы управления исчезают из формы:

    > [!div class="mx-imgBorder"]
    > ![Свойство Visible равным false.](media/northwind-orders-canvas-part2/form-10.png)

1. Изменение размера [ **Выбор даты** ](controls/control-date-picker.md) управления для отображения полной даты:

    > [!div class="mx-imgBorder"]
    > ![Изменение размера элемента выбора даты](media/northwind-orders-canvas-part2/form-11.png)

    Далее будет повторена последних шагах для **платные даты** поля.

1. В **представление в виде дерева** области выберите время элементов управления в **платные даты** карточки данных:

    > [!div class="mx-imgBorder"]
    > ![Выберите время управления в карточке платные даты](media/northwind-orders-canvas-part2/form-12.png)

1. Задать выбранные элементы управления **Visible** свойства **false**:

    > [!div class="mx-imgBorder"]
    > ![Свойство Visible равным false.](media/northwind-orders-canvas-part2/form-13.png)

1. Изменение размера элементе выбора даты в **Дата оплачиваемого** карты:

    > [!div class="mx-imgBorder"]
    > ![Изменение размера элемента выбора даты](media/northwind-orders-canvas-part2/form-14.png)

## <a name="connect-the-order-gallery"></a>Подключение коллекции заказа

1. В **представление в виде дерева** области свернуть формы, которые помогут вам быстро найти имя коллекции заказа и, при необходимости измените имя на **Gallery1**.

1. Сводка формы задайте **элемент** свойство следующее выражение:

    ```powerapps-comma
    Gallery1.Selected
    ```

    > [!div class="mx-imgBorder"]
    > ![Задайте для свойства элемента формы](media/northwind-orders-canvas-part2/form-15.png)

    В форме будет представлена сводка по независимо от порядка, пользователь выбирает в списке.

    > [!div class="mx-imgBorder"]
    > ![Выберите в списке для отображения в форме ее Обзор](media/northwind-orders-canvas-part2/form-select.gif)

## <a name="replace-a-data-card"></a>Заменить карточки данных

**Номер заказа** — это идентификатор, присвоенный Common Data Service автоматически при создании записи. Это поле имеет [ **ввода текста** ](controls/control-text-input.md) управления по умолчанию, но вы замените его метку, чтобы пользователь в этом поле нельзя изменить.

1. Выберите форму, выберите **изменить поля** в **свойства** рядом с правым краем, а затем выберите **номер заказа** поля:

    > [!div class="mx-imgBorder"]
    > ![Выберите поле номер заказа](media/northwind-orders-canvas-part2/alt-01.png)

1. Откройте **типа элемента управления** списка:

    > [!div class="mx-imgBorder"]
    > ![Откройте ** список управления типа **](media/northwind-orders-canvas-part2/alt-02,png)

1. Выберите **просмотра текста** карточки данных:

    > [!div class="mx-imgBorder"]
    > ![Выберите ** представления текста ** карточки данных](media/northwind-orders-canvas-part2/alt-02b.png)

1. Закрыть **поля** области.

    Пользователь больше не может изменить порядковый номер:

    > [!div class="mx-imgBorder"]
    > ![Порядковый номер только для чтения](media/northwind-orders-canvas-part2/alt-03.png)

1. На **Главная** вкладке, изменить размер шрифта номер заказа на 20 точек, таким образом, чтобы поле было легко найти:

    > [!div class="mx-imgBorder"]
    > ![Изменить размер шрифта номер заказа](media/northwind-orders-canvas-part2/alt-04.png)

## <a name="use-a-many-to-one-relationship"></a>Используйте отношение многие к одному

**Заказы** сущность имеет отношение "многие к одному" с **сотрудников** сущности: каждого сотрудника можно создать много заказов, но каждый заказ может быть назначен только одному сотруднику. Когда пользователь выбирает сотрудника в [ **поле со списком** ](controls/control-combo-box.md) элемента управления, его **выбранные** свойство предоставляет всю запись сотрудника из **сотрудников**  сущности. Таким образом, можно настроить [ **изображение** ](controls/control-image.md) управления для представления пользователю представление о любой сотрудник выбирает в поле со списком.

1. Выберите **сотрудника** карточки данных:

    > [!div class="mx-imgBorder"]
    > ![Выбор карточки данных сотрудников](media/northwind-orders-canvas-part2/employee-01.png)

1. В **Дополнительно** вкладке рядом с правым краем, разблокировать карточку данных, чтобы можно было отредактировать формулы, которые были ранее доступны только для чтения:

    > [!div class="mx-imgBorder"]
    > ![Разблокировать карточку данных сотрудников](media/northwind-orders-canvas-part2/employee-02.png)

1. В карточке данных уменьшите ширину поля со списком, чтобы освободить место для рисунка сотрудника:

    > [!div class="mx-imgBorder"]
    > ![Размер элемента управления полем со списком](media/northwind-orders-canvas-part2/employee-03b.png)

1. На **вставить** выберите **мультимедиа** > **изображение**:

    > [!div class="mx-imgBorder"]
    > ![Вставить изображение](media/northwind-orders-canvas-part2/employee-04.png)

    Изображение снова появится в карточке данных, которая разворачивается для нее:

    > [!div class="mx-imgBorder"]
    > ![Карточки данных сотрудников с помощью элемента управления Image](media/northwind-orders-canvas-part2/employee-05.png)

1. Изменяет размер изображения и переместите его в правой части поля со списком:

    > [!div class="mx-imgBorder"]
    > ![Перемещение и изменение размеров элемента управления image](media/northwind-orders-canvas-part2/employee-06.png)

1. Задайте **изображение** свойство изображения следующую формулу, заменив номер в конце DataCardValue при необходимости:

    ```powerapps-comma
    DataCardValue7.Selected.Picture
    ```

    > [!div class="mx-imgBorder"]
    > ![Задайте для свойства изображения образа](media/northwind-orders-canvas-part2/employee-07.png)

    Рисунок выбранного сотрудника отображается.

1. Удерживая нажатой клавишу Alt, выделите другому сотруднику в поле со списком, чтобы убедиться, что размер изображения изменяется.

    > [!div class="mx-imgBorder"]
    > ![Выберите сотрудника отображения рисунка сотрудника](media/northwind-orders-canvas-part2/employee-select.gif)

## <a name="add-a-save-icon"></a>Добавить значок сохранения

1. В **представление в виде дерева** области выберите **Screen1**, а затем выберите **вставить** > **значки**  >  **Проверьте**:

    > [!div class="mx-imgBorder"]
    > ![Значок галочки](media/northwind-orders-canvas-part2/save-01.png)

    [ **Проверьте** ](controls/control-shapes-icons.md) отображается значок в левом верхнем углу по умолчанию, где другие элементы управления могут затруднить значок поиска:

    > [!div class="mx-imgBorder"]
    > ![Значок в расположение по умолчанию](media/northwind-orders-canvas-part2/save-02.png)

1. На **Главная** вкладке **цвет** свойства значка на белый, изменить размер значка и переместите его рядом с правым краем строки заголовка:

    > [!div class="mx-imgBorder"]
    > ![Настроить цвет, размер и расположение сохранения значок](media/northwind-orders-canvas-part2/save-03.png)

1. В **представление в виде дерева** области, убедитесь, что имя формы **Form1**, а затем установите значок **OnSelect** следующую формулу:

    ```powerapps-comma
    SubmitForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![Задайте свойства OnSelect значка](media/northwind-orders-canvas-part2/save-04.png)

    Когда пользователь выбирает значок [ **SubmitForm** ](functions/function-form.md) функция собирает все измененные значения в форме и отправляет их в источник данных. Точек марта в верхней части экрана, как данные передаются, и порядок коллекции отражает изменения после завершения процесса.

1. Значок **DisplayMode** следующую формулу:

    ```powerapps-comma
    If( Form1.Unsaved; DisplayMode.Edit; DisplayMode.Disabled )
    ```

    > [!div class="mx-imgBorder"]
    > ![Установите свойство DisplayMode значка](media/northwind-orders-canvas-part2/save-05.png)

    Если были сохранены все изменения в форму, значок и отображается в **DisabledColor**, который затем необходимо настроить.

1. Значок **DisabledColor** следующее значение:

    ```powerapps-comma
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![Установите свойство DisabledColor значок](media/northwind-orders-canvas-part2/save-06.png)

    Пользователь может сохранить изменения в заказ, выбрав значок с галочкой, которая затем отключено и недоступно, пока пользователь делает еще одно изменение:

    > [!div class="mx-imgBorder"]
    > ![Сохранение изменений](media/northwind-orders-canvas-part2/save-submit.gif)

## <a name="add-a-cancel-icon"></a>Добавить значок отмены

1. На **вставить** выберите **значки** > **отменить**:

    > [!div class="mx-imgBorder"]
    > ![Добавить значок отмены](media/northwind-orders-canvas-part2/save-07.png)

    Значок отображается в левом верхнем углу по умолчанию, где другие элементы управления могут затруднить значок поиска:

    > [!div class="mx-imgBorder"]
    > ![Значок отмены в расположении по умолчанию](media/northwind-orders-canvas-part2/save-08.png)

1. На **Главная** вкладке, изменить значок **цвет** свойство на белый, изменить размер значка и переместите его влево значок с изображением флажка:

    > [!div class="mx-imgBorder"]
    > ![Изменить цвет, размер и расположение значка "Отмена"](media/northwind-orders-canvas-part2/save-09.png)

1. Задать значок отмены **OnSelect** следующую формулу:

    ```powerapps-comma
    ResetForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![Значок "Отмена" для свойства OnSelect](media/northwind-orders-canvas-part2/save-10.png)

    [ **ResetForm** ](functions/function-form.md) функция отменяет все изменения в форме, которая возвращается в исходное состояние.

1. Задать значок отмены **DisplayMode** следующую формулу:

    ```powerapps-comma
    If( Form1.Unsaved Or Form1.Mode = FormMode.New; DisplayMode.Edit; DisplayMode.Disabled )
    ```

    > [!div class="mx-imgBorder"]
    > ![Установите свойство DisplayMode значок отмены](media/northwind-orders-canvas-part2/save-11.png)

    Эта формула отличается несколько отличается от используемого для значок с галочкой. Значок отмены будет отключен, если все изменения были сохранены или форма находится в **New** режиме, который затем будет включена. В этом случае **ResetForm** отбрасывает новой записи.

1. Задать значок отмены **DisabledColor** следующее значение:

    ```powerapps-comma
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![Установите свойство DisabledColor значок отмены](media/northwind-orders-canvas-part2/save-12.png)

    Пользователь может отменить изменения в заказ, и флажок "и" Отмена значки отключаются и недоступна, если все изменения были сохранены:

    > [!div class="mx-imgBorder"]
    > ![Сохранение и Отмена изменений](media/northwind-orders-canvas-part2/save-cancel.gif)

## <a name="add-an-add-icon"></a>Добавить значок Add

1. На **вставить** выберите **значки** > **добавить**.

    > [!div class="mx-imgBorder"]
    > ![Вставьте значок Add](media/northwind-orders-canvas-part2/save-13.png)

    **Добавить** отображается значок в левом верхнем углу по умолчанию, где другие элементы управления может быть сложно найти:

    > [!div class="mx-imgBorder"]
    > ![Расположение по умолчанию значок добавления](media/northwind-orders-canvas-part2/save-14.png)

1. На **Главная** вкладке **цвет** свойство значок добавления на белый, изменить размер значка и переместите его слева от значка "Отмена":

    > [!div class="mx-imgBorder"]
    > ![Изменение цвета, размера и расположения значок добавления](media/northwind-orders-canvas-part2/save-15.png)

1. Задать значок добавления **OnSelect** следующую формулу:

    ```powerapps-comma
    NewForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![Установите свойство OnSelect значок добавления](media/northwind-orders-canvas-part2/save-15b.png)

    [ **NewForm** ](functions/function-form.md) функция показана пустую запись в форме.  

1. Задать значок добавления **DisplayMode** следующую формулу:

    ```powerapps-comma
    If( Form1.Unsaved Or Form1.Mode = FormMode.New; DisplayMode.Disabled; DisplayMode.Edit )
    ```

    > [!div class="mx-imgBorder"]
    > ![Установите свойство DisplayMode значок добавления](media/northwind-orders-canvas-part2/save-16.png)

    Формула отключает значок добавления в этих условиях:

    - Пользователь вносит изменения, но не сохранить или отменить их, который является противоположным результатам из набора значков проверка и Отмена.
    - Пользователь выбирает значок добавления, но не вносит никаких изменений.

1. Задать значок добавления **DisabledColor** следующее значение:

    ```powerapps-comma
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![Установите свойство DisabledColor значок добавления](media/northwind-orders-canvas-part2/save-17.png)

    Пользователь может создать заказ, если они не вносить изменения или их сохранить или отменить все изменения, внесенные они. (Если пользователь щелкнет этот значок, они не удается выбрать его снова до их внести одно или несколько изменений и сохранить или отменить эти изменения):

    > [!div class="mx-imgBorder"]
    > ![Создание заказа](media/northwind-orders-canvas-part2/save-new.gif)

> [!NOTE]
> Если вы создаете и сохранить заказ, может потребоваться выполнить прокрутку вниз в порядке коллекции, чтобы отобразить новый заказ. Он не будет итоговая цена, так как вы еще не добавили сведений о заказе.

## <a name="add-a-trash-icon"></a>Добавить значок корзины

1. На **вставить** выберите **значки** > **корзины**.

    > [!div class="mx-imgBorder"]
    > ![Вставьте значок корзины](media/northwind-orders-canvas-part2/save-18.png)

    **Корзины** отображается значок в левом верхнем углу по умолчанию, где другие элементы управления может быть сложно найти:

    > [!div class="mx-imgBorder"]
    > ![Расположение по умолчанию значок корзины](media/northwind-orders-canvas-part2/save-19.png)

1. На **Главная** вкладке, измените значок корзины **цвет** свойство на белый, изменить размер значка и переместите его влево значок добавления:

    > [!div class="mx-imgBorder"]
    > ![Изменить цвет, размер и расположение значка корзины](media/northwind-orders-canvas-part2/save-20.png)

1. Задать значок корзины **OnSelect** следующую формулу:

    ```powerapps-comma
    Remove( Orders; Gallery1.Selected )
    ```

    > [!div class="mx-imgBorder"]
    > ![Установите свойство OnSelect значок корзины](media/northwind-orders-canvas-part2/save-21.png)

    [ **Удалить** ](functions/function-remove-removeif.md) функция удаляет запись из источника данных. В этой формуле функция удаляет запись, которую выбрал в коллекции заказа. Значок корзины появляется рядом сводной форме (не коллекции заказа), поскольку форма отображает дополнительные сведения о записи, чтобы пользователю было легче идентифицировать запись, которая приведет к удалению формулы.

1. Задать значок корзины **DisplayMode** следующую формулу:

    ```powerapps-comma
    If( Form1.Mode = FormMode.New; DisplayMode.Disabled; DisplayMode.Edit )
    ```

    > [!div class="mx-imgBorder"]
    > ![Установите свойство DisplayMode значок корзины](media/northwind-orders-canvas-part2/save-22.png)

    Эта формула отключает значок корзины, если пользователь создает запись. Пока пользователь не сохранит записи **удалить** функция не имеет записи для удаления.

1. Задать значок корзины **DisabledColor** следующее значение:

    ```powerapps-comma
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![Установите свойство DisabledColor значок корзины](media/northwind-orders-canvas-part2/save-23.png)

    Пользователь может удалять заказа.

    > [!div class="mx-imgBorder"]
    > ![Удаление заказов](media/northwind-orders-canvas-part2/save-delete.gif)

## <a name="summary"></a>Сводка

Формулируя кратко, вы добавили формы, в котором пользователь может показать и изменения сводки о каждом заказе, и вы использовали эти элементы:

- Формы, в которой представлены данные о **заказы** сущности: **Form1.DataSource =** `Orders`
- Подключение между формой и порядок коллекции: **Form1.Item =** `Gallery1.Selected`
- Элемент управления альтернативного для **номер заказа** поля: **Просмотр текста**
- Отношение "многие к одному" отображения рисунка сотрудника в **сотрудника** карточки данных: `DataCardValue1.Selected.Picture`
- Значок, чтобы сохранить изменения в заказ: `SubmitForm( Form1 )`
- Значок для отмены изменений в заказ: `ResetForm( Form1 )`
- Значок, чтобы создать заказ: `NewForm( Form1 )`
- Значок удаления заказа: `Remove( Orders; Gallery1.Selected )`

## <a name="next-step"></a>Дальнейшие действия

В следующем разделе вам предстоит добавить другой коллекции, чтобы отобразить продукты в каждый заказ, а вы измените эти сведения с помощью [ **Patch** ](functions/function-patch.md) функции.

> [!div class="nextstepaction"]
> [Создание коллекции данных](northwind-orders-canvas-part3.md)