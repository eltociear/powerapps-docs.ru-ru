---
title: Подключение к Common Data Service | Документация Майкрософт
description: Узнайте, как подключиться к Common Data Service и использовать его для создания приложений в Power Apps.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/04/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 227482b383acd3117cc78eddf97698ffa9146698
ms.sourcegitcommit: 56c8c7cc64695ccb00e0d021c9f98cf70b69b4a2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2020
ms.locfileid: "78845199"
---
# <a name="connect-to-common-data-service"></a>Подключение к Common Data Service

## <a name="overview"></a>Обзор

Вы можете безопасно хранить бизнес-данные в Common Data Service и создавать полнофункциональные приложения в Power Apps, чтобы пользователи могли управлять этими данными. Эти данные также можно интегрировать в решения, включающие Power автоматизиру, Power BI и данные из Dynamics 365.

По умолчанию соединитель Common Data Service подключается к данным в текущей среде приложения. Если приложение перемещается в другую среду, соединитель подключается к данным в новой среде. Это поведение хорошо подходит для приложения, использующего единую среду или приложение, которое следует процессу ALM для перехода от разработки к рабочей среде.

При добавлении источника данных с помощью соединителя Common Data Service можно изменить среду, а затем выбрать одну или несколько сущностей. По умолчанию приложение подключается к данным в текущей среде.

![Окружение по умолчанию](media/connection-common-data-service/common-data-service-connection-change-environment.png)

При выборе **изменить**можно указать другую среду для извлечения данных из нее, а не в текущую среду или в дополнение к текущей среде.

![Другие среды](media/connection-common-data-service/common-data-service-connection-select-environment.png)

Имя выбранной среды отображается в списке сущности.

![Новые среды](media/connection-common-data-service/common-data-service-connection-after-change-environment.png)

Соединитель Common Data Service является более надежным, чем соединитель Dynamics 365 и приближается к сравнению функций.

### <a name="common-data-service-and-the-improved-data-source-experience"></a>Common Data Service и Улучшенный интерфейс источников данных

Если вы создали приложение Canvas с соединителем Common Data Service до 2019 ноября, возможно, у вас не будет преимуществ последней версии Common Data Service. Дополнительные сведения и обновление подключения см. в статье [улучшения подключения Common Data Service](../use-native-cds-connector.md) .