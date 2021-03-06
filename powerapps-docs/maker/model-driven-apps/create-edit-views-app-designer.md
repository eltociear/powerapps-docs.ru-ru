---
title: Создание и изменение общих или системных представлений управляемых моделью приложений в Power Apps | Документация Майкрософт
description: Узнайте, как создавать или изменять представления с помощью конструктора приложений
keywords: ''
ms.date: 03/23/2020
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 666ab3f3-abda-468c-b248-3a0b410286b0
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 1
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 10aa1623cbc3ff90788257641afd71ac0e149375
ms.sourcegitcommit: 9f2694bd14d70798310b89a4673672c1bfad989d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "3166853"
---
# <a name="create-and-edit-public-or-system-model-driven-app-views"></a>Создание и изменение общих или системных представлений управляемых моделью приложений

В этом разделе вы выполните несколько задач, необходимых для работы с представлениями, например создание общего представления, добавление существующего представления к приложению и изменение столбцов, фильтров и порядка сортировки для представления.

В Power Apps представления определяют отображение записей для конкретной сущности. Представление определяет следующее:
-  Отображаемые столбцы (атрибуты)
-  Ширина столбцов
-  Порядок сортировки записей по умолчанию
-  Какие фильтры применяются по умолчанию для определения отображаемых записей в списке

Как правило, представления классифицируются по трем типам:
- **Личное.** Отдельные пользователи могут создавать личные представления согласно своим личным требованиям. Эти представления отображаются только пользователю, создавшему их, и всем, кому этот пользователь предоставил доступ к этим представлениям. 
- **Общие.** Как создатель приложений, вы можете создавать и изменять общие представления в соответствии с требованиями организации. Эти представления отображаются в средстве выбора представлений, и их можно использовать во вложенных сетках в форме или в виде списка на панели мониторинга.
- **Системные.** Как создатель приложения, вы можете также изменять системные представления в соответствии с требованиями организации. Это специальные представления, от которых зависит приложение: они существуют для системных сущностей или автоматически создаются при создании настраиваемых сущностей. Такие представления доступны некоторым или всем пользователям, в зависимости от их разрешений.

Дополнительные сведения см. в разделе [Сведения о представлениях](create-edit-views.md)

## <a name="create-a-public-view-in-power-apps"></a>Создание общего представления в Power Apps
Как создатель приложения, вы можете создавать и изменять общие представления с помощью Power Apps.
1. Выполните вход в [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  

2.  Разверните **Данные**, выберите **Сущности**, выберите требуемую сущность, затем выберите вкладку **Представления**. 

3. На панели инструментов выберите **Добавить представление**. 

4. В диалоговом окне **Создать представление** введите имя и, при желании, описание, затем выберите **Создать**. 
    
5. В конструкторе представлений выберите кнопку со знаком "плюс" для добавления дополнительных столбцов, которые требуются показывать в представлении. Дополнительные сведения: [Добавление столбца в представление в конструкторе приложений](#add-a-column-to-your-view-in-app-designer) 

   ![Добавить столбец](../common-data-service/media/add-column-to-view.png)

6. В конструкторе представлений можно выполнить следующие задачи: 
   - Для изменения фильтра столбца выберите заголовок столбца, который требуется фильтровать, затем в раскрывающемся списке выберите **Фильтровать по**.
   - Для изменения сортировку столбца выберите заголовок столбца, который требуется фильтровать, затем выберите **Сортировка от А до Я** или **Сортировка от Я до А**.
   - Задайте ширину столбца, щелкнув и перетащив столбец в требуемое положение.
   - Измените порядок столбцов, перетащив столбец в требуемое положение. 

    > [!NOTE]
    > Можно также изменить порядок столбцов, щелкнув заголовок столбца и выбрав **Вправо** или **Влево**.

10. Выберите **Опубликовать**, чтобы сохранить представление и сделать его доступным для других пользователей в организации. 
   

## <a name="work-with-views-in-app-designer"></a>Работа с представлениями в конструкторе приложений
В следующих разделах описываются способы создания и изменения представлений в конструкторе приложений.

### <a name="open-and-add-a-view-in-the-app-designer"></a>Открытие и добавление представления в конструкторе приложений

Следующие шаги объясняют, как открыть и добавить представление в конструкторе приложений.
1. В Power Apps выберите **Приложения** в левой панели навигации, выберите **...** рядом с требуемым приложением, затем выберите **Изменить**. 

2. В разделе **Представление сущности** конструктора приложений выберите **Представления**.

    В этом примере мы выбрали **Представления** из сущности **Организация**.

    ![Представление конструктора приложений](media/ViewAppDesigner_AccountAppDesignerView.png "Представление конструктора приложений для сущности организации")

3. Для добавления представления выберите его с помощью типов представлений, таких как общее, расширенный поиск и постановка. Представление автоматически добавляется в список **Представления**.

    > [!NOTE]
    > Представления отображаются на основе сущности, которую вы выбрали. Например, если выбрана сущность **Организация**, отображаются представления, связанные с сущностью "Организация".

Дополнительные сведения по конструктору приложений: [Разработка настраиваемых бизнес-приложений с помощью конструктора приложений](design-custom-business-apps-using-app-designer.md)


### <a name="add-a-column-to-your-view-in-app-designer"></a>Добавление столбца в представление в конструкторе приложений
В представлении записи отображаются в таблице, содержащей строки и столбцы. Каждая строка представляет запись, а отображаемые поля записи определяются столбцами, добавленными в представление.

1. В конструкторе приложений выберите нужное представление сущности, затем на правой панели рядом с требуемым представлением выберите "изменить" (кнопка с карандашом).  
2. На вкладке **Компоненты** выберите список **Атрибуты столбца** для **Основная сущность** или **Связанная сущность**.

    ![Добавить столбец](media/ViewAppDesigner_AddColumn.png "Добавление столбца к представлению") 

3. В списке выберите требуемый атрибут и перетащите его к заголовку столбца. Можно также добавить атрибут, дважды щелкнув его.
4. Повторите шаг 3, пока не добавите все требующиеся атрибуты, которые требуется показывать в представлении.

По мере добавления атрибутов можно перетаскивать их в любое положение среди существующих заголовков столбцов. Можно также перетаскивать столбцы после их добавления в представление.


### <a name="define-filter-criteria-in-app-designer"></a>Задание условий фильтрации в конструкторе приложений
Можно задать условия фильтра, чтобы только подмножество записей отображалось в представлении. Если пользователь открывает представление, отображаются только записи, которые соответствуют определенным условиям фильтрации. Для фильтрации можно выбирать поля как в основном, так и в связанных представлениях.
1. В конструкторе приложений разверните раздел **Критерии фильтра**.
   
    ![Задать условия фильтра](media/ViewAppDesigner_FilterCriteria.png "Задание условий фильтра") 

2. Выберите **Добавить фильтр**.
3. Выберите атрибут из раскрывающегося списка в первом столбце. 
4. Выберите оператор из раскрывающегося списка во втором столбце.

    ![Задание оператора критериев фильтра](media/ViewAppDesigner_FilterCriteriaOption.png "Задание оператора критериев фильтра")

5. Введите значение, по которому требуется выполнять фильтрацию, в третьем столбце.

Можно выполнить фильтрацию данных на основе атрибутов связанных сущностей в дополнение к основной сущности. 

1. На вкладке **Компоненты** выберите список **Атрибуты столбца** для **Связанная сущность**, выберите значок со стрелкой вниз **Выберите сущность** в самом верхнем поле, затем выберите требуемую сущность.

    При этом будет добавлен отдельный раздел.

2. Повторите шаги со 2 по 5 из предыдущей процедуры.

Дополнительные сведения: [Создание и изменение отношений между сущностями](../common-data-service/create-edit-entity-relationships.md)

#### <a name="group-multiple-filters-in-app-designer"></a>Группировка нескольких фильтров в конструкторе приложений
Можно добавить несколько фильтров в представление, если требуется фильтровать записи с помощью нескольких полей. 

1. Выберите фильтры, который необходимо сгруппировать.
    ![Задание группировки фильтров](media/ViewAppDesigner_GroupFilter.png "Задание группировки фильтров")
2. Выберите "Группировка И" или "Группировка ИЛИ" для группирования фильтров.
    ![Выбор группирования фильтров](media/ViewAppDesigner_GroupFilterSelection.png "Выбор группирования фильтров") Если выбран вариант **Группировка И**, в представлении отображаются только записи, которые соответствуют обоим критериям. Если выбран вариант **Группировка ИЛИ**, отображаются записи, отвечающие любому из указанных условий фильтра. Например, чтобы отобразить только записи с уровнем приоритета "Высокий" или "Обычный" и состоянием "Активна", выберите **Группировка И**.

Чтобы удалить фильтр из группы, выберите группу, затем выберите **Разгруппировать**. 

### <a name="set-primary-and-secondary-sort-order-for-columns-in-app-designer"></a>Задание основного и дополнительного порядка сортировки для столбцов в конструкторе приложений
При открытии представления отображаемые записи сортируются в порядке, заданном при создании представления.   По умолчанию записи сортируются в соответствии с первым столбцом в представлении, если порядок сортировки не выбран. Можно выбрать сортировку по одному столбцу или можно выбрать сортировку по двум столбцам — одному основному и одному дополнительному. При открытии представления записи сначала сортируются по столбцу, который требуется использовать для основной сортировки, а затем по столбцу, который будет использоваться для дополнительной сортировки. 

> [!NOTE]
> Можно задать основной и дополнительный порядки сортировки только для атрибутов столбцов, добавленных из основной сущности.

1. Выберите столбец, который требуется использовать для сортировки.
2. Выберите стрелку вниз, затем выберите **Основная сортировка** или **Дополнительная сортировка**.
 
    ![Сортировка записи](media/ViewAppDesigner_SortRecords.png "Сортировка записей на основе основного и дополнительного порядков сортировки") 

Если удалить столбец, выбранный для основного порядка сортировки, основным становится столбец, выбранный для дополнительного порядка сортировки.

### <a name="define-a-web-resource-in-app-designer"></a>Определение веб-ресурса в конструкторе приложений
Укажите веб-ресурс типа "скрипт", чтобы ассоциировать его со столбцом в представлении. Эти скрипты помогают отображать значки для столбцов.

1. Выберите столбец, в который требуется добавить веб-ресурс.
2. На вкладке **Свойства** выберите **Дополнительно**.
3. В раскрывающемся списке **Веб-ресурс** выберите требуемый веб-ресурс.
4. В поле **Имя функции** введите имя функции.

### <a name="edit-a-public-or-system-view-in-app-designer"></a>Изменение общего или системного представления в конструкторе приложений
Можно изменить способ отображения общего или системного представления, добавляя, настраивая или удаляя столбцы.
1. В списке **Представления** для сущности выберите стрелку вниз **Показать список ссылок** ![Раскрывающийся список](media/DownArrow.png "Стрелка раскрывающегося списка").
    ![Изменение представления](media/ViewAppDesigner_EditView.png "Изменение общего или системного представления")
2. Рядом с представлением, которое требуется изменить, выберите **Открыть конструктор представлений** ![Открыть конструктор представлений](media/dynamics365-open-designer.png "Открытие конструктора представлений"). 

    Представление открывается в конструкторе представлений. 

При изменении общего или системного представления необходимо сохранить и опубликовать изменения, чтобы они отображались в приложении.


## <a name="community-tools"></a>Средства сообщества
**View Layout Replicator** и **View Designer** — это средства, разработанные сообществом XrmToolbox для Power Apps.

Дополнительные сведения: [Средства для разработчиков](/powerapps/developer/common-data-service/developer-tools).

> [!NOTE]
> Эти средства предоставляются сообществом XrmToolBox и не поддерживаются Майкрософт. При наличии вопросов по средству обращайтесь к его издателю. Дополнительные сведения: [XrmToolBox](https://www.xrmtoolbox.com/). 

### <a name="next-steps"></a>Дальнейшие действия
[Создание отношений 1: N (один-ко-многим) или N:1 (многие-к-одному)](../common-data-service/create-edit-1n-relationships.md)
