---
title: Часто задаваемые вопросы | Документация Майкрософт
description: Часто задаваемые вопросы на порталах PowerApps.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: eb7228f669fe8c36e25a18f4db0c7e4c4964a42d
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976698"
---
# <a name="powerapps-portals-faq"></a>Порталы PowerApps: вопросы и ответы

Мы отправили список часто задаваемых вопросов и получили краткие ответы, которые помогут быстро получить информацию.

## <a name="im-getting-an-error-that-only-one-portal-can-be-created"></a>При получении сообщения об ошибке можно создать только один портал.

В настоящее время в среде для каждого языка можно создать только один портал каждого типа. При попытке создать несколько порталов отобразится следующее сообщение об ошибке:

> [!div class=mx-imgBorder]
> ![Максимальное количество ошибок создания]портала,(media/portal-max-error.png "созданное на портале")

Чтобы создать больше порталов, необходимо создать новую среду, используя ссылку **создать новую среду** в сообщении об ошибке. Дополнительные сведения о создании портала см. в разделе [Создание портала](create-portal.md).

## <a name="im-getting-an-error-that-i-cant-delete-my-portal"></a>Я получаю сообщение об ошибке, что не удается удалить портал.

Если у вас недостаточно прав для удаления портала, появится сообщение об ошибке, как показано ниже.

> [!div class=mx-imgBorder]
> Ошибка ![удаления портала]при(media/portal-delete-error.png "удалении портала")

Сведения об удалении портала и необходимых привилегий см. в разделе [Удаление портала](manage-existing-portals.md#delete).

## <a name="im-getting-an-error-that-i-cant-create-a-portal"></a>Я получаю сообщение об ошибке, когда не удается создать портал.

Если у вас нет достаточных прав для создания портала в среде, вы увидите ошибку следующим образом:

> [!div class=mx-imgBorder]
> Ошибка ![создания портала]при(media/portal-create-error.png "создании портала")

Сведения о создании портала и необходимых привилегий см. в разделе [Создание портала](create-portal.md).

## <a name="im-getting-the-message-your-data-isnt-quite-ready"></a>Я получаю сообщение «ваши данные не полностью готовы».

Иногда создание базы данных может занять некоторое время, а правильное состояние может не отражаться на домашней странице. В этом случае вы увидите следующее сообщение:

> [!div class=mx-imgBorder]
> Данные, ![не готовые]к работе,(media/data-not-ready.png "не готовы")

Если вы продолжаете получать запрос на создание базы данных или если данные не являются достаточно готовыми, можно попробовать обновить домашнюю страницу PowerApps, прежде чем выбирать **портал с пустой** плитки.

## <a name="im-getting-an-error-that-i-dont-have-required-permissions-to-create-azure-active-directory-applications"></a>Я получаю сообщение об ошибке, что у меня нет необходимых разрешений для создания Azure Active Directory приложений.

При создании портала в Azure Active Directory, связанном с клиентом, регистрируется портал как новое приложение. Если у вас нет достаточных разрешений для регистрации приложения в Azure Active Directory клиенте, вы увидите ошибку следующим образом:

> [!div class=mx-imgBorder]
> ![Azure Active Directory ошибка](media/azure-ad-error.png "Azure Active Directory") ошибка

Чтобы создать и зарегистрировать приложения в Azure Active Directory, необходимо обратиться к администратору клиента, чтобы включить параметр **Регистрация приложений** для вашего клиента. Дополнительные сведения см. в разделе [необходимые разрешения](https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions).

## <a name="im-getting-an-error-that-portal-creation-is-blocked-in-this-tenant-by-global-administrator"></a>Я получаю сообщение об ошибке: создание портала в этом клиенте запрещено глобальным администратором

Если создание портала в клиенте заблокировано глобальным администратором, вы увидите следующее сообщение об ошибке:

> [!div class=mx-imgBorder]
> ![Создание портала. заблокированная]ошибка(media/portal-create-blocked-error.png "при создании портала")

Необходимо обратиться к глобальному администратору, чтобы разрешить создание порталов без прав администратора.

Если вы являетесь глобальным администратором, необходимо отключить параметр `disablePortalsCreationByNonAdminUsers` уровня клиента с помощью PowerShell. Выполните следующую команду в окне PowerShell (запустите PowerShell от имени администратора).

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $false }
```

Дополнительные сведения: [Отключение создания портала в клиенте](create-portal.md#disable-portal-creation-in-a-tenant)

## <a name="im-getting-an-error-that-i-dont-have-appropriate-license-to-access-this-website"></a>Я получаю сообщение об ошибке, что у меня нет подходящей лицензии для доступа к этому веб-сайту.

Внутренним пользователям организации, использующим порталы для доступа к страницам, прошедшим проверку подлинности, требуется, чтобы лицензии были назначены среде, к которой подключен портал. Дополнительные сведения о правах пользователей для порталов для внутренних пользователей можно узнать [здесь](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-flow-licensing-faq#can-you-clarify-the-use-rights-to-portals-for-internal-users). Если в среде не назначены лицензии, внутренние пользователи получат следующее сообщение об ошибке:

> [!div class=mx-imgBorder]
> ![](media/portal-login-error.png "Ошибка при входе") на портал ошибка входа на портал

