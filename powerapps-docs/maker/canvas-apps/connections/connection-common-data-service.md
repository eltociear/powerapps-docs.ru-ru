---
title: Подключение к Common Data Service | Документация Майкрософт
description: Узнайте, как подключиться к Common Data Service и использовать его для создания приложений в Power Apps.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: ''
ms.date: 04/22/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2473f445839b774ecc28fe007912511095d9316d
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74723832"
---
# <a name="connect-to-common-data-service"></a>Подключение к Common Data Service

Вы можете безопасно хранить бизнес-данные в Common Data Service и создавать полнофункциональные приложения в Power Apps, чтобы пользователи могли управлять этими данными. Эти данные также можно интегрировать в решения, включающие Power автоматизиру, Power BI и данные из Dynamics 365.

По умолчанию соединитель Common Data Service подключается к данным в текущей среде приложения. Если приложение перемещается в другую среду, соединитель подключается к данным в новой среде. Это поведение хорошо подходит для приложения, использующего единую среду или приложение, которое следует процессу ALM для перехода от разработки к рабочей среде.

При добавлении источника данных с помощью соединителя Common Data Service можно изменить среду, а затем выбрать одну или несколько сущностей. По умолчанию приложение подключается к данным в текущей среде, а пользовательский интерфейс показывает **(текущий)** список сущностей.

> [!div class="mx-imgBorder"]
> ![среды по умолчанию](media/connection-common-data-service/common-data-service-connection-change-environment.png)

При выборе **изменить**можно указать другую среду для извлечения данных из нее, а не в текущую среду или в дополнение к текущей среде.

> [!div class="mx-imgBorder"]
> ![других окружений](media/connection-common-data-service/common-data-service-connection-select-environment.png)

Имя выбранной среды отображается под полем поиска.

> [!div class="mx-imgBorder"]
> ![новых окружений](media/connection-common-data-service/common-data-service-connection-after-change-environment.png)

Соединитель Common Data Service является более надежным, чем соединитель Dynamics 365 и приближается к сравнению функций.

Дополнительные сведения: [что такое Common Data Service?](../../common-data-service/data-platform-intro.md)
