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
ms.openlocfilehash: 97be49797df13b82901425ae9389e85538068f5d
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74726220"
---
# <a name="add-an-app-to-microsoft-teams"></a>Добавление приложения в Microsoft Teams

Microsoft Teams — это платформа для совместной работы на основе чата, использующая технологии Office 365. Вы можете настроить работу в Teams, добавив приложения Power Apps на основе холста в каналы Teams. В этом разделе вы узнаете, как добавить пример приложения Product Showcase в канал Teams, а затем открыть приложение из канала. 

![Приложение, внедренное в Microsoft Teams](./media/open-app-embedded-in-teams/embedded-app.png)

Если вы не зарегистрированы в Power Apps, перед началом работы [пройдите бесплатную регистрацию](https://make.powerapps.com/signup?redirect=marketing&email=).

## <a name="prerequisites"></a>Предварительные требования

Для выполнения этой процедуры требуется [подписка на Office 365](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1) и [канал в Teams](https://www.youtube.com/watch?v=he2f1quaR7M).

## <a name="sign-in-to-power-apps"></a>Вход в Power Apps

Войдите в Power Apps по адресу [https://make.powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

## <a name="add-an-app"></a>Добавить приложение

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
* Поддерживаются только следующие форматы звука: AAC, H264, OGG Vorbis и WAV.

## <a name="clean-up-resources"></a>Очистка ресурсов

Чтобы удалить приложение из канала, на вкладке **Product Showcase** нажмите кнопку **Удалить**.

## <a name="next-steps"></a>Дальнейшие действия

В этом разделе вы добавили пример приложения Product Showcase в канал Teams, а затем открыли приложение из канала. Чтобы узнать больше о Power Apps, изучите следующие учебники.

> [!div class="nextstepaction"]
> [Учебники по Power Apps](../maker/canvas-apps/get-started-create-from-blank.md)
