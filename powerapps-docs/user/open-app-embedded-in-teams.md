---
title: Добавление приложения в Microsoft Teams | Документы Майкрософт
description: Узнайте, как добавить приложение в канал Microsoft Teams, чтобы любой пользователь, которому был предоставлен общий доступ к этому приложению, мог открыть его в данном канале.
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 11/16/2018
ms.author: mduelae
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 62a7166f228545f2a200570186ee23c868650b79
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543494"
---
# <a name="add-an-app-to-microsoft-teams"></a>Добавление приложения в Microsoft Teams

Microsoft Teams — это платформа для совместной работы на основе чата, использующая технологии Office 365. Вы можете настроить работу в Teams, добавив приложения PowerApps на основе холста в каналы Teams. В этом разделе вы узнаете, как добавить пример приложения Product Showcase в канал Teams, а затем открыть приложение из канала. 

![Приложение, внедренное в Microsoft Teams](./media/open-app-embedded-in-teams/embedded-app.png)

Если вы не зарегистрированы в PowerApps, перед началом работы [пройдите бесплатную регистрацию](https://make.powerapps.com/signup?redirect=marketing&email=).

## <a name="prerequisites"></a>Технические условия

Для выполнения этой процедуры требуется [подписка на Office 365](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1) и [канал в Teams](https://www.youtube.com/watch?v=he2f1quaR7M).

## <a name="sign-in-to-powerapps"></a>Вход в PowerApps

Войдите в PowerApps по адресу [https://make.powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

## <a name="add-an-app"></a>Добавление приложения

1. В Microsoft Teams выберите команду и канал в ней. В этом примере используется канал **Общее** в команде **Развитие бизнеса**.

    ![](./media/open-app-embedded-in-teams/teams-select-channel.png)

2. Нажмите кнопку **+** , чтобы добавить вкладку.

    ![](./media/open-app-embedded-in-teams/teams-add-tab.png)

3. В диалоговом окне **Добавление вкладки** выберите **PowerApps**.

    ![](./media/open-app-embedded-in-teams/add-a-tab.png)

4. Последовательно выберите **Примеры приложений** > **Product Showcase** > **Сохранить**.

    ![](./media/open-app-embedded-in-teams/select-an-app.png)

    Теперь приложение можно использовать в канале.

    ![](./media/open-app-embedded-in-teams/app-in-channel.png)

> [!NOTE]
> Перед добавлением собственных приложений в Teams необходимо предоставить [общий доступ](../maker/canvas-apps/share-app.md) к ним (доступ к примерам приложений предоставляется по умолчанию).

## <a name="open-an-app"></a>Запуск приложения

1. В Microsoft Teams выберите команду и канал, который содержит приложение.

    ![](./media/open-app-embedded-in-teams/teams-select-channel.png)

2. Перейдите на вкладку **Product Showcase**.

    ![](./media/open-app-embedded-in-teams/open-tab.png)

    Приложение откроется в канале.

    ![](./media/open-app-embedded-in-teams/app-in-channel.png)

## <a name="known-issues"></a>Известные проблемы

В классическом приложении для Microsoft Teams:

* Приложения должны загружать содержимое, такое как изображения и PDF-файлы, через защищенное подключение (HTTPS).
* Поддерживаются не все датчики, в том числе **Ускорение**, **Компас** и **Расположение**.
* Поддерживаются только эти звуковые форматы: AAC, H264, OGG Vorbis и WAV.

## <a name="clean-up-resources"></a>Очистка ресурсов

Чтобы удалить приложение из канала, на вкладке **Product Showcase** нажмите кнопку **Удалить**.

## <a name="next-steps"></a>Дальнейшие действия

В этом разделе вы добавили пример приложения Product Showcase в канал Teams, а затем открыли приложение из канала. Чтобы узнать больше о PowerApps, перейдите к следующим учебникам.

> [!div class="nextstepaction"]
> [Учебники по PowerApps](../maker/canvas-apps/get-started-create-from-blank.md)
