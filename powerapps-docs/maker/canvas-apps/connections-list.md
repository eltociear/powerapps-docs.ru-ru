---
title: Общие сведения о соединителях для приложений на основе холста | Документы Майкрософт
description: Обзор всех доступных подключений, которые можно использовать для создания приложений на основе холста
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/28/2017
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 907ac3cf53709edd5a8b523479ec99816c6eec9c
ms.sourcegitcommit: 0f0b26122be28d674af0833247b491e9367c4932
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73897839"
---
# <a name="overview-of-canvas-app-connectors-for-powerapps"></a>Общие сведения о соединителях для приложений на основе холста в PowerApps
Большинство приложений основываются на данных, в том числе и те, которые создаются в PowerApps. Эти данные хранятся в *источниках данных*. Вы переносите их в приложение при создании *подключения*. Для подключения используется определенный *соединитель*, который обеспечивает обмен данными с источником данных. В PowerApps есть соединители для многих популярных служб и локальных источников данных, включая SharePoint, SQL Server, Office 365, Salesforce и Twitter. Чтобы начать добавлять данные в приложение на основе холста, ознакомьтесь со статьей [Добавление подключения к данным в PowerApps](add-data-connection.md).

Соединитель может предоставлять **таблицы** данных или **действия**. Некоторые соединители предоставляют только таблицы, некоторые — только действия, а некоторые — и то, и другое. Соединитель может быть стандартным или настраиваемым.

## <a name="tables"></a>Таблицы

Если ваш соединитель предоставляет таблицы, вы добавляете источник данных, а затем выбираете таблицу в источнике данных, которой вы хотите управлять. PowerApps извлекает данные таблицы в приложение и обновляет данные в источнике данных. Например, можно добавить источник данных, который содержит таблицу с именем **Lessons**, и задать для свойства **Items** элемента управления (например, коллекции или формы) следующее значение в строке формул:

 ![Свойство Items простого источника данных](./media/connections-list/ItemPropertyPlain.png)

Данные, извлекаемые приложением, можно указать, настроив свойство **Items** элемента управления, отображающего данные. Продолжая предыдущий пример, вы можете сортировать или фильтровать данные в таблице **Lessons** с помощью этого имени в качестве аргумента для функций **Search** и **SortByColumn**. На этом рисунке формула, по которой задано свойство **Items**, указывает, что данные сортируются и фильтруются в соответствии с текстом в поле **TextSearchBox1**. 

 ![Развернутое свойство Items источника данных](./media/connections-list/ItemPropertyExpanded.png)

Дополнительные сведения о настройке формулы с таблицами см. в следующих разделах:

  [Общие сведения об источниках данных в PowerApps](working-with-data-sources.md)<br> 
  [Создание приложения на основе данных Excel](get-started-create-from-data.md)<br> 
  [Создание приложения с нуля](get-started-create-from-blank.md)<br>
  [Understand tables and records in PowerApps](working-with-tables.md) (Общие сведения о таблицах и записях PowerApps)

  > [!NOTE]
  > Чтобы подключиться к данным в книге Excel, необходимо разместить книгу в службе облачного хранения, например OneDrive. Дополнительные сведения см. в статье о [подключении к облачным хранилищам из PowerApps](connections/cloud-storage-blob-connections.md).

## <a name="actions"></a>Действия

Если ваш соединитель предоставляет действия, вам также нужно выбрать источник данных. Но вместо выбора таблицы в качестве следующего шага, вам нужно вручную подключить элемент управления к действию путем изменения свойства **Items** элемента управления, который будет отображать данные. Формула, для которой вы задаете свойство **Items**, указывает действие, которое извлекает данные. Например, приложение не получит никакие данные, если вы подключитесь к Yammer, а затем укажете для свойства **Items** имя источника данных. Чтобы заполнить элемент управления данными, укажите действие, например **GetMessagesInGroup(5033622).messages**.

![Свойство Items для действия источника данных](./media/connections-list/ItemPropertyAction.png)

Если вам нужно обрабатывать пользовательские обновления данных для соединителей действия, создайте формулу с функцией **Patch**. В формуле определите действие и поля, которые требуется привязать к действию.  

Дополнительные сведения о настройке формулы для пользовательских обновлений см. в следующих разделах:

[Patch](functions/function-patch.md)<br>[Collect](functions/function-clear-collect-clearcollect.md)<br>[Update](functions/function-update-updateif.md)

> [!NOTE]
>  **PowerApps не работает с динамической схемой**. Динамическая схема фразы означает возможность того, что одно и то же действие может вернуть другую таблицу с разными столбцами. Условия, которые могут привести к различиям в столбцах в таблицах, включают входные параметры действия, пользователя или роль, которая исполняет действие, а также группу, в которой работает пользователь, и т. д. Например, SQL Server хранимые процедуры могут возвращать различные столбцы, если они выполняются с разными входными данными. Для действий с динамической схемой документация по соединителю показывает, **что выходные данные этой операции являются динамическими.** в качестве возвращаемого значения. В отличие от этого, Power автоматизиру работает с динамической схемой и может предоставить обработку для вашего сценария.

## <a name="popular-connectors"></a>Популярные соединители

В этой таблице содержатся ссылки на статьи с дополнительными сведениями о самых популярных соединителях. Полный список соединителей см. в разделе [Все соединители](https://docs.microsoft.com/connectors/).

| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- | --- | --- |
| ![Common Data Service](./media/connections-list/cdm.png) |[**Common Data Service**](../common-data-service/data-platform-intro.md) |&nbsp; |![Outlook в Office 365](./media/connections-list/office365.png) |[**Outlook в Office 365**](connections/connection-office365-outlook.md) |
| ![SharePoint](./media/connections-list/sharepoint.png) |[**SharePoint**](connections/connection-sharepoint-online.md) |&nbsp; |![Excel](./media/connections-list/excel.png) |[**Excel**](connections/connection-excel.md) |
| ![SQL Server](./media/connections-list/sql.png) |[**SQL Server**](connections/connection-azure-sqldatabase.md) |&nbsp; |![OneDrive для бизнеса](./media/connections-list/onedrive.png) |[**OneDrive для бизнеса**](connections/cloud-storage-blob-connections.md) |
| ![Dynamics 365.](./media/connections-list/dynamics-365.png) |[**Dynamics 365**](connections/connection-dynamics-crmonline.md) |&nbsp; |![OneDrive](./media/connections-list/onedrive.png) |[**OneDrive**](connections/cloud-storage-blob-connections.md) |
| ![Пользователи Office 365](./media/connections-list/office365.png) |[**Пользователи Office 365**](connections/connection-office365-users.md) |&nbsp; |![Dropbox](./media/connections-list/dropbox.png) |[**Dropbox**](connections/cloud-storage-blob-connections.md) |

## <a name="standard-and-custom-connectors"></a>Стандартные и пользовательские соединители
PowerApps предоставляет *стандартные* соединители для многих часто используемых источников данных, таких как перечисленные выше. Если в PowerApps есть стандартный соединитель для типа источника данных, который вы хотите использовать, следует использовать этот соединитель. Чтобы подключиться к другому типу источника данных, например созданной вами службе, см. инструкции по [регистрации и использованию настраиваемых соединителей](../canvas-apps/register-custom-api.md).

## <a name="all-standard-connectors"></a>Все стандартные соединители
Полный список стандартных соединителей см. в [справочнике по соединителям Майкрософт](https://docs.microsoft.com/connectors/). Для соединителей уровня "Премиум" требуется план 1 или 2 службы PowerApps. Дополнительные сведения см. на странице [планов PowerApps](https://powerapps.microsoft.com/pricing/).

Вы можете задавать вопросы по конкретному соединителю на [форумах PowerApps](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1), а также предложить новые соединители или другие улучшения на странице [Идей о PowerApps](https://powerusers.microsoft.com/t5/PowerApps-Ideas/idb-p/PowerAppsIdeas).
