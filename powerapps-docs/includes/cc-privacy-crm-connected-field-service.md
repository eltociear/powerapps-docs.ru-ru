После установки [!INCLUDE[pn_connected_field_service_msdyn365](pn-connected-field-service-msdyn365.md)] при указании сведений о подписке [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] будут развернуты обязательные ресурсы [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] (перечисленные ниже), а ваш экземпляр [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] будет передавать данные (например команды и сведения о регистрации) в [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], чтобы сделать возможной реализацию сценариев IoT, включающих регистрацию устройств и последующую передачу им команд. Администратор может удалить Connected Field Service, чтобы удалить соответствующую функцию, а затем перейти к порталу [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для управления всеми связанными службами [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], которые больше не требуются.  
  
 Компоненты и службы [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], необходимые для реализации функций Connected Field Service, подробно рассматриваются в следующих разделах.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Очередь шины обслуживания](https://azure.microsoft.com/documentation/articles/service-bus-dotnet-get-started-with-queues/)  
  
 Обеспечивает очередь для входящих и исходящих сообщений (команд), передаваемых между [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] и [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. При отправке в [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] оповещения IoT или при отправке команды из [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] в центр IoT эти команды и оповещения помещаются в эту очередь.  
  
 [Логические приложения](https://azure.microsoft.com/services/logic-apps/)  
  
 Обеспечивают службу согласования, которая использует соединитель [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] и соединитель очереди. Соединители [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] служат для создания сущностей, которые относятся к [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], а соединители очереди служат для опроса очереди.  
  
 [Stream Analytics](https://azure.microsoft.com/services/stream-analytics/)  
  
 Обеспечивает полностью управляемый механизм обработки событий в реальном времени, который помогает получать наиболее неочевидные выводы на основе данных. Stream Analytics упрощает настройку аналитических расчетов в реальном времени. Эти расчеты выполняются над данными, получаемыми от устройств, датчиков, с веб-сайтов, из социальных сетей, приложений, инфраструктурных систем и т. д. Эта функция выполняет роль воронки, передающей выборочные оповещения IoT в [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)].  
  
 [Центр IoT](https://azure.microsoft.com/services/iot-hub/)  
  
 Службы Connected Field Services используют центр IoT для управления состоянием зарегистрированных устройств и активов. Кроме того, центр IoT отправляет команды и уведомления подключенным устройствам и отслеживает доставку сообщений, получая подтверждения. Отправляемые сообщения имеют длительный срок действия, чтобы недостаточно надежно подключенные устройства также их получали.  
  
 **Симулятор**  
  
 Это тестовое веб-приложение, эмулирующее устройство, которое отправляет команды или принимает команды от центра IoT.  
  
 [База данных SQL Azure](https://azure.microsoft.com/services/sql-database/)  
  
 Служба Connected Field Service использует SQL [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для хранения сообщений тактовых импульсов для дальнейшего использования в PowerBI с целью отображения состояния устройств в [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)].  
  
 [Хранилище BLOB-объектов Azure](https://azure.microsoft.com/services/storage/)  
  
 Запросы, которые будут использоваться в Stream Analytics, сохраняются в хранилище больших двоичных объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].