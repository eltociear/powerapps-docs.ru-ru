---
title: Создание и изменение отношений сущностей "Один-ко-многим" или "Многие-к-одному" на портале PowerApps | MicrosoftDocs
description: 'Узнайте, как создать отношение сущностей "один-ко-многим" или "многие-к-одному" с помощью портала PowerApps.'
ms.custom: ''
ms.date: 06/11/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-and-edit-one-to-many-or-many-to-one-entity-relationships-using-powerapps-portal"></a>Создание и изменение отношений сущностей "Один-ко-многим" или "Многие-к-одному" на портале PowerApps

[Портал PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) обеспечивает простой способ создания и изменения отношений 1:N (один-ко-многим) или N:1 (многие-к-одному) в Common Data Service для приложений.

Портал позволяет настроить самые распространенные параметры, но некоторые параметры можно задать только с помощью обозревателя решений. Дополнительные сведения: 
- [Создание и изменение отношений 1:N (один-ко-многим) или N:1 (многие-к-одному)](create-edit-1n-relationships.md)
- [Создание и изменение отношений сущностей 1:N (один-ко-многим) или N:1 (многие-к-одному) с помощью обозревателя решений](create-edit-1n-relationships-solution-explorer.md).

## <a name="view-entity-relationships"></a>Просмотр отношений сущностей

1. На [портале PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) выберите режим конструирования **Управляемые моделью** или **Холст**.
2. Выберите **Данные** > **Сущности** и выберите сущность с отношениями, которые необходимо просмотреть.
3. На вкладке **Отношения** можно выбрать следующие представления. 

 |Представление|Описание|
 |--|--|
 |**Все**| Отображаются все отношения для сущности|
 |**Настраиваемый**|Отображаются все только настраиваемые отношения для сущности|
 |**По умолчанию**|Отображаются только стандартные отношения для сущности|
<!-- TODO: What is the actual difference between All and Default? -->

![Отношения сущностей организации](media/view-account-relationships-portal.png)

## <a name="create-relationships"></a>Создание отношений

Во время [просмотра отношений сущностей](#view-entity-relationships) на панели команд выберите **Добавить отношение** и выберите **Многие-к-одному** или **Многие-ко-многим**.

![Выбор типа отношения](media/add-relationship-menu-portal.png)

> [!NOTE]
> Дополнительные сведения об отношениях **Многие-ко-многим** см. в разделе [Создание отношений N:N (многие-ко-многим)](create-edit-nn-relationships.md)

<!-- This may change going forward, but this is the way it is now. #2534972 -->
> [!Important]
> Терминология на портале отличается от терминологии в обозревателе решений. Термины инвертированы. **Связанная сущность** в обозревателе решений — это **Основная сущность** на портале. Аналогично, **Основная сущность** в обозревателе решений — это **Связанная сущность** на портале.

В зависимости от выбора вы увидите одно из двух:

<!-- These are the correct screenshots from the UI as of 6/11/18 -->
|Тип|Панель|
|--|--|
|**Многие-к-одному**|![Панель отношения "многие-к-одному"](media/many-to-one-relationship-panel.png)|
|**Один-ко-многим**|![Панель отношения "один-ко-многим"](media/one-to-many-relationship-panel.png)|

Выберите параметр **Связанная сущность** или **Основная сущность** для отношения, которое требуется создать между двумя сущностями. 

> [!NOTE]
> В любом случае поле поиска будет создано в *основной* сущности.

После выбора сущности можно изменять сведения об отношении. В этом примере несколько записей сущностей контактов можно связать с одной организацией.

<!-- These are the correct screenshots from the UI as of 6/11/18 -->
![Организация и контакт отношения "один-ко-многим"](media/One-to-many-account-contact.png)

Перед сохранением можно изменить предоставленные значения по умолчанию. Выберите **Дополнительно** для просмотра значений **Имя отношения** и **Описание поля поиска**.

|Поле|Описание|
|--|--|
|**Отображаемое имя поля поиска**|Локализуемый текст для поля поиска, который будет создан в связанной сущности.<br />Его можно изменить позже.|
|**Имя поля поиска**|Имя поля поиска, которое будет создано в связанной сущности.|
|**Имя отношения**|Имя отношения, которое будет создано.|
|**Описание поля поиска**|Описание поля поиска. В управляемых моделью приложениях оно отобразится как всплывающая подсказка при наведении указателя мыши на поле. <br />Его можно изменить позже.|

Вы можете продолжить изменение сущности. Выберите **Сохранить сущность** для создания настроенного отношения.

## <a name="edit-relationships"></a>Редактирование отношений

Во время [просмотра отношений сущности](#view-entity-relationships) выберите отношение, которое следует изменить.

> [!NOTE]
> Каждое отношение можно найти в основной или связанной сущности как отношение **Многие-к-одному** или **Один-ко-многим**. Хотя его можно изменить в любом месте, это то же самое отношение.
>
> Издатель управляемого решения поможет запретить некоторые настройки отношений, являющиеся частью его решения.

Единственные поля, которые можно изменить, — это **Отображаемое имя поля поиска** и **Описание поля поиска**. Это также можно изменить в свойствах поля поиска в связанной сущности. Дополнительные сведения: [Изменение поля](create-edit-field-portal.md#edit-a-field)

## <a name="delete-relationships"></a>Удаление отношений

Во время [просмотра отношений сущности](#view-entity-relationships) выберите отношение, которое следует удалить.

![Удаление отношения сущностей](media/delete-entity-relationship-portal.png)

Можно использовать команду **Удалить отношение** с панели команд или из контекстного меню строки при нажатии многоточия (**...**).

Удаление отношения приведет к удалению поля поиска в связанной сущности.

> [!NOTE]
> Вы не сможете удалить отношение, которое имеет зависимости. Например, при добавлении поля поиска в форму для связанной сущности следует удалить поле из формы перед удалением отношения.

### <a name="see-also"></a>См. также

[Создание и изменение отношений между сущностями](create-edit-entity-relationships.md)<br />
[Создание и изменение отношений 1:N (один-ко-многим) или N:1 (многие-к-одному)](create-edit-1n-relationships.md)<br />
[Создание и изменение отношений сущностей 1:N (один-ко-многим) или N:1 (многие-к-одному) с помощью обозревателя решений](create-edit-1n-relationships-solution-explorer.md)<br />
[Изменение поля](create-edit-field-portal.md#edit-a-field)