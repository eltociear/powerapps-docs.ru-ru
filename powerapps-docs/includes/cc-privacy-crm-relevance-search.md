---
ms.openlocfilehash: dff813dcdf6d025ba47e29699e2047f79cf85600
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2019
ms.locfileid: "67225491"
---
Если включить поиск по релевантности, данные в участвующих сущностях и атрибутах в вашем экземпляре [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] будут синхронизироваться и храниться в индексе поиска [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 Поиск по релевантности по умолчанию отключен. Системный администратор должен включить эту функцию в экземпляре [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)]. После включения поиска по релевантности системные администраторы и создатели настроек получают полный контроль над данными, которые будут синхронизироваться с индексом поиска [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 Создатели настроек системы могут использовать диалоговое окно **Настройка поиска по релевантности** в разделе **средств настройки**, чтобы включить поиск для определенных сущностей и затем настроить представления быстрого поиска для включенных сущностей, чтобы можно было выбрать атрибуты для поиска. Изменения данных постоянно синхронизируются между [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] и поиском [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] через безопасное подключение.  Используется шифрование данных конфигурации; необходимые секреты хранятся в [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)].  
  
 Компоненты и службы Azure, используемые с функцией поиска по релевантности, подробно рассматриваются в следующих разделах.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc_privacy_note_azure_trust_center.md)]  
  
 [Службы поиска Azure](https://azure.microsoft.com/services/search/)  
  
 Индекс поиска [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] используется для предоставления результатов поиска высокого качества с быстрым откликом.  Поиск [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] добавляет мощные и сложные возможности поиска следующего поколения для [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)].  Это выделенная служба поиска, внешняя по отношению к службе [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)], предоставляемой [!INCLUDE[pn_Windows_Azure](pn-windows-azure.md)]. Все новые индексы поиска [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] шифруются при хранении.  Если вы зарегистрировались до 24 января 2018 г., необходима повторная индексация данных; для этого отмените регистрацию в поиске по релевантности, подождите час и зарегистрируйтесь снова.  
  
 [База данных SQL Azure](https://azure.microsoft.com/services/sql-database/)  
  
 Поиск по релевантности использует [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] для хранения:  
  
-   данных конфигурации, относящихся к организации, и соответствующего индекса;  
  
-   метаданных, относящихся к службе поиска и индексам;  
  
-   указателей на системные метаданные и данных при синхронизации изменений;  
  
-   данных авторизации, позволяющих включить повышенную безопасность на уровне строк.  
  
[Центры событий Azure](https://azure.microsoft.com/services/event-hubs/)  
  
Компонент [!INCLUDE[pn_azure_event_hubs](pn-azure-event-hubs.md)] используется для обмена сообщениями между [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] и [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], а также для поддержки рабочих элементов, управление которыми осуществляется в процессе синхронизации. Каждое сообщение хранит сведения, например идентификатор и сущности названия организации, которые используются для синхронизации данных.  
  
[Кластер Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)  
  
Обработка и индексирование данных ведутся в микрослужбах, развернутых на виртуальных машинах, управляемых с помощью среды выполнения Service Fabric. API-интерфейсы поиска и процесс синхронизации данных также размещены в кластере Service Fabric.  
  
Service Fabric были выпущены в течение нескольких лет в корпорации Майкрософт, предоставляя критически важные облачные службы, и теперь она становится рабочей. Это основополагающая технология, на которой работает базовая инфраструктура [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], а также такие службы, как [!INCLUDE[pn_skype_for_business](pn-skype-for-business.md)], [!INCLUDE[pn_intune](pn-intune.md)], [!INCLUDE[pn_azure_event_hubs](pn-azure-event-hubs.md)], [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Data Factory, [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] DocumentDB, [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] и [!INCLUDE[pn_cortana](pn-cortana.md)], которые могут масштабировать и обрабатывать более 500 млн вычислений в секунду.  
  
[Масштабируемые наборы виртуальных машин Azure](https://azure.microsoft.com/services/virtual-machine-scale-sets/)  
  
Масштабируемые наборы виртуальных машин [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] эластичны и обеспечивают поддержку горизонтального гипермасштабирования рабочих нагрузок. Кластер [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] работает в масштабируемых наборах виртуальных машин. Микрослужбы для обработки данных и индексирования данных размещаются в масштабируемых наборах и управляются средой выполнения Service Fabric.  
  
[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)  
  
[!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] используется для безопасного управления сертификатами, ключами и другими секретными данными, используемыми в процессе поиска.  
  
[Служба хранилища Azure (хранилище BLOB-объектов)](https://azure.microsoft.com/services/storage/blobs/?b=16.38)  
  
Изменения в данных клиента хранятся в [!INCLUDE[pn_azure_blob_storage](pn_azure_blob_storage.md)] в течение двух дней.  Эти большие двоичные объекты шифруются с помощью новой функции пакета SDK хранилища [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], которая обеспечивает поддержку симметричного и асимметричного шифрования и интеграцию с [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)]. При использовании [!INCLUDE[pn_crm_8_2_0_online_subsequent](pn-crm-8-2-0-online-subsequent.md)] документы в заметках и вложениях в сообщениях электронной почты и встречах также синхронизируются в хранилище BLOB-объектов.  
  
[Служба Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
[!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] используется для проверки подлинности между службами [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] и [!INCLUDE[pn_Windows_Azure](pn-windows-azure.md)].  
  
[Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/)  
  
[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Load Balancer распределяет входящий трафик между работоспособными экземплярами службы в облачных службах или виртуальных машинах, определенных в наборе с балансировкой нагрузки. Поиск по релевантности использует его для балансировки нагрузки конечных точек в развертывании.  
  
[Виртуальные сети Azure](https://azure.microsoft.com/documentation/articles/virtual-networks-overview/)  
  
Виртуальные машины в кластере Service Fabric, работающие в одной подсети или нескольких, соединены виртуальной сетью [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Политики безопасности, параметры DNS, таблицы маршрутов и IP-адресов полностью управляются этой виртуальной сетью. Чтобы применить правила безопасности для этой виртуальной сети, используются группы безопасности сети. Эти правила разрешают или запрещают передачу сетевого трафика к виртуальным машинам в виртуальной сети.