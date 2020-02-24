---
title: Загрузка открытого ключа портала | MicrosoftDocs
description: Научитесь загружать открытый ключ портала.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 8b74e1943e6a356884be167be033b7e633660b40
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977907"
---
# <a name="download-public-key-of-portal"></a>Загрузка открытого ключа портала

Открытый ключ портала используется для настройки работы Live Assist for приложений на основе модели в Dynamics 365 с посетителями портала, прошедшими проверку подлинности. [Live Assist](https://www.cafex.com/en/products/live-assist-dynamics-365/) от CafeX предоставляет решение чата, с помощью которого пользователи могут внедрять помощь живого чата в свой портал. Дополнительные сведения о том, как использовать открытый ключ для внедрения чата на портал: [Посетители, прошедшие проверку подлинности на портале клиентов Dynamics](https://www.liveassistfor365.com/en/support/authenticated-visitors-in-the-dynamics-customer-portal/)

1. Открытие [Центра администрирования портала Power Apps](admin-overview.md).

2.  Выберите **Действия портала** > **Получить открытый ключ**. Отображается ключ.

    > [!div class=mx-imgBorder]
    > ![Получить открытый ключ портала](../media/get-public-key.png "Получить открытый ключ портала")

3.  Выберите **Загрузить как текст** для загрузки ключа в текстовый файл.

Вместо этого можно также получить открытый ключ, перейдя по URL-адресу: `<portal_base_URL>/_ services/auth/publickey` 

> [!NOTE]
> Если портал в данный момент подготавливается или установка пакета не закончена в организации, отображается ошибка при попытке загрузить открытый ключ. Необходимо дождаться завершения подготовки портала, когда портал будет настроен и начнет работать.
