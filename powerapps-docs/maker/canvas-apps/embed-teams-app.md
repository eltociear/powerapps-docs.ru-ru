---
title: Внедрение приложения в группы | Документация Майкрософт
description: Вы можете внедрить приложение, созданное в Power Apps, в Microsoft Teams, чтобы поделиться им.
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/16/2020
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 088e817c8ef829b340032af577193888079c832a
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2020
ms.locfileid: "79436822"
---
# <a name="embed-an-app-in-teams"></a>Внедрение приложения в Teams

Вы можете поделиться созданным приложением, внедрив его непосредственно в Microsoft Teams. По завершении пользователи могут выбрать **+** , чтобы добавить приложение в любой канал **команды или** беседы в группе, в которой вы являетесь. Приложение отображается в виде плитки в разделе **вкладок команды**.

Администратор может отправить приложение, чтобы оно выводилось для **всех** команд в вашем клиенте в **разделе все вкладки**. См. раздел [совместное использование приложения в Microsoft Teams](https://docs.microsoft.com/power-platform/admin/embed-app-teams).

> [!NOTE]
> Политики настраиваемых приложений команды должны быть настроены, чтобы разрешить отправку пользовательских приложений. Если вы не можете внедрить приложение в группы, обратитесь к администратору, чтобы узнать, не настроены ли [Параметры настраиваемого приложения](https://docs.microsoft.com/MicrosoftTeams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings).

## <a name="prerequisites"></a>Предварительные требования

- Вам потребуется действительная [Лицензия на Power Apps](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus).
- Чтобы внедрить приложение в команды, вам потребуется существующее приложение, [созданное с помощью Power Apps](data-platform-create-app.md).

## <a name="download-the-app"></a>Загрузите приложение

1. Войдите в [make.powerapps.com](https://make.powerapps.com)и выберите **приложения** в меню.

    ![Отобразить список приложений](./media/embed-teams-app/file-apps2.png "Открытие списка приложений")

2. Выберите **Дополнительные действия** (...) для приложения, которое вы хотите использовать в командах, а затем выберите **Добавить в группы**.

    ![Сведения о приложении](./media/embed-teams-app/add-to-teams.png "Добавить в команды")

3. На панели добавить в команды выберите **скачать**. Затем Power Apps создаст файл манифеста команд, используя описание приложения и логотип, которые вы уже задали в своем приложении.

    ![Сведения о приложении](./media/embed-teams-app/download-app.png "Скачать приложение")

## <a name="add-the-app-as-a-personal-app"></a>Добавление приложения в качестве личного приложения

1. Чтобы добавить приложение в качестве личного приложения или вкладки для любого канала или диалога, выберите **приложения** в левой области навигации, а затем выберите **Отправить пользовательское приложение**.

    > [!NOTE]
    > Команда **Отправить пользовательское приложение** отображается только в том случае, если администратор команд создал [пользовательскую политику приложений](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies) и включил параметр **Разрешить передачу пользовательских приложений**.

    ![Добавить вкладку "приложение как"](./media/embed-teams-app/upload-custom-app.png "Отправка пользовательского приложения")

2. Выберите **Добавить** , чтобы добавить приложение в качестве личного приложения, или выберите **Добавить в группу** , чтобы добавить приложение в качестве вкладки в существующий канал или беседу.

## <a name="publish-the-app-to-the-teams-catalog"></a>Публикация приложения в каталоге команд

Если вы являетесь администратором, вы также можете [опубликовать приложение](https://docs.microsoft.com/microsoftteams/tenant-apps-catalog-teams) в каталоге Microsoft Teams.

## <a name="use-context-from-teams"></a>Использование контекста из команд

Для создания глубоко интегрированных приложений с командами можно использовать переменные контекста команды с функцией `Param()`. Например, используйте следующую формулу в свойстве **Fill** экрана, чтобы изменить фон приложения на основе темы пользователя в группах.

```
Switch(
        Param("theme"),
        "dark",
        RGBA(
            32,
            31,
            31,
            1
        ),
        "contrast",
        RGBA(
            0,
            0,
            0,
            1
        ),
        RGBA(
            243,
            242,
            241,
            1
        )
    )
```

Чтобы протестировать приложение, опубликуйте его, а затем воспроизведите в командах.

Поддерживаются следующие переменные контекста из команд:

- locale
- channelId
- channelType
- чатид
- groupId
- хостклиенттипе
- субентитид
- теамид
- теамтипе
- тема
- усертеамроле

> [!NOTE]
> Эта функция была добавлена в марте, 2020. Если вы внедряете приложение в группы до этого, вам может потребоваться повторно добавить приложение в группы для использования этой функции.

## <a name="improve-the-performance-of-your-app"></a>Повышение производительности приложения

При необходимости можно предварительно загрузить приложение в группы, чтобы повысить производительность.

1. Войдите в [make.powerapps.com](https://make.powerapps.com)и выберите **приложения** в меню.

2. Выберите **Дополнительные действия** (...) для приложения, которое вы хотите использовать в командах, а затем щелкните **Параметры**.

3. На панели Параметры выберите параметр **Предварительная загрузка приложения для повышения производительности** на **Да**. Приложение будет предварительно загружено каждый раз при внедрении в группы.

    ![Сведения о приложении](./media/embed-teams-app/preload-app.png "Предварительная загрузка приложения для повышения производительности")

4. Чтобы изменения вступили в силу, удалите и снова добавьте приложение в группы.

> [!NOTE]
> Это позволяет пользователям скачивать файл приложения, когда выполняется проверка подлинности для внедренных сценариев. Тем не менее пользователи могут запускать приложение только после успешной проверки подлинности. Это гарантирует, что данные приложения не будут доступны пользователям, не прошедшим проверку подлинности.

### <a name="see-also"></a>См. также:

[Добро пожаловать в Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/teams-overview)
