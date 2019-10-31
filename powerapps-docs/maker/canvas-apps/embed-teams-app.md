---
title: Внедрение приложения в группы | Документация Майкрософт
description: Вы можете внедрить приложение, созданное в PowerApps в Microsoft Teams, чтобы поделиться им.
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/29/2019
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 42075fbaee40ec98bec0d47e6bfd3c00dc6f9ef6
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2019
ms.locfileid: "73182484"
---
# <a name="embed-an-app-in-teams"></a>Внедрение приложения в группы

Вы можете поделиться созданной вами PowerApps, внедрив ее непосредственно в Microsoft Teams. По завершении пользователи могут выбрать **+** , чтобы добавить приложение в любой канал **команды или** беседы в группе, в которой вы являетесь. Приложение отображается в виде плитки в разделе **вкладок команды**.

Администратор может отправить приложение, чтобы оно выводилось для **всех** команд в вашем клиенте в **разделе все вкладки**. См. раздел [совместное использование приложения в Microsoft Teams](https://docs.microsoft.com/power-platform/admin/embed-app-teams).

> [!NOTE]
> Политики настраиваемых приложений команды должны быть настроены, чтобы разрешить отправку пользовательских приложений. Если вы не можете внедрить приложение в группы, обратитесь к администратору, чтобы узнать, не настроены ли [Параметры настраиваемого приложения](https://docs.microsoft.com/MicrosoftTeams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings).

## <a name="prerequisites"></a>Технические условия

- Требуется действительная [Лицензия PowerApps](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus).
- Чтобы внедрить приложение в команды, вам потребуется существующее приложение, [созданное с помощью PowerApps](data-platform-create-app.md).

## <a name="download-the-app"></a>Скачать приложение

1. Войдите в [Web.powerapps.com](https://web.powerapps.com)и выберите **приложения** в меню.

    ![Отобразить список приложений](./media/embed-teams-app/file-apps2.png "Открытие списка приложений")

2. Выберите **Дополнительные действия** (...) для приложения, которое вы хотите использовать в командах, а затем выберите **Добавить в группы**.

    ![Сведения о приложении](./media/embed-teams-app/add-to-teams.png "Добавить в команды")

3. На панели добавить в команды выберите **скачать**. Затем PowerApps создаст файл манифеста команд, используя описание приложения и логотип, которые вы уже задали в своем приложении.

    ![Сведения о приложении](./media/embed-teams-app/download-app.png "Скачать приложение")

## <a name="add-the-app-as-a-personal-app"></a>Добавление приложения в качестве личного приложения

1. Чтобы добавить приложение в качестве личного приложения или вкладки для любого канала или диалога, выберите **приложения** в левой области навигации, а затем выберите **Отправить пользовательское приложение**.

    > [!NOTE]
    > Команда **Отправить пользовательское приложение** отображается только в том случае, если администратор команд создал [пользовательскую политику приложений](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies) и включил параметр **Разрешить передачу пользовательских приложений**.

    ![Добавить вкладку "приложение как"](./media/embed-teams-app/upload-custom-app.png "Отправка пользовательского приложения")

2. Выберите **Добавить** , чтобы добавить приложение в качестве личного приложения, или выберите **Добавить в группу** , чтобы добавить приложение в качестве вкладки в существующий канал или беседу.

## <a name="publish-the-app-to-the-teams-catalogue"></a>Публикация приложения в каталоге команд

Если вы являетесь администратором, вы также можете [опубликовать приложение](https://docs.microsoft.com/microsoftteams/tenant-apps-catalog-teams) в каталоге Microsoft Teams.

### <a name="see-also"></a>См. также

[Добро пожаловать в Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/teams-overview)
