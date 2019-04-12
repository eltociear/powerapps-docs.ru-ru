---
title: Создание отношений сущностей "многие-ко-многим" в Common Data Service с помощью портала PowerApps | MicrosoftDocs
description: 'Узнайте, как создавать отношения многие-ко-многим'
ms.custom: ''
ms.date: 06/11/2018
ms.reviewer: ''
ms.service: powerapps
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

# <a name="create-many-to-many-entity-relationships-in-common-data-service-using-powerapps-portal"></a>Создание отношений сущностей "многие-ко-многим" в Common Data Service с помощью портала PowerApps

[Портал PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) обеспечивает простой способ создания и изменений отношений сущностей "многие ко многим" в Common Data Service.

Портал позволяет настроить самые распространенные параметры, но некоторые параметры можно задать только с помощью обозревателя решений. Дополнительные сведения: 
- [Обзор создания отношений сущностей N:N (многие-ко-многим)](create-edit-nn-relationships.md)
- [Создание отношений сущностей N:N (многие-ко-многим) в Common Data Service с помощью обозревателя решений](create-edit-nn-relationships-solution-explorer.md)

## <a name="view-many-to-many-entity-relationships"></a>Просмотр отношений сущностей "многие-ко-многим"

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

Отношения "многие-ко-многим" будут иметь **Тип отношения** **Многие-ко-многим**.

> [!NOTE]
> Просматриваемая сущность может не иметь отношений **Многие-ко-многим**.

## <a name="create-relationships"></a>Создание отношений

Во время [просмотра отношений сущности](#view-many-to-many-entity-relationships) на панели команд выберите **Добавить отношение** и выберите **Многие-ко-многим**.

![Выбор типа отношения](media/add-relationship-menu-portal.png)

На панели **Многие-ко-многим** выберите сущность, которую необходимо связать с текущей сущностью.

![Панель "многие-ко-многим" с выбранной сущностью организации](media/many-to-many-panel-1.png)

Выберите **Дополнительно** для просмотра полей **Имя отношения** и **Имя сущности отношения**.

![Панель "многие-ко-многим" с выбранным пунктом "Дополнительно"](media/many-to-many-panel-2.png)

Значения в этих полях создаются для вас на основе выбранных сущностей.

> [!NOTE]
> Если создается несколько отношений **Многие ко многим** с одинаковыми сущностями, нужно будет изменить создаваемые поля **Имя отношения** и **Имя сущности отношения**, чтобы они стали уникальными.

Выберите **ОК**, чтобы закрыть панель **Многие-ко-многим**. Будет создано отношение при сохранении изменений сущности. 

После сохранения ничего нельзя изменить с помощью [портала PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). Для редактирования свойств отношения для управляемых моделью приложений используйте [обозреватель решений](create-edit-nn-relationships-solution-explorer.md).

## <a name="delete-relationships"></a>Удаление отношений

Во время [просмотра отношений сущности](#view-many-to-many-entity-relationships) выберите отношение, которое следует удалить.

![Удаление отношения сущностей](media/delete-entity-relationship-portal.png)

Можно использовать команду **Удалить отношение** с панели команд или из контекстного меню строки при выборе многоточия (**...**).

При удалении отношения "многие ко многим" будет удалена созданная сущность отношения. Все данные, соединяющие сущности с помощью отношения, будут утрачены.

### <a name="see-also"></a>См. также

[Обзор создания отношений сущностей N:N (многие-ко-многим)](create-edit-nn-relationships.md)<br />
[Создание отношений сущностей N:N (многие-ко-многим) в Common Data Service с помощью обозревателя решений](create-edit-nn-relationships-solution-explorer.md)
