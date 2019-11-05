---
title: Обзор центра администрирования порталов PowerApps | MicrosoftDocs
description: Сведения о центре администрирования порталов PowerApps.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6f8434a6a395931fc4edfe02913f47536b4a709d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543081"
---
# <a name="powerapps-portals-admin-center"></a>Центр администрирования порталов PowerApps

Центр администрирования порталов PowerApps позволяет выполнять расширенные административные действия на порталах. Центр администрирования доступен после успешного завершения подготовки портала.

## <a name="open-powerapps-portals-admin-center"></a>Открыть центр администрирования порталов PowerApps

1. Перейдите в раздел **недавние приложения** на домашней странице PowerApps и найдите портал.

    > [!div class=mx-imgBorder]
    > ![Последние приложения](../media/recent-apps.png "Последние приложения")  

2. Выберите **Дополнительные команды (...)**  > **Параметры**.

    > [!div class=mx-imgBorder]
    > ![Параметр "Параметры портала"](../media/portal-settings-option.png "Параметр "Параметры портала"")

3. В области **Параметры портала** выберите **Администрирование**.

    > [!div class=mx-imgBorder]
    > ![Область параметров портала](../media/portal-settings-admin.png "Область параметров портала")

## <a name="add-yourself-as-an-owner-of-the-azure-ad-application"></a>Добавление себя в качестве владельца приложения Azure AD

Если вы не являетесь глобальным администратором и пытаетесь управлять порталом, который уже был подготовлен, или повторно отправить подготовку в случае сбоя, необходимо быть владельцем приложения Azure Active Directory (Azure AD), подключенного к порталу.

1. Перейдите в центр администрирования порталов PowerApps и откройте вкладку **сведения о портале** .

2. Скопируйте значение из поля **Application ID (идентификатор приложения** ).

    > [!div class=mx-imgBorder]
    > ![Вкладка "сведения о портале"](../media/portal-details-admin.png "Вкладка "сведения о портале"")

3. Перейдите к Azure AD, связанному с вашим клиентом. [!include[](../../../includes/proc-more-information.md)] [получить неуправляемый каталог от имени администратора в Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-o365-subscription)

4. В Azure AD найдите регистрацию приложения, используя скопированный идентификатор приложения. Может потребоваться переключиться со всех приложений на **все приложения**.

5. Добавление пользователей или групп в качестве владельцев регистрации приложения. [!include[](../../../includes/proc-more-information.md)] [Управление доступом к приложениям](https://docs.microsoft.com/azure/active-directory/active-directory-managing-access-to-apps)

    > [!Note]
    > Эта задача может быть выполнена глобальным администратором организации или существующим владельцем этого приложения.

6. После добавления себя в качестве владельца снова откройте страницу центра администрирования порталов PowerApps.