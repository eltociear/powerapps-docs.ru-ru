---
title: Работа со средами | Документация Майкрософт
description: Переключение сред и понимание механизма изменения содержимого на ваших страницах.
author: linhtranms
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/14/2016
ms.author: litran
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: eeb7a80c106541acd6ca284541fae6112b6d470c
ms.sourcegitcommit: 065b3b210273e5fe9025d41d27a08a62dfa16d03
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2019
ms.locfileid: "64904111"
---
# <a name="working-with-environments-and-microsoft-powerapps"></a>Работа со средами и Microsoft PowerApps
С помощью PowerApps можно работать в различных средах и легко переключаться между ними. Общие сведения о средах см. в [обзоре сред](../../administrator/environments-overview.md), в котором подробно объясняется, для чего предназначены среды, а также рассматриваются способы создания и управления ими. В этой статье будут рассмотрены следующие темы, касающиеся сред:

- как переключать среды на сайте powerapps.com;
- Создание приложения в правильной среде
- как просматривать приложения в правильной среде.

## <a name="switch-the-environment"></a>Переключение сред
При регистрации и первом входе в PowerApps, он открывается в среде по умолчанию, который способен выявлять в правом верхнем углу страницы.

> [!div class="mx-imgBorder"]
> ![Среда по умолчанию](./media/working-with-environments/env-dropdown.png)

Все пользователи в организации можно получить доступ к среде по умолчанию. Можно создавать приложения в этой среде и совместное использование приложений с другими пользователями. Также имеется доступ к другим средам ли [их создания](../../administrator/environments-administration.md) или другим пользователям. Для переключения сред, открыв список сред в правом верхнем углу и выбрав другую среду. В этом примере показано переключение из **Microsoft** для **MyOwnEnv**.

> [!div class="mx-imgBorder"]
> ![Переключение сред](./media/working-with-environments/switch-environment.png)

После переключения сред новой среды отображается все приложения, к которым имеется доступ, в этой среде.

## <a name="create-apps-in-the-right-environment"></a>Создание приложений в правильной среде
Приложения можно разрабатывать в создаваемой среде или в среде, к которой вам предоставлен доступ. Однако создание собственной среды требует [определенного плана](../../administrator/pricing-billing-skus.md). Перед созданием приложения **необходимо выбрать среду, в которой оно будет создано**. В противном случае придется перемещать приложения между средами.

Для создания приложения в правильной среде:

1. [Войдите в PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

1. Как описано в предыдущем разделе, выберите среду, в котором вы хотите создать приложение.

1. Выберите **приложений** возле левого края, а затем выберите **Создание приложения**.

## <a name="view-apps-in-the-right-environment"></a>Просмотр приложений в правильной среде
При работе с веб-сайтом [powerapps.com](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) или PowerApps Studio отображаемый список приложений, подключений и пр. всегда фильтруется с учетом среды, выбранной в раскрывающемся списке. Если вы не видите приложения, которые вы ищете, всегда Подтвердите ли правильной среде.

Дополнительные сведения о средах см. в [этом обзоре](../../administrator/environments-overview.md).
