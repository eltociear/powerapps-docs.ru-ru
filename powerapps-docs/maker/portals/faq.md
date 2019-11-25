---
title: Вопросы и ответы | Документация Майкрософт
description: Вопросы и ответы в порталах PowerApps.
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
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759879"
---
# <a name="powerapps-portals-faq"></a>Вопросы и ответы в порталах PowerApps

Мы составили список часто задаваемых вопросов и кратких ответов на них, чтобы вы могли быстро получить нужную информацию.

## <a name="im-getting-an-error-that-only-one-portal-can-be-created"></a>Я получаю сообщение об ошибке. только один портал можно создавать.

В настоящее время, можно создать только один портал каждого типа в среде для каждого языка. При попытке создать более одного портала, вы увидите следующее сообщение об ошибке:

> [!div class=mx-imgBorder]
> ![Ошибка создания максимального количества порталов](media/portal-max-error.png "Ошибка создания максимального количества порталов")

Для создания нескольких порталов необходимо создать новую среду используя ссылку **создать новую среду** в сообщении об ошибке. Дополнительные сведения о создании портала см. в разделе [Создание портала](create-portal.md).

## <a name="im-getting-an-error-that-i-cant-delete-my-portal"></a>Я получаю сообщение об ошибке что не удается удалить мой портал.

Если у вас недостаточно прав для удаления портала, вы увидите сообщение об ошибке:

> [!div class=mx-imgBorder]
> ![Ошибка удаления портала](media/portal-delete-error.png "Ошибка удаления портала")

Дополнительные сведения о уничтожении портала и необходимых привилегий см. раздел [Удаление портала](manage-existing-portals.md#delete).

## <a name="im-getting-an-error-that-i-cant-create-a-portal"></a>Я получаю сообщение об ошибке что не удается создать мой портал.

Если у вас недостаточно прав для создания портала в среде, вы увидите сообщение об ошибке:

> [!div class=mx-imgBorder]
> ![Ошибка создания портала](media/portal-create-error.png "Ошибка создания портала")

Дополнительные сведения о создании портала и необходимых привилегий см. раздел [Создание портала](create-portal.md).

## <a name="im-getting-the-message-your-data-isnt-quite-ready"></a>Появилось сообщение: "Данные еще не готовы".

Иногда создание базы данных может занять некоторое время, и правильный статус может не отражаться на домашней странице. В этом случае появится следующее сообщение:

> [!div class=mx-imgBorder]
> ![Данные не готовы](media/data-not-ready.png "Данные не готовы")

Если вы продолжаете получать запрос на создание базы данных или ваши данные не совсем готовы, вы можете попробовать обновить домашнюю страницу PowerApps, прежде чем выбрать плитку **Портал с нуля**.

## <a name="im-getting-an-error-that-i-dont-have-required-permissions-to-create-azure-active-directory-applications"></a>Я получаю сообщение об ошибке, что у меня нет необходимых разрешений для создания приложений Azure Active Directory.

При создании портала портал как новое приложение регистрируется в Azure Active Directory связанный с клиентом. Если у вас недостаточно прав для регистрации приложения в клиенте Azure Active Directory, вы увидите следующее сообщение об ошибке:

> [!div class=mx-imgBorder]
> ![Ошибка Azure Active Directory](media/azure-ad-error.png "Ошибка Azure Active Directory")

Чтобы создавать и регистрировать приложения в Azure Active Directory, необходимо связаться администратор клиента, чтобы включить параметр **Регистрация приложений** для клиента. Для получения информации см. [Необходимые разрешения](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions).

## <a name="im-getting-an-error-that-portal-creation-is-blocked-in-this-tenant-by-global-administrator"></a>Я получаю сообщение об ошибке, что глобальный администратор заблокировал создание портала в этом клиенте

Если создание портала заблокировано в клиенте вашим глобальным администратором, вы увидите ошибку:

> [!div class=mx-imgBorder]
> ![Ошибка блокировки создания портала](media/portal-create-blocked-error.png "Ошибка блокировки создания портала")

Вы должны связаться с вашим глобальным администратором, чтобы разрешить создание порталов пользователями, не являющимися администраторами.

Если вы являетесь глобальным администратором, вы должны отключить параметр уровня клиента `disablePortalsCreationByNonAdminUsers` посредством PowerShell. Выполните следующую команду в окне PowerShell (запустите PowerShell от лица администратора).

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $false }
```

Дополнительные сведения: [Отключить создание портала в клиенте](create-portal.md#disable-portal-creation-in-a-tenant)

## <a name="im-getting-an-error-that-i-dont-have-appropriate-license-to-access-this-website"></a>Я получаю сообщение об ошибке, что у меня нет соответствующей лицензии для доступа на этот веб-сайт.

Для внутренних пользователей организации, использующих порталы для получения доступа к прошедшим аутентификацию страницам, требуется, чтобы лицензии были назначены среде, к которой подключен портал. Можно прочитать дополнительные сведения о правах пользователей для порталов для внутренних пользователей [здесь](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-clarify-the-use-rights-to-portals-for-internal-users). Если среда не имеет назначенные лицензии, внутренние пользователи получат ошибку, как указано ниже:

> [!div class=mx-imgBorder]
> ![Ошибка входа на портал](media/portal-login-error.png "Ошибка входа на портал")

