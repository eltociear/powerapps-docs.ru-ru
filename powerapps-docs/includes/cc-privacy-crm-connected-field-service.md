---
ms.openlocfilehash: ce9db35844f46e9779055ec30dcba0f9459c3a16
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61583494"
---
При установке [!INCLUDE[pn_connected_field_service_msdyn365](pn-connected-field-service-msdyn365.md)], когда вы предоставляете сведения о своей подписке [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], будут развернуты необходимые ресурсы [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] (перечислены ниже), а экземпляр [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] отправит данные (команды и регистрации) в [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], чтобы включить сценарии с поддержкой IoT, которые регистрируют устройства, а затем отправляют команды на такие зарегистрированные устройства и получают команды от них. Администратор может удалить службу Connected Field Service, чтобы удалить соответствующую функциональность, а затем перейти на портал [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для совершения действий со всеми связанными службами [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], которые больше не нужны.  
  
 Компоненты и службы [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], используемые при разработке функциональности Connected Field Service, подробно описываются в следующих разделах.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Очередь служебной шины](https://azure.microsoft.com/documentation/articles/service-bus-dotnet-get-started-with-queues/)  
  
 Позволяет ставить в очередь входящие и исходящие сообщения (команды), которыми обмениваются [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] и [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Если [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] отправляется оповещение IoT или в центр Интернета вещей из [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] отправляется команда, она будет помещена в эту очередь.  
  
 [Logic Apps](https://azure.microsoft.com/services/logic-apps/)  
  
 Предоставляет службу оркестрации, которая использует соединитель [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] и соединитель очереди. Соединители [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] используются для создания сущностей, характерных для [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], а соединители очереди используются для опроса очереди.  
  
 [Stream Analytics](https://azure.microsoft.com/services/stream-analytics/)  
  
 Предоставляет полностью управляемый механизм обработки событий в реальном времени, который помогает извлекать из данных ценные аналитические сведения. Stream Analytics позволяет легко настраивать аналитические вычисления в режиме реального времени для потоков данных, поступающих с устройств, датчиков, веб-сайтов, из социальных сетей, приложений, инфраструктурных систем и т. д. Эта служба выполняет роль воронки для отправки избранных оповещений IoT в [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)].  
  
 [Центр Интернета вещей](https://azure.microsoft.com/services/iot-hub/)  
  
 Connected Field Services использует Центр Интернета вещей для управления состоянием зарегистрированных устройств и ресурсов. Кроме того, Центр Интернета вещей отправляет команды и уведомления на подключенные устройства, а также отслеживает доставку приложений с подтверждением получения. Сообщения между устройствами пересылаются надежным способом, подходящим для устройств, которые не всегда подключены.  
  
 **Simulator**  
  
 Это тестовое веб-приложение для имитации устройства, которое отправляет команды в Центр Интернета вещей или получает их оттуда.  
  
 [База данных SQL Azure](https://azure.microsoft.com/services/sql-database/)  
  
 Connected Field Service использует SQL [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для хранения пакетов пульса устройства для дальнейшего использования в PowerBI с целью отображения статуса устройства в [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)].  
  
 [Хранилище BLOB-объектов Azure](https://azure.microsoft.com/services/storage/)  
  
 Запросы, которые использует Stream Analytics, хранятся в хранилище BLOB-объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].