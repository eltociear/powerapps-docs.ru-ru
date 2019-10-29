---
title: Скачать открытый ключ портала | MicrosoftDocs
description: Узнайте, как скачать открытый ключ портала.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 39e909acb325bd870f73e16a72da78b4bec07c79
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975985"
---
# <a name="download-public-key-of-portal"></a>Загрузка открытого ключа портала

Открытый ключ портала используется для настройки Live Assist для приложений, управляемых моделями в Dynamics 365, для работы с прошедших проверку подлинности посетителями портала. [Live Assist](https://www.cafex.com/en/products/live-assist-dynamics-365/), кафекс, предоставляет решение для разговора, с помощью которого пользователи могут внедрять Live Chat на портале. Дополнительные сведения об использовании открытого ключа для внедрения разговора на портале: [прошедшие проверку посетителей](https://www.liveassistfor365.com/en/support/authenticated-visitors-in-the-dynamics-customer-portal/) на портале клиента Dynamics

1. Откройте [центр администрирования порталов PowerApps](admin-overview.md).

2.  Перейдите к **действиям портала** > **получить открытый ключ**. Отобразится ключ.

    > [!div class=mx-imgBorder]
    > ![Получение открытого ключа портала](../media/get-public-key.png "получить открытый ключ портала")

3.  Выберите **скачать как текст** , чтобы скачать ключ в текстовый файл.

Кроме того, Открытый ключ можно получить, перейдя по URL-адресу: `<portal_base_URL>/_ services/auth/publickey` 

> [!NOTE]
> Если на портале в настоящее время выполняется подготовка или установка пакета не завершена в Организации, при попытке скачать открытый ключ отображается сообщение об ошибке. Необходимо дождаться завершения подготовки портала и запуска портала.
