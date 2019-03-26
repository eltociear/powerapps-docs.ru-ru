---
title: Создание зависимого стрелку раскрывающегося списка в приложение на основе холста | Документация Майкрософт
description: В PowerApps создайте стрелку раскрывающегося списка, который фильтрует другой стрелку раскрывающегося списка в приложение на основе холста.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 02/28/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e00c81f25de9a764e8f6d963ff94f3c0ffe052a2
ms.sourcegitcommit: 5b2b70c3fc7bcba5647d505a79276bbaad31c610
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58357260"
---
# <a name="create-dependent-drop-down-lists-in-a-canvas-app"></a>Создание зависимых раскрывающихся списков в приложение на основе холста

При создании зависимого (или каскадные) раскрывающиеся списки пользователей выберите параметр в списке, чтобы параметры фильтра из другого списка. Во многих организациях Создание зависимых списков, чтобы помочь пользователям заполнять формы более эффективно. Например пользователи могут выбрать страну или регион, чтобы отфильтровать список городов, или пользователи могут выбрать категорию, чтобы показать только коды в этой категории.

Рекомендуется создайте источник данных для значений в «родительской» и «дочерняя» списков (например, страны и регионы и города), отдельно от источника данных, который пользователи обновлять с помощью приложения. При использовании этого подхода же родительских и дочерних данных можно использовать в более чем одно приложение, и эти данные можно обновить без повторной публикации приложения или приложения, использующие их. Того же результата можно выполнить с помощью коллекции или статические данные, но не рекомендуется для корпоративных сценариев.

Для сценария, в этом разделе, хранить проблемы отправить сотрудникам, которые **инцидентов** список с помощью формы. Сотрудники указать не только расположение хранилища, в котором произошел инцидент, но также отдел в этом расположении. Не все расположения иметь же отделов, поэтому **расположения** списка гарантирует, что сотрудники нельзя указать подразделение для расположения, в котором нет этого отдела.

В этом разделе используется списков SharePoint в качестве источников данных, но все табличные источники данных работать так же.

## <a name="create-data-sources"></a>Создание источников данных

Объект **расположения** список отделов в каждом расположении.

| Location | Department |
|----------------|------------------|
| Eganville      | Кондитерская           |
| Eganville      | Разделитель             |
| Eganville      | Создать          |
| Renfrew        | Кондитерская           |
| Renfrew        | Разделитель             |
| Renfrew        | Создать          |
| Renfrew        | Лекарства         |
| Renfrew        | Цветы           |
| Потакет       | Кондитерская           |
| Потакет       | Разделитель             |
| Потакет       | Создать          |
| Потакет       | Цветы           |

**Инцидентов** перечислены контактные данные и сведения о каждом инциденте. Создать столбец дат как **даты** столбца, но создать те столбцы, что **однострочный текст** столбцы для упрощения настройки и избежать [делегирования](./delegation-overview.md) предупреждений в PowerApps.

| Имя | Фамилия | Номер телефона     | Location | Department | Описание       | Date      |
|------------|-----------|------------------|----------------|------------|-------------------------|-----------|
| Тоня       | Cortez   | (206) 555 - 1022 | Eganville      | Создать    | У меня есть проблема с...   | 2/12/2019 |
| Финансирования Moses     | Laflamme     | (425) 555 - 1044 | Renfrew        | Цветы     | Я столкнулся проблеме... | 2/13/2019 |

По умолчанию пользовательские списки SharePoint содержат **Title** столбца невозможно переименовать или удалить, и он должен содержать данные, чтобы можно было сохранить элемент в списке. Настройка столбца таким образом, чтобы он не требует данных:

1. В правом верхнем углу щелкните значок шестеренки, а затем выберите **параметры списка**.
1. На **параметры** выберите **Title** в списке столбцов.
1. В разделе **требуют, что этот столбец содержит сведения о**выберите **нет**.

После этого изменения можно игнорировать **Title** столбца, либо [удалить](https://support.office.com/article/edit-a-list-column-in-sharepoint-online-77130c2e-76d1-4f80-af8b-4c6f47b264b8) из представления по умолчанию, если хотя бы один столбец.

## <a name="open-the-form"></a>Откройте форму

1. Откройте **инцидентов** , а затем выберите **PowerApps** > **настройки форм**.

    > [!div class="mx-imgBorder"]
    > ![Откройте список инцидентов, а затем выберите PowerApps > Настройка форм. ](./media/dependent-drop-down-lists/open-form.png "Откройте список инцидентов, а затем выберите PowerApps > Настройка форм.")

    На вкладке браузера откроется форма по умолчанию в PowerApps Studio.

1. (необязательно) В **поля** панели при наведении поверх **Title** выберите кнопку с многоточием (...) отображается, а затем выберите **удалить**.

    Если вы закрыли **поля** области, можно открыть его снова, выбрав **SharePointForm1** в левой панели навигации, а затем пункт **изменить поля** на **Свойства** вкладку на панели справа.

1. (необязательно) Повторите предыдущий шаг, чтобы удалить **вложения** поля из формы.

    Появится форма с только поля, которые были добавлены.

    > [!div class="mx-imgBorder"]
    > ![Форме без полей заголовка и вложения](./media/dependent-drop-down-lists/default-form.png)

## <a name="replace-the-controls"></a>Замените элементы управления

1. В **поля** панели, щелкните стрелку вниз рядом с полем **расположение**.

    Если вы закрыли **поля** области, можно открыть его снова, выбрав **SharePointForm1** в левой панели навигации, а затем пункт **изменить поля** на **Свойства** вкладку на панели справа.

1. Откройте **типа элемента управления** , а затем выберите **разрешенные значения**.

    > [!div class="mx-imgBorder"]
    > ![Допустимые значения](./media/dependent-drop-down-lists/change-control.png)

    Механизм ввода изменяется на **раскрывающийся список** элемента управления.

1. Повторите эти шаги для **отдел** карты.

## <a name="add-the-locations-list"></a>Добавить в список расположений

1. Выберите **представление** > **источников данных** > **добавить источник данных**.

1. Выберите или создайте подключение SharePoint и затем выберите узел, который содержит **расположения** списка.

1. Установите флажок для этого списка, а затем выберите **Connect**.

    > [!div class="mx-imgBorder"]
    > ![Панель «данные»](./media/dependent-drop-down-lists/select-list.png)

    Список подключений отображается **инцидентов** списка, на котором основан формы, и **расположения** списка, которое будет определять и расположения подразделений в форме.

    > [!div class="mx-imgBorder"]
    > ![Источники данных SharePoint](./media/dependent-drop-down-lists/data-sources.png)

## <a name="unlock-the-cards"></a>Разблокировка карточки

1. Выберите **расположение** карты, выберите **Дополнительно** на панели справа, а затем выберите **Unlock для изменения свойств**.

1. Повторите предыдущий шаг для **отдел** карты.

## <a name="rename-the-controls"></a>Переименуйте элементы управления

При переименовании элементов управления, более легко определить их и в примерах показаны нагляднее. Познакомьтесь с другими рекомендациями, см. в статье [кодирования стандартам и правилам Технический документ](https://aka.ms/powerappscanvasguidelines).

1. В **расположение** карты, выберите **раскрывающийся список** элемента управления.

1. В верхней части панели справа, Переименование выбранного элемента управления, введя или вставив **ddLocation**.

    > [!div class="mx-imgBorder"]
    > ![Переименование элемента управления](./media/dependent-drop-down-lists/rename-control.png)

1. Повторите предыдущие два шага в **отдел** карты, чтобы переименовать **раскрывающийся список** управления **ddDepartment**.

## <a name="configure-the-locations"></a>Настройка расположений

1. Задайте **элементы** свойство **ddlocation** следующую формулу:

    `Distinct(Locations, Location)`

1. (необязательно) Удерживая нажатой клавишу Alt, откройте **ddLocation**и убедитесь, что в списке отображается трех расположениях.

## <a name="configure-the-departments"></a>Настройка отделов

1. Выберите **ddDepartment** и затем на **свойства** вкладку на правой панели, выберите **зависит.**

1. В разделе **родительского элемента управления**, убедитесь, что **ddLocation** появляется в верхнем списке и **результат** отображается в нижнем списке.

    > [!NOTE]
    > Если вы не хотите совпадений в строке, а на фактический идентификатор строки данных, выберите **идентификатор** вместо **результат**.

1. В разделе **поля сопоставления**выберите **расположения** в верхнем списке выберите **расположение** в нижнем списке, а затем выберите **применить**.

    > [!div class="mx-imgBorder"]
    > ![Зависит от связи](./media/dependent-drop-down-lists/depends-on.png)

    **Элементы** свойство **ddDepartment** задайте следующую формулу:

    `Filter(Locations, Location = ddLocation.Selected.Result)`

    Эта формула фильтрует элементы в **ddDepartment** на пользователь выбирает в основе **ddLocation**. Такая конфигурация гарантирует, что «дочерняя» список отделов отражает данные к расположению «родительский» как **расположения** Указывает список в SharePoint.

1. На **свойства** вкладку на панели справа откройте список рядом с полем **значение**, а затем выберите **отдел**.

    Этот шаг задает отображаемый текст для параметров из **отдел** столбец **расположения** списка в SharePoint.

    > [!div class="mx-imgBorder"]
    > ![Значение отдела](./media/dependent-drop-down-lists/dept-value.png)

## <a name="test-the-form"></a>Проверить форму

Хотя удерживая нажатой клавишу Alt, откройте список расположений, выберите один, откройте список отделов и затем выберите один.

В списках и расположения подразделений, отражает сведения в **расположения** списка в SharePoint.

> [!div class="mx-imgBorder"]
> ![Откройте список расположений, измените из Renfrew потакет; и затем откройте список отделов](./media/dependent-drop-down-lists/dropdowns.gif)

## <a name="save-and-open-the-form-optional"></a>Сохранить и открыть форму (необязательно)

1. Откройте **файл** меню, а затем выберите **Сохранить** > **опубликовать в SharePoint** > **опубликовать в SharePoint**.

1. В левом верхнем углу нажмите на стрелку "Назад" и выберите **Вернуться в SharePoint**.

1. На панели команд выберите **Создать**, чтобы открыть настроенную форму.

## <a name="faq"></a>ВОПРОСЫ И ОТВЕТЫ

**Я не вижу данные: источники, окажутся пустыми или иметь неверные данные.**
Подтверждение ли вы отображаете соответствующие поля для элемента управления в любой из следующих способов:

- Выберите стрелку раскрывающегося списка, а затем выберите **значение** свойство в **свойства** вкладку на панели справа.

    > [!div class="mx-imgBorder"]
    > ![Раскрывающийся список для смены](./media/dependent-drop-down-lists/drop-down-display-field.png)

- Выберите поле со списком и убедитесь, что основной текст является полем, которое будет отображаться.

    > [!div class="mx-imgBorder"]
    > ![Поле со списком изменений](./media/dependent-drop-down-lists/combo-box-display-field.png)

**Мой список раскрывающегося списка дочерних содержит повторяющиеся элементы.**
Этот симптом, вероятнее всего из-за использования **подстановки** столбец SharePoint или **варианты** функции в PowerApps. Для удаления дублирования, заключите **Distinct** функция вокруг правильно возвращаемых данных. Дополнительные сведения: [Функция DISTINCT](functions/function-distinct.md)

## <a name="known-limitations"></a>Известные ограничения

Эта конфигурация доступна на **раскрывающийся список** элементов управления, а также **поле со списком** и **поле со списком** элементов управления, которые допускаются за раз. Нельзя использовать **зависит** конфигурации для любого из этих элементов управления, если они разрешить выбор нескольких элементов. Такой подход не рекомендуется для работы с наборами параметр и общие службы данных.

**Зависит** конфигурации не поддерживает статические данные или коллекций. Чтобы настроить зависимых раскрывающихся списков в этих источниках, измените выражение непосредственно в строке формул. Кроме того, PowerApps не поддерживает использование два поля выбора в SharePoint без любой сопоставления таблицы данных, и нельзя определить **сопоставление поля** в пользовательском Интерфейсе.