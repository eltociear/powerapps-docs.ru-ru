---
title: Создание компонента для приложений на основе холста | Документация Майкрософт
description: Введение в повторно используемые компоненты для приложений на основе холста
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 12/12/2018
ms.author: yifwang
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 369304ded3fdc9fcd69459da9875e6080d5d860c
ms.sourcegitcommit: 2e2cfbaa29cbfdbe48bd5563e65edcfc57a69b9d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2019
ms.locfileid: "57989641"
---
# <a name="create-a-component-for-canvas-apps"></a>Создание компонента для приложений на основе холста

> [!IMPORTANT]
> Эта функция по-прежнему экспериментальных и отключен по умолчанию. Дополнительные сведения см. в разделе [экспериментальные и предварительной версий](working-with-experimental.md).

Компоненты являются повторно используемых стандартных блоков для приложений на основе холста, чтобы разработчики приложений могут создавать пользовательские элементы управления для использования в приложении или в приложениях. Дополнительные функции, например пользовательские свойства использовать сложные возможности компонентов. В этой статье рассматриваются основные понятия компонента и некоторые примеры.

Компоненты полезны при создании больших приложений, которые имеют похожие шаблоны элемента управления. Если вы обновляете Определение компонента, все экземпляры в приложении соответствии с внесенными изменениями. Можно также повысить производительность с помощью одного или нескольких компонентов, так как не копировании и вставке элементов управления, который дублирует издержки. Компоненты также способствует совместной разработки и стандартизирует внешний вид и поведение в организации.

## <a name="prerequisite"></a>Необходимое условие

Откройте **параметры приложения** выберите **Дополнительные параметры**и включить функцию, а также убедиться, что **отрисовки приложения Improved** включена.

## <a name="component-canvas"></a>Компонент canvas

Можно создать компонент из **компоненты** меню **вставить** вкладку или, как показано далее графики, на панели навигации слева. Этот список содержит компоненты, заданные в приложении, отсортированных по дате создания.

![Представление списка компонентов](./media/create-component/list-view.png)

Независимо от выбранного подхода появится пустой холст, где можно добавить элементы управления как часть определения компонента. При редактировании компонента на холсте, обновите экземпляры одного компонента в других экранов приложения и другие приложения.

Если выбран экран, можно выбрать компонент из списка существующих компонентов в левой панели навигации или **компоненты** меню **вставить** вкладку. При выборе компонента вставке экземпляра этого компонента к экрану, так же, как Вставка элемента управления.

## <a name="scope"></a>Область действия

Считать компонент инкапсулированный черного прямоугольника со свойствами как интерфейс. При отсутствии доступа к элементам управления в компоненте за пределами компонента и не может ссылаться на что-либо за пределами компонента из внутри компонента. Если вы попытаетесь, отображается сообщение об ошибке. Ограничения области контракт данных компонента простой и единообразный, а он помогает обеспечить простой компонент-обновлений, особенно в приложениях. Контракт данных компонента можно обновить, создав один или несколько пользовательских свойств.

## <a name="variables"></a>Переменные

Компоненты не поддерживают **UpdateContext** функция, но можно создать и обновить с помощью переменных в компоненте **задать** функции. Область этих переменных ограничена компонента, но они будут доступны из вне компонента, используя настраиваемые выходные данные свойства.

## <a name="import-and-export"></a>Импорт и экспорт

Если вы экспортируете компонента, создается локальный файл, который можно импортировать в другое приложение. Если приложение содержит измененную версию того же компонента, будет предложено решить, следует ли заменить измененной версии или Отмена импорта. На момент написания этой статьи невозможно сохранить компонентов в облаке или совместно использовать их в этой среде.

![Импорт и экспорт](./media/create-component/import.png)

## <a name="custom-properties"></a>Пользовательские свойства

Компонент может получать входные значения и передачи данных в том случае, если вы создаете один или несколько пользовательских свойств. Эти сценарии являются расширенными и требуют представления о формулах и контракты.

Входного свойства — как компонент получает данные для использования в компоненте. Входные свойства отображаются в **свойства** вкладку на панели справа, если установлен экземпляр компонента. Можно настроить входные свойства с выражениями или формулы, так же, как настроить стандартные свойства в других элементах управления. Другие элементы управления входные свойства, такие как **по умолчанию** свойство **ввода текста** элемента управления.

Выходные свойства может выдавать состояние данных или компонента. Например **выбранные** свойство **коллекции** элемент управления является свойством вывода. При создании выходного свойства, можно определить другие элементы управления могут ссылаться на состояние компонента.

Далее в этом пошаговом руководстве описываются эти понятия.

## <a name="create-an-example-component"></a>Создание компонента

В этом примере вы создадите компонент меню, похожий на этом рисунке и в котором можно изменить текст и использовать в нескольких экранов и приложения:

![Окончательная версия коллекции](./media/create-component/menu-instance.png)

1. В PowerApps Studio создайте пустое приложение.

1. На панели навигации слева, откройте список компонентов и затем выберите **новый компонент**.

    ![Список компонентов](./media/create-component/component-list.png)

1. При наведении указателя новый компонент, нажмите кнопку с многоточием (...), выберите **Переименовать**, а затем введите или вставьте **MenuComponent**.

1. На панели справа задайте ширину компонента **150** и высоту, чтобы **250**, а затем выберите **новое пользовательское свойство**.

    ![Новое свойство](./media/create-component/new-property.png)

1. В **отображаемое имя**, **имя свойства**, и **описание** полях введите или вставьте **элементы**.

    ![Отображаемое имя, имя свойства, поля описания](./media/create-component/property-names.png)

    При указании имени свойства, не включайте пробелы, так как вы будете ссылаться на компонент с этим именем при написании формулу (например, **ComponentName.PropertyName**).

    Отображаемое имя отображается на **свойства** вкладки в области справа при выборе компонента. Описательное отображаемое имя поможет вам и другим лицам, принимающим понять назначение этого свойства. **Описание** отображается во всплывающей подсказке при наведении на отображаемое имя этого свойства в **свойства** вкладки.

1. В **тип данных** выберите **таблицы**, а затем выберите **создать**.

    ![Тип данных свойства](./media/create-component/property-data-type.png)

    **Элементы** свойству присвоено значение по умолчанию, в зависимости от заданного типа данных, но можно разместить его в значение, соответствующее вашим требованиям. Если указан тип данных **таблицы** или **записи**, может потребоваться изменить значение **элементы** свойства в соответствии со схемой данных, который требуется набор входных данных для компонента. В этом случае вам предстоит изменить на список строк.

    Можно задать значение свойства в строке формул, при выборе имени свойства на **свойства** вкладку на панели справа.

    ![Пользовательские входные свойства на вкладке "Свойства"](./media/create-component/properties-tab.png)

    Как показано в следующем графики, можно также изменить значение свойства на **Дополнительно** вкладку на панели справа.

1. Задание компонента **элементы** следующую формулу:

    ```powerapps-dot
    Table({Item:"SampleText"})
    ```

    ![Формула](./media/create-component/set-component-items.png)

1. В компоненте, вставить пустая, вертикальная **коллекции** элемента управления.

1. Убедитесь, что в списке свойств отображается **элементы** свойство (так как он это делает по умолчанию) и укажите значение этого свойства значение этого выражения:

    ```powerapps-dot
    MenuComponent.Items
    ```

    Таким образом, **элементы** свойство **коллекции** управления считывает и зависит от **элементы** входные свойства компонента.

1. Задайте **коллекции** элемента управления **BorderThickness** свойства **1** и его **TemplateSize** свойства **50**.

1. В шаблоне элемента **коллекции** управления, добавьте **метка** элемента управления.

    ![Добавьте метку и задайте границы элемента коллекции](./media/create-component/add-label.png)

Далее вы добавите компонент на экран и укажите таблицу строк для компонента для отображения.

1. На панели навигации слева выберите список экранов и выберите экран по умолчанию.

    ![Экран по умолчанию](./media/create-component/default-screen.png)

1. На **вставить** открытой вкладкой ", **компоненты** меню, а затем выберите **MenuComponent**.

    ![Вставить](./media/create-component/insert.png)

    Новый компонент называется **MenuComponent_1** по умолчанию.

1. Задайте **элементы** свойство **MenuComponent_1** следующую формулу:

    ```powerapps-dot
    Table({Item:"Home"}, {Item:"Admin"}, {Item:"About"}, {Item:"Help"})
    ```

    Этот экземпляр похоже на этом рисунке, но вы можете настроить текст и другие свойства каждого экземпляра.

    ![Окончательная версия коллекции](./media/create-component/menu-instance.png)

На данный момент создания компонента и добавить его в приложение. Далее вы создадите выходное свойство, которое отражает элемент, который пользователь выбирает в меню.

1. Откройте список компонентов, а затем выберите **MenuComponent**.

1. На панели справа выберите **свойства** , а затем выберите **новое пользовательское свойство**.

1. В **отображаемое имя**, **имя свойства**, и **описание** полях введите или вставьте **выбранные**.

1. В разделе **тип свойства**выберите **выходные данные**, а затем выберите **создать**.

1. На **Дополнительно** вкладке, установите для параметра **выбранные** значение этого выражения, Настройка цифрой в имени коллекции, при необходимости:

    ```powerapps-dot
    Gallery1.Selected.Item
    ```

    ![«Дополнительно»](./media/create-component/advance.png)

1. На экране по умолчанию приложения, добавьте метку и задайте его **текст** значение этого выражения, Настройка цифра в имя компонента, при необходимости:

    ```powerapps-dot
    MenuComponent_1.Selected
    ```

    Обратите внимание, что **MenuComponent_1** является именем экземпляра, а не имя определения компонента по умолчанию. Можно переименовать любой экземпляр.

1. Удерживая нажатой клавишу Alt, выберите все элементы в меню.

    **Метка** элемент управления представляет пункт меню, который вы выбрали наиболее недавно.

## <a name="known-limitations"></a>Известные ограничения

- На момент написания этой статьи, источники данных не сохраняются с компонентами, поэтому форм и таблицы данных отключены. 
- Если вы создаете переменную в компоненте, этой переменной относится только к этому компоненту и перестанет отображаться с переменными приложения.
- PowerApps не поддерживает коллекции в компонентах.
- Невозможно вставить компонента в коллекции, форме или карточки данных.
- Основной экземпляр компонента является локальным master и областью действия в приложение. Если вы измените основной экземпляр, изменения будут отражены только копии компонента в приложении. Копирует в других приложениях остается неизменным, если только вы снова импортировать библиотеки компонентов. Все экземпляры master в этих приложениях будет автоматически обнаружен и обновляется.
- Невозможно упаковать файлы мультимедиа, при импорте компонента.