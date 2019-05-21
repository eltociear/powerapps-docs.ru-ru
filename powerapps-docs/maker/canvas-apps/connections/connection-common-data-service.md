---
title: Подключение к Common Data Service | Документация Майкрософт
description: Узнайте, как подключиться к службе Common Data Service и использовать его для создания приложений в PowerApps.
author: aftowen
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: ''
ms.date: 04/22/2019
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ede2736711fbb79250e1ca4b8e735f7fbd19b78d
ms.sourcegitcommit: be110258910aa097b0065da1ee4ea1c40b7e1334
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2019
ms.locfileid: "65922492"
---
# <a name="connect-to-common-data-service"></a>Подключение к Common Data Service

Можно безопасно хранить бизнес-данных в Common Data Service и создавать полнофункциональные приложения в PowerApps, чтобы пользователи могли управлять эти данные. Эти данные также можно интегрировать в решений, которые включают данные из Dynamics 365, Microsoft Flow и Power BI.

По умолчанию соединитель Common Data Service подключается к данным в отключению текущего приложения. Если ваше приложение переходит на другую среду, соединитель подключается к данным в новой среде. Это подходит для приложения с помощью одной среде или приложение, которое следует за управление жизненным циклом Приложений процесс перехода от разработки приложений для тестирования в рабочей среде.

При добавлении источника данных с помощью соединителя Common Data Service, можно изменить среду, а затем выберите одну или несколько сущностей.  По умолчанию приложение подключается к данным в текущей среде, и интерфейс пользователя показывает **(текущей)** через список сущностей. При выборе **изменение**, можно указать другую среду для извлечения данных из него вместо или в дополнение к текущей среде. 

![Среда изменения службы общих данных](media/connection-common-data-service/common-data-service-connection-change-environment.png)

Соединитель Common Data Service является более надежным, чем соединителя Dynamics 365 и размером около аналогичные функции.

Дополнительные сведения: [Что такое Common Data Service?](../../common-data-service/data-platform-intro.md)
