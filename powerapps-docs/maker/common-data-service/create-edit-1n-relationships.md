---
title: Создание отношений сущностей 1:N (один-ко-многим) или N:1 (многие-к-одному) в обзоре Power Apps | MicrosoftDocs
description: Узнайте, как создавать отношения сущностей "один-ко-многим" или "многие-к-одному".
ms.custom: ''
ms.date: 05/27/2018
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
ms.assetid: 52c00707-b2bc-4950-abec-89baefd94f6e
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 07e173dff08a10de5354c08d3530605f530e512d
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2019
ms.locfileid: "2866150"
---
# <a name="create-one-to-many-or-many-to-one-entity-relationships-overview"></a>Создание отношений сущностей "один-ко-многим" или "многие-к-одному" с помощью обзора

В Common Data Service отношения 1:N (один-ко-многим) или N:1 (многие-к-одному) определяют, как две сущности связаны друг с другом. 
  
Прежде чем создать настраиваемое отношение сущностей, оцените, соответствует ли существующее отношение сущностей вашим требованиям. <br />Дополнительные сведения: [Создание новых или использование существующих метаданных](create-edit-metadata.md#create-new-metadata-or-use-existing-metadata)

Существует два конструктора, которые можно использовать для создания и изменения отношений 1:N (один-ко-многим) или N:1 (многие-к-одному):

|Дизайнер| Описание|
|--|--|
|[портал Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|Обеспечивает простое модернизированное взаимодействие, но некоторые специальные параметры недоступны.<br />Дополнительные сведения: [Создание и изменение отношений сущностей 1:N (один-ко-многим) или N:1 (многие-к-одному) на портале Power Apps](create-edit-1n-relationships-portal.md)|
|Обозреватель решений|Не так прост, но предоставляет больше гибкости для менее распространенных требований. <br />Дополнительные сведения: [Создание и изменение отношений сущностей 1:N (один-ко-многим) или N:1 (многие-к-одному) с помощью обозревателя решений](create-edit-1n-relationships-solution-explorer.md) |

> [!NOTE]
> Можно также создать новое отношение сущностей в среде, используя следующее:
> - В управляемых моделью приложениях выберите **Создать поле** в редакторе форм и создайте поле *Поиск*. <br />Дополнительные сведения: [Добавление поля в форму](../model-driven-apps/add-field-form.md)
> - Создайте новое поле "Поиск" для связанной сущности. <br />Дополнительные сведения: [Создание и изменение полей](create-edit-fields.md)
> - Импорт решения, которое содержит определение отношения сущностей. <br />Дополнительные сведения: [Импорт, обновление и экспорт решений](import-update-export-solutions.md)
> - Используйте Power Query для создания новых сущностей и из заполнения данными. <br />Дополнительные сведения: [Добавление данных в сущность в Common Data Service с помощью Power Query](data-platform-cds-newentity-pq.md).
> - Разработчик может использовать [службы метаданных](../../developer/common-data-service/metadata-services.md), чтобы создать программу для создания и обновления отношений между сущностями. <br />Дополнительные сведения: [Настройка метаданных отношений между сущностями](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)

Информация в этом разделе поможет вам выбрать конструктор для использования. 

Следует использовать портал Power Apps для создания и редактирования отношений сущностей 1:N (один-ко-многим) или N:1 (многие-к-одному) кроме случаев, когда необходимо выполнить любое из следующих требований:

- Настройка сопоставлений полей
- Настройка параметров области навигации для управляемого моделью приложения
- Настройка поведения отношений
- Определите, будет ли отношение скрыто в расширенном поиске.
- Создание иерархического отношения


## <a name="community-tools"></a>Средства сообщества

**[Создатель диаграмм отношений сущностей](https://www.xrmtoolbox.com/plugins/JourneyIntoCRM.XrmToolbox.ERDPlugin/)** — это средство, разработанное сообществом XrmToolbox для Common Data Service. Дополнительные средства разработки от сообщества см. в разделе [Средства разработчика для Common Data Service](https://docs.microsoft.com/dynamics365/customer-engagement/developer/developer-tools).

> [!NOTE]
> Средства сообществ не являются продуктом корпорации Майкрософт, и на них не распространяется поддержка. При наличии вопросов по средству обращайтесь к его издателю. Дополнительные сведения: [XrmToolBox](https://www.xrmtoolbox.com).

### <a name="see-also"></a>См. также

[Создание и изменение отношений между сущностями](create-edit-entity-relationships.md)<br />
[Создание и изменение отношений сущностей 1:N (один-ко-многим) или N:1 (многие-к-одному) на портале Power Apps](create-edit-1n-relationships-portal.md)<br />
[Создание и изменение отношений сущностей 1:N (один-ко-многим) или N:1 (многие-к-одному) с помощью обозревателя решений](create-edit-1n-relationships-solution-explorer.md)<br />
[Документация для разработчиков. Настройка метаданных отношений между сущностями](/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)<br />
[Документация для разработчиков. Доступность отношений между сущностями](/dynamics365/customer-engagement/developer/entity-relationship-eligibility)


