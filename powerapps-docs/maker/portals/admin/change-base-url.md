---
title: Изменение базового URL-адреса портала | MicrosoftDocs
description: Узнайте, как изменить базовый URL-адрес портала.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: cfc2fd0ca753aebfe7bc77b73c7e7ec1ca011387
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977480"
---
# <a name="change-the-base-url-of-a-portal"></a>Изменение базового URL-адреса портала

Вы можете изменить базовый URL-адрес портала после его подготовки. Например, если выбрать `contosocommunity.microsoftcrmportals.com` в качестве базового URL-адреса при подготовке портала, позднее можно изменить его на `contosocommunityportal.microsoftcrmportals.com` в соответствии с вашими требованиями.

> [!NOTE]
> После изменения базового URL-адреса портала старый URL-адрес больше не будет доступен, и он станет доступен другим клиентам для использования на своих порталах.

1.  Откройте [центр администрирования порталов PowerApps](admin-overview.md).

2.  Перейдите к **действиям портала** > **изменить базовый URL-адрес**. 

    > [!div class=mx-imgBorder]
    > ![Изменить базовый URL-адрес портала](../media/change-base-url-action.png "изменить базовый URL-адрес портала")

3.  В окне изменить базовый URL-адрес введите новый базовый URL-адрес портала.

    > [!div class=mx-imgBorder]
    > ![Укажите новый базовый URL-адрес портала](../media/change-base-url.png "укажите новый базовый URL-адрес портала")

4.  В окне подтверждения выберите **изменить URL-адрес** .

## <a name="troubleshooting"></a>Устранение неполадок

В этом разделе содержатся сведения об устранении неполадок, возникающих при изменении базового URL-адреса портала.

### <a name="changing-the-base-url-fails"></a>Не удается изменить базовый URL-адрес

Если изменить базовый URL-адрес портала не удается, отображается сообщение об ошибке, как показано на следующем рисунке:

> [!div class=mx-imgBorder]
> ![Ошибка при изменении базового URL-адреса портала](../media/change-base-url-error.png "при изменении базового URL-адреса портала")

Как правило, это временные ошибки, поэтому необходимо выбрать **изменить базовый URL-адрес** , чтобы повторить попытку изменения базового URL-адреса. Если проблема будет повторяться, обратитесь в службу поддержки Майкрософт.
