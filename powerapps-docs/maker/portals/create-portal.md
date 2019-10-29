---
title: Создание портала в PowerApps | Документация Майкрософт
description: Инструкции по созданию портала в PowerApps.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 92ba08e47d3f0d657330ac3fcc6885626ff4a9e5
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975341"
---
# <a name="create-a-common-data-service-starter-portal"></a>Создание Common Data Service начального портала

С помощью возможности создания портала в PowerApps можно создать веб-сайт для внешних и внутренних пользователей, что позволит им взаимодействовать с данными, хранящимися в Common Data Service.

Ниже приведены некоторые преимущества создания портала.

- Поскольку данные хранятся в Common Data Service, вам не нужно создавать подключение из PowerApps так же, как и с такими источниками данных, как SharePoint, приложениями, управляемыми моделью, в Dynamics 365 или Salesforce. Необходимо только указать сущности, которые требуется отображать на портале или управлять ими.

- Вы можете спроектировать портал в студии WYSIWYG PowerApps, добавив и настроив компоненты на веб-страницах.

Портал можно создать либо в новой среде, либо в существующей среде.

Если вы решили создать портал в новой среде с помощью ссылки **создать новую среду** , необходимые предварительные требования для портала, такие как сущности, данные и шаблон начального портала, будут установлены при создании среды. В этом методе портал подготавливается через несколько минут.

Если вы решили создать портал в существующей среде без предварительных требований к порталу, предварительные требования устанавливаются первыми, а затем создается портал. В этом методе подготовка портала может занять некоторое время, и вы будете уведомлены о подготовке портала.

Вы можете создать Common Data Service начальный портал или портал Dynamics 365 в PowerApps на основе выбранной среды.

Дополнительные сведения о работе с средами: [Работа с средами и Microsoft PowerApps](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-environments)

Дополнительные сведения о доступных шаблонах портала: [шаблоны портала](portal-templates.md)

Чтобы создать портал, выполните следующие действия.

1.  Войдите в [PowerApps](http://web.powerapps.com).  

2.  В разделе **Создание собственного приложения**выберите **портал из пустого**списка.

3.  Если выбранная среда не содержит необходимых компонентов портала, в **пустом окне портала** отобразится сообщение с предложением выбрать другую среду или создать новую.

    > [!div class=mx-imgBorder]
    > ![создать сообщение о новой среде](media/create-portal-message.png "создать сообщение о среде")

4.  Если вы решили продолжить работу с текущей средой, введите необходимые сведения в окне, как описано в следующих шагах. Если вы решили создать новую среду, см. раздел [Создание новой](#create-new-environment)среды.

5.  На **портале из пустого** окна введите имя портала и адрес веб-сайта, а затем выберите язык из раскрывающегося списка. Когда все будет готово, нажмите кнопку **создать**.

    > [!div class=mx-imgBorder]
    > ![Создание]портала создание нового(media/create-new-portal.png "портала")  

После выбора **создать**портал начнет подготовку, а состояние подготовки отобразится в [уведомлениях](#portal-provisioning-notifications).

Если вы создали портал в среде, в которой не установлены предварительные требования к порталу, состояние подготовки также отображается в сетке:

> [!div class=mx-imgBorder]
> (media/provision-progress-notif.png "Уведомление сетки") ![уведомлений сетки]

После успешного завершения подготовки портала состояние изменится, и портал отобразится в сетке:

> [!div class=mx-imgBorder]
> Подготовленный портал ![портала](media/recent-apps.png "подготовлен")

Чтобы изменить портал в PowerApps Portals Studio, см. статью [изменение портала](manage-existing-portals.md#edit).

> [!NOTE]
> - В клиенте можно создать не более пяти порталов. Однако в среде может быть только один портал каждого типа.
> - Если у вас недостаточно прав для предоставления портала, отображается сообщение об ошибке. Для создания портала необходимо иметь роль системного администратора в Common Data Service. Кроме того, необходимо установить **режим доступа** **чтение и запись** в разделе **сведения о клиентской лицензии (CAL)** в записи пользователя.
> - Если вы приобрели более старую надстройку портала и хотите подготавливать портал с помощью надстройки, необходимо посетить страницу **центра администрирования Dynamics 365** . Дополнительные сведения: [подготавливайте портал](https://docs.microsoft.com/en-gb/dynamics365/customer-engagement/portals/provision-portal)
> - Если вы подготовили портал с помощью более старой надстройки портала, вы по-прежнему можете настраивать ее и управлять ими из [make.powerapps.com](https://make.powerapps.com).
> - Подготовка порталов от [make.powerapps.com](https://make.powerapps.com) не использует более старые надстройки портала. Кроме того, эти порталы не отображаются на вкладке **приложения** на странице **центра администрирования Dynamics 365** .
> - Common Data Service начальный портал нельзя создать на странице **центра администрирования Dynamics 365** .
> - Порталы PowerApps недоступны в регионе Франции.

## <a name="create-new-environment"></a>Создать новое окружение

Выполните следующие действия при создании среды с помощью параметра, предоставленного на **портале, из пустого** окна.

1.  В области **Новая среда** введите имя среды, а затем выберите регион и тип среды из раскрывающихся списков. После создания среды изменить регион уже невозможно. Когда все будет готово, выберите **создать среду**.

    > [!div class=mx-imgBorder]
    > создать ![среду]создать(media/create-new-environment.png "новое") окружение  

2.  После создания среды в диалоговом окне появится сообщение с подтверждением, и вам будет предложено создать базу данных. Выберите **создать базу данных** , чтобы разрешить доступ к Common Data Service.

    > [!NOTE]
    > Запрос на создание базы данных может не отображаться автоматически. В этом случае необходимо вернуться в новую среду и снова выбрать **портал из пустой** плитки.

    > [!div class=mx-imgBorder]
    > ![Новая среда создала](media/new-environment-created.png "созданную среду")  

3.  Выберите валюту и язык для данных, хранящихся в базе данных. Вы не сможете изменить валюту или язык после создания базы данных. Когда все будет готово, выберите **создать мою базу данных**. База данных создается с помощью начального портала, который позволяет быстро начать работу с примером содержимого после подготовки портала.

    > [!NOTE]
    > Параметр **включить начальный портал** доступен только при создании среды с помощью параметра, предоставленного на **портале, из пустого** окна. Этот параметр недоступен при создании среды из центра администрирования PowerApps.

    > [!div class=mx-imgBorder]
    > ![создать новую базу данных](media/create-new-database.png "создать базу данных") 

    Создание базы данных на Common Data Service может занять несколько минут. После создания базы данных в списке сред на домашней странице PowerApps будет выбрана новая среда и создано приложение управления портала. Это приложение не является реальным порталом, но является сопутствующим приложением на основе моделей, которое позволяет выполнять дополнительные действия по настройке. Теперь можно приступить к созданию портала для проектирования внешнего веб-сайта.

    > [!div class=mx-imgBorder]
    > ![](media/portal-mgmt-app.png "приложение") управления портала приложений Управление порталом

4. После создания среды и базы данных в разделе **Создание собственного приложения**выберите **портал из пустого**списка. 

    > [!NOTE]
    > Если база данных создана и вы все еще получаете запрос на создание базы данных, необходимо обновить домашнюю страницу PowerApps, прежде чем выбирать **портал из пустой** плитки.


## <a name="portal-provisioning-notifications"></a>Уведомления о подготовке портала

После выбора **создать**портал начнет подготовку, а состояние подготовки отобразится в уведомлениях.

**Уведомление в виде всплывающего уведомления**

При выборе **создать** для инициализации портала отображается следующее уведомление.

> [!div class=mx-imgBorder]
> ![](media/toast-notif.png "Всплывающее уведомление") всплывающего уведомления 

**Уведомления на панели "уведомления"**

После успешного размещения запроса на подготовку в области **уведомлений** отобразятся следующие уведомления.

Уведомление, отображаемое для выполнения подготовки

> [!div class=mx-imgBorder]
> (media/pane-notif.png "Уведомление") панели ![уведомлений панели] 

Уведомление, отображаемое для подготовки, успешно завершено

> [!div class=mx-imgBorder]
> (media/provision-complete-notif.png "Уведомление об успешном завершении") подготовки ![уведомления об успешном выполнении] 

Если подготовка портала завершается неудачно, уведомления отображаются аналогичным образом.
  
**Уведомления по электронной почте**

После успешного размещения запроса на подготовку пользователю будет отправлено уведомление по электронной почте с просьбой создать портал. Кроме того, после завершения подготовки портала пользователю отправляется сообщение электронной почты.

## <a name="disable-portal-creation-in-a-tenant"></a>Отключение создания портала в клиенте

Как глобальный администратор, если вы хотите отключить создание портала в клиенте без прав администратора, это можно сделать, включив параметр уровня клиента `disablePortalsCreationByNonAdminUsers` с помощью PowerShell. Чтобы запустить командлеты PowerShell, необходимо сначала установить необходимые модули. Сведения об установке необходимых модулей PowerShell см. в разделе [Установка](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-powershell#installation).

После установки модулей выполните следующую команду в окне PowerShell (запустите PowerShell от имени администратора).

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $true }
```

Администраторы — это пользователи с одной из следующих ролей Azure:

- Глобальный администратор
- Администратор службы Dynamics 365
- Администратор службы Power Platform

Пользователи, не имеющие указанных выше ролей Azure, считаются не являющимися администраторами.

Если создание портала отключено в клиенте, неадминистраторы увидят ошибку следующим образом:

> [!div class=mx-imgBorder]
> ![Создание портала. заблокированная]ошибка(media/portal-create-blocked-error.png "при создании портала")