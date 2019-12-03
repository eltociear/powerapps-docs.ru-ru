---
title: Общие сведения о соединителях для приложений на основе холста | Документы Майкрософт
description: Обзор всех доступных подключений, которые можно использовать для создания приложений на основе холста
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/19/2019
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9449c9ab8e03159ffdc4e5657d7eb8ca92cbf0f0
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74724044"
---
# <a name="overview-of-canvas-app-connectors-for-power-apps"></a>Общие сведения о соединителях Canvas-App для Power Apps
Данные являются основой большинства приложений, включая те, которые вы создаете в Power Apps. Эти данные хранятся в *источниках данных*. Вы переносите их в приложение при создании *подключения*. Для подключения используется определенный *соединитель*, который обеспечивает обмен данными с источником данных. В Power Apps есть соединители для многих популярных служб и локальных источников данных, включая SharePoint, SQL Server, Office 365, Salesforce и Twitter. Чтобы приступить к добавлению данных в приложение Canvas, см. статью [Добавление подключения к данным в Power Apps](add-data-connection.md).

Соединитель может предоставлять **таблицы** данных или **действия**. Некоторые соединители предоставляют только таблицы, некоторые — только действия, а некоторые — и то, и другое. Соединитель может быть стандартным или настраиваемым.

## <a name="tables"></a>Таблицы

Если ваш соединитель предоставляет таблицы, вы добавляете источник данных, а затем выбираете таблицу в источнике данных, которой вы хотите управлять. Power Apps извлекает данные таблицы в приложение и обновляет данные в источнике данных. Например, можно добавить источник данных, который содержит таблицу с именем **Lessons**, и задать для свойства **Items** элемента управления (например, коллекции или формы) следующее значение в строке формул:

 ![Свойство Items простого источника данных](./media/connections-list/ItemPropertyPlain.png)

Данные, извлекаемые приложением, можно указать, настроив свойство **Items** элемента управления, отображающего данные. Продолжая предыдущий пример, вы можете сортировать или фильтровать данные в таблице **Lessons** с помощью этого имени в качестве аргумента для функций **Search** и **SortByColumn**. На этом рисунке формула, по которой задано свойство **Items**, указывает, что данные сортируются и фильтруются в соответствии с текстом в поле **TextSearchBox1**. 

 ![Развернутое свойство Items источника данных](./media/connections-list/ItemPropertyExpanded.png)

Дополнительные сведения о настройке формулы с таблицами см. в следующих разделах:

  [Общие сведения об источниках данных в Power Apps](working-with-data-sources.md)<br> 
  [Создание приложения на основе данных Excel](get-started-create-from-data.md)<br> 
  [Создание приложения с нуля](get-started-create-from-blank.md)<br>
  [Общие сведения о таблицах и записях в Power Apps](working-with-tables.md)

  > [!NOTE]
  > Чтобы подключиться к данным в книге Excel, необходимо разместить книгу в службе облачного хранения, например OneDrive. Дополнительные сведения см. [в статье подключение к хранилищу в облаке из Power Apps](connections/cloud-storage-blob-connections.md).

## <a name="actions"></a>Действия

Если ваш соединитель предоставляет действия, вам также нужно выбрать источник данных. Но вместо выбора таблицы в качестве следующего шага, вам нужно вручную подключить элемент управления к действию путем изменения свойства **Items** элемента управления, который будет отображать данные. Формула, для которой вы задаете свойство **Items**, указывает действие, которое извлекает данные. Например, приложение не получит никакие данные, если вы подключитесь к Yammer, а затем укажете для свойства **Items** имя источника данных. Чтобы заполнить элемент управления данными, укажите действие, например **GetMessagesInGroup(5033622).messages**.

![Свойство Items для действия источника данных](./media/connections-list/ItemPropertyAction.png)

Если вам нужно обрабатывать пользовательские обновления данных для соединителей действия, создайте формулу с функцией **Patch**. В формуле определите действие и поля, которые требуется привязать к действию.  

Дополнительные сведения о настройке формулы для пользовательских обновлений см. в следующих разделах:

[Patch](functions/function-patch.md)<br>[Collect](functions/function-clear-collect-clearcollect.md)<br>[Update](functions/function-update-updateif.md)

> [!NOTE]
>  **Power Apps не работает с динамической схемой**. Динамическая схема фразы означает возможность того, что одно и то же действие может вернуть другую таблицу с разными столбцами. Условия, которые могут привести к различиям в столбцах в таблицах, включают входные параметры действия, пользователя или роль, которая исполняет действие, а также группу, в которой работает пользователь, и т. д. Например, SQL Server хранимые процедуры могут возвращать различные столбцы, если они выполняются с разными входными данными. Для действий с динамической схемой документация по соединителю показывает, **что выходные данные этой операции являются динамическими.** в качестве возвращаемого значения. В отличие от этого, Power автоматизиру работает с динамической схемой и может предоставить обработку для вашего сценария.

## <a name="popular-connectors"></a>Популярные соединители

В этой таблице содержатся ссылки на статьи с дополнительными сведениями о самых популярных соединителях. Полный список соединителей см. в разделе [Все соединители](https://docs.microsoft.com/connectors/).

| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- | --- | --- |
| ![Common Data Service](./media/connections-list/cdm.png) |[**Common Data Service**](connections/connection-common-data-service.md) |&nbsp; |![Облачное хранилище](./media/connections-list/onedrive.png) | ** [**облачного хранилища**](connections/cloud-storage-blob-connections.md) |
| ![Dynamics 365.](./media/connections-list/dynamics-365.png) |[**Dynamics 365**](connections/connection-dynamics-crmonline.md) |&nbsp; | ![Dynamics AX](./media/connections-list/dynamics-ax.png) |[**Dynamics AX**](connections/connection-dynamicsax.md) |
|![Excel](./media/connections-list/excel.png) |[**Excel**](connections/connection-excel.md) |&nbsp; |![Microsoft Translator](./media/connections-list/microsoft-translator.png) |[**Microsoft Translator**](connections/connection-microsoft-translator.md) |
|![Outlook в Office 365](./media/connections-list/office365.png) |[**Outlook в Office 365**](connections/connection-office365-outlook.md) |&nbsp; | ![Пользователи Office 365](./media/connections-list/office365.png) |[**Пользователи Office 365**](connections/connection-office365-users.md) |
| ![Oracle](./media/connections-list/oracle-icon.png) |[**СУБД**](connections/connection-oracledb.md) |&nbsp; | ![Power BI](./media/connections-list/powerbi.png) |[**Power BI**](connections/connection-powerbi.md) |
| ![SharePoint](./media/connections-list/sharepoint.png) |[**SharePoint**](connections/connection-sharepoint-online.md) |&nbsp; | ![SQL Server](./media/connections-list/sql.png) |[**SQL Server**](connections/connection-azure-sqldatabase.md) 
|![Twitter](./media/connections-list/twitter.png) |[**Twitter**](connections/connection-twitter.md)

\* * Применяется к большому двоичному объекту Azure, Box, Dropbox, Google Drive, OneDrive и OneDrive для бизнеса

## <a name="standard-and-custom-connectors"></a>Стандартные и пользовательские соединители
Power Apps предоставляет *стандартные* соединители для многих широко используемых источников данных, например перечисленных выше. Если Power Apps имеет стандартный соединитель для типа источника данных, который вы хотите использовать, следует использовать этот соединитель. Чтобы подключиться к другому типу источника данных, например созданной вами службе, см. инструкции по [регистрации и использованию настраиваемых соединителей](../canvas-apps/register-custom-api.md).

## <a name="all-standard-connectors"></a>Все стандартные соединители
Полный список стандартных соединителей см. в [справочнике по соединителям Майкрософт](https://docs.microsoft.com/connectors/). Для соединителей уровня "Премиум" требуется Power Apps план 1 или план 2. Дополнительные сведения см. в статье [планы Power Apps](https://powerapps.microsoft.com/pricing/).

Вы можете задавать вопросы о конкретном соединителе на [форумах Power Apps](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1). Вы можете предложить соединители, чтобы добавить или другие улучшения в [идеи Power Apps](https://powerusers.microsoft.com/t5/PowerApps-Ideas/idb-p/PowerAppsIdeas).
