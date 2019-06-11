---
title: Создать коллекцию данных в приложение на основе холста | Документация Майкрософт
description: Создать коллекцию данных в приложение для управления данными для Northwind Traders на основе холста
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
ms.openlocfilehash: 9549b8f389cf696cf3fc8e4659da6b418383ac6e
ms.sourcegitcommit: e85072f7a80da308c4caabe20adbf2509588ca57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66760966"
ms.PowerAppsDecimalTransform: true
---
# <a name="create-a-detail-gallery-in-a-canvas-app"></a>Создать коллекцию данных в приложение на основе холста

Выполните пошаговые инструкции для создания коллекции данных в приложение на основе холста для управления вымышленные данные в базе данных Northwind Traders. Этот раздел является частью серии, в которой объясняется, как создать бизнес-приложения на реляционных данных в Common Data Service. Для получения наилучших результатов изучите следующие разделы в этой последовательности:

1. [Как создать галерею с порядок](northwind-orders-canvas-part1.md).
1. [Создание сводки формы](northwind-orders-canvas-part2.md).
1. Создать галерею детализации (**в этом разделе**).

> [!div class="mx-imgBorder"]
> ![Определение области экрана](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>Технические условия

Перед началом в этом разделе, необходимо установить базы данных, как описано ранее в этом разделе. Необходимо затем создание коллекции заказа и сводной форме или открыть **Northwind Orders (холст) — часть 3 начать** приложение, которое уже содержит этой коллекции и этой формы.

## <a name="create-another-title-bar"></a>Создайте другой заголовок

1. В верхней части экрана, выберите [ **метка** ](controls/control-text-box.md) управления, который выступает в качестве строки заголовка, скопируйте его, нажав клавиши Ctrl-C, а затем вставьте его, нажав клавиши Ctrl-v.

    > [!div class="mx-imgBorder"]
    > ![Скопируйте и вставьте строку заголовка](media/northwind-orders-canvas-part3/details-01.png)

1. Изменение размера и переместить ее таким образом, чтобы он отображался под сводной форме.

1. Удалите текст из копии в любом из следующих способов:

    - Дважды щелкните текст, выделите его и нажмите клавишу Delete.
    - Задание метки **текст** свойству пустую строку ( **«»** ).

    > [!div class="mx-imgBorder"]
    > ![Удалите текст из копии строки заголовка](media/northwind-orders-canvas-part3/details-02.png)

## <a name="add-a-gallery"></a>Добавление коллекции

1. Вставить [ **коллекции** ](controls/control-gallery.md) управления **пустая, вертикальная** макета:

    > [!div class="mx-imgBorder"]
    > ![Добавить пустую вертикальную коллекцию](media/northwind-orders-canvas-part3/details-03.png)

    Новая коллекция, отобразятся сведения о заказе, отображается в левом верхнем углу:

    > [!div class="mx-imgBorder"]
    > ![Расположение по умолчанию для коллекции сведения о заказе](media/northwind-orders-canvas-part3/details-04.png)

1. Закрыть **данных** области и затем изменения размеров и перемещение коллекции сведений в правый нижний угол, под заголовком окна нового:

    > [!div class="mx-imgBorder"]
    > ![Конечное расположение сведений о заказах коллекции](media/northwind-orders-canvas-part3/details-05.png)

1. Задайте **элементы** свойство детализации коллекции следующую формулу:

    ```powerapps-comma
    Gallery1.Selected.'Order Details'
    ```

    > [!div class="mx-imgBorder"]
    > ![Задайте для свойства Items коллекции данных](media/northwind-orders-canvas-part3/details-06.png)

    Если отображается сообщение об ошибке, убедитесь, что порядок коллекции называется **Gallery1** (в **представление в виде дерева** панель у левого края). Если этой коллекции имеет другое имя, переименуйте его **Gallery1**.

    Просто связаны две коллекции. Когда пользователь выбирает заказ в порядке коллекции, этот выбор определяет запись в **заказы** сущности. Если что заказ содержит строки один или несколько элементов, запись в **заказы** сущность, связанная с одной или нескольких записей в **Order details** сущности и данных этих записей отображается в коллекции сведений. Это отражает связи один ко многим, который был создан для вас между **заказы** и **Order Details** сущностей. Формулы, указанной «подробно» такую связь с помощью точечной нотации:

    > [!div class="mx-imgBorder"]
    > ![Один ко многим связь между сущностями заказы и сведения о заказе](media/northwind-orders-canvas-part3/schema-orders-rel.png)

## <a name="show-product-names"></a>Показать имена продуктов

1. В коллекции сведений, выберите **добавить элемент с вкладки «Вставка»** можно выбрать шаблон коллекции:

    > [!div class="mx-imgBorder"]
    > ![Выберите шаблон для коллекции данных](media/northwind-orders-canvas-part3/details-07.png)

    Убедитесь, что вы выбрали шаблон коллекции, а не самой галереи. Ограничивающий прямоугольник немного следует внутри границы коллекции и, скорее всего, меньше, чем высота галереи. Как вставлять элементы управления в этом шаблоне, они будут повторяться для каждого элемента в коллекции.

1. На **вставить** вкладке, Вставить метку в коллекции сведений.

    Метка должна отображаться в коллекции; Если это не так, повторите попытку, но не забудьте выбрать шаблон коллекции, перед вставкой метки.

    > [!div class="mx-imgBorder"]
    > ![Добавьте метку в коллекции сведений](media/northwind-orders-canvas-part3/details-08.png)

1. Задайте новые метки **текст** следующую формулу:

    ```powerapps-comma
    ThisItem.Product.'Product Name'
    ```

    Если текст не отображается, щелкните стрелку рядом с **0901 порядок** ближе к концу коллекции заказа.

1. Измените размер метки так, чтобы отображался весь текст:

    > [!div class="mx-imgBorder"]
    > ![Отображения имени продукта в сведения о заказе](media/northwind-orders-canvas-part3/details-09.png)

    Это выражение последовательно из записи в **Order Details** сущности. Запись хранится в **ThisItem** over к **заказ продуктов** сущности по связи многие к одному:

    > [!div class="mx-imgBorder"]
    > ![Многие к одному связь между сущностями сведения о заказе и продукта заказа](media/northwind-orders-canvas-part3/schema-orderdetails-rel.png)

    **Название продукта** извлекаются поля (и другие поля, которые вы собираетесь использовать):

    > [!div class="mx-imgBorder"]
    > ![Поля в сущности Заказ продуктов](media/northwind-orders-canvas-part3/schema-products-fields.png)

## <a name="show-product-images"></a>Отображение изображений продуктов

1. На **вставить** вкладке, вставить [ **изображение** ](controls/control-image.md) элемента управления в коллекции сведений:

    > [!div class="mx-imgBorder"]
    > ![Вставка элемента управления image](media/northwind-orders-canvas-part3/details-10.png)

1. Изменение размера и перемещение изображения и метки быть рядом друг с другом.

    > [!TIP]
    > Возможность точного управления размер и положение элемента управления начать изменение размера или перемещение не нажать клавишу Alt, а затем продолжить изменение размера или перемещение элемента управления, удерживая нажатой клавишу Alt:

    > [!div class="mx-imgBorder"]
    > ![Перемещение элемента управления image](media/northwind-orders-canvas-part3/details-11.png)

1. Задать изображение **изображение** следующую формулу:

    ```powerapps-comma
    ThisItem.Product.Picture
    ```

    Опять же, выражение ссылается на продукт, который связан с данным заказа детализации и извлечение **рисунок** поле для отображения.

    > [!div class="mx-imgBorder"]
    > ![Показать изображение продукта](media/northwind-orders-canvas-part3/details-12.png)

1. Уменьшить высота шаблона коллекции таким образом, больше, чем один **Order Detail** запись отображается за раз:

    > [!div class="mx-imgBorder"]
    > ![Сократите шаблона коллекции](media/northwind-orders-canvas-part3/details-13.png)

## <a name="show-product-quantity-and-cost"></a>Показать количество продукта и затрат

1. На **вставить** вкладке, вставить другую метку в коллекции сведений и изменение размера и переместить новую метку в правой части информации о продукте.

1. Задайте новые метки **текст** свойство следующее выражение:

    ```powerapps-comma
    ThisItem.Quantity
    ```

    Эта формула извлекает сведения о непосредственно из **Order Details** сущности (связи не требуется).

    > [!div class="mx-imgBorder"]
    > ![Показать количество продукта](media/northwind-orders-canvas-part3/details-13b.png) 

1. На **Главная** вкладке, изменить выравнивание этого элемента управления **справа**:

    > [!div class="mx-imgBorder"]
    > ![Изменение выравнивания](media/northwind-orders-canvas-part3/details-14.png)

1. На **вставить** вкладке, вставить другую метку в коллекции сведений и изменять размеры и переместите метку справа от метки quantity.

1. Задайте новые метки **текст** следующую формулу:

    ```powerapps-comma
    Text( ThisItem.'Unit Price'; "[$-en-US]$ #,###.00" )
    ```

    Если вы не включаете тег языка ( **[$-en US]** ), оно будет добавляться, который основан на язык и регион. Если вы используете тег другой язык, необходимо удалить **$** сразу после закрывающей квадратной ( **]** ), а затем добавить символ валюты в этой позиции.

    > [!div class="mx-imgBorder"]
    > ![Показать цена за единицу](media/northwind-orders-canvas-part3/details-15.png)

1. На **Главная** вкладке, изменить выравнивание этого элемента управления **справа**:

    > [!div class="mx-imgBorder"]
    > ![Изменение выравнивания](media/northwind-orders-canvas-part3/details-16.png)

1. На **вставить** вкладке, вставьте другой элемент управления label в коллекции сведений и изменение размера и переместить новую метку справа от цена за единицу.

1. Задайте новые метки **текст** следующую формулу:

    ```powerapps-comma
    Text( ThisItem.Quantity * ThisItem.'Unit Price'; "[$-en-US]$ #,###.00" )
    ```

    Опять же если вы не включаете тег языка ( **[$-en US]** ), оно будет добавляться, который основан на язык и регион. Если тег не совпадают, стоит использовать символ валюты вместо **$** сразу после закрывающей квадратной ( **]** ).

    > [!div class="mx-imgBorder"]
    > ![Показать наценок](media/northwind-orders-canvas-part3/details-17.png)

1. На **Главная** вкладке, изменить выравнивание этого элемента управления **справа**:

    > [!div class="mx-imgBorder"]
    > ![Изменение выравнивания](media/northwind-orders-canvas-part3/details-18.png)

    Теперь все готово Добавление элементов управления в коллекции сведений.

1. В **представление в виде дерева** области выберите **Screen1** чтобы убедиться, что сведения о коллекции больше не выбран.

## <a name="add-text-to-the-new-title-bar"></a>Добавьте текст в новый заголовок окна

1. На **вставить** вкладке, вставить другую метку на экране:

    > [!div class="mx-imgBorder"]
    > ![Вставить подпись](media/northwind-orders-canvas-part3/details-19.png)

1. Изменение размера и переместить новую метку выше изображения продуктов в строке заголовка второй измените цвет текста на белый на **Главная** вкладки.

1. Дважды щелкните текст метки, а затем введите **продукта**:

    > [!div class="mx-imgBorder"]
    > ![Измените текст надписи на продукт](media/northwind-orders-canvas-part3/details-20.png)

1. Скопируйте и вставьте метку продукта, изменение размера и переместить ее над столбцом quantity.

1. Дважды щелкните текст новую метку, а затем введите **количество**:

    > [!div class="mx-imgBorder"]
    > ![Измените текст надписи на количество](media/northwind-orders-canvas-part3/details-21.png)

1. Скопируйте и вставьте метку quantity, изменение размера и переместить ее над столбцом Цена за единицу.

1. Дважды щелкните текст новую метку, а затем введите **цена за единицу**:

    > [!div class="mx-imgBorder"]
    > ![Измените текст надписи на цена за единицу](media/northwind-orders-canvas-part3/details-22.png)

1. Скопируйте и вставьте метку цена за единицу, изменение размера и переместить ее над столбцом отпускная цена.

1. Дважды щелкните текст в новую метку, а затем введите **Extended**:

    > [!div class="mx-imgBorder"]
    > ![Измените текст надписи на расширенный](media/northwind-orders-canvas-part3/details-23.png)

## <a name="display-order-totals"></a>Отображать итоги заказа

1. Уменьшите высоту коллекции сведений, чтобы освободить место для итоги заказов в нижней части экрана:

    > [!div class="mx-imgBorder"]
    > ![Сократите коллекции сведения о заказе](media/northwind-orders-canvas-part3/sum-01.png)

1. Скопируйте и вставьте строку заголовка в центре экрана и переместите ее в нижней части экрана:

    > [!div class="mx-imgBorder"]
    > ![Копирование строки заголовка и перемещение копирования по нижнему краю](media/northwind-orders-canvas-part3/sum-02.png)

1. Скопируйте и вставьте метку продукта из средней заголовка и затем переместить ее в строку заголовка снизу, слева от **количество** столбца.

1. Дважды щелкните текст новую метку и введите следующий текст:<br>**Итоги заказа:**

    > [!div class="mx-imgBorder"]
    > ![Добавить метку для итоги заказа](media/northwind-orders-canvas-part3/sum-03.png)

1. Скопируйте и вставьте метку итоги заказа, изменение размера и переместить ее справа от метки итоги заказа.

1. Задайте новые метки **текст** следующую формулу:

    ```powerapps-comma
    Sum( Gallery1.Selected.'Order Details'; Quantity )
    ```

    Эта формула показано предупреждение делегирования, но его можно пропустить, поскольку нет одного заказа будет содержать более 500 программных продуктов.

1. На **Главная** вкладку, задайте новую метку выравнивание текста **справа**:

    > [!div class="mx-imgBorder"]
    > ![Изменение выравнивания](media/northwind-orders-canvas-part3/sum-04.png)

1. Скопируйте и вставьте этот элемент управления label и изменение размера и переместить ее в разделе **Extended** столбца.

1. Переключите копию **текст** следующую формулу:

    ```powerapps-comma
    Text( Sum( Gallery1.Selected.'Order Details'; Quantity * 'Unit Price' ); "[$-en-US]$ #,###.00" )
    ```

    Эта формула показано предупреждение делегирования, но его можно пропустить, поскольку нет одного заказа будет содержать более 500 программных продуктов.

    > [!div class="mx-imgBorder"]
    > ![Показать общую стоимость заказа](media/northwind-orders-canvas-part3/sum-05.png)

## <a name="add-space-for-new-details"></a>Добавить место для новых данных

В любой коллекции можно показать данные, но не удается обновить его или добавить записи. В коллекции сведений, вы добавите область, где пользователь может настроить запись в **Order Details** сущности и вставки, записи в заказ.

1. Уменьшите высоту коллекции сведений достаточно, чтобы освободить место для отдельного элемента ввода редактирования в этой коллекции.

    В этой области вы добавите элементы управления, чтобы пользователь мог Добавить подробности заказа:

    > [!div class="mx-imgBorder"]
    > ![Сократите коллекции данных](media/northwind-orders-canvas-part3/add-details-01.png)

1. На **вставить** вкладке, Вставить метку и изменение размера и переместить его в коллекции сведений.

    > [!div class="mx-imgBorder"]
    > ![Добавить метку](media/northwind-orders-canvas-part3/add-details-02.png)

1. Дважды щелкните текст в новую метку и нажмите клавишу Delete.

1. На **Главная** вкладку, задайте новые метки **заполнения** цвет **LightBlue**:

    > [!div class="mx-imgBorder"]
    > ![Изменение заливки метки в светло-синий](media/northwind-orders-canvas-part3/add-details-03.png)

## <a name="add-the-order-details-data-source"></a>Добавление источника данных сведения о заказе

1. На **представление** выберите **источников данных**, а затем выберите **добавить источник данных** в **данных** области:

    > [!div class="mx-imgBorder"]
    > ![Добавление источника данных](media/northwind-orders-canvas-part3/add-details-04.png)

1. Выберите **Common Data Service**:

    > [!div class="mx-imgBorder"]
    > ![Выберите Common Data Service](media/northwind-orders-canvas-part3/add-details-05.png)

1. В верхней части **данных** введите **порядок** в поле поиска, выберите **Order Details** флажок, а затем выберите **Connect** в внизу панели:

    > [!div class="mx-imgBorder"]
    > ![Укажите сведения о сущности Order](media/northwind-orders-canvas-part3/add-details-06.png)

    Вы только что добавили другого источника данных в приложение:

    > [!div class="mx-imgBorder"]
    > ![Список источников данных](media/northwind-orders-canvas-part3/add-details-07.png)

    Необходимо добавить этот источник данных, поскольку, несмотря на то, что приложение может считывать посредством отношения один ко многим, приложение не может еще обратной записи изменения. Приложение необходимо внести изменения непосредственно с помощью связанной сущности.

1. Закрыть **данных** области.

## <a name="select-a-product"></a>Выберите продукт

1. На **вставить** выберите **элементов управления** > **поле со списком**:

    > [!div class="mx-imgBorder"]
    > ![Вставить поле со списком](media/northwind-orders-canvas-part3/add-details-08.png)

    [ **Поле со списком** ](controls/control-combo-box.md) элемент управления отображается в левом верхнем углу.

1. Задать поле со списком **элементы** следующую формулу:

    ```powerapps-comma
    Choices( 'Order Details'.Product )
    ```

    > [!div class="mx-imgBorder"]
    > ![Задайте свойство Items Бокса поля со списком](media/northwind-orders-canvas-part3/add-details-09.png)

    [ **Варианты** ](functions/function-choices.md) функция возвращает таблицу всех возможных значений для **продукта** в **Order Details** сущности. Это поле является уточняющего запроса в отношении "многие к одному", так что **варианты** возвращает все записи в **заказ продуктов** сущности.

    > [!NOTE]
    > Можно также использовать **варианты** с наборы параметров, чтобы вернуть таблицу для всех параметров. Действия не упомянул этот подход, но использовалась уже в том случае, когда вы добавили поле со списком, который показывает **состояние заказа** в сводной форме.

1. В **данных** открытой областью **основной текст** , а затем выберите **nwind_productname**. 

1. Откройте **SearchField** , а затем выберите **nwind_productname**.

    Укажите логическое имя, так как **данных** области пока не поддерживает отображаемые имена в нашем примере:

    > [!div class="mx-imgBorder"]
    > ![Задает основной текст для поля со списком](media/northwind-orders-canvas-part3/add-details-10.png)

1. Закрыть **данных** области.

1. В **свойства** вкладке рядом с правым краем, прокрутите вниз, снимите соответствующий флажок **разрешить выбор нескольких элементов**и убедитесь, что **разрешить поиск** включен:

    > [!div class="mx-imgBorder"]
    > ![Отключить выбор нескольких элементов и поиска](media/northwind-orders-canvas-part3/add-details-12.png)

1. Изменение размера и переместить поле со списком голубой, просто в столбце Имя продукта в коллекции сведений:

    > [!div class="mx-imgBorder"]
    > ![Переместить поле со списком](media/northwind-orders-canvas-part3/add-details-13.png)

    В этом поле со списком пользователь укажет записи в **продукта** сущность для **Order Details** запись, которая создаст приложение.

1. Удерживая нажатой клавишу Alt, выберите стрелку вниз в поле со списком.

    > [!TIP]
    > Удерживая нажатой клавишу Alt, вы можете взаимодействовать с элементами управления в PowerApps Studio без открытия в режиме предварительного просмотра.

1. В открывшемся списке продуктов выберите продукт:

    > [!div class="mx-imgBorder"]
    > ![Выберите продукт в поле со списком](media/northwind-orders-canvas-part3/add-details-14.png)

## <a name="add-a-product-image"></a>Добавить изображение продукта

1. На **вставить** выберите **мультимедиа** > **изображение**:

    > [!div class="mx-imgBorder"]
    > ![Вставка элемента управления image](media/northwind-orders-canvas-part3/add-details-15.png)

    [ **Изображение** ](controls/control-image.md) элемент управления отображается в левом верхнем углу:

    > [!div class="mx-imgBorder"]
    > ![Расположение по умолчанию элемента управления изображения](media/northwind-orders-canvas-part3/add-details-16.png)

1. Изменение размера изображения или переместите его в область голубой под другие изображения товаров и рядом с полем со списком.

1. Задайте **изображение** свойство изображения:

    ```powerapps-comma
    ComboBox1.Selected.Picture
    ```

    > [!div class="mx-imgBorder"]
    > ![Задайте для свойства изображения образа](media/northwind-orders-canvas-part3/add-details-17.png)

    Же прием используется в качестве вы использовали для отображения в форме сводки изображение сотрудника. **Выбранные** поле со списком возвращает всю запись, независимо от продукта, пользователь выбирает, включая **рисунок** поля.

## <a name="add-a-quantity-box"></a>Окно количества

1. На **вставить** выберите **текст** > **ввода текста**:

    > [!div class="mx-imgBorder"]
    > ![Добавить поле для ввода текста](media/northwind-orders-canvas-part3/add-details-18.png)

    [ **Ввода текста** ](controls/control-text-input.md) элемент управления отображается в левом верхнем углу:

    > [!div class="mx-imgBorder"]
    > ![Расположение по умолчанию поле для ввода текста](media/northwind-orders-canvas-part3/add-details-19.png)

1. Изменение размера и переместить поле ввода текста справа от поля со списком, в столбце "Количество" в коллекции сведений:

    > [!div class="mx-imgBorder"]
    > ![Измените размер или переместите поле для ввода текста](media/northwind-orders-canvas-part3/add-details-20.png)

    В этом окне текстовое поле, пользователь укажет **количество** поле **Order Details** записи.

1. Задайте **по умолчанию** свойства этого элемента управления **«»** :

    > [!div class="mx-imgBorder"]
    > ![Задайте ** свойство по умолчанию ** в поля ввода текста](media/northwind-orders-canvas-part3/add-details-21.png)

1. На **Главная** вкладке, задать выравнивание текста этого элемента управления **справа**:

    > [!div class="mx-imgBorder"]
    > ![Изменение выравнивания](media/northwind-orders-canvas-part3/add-details-22.png)

## <a name="show-the-unit-and-extended-prices"></a>Показывать единицы и отпускная цена

1. На **вставить** вкладке, вставить **метка** элемента управления.

    Метка отображается в левом верхнем углу экрана:

    > [!div class="mx-imgBorder"]
    > ![Добавить метку](media/northwind-orders-canvas-part3/add-details-23.png)

1. Изменение размера и переместить метки справа от элемента управления для ввода текста, а также задавать метки **текст** следующую формулу:

    ```powerapps-comma
    Text( ComboBox1.Selected.'List Price'; "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![Задайте для свойства Text метки](media/northwind-orders-canvas-part3/add-details-24.png)

    Этот элемент управления отображает **по прейскуранту** из **заказ продуктов** сущности. Это значение будет определять **цена за единицу** в **Order Details** записи.

    > [!NOTE]
    > В этом сценарии значение доступно только для чтения, но может вызывать другие сценарии для пользователя приложения для его изменения. В этом случае использовать **ввода текста** и задать его **по умолчанию** свойства **по прейскуранту**.

1. На **Главная** вкладке, задать выравнивание текста метки по прейскуранту **справа**:

    > [!div class="mx-imgBorder"]
    > ![Изменение выравнивания](media/northwind-orders-canvas-part3/add-details-25.png)

1. Скопируйте и вставьте прейскуранту метку, изменение размера и переместить ее справа от метки по прейскуранту.

1. Задайте новые метки **текст** следующую формулу:

    ```powerapps-comma
    Text( Value(TextInput1.Text) * ComboBox1.Selected.'List Price'; "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![Задайте для свойства Text новую метку](media/northwind-orders-canvas-part3/add-details-27.png)

    Этот элемент управления отображает расширенная цена на основе количества, указанное пользователем приложения и по прейскуранту продукта, выбранного пользователем приложения. Это исключительно для информационных целей для пользователя приложения.

1. Дважды щелкните элемент управления "текстовое поле" количество, а затем введите число.

    **Extended** метка цена пересчитывает Показать новое значение:

    > [!div class="mx-imgBorder"]
    > ![Укажите количество и Показать наценок](media/northwind-orders-canvas-part3/add-details-28.png)

## <a name="add-an-add-icon"></a>Добавить значок Add

1. На **вставить** выберите **значки** > **добавить**:

    > [!div class="mx-imgBorder"]
    > ![Добавить значок INSERT](media/northwind-orders-canvas-part3/add-details-29.png)

    Значок отображается в левом верхнем углу экрана.

    > [!div class="mx-imgBorder"]
    > ![Расположение по умолчанию значок добавления](media/northwind-orders-canvas-part3/add-details-30.png)

1. Изменение размера и перемещение по правому краю области голубой этот значок и задайте значок **OnSelect** следующую формулу:

    ```powerapps-comma
    Patch( 'Order Details';
        Defaults('Order Details');
        {
            Order: Gallery1.Selected;
            Product: ComboBox1.Selected;
            Quantity: Value(TextInput1.Text);
            'Unit Price': ComboBox1.Selected.'List Price'
        }
    );;
    Refresh( Orders );;
    Reset( ComboBox1 );;
    Reset( TextInput1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![Значок для свойства OnSelect](media/northwind-orders-canvas-part3/add-details-31.png)

    В общем случае [ **Patch** ](functions/function-patch.md) функция обновляет и создает записи и определенные аргументы в этой формуле определить конкретные изменения, чтобы сделать функцию.

    - Первый аргумент указывает источник данных (в этом случае **Order Details** сущности) в которой функция будет обновить или создать запись.
    - Второй аргумент указывает, что функция будет создавать запись со значениями по умолчанию для **Order Details** сущности, если не указано в качестве третьего аргумента.
    - Третий аргумент указывает, что четыре столбца в новой записи будут содержать значения от пользователя.

      - **Порядок** столбец будет содержать номер заказа, что пользователь выбрал в коллекции в порядке.
      - **Продукта** столбец будет содержать имя продукта, что пользователь, выбранный в поле со списком, который отображаются продукты.
      - **Количество** столбец будет содержать значение, которое пользователь указал в поле ввода текста.
      - **Цена за единицу** столбец будет содержать по прейскуранту продукта, который пользователь выбрал для этого сведения о заказе.

    > [!NOTE]
    > Вы можете создавать формулы, использующие данные из любого столбца (в **заказ продуктов** сущностей) для любого продукта приложения пользователь выбирает в поле со списком, отображаются продукты. Когда пользователь выбирает запись в **заказ продуктов** сущность, не только название продукта, отображаются в этом поле со списком, но также продукты, цена отображается в метке. Каждое значение поиска в приложение на основе холста ссылается на всю запись, не только первичный ключ.

    **Обновить** функция гарантирует, что **заказы** сущности отражает запись, которую вы только что добавили к **Order Details** сущности. **Сброс** функция очищает продукта, количество и цена за единицу данных, таким образом, чтобы пользователь могут более просто создавать другой подробности заказа для том же порядке.

1. Нажмите клавишу F5, а затем выберите **добавить** значок.

    Порядок отражает сведения, которые вы указали:

    > [!div class="mx-imgBorder"]
    > ![Анимация для добавления заказа](media/northwind-orders-canvas-part3/add-details.gif)

1. (необязательно) Добавление другого элемента в заказ.

1. Нажмите клавишу Esc, чтобы закрыть режим предварительного просмотра.

## <a name="remove-an-order-detail"></a>Удалить деталь заказа

1. В центральной части экрана выберите шаблон из коллекции сведений:

    > [!div class="mx-imgBorder"]
    > ![Выберите шаблон коллекции](media/northwind-orders-canvas-part3/remove-details-01.png)

1. На **вставить** выберите **значки** > **корзины**:

    > [!div class="mx-imgBorder"]
    > ![Вставьте значок корзины](media/northwind-orders-canvas-part3/remove-details-02.png)

    В левом верхнем углу шаблона коллекции появится значок корзины.

    > [!div class="mx-imgBorder"]
    > ![Расположение по умолчанию значок](media/northwind-orders-canvas-part3/remove-details-03.png)

1. Изменение размера и переместить значок корзины в правой части шаблона коллекции данных, а также задавать значок **OnSelect** следующую формулу:

    ```powerapps-comma
    Remove( 'Order Details'; ThisItem );; Refresh( Orders )
    ```

    > [!div class="mx-imgBorder"]
    > ![Значок для свойства OnSelect](media/northwind-orders-canvas-part3/remove-details-04.png)

    На момент написания этой статьи, не удается удалить запись непосредственно из связи, поэтому [ **удалить** ](functions/function-remove-removeif.md) функция удаляет запись непосредственно из связанной сущности. **ThisItem** указывает запись для удаления, взятое из одной и той же записи в коллекции сведений, где отображается значок корзины.

    Опять же, операция использует кэшированные данные, поэтому **обновить** функция сообщает **заказы** сущности, что это приложение был изменен связанные с ней сущности.

1. Нажмите клавишу F5, чтобы откройте режим предварительного просмотра, а затем выберите значок корзины рядом с каждым **Order Details** записи, который требуется удалить из него.

1. Попробуйте добавить и удалить различные сведения о заказе из заказов:

    > [!div class="mx-imgBorder"]
    > ![Анимация для добавления и удаления сведений о заказе](media/northwind-orders-canvas-part3/remove-details.gif)

## <a name="in-conclusion"></a>В заключение

Формулируя кратко, вы добавили другой коллекции, чтобы отобразить сведения о заказе и элементы управления, добавление и удаление подробности заказа в приложении. Вы использовали эти элементы:

- Второй элемент управления галереи, связано с коллекции порядке через отношение один ко многим: **Gallery2.Items** = `Gallery1.Selected.'Order Details'`
- Отношение "многие к одному" с **Order Details** сущность **заказ продуктов** сущности: `ThisItem.Product.'Product Name'` и `ThisItem.Product.Picture`
- **Варианты** функцию для получения списка продуктов: `Choices( 'Order Details'.Product' )`
- **Выбранные** свойства поля со списком как полный многие к одному связанные записи: `ComboBox1.Selected.Picture` и `ComboBox1.Selected.'List Price'`
- **Patch** функцию для создания **Order Details** записи: `Patch( 'Order Details'; Defaults( 'Order Details' ); ... )`
- **Удалить** функции, чтобы удалить **Order Details** записи: `Remove( 'Order Details'; ThisItem )`

Этой серии документов была краткое описание с помощью связей Common Data Service и параметр задает в приложение на основе холста в образовательных целях. Перед выпуском любого приложения в рабочей среде, следует, что проверка полей, обработка ошибок и множество других факторов.