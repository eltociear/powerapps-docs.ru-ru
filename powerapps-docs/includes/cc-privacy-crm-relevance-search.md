После включения функции поиска с сортировкой по релевантности данные в участвующих сущностях и атрибутах в экземпляре [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] будут синхронизироваться и сохраняться в индексе поиска [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 По умолчанию поиск с сортировкой по релевантности выключен. Системный администратор должен включить эту функцию в экземпляре [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)]. После включения поиска с сортировкой по релевантности администраторы и настройщики системы получают полный контроль над данными, которые будут синхронизироваться с индексом поиска [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 Настройщики системы могут использовать диалоговое окно **Настроить поиск по релевантности** в **средствах настройки**, чтобы включить определенные сущности для поиска, а затем настроить представления быстрого поиска для включенных сущностей, чтобы выбрать доступные для поиска атрибуты. Изменения данных постоянно синхронизируются между [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] и поиском [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] по безопасному соединению.  Данные конфигурации шифруются, и необходимые секретные ключи сохранятся в [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)].  
  
 Компоненты и службы Azure, задействованные в функциональности поиска с сортировкой по релевантности, подробно рассматриваются в следующих разделах.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc_privacy_note_azure_trust_center.md)]  
  
 [Службы поиска Azure](https://azure.microsoft.com/services/search/)  
  
 Поисковый индекс [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] используется для отображения высококачественных результатов поиска при малом времени отклика.  Поиск [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] предоставляет мощные и усовершенствованные возможности поиска следующего поколения для [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)].  Это выделенная служба поиска, не связанная с [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)], предоставляемая [!INCLUDE[pn_Windows_Azure](pn-windows-azure.md)]. Все новые индексы поиска [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] шифруются в неактивном состоянии.  Если вы присоединились до 24 января 2018 г., вам потребуется повторно индексировать данные, отказавшись от использования поиска с сортировкой по релевантности, подождав час и снова присоединившись к сервису.  
  
 [База данных SQL Azure](https://azure.microsoft.com/services/sql-database/)  
  
 Поиск с сортировкой по релевантности использует [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] для хранения указанных ниже данных.  
  
-   Данные конфигурации, связанные с организацией, и соответствующий индекс.  
  
-   Метаданные, связанные со службой поиска и индексами.  
  
-   Указатели на метаданные системы и данные при синхронизации изменений.  
  
-   Данные авторизации для обеспечения усиленной защиты на уровне строк.  
  
[Концентраторы событий Azure](https://azure.microsoft.com/services/event-hubs/)  
  
Компонент [!INCLUDE[pn_azure_event_hubs](pn-azure-event-hubs.md)] используется для обмена сообщениями между [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] и [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], а также для ведения рабочих элементов, обрабатываемых в процессе синхронизации. В каждом сообщении хранятся сведения, например код организации и имя сущности, используемые для синхронизации данных.  
  
[Azure Service Fabric Cluster](https://azure.microsoft.com/services/service-fabric/)  
  
Обработка и индексация данных производятся с помощью микрослужб, развернутых на виртуальных машинах под управлением среды выполнения Service Fabric. API-интерфейсы поиска и процесс синхронизации данных также размещены в кластере Service Fabric.  
  
При создании службы Service Fabric использовался многолетний опыт корпорации Майкрософт в области критически важных облачных служб, и эта служба проверялась в производственных условиях более пяти лет. Это главная технология, которая лежит в основе базовой инфраструктуры [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] и обеспечивает работу различных служб, включая [!INCLUDE[pn_skype_for_business](pn-skype-for-business.md)], [!INCLUDE[pn_intune](pn-intune.md)], [!INCLUDE[pn_azure_event_hubs](pn-azure-event-hubs.md)], фабрику данных [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] DocumentDB, [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] и [!INCLUDE[pn_cortana](pn-cortana.md)], которые можно масштабировать для обработки более 500 миллионов оценок в секунду.  
  
[Масштабируемые наборы виртуальных машин Azure](https://azure.microsoft.com/services/virtual-machine-scale-sets/)  
  
Гибкие масштабируемые наборы виртуальных машин [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] рассчитаны на поддержку гипермасштабируемых рабочих нагрузок. Кластер [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] работает на масштабируемых наборах виртуальных машин. Микрослужбы для обработки и индексации данных размещены на масштабируемых наборах и работают под управлением среды выполнения Service Fabric.  
  
[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)  
  
Для безопасного управления сертификатами, ключами и другими секретными данными, которые используются в процессе поиска, служит [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)].  
  
[Служба хранилища Azure (хранилище больших двоичных объектов)](https://azure.microsoft.com/services/storage/blobs/?b=16.38)  
  
Изменения данных клиентов хранятся в [!INCLUDE[pn_azure_blob_storage](pn_azure_blob_storage.md)] до двух дней.  Эти большие двоичные объекты шифруются с помощью новейшей функции в пакете SDK службы хранилища [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], обеспечивая поддержку симметричного и асимметричного шифрования и интеграцию с [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)]. С помощью [!INCLUDE[pn_crm_8_2_0_online_subsequent](pn-crm-8-2-0-online-subsequent.md)] документы в примечаниях и вложениях сообщений электронной почты и встреч также синхронизируются с хранилищем BLOB-объектов.  
  
[Служба Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
[!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] используется для проверки подлинности данных, которыми обмениваются [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] и службы [!INCLUDE[pn_Windows_Azure](pn-windows-azure.md)].  
  
[Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/)  
  
[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Load Balancer служит для распределения входящего трафика между работоспособными экземплярами службы в облачных службах или на виртуальных машинах, заданных в наборе с балансировкой нагрузки. В поиске с сортировкой по релевантности это средство используется для равномерного распределения нагрузки по конечным точкам в развертывании.  
  
[Виртуальные сети Azure](https://azure.microsoft.com/documentation/articles/virtual-networks-overview/)  
  
Виртуальные машины в кластере Service Fabric, работающие в одной или нескольких подсетях, соединяются между собой с помощью виртуальной сети [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Политики безопасности, параметры DNS, таблицы маршрутизации и IP-адреса полностью контролируются в рамках этой виртуальной сети. Для применения ролей безопасности в этой виртуальной сети используются группы безопасности сети. Эти правила разрешают или запрещают передачу сетевого трафика на виртуальные машины в виртуальной сети.