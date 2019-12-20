---
title: Обзор центра администрирования порталов Power Apps | Документация Майкрософт
description: Сведения о центре администрирования порталов Power Apps.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 0996704ccbc10f81b95c41d86234ca626a33a345
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2019
ms.locfileid: "2867426"
---
# <a name="power-apps-portals-admin-center"></a>Центр администрирования портала Power Apps

Центр администрирования порталов Power Apps позволяет выполнять расширенные административные действия на порталах. Центр администрирования доступен когда портал подготовлен успешно.

## <a name="open-power-apps-portals-admin-center"></a>Открытие Центра администрирования порталов Power Apps.

1. Перейдите в раздел **Последние приложения** на домашней странице Power Apps и найдите ваш портал.

    > [!div class=mx-imgBorder]
    > ![Недавние приложения](../media/recent-apps.png "Недавние приложения")  

2. Выберите **Дополнительные команды (...)** > **Параметры**.

    > [!div class=mx-imgBorder]
    > ![Параметр настроек портала](../media/portal-settings-option.png "Параметр настроек портала")

3. В области **Параметры портала** выберите **Администрирование**.

    > [!div class=mx-imgBorder]
    > ![Область настроек портала](../media/portal-settings-admin.png "Область настроек портала")

## <a name="add-yourself-as-an-owner-of-the-azure-ad-application"></a>Добавление себя как ответственного за приложение Azure AD

Если вы не являетесь глобальным администратором и пытаетесь управлять уже подготовленным порталом или заново отправить подготовленный портал в случае сбоя отправки, вы должны быть ответственным за приложение Azure Active Directory (Azure AD), подключенное к вашему порталу.

1. Откройте центр администрирования порталов Power Apps и перейдите на вкладку **Сведения о портале**.

2. Скопируйте значение в поле **Идентификатор приложения**.

    > [!div class=mx-imgBorder]
    > ![Вкладка сведений о портале](../media/portal-details-admin.png "Вкладка сведений о портале")

3. Перейдите в Azure AD, связанный с вашим клиентом Azure. [!include[](../../../includes/proc-more-information.md)] [Принятие функций администратора неуправляемого каталога в Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-o365-subscription)

4. В Azure AD найдите регистрацию приложения по скопированному идентификатору приложения. Может потребоваться переключиться с **Мои приложения** на **Все приложения**.

5. Добавьте пользователей или группы в качестве ответственных за эту регистрацию приложения. [!include[](../../../includes/proc-more-information.md)] [Управление доступом к приложениям](https://docs.microsoft.com/azure/active-directory/active-directory-managing-access-to-apps)

    > [!Note]
    > Эта задача может выполняться глобальным администратором вашей организации или существующим ответственным за данное приложение.

6. После добавления себя в качестве ответственного снова откройте страницу центра администрирования порталов Power Apps.