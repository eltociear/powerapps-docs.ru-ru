---
title: Реагирование на запросы субъектов данных на удаление пользовательских данных | Документация Майкрософт
description: Реагирование на запросы субъектов данных на удаление пользовательских данных
services: powerapps
suite: powerapps
documentationcenter: na
author: jamesol-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/17/2018
ms.author: jamesol
ms.openlocfilehash: 67e1ad0056f80b892343506ec9a89845e0bca05e
ms.sourcegitcommit: e3a2819c14ad67cc4ca6640b9064550d0f553d8f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2018
---
# <a name="responding-to-delete-data-subject-rights-dsr-requests-for-customer-data-in-powerapps"></a>Реагирование на запросы субъектов данных на удаление пользовательских данных в PowerApps

"Право на стирание" путем удаления персональных данных из пользовательских данных организации является основным методом защиты в Общем регламенте по защите данных (GDPR). Удаление персональных данных включает удаление системных журналов, но не данных из журналов аудита.

PowerApps позволяет пользователям создавать бизнес-приложения, которые являются важной частью повседневной работы вашей организации. Когда пользователь покидает вашу организацию, вам необходимо будет вручную просмотреть и определить, следует ли удалять определенные, созданные им данные и ресурсы. Другие персональные данные будут автоматически удаляться всякий раз, когда учетная запись пользователя будет удалена из Azure Active Directory.

Ниже приведены сведения о том, какие персональные данные будут автоматически удалены и какие данные потребуется просмотреть и удалить вручную.

Требуется проверка и удаление в ручном режиме |   Автоматически удаляются при удалении пользователя из Azure Active Directory
--- | ---
Среда\** | Шлюз
Разрешения среды\*** | Разрешения шлюза
Приложение на основе холста\** | Уведомления PowerApps
Разрешения приложений на основе холста | Параметры пользователя PowerApps
Подключение\** | Параметры приложений пользователя PowerApps
Разрешения подключения |
Настраиваемый соединитель\** |
Разрешения настраиваемого соединителя |  

\** Каждый из этих ресурсов содержит записи "кем создано" и "кем изменено", которые включают в себя персональные данные. По соображениям безопасности эти записи будут сохраняться до тех пор, пока ресурс не будет удален.

\*** Для сред, которые содержат базу данных Common Data Service (CDS) for Apps, разрешения среды (то есть, каким пользователям назначены роли создателя и администратора в среде) хранятся в виде записей в этой базе данных. Руководство по реагированию на запросы DSR в отношении пользовательских данных в CDS for Apps см. [здесь](https://go.microsoft.com/fwlink/?linkid=872251).

Для данных и ресурсов, требующих просмотра в ручном режиме, PowerApps предлагает следующие возможности переназначения (если необходимо) или удаления персональных данных конкретного пользователя:

- Доступ к веб-сайтам: [сайт PowerApps](https://web.powerapps.com), [центр администрирования PowerApps](https://admin.powerapps.com/) и [портал Office 365 Service Trust Portal](https://servicetrust.microsoft.com/).
- Доступ к PowerShell: командлеты PowerApps для [создателей приложений](https://go.microsoft.com/fwlink/?linkid=871448) и [администраторов](https://go.microsoft.com/fwlink/?linkid=871804) и командлеты для [локальных шлюзов](https://go.microsoft.com/fwlink/?linkid=872238).
Ниже поведены доступные возможности для удаления каждого типа ресурсов, которые могут содержать персональные данные:

Ресурсы, содержащие персональные данные | Доступ к веб-сайтам | Доступ к PowerShell
--- | --- | ---
Среда | Центр администрирования PowerApps |  Командлеты PowerApps
Разрешения среды**   | Центр администрирования PowerApps | Командлеты PowerApps
Приложение на основе холста  | Центр администрирования PowerApps <br> Сайт PowerApps| Командлеты PowerApps
Разрешения приложений на основе холста  | Центр администрирования PowerApps | Командлеты PowerApps
Подключение | | Разработчик приложений: доступно <br> Администратор: на стадии разработки
Разрешения подключения | | Разработчик приложений: доступно <br> Администратор: на стадии разработки
Настраиваемый соединитель | | Разработчик приложений: доступно <br> Администратор: на стадии разработки
Разрешения настраиваемого соединителя | | Разработчик приложений: доступно <br> Администратор: на стадии разработки

\** С выходом службы CDS for Apps, если в среде создается база данных, разрешения среды и приложения на основе модели хранятся в виде записей в экземпляре этой базы данных. Руководство по реагированию на запросы DSR в отношении пользовательских данных в CDS for Apps см. [здесь](https://go.microsoft.com/fwlink/?linkid=872251).

## <a name="prerequisites"></a>Технические условия

### <a name="for-users"></a>Для пользователей
Любой пользователь с действующей лицензией PowerApps может выполнять операции пользователя, описанные в этом документе, с помощью [сайта PowerApps](https://web.powerapps.com) или [командлетов PowerShell для создателей приложений](https://go.microsoft.com/fwlink/?linkid=871448).

### <a name="for-administrators"></a>Для администраторов
Для выполнения операций администрирования, описанных в этом документе, в [центре администрирования PowerApps](https://admin.powerapps.com/), центре администрирования Microsoft Flow или с помощью [командлетов PowerShell для администраторов PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) вам понадобится учетная запись со следующими разрешениями.

- Платная или пробная лицензия PowerApps (план 2). Вы можете [получить пробную лицензию](http://web.powerapps.com/trial) и продлить ее через 30 дней.
- Права [глобального администратора Office 365](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) или [глобального администратора Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) также необходимы, если вам нужно выполнить поиск по ресурсам другого пользователя. В противном случае вы будете иметь доступ только к тем средам и ресурсам среды, где у вас есть привилегии администратора среды.

## <a name="step-1-delete-or-reassign-all-environments-created-by-the-user"></a>Шаг 1. Удаление или переназначение всех сред, созданных пользователем
Как администратор, вы принимаете два решения при обработке запроса DSR на удаление для каждой среды, созданной пользователем:

1.  Если вы определите, что среда не используется кем-либо еще в вашей организации, вы можете ее удалить.

2.  Если вы решите, что среда по-прежнему требуется, вы можете отказаться от удаления среды и добавить себя (или другого пользователя в организации) в качестве администратора среды.

> [!IMPORTANT]
> В результате удаления среды все ресурсы в ней, включая все приложения, потоки, подключения и т. д., будут навсегда удалены. Поэтому перед удалением просмотрите содержимое среды.

### <a name="give-access-to-a-users-environments-from-the-powerapps-admin-center"></a>Предоставление доступа к средам пользователей из центра администрирования PowerApps
Администратор может предоставить административный доступ к среде, созданной определенным пользователем, из [центра администрирования PowerApps](https://admin.powerapps.com/), выполнив следующие действия:

1. В [центре администрирования PowerApps](https://admin.powerapps.com/) выберите все среды вашей организации.

    ![Целевая страница центра администрирования](./media/powerapps-gdpr-delete-dsr/admin-center-landing.png)

2. Если среда была создана пользователем, отправившим запрос DSR, выберите **Безопасность** и выполните шаги, описанные в статье [Администрирование сред в PowerApps](environments-administration.md), чтобы предоставить привилегии администратора себе или другому пользователю в вашей организации.

    ![Безопасность среды](./media/powerapps-gdpr-delete-dsr/share-environment.png)

### <a name="delete-environments-created-by-a-user-from-the-powerapps-admin-center"></a>Удаление сред, созданных пользователем, из центра администрирования PowerApps
Администратор может просмотреть и удалить среды, созданные определенным пользователем, из [центра администрирования PowerApps](https://admin.powerapps.com/), выполнив следующие действия:

1. В [центре администрирования PowerApps](https://admin.powerapps.com/) выберите все среды вашей организации.

    ![Целевая страница центра администрирования](./media/powerapps-gdpr-delete-dsr/admin-center-landing.png)

2. Если среда была создана пользователем, отправившим запрос DSR, щелкните **Удалить**, а затем выполните действия по удалению среды:

    ![Удаление среды](./media/powerapps-gdpr-delete-dsr/delete-environment.png)

### <a name="give-access-to-a-users-environments-using-powershell"></a>Предоставление доступа к средам пользователя с помощью PowerShell
Администратор может назначить себе (или другому пользователю в своей организации) доступ ко всем средам, созданным пользователем, с помощью одного из командлетов [PowerShell для администраторов PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) — **Set-AdminEnvironmentRoleAssignment**:

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"
$myUserId = $global:currentSession.UserId

#Assign yourself as an admin to each environment created by the user
Get-AdminEnvironment -CreatedBy $deleteDsrUserId | Set-AdminEnvironmentRoleAssignment -RoleName EnvironmentAdmin -PrincipalType User -PrincipalObjectId $myUserId

#Retrieve the environment role assignments to confirm
Get-AdminEnvironment -CreatedBy $deleteDsrUserId | Get-AdminEnvironmentRoleAssignment
```

> [!IMPORTANT]
> Эта функция работает только в средах, в которых отсутствует экземпляр базы данных в CDS for Apps.

### <a name="delete-environments-created-by-a-user-using-powershell"></a>Удаление созданных пользователем сред с помощью PowerShell
 Администратор может удалить все созданные пользователем среды с помощью одного из командлетов [PowerShell для администраторов PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) — **Remove-AdminEnvironment**:

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

# Retrieve all environments created by the user and then delete them
Get-AdminEnvironment -CreatedBy $deleteDsrUserId | Remove-AdminEnvironment
```

## <a name="step-2-delete-the-users-permissions-to-all-other-environments"></a>Шаг 2. Удаление разрешений пользователя во всех других средах
В среде пользователям могут назначаться разрешения (например, "Администратор окружения" и "Создатель окружения"), которые хранятся в службе PowerApps как "назначение ролей".
С выходом службы CDS for Apps, если в среде создается база данных, эти назначения ролей хранятся в виде записей в экземпляре базы данных.
Дополнительные сведения см. в статье [Администрирование сред в PowerApps](environments-administration.md).

### <a name="for-environments-without-a-cds-for-apps-database"></a>Для сред без базы данных CDS for Apps

#### <a name="powerapps-admin-center"></a>Центр администрирования PowerApps
Администратор может удалить разрешения среды для пользователя в [центре администрирования PowerApps](https://admin.powerapps.com/), выполнив следующие действия:

1.  В [центре администрирования PowerApps](https://admin.powerapps.com/) выберите все среды вашей организации.

    Вы должны быть [глобальным администратором Office 365](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) или [глобальным администратором Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal), чтобы иметь возможность просматривать все среды, созданные в вашей организации.

    ![Целевая страница центра администрирования](./media/powerapps-gdpr-delete-dsr/admin-center-landing.png)

2.  Выберите **Безопасность**.

    Если в вашей среде нет базы данных CDS for Apps, вы увидите раздел **Роли среды**.

4.  В разделе **Роли среды** выберите **Администратор окружения** и **Создатель окружения** отдельно, а затем с помощью панели поиска выполните поиск по имени пользователя.

    ![Страница "Роли среды"](./media/powerapps-gdpr-delete-dsr/admin-environment-role-share-page.png)

5.  Если у пользователя есть доступ к любой из ролей, на экране **Пользователи** удалите их разрешение и щелкните **Сохранить**.

#### <a name="powershell"></a>PowerShell
Администраторы могут удалять все назначения ролей среды для пользователя во всех средах без базы данных CDS for Apps с помощью одного из командлетов [PowerShell для администратора PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) — **Remove-AdminEnvironmentRoleAssignment**:

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#find all environment role assignments for the user for environments without a CDS for Apps instance and delete them
Get-AdminEnvironmentRoleAssignment -UserId $deleteDsrUserId | Remove-AdminEnvironmentRoleAssignment
```

> [!IMPORTANT]
> Эта функция работает только в средах, в которых отсутствует экземпляр базы данных CDS for Apps.

### <a name="for-environments-with-a-cds-for-apps-database"></a>Для сред с базой данных CDS for Apps
С выходом службы CDS for Apps, если в среде создается база данных, эти назначения ролей хранятся в виде записей в экземпляре базы данных. Ознакомьтесь с документацией о том, как удалить персональные данные из экземпляра базы данных в CDS for Apps.

## <a name="step-3-delete-or-reassign-all-canvas-apps-owned-by-a-user"></a>Шаг 3. Удаление или переназначение всех приложений на основе холста, принадлежащих пользователю

### <a name="reassign-a-users-canvas-apps-using-the-powerapps-admin-powershell-cmdlets"></a>Переназначение принадлежащего пользователю приложения на основе холста с помощью командлетов PowerShell для администраторов PowerApps
Если администратор решает не удалять приложения на основе холста, их можно переназначать с помощью **Set-AdminAppOwner**, одного из командлетов [PowerShell для администраторов PowerApps](https://go.microsoft.com/fwlink/?linkid=871804):

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"
$newAppOwnerUserId = "72c272b8-14c3-4f7a-95f7-a76f65c9ccd8"

#find all apps owned by the DSR user and assigns them a new owner
Get-AdminApp -Owner $deleteDsrUserId | Set-AdminAppOwner -AppOwner $newAppOwnerUserId
```

### <a name="delete-a-users-canvas-app-using-the-powerapps-site"></a>Удаление принадлежащего пользователю приложения на основе холста с помощью сайта PowerApps
Пользователь может удалить приложение с [сайта PowerApps](https://web.powerapps.com). Все действия по удалению приложения см. в разделе об удалении приложения.

### <a name="delete-a-users-canvas-app-using-the-powerapps-admin-center"></a>Удаление принадлежащего пользователю приложения на основе холста с помощью центра администрирования PowerApps
Администратор может удалить созданные пользователем приложения в [центре администрирования PowerApps](https://admin.powerapps.com/), выполнив следующие действия:

1.  В [центре администрирования PowerApps](https://admin.powerapps.com/) выберите все среды вашей организации.

    Вы должны быть [глобальным администратором Office 365](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) или [глобальным администратором Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal), чтобы иметь возможность просматривать все среды, созданные в вашей организации.

    ![Целевая страница центра администрирования](./media/powerapps-gdpr-delete-dsr/admin-center-landing.png)

2.  Щелкните **Ресурсы** > **Приложения**.

3.  Используя панель поиска, выполните поиск имени пользователя. Вы получите список названий всех приложений, созданных пользователем в этой среде.

    ![Поиск приложений](./media/powerapps-gdpr-delete-dsr/search-apps.png)

4.  Щелкните **Подробности** для каждого из приложений, принадлежащих пользователю:

    ![Выбор сведений о приложении](./media/powerapps-gdpr-delete-dsr/select-app-details.png)

5.  Щелкните **Удалить**, чтобы удалить каждое приложение.

### <a name="delete-a-users-canvas-app-using-the-powerapps-admin-powershell-cmdlets"></a>Удаление принадлежащего пользователю приложения на основе холста с помощью командлетов PowerShell для администраторов PowerApps
Если администратор решает удалить все приложения на основе холста, принадлежащие пользователю, это можно сделать с помощью одного из командлетов [PowerShell для администраторов PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) — **Remove-AdminApp**:

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#find all apps owned by the DSR user and deletes them
Get-AdminApp -Owner "0ecb1fcc-6782-4e46-a4c4-738c1d3accea" | Remove-AdminApp
```

## <a name="step-4-delete-the-users-permissions-to-canvas-apps"></a>Шаг 4. Удаление разрешений пользователя на приложение на основе холста
Каждый раз, когда к приложению получает общий доступ один из пользователей, PowerApps сохраняет запись с именем "назначение ролей", в которой описываются разрешения пользователя в приложении (CanEdit или CanUser). Дополнительные сведения см. в статье о предоставлении совместного доступа к приложениям в PowerApps.

> [!NOTE]
> Назначения ролей приложения будут удалены при удалении приложения.

> [!NOTE]
> Назначение роли владельца приложения можно удалить, только назначив нового владельца.

### <a name="powerapps-admin-center"></a>Центр администрирования PowerApps
Администратор может удалить назначения ролей приложения для пользователя в [центре администрирования PowerApps](https://admin.powerapps.com/), выполнив следующие действия:

1.  В [центре администрирования PowerApps](https://admin.powerapps.com/) выберите все среды вашей организации.

    Вы должны быть [глобальным администратором Office 365](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) или [глобальным администратором Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal), чтобы иметь возможность просматривать все среды, созданные в вашей организации.

    ![Целевая страница центра администрирования](./media/powerapps-gdpr-delete-dsr/admin-center-landing.png)

2.  Для каждой среды выберите **Ресурсы** > **Приложения**.

3.  Выберите **Share** (Предоставить доступ) для каждого из приложений в среде.

    ![Выбор параметра предоставления доступа](./media/powerapps-gdpr-delete-dsr/select-admin-share-nofilter.png)

6.  Если у пользователя есть доступ к любому из приложений, на экране **Share** (Предоставление доступа) приложения удалите его разрешения и щелкните **Сохранить**.

    ![Страница предоставления общего доступа к приложению администратора](./media/powerapps-gdpr-delete-dsr/admin-share-page.png)

### <a name="powerapps-admin-powershell-cmdlets"></a>Командлеты PowerShell для администраторов PowerApps
Администратор может удалить все назначения роли для приложения на основе холста с помощью одного из [командлетов PowerShell для администраторов PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) — **Remove-AdminAppRoleAssignmnet**:

```
Add-PowerAppsAccount
$deleteDsrUserId = "0ecb1fcc-6782-4e46-a4c4-738c1d3accea"

#find all app role assignments for the DSR user and deletes them
Get-AdminAppRoleAssignment -UserId $deleteDsrUserId | Remove-AdminAppRoleAssignment
```

## <a name="step-5-delete-connections-created-by-a-user"></a>Шаг 5. Удаление подключений, созданных пользователем
Подключения используются вместе с соединителями при установке подключения к другим API и системам SaaS.  Подключения включают в себя ссылки на пользователя, который их создал, и могут быть удалены, чтобы удалить все ссылки на пользователя.

### <a name="powershell-cmdlets-for-app-creators"></a>Командлеты PowerShell для создателей приложений
Пользователь может удалить все свои подключения с помощью одного из командлетов [PowerShell для создателей приложений](https://go.microsoft.com/fwlink/?linkid=871448) — Remove-Connection:

```
Add-PowerAppsAccount

#Retrieves all connections for the calling user and deletes them
Get-Connection | Remove-Connection
```

### <a name="powershell-cmdlets-for-powerapps-administrators"></a>Командлеты PowerShell для администраторов PowerApps
Функция, позволяющая администратору находить и удалять подключения пользователя с помощью [командлетов PowerShell](https://go.microsoft.com/fwlink/?linkid=871804), находится в стадии разработки.

## <a name="step-6-delete-the-users-permissions-to-shared-connections"></a>Шаг 6. Удаление разрешений пользователя для доступа к общедоступным подключениям

### <a name="powershell-cmdlets-for-app-creators"></a>Командлеты PowerShell для создателей приложений
Пользователь может удалить все свои назначения роли для общих подключений с помощью одного из командлетов [PowerShell для создателей приложений](https://go.microsoft.com/fwlink/?linkid=871448) — Remove-ConnectionRoleAssignment:

```
Add-PowerAppsAccount

#Retrieves all connection role assignments for the calling users and deletes them
Get-ConnectionRoleAssignment | Remove-ConnectionRoleAssignment
```
> [!NOTE]
> Назначения ролей владельца не могут быть удалены без удаления ресурса подключения.

### <a name="powerapps-admin-powershell-cmdlets"></a>Командлеты PowerShell для администраторов PowerApps
Функция, позволяющая администратору находить и удалять назначения роли для подключения с помощью командлетов [PowerShell для администраторов PowerApps](https://go.microsoft.com/fwlink/?linkid=871804), находится в стадии разработки.

## <a name="step-7-delete-custom-connectors-created-by-the-user"></a>Шаг 7. Удаление настраиваемых соединителей, созданных пользователем
Настраиваемые соединители дополняют имеющиеся встроенные соединители и позволяют подключаться к другим API, SaaS и системам собственной разработки. Вам может понадобиться передать права на использование настраиваемого соединителя другим пользователям в организации или удалить настраиваемый соединитель.

### <a name="powershell-cmdlets-for-app-creators"></a>Командлеты PowerShell для создателей приложений
Пользователь может удалить все свои настраиваемые соединители с помощью одного из командлетов [PowerShell для создателей приложений](https://go.microsoft.com/fwlink/?linkid=871448) — Remove-Connector:

```
Add-PowerAppsAccount

#Retrieves all custom connectors for the calling user and deletes them
Get-Connector -FilterNonCustomConnectors | Remove-Connector
```

### <a name="powerapps-admin-powershell-cmdlets"></a>Командлеты PowerShell для администраторов PowerApps
Функция, позволяющая администратору находить и удалять настраиваемые соединители с помощью командлетов [PowerShell для администраторов PowerApps](https://go.microsoft.com/fwlink/?linkid=871804), находится в стадии разработки.

## <a name="step-8-delete-the-users-permissions-to-shared-custom-connectors"></a>Шаг 8. Удаление разрешений пользователя для доступа к общедоступным настраиваемым соединителям

### <a name="powershell-cmdlets-for-app-creators"></a>Командлеты PowerShell для создателей приложений
Пользователь может удалить все свои назначения роли соединителя для общих настраиваемых соединителей с помощью одного из командлетов [PowerShell для создателей приложений](https://go.microsoft.com/fwlink/?linkid=871448) — Remove-ConnectorRoleAssignment:

```
Add-PowerAppsAccount

#Retrieves all connector role assignments for the calling users and deletes them
Get-ConnectorRoleAssignment | Remove-ConnectorRoleAssignment
```

> [!NOTE]
> Назначения ролей владельца не могут быть удалены без удаления ресурса подключения.

### <a name="powerapps-admin-powershell-cmdlets"></a>Командлеты PowerShell для администраторов PowerApps
Функция, позволяющая администратору находить и удалять назначения роли для соединителя с помощью командлетов [PowerShell для администраторов PowerApps](https://go.microsoft.com/fwlink/?linkid=871804), находится в стадии разработки.

## <a name="step-9-delete-the-users-personal-data-in-microsoft-flow"></a>Шаг 9. Удаление персональных данных пользователя в Microsoft Flow
Лицензии PowerApps всегда содержат возможности Microsoft Flow. Помимо этого, Microsoft Flow также доступна в качестве автономной службы.
Руководство по реагированию на запросы DSR для пользователей, использующих службу Microsoft Flow, см. [здесь](https://go.microsoft.com/fwlink/?linkid=872250).

> [!IMPORTANT]
> Рекомендуется, чтобы администраторы выполнили этот шаг для пользователя PowerApps

## <a name="step-10-delete-the-users-personal-data-in-instances-of-cds-for-apps"></a>Шаг 10. Удаление персональных данных пользователя в экземплярах CDS for Apps
Некоторые лицензии PowerApps, включая "План сообщества PowerApps", дают пользователям организации возможность создавать экземпляры CDS for Apps и приложения в этой службе. "План сообщества PowerApps" — это бесплатная лицензия, которая позволяет пользователям испытать CDS for Apps в отдельной среде. Сведения о возможностях, включенных в каждую лицензию PowerApps, см. на странице с ценами на PowerApps.

Руководство по реагированию на запросы DSR для пользователей, использующих CDS for Apps, см. [здесь](https://go.microsoft.com/fwlink/?linkid=872251).

> [!IMPORTANT]
> Рекомендуется, чтобы администраторы выполнили этот шаг для пользователя PowerApps

## <a name="step-11-delete-the-user-from-azure-active-directory"></a>Шаг 11. Удаление пользователя из Azure Active Directory
По завершении вышеуказанных шагов следует удалить учетную запись пользователя Azure Active Directory, выполнив действия, описанные в Общем регламенте по запросам субъектов данных Azure (GDPR), который находится на портале [Office 365 Service Trust Portal](https://servicetrust.microsoft.com/ViewPage/GDPRDSR).