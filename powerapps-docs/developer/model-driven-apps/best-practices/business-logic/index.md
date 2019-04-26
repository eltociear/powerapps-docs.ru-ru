---
title: 'Для разработчиков: рекомендации по написанию скриптов на стороне клиента для приложений на основе модели | Документация Майкрософт'
description: Рекомендации для разработчиков по написанию скриптов на стороне клиента для приложений на основе модели в PowerApps.
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/12/2018
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e2b43178882cb66abba2305f65f78855915591ed
ms.sourcegitcommit: 4ed29d83e90a2ecbb2f5e9ec5578e47a293a55ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63317676"
---
# <a name="best-practices-and-guidance-of-client-side-scripting-for-model-driven-apps"></a>Рекомендации по написанию скриптов на стороне клиента для приложений на основе модели

В списке ниже приводятся все рекомендации по написанию скриптов на стороне клиента для приложений на основе модели.

|Рекомендация  |Описание  |
|---------|---------|
|[Избегайте использовать window.top](avoid-window-top.md)     |Описывается, как избежать ошибок в скриптах и неполадок в работе приложений, связанных с использованием window.top в настройках JavaScript.         |
|[Рекомендуется отключить панель навигации при открытии форм сущностей или представлений с помощью программных средств](consider-disabling-navbar-programmatically-opening-entity-forms-views.md)|Если для открытия форм сущностей или представлений используется URL-адрес, в сетях с высокой задержкой может ухудшиться производительность клиента при включенной панели навигации.|
|[Рекомендации: клиентские скрипты в приложениях на основе модели](../../clientapi/client-scripting-best-practices.md)     |Ряд советов, которые могут быть полезны при написании кода JavaScript для приложений на основе модели.         |
|[Используйте асинхронное взаимодействие с ресурсами HTTP и HTTPS](interact-http-https-resources-asynchronously.md)     |При написании клиентских расширений JavaScript для приложений на основе модели следует взаимодействовать с ресурсами HTTP и HTTPS в асинхронном режиме.         |
|[Удалите отключенные настройки](remove-deactivated-disabled-configurations.md)     |Отключенные настройки следует удалить из решения, чтобы упростить управление им и снизить риск использования устаревших компонентов.         |

# <a name="see-also"></a>См. также
[Применение бизнес-логики с помощью клиентских скриптов](../../client-scripting.md) <br />
 