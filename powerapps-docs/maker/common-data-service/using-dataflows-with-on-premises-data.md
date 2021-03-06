---
title: Использование локального шлюза данных в потоках данных Power Platform | Документация Майкрософт
description: Узнайте, как пользоваться локального шлюза данных в потоках данных Power Platform
ms.custom: ''
ms.date: 08/05/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: ''
caps.latest.revision: ''
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0b534e3c4a7aae36d38901b75b34cc87fd7f511e
ms.sourcegitcommit: 64d816a759c5cc6343928d56a673812c3ea066c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/06/2019
ms.locfileid: "2895255"
---
# <a name="using-an-on-premises-data-gateway-in-power-platform-dataflows"></a>Использование локального шлюза данных в потоках данных Power Platform

Установите локальный шлюз данных для быстрой и безопасной передачи данных между потоком данных Power Platform и источником данных, который не находится в облаке, таким как локальная база данных сервера SQL или локальный сайт SharePoint.
Можно просматривать все шлюзы, для которых у вас есть административные разрешения, и управлять разрешениями и соединениями для этих шлюзов.

С помощью шлюза можно подключаться к локальным данным через эти соединения:

-   SharePoint

-   SQL Server

-   Oracle

-   Informix

-   Filesystem

-   DB2

## <a name="prerequisites"></a>Необходимые компоненты

-   Учетная запись Power Apps. Нет ни одной из них? [Зарегистрируйтесь на 30 дней бесплатно](https://docs.microsoft.com/powerapps/maker/signup-for-powerapps).

-   Административные разрешения на шлюзе. Эти разрешения предоставляются по умолчанию для устанавливаемых вами шлюзов. Администраторы могут предоставлять другим пользователям разрешения для шлюзов. 

-   Лицензия, которая поддерживает доступ к локальным данным с использованием локального шлюза. Для получения дополнительной информации см. раздел «Подключение к вашим данным и системам» на странице [Найди свой план Power Apps](https://powerapps.microsoft.com/pricing/).

-   Шлюзы и локальные соединения могут создаваться и использоваться только в пользовательской среде по умолчанию. Дополнительные сведения см. в разделе [Работа со средами и Microsoft Power Apps](../canvas-apps/working-with-environments.md).

## <a name="install-a-gateway"></a>Установка шлюза
1.  В левой области навигации на странице [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) выберите **Шлюзы**.

    ![Шлюзы в левой области навигации](media/nav-pane-gateways.png)

2.  Выберите шлюз из списка. Если у вас нет прав администратора для шлюза, выберите [Установить шлюз сейчас](https://go.microsoft.com/fwlink/?LinkID=820931), и следуйте инструкциям мастера.

     ![Установка шлюзов](media/install-gateway-now.png)

     Для получения дополнительной информации о том, как настроить шлюз, см. раздел [Общие сведения о локальных шлюзах данных](../canvas-apps/gateway-reference.md).

## <a name="use-an-on-premises-data-source-in-a-dataflow"></a>Использовать локальный источник данных в потоке данных
1. Выберите локальный источник данных из списка источников данных.

   ![Выберите локальный источник данных](media/on-premises-data-sources.png)

2. Укажите сведения о соединении для корпоративного шлюза, который будет использоваться для доступа к локальным данным. Необходимо выбрать сам шлюз и предоставить учетные данные для выбранного шлюза. В списке отображаются только шлюзы, для которых вы являетесь администратором.

    ![Укажите сведения о подключении](media/connection-creds.png)

Можно изменить корпоративный шлюз, используемый для данного потока данных, и изменить шлюз, назначенный для всех ваших запросов, с помощью инструмента разработки потока данных.

> [!NOTE]
> Поток данных попробует найти или создавать необходимые источники данных с помощью новый шлюз. Если это невозможно, пользователь не сможет изменить шлюз, пока все необходимые потоки данных не будут доступны с выбранного шлюза.


## <a name="view-and-manage-gateway-permissions"></a>Просмотр и управление разрешениями шлюза
1.  В левой области навигации на странице [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) выберите **Шлюзы**, а затем выберите нужный шлюз.

2.  Чтобы добавить пользователя в шлюз, выберите **Пользователи**, укажите пользователя или группу, а затем укажите уровень разрешений:

    -   **Можно использовать.** Пользователи с этим разрешением могут создавать соединения на шлюзе, чтобы использовать их для приложений и потоков, но не могут совместно использовать шлюз. Используйте это разрешение для пользователей, которые будут запускать приложения, но не будут делиться ими.

    -   **Можно использовать + общий доступ.** Пользователи с этим разрешением могут создавать на шлюзе соединение для приложений и потоков и автоматически предоставлять общий доступ к шлюзу при совместном использовании приложения. Используйте это разрешение для пользователей, которым необходимо предоставить доступ к приложениям другим пользователям или организации.

    -   **Администратор.** Администраторы имеют полный контроль над шлюзом, включая добавление пользователей, настройку разрешений, создание соединений со всеми доступными источниками данных и удаление шлюза.

      Для уровней разрешения **Можно использовать** и **Можно использовать + общий доступ** выберите источники данных, к которым пользователь может подключиться через шлюз.

## <a name="view-and-manage-gateway-connections"></a>Просмотр и управление соединениями шлюза
1.  На левой панели навигации на странице *powerapps.com* выберите **Шлюзы**, а затем выберите нужный шлюз.

2.  Выполните необходимое действие: 
    - Чтобы просмотреть сведения, отредактировать настройки или удалить шлюз, выберите **Соединения**, после чего выберите соединение.
    - Чтобы поделиться подключением, выберите **Общий доступ**, а затем добавьте или удалите пользователей.

      > [!NOTE]
      > Вы можете использовать только некоторые типы соединений, например, соединение SQL Server. Чтобы получить дополнительные сведения, см. раздел [Поделиться ресурсами приложения на основе холста в Power Apps](../canvas-apps/share-app-resources.md). <br />
      >
      > Дополнительные сведения о том, как управлять подключением, см. в разделе [Управление соединениями приложения на основе холста в Power Apps](../canvas-apps/add-manage-connections.md).


## <a name="limitations"></a>Ограничения
Существует несколько известных ограничений при использовании корпоративных шлюзов и потоков данных.

-   Каждый поток данных может использовать только один шлюз. Таким образом, все запросы должны быть настроены с использованием одного и того же шлюза.

-   Изменение шлюза влияет на весь поток данных.

-   При потребности в несколько шлюзов рекомендуется создать несколько потоков данных (по одному для каждого шлюза) и использовать возможности вычисления или ссылки на сущности для унификации данных.

-   Потоки данных поддерживаются только с использованием корпоративных шлюзов. Персональные шлюзы не будут доступны для выбора в раскрывающихся списках и экранах настроек.

Информацию об устранении неполадок со шлюзами или о настройке службы шлюзов для вашей сети см. в разделе [Общие сведения о локальных шлюзов данных](../canvas-apps/gateway-reference.md).

## <a name="next-steps"></a>Дальнейшие шаги

- [Создание и использование потоков данных в Power Apps](create-and-use-dataflows.md)

- [Добавление данных в сущность в Common Data Service с помощью Power Query](data-platform-cds-newentity-pq.md)

- [Подключение Azure Data Lake Storage 2-го поколения для хранения потока данных](/power-bi/service-dataflows-connect-azure-data-lake-storage-gen2)


