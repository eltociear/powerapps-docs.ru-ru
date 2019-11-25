---
title: Изменение сообщений системной сущности с PowerApps | MicrosoftDocs
description: Узнайте, как редактировать сообщения системной сущности
ms.custom: ''
ms.date: 05/15/2018
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
ms.assetid: 3ccbd8de-8d6f-4058-87f7-15463667cfc6
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f90f2fc6f3a4eb0707eda9d9ce73acfc422ed5d9
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "2705418"
---
# <a name="edit-system-entity-messages"></a>Редактирование сообщений системной сущности

Отображаемое имя по умолчанию некоторых системных сущностей используется в тексте ИП и сообщениях об ошибках в Common Data Service. Если изменить отображаемое имя, следует также обновить все сообщения, в которых используется отображаемое имя по умолчанию. Например, при изменении отображаемого имени с *Организация* на *Компания*, в сообщении об ошибке по-прежнему будет отображаться старое имя.  

Нельзя изменять системные сообщения с помощью портала PowerApps, необходимо использовать обозреватель решений.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

В проводнике под сущностью, если отображается узел **Сообщения**, можно изменить определенный текст, который включает ссылки на исходное отображаемое имя сущности. 

![Сообщения сущности](../model-driven-apps/media/entity-messages.png)

Редактирование этого текста достаточно просто и понятно. Дважды щелкните сообщение, чтобы увидеть форму с тремя полями.  
  
|Поле|Описание|  
|-----------|-----------------|  
|**Отображаемая строка по умолчанию**|Показывает исходный текст.|  
|**Настраиваемая отображаемая строка**|Измените этот текст, чтобы изменить отображаемую строку.|  
|**Комментарий**|Необязательно. Включите комментарий о причине изменения и внесенных изменениях.|  
  
Часть текста сообщения может иметь местозаполнители. Эти заполнители — числа со скобками с обеих сторон. Например: `{0}`. Эти заполнители позволяют вставлять текст в сообщение. При редактировании сообщений убедитесь, что эти местозаполнители сохраняются. 

Выберите ![Сохранить](media/save-entity-icon-solution-explorer.png), чтобы сохранить изменения. Выберите **Сохранить и закрыть**, чтобы закрыть форму при сохранении.

> [!NOTE]
> Хотя пользовательский интерфейс, предоставляемый для изменения сообщений системных сущностей, включает много ссылок на имена сущностей, он не включает все из них. Для более всестороннего подхода см. раздел [Обновление локализуемого текста на базовом языке](../model-driven-apps/translate-localizable-text.md#updating-localizable-text-in-the-base-language)

## <a name="programmatically-update-entity-display-strings"></a>Программное обновление отображаемых строк сущности

Для разработчиков, которым требуется способ работать с этим в коде, отображаемые строки хранятся в сущности [DisplayString](../../developer/common-data-service/reference/entities/displaystring.md). 

Сущность `DisplayString` не содержит отображаемые строки по умолчанию. Два атрибута для этой сущности, которые содержат текст, это [CustomDisplayString](../../developer/common-data-service/reference/entities/displaystring.md#BKMK_CustomDisplayString) и [PublishedDisplayString](../../developer/common-data-service/reference/entities/displaystring.md#BKMK_PublishedDisplayString). По умолчанию эти значения атрибутов равны NULL, если только отображаемая строка не была изменена и опубликована. Значение `PublishedDisplayString` доступно только для чтения и отражает текущий опубликованный атрибут `CustomDisplayString`.
 
## <a name="see-also"></a>См. также
[Изменение сущности](edit-entities.md)<br />
[Перевод локализуемого текста для управляемых моделью приложений](../model-driven-apps/translate-localizable-text.md)
