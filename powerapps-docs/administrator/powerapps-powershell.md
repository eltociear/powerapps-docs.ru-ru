---
title: Поддержка PowerShell (предварительная версия) | Документация Майкрософт
description: Описание различных командлетов PowerShell и пошаговое руководство по их установке и запуску.
author: jamesol-msft
manager: kvivek
ms.service: powerapps
ms.component: pa-admin
ms.topic: reference
ms.date: 01/18/2019
ms.author: jamesol
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: 0152296adbe01abae2b831576c312a43d1f2a2b8
ms.sourcegitcommit: 3ce7c17f90f87756a072210c8abfbd93733a6d4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2019
ms.locfileid: "54397774"
---
# <a name="powershell-support-for-powerapps-preview"></a>Поддержка PowerShell в PowerApps (предварительная версия)
С помощью предварительной версии командлетов PowerShell для создателей и администраторов приложений вы можете автоматизировать многие задачи мониторинга и управления, которые раньше выполнялись только вручную в [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) или [центре администрирования PowerApps](https://admin.powerapps.com).

## <a name="cmdlets"></a>Командлеты
[Командлеты](https://docs.microsoft.com/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet) представляют собой функции, написанные на языке сценариев PowerShell, которые выполняют команды в среде Windows PowerShell. Выполнение этих командлетов PowerApps позволяет взаимодействовать с вашей платформой бизнес-приложений без необходимости использовать портал администрирования в веб-браузере. Эти командлеты можно объединить с другими функциями PowerShell для написания сложных сценариев, позволяющих оптимизировать рабочий процесс. Учтите, что командлеты можно использовать, даже не являясь администратором клиента, но сфера их действия будет ограничена только теми ресурсами, которыми вы владеете. Командлеты, начинающиеся со слова Admin, предназначены для использования учетной записью администратора.

Командлеты доступны в коллекции PowerShell в виде двух разных модулей: 
- [Administrator](https://www.powershellgallery.com/packages/Microsoft.PowerApps.Administration.PowerShell/2.0.1)
- [Maker](https://www.powershellgallery.com/packages/Microsoft.PowerApps.PowerShell/1.0.1) 

## <a name="installation"></a>Установка
Прежде чем выполнять командлеты PowerShell для создателей приложений, выполните указанные ниже действия.

1. Запустите PowerShell от имени администратора.

   > [!div class="mx-imgBorder"] 
   > ![Запуск PowerShell от имени администратора](media/open-powershell-as-admin75.png "Run PowerShell as an administrator")

2. Импортируйте необходимые модули, используя следующие команды:

    ```
    Install-Module -Name Microsoft.PowerApps.Administration.PowerShell
    Install-Module -Name Microsoft.PowerApps.PowerShell -AllowClobber
    ```
3. Если будет предложено принять изменение в значении *InstallationPolicy* репозитория, примите вариант [А] "Да" для всех модулей. Для этого введите "A" и нажмите клавишу **ВВОД** для каждого модуля.

   ![Примите значение InstallationPolicy](media/accept-installationpolicy-value75.png "Accept InstallationPolicy value")

4. Прежде чем обращаться к любой из команд, можно предоставить свои учетные данные, используя команду ниже. Эти учетные данные обновляются максимум за 8 часов, прежде чем вам потребуется снова войти в систему, чтобы продолжить использование командлетов.

    ```
    # This call opens prompt to collect credentials (Azure Active Directory account and password) used by the commands 
    Add-PowerAppsAccount
    ```

    ```
    # Here is how you can pass in credentials (avoiding opening a prompt)
    $pass = ConvertTo-SecureString "password" -AsPlainText -Force
    Add-PowerAppsAccount -Username foo@bar.com -Password $pass
    ```

## <a name="powerapps-cmdlets-for-app-creators-preview"></a>Командлеты PowerApps для создателей приложений (предварительная версия)

### <a name="prerequisite"></a>Необходимое условие
Пользователи с действующей лицензией PowerApps могут выполнять операции в этих командлетах. При этом они будут иметь доступ только к ресурсам (например, приложениям, потокам и т. д.), которые были созданы или предоставлены им для общего доступа.

### <a name="cmdlet-list---maker-cmdlets"></a>Список командлетов — командлеты модуля Maker
> [!NOTE]
> В последнем выпуске мы обновили некоторые из имен функций командлетов, добавив подходящие префиксы для предотвращения конфликтов. Обзор изменений см. в таблице ниже.

| Цель | Командлет |
| --- | --- |
| Чтение сред | Get-PowerAppEnvironment *(ранее Get-PowerAppsEnvironment)* <br> Get-FlowEnvironment |
| Чтение, обновление и удаление приложения на основе холста | Get-PowerApp *(ранее Get-App)* <br> Remove-PowerApp *(ранее Remove-App)* <br> Publish-PowerApp *(ранее Publish-App)* <br> Set-AppDisplayName *(ранее Set-PowerAppDisplayName)*<br> Get-PowerAppVersion *(ранее Get-AppVersion)* <br> Restore-PowerAppVersion *(ранее Restore-AppVersion)* |
| Чтение, обновление и удаление разрешений приложений на основе холста | Get-PowerAppRoleAssignment *(ранее Get-AppRoleAssignment)* <br> Set-PowerAppRoleAssignment *(ранее Set-AppRoleAssignment)* <br> Remove-PowerAppRoleAssignment *(ранее Remove-AppRoleAssignment)* |
| Read, update, and delete a flow | Get-Flow <br> Get-FlowRun <br> Enable-Flow <br> Disable-Flow <br> Remove-Flow |
| Чтение, обновление и удаление разрешений потоков | Get-FlowOwnerRole <br> Set-FlowOwnerRole <br> Remove-FlowOwnerRole |
| Чтение и ответ на утверждения потоков | Get-FlowApprovalRequest <br> Get-FlowApproval <br> RespondTo-FlowApprovalRequest |
| Чтение и удаление соединений | Get-PowerAppConnection *(ранее Get-Connection)* <br> Remove-PowerAppConnection *(ранее Remove-Connection)* |
| Чтение, обновление и удаление разрешений соединений | Get-PowerAppConnectionRoleAssignment *(ранее Get-ConnectionRoleAssignment)* <br> Set-PowerAppConnectionRoleAssignment *(ранее Set-ConnectionRoleAssignment)* <br> Remove-PowerAppConnectionRoleAssignment *(ранее Remove-ConnectionRoleAssignment)* |
| Чтение и удаление соединителей | Get-PowerAppConnector *(ранее Get-Connector)* <br> Remove-PowerAppConnector *(ранее Remove-Connector)* |
| Чтение, обновление и удаление пользовательских разрешений соединителей | Get-PowerAppConnectorRoleAssignment *(ранее Get-ConnectorRoleAssignment)* <br> Set-PowerAppConnectorRoleAssignment *(ранее Set-ConnectorRoleAssignment)* <br> Remove-PowerAppConnectorRoleAssignment *(ранее Remove-ConnectorRoleAssignment)* |

## <a name="powerapps-cmdlets-for-administrators-preview"></a>Командлеты PowerApps для администраторов (предварительная версия)

### <a name="prerequisite"></a>Необходимое условие
Чтобы выполнить операции администрирования в командлетах администратора, понадобится следующее:

* Платная лицензия PowerApps (план 2) или лицензия на пробную версию PowerApps (план 2). Вы можете зарегистрироваться для бесплатного использования 30-дневной пробной лицензии здесь: [http://web.powerapps.com/trial](http://web.powerapps.com/trial). Лицензии на пробную версию можно продлить по истечении их срока действия.

* Права [глобального администратора Office 365](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) или [глобального администратора Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal), если вам нужно выполнить поиск по ресурсам другого пользователя. (Помните, что администраторы среды имеют доступ только к тем средам и ресурсам среды, на которые у них есть разрешения.)

### <a name="cmdlet-list---admin-cmdlets"></a>Список командлетов — командлеты модуля Admin

| Цель | Командлеты
| --- | ---
| Чтение, обновление и удаление сред и баз данных службы Common Data Service for Apps | New-AdminPowerAppEnvironment <br> Set-AdminPowerAppEnvironmentDisplayName <br> Get-AdminPowerAppEnvironment *(ранее Get-AdminEnvironment)* <br> Remove-AdminPowerAppEnvironment *(ранее Remove-AdminEnvironment)* <br> New-AdminPowerAppCdsDatabase <br> Get-AdminPowerAppCdsDatabaseLanguages <br> Get-AdminPowerAppCdsDatabaseCurrencies <br> Get-AdminPowerAppEnvironmentLocations |
| Удаление базы данных CDS | Remove-LegacyCDSDatabase **\*новый\*** | 
| Чтение, обновление и удаление разрешений среды <br><br> *Эти командлеты сейчас работают только в средах без базы данных Common Data Service (CDS) for Apps.* | Get-AdminPowerAppEnvironmentRoleAssignment *(ранее Get-AdminEnvironmentRoleAssignment)* <br> Set-AdminPowerAppEnvironmentRoleAssignment *(ранее Set-AdminEnvironmentRoleAssignment)* <br> Remove-AdminPowerAppEnvironmentRoleAssignment *(ранее Remove-AdminEnvironmentRoleAssignment)* |
| Чтение, обновление и удаление приложений на основе холста | Get-AdminPowerApp *(ранее Get-AdminApp)* <br> Remove-AdminPowerApp *(ранее Remove-AdminApp)* <br> Get-AdminPowerAppConnectionReferences <br> Set-AdminPowerAppAsFeatured <br> Clear-AdminPowerAppAsFeatured <br> Set-AdminPowerAppAsHero <br> Clear-AdminPowerAppAsHero <br> Set-AdminPowerAppApisToBypassConsent <br> Clear-AdminPowerAppApisToBypassConsent |
| Чтение, обновление и удаление разрешений приложений на основе холста | Get-AdminPowerAppRoleAssignment *(ранее Get-AdminAppRoleAssignment)* <br> Remove-AdminPowerAppRoleAssignment *(ранее Remove-AdminAppRoleAssignment)* <br> Set-AdminPowerAppRoleAssignment *(ранее Set-AdminAppRoleAssignment)* <br> Set-AdminPowerAppOwner *(ранее Set-AdminAppOwner)* |
| Чтение, обновление и удаление потоков | Get-AdminFlow <br> Enable-AdminFlow <br> Disable-AdminFlow <br> Remove-AdminFlow <br> Remove-AdminFlowApprovals |
| Чтение, обновление и удаление разрешений потоков | Get-AdminFlowOwnerRole <br> Set-AdminFlowOwnerRole <br> Remove-AdminFlowOwnerRole |
| Чтение и удаление соединений | Get-AdminPowerAppConnection *(ранее Get-AdminConnection)* <br> Remove-AdminPowerAppConnection *(ранее Remove-AdminConnection)* |
| Чтение, обновление и удаление разрешений соединений | Get-AdminPowerAppConnectionRoleAssignment *(ранее Get-AdminConnectionRoleAssignment)* <br> Set-AdminPowerAppEnvironmentConnectionRoleAssignment *(ранее Set-AdminConnectionRoleAssignment)* <br> Remove-AdminPowerAppConnectionRoleAssignment *(ранее Remove-AdminConnectionRoleAssignment)* |
| Получение и удаление пользовательских соединителей | Get-AdminPowerAppConnector *(ранее Get-AdminConnector)* <br> Remove-AdminPowerAppConnector *(ранее Remove-AdminConnector)* |
| Чтение, обновление и удаление пользовательских разрешений соединителей | Get-AdminPowerAppConnectorRoleAssignment *(ранее Get-AdminConnectorRoleAssignment)*<br> Set-AdminPowerAppConnectorRoleAssignment *(ранее Set-AdminConnectorRoleAssignment)* <br> Remove-AdminPowerAppConnectorRoleAssignment *(ранее Remove-AdminConnectorRoleAssignment)* |
| Чтение параметров пользователя, параметров приложения пользователя и уведомлений PowerApps | Get-AdminPowerAppsUserDetails |
| Чтение и удаление параметров Microsoft Flow пользователя, которые не видны ему, но поддерживают выполнение потока | Get-AdminFlowUserDetails <br> Remove-AdminFlowUserDetails |
| Создание, чтение, обновление и удаление политик защиты от потери данных для вашей организации | Get-AdminDlpPolicy *(ранее Get-AdminApiPolicy)* <br> New-AdminDlpPolicy *(ранее Add-AdminApiPolicy)* <br> Remove-AdminDlpPolicy *(ранее Remove-AdminApiPolicy)* <br> Set-AdminDlpPolicy *(ранее Set-AdminApiPolicy)* <br> Add-ConnectorToBusinessDataGroup <br>  Remove-ConnectorFromBusinessDataGroup <br/>Add-CustomConnectorToPolicy<br/> Remove-CustomConnectorFromPolicy|

## <a name="tips"></a>Советы

- Используйте команду Get-Help <Имя_командлета>, чтобы получить список примеров.

     ![Команда Get-Help](media/get-help-cmdlet.png "Get-Help command")

- Чтобы пролистать список возможных вариантов для входных тегов, нажмите клавишу TAB после ввода символа дефиса (-) после имени командлета.

Примеры команд:

```
Get-Help Get-AdminPowerAppEnvironment
Get-Help Get-AdminPowerAppEnvironment -Examples
Get-Help Get-AdminPowerAppEnvironment -Detailed
```

## <a name="operation-examples"></a>Примеры операций

Ниже приведены некоторые распространенные сценарии, которые демонстрируют использование новых и существующих командлетов PowerApps.

- [Команды среды](#environments-commands)
- [Команды PowerApps](#powerapps-commands)
- [Команды Flow](#flow-commands)
- [Команды подключения API](#api-connection-commands)
- [Команды политики защиты от потери данных (DLP)](#data-loss-prevention-dlp-policy-commands)

### <a name="environments-commands"></a>Команды среды

Эти команды служат для получения сведений о среде и изменения ее параметров в клиенте.

#### <a name="display-a-list-of-all-environments"></a>Вывод списка всех сред

```
Get-AdminPowerAppEnvironment
```

Возвращает список всех сред в клиенте с подробными сведениями о каждой среде (например, имя среды (GUID), отображаемое имя, расположение, автор и т. д.).

#### <a name="display-details-of-your-default-environment"></a>Отображение подробных сведений о среде по умолчанию

```
Get-AdminPowerAppEnvironment –Default
```

Возвращает подробные сведения только об одной среде по умолчанию клиента.

#### <a name="display-details-of-a-specific-environment"></a>Отображение подробных сведений о конкретной среде

```
Get-AdminPowerAppEnvironment –EnvironmentName ‘EnvironmentName’
```

**Примечание**. Поле *EnvironmentName* — это уникальный идентификатор, который отличается от *DisplayName* (см. первое и второе поле в выходных данных на следующем рисунке).

![Команда Get-AdminEnvironment](media/get-adminenvironment.png "Get-AdminEnvironment command")

### <a name="powerapps-commands"></a>Команды PowerApps

Эти операции используются для чтения и изменения данных PowerApps в клиенте.

#### <a name="display-a-list-of-all-powerapps"></a>Вывод списка всех приложений PowerApps

```
Get-AdminPowerApp
```

Возвращает список всех приложений PowerApps для клиента с подробными сведениями о каждом (например, имя приложения (GUID), отображаемое имя, автор и т. д.).

#### <a name="display-a-list-of-all-powerapps-that-match-the-input-display-name"></a>Отображение списка всех приложений PowerApps, которые соответствуют входному отображаемому имени

```
Get-AdminPowerApp 'DisplayName'
```

Возвращает список всех приложений PowerApps в клиенте, которые соответствуют отображаемому имени. 

**Примечание**. Используйте символы кавычек (") вокруг входных значений, содержащих пробелы.

#### <a name="feature-an-application"></a>Добавление приложения в подборку

```
Set-AdminPowerAppAsFeatured –AppName 'AppName'
```

Популярные приложения группируются и помещаются в верхнюю часть списка в мобильном проигрывателе PowerApps.

**Примечание**. Аналогично средам, поле *AppName* — это уникальный идентификатор, который отличается от *DisplayName*. Если вы хотите выполнить операции, основанные на отображаемом имени, некоторые функции позволят вам использовать конвейер (см. следующую функцию).

#### <a name="make-an-application-a-hero-app-using-the-pipeline"></a>Преобразование приложения в главное имиджевое приложение с помощью конвейера

```
Get-AdminPowerApp 'DisplayName' | Set-AdminPowerAppAsHero
```

Главное имиджевое приложение будет отображаться в верхней части списка в мобильном проигрывателе PowerApps. Может существовать только одно главное имиджевое приложение.

Конвейер (представленный в виде символа "|" между двумя командлетами) принимает выходные данные первого командлета и передает его в качестве входного значения второго, при условии что функция поддерживает возможности конвейера.

**Примечание**. Приложение уже должно быть популярным приложением для его преобразования в главное имиджевое приложение.

#### <a name="display-the-number-of-apps-each-user-owns"></a>Отображение числа приложений, принадлежащих каждому пользователю

```
Get-AdminPowerApp | Select –ExpandProperty Owner | Select –ExpandProperty displayname | Group
```

Собственные функции PowerShell можно объединить с командлетами PowerApps для расширенного управления данными. Здесь мы используем функцию Select, чтобы изолировать атрибут Owner (объект) от объекта Get-AdminApp. Затем мы изолируем имя объекта владельца путем передачи этих выходных данных по конвейеру в другую функцию Select. Наконец, при передаче второго набора выходных данных функции Select в функцию Group возвращается неплохая таблица, содержащая количество приложений каждого владельца.

![Команда Get-AdminPowerApp](media/get-adminpowerapp.png "Get-AdminPowerApp command")

#### <a name="display-the-number-of-apps-in-each-environment"></a>Отображение количества приложений в каждой среде

```
Get-AdminPowerApp | Select -ExpandProperty EnvironmentName | Group | %{ New-Object -TypeName PSObject -Property @{ DisplayName = (Get-AdminPowerAppEnvironment -EnvironmentName $_.Name | Select -ExpandProperty displayName); Count = $_.Count } }
```

![Команда Get-AdminPowerApp](media/get-adminpowerapp-environment.png "Get-AdminPowerApp command")

#### <a name="download-powerapps-user-details"></a>Загрузка сведений о пользователе PowerApps

```
Get-AdminPowerAppsUserDetails -OutputFilePath '.\adminUserDetails.txt' –UserPrincipalName ‘admin@bappartners.onmicrosoft.com’
```

Приведенная выше команда сохраняет сведения о пользователе PowerApps (базовые сведения об использовании для пользователя по имени участника-пользователя) в указанном текстовом файле. Она создает новый файл в том случае, если существующий файл с таким именем отсутствует, и перезаписывает текстовый файл, если он уже существует.

#### <a name="set-logged-in-user-as-the-owner-of-a-powerapp"></a>Задание вошедшего в систему пользователя как владельца PowerApp

```
Set-AdminPowerAppOwner –AppName 'AppName' -AppOwner $Global:currentSession.userId –EnvironmentName 'EnvironmentName'
```

Изменяет роль владельца PowerApp, назначая ее текущему пользователю, и заменяет тип роли исходного владельца типом "может просматривать".

**Примечание**. Поля AppName и EnvironmentName являются уникальными идентификаторами (GUID), а не отображаемыми именами.

### <a name="flow-commands"></a>Команды Flow

Используйте следующие команды для просмотра и изменения данных, связанных с Microsoft Flow.

#### <a name="display-all-flows"></a>Отображение всех потоков

```
Get-AdminFlow
```

Возвращает список всех потоков в клиенте.

#### <a name="display-flow-owner-role-details"></a>Отображение сведений о роли владельца потока

```
Get-AdminFlowOwnerRole –EnvironmentName 'EnvironmentName' –FlowName ‘FlowName’
```

Возвращает сведения о владельце указанного потока.

**Примечание**. Аналогично *средам* и *PowerApps*, поле *FlowName* является уникальным идентификатором (GUID), который отличается от отображаемого имени потока.

#### <a name="display-flow-user-details"></a>Отображение сведений о пользователе потока

```
Get-AdminFlowUserDetails –UserId $Global:currentSession.userId
```

Возвращает сведения о пользователе, касающиеся использования потоков. В этом примере в качестве входных данных мы используем идентификатор текущего пользователя, выполнившего вход в сеанс PowerShell.

#### <a name="remove-flow-user-details"></a>Удаление сведений о пользователе потока

```
Remove-AdminFlowUserDetails –UserId 'UserId'
```

Сведения о пользователе потока полностью удаляются из базы данных Майкрософт. Все потоки, которые принадлежат указанному пользователю, должны быть удалены, прежде чем можно будет очистить данные о пользователе потока.

**Примечание**. Поле UserId — это идентификатор объекта записи Azure Active Directory пользователя, который можно найти на [портале Azure](https://portal.azure.com) в разделе **Azure Active Directory** > **Пользователи** > **Профиль** > **Идентификатор объекта**. Эти данные на портале доступны только администраторам.

#### <a name="export-all-flows-to-a-csv-file"></a>Экспорт всех потоков в CSV-файл

```
Get-AdminFlow | Export-Csv -Path '.\FlowExport.csv'
```

Экспортирует все потоки в клиенте в CSV-файл табличного представления.

### <a name="api-connection-commands"></a>Команды подключения API

Просмотр и управление подключениями API в клиенте.

#### <a name="display-all-native-connections-in-your-default-environment"></a>Отображение всех собственных подключений в среде по умолчанию

```
Get-AdminPowerAppEnvironment -Default | Get-AdminConnection
```

Отображает список всех подключений API в среде по умолчанию. Собственные подключения будут указаны на вкладке **Данные** > **Подключения** на портале разработчика.

#### <a name="display-all-custom-connectors-in-the-tenant"></a>Отображение всех пользовательских соединителей в клиенте

```
Get-AdminPowerAppConnector
```

Возвращает список сведений обо всех пользовательских соединителях в клиенте.

### <a name="data-loss-prevention-dlp-policy-commands"></a>Команды политики защиты от потери данных (DLP)

Эти командлеты будут контролировать политики защиты от потери данных для клиента.

#### <a name="display-all-policies"></a>Отображение всех политик

```
Get-AdminDlpPolicy
```

Возвращает список всех политик.

#### <a name="display-a-filtered-list-of-policies"></a>Отображение фильтрованного списка политик

```
Get-AdminDlpPolicy 'DisplayName'
```

Использует отображаемое имя для фильтрации политик

#### <a name="display-all-business-data-only-api-connectors-in-a-policy"></a>Отображение всех соединителей API "Только бизнес-данные" в политике

```
Get-AdminDlpPolicy 'PolicyName' | Select –ExpandProperty BusinessDataGroup
```

Список подключений API, которые находятся в поле *Только бизнес-данные* (или *BusinessDataGroup*) в политике ввода.

#### <a name="add-a-connector-to-the-business-data-only-group"></a>Добавление соединителя в группу "Только бизнес-данные"

```
Add-ConnectorToBusinessDataGroup -PolicyName 'PolicyName' –ConnectorName 'ConnectorName'
```

Добавляет соединитель в группу "Только бизнес-данные" в одной политике защиты от потери данных. Здесь можно просмотреть список соединителей по отображаемому имени *DisplayName* и имени соединителя *ConnectorName* (используется в качестве входных данных).

## <a name="version-history"></a>Журнал версий
| Версия | Date | Обновления |
| --- | --- | --- |
| 1.0 | 23.04.2018 | <ol> <li> Начальный запуск командлетов PowerApps для создателей приложений (предварительная версия), включая командлеты управления для сред, приложений, потоков, утверждения потоков, соединений и настраиваемых соединителей </li> <li> Начальный запуск командлетов PowerApps для администраторов (предварительная версия), включая командлеты администрирования для сред, приложений и потоков </li></ol>|
| 2.0 | 24.05.2018 | <ol> <li> Исправления незначительных ошибок в командлетах для создателей и администраторов приложений </li> <li> Добавлены следующие новые командлеты администрирования: <br> Get-AdminConnection <br> Remove-AdminConnection <br> Get-AdminConnectionRoleAssignment <br> Set-AdminConnectionRoleAssignment <br>Remove-AdminConnectionRoleAssignment <br>Get-AdminConnector  <br>Remove-AdminConnector <br>Set-AdminConnectorRoleAssignment  <br>Get-AdminConnectorRoleAssignment  <br>Remove-AdminConnectorRoleAssignment <br>Get-AdminPowerAppsUserDetails <br>Get-AdminFlowUserDetails <br>Remove-AdminFlowUserDetails <br>Get-AdminApiPolicy  <br>Add-AdminApiPolicy <br>Remove-AdminApiPolicy <br>Set-AdminApiPolicy <br>Add-ConnectorToBusinessDataGroup  <br>Remove-ConnectorFromBusinessDataGroup </li> </ol>
| 3.0 | 30.07.2018 | <ol> <li> Добавлена возможность передачи учетных данных в Add-PowerAppsAccount (для включения повторяющихся скриптов) </li> <li>  Исправления незначительных ошибок в командлетах для создателей и администраторов приложений </li> <li> Добавлен префикс "PowerApp" или "Flow" в каждый командлет для создателей приложений </li> <li>  Добавлен префикс "AdminPowerApp" или "AdminFlow" в каждый командлет для администраторов </li> <li> Добавлены следующие новые командлеты администрирования: <br> New-AdminPowerAppEnvironment <br> Set-AdminPowerAppEnvironmentDisplayName <br> New-AdminPowerAppCdsDatabase <br> Get-AdminPowerAppCdsDatabaseLanguages <br> Get-AdminPowerAppCdsDatabaseCurrencies <br> Get-AdminPowerAppEnvironmentLocations <br> Get-AdminPowerAppConnectionReferences <br> Set-AdminPowerAppAsFeatured <br> Clear-AdminPowerAppAsFeatured <br> Set-AdminPowerAppAsHero <br> Clear-AdminPowerAppAsHero <br> Set-AdminPowerAppApisToBypassConsent <br> Clear-AdminPowerAppApisToBypassConsent <br> Remove-AdminFlowApprovals </li></ol>
| 4.0 | 15.08.2018 | Добавлен необязательный параметр в New-AdminPowerAppCdsDatabase для синхронизации функции по умолчанию (т. е. она не вернется до успешной подготовки базы данных)
| 5.0 | 24.08.2018 | Исправлена проблема, при которой командлеты для администраторов потока не возвращали данные по использованию в зависимости от параметры безопасности
| 6.0 | 09.01.2019 | <ol><li>Командлеты теперь доступны в коллекции PowerShell в виде двух разных модулей: Administrator и Maker.</li> <li>Добавлен командлет администрирования: Remove-LegacyCDSDatabase</li><li> Добавлены примеры операций</li><li>Добавлена возможность управления соединителями HTTP и пользовательскими соединителями в политике защиты от потери данных (DLP)</li></ol>|

## <a name="questions"></a>Вопросы?

Если у вас есть какие-либо комментарии, предложения или вопросы, опубликуйте их на [доске сообщества администрирования PowerApps](https://powerusers.microsoft.com/t5/Administering-PowerApps/bd-p/Admin_PowerApps).
