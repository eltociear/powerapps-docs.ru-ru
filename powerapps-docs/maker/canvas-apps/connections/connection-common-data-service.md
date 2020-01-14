---
title: Подключение к Common Data Service | Документация Майкрософт
description: Узнайте, как подключиться к Common Data Service и использовать его для создания приложений в Power Apps.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: ''
ms.date: 11/27/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e2b11b536c29a31053353f3c2616a594208e8acf
ms.sourcegitcommit: 54d52a9c3c9242f95be54f4444054d9c41ed577c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2020
ms.locfileid: "75928900"
---
# <a name="connect-to-common-data-service"></a>Подключение к Common Data Service

Вы можете безопасно хранить бизнес-данные в Common Data Service и создавать полнофункциональные приложения в Power Apps, чтобы пользователи могли управлять этими данными. Эти данные также можно интегрировать в решения, включающие Power автоматизиру, Power BI и данные из Dynamics 365.

По умолчанию соединитель Common Data Service подключается к данным в текущей среде приложения. Если приложение перемещается в другую среду, соединитель подключается к данным в новой среде. Это поведение хорошо подходит для приложения, использующего единую среду или приложение, которое следует процессу ALM для перехода от разработки к рабочей среде.

При добавлении источника данных с помощью соединителя Common Data Service можно изменить среду, а затем выбрать одну или несколько сущностей. По умолчанию приложение подключается к данным в текущей среде.

![Окружение по умолчанию](media/connection-common-data-service/common-data-service-connection-change-environment.png)

При выборе **изменить**можно указать другую среду для извлечения данных из нее, а не в текущую среду или в дополнение к текущей среде.

![Другие среды](media/connection-common-data-service/common-data-service-connection-select-environment.png)

Имя выбранной среды отображается в списке сущности.

![Новые среды](media/connection-common-data-service/common-data-service-connection-after-change-environment.png)

Соединитель Common Data Service является более надежным, чем соединитель Dynamics 365 и приближается к сравнению функций.

Дополнительные сведения: [что такое Common Data Service?](../../common-data-service/data-platform-intro.md)
