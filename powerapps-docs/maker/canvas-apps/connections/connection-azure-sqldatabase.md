---
title: Общие сведения о подключении к SQL Server | Документация Майкрософт
description: Пошаговые инструкции по подключению к Azure SQL или локальной базе данных SQL Server
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 07/12/2016
ms.author: lanced
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: eed7a0bd6b9ee269877b6dfe4fcfd5bc6c56e3af
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678817"
---
# <a name="connect-to-sql-server-from-powerapps"></a>Подключение к SQL Server из PowerApps
![Значок SQL Server](./media/connection-azure-sqldatabase/sqlicon.png)

Подключайтесь к SQL Server в Azure или к локальной базе данных, чтобы отображать данные из базы данных в PowerApps.

## <a name="prerequisites"></a>Технические условия

* [Зарегистрируйтесь](../../signup-for-powerapps.md) в Power Apps, а затем выполните [Вход](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) , указав те же учетные данные, которые использовались для регистрации.
* Соберите следующие сведения о базе данных, которая содержит по крайней мере одну таблицу с первичным ключом:
  
  * имя базы данных;
  * имя сервера, на котором размещена база данных;
  * допустимые имя пользователя и пароль для подключения к базе данных;
  * тип проверки подлинности, необходимый для подключения к базе данных.
    
    Если у вас нет этих сведений, обратитесь к администратору базы данных, которую вы хотите использовать.
* Если вы подключаетесь к локальной базе данных, определите [шлюз данных](../gateway-management.md), к которому у вас есть доступ (или создайте новый).
  
    > [!NOTE]
  > Пользователь может создавать и использовать шлюзы и локальные подключения только в своей [среде по умолчанию](../working-with-environments.md).

## <a name="generate-an-app-automatically"></a>Автоматическое создание приложения
1. В Power Apps Studio щелкните **создать** в меню **файл** (вдоль левого края).
   
    ![Пункт "Создать" в меню "Файл"](./media/connection-azure-sqldatabase/file-new.png)
2. В разделе **Начать с данных** выберите стрелку вправо в конце строки соединителей.
3. Если у вас уже есть подключение к базе данных, которую вы хотите использовать, выберите его и перейдите к шагу 7 в этой процедуре.
4. Выберите последовательно **Новое подключение** и **SQL Server**.
   
    ![Добавление подключения к SQL Server](./media/connection-azure-sqldatabase/add-sql-connection.png)
5. Выполните одно из следующих действий.
   
   * Выберите параметр **Прямое подключение (облачные службы)** , затем укажите имя сервера, имя базы данных, имя пользователя и пароль для базы данных, которую вы хотите использовать.
     
       ![Подключение к базе данных в Azure](./media/connection-azure-sqldatabase/connect-azure.png)
   * Выберите параметр **Подключиться с помощью локального шлюза данных**, укажите имя сервера, имя базы данных, имя пользователя и пароль для базы данных, которую вы хотите использовать, а также тип проверки подлинности и шлюз.
     
       ![Подключение к локальной базе данных](./media/connection-azure-sqldatabase/connect-onprem.png)
     
       > [!NOTE]
     > Если у вас нет шлюза, [установите его](../gateway-reference.md), а затем выберите **Обновить список шлюзов**.
6. Нажмите кнопку **Подключиться**.
7. Выберите вариант в полях **Выбрать набор данных** и **Выбрать таблицу**, затем нажмите кнопку **Подключиться**.
   
    Power Apps создает приложение, которое показывает данные на трех экранах. Эвристика предлагает данные для отображения, но вы можете настроить пользовательский интерфейс по своему усмотрению.
8. Настройте приложение, используя методики, описанные в статье о [создании приложения из Excel](../get-started-create-from-data.md). Начните настройку с изменения макета приложения.

## <a name="build-an-app-from-scratch"></a>Создание приложения с нуля
1. Войдите на сайт [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) с помощью той же учетной записи, которая использовалась для регистрации PowerApps.
2. На панели навигации слева выберите меню **Подключения**.  
   
    ![Управление подключениями](./media/connection-azure-sqldatabase/manage-connections.png)
3. В правом верхнем углу выберите последовательно **Новое подключение** и **SQL Server**.
4. Выполните одно из следующих действий.
   
   * Выберите параметр **Прямое подключение (облачные службы)** , затем укажите имя сервера, имя базы данных, имя пользователя и пароль для базы данных, которую вы хотите использовать.
     
       ![Подключение к базе данных в Azure](./media/connection-azure-sqldatabase/connect-azure-portal.png)
   * Выберите параметр **Подключиться с помощью локального шлюза данных**, укажите имя сервера, имя базы данных, имя пользователя и пароль для базы данных, которую вы хотите использовать, а также тип проверки подлинности и шлюз.
     
       ![Подключение к базе данных в Azure](./media/connection-azure-sqldatabase/connect-onprem-portal.png)
     
       > [!NOTE]
     > Если у вас нет шлюза, [установите его](../gateway-reference.md), а затем щелкните значок обновления списка.
5. Нажмите кнопку **Создать**, чтобы создать подключение.
6. Создайте приложение, используя методики, описанные в статье о [создании приложения с нуля](../get-started-create-from-blank.md).

## <a name="update-an-existing-app"></a>Обновление существующего приложения
1. В Power Apps Studio откройте приложение, которое требуется обновить.
2. Откройте вкладку **Представление** и выберите пункт **Источники данных**.
3. На панели справа выберите команду **Добавить источник данных**.
   
    ![Добавление источника данных](./media/connection-azure-sqldatabase/add-data-source.png)
4. Выберите последовательно **Новое подключение**, **SQL Server**, затем нажмите кнопку **Подключиться**.
5. Выполните одно из следующих действий.
   
   * Выберите параметр **Прямое подключение (облачные службы)** , затем укажите имя сервера, имя базы данных, имя пользователя и пароль для базы данных, которую вы хотите использовать.
     
       ![Подключение к базе данных в Azure](./media/connection-azure-sqldatabase/connect-azure-fromblank.png)
   * Выберите параметр **Подключиться с помощью локального шлюза данных**, укажите имя сервера, имя базы данных, имя пользователя и пароль для базы данных, которую вы хотите использовать, а также тип проверки подлинности и шлюз.
     
       ![Подключение к базе данных в Azure](./media/connection-azure-sqldatabase/connect-onprem-fromblank.png)
     
       > [!NOTE]
     > Если у вас нет шлюза, [установите его](../gateway-reference.md), а затем щелкните значок обновления списка.
6. Нажмите кнопку **Подключиться**.
7. В поле **Выберите набор данных** выберите параметр.
8. В разделе **Выберите таблицу** установите один или несколько флажков, а затем нажмите кнопку **Подключиться**.

## <a name="next-steps"></a>Дальнейшие действия
* Узнайте, как [отобразить данные из источника данных](../add-gallery.md).
* Узнайте, как [создать, обновить записи и просмотреть сведения о них](../add-form.md).
* См. другие типы [источников данных](../connections-list.md), к которым можно подключаться.  
* Ознакомьтесь с [общими сведениями о таблицах и записях](../working-with-tables.md) с табличными источниками данных.

<!--NotAvailableYet
## View the available functions ##
This connection includes the following functions:

| Function Name |  Description |
| --- | --- |
|[GetItems](connection-azure-sqldatabase.md#getitems) | Retrieves rows from a SQL table |
|[PostItem](connection-azure-sqldatabase.md#postitem) | Inserts a new row into a SQL table |
|[GetItem](connection-azure-sqldatabase.md#getitem) | Retrieves a single row from a SQL table |
|[DeleteItem](connection-azure-sqldatabase.md#deleteitem) | Deletes a row from a SQL table |
|[PatchItem](connection-azure-sqldatabase.md#patchitem) | Updates an existing row in a SQL table |
|[GetTables](connection-azure-sqldatabase.md#gettables) | Retrieves tables from a SQL database |

### GetItems
Get rows: Retrieves rows from a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|$skip|integer|no|Number of entries to skip (default = 0)|
|$top|integer|no|Maximum number of entries to retrieve (default = 256)|
|$filter|string|no|An ODATA filter query to restrict the number of entries|
|$orderby|string|no|An ODATA orderBy query for specifying the order of entries|

### PostItem
Insert row: Inserts a new row into a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|item| |yes|Row to insert into the specified table in SQL|

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|value|array|No | |


### GetItem
Get row: Retrieves a single row from a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|id|string|yes|Unique identifier of the row to retrieve|

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|ItemInternalId|string|No | |


### DeleteItem
Delete row: Deletes a row from a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|id|string|yes|Unique identifier of the row to delete|

#### Output properties
None.

### PatchItem
Update row: Updates an existing row in a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|id|string|yes|Unique identifier of the row to update|
|item| |yes|Row with updated values|

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|ItemInternalId|string|No | &nbsp; |


### GetTables
Get tables: Retrieves tables from a SQL database

#### Input properties
None.

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|value|array|No | Can output the Name and DisplayName properties |

### ExecuteProcedure
Execute stored procedure: Executes a stored procedure in SQL

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|procedure|string|yes|Procedure name|
|parameters| |yes|Input parameters|

#### Output properties
Result of the stored procedure execution.

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|OutputParameters|object|No | Output parameter values |
|ReturnCode|integer|No | Return code of a procedure |
|ResultSets|object|No | Result sets|

-->
