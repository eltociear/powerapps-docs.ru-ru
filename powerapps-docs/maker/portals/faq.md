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
ms.openlocfilehash: 810829b58d666b66bd2cac7235d013a4bfdcd806
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542526"
---
# <a name="powerapps-portals-faq"></a>Порталы PowerApps: вопросы и ответы

Мы отправили список часто задаваемых вопросов и получили краткие ответы, которые помогут быстро получить информацию.

## <a name="im-getting-an-error-that-only-one-portal-can-be-created"></a>При получении сообщения об ошибке можно создать только один портал.

В настоящее время в среде для каждого языка можно создать только один портал каждого типа. При попытке создать несколько порталов отобразится следующее сообщение об ошибке:

> [!div class=mx-imgBorder]
> ![Ошибка при создании максимального значения на портале](media/portal-max-error.png "Ошибка при создании максимального значения на портале")

Чтобы создать больше порталов, необходимо создать новую среду, используя ссылку **создать новую среду** в сообщении об ошибке. Дополнительные сведения о создании портала см. в разделе [Создание портала](create-portal.md).

## <a name="im-getting-an-error-that-i-cant-delete-my-portal"></a>Я получаю сообщение об ошибке, что не удается удалить портал.

Если у вас недостаточно прав для удаления портала, появится сообщение об ошибке, как показано ниже.

> [!div class=mx-imgBorder]
> ![Ошибка при удалении портала](media/portal-delete-error.png "Ошибка при удалении портала")

Сведения об удалении портала и необходимых привилегий см. в разделе [Удаление портала](manage-existing-portals.md#delete).

## <a name="im-getting-an-error-that-i-cant-create-a-portal"></a>Я получаю сообщение об ошибке, когда не удается создать портал.

Если у вас нет достаточных прав для создания портала в среде, вы увидите ошибку следующим образом:

> [!div class=mx-imgBorder]
> ![Ошибка при создании портала](media/portal-create-error.png "Ошибка при создании портала")

Сведения о создании портала и необходимых привилегий см. в разделе [Создание портала](create-portal.md).

## <a name="im-getting-the-message-your-data-isnt-quite-ready"></a>Я получаю сообщение «ваши данные не полностью готовы».

Иногда создание базы данных может занять некоторое время, а правильное состояние может не отражаться на домашней странице. В этом случае вы увидите следующее сообщение:

> [!div class=mx-imgBorder]
> ![Данные не готовы](media/data-not-ready.png "Данные не готовы")

Если вы продолжаете получать запрос на создание базы данных или если данные не являются достаточно готовыми, можно попробовать обновить домашнюю страницу PowerApps, прежде чем выбирать **портал с пустой** плитки.

## <a name="im-getting-an-error-that-i-dont-have-required-permissions-to-create-azure-active-directory-applications"></a>Я получаю сообщение об ошибке, что у меня нет необходимых разрешений для создания Azure Active Directory приложений.

При создании портала в Azure Active Directory, связанном с клиентом, регистрируется портал как новое приложение. Если у вас нет достаточных разрешений для регистрации приложения в Azure Active Directory клиенте, вы увидите ошибку следующим образом:

> [!div class=mx-imgBorder]
> ![Ошибка Azure Active Directory](media/azure-ad-error.png "Ошибка Azure Active Directory")

Чтобы создать и зарегистрировать приложения в Azure Active Directory, необходимо обратиться к администратору клиента, чтобы включить параметр **Регистрация приложений** для вашего клиента. Дополнительные сведения см. в разделе [необходимые разрешения](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions).

## <a name="im-getting-an-error-that-portal-creation-is-blocked-in-this-tenant-by-global-administrator"></a>Я получаю сообщение об ошибке: создание портала в этом клиенте запрещено глобальным администратором

Если создание портала в клиенте заблокировано глобальным администратором, вы увидите следующее сообщение об ошибке:

> [!div class=mx-imgBorder]
> ![Ошибка блокировки при создании портала](media/portal-create-blocked-error.png "Ошибка блокировки при создании портала")

Необходимо обратиться к глобальному администратору, чтобы разрешить создание порталов без прав администратора.

Если вы являетесь глобальным администратором, необходимо отключить параметр `disablePortalsCreationByNonAdminUsers` уровня клиента с помощью PowerShell. Выполните следующую команду в окне PowerShell (запустите PowerShell от имени администратора).

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $false }
```

Дополнительные сведения: [Отключение создания портала в клиенте](create-portal.md#disable-portal-creation-in-a-tenant)

## <a name="im-getting-an-error-that-i-dont-have-appropriate-license-to-access-this-website"></a>Я получаю сообщение об ошибке, что у меня нет подходящей лицензии для доступа к этому веб-сайту.

Внутренним пользователям организации, использующим порталы для доступа к страницам, прошедшим проверку подлинности, требуется, чтобы лицензии были назначены среде, к которой подключен портал. Дополнительные сведения о правах пользователей для порталов для внутренних пользователей можно узнать [здесь](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-clarify-the-use-rights-to-portals-for-internal-users). Если в среде не назначены лицензии, внутренние пользователи получат следующее сообщение об ошибке:

> [!div class=mx-imgBorder]
> ![Ошибка входа на портал](media/portal-login-error.png "Ошибка входа на портал")

