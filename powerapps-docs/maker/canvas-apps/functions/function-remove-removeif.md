---
title: Функции Remove и RemoveIf | Документация Майкрософт
description: Справочные сведения, включая синтаксис и примеры, для функций Remove и Ремовеиф в Power Apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/02/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: bddce14842d111757859b836c0137b35111805d1
ms.sourcegitcommit: 49b69129262a9b530e69508e84c3822b742066df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/07/2020
ms.locfileid: "80759841"
ms.PowerAppsDecimalTransform: true
---
# <a name="remove-and-removeif-functions-in-power-apps"></a>Удаление и Ремовеиф функций в Power Apps
Удаляют [записи](../working-with-tables.md#records) из [источника данных](../working-with-data-sources.md).

## <a name="description"></a>Описание
### <a name="remove-function"></a>Функция Remove
С помощью функции **Remove** можно удалить из источника данных определенную запись или набор записей.  

Для [коллекций](../working-with-data-sources.md#collections) должна совпадать вся запись. Удалить все копии записи можно с помощью аргумента **All**; в противном случае удаляется только одна копия.

### <a name="removeif-function"></a>Функция RemoveIf
С помощью функции **RemoveIf** можно удалить одну или несколько записей на основе определенного условия или набора условий. Каждое из этих условий может быть любой формулой, которая возвращает результат **true** (истина) или **false** (ложь), и может содержать ссылки на [столбцы](../working-with-tables.md#columns) источника данных (по имени). Каждое условие оценивается отдельно для каждой записи, и запись удаляется, если все условия возвращают значение **true**.

Функции **Remove** и **RemoveIf** возвращают измененный источник данных в виде [таблицы](../working-with-tables.md). Обе эти функции можно использовать только в [формулах поведения](../working-with-formulas-in-depth.md).

Кроме того, удалить все записи из источника данных можно с помощью функции **[Clear](function-clear-collect-clearcollect.md)** .

### <a name="delegation"></a>Делегирование
[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>Синтаксис
**Remove**(*источник_данных*; *запись_1*[; *запись_2*; ... ] [; **All**])

* *источник_данных* — обязательный аргумент. Это источник данных, содержащий запись или записи, которые требуется удалить.
* *запись(_n)*  — обязательный аргумент. Запись или записи, которые требуется удалить.
* **All** — необязательный аргумент. В коллекции может существовать несколько копий одной записи.  С помощью аргумента **All** можно удалить их все.

**Remove**(*источник_данных*; *таблица*[; **All**])

* *источник_данных* — обязательный аргумент. Это источник данных, содержащий записи, которые требуется удалить.
* *таблица* — обязательный аргумент. Таблица с записями, которые требуется удалить.
* **All** — необязательный аргумент. В коллекции может существовать несколько копий одной записи.  С помощью аргумента **All** можно удалить их все.

**RemoveIf**(*источник_данных*; *условие*[; ... ])

* *источник_данных* — обязательный аргумент. Это источник данных, содержащий запись или записи, которые требуется удалить.
* *Condition(s)*  — обязательный аргумент. Формула, возвращающая значение **true** (истина) для записи или записей, которые требуется удалить.  В формуле можно использовать названия столбцов из *источника_данных*.  Если указано несколько *условий*, для удаления соответствующей записи все они должны возвращать значение **true**.

## <a name="examples---single-formulas"></a>Примеры — отдельные формулы

В этих примерах выполняется удаление записи или записей из источника данных под названием **IceCream**, начинающегося со значений из следующей таблицы:

![](media/function-remove-removeif/icecream.png)

#### <a name="create-a-collection-with-sample-records"></a>Создание коллекции с примерами записей

Чтобы создать коллекцию с этими данными, выполните следующие действия.

1. Вставка элемента управления [ **"Кнопка"** ](../controls/control-button.md) .
1. Задайте для свойства **OnSelect** элемента управления Button следующую формулу:

    ```powerapps-comma
    ClearCollect( IceCream;
                  { ID: 1; Flavor: "Chocolate";  Quantity: 100 };
                  { ID: 2; Flavor: "Vanilla";    Quantity: 200 };
                  { ID: 3; Flavor: "Strawberry"; Quantity: 300 }
    )
    ```
1. Нажмите кнопку, [удерживая клавишу Alt](../keyboard-shortcuts.md#alternate-behavior):


#### <a name="remove-sample-records-from-collection-using-a-formula"></a>Удаление образцов записей из коллекции с помощью формулы

| Формула | Описание | Возвращаемый результат |
| --- | --- | --- |
| **Remove(&nbsp;IceCream;<br>First(&nbsp;Filter(&nbsp;IceCream;&nbsp;Flavor="Chocolate"&nbsp;)&nbsp;))** |Удаляет из источника данных запись **Chocolate**. |<style>img {max-width: None}</style> ![](media/function-remove-removeif/icecream-no-chocolate.png)<br><br>Источник данных **IceCream** изменен. |
| **Remove(&nbsp;IceCream;<br>First(&nbsp;Filter(&nbsp;IceCream;&nbsp;Flavor="Chocolate"&nbsp;)&nbsp;) First(&nbsp;Filter(&nbsp;IceCream;&nbsp;Flavor="Strawberry"&nbsp;)&nbsp;))** |Удаляет из источника данных две записи. |![](media/function-remove-removeif/icecream-only-vanilla.png)<br><br>Источник данных **IceCream** изменен. |
| **RemoveIf(&nbsp;IceCream; Quantity&nbsp;>&nbsp;150)** |Удаляет записи со значением **Quantity** больше **150**. |![](media/function-remove-removeif/icecream-only-chocolate.png)<br><br>Источник данных **IceCream** изменен. |
| **RemoveIf(&nbsp;IceCream; Quantity&nbsp;>&nbsp;150; Left(&nbsp;Flavor;&nbsp;1&nbsp;) = "S")** |Удаляет записи со значением **Quantity** больше 150 и значением **Flavor**, начинающимся с буквы **S**. |![](media/function-remove-removeif/icecream-no-strawberry.png)<br><br><br>Источник данных **IceCream** изменен. |
| **RemoveIf(&nbsp;IceCream; true)** |Удаляет из источника данных все записи. |![](media/function-remove-removeif/icecream-empty.png)<br><br>Источник данных **IceCream** изменен. |

## <a name="examples---remove-button-outside-a-gallery"></a>Примеры. Удаление кнопки за пределами коллекции

В этом примере для вывода списка записей в таблице используется [элемент управления " **коллекция** ](../controls/control-gallery.md) ". А затем используйте функцию **Remove** для выборочного удаления элемента.  

### <a name="prepare-for-sample-data"></a>Подготовка к примерам данных

В этом примере используется сущность **Contacts** в Common Data Service, доступная в *примерах приложений и данных*. Вы можете развернуть *примеры приложений и данные* при [создании среды](https://docs.microsoft.com/power-platform/admin/create-environment#create-an-environment-with-a-database). Кроме того, можно использовать любой другой источник данных.

### <a name="remove-button-outside-a-gallery"></a>Удалить кнопку за пределами коллекции

В этом примере элемент удаляется с помощью *кнопки* , находящегося за пределами коллекции.

1. Создание [нового приложения пустого холста](../data-platform-create-app-scratch.md) с помощью макета для телефона.

    ![Пустое приложение Canvas с использованием макета телефона](media/function-remove-removeif/gallery-new.png)

1. Выберите **вставку** в левой области.

1. Выбрать **вертикальную галерею**. <br>
    На экран будет добавлен элемент управления " **Галерея** ".

    ![Использование панели инструментов «вставка» для добавления вертикального элемента управления «коллекция»](media/function-remove-removeif/gallery-add.png)

1. Вам будет предложено выбрать источник данных, в котором можно выбрать источник данных из доступных источников данных. <br>
    Например, выберите сущность **Контакты** для использования *образца данных*:  

    ![Выбор сущности "Контакты" для показа в коллекции](media/function-remove-removeif/gallery-datasource.png)

    В галерее показаны элементы из этой сущности: 

    ![Добавленная коллекция с сущностью "Контакты"](media/function-remove-removeif/gallery-data.png)

1. Вставка элемента управления [ **"Кнопка"** ](../controls/control-button.md) из левой панели:
    
    ![Добавление элемента управления "Кнопка" с помощью панели инструментов "Вставка"](media/function-remove-removeif/gallery-addbutton.png)

1. Переместите добавленную кнопку под элементами коллекции:

    ![Кнопка "Переместить"](media/function-remove-removeif/move-button-down.png)

1. Обновите свойство текста кнопки, чтобы *Удалить запись*. Можно также использовать текст по своему усмотрению:

    ![Кнопка "Переименовать"](media/function-remove-removeif/button-text.png)

1. Установите для этого элемента управления "Кнопка" свойство **OnSelect** со следующей формулой:

    ```powerapps-comma
    Remove( Contacts; Gallery1.Selected )
    ```

    ![Задание свойства OnSelect элемента управления Button](media/function-remove-removeif/gallery-button-onselect.png)

    Элемент управления "Коллекция" делает выбранную запись доступной с помощью **выбранного** свойства. Функция **Remove** ссылается на эту выбранную запись, чтобы удалить ее.

1. Просмотрите приложение с помощью кнопки *воспроизведения* в правом верхнем углу или нажмите клавишу *F5* на клавиатуре:

    ![Предварительная версия приложения](media/function-remove-removeif/preview-app.png)

1. Выберите удаляемую запись, например запись *Нэнси*в этом примере:

    ![Выбор записи](media/function-remove-removeif/select-nancy-record.png)

1. Выберите **Удалить запись**:

    ![Коллекция контактов теперь без записи Нэнси, которая была удалена](media/function-remove-removeif/gallery-activatebutton.png)

    При нажатии кнопки удаляется выбранная запись (в этом примере запись Нэнси).

1. Закройте предварительную версию приложения.

    > [!TIP]
    > Можно также использовать альтернативное поведение с клавишей [*ALT*](../keyboard-shortcuts.md#alternate-behavior) , а не использовать предварительный просмотр приложения с кнопкой *воспроизвести* или *клавишу F5*.

## <a name="examples---trash-can-icon-inside-a-gallery"></a>Примеры для значка корзины в галерее

В этом примере элемент удаляется с помощью *значка* , помещенного в коллекцию.

### <a name="create-a-collection-with-sample-data"></a>Создание коллекции с демонстрационными данными

Если вы уже [подготовили демонстрационные данные](#prepare-for-sample-data), пропустите этот шаг и переместитесь в корзину, чтобы [получить значок в галерее](#trash-can-icon-inside-a-gallery).

1. Добавьте на экран элемент управления [ **"Кнопка"** ](../controls/control-button.md) .
1. Задайте для свойства **OnSelect** следующую формулу:

    ```powerapps-comma
    ClearCollect( SampleContacts; 
          { 'Full Name': "Yvonne McKay (sample)";      'Primary Email': "someone_a@example.com" };
          { 'Full Name': "Susanna Stubberod (sample)"; 'Primary Email': "someone_b@example.com" };
          { 'Full Name': "Nancy Anderson (sample)";    'Primary Email': "someone_c@example.com" };
          { 'Full Name': "Maria Campbell (sample)";    'Primary Email': "someone_d@example.com" };
          { 'Full Name': "Robert Lyon (sample)";       'Primary Email': "someone_e@example.com" };
          { 'Full Name': "Paul Cannon (sample)";       'Primary Email': "someone_f@example.com" };
          { 'Full Name': "Rene Valdes (sample)";       'Primary Email': "someone_g@example.com" } 
    )
    ```
1. Нажмите кнопку, [удерживая](../keyboard-shortcuts.md#alternate-behavior)клавишу ALT.

Будет создан образец коллекции, который можно использовать в следующем примере.

### <a name="trash-can-icon-inside-a-gallery"></a>Значок корзины в галерее

1. Создание [нового приложения пустого холста](../data-platform-create-app-scratch.md) с помощью макета для телефона.

    ![Пустое приложение Canvas с использованием макета телефона](media/function-remove-removeif/gallery-new.png)

1. Выберите **вставку** в левой области.

1. Выбрать **вертикальную галерею**. <br>
    На экран будет добавлен элемент управления " **Галерея** ".

    ![Использование панели инструментов «вставка» для добавления вертикального элемента управления «коллекция»](media/function-remove-removeif/gallery-add.png)

1. Вам будет предложено выбрать источник данных, в котором можно выбрать источник данных из доступных источников данных. <br>
    Например, выберите сущность **Контакты** для использования *образца данных*:  

    ![Выбор сущности "Контакты" для показа в коллекции](media/function-remove-removeif/gallery-datasource.png)

    Если вы создали [коллекцию](#create-a-collection-with-sample-data), выберите свою коллекцию:

    ![Пример коллекции контактов](media/function-remove-removeif/sample-contacts.png)

1. Выберите элемент управления в верхнем элементе коллекции. <br>
    
    Чтобы следующий шаг вставил элемент в шаблон коллекции, а не вне коллекции, обязательно выполните этот шаг, прежде чем переходить к следующему шагу.
    
    ![Выбор верхней записи в коллекции](media/function-remove-removeif/gallery-select-template.png)

1. Выберите **Добавить значок** из левой панели. <br>
    
    ![Добавление элемента управления "значок" с помощью панели инструментов "Вставка"](media/function-remove-removeif/gallery-addicon.png)

    > [!NOTE]
    > **Значок "добавить** " вставляет значок **+** в левой части коллекции, реплицированный для каждого элемента в коллекции. 

1. В верхнем элементе переместите значок на правую часть экрана.

    ![Значок «Переместить»](media/function-remove-removeif/move-icon.png)

1. Выберите свойство **значок** для значка и задайте для него следующую формулу, чтобы обновить изображение значка корзины:

    ```powerapps-comma 
    Icon.Trash
    ```
    
    > [!NOTE]
    > **Значок.** префикс отображается только при активном редактировании формулы.

    ![Изменение значка на значок корзины](media/function-remove-removeif/gallery-icontrash.png)

1. Задайте для свойства **OnSelect** следующую формулу:

    ```powerapps-comma
    Remove( [@Contacts]; ThisItem )
    ```

    > [!NOTE]
    > Необходимо использовать [глобальный оператор устранения неоднозначности](operators.md#disambiguation-operator) **[@** ... **]** в этом примере с образцами данных, которые используют сущность *Contacts* во избежание конфликта со связью *«один ко многим* ». При использовании таких источников данных, как список SharePoint или SQL Serverная таблица, использование *глобального оператора дисамбгулатион* не требуется.

    ![OnSelect для значка корзины](media/function-remove-removeif/gallery-onselect.png)

1. Просмотрите приложение с помощью кнопки *воспроизведения* в правом верхнем углу или нажмите клавишу *F5* на клавиатуре.

1. Щелкните значок корзины рядом с записью, например *Мария*:

    ![Коллекция с одним из удаленных контактов](media/function-remove-removeif/gallery-activateicon.png)

    Запись удалена:

    ![Удаленная запись](media/function-remove-removeif/deleted-record.png)

1. Закройте предварительную версию приложения.
