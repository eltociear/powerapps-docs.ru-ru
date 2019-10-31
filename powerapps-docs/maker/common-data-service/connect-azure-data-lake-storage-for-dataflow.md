---
title: Подключение Azure Data Lake Storage 2-го поколения для хранения потока данных (предварительная версия) | Документация Майкрософт
description: 'Узнайте, как подключить Azure Data Lake Storage 2-го поколения для хранения потока данных'
ms.custom: ''
ms.date: 09/05/2019
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
ms.assetid: null
caps.latest.revision: null
ms.author: matp
manager: kvivek
tags: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="connect-azure-data-lake-storage-gen2-for-dataflow-storage"></a>Подключение Azure Data Lake Storage 2-го поколения для хранения потока данных

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Вы можете настроить потоки данных для хранения данных в учетной записи Azure Data Lake Storage 2 поколения организации. В этой статье описываются общие шаги, необходимые для этого, а также указания и рекомендации. 

Есть несколько преимуществ для настройки потоков данных для хранения их определений и файлов данных в озере данных, включая следующие:
- Azure Data Lake Storage 2 поколения предоставляет масштабируемое хранилище данных.
- Разработчики вашего отдела ИТ могут использовать данные и файлы определений потоков данных для использования служб данных и искусственного интеллекта (AI) Azure, как показано в примерах GitHub из служб данных Azure.
- Это позволяет разработчикам в вашей организации интегрировать данные потоков данных во внутренние приложения и бизнес-решения, используя ресурсы разработчика для потоков данных и Azure.

## <a name="requirements"></a>Требования
Чтобы использовать Azure Data Lake Storage 2 поколения для потоков данных, требуется следующее:
- Среда PowerApps. Любой план PowerApps позволяет создавать потоки данных с Azure Data Lake Storage 2 поколения в качестве места назначения. Вы должны быть авторизованы в среде как разработчик. 
- Подписка Azure. Для использования Azure Data Lake Storage 2 поколения необходима подписка Azure.
- Группа ресурсов. Используйте уже имеющуюся группу ресурсов или создайте новую.
- Учетная запись службы хранилища Azure. Учетная запись хранения должна иметь функцию Data Lake Storage 2 поколения.

> [!TIP]
> Если у вас нет подписки Azure, [создайте бесплатная учетная запись](https://azure.microsoft.com/free/) прежде чем приступить к работе.

## <a name="prepare-your-azure-data-lake-storage-gen2-for-power-platform-dataflows"></a>Подготовка Azure Data Lake Storage 2 поколения для потоков данных Power Platform
Перед настройкой Power BI с учетной записью Azure Data Lake Storage 2 поколения, необходимо создать и настроить учетную запись хранения. Вот требования для потоков данных Power Platform:
1.  Учетная запись хранения необходимо создавать в том же клиенте Azure Active Directory, что и ваш клиент PowerApps.
2.  Рекомендуется создать учетную запись хранения в том же регионе, что и среда PowerApps, в которой вы планируете ее использовать. Чтобы определить расположение среды PowerApps, обратитесь к администратору среды.
3.  Учетная запись хранения должна иметь включенную функцию иерархического пространства имен.
4.  Вам должна быть предоставлена роль Владельца в учетной записи хранения.

В следующих разделах описаны шаги, необходимые для настройки учетной записи Azure Data Lake Storage 2 поколения.

## <a name="create-the-storage-account"></a>Создание учетной записи хранения
Выполните шаги, описанные в разделе [Создание учетная запись хранения Azure Data Lake Storage 2 поколения](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account).
1.  Убедитесь, что вы выбрали то же местоположение, что и у своего клиента Power BI, и задали хранилище как StorageV2 (общего назначения v2).
2.  Убедитесь, что вы включили функцию иерархического пространства имен. 
3.  Рекомендуется установить для параметра репликации значение геоизбыточного хранилища с доступом для чтения (RA-GRS).



<!--from editor: I haven't heard of Athena before. Is it the Amazon service, https://aws.amazon.com/athena/? If so, it probably should be identified as Amazon at first mention. -->


## <a name="create-a-cross-origin-resource-sharing-cors-rule-for-the-athena-service"></a>Создание правила общего доступа к ресурсам независимо от источника (CORS) к службе Athena

> [!NOTE]
> Потоки данных Power Platform используют службу Athena для подключения озера данных к среде PowerApps. В этом разделе вы должны предоставить службе Athena роль учетной записи хранения, чтобы ее можно было настроить для использования потока данных.

Далее, необходимо включить службу Athena для доступа к учетной записи хранения через веб-браузер и портал PowerApps. В веб-браузерах реализовано ограничение безопасности, известное как [политика одного источника](http://www.w3.org/Security/wiki/Same_Origin_Policy), которое не позволяет веб-странице вызывать API в другом домене; CORS предоставляет безопасный способ разрешить одному домену (исходному домену) вызывать API в другом домене. Дополнительные сведения о CORS см. в разделе [спецификация CORS](http://www.w3.org/TR/cors/).

Следуйте инструкциям в учетной записи хранения, которую вы только что создали, на странице настроек на портале Azure. В пункте меню CORS выберите раздел службы Blob и введите эти сведения. 

|Параметр  |Value  |
|---------|---------|
|Разрешенные источники   | https://athena-ui-prod.trafficmanager.net     |
|Разрешенные методы   |  DELETE, GET, HEAD, MERGE, POST, OPTIONS, PUT, PATCH   |
|Разрешенные заголовки   | *    |
|Предоставляемые заголовки   | *    |
|Максимальный возраст |   *  |


На следующем рисунке показано правило CORS, настроенное для службы Athena.

![Правило CORS](media/dataflows-cores-rule.png)

## <a name="connect-your-azure-data-lake-storage-gen2-to-powerapps"></a>Подключите Azure Data Lake Storage 2 поколения к PowerApps
После настройки учетной записи Azure Data Lake Storage 2 поколения портале Azure, вы готовы подключить ее к определенному потоку данных или среде PowerApps. Подключение озера данных к среде позволяет другим разработчикам и администраторам в среде создавать потоки данных, которые также хранят свои данные в озере данных организации. 

Чтобы подключить учетную запись Azure Data Lake Storage 2 поколения к потоку данных, выполните следующие действия:
1.  Выполните вход в [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), и проверьте, в какой среде вы находитесь. Переключатель среды находится на правой стороне заголовка. 
2. В левой области навигации выберите стрелку вниз рядом с **Данными**.

   ![Вкладка д"Данные" портала разработчика PowerApps](media/powerapps-portal-data.png)

3. В появившемся списке выберите **Потоки данных** а затем в командной строке выберите **Новый поток данных**.

   ![Создать новый поток данных](media/new-dataflow.png) 

4. Выберите требуемые аналитические сущности. Эти сущности отображают какие данные нужно хранить в учетной записи Azure Data Lake Store 2 поколения организации. 

   ![Выберите аналитические сущности](media/select-analytical-entities.png)

## <a name="select-the-storage-account-to-use-for-dataflow-storage"></a>Выберите учетная запись хранения для использования для хранения потока данных
Если учетная запись хранилища еще не была связана со средой, появится диалоговое окно **Связать с озером данных**. Вам потребуется выполнить вход и найти озеро данных, которое вы создали в предыдущих шагах. В этом примере ни одно озеро данных не связано со средой, поэтому возникает запрос на его добавление. 



<!--from editor: Should "storage account" be in bold because it's something the user has to select? --"

1. Select storage account.

    The **Select Storage Account** screen appears.
    
    ![Select storage account](media/select-storage-account.png)
    
2. Select the **Subscription ID** of the storage account.
3. Select the **Resource group name** in which the storage account was created.
4. Enter the **Storage account name**.
5. Select **Save**.

Once these steps are successfully completed, your Azure Data Lake Storage Gen2 account is connected to Power Platform Dataflows and you can continue to create a dataflow.

## Considerations and limitations
There are a few considerations and limitations to keep in mind when working with your dataflow storage:
- Linking an Azure Data Lake Store Gen2 account for dataflow storage is not supported in the default environment.
- Once a dataflow storage location is configured for a dataflow, it can't be changed.
- By default, any member of the environment can access dataflow data using the Power Platform Dataflows Connector. However, only the owners of a dataflow can access its files directly in Azure Data Lake Storage Gen2. To authorize additional people to access the dataflows data directly in the lake, you must authorize them to the dataflow’s CDM folder in the data lake or the data lake itself.
- When a dataflow is deleted, its CDM folder in the lake will also be deleted. 

> [!IMPORTANT]
> You shouldn't change files created by dataflows in your organization’s lake or add files to a dataflow’s CDM folder. Changing files might damage dataflows or alter their behavior and is not supported. Power Platform Dataflows only grants read access to files it creates in the lake. If you authorize other people or services to the filesystem used by Power Platform Dataflows, only grant them read access to files or folders in that filesystem.

## Frequently asked questions
*What if I had previously created dataflows in my organization’s Azure Data Lake Storage Gen2 and would like to change their storage location?*

   You can't change the storage location of a dataflow after it was created.

*When can I change the dataflow storage location of an environment?*

   Changing the environment's dataflow storage location is not currently supported. 

## Next steps
This article provided guidance about how to connect an Azure Data Lake Storage Gen2 account for dataflow storage. 

For more information about dataflows, the Common Data Model, and Azure Data Lake Storage Gen2, see these articles:
- [Self-service data prep with dataflows](https://go.microsoft.com/fwlink/?linkid=2099972)
- [Creating and using dataflows in PowerApps](https://go.microsoft.com/fwlink/?linkid=2100076)
- [Connect Azure Data Lake Storage Gen2 for dataflow storage](https://go.microsoft.com/fwlink/?linkid=2099973)
- [Add data to an entity in Common Data Service](https://go.microsoft.com/fwlink/?linkid=2100075)

For more information about Azure storage, see this article:
- [Azure Storage security guide](https://docs.microsoft.com/azure/storage/common/storage-security-guide)

For more information about the Common Data Model, see these articles:
- [Common Data Model - overview](https://docs.microsoft.com/powerapps/common-data-model/overview) 
- [Common Data Model folders](https://go.microsoft.com/fwlink/?linkid=2045304)
- [CDM model file definition](https://go.microsoft.com/fwlink/?linkid=2045521)

You can ask questions in the [PowerApps Community](https://go.microsoft.com/fwlink/?linkid=2099971).
