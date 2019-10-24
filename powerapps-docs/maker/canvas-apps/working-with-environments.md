---
title: Работа со средами | Документация Майкрософт
description: Переключение сред и понимание механизма изменения содержимого на ваших страницах.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/14/2016
ms.author: litran
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d7783113c7102d9c8b292d0ee84d4329709eeaa7
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2019
ms.locfileid: "71705238"
---
# <a name="working-with-environments-and-microsoft-powerapps"></a>Работа со средами и Microsoft PowerApps
С помощью PowerApps можно работать в различных средах и легко переключаться между ними. Общие сведения о средах см. в [обзоре сред](../../administrator/environments-overview.md), в котором подробно объясняется, для чего предназначены среды, а также рассматриваются способы создания и управления ими. В этой статье будут рассмотрены следующие темы, касающиеся сред:

- как переключать среды на сайте powerapps.com;
- Создание приложения в правой среде
- как просматривать приложения в правильной среде.

## <a name="switch-the-environment"></a>Переключение сред
При регистрации и первом входе в PowerApps он открывается в среде по умолчанию, которую можно найти в правом верхнем углу страницы.

> [!div class="mx-imgBorder"]
> ![Default ](./media/working-with-environments/env-dropdown.png) среды

Все пользователи в организации могут получить доступ к среде по умолчанию. Вы можете создавать приложения в этой среде и совместно использовать приложения с другими пользователями. У вас также может быть доступ к другим средам, будь [то их создание](../../administrator/environments-administration.md) или другие. Можно переключить среду, открыв список сред в правом верхнем углу и выбрав другую среду. В этом примере показано переключение с **Майкрософт** на **мйовненв**.

> [!div class="mx-imgBorder"]
> ![Switch ](./media/working-with-environments/switch-environment.png) среды

После переключения сред в новой среде отобразятся все приложения, к которым у вас есть доступ в этой среде.

## <a name="create-apps-in-the-right-environment"></a>Создание приложений в правильной среде
Приложения можно разрабатывать в создаваемой среде или в среде, к которой вам предоставлен доступ. Однако создание собственной среды требует [определенного плана](../../administrator/pricing-billing-skus.md). Перед созданием приложения **необходимо выбрать среду, в которой оно будет создано**. В противном случае придется перемещать приложения между средами.

Чтобы создать приложение в правой среде, сделайте следующее:

1. [Войдите в PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

1. Как описано в предыдущем разделе, выберите среду, в которой вы хотите создать приложение.

1. Выберите **приложения** рядом с левым ребром, а затем выберите **создать приложение**.

## <a name="view-apps-in-the-right-environment"></a>Просмотр приложений в правильной среде
При работе с веб-сайтом [powerapps.com](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) или PowerApps Studio отображаемый список приложений, подключений и пр. всегда фильтруется с учетом среды, выбранной в раскрывающемся списке. Если вы не видите нужные приложения, всегда проверяя, выбрана ли нужная среда.

Дополнительные сведения о средах см. в [этом обзоре](../../administrator/environments-overview.md).
