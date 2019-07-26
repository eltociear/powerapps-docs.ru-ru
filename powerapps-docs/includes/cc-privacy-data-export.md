---
ms.openlocfilehash: e9b0446c2fb09cad33f5a3ae4bb69103f7d07d70
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2019
ms.locfileid: "67212645"
---
При использовании службы экспорта данных, когда вы активируете профиль экспорта данных из среды [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)], данные сущностей, добавленных в профиль, отправляются в [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Начальная синхронизация включает все данные, связанные с добавленными в профиль экспорта сущностями, но после этого синхронизация будет включать только новые изменения, которые постоянно отправляются в службу экспорта данных. Данные, отправляемые в службу экспорта данных, временно хранятся в [!INCLUDE[pn_azure_service_bus](pn_azure_service_bus.md)] и хранилище [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], обрабатываются в [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] и наконец синхронизируются (вставляются, обновляются или удаляются) в целевой базе данных, указанной в вашей подписке [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. После синхронизации данных они удаляются из [!INCLUDE[pn_azure_service_bus](pn_azure_service_bus.md)] и хранилища [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Если во время синхронизации данных возникает сбой, минимальный объем данных, соответствующих типу сущности, идентификатору записи и метке времени синхронизации, сохраняется в хранилище [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], чтобы можно было скачать список записей, которые не были обновлены.  
  
 Администратор может отключить профиль экспорта данных в любое время, чтобы остановить синхронизацию данных. Кроме того, администратор может удалить профиль экспорта для удаления всех журналов записей со сбоем; также он может удалить решение службы экспорта данных, чтобы прекратить использование службы экспорта данных.  
  
 Синхронизация данных между [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] и службой экспорта данных ведется непрерывно в безопасном режиме. Данные шифруются в ходе непрерывной пересылки между [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] и службой экспорта данных.  
  
 Компоненты и службы Azure, используемые со службой экспорта данных, подробно рассматриваются в следующих разделах.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc_privacy_note_azure_trust_center.md)]  
  
 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)  
  
 Предоставляет API и вычислительные ресурсы виртуальных машин [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] с целью обработки уведомлений о синхронизации записей, получаемых от [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)], и их последующей обработки для вставки, обновления или удаления данных записей в целевой базе данных. Микрослужбы, развертываемые на виртуальных машинах под управлением среды выполнения [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)], обрабатывают все вычисления, связанные с синхронизацией данных.  
  
 [Служебная шина Azure](https://azure.microsoft.com/services/service-bus/)  
  
 Обеспечивает канал сообщений, куда [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] вставляет сообщения с уведомлениями синхронизации, которые обрабатываются вычислительными узлами в [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)]. Каждое сообщение содержит сведения, например идентификатор организации и записи, для которых требуется синхронизация данных. Данные в служебной шине Azure не шифруются при хранении, но доступны только для службы экспорта данных.  
  
 [Хранилище BLOB-объектов Azure](https://azure.microsoft.com/services/storage/)  
  
 Данные временно хранятся в [!INCLUDE[pn_azure_blob_storage](pn_azure_blob_storage.md)] на случай, если данные уведомлений о синхронизации записей окажутся слишком велики для хранения в сообщении, или на случай временного сбоя при обработке уведомления синхронизации. Эти большие двоичные объекты шифруются с помощью новой функции пакета SDK хранилища [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], которая обеспечивает поддержку симметричного и асимметричного шифрования и интеграцию с [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)].  
  
 [SQL Azure](https://azure.microsoft.com/services/sql-database/)  
  
 [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] хранит конфигурацию профилей экспорта данных и метрики синхронизации данных.