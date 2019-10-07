---
title: Подключение к Common Data Service | Документация Майкрософт
description: Узнайте, как подключиться к Common Data Service и использовать его для создания приложений в PowerApps.
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
ms.openlocfilehash: fcadc4d214494380f50f712e453554d41d08eabe
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "71994007"
---
# <a name="connect-to-common-data-service"></a>Подключение к Common Data Service

Вы можете безопасно хранить бизнес-данные в Common Data Service и создавать многофункциональные приложения в PowerApps, чтобы пользователи могли управлять этими данными. Эти данные также можно интегрировать в решения, включающие Microsoft Flow, Power BI и данные из Dynamics 365.

По умолчанию соединитель Common Data Service подключается к данным в текущей среде приложения. Если приложение перемещается в другую среду, соединитель подключается к данным в новой среде. Это поведение хорошо подходит для приложения, использующего единую среду или приложение, которое следует процессу ALM для перехода от разработки к рабочей среде.

При добавлении источника данных с помощью соединителя Common Data Service можно изменить среду, а затем выбрать одну или несколько сущностей. По умолчанию приложение подключается к данным в текущей среде, а пользовательский интерфейс показывает **(текущий)** список сущностей.

> [!div class="mx-imgBorder"]
> среда @no__t 0Default @ no__t-1

При выборе **изменить**можно указать другую среду для извлечения данных из нее, а не в текущую среду или в дополнение к текущей среде.

> [!div class="mx-imgBorder"]
> @no__t среды 0Other @ no__t-1

Имя выбранной среды отображается под полем поиска.

> [!div class="mx-imgBorder"]
> @no__t среды 0New @ no__t-1

Соединитель Common Data Service является более надежным, чем соединитель Dynamics 365 и приближается к сравнению функций.

Дополнительные сведения: [Что такое Common Data Service?](../../common-data-service/data-platform-intro.md)
