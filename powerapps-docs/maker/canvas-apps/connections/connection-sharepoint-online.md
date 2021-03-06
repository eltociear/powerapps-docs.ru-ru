---
title: Общие сведения о подключении к SharePoint | Документация Майкрософт
description: См. доступные функции, ответы и примеры для SharePoint.
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/03/2019
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0c0f4744e7b323e3262a63278e7c12348142a99b
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79212453"
---
# <a name="connect-to-sharepoint-from-a-canvas-app"></a>Подключение к SharePoint из приложения Canvas

![SharePoint](./media/connection-sharepoint-online/sharepointicon.png)

Подключитесь к сайту SharePoint для автоматического создания приложения из пользовательского списка или создайте подключение, прежде чем добавлять данные в существующее приложение или создавать приложения с нуля.

В зависимости от того, где находятся данные, можно использовать один из этих подходов или оба.

- Отображение данных из пользовательского списка на сайте SharePoint Online или на локальном сайте.
- Отображение изображений и воспроизведение видео-или звуковых файлов в библиотеке (только для SharePoint Online).

## <a name="generate-an-app"></a>Создание приложения

Если вы хотите управлять данными в пользовательском списке, Power Apps может [автоматически создать приложение с тремя экранами](../app-from-sharepoint.md). Пользователи могут просматривать список на первом экране, отображать сведения о элементе на втором экране, а также создавать или обновлять элементы на третьем экране.

> [!NOTE]
> Если список SharePoint содержит столбец **выбора**, **поиска**или **пользователя или группы** , см. раздел [Отображение данных в галерее](connection-sharepoint-online.md#show-list-columns-in-a-gallery) далее в этом разделе.

## <a name="create-a-connection"></a>Создание подключения

1. [Войдите в Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), выберите **данные** > **подключения** на левой панели навигации, а затем выберите **новое подключение** в левом верхнем углу.

    > [!div class="mx-imgBorder"]
    > ![выберите данные > подключения на левой панели навигации, а затем выберите новое подключение в левом верхнем углу.](./media/connection-sharepoint-online/new-connection.png)

1. В поле поиска, расположенном в правом верхнем углу, введите или вставьте **SharePoint**, а затем выберите **SharePoint**.

    > [!div class="mx-imgBorder"]
    > ![в поле поиска, расположенном в правом верхнем углу, введите или вставьте SharePoint, а затем выберите SharePoint.](./media/connection-sharepoint-online/select-sharepoint.png)

1. Выполните один из следующих наборов действий.

    - Чтобы подключиться к SharePoint Online, выберите **подключиться напрямую (облачные службы)**, щелкните **создать**, а затем укажите учетные данные (при появлении соответствующего запроса).

        > [!div class="mx-imgBorder"]
        > ![для подключения к SharePoint Online выберите подключиться напрямую (облачные службы)](./media/connection-sharepoint-online/select-online.png)

        Подключение будет создано, и вы сможете добавить данные в существующее приложение или создать приложение с нуля.

    - Чтобы подключиться к локальному сайту, выберите **подключиться с помощью локального шлюза данных**.

        > [!div class="mx-imgBorder"]
        > ![подключиться к локальному сайту, выберите * * подключение с помощью локального шлюза данных)](./media/connection-sharepoint-online/select-onprem.png)

        Выберите параметр **Windows** в качестве типа проверки подлинности, а затем введите учетные данные. (Если учетные данные содержат имя домена, укажите его в формате *домен\псевдоним*.)

        > [!div class="mx-imgBorder"]
        > ![указать учетные данные](./media/connection-sharepoint-online/specify-creds.png)

        В разделе **Выбор шлюза**выберите шлюз, который требуется использовать, и нажмите кнопку **создать**.

        > [!NOTE]
        > Если локальный шлюз данных не установлен, [установите его](../gateway-reference.md), а затем щелкните значок, чтобы обновить список шлюзов.

        > [!div class="mx-imgBorder"]
        > ![выбрать](./media/connection-sharepoint-online/choose-gateway.png) шлюза

        Подключение будет создано, и вы сможете добавить данные в существующее приложение или создать приложение с нуля.

## <a name="add-data-to-an-existing-app"></a>Добавление данных в существующее приложение

1. В Power Apps Studio откройте приложение, которое необходимо обновить, перейдите на вкладку **вид** и выберите **Источники данных**.

    > [!div class="mx-imgBorder"]
    > ![на вкладке Вид, а затем выберите источники данных](./media/connection-sharepoint-online/view-data-sources.png)

1. На панели **данные** выберите **добавить источник данных** > **SharePoint**.

1. В разделе **Подключение к сайту SharePoint**выберите запись в списке **Последние сайты** (или введите или вставьте URL-адрес сайта, который вы хотите использовать), а затем нажмите кнопку **Подключиться**.

    > [!div class="mx-imgBorder"]
    > ![выбрать](./media/connection-sharepoint-online/select-sp-site.png) сайта

1. В разделе **Выбор списка**установите флажок для **документов** или одного или нескольких списков, которые необходимо использовать, а затем выберите **подключить**.

    > [!div class="mx-imgBorder"]
    > ![в разделе Выбор списка установите флажок для документов или одного или нескольких списков, которые необходимо использовать, а затем выберите Подключить](./media/connection-sharepoint-online/select-sp-tables.png)

    По умолчанию отображаются не все типы списков. Power Apps поддерживает пользовательские списки, а не списки на основе шаблона. Если имя списка, которое вы хотите использовать, не отображается, прокрутите вниз и введите имя списка в поле, содержащее **имя настраиваемой таблицы**.

    > [!div class="mx-imgBorder"]
    > ![введите имя списка в поле, содержащее имя настраиваемого списка.](./media/connection-sharepoint-online/custom-list.png)

    Источник данных или источники добавляются в приложение.

## <a name="build-your-own-app-from-scratch"></a>Создание собственного приложения с нуля

Применяйте концепции в разделе [Создание приложения с нуля](../get-started-create-from-blank.md) для SharePoint, а не Excel.

## <a name="show-list-columns-in-a-gallery"></a>Отображение столбцов списка в коллекции

Если пользовательский список содержит какие-либо из этих типов столбцов, покажите эти данные в элементе управления " **коллекция** " с помощью строки формул, чтобы задать свойство **Text** одного или нескольких элементов управления **Label** в этой коллекции:

- Для столбца **выбора** или **подстановки** укажите **сиситем.** _ColumnName_**. Значение** для отображения данных в этом столбце.

    Например, если вы используете столбец **Выбор** с именем **Location**, укажите значение **ThisItem.Location.Value**. Если же вы используете столбец **Подстановка** с именем **PostalCode**, укажите значение **ThisItem.PostalCode.Value**.

- Для столбца " **пользователь" или "Группа** " укажите **сиситем.** _ColumnName_**. DisplayName** для отображения отображаемого имени пользователя или группы.

    Например, укажите значение **ThisItem.Manager.DisplayName**, чтобы отобразить имя из столбца **Пользователь или группа** с именем **Manager**.

    Вы также можете отобразить другие сведения о пользователях, например адрес электронной почты или должность. Чтобы отобразить полный список параметров, укажите **сиситем.** _ColumnName_**.** (включая конечную точку).

    > [!NOTE]
    > Для столбца **CreatedBy** укажите **сиситем. Author. DisplayName** , чтобы отобразить отображаемые имена пользователей, создавших элементы в списке. Для столбца **ModifiedBy** укажите значение **ThisItem.Editor.DisplayName**, чтобы отобразить имена пользователей, изменивших элементы в списке.

- Для столбца **управляемых метаданных** укажите **сиситем.** _ColumnName_**. Метка** для отображения данных в этом столбце.

    Например, при наличии столбца **Управляемые метаданные** с именем **Languages** укажите значение **ThisItem.Languages.Label**.

## <a name="show-data-from-a-library"></a>Отображение данных из библиотеки

Если в библиотеке SharePoint имеется несколько изображений, можно добавить в приложение **раскрывающийся список** , чтобы пользователи могли указать, какие изображения следует отображать. Вы также можете применить те же принципы к другим элементам управления, таким как элементы управления **галереи** , и другим типам данных, таким как видео.

1. [Создайте подключение](#create-a-connection), а затем [добавьте данные в существующее приложение](#add-data-to-an-existing-app), если вы еще этого не сделали.

1. Добавьте элемент управления "раскрывающийся **список** " и назовите его **ImageList**.

1. Присвойте свойству **Items** элемента **ImageList** значение **Documents**.

1. На вкладке **Свойства** правой панели откройте список **значение** и выберите **имя**.

    Имена файлов изображений в библиотеке отображаются в **ImageList**.

    > [!div class="mx-imgBorder"]
    > ![список образов](./media/connection-sharepoint-online/dropdown-items.png)

1. Добавьте элемент управления **Image** и задайте для его свойства **Image** следующее выражение:

    `ImageList.Selected.'Link to item'`

1. Нажмите клавишу F5, а затем выберите другое значение в **ImageList**.

    Появится указанное изображение.

    > [!div class="mx-imgBorder"]
    > ![](./media/connection-sharepoint-online/golden-honey.png) образца образа

Вы можете [скачать пример приложения](https://pwrappssamples.blob.core.windows.net/samples/spdoclib_blogapp.msapp) , демонстрирующий более сложный подход к отображению данных из библиотеки SharePoint.

1. После загрузки приложения откройте [Power Apps Studio](https://us.create.powerapps.com/studio/#), выберите **Открыть** на панели навигации слева и нажмите кнопку **Обзор**.
1. В диалоговом окне **Открыть** найдите и откройте скачанный файл, а затем добавьте библиотеку SharePoint в качестве источника данных, выполнив первые две процедуры, описанные в этом разделе.

> [!NOTE]
> По умолчанию в этом приложении отображаются [предупреждения о делегировании](../delegation-overview.md), но их можно игнорировать, если в библиотеке содержится менее 500 элементов.

В этом одностраничном приложении в списке в левом нижнем углу отображаются все файлы в библиотеке.

- Можно выполнить поиск файла, введя или вставляя один или несколько символов в поле поиска рядом с верхней.
- Если библиотека содержит папки, можно отфильтровать список файлов, щелкнув значок фильтра в списке папок в заголовке окна.

Если нужный файл найден, выберите его, чтобы отобразить в элементе управления **видео**, **изображение**или **звук** на правой стороне.

> [!div class="mx-imgBorder"]
> ![](./media/connection-sharepoint-online/library-app.png) образца образа

## <a name="known-issues"></a>Известные проблемы

### <a name="lists"></a>Списки

Power Apps может считывать имена столбцов, содержащих пробелы, но пробелы заменяются шестнадцатеричным escape-кодом **"\_x0020\_"**. Например, **"имя столбца"** в SharePoint будет отображаться как **"Column_x0020_Name"** в Power Apps, если оно отображается в макете данных или используется в формуле.

Поддерживаются не все типы столбцов, а не все типы столбцов поддерживают все типы карт.

| Тип столбца | Поддержка | Карточки по умолчанию |
| --- | --- | --- |
| Однострочный текст |Да |Просмотр текста |
| Многострочный текст |Да |Просмотр текста |
| Выбор |Да |Просмотреть подстановку<br>Изменить подстановку<br>Просмотр полей с множественным выбором<br>Редактирование полей с множественным выбором |
| Number |Да |Просмотреть процентное значение<br>Просмотреть оценку<br>Просмотр текста |
| Currency |Да |Просмотреть процентное значение<br>Просмотреть оценку<br>Просмотр текста |
| Дата и время |Да |Просмотр текста |
| Просмотр |Да |Просмотреть подстановку<br>Изменить подстановку<br>Просмотр полей с множественным выбором<br>Редактирование полей с множественным выбором |
| Логическое значение (да или нет) |Да |Просмотр текста<br>Просмотреть переключатель |
| "Пользователь" или "Группа"; |Да |Просмотреть подстановку<br>Изменить подстановку<br>Просмотр полей с множественным выбором<br>Редактирование полей с множественным выбором |
| Hyperlink |Да |Просмотреть URL-адрес<br>Просмотр текста |
| Рисунок |Да (только для чтения) |Просмотреть изображение<br>Просмотр текста |
| Вложение |Да (только для чтения) |Просмотр вложений|
| Вычисляемое |Да (только для чтения) | |
| Результат задачи |Нет | |
| Внешние данные |Нет | |
| "Управляемые метаданные". |Да (только для чтения) | |
| Rating |Нет | |

### <a name="libraries"></a>Библиотеки

- Вы не можете отправлять файлы из Power Apps в библиотеку.
- Не удается отобразить PDF-файлы из библиотеки в элементе управления PDF Viewer.
- Power Apps Mobile не поддерживает функцию **скачивания** .
- Если пользователи будут запускать приложение в приложении Power Apps Mobile или Windows 10, используйте функцию **запуска** для показа содержимого библиотеки в галерее.

## <a name="next-steps"></a>Следующие шаги

- Узнайте, как [отобразить данные из источника данных](../add-gallery.md).
- Узнайте, как [создать, обновить записи и просмотреть сведения о них](../add-form.md).
- См. другие типы [источников данных](../connections-list.md), к которым можно подключаться.
