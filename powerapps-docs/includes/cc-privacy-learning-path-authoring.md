---
ms.openlocfilehash: 509ad3f5b1b94378b2c6fd7661510b7aef0e3a23
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61582963"
---
Если вы включили разработку схемы обучения для организации [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], содержимое схемы обучения (опубликованное или черновое), создаваемое пользователями (с надлежащими привилегиями безопасности), будет храниться в [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)]. Кроме того, включение функции позволяет [!INCLUDE[pn_azure_cloud_services](pn-azure-cloud-services.md)] записывать следующие данные, связанные с организацией [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]:  
  
-   Список организаций в клиенте  
  
-   Клиент [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] и применимый браузер конечных пользователей; конфигурация ОС  
  
-   Данные об использовании от конечных пользователей — например, время, затраченное на учебные материалы, или записанные щелчки  
  
-   Агрегированные данные от конечных пользователей — расположение, роль безопасности, язык пользователя  
  
-   Агрегированные данные от конечных пользователей — расположение, роль безопасности, язык пользователя  
  
-   Подробные отзывы от конечных пользователей  
  
 Администратор может включить (и впоследствии отключить) разработку схемы обучения при помощи параметра на вкладке **Общие** в диалоговом окне **Параметры системы**.  
  
 Компоненты и службы [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], используемые при разработке схемы обучения, подробно рассматриваются в следующих разделах.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Облачные службы](https://azure.microsoft.com/en-us/services/cloud-services/)  
  
 **Веб-служба**  
  
 Веб-служба предоставляет элементы управления, которые подготавливаются к просмотру на клиенте средой выполнения схем обучения. Веб-служба также поддерживает API конструктора, который используется для разработки схемы обучения. Элементы управления хранятся службой на [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)].  
  
 **Компилятор (рабочая роль)**  
  
 Роль компилятора управляет публикацией элементов управления в группе публикации. Компилятор использует очереди для хранения сообщений о задании публикации. Результаты сохраняются в [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)].  
  
 [База данных SQL Azure](https://azure.microsoft.com/en-us/services/sql-database/)  
  
 Схема обучения использует [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] для хранения:  
  
-   элементов управления, которые создаются с помощью схемы обучения;  
  
-   относящихся к конфигурации аспектов разработки схемы обучения.  
  
 [Azure Active Directory](https://azure.microsoft.com/en-us/services/active-directory/)  
  
 Схема обучения использует [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] для проверки подлинности веб-службы.  
  
 [Диспетчер трафика Azure](https://azure.microsoft.com/en-us/services/traffic-manager/)  
  
 Схема обучения использует диспетчер трафика [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для балансировки нагрузки на веб-службу по доступности и производительности.  
  
 [Очередь хранилища Azure](https://azure.microsoft.com/en-us/services/storage/)  
  
 Очередь хранилища [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] используется для координации обмена данными между ролями веб-службы и компилятора.  
  
 [Хранилище BLOB-объектов Azure](https://azure.microsoft.com/en-us/services/storage/)  
  
 Схема обучения использует [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)] для хранения статического содержимого (клиентских [!INCLUDE[pn_JavaScript](pn-javascript.md)], изображений, содержимого CSS).  
  
 [Сеть доставки содержимого Azure (CDN)](https://azure.microsoft.com/en-us/services/cdn/)  
  
 CDN используется для кэширования статического содержимого на стороне клиента ([!INCLUDE[pn_JavaScript](pn-javascript.md)], изображений и CSS-файлов), а также для их передачи из глобальной сети CDN.