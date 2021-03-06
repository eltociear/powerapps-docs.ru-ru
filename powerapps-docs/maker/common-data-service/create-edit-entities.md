---
title: Создание и изменение сущностей в Common Data Service | MicrosoftDocs
description: Инструкции по созданию и изменению сущностей
ms.custom: ''
ms.date: 04/16/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
author: Mattp123
ms.assetid: fa04f99d-a5f9-48cb-8bfb-f0f50718ccee
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d700c76009f45c4e28f78732e7ae52ab57693ccb
ms.sourcegitcommit: 2b34de88c977c149e4c632b23d8e816901c15949
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2020
ms.locfileid: "3040531"
---
# <a name="create-and-edit-entities-in-common-data-service"></a>Создание и изменение сущностей в Common Data Service

Прежде чем создать пользовательскую сущность, оцените, соответствует ли существующая сущность вашим требованиям. Дополнительные сведения: [Создание новых или использование существующих метаданных](create-edit-metadata.md#create-new-metadata-or-use-existing-metadata)

Имеется два конструктора, которые можно использовать для создания сущности:

|Дизайнер| Описание|
|--|--|
|[портал Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|Обеспечивает простое модернизированное взаимодействие, но некоторые специальные параметры недоступны.<br />Дополнительные сведения: <br />[Учебник. Создание настраиваемой сущности с компонентами в Power Apps](/powerapps/maker/common-data-service/create-custom-entity)<br />[Создание и изменение сущностей с помощью портала Power Apps](create-edit-entities-portal.md)|
|Обозреватель решений|Не так прост, но предоставляет больше гибкости для менее распространенных требований. <br />Дополнительные сведения: [Создание и изменение сущностей с помощью обозревателя решений](create-edit-entities-solution-explorer.md)|

> [!NOTE]
> Можно также создать сущности в среде с помощью следующих действий.
> - Импорт решения, которое содержит определение сущности.
> - Используйте Power Query для создания новых сущностей и из заполнения данными. Дополнительные сведения: [Добавление данных в сущность в Common Data Service с помощью Power Query](/powerapps/maker/common-data-service/data-platform-cds-newentity-pq).
> - Разработчик может использовать [службы метаданных](/powerapps/developer/common-data-service/use-web-services#metadata-services) для написания программы.

## <a name="entity-options-not-available-in-the-power-apps-portal"></a>Параметры сущностей, недоступные на портале Power Apps

Информация в этом разделе поможет вам выбрать конструктор для использования. Можно использовать портал Power Apps для создания сущности, если только вам не нужно выполнить любое из следующих требований.

- Управление префиксом настройки

  Часть имени любой создаваемой настраиваемой сущности — это префикс настройки. Это настраивается с использованием издателя решений для решения, в котором выполняется работа. Если важен префикс настройки, убедитесь, что вы работаете с неуправляемым решением, префикс настройки в котором — тот, который нужен для данной сущности. Дополнительные сведения: [Изменение префикса издателя решения](change-solution-publisher-prefix.md).

- Изменение значков настраиваемой сущности

  По умолчанию все настраиваемые сущности в управляемых моделью приложениях имеют одни и те же значки. Можно создать веб-ресурсы изображений для значков, требуемых для настраиваемых сущностей. Дополнительные сведения: [Изменение значков настраиваемых сущностей](../model-driven-apps/change-custom-entity-icons.md). 

- Измените любые из следующих свойств, которые могут быть только включены:

  [!INCLUDE [cc_entity-set-once-options-table](../../includes/cc_entity-set-once-options-table.md)]

- Измените любые из следующих свойств:

  |Параметр   |Описание  |
  |---------|---------|
  |**Области для отображения сущности**|В веб-приложении выберите одну из доступных областей карты сайта для отображения этой сущности. Это не относится к управляемым моделью приложениям.|
  |**Аудит**|Если аудит включен для вашей организации, можно с течением времени фиксировать изменения в записях сущностей. При включении аудита для сущности аудит также включается во всех ее полях. Можно выделить или отменить выделение полей, для которых требуется включить аудит.|
  |**Цвет**|Задайте цвет, который будет использоваться для сущности в управляемых моделью приложениях.|
  |**Управление документами**|После того как были выполнены другие задачи для включения управления документами для организации, включение этой функции позволит сущности участвовать в интеграции с SharePoint. |
  |**Включить для мобильных устройств**|Сделайте эту сущность доступной для приложений Dynamics 365 for phones и tablets. Также можно сделать эту сущность **Доступно только для чтения в мобильном**.<br /><br /> Если формы для сущности требуют расширение, не поддерживаемое в Dynamics 365 for phones и tablets, воспользуйтесь этим параметром, чтобы предотвратить изменение данных в этих сущностях пользователями мобильных приложений.|
  |**Включить для phone express**|Сделайте эту сущность доступной для приложения Dynamics 365 for phones.|
  |**Область чтения в Dynamics 365 for Outlook**|Будет ли сущность видна в области чтения для приложения Dynamics 365 for Outlook.|
  |**Использовать настраиваемую справку**|Когда эта функция включена, можно указать URL-адрес справки для управления тем, какие страницы будут видеть пользователи при нажатии кнопки справки в приложении. Это используется для предоставления инструкций, характерных для процессов вашей компании для сущности.|


### <a name="see-also"></a>См. также

[Создание и изменение сущностей с помощью обозревателя решений](create-edit-entities-solution-explorer.md)<br />
[Учебник. Создание настраиваемой сущности с компонентами в Power Apps](/powerapps/maker/common-data-service/create-custom-entity)<br />
[Изменение сущности](edit-entities.md)<br />
[Документация для разработчиков. Создание настраиваемой сущности](/dynamics365/customer-engagement/developer/org-service/create-custom-entity)
