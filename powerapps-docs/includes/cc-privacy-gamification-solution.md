В результате установки и включения решения [!INCLUDE[pn_gamification](pn-gamification.md)] идентификаторы организации пользователя (например, имя, фамилия и адрес электронной почты) будут сохранены в [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для получения авторизации от службы [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)], размещенной в [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Это применяется ко всем пользователям, включенным в службе [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] администратором. Решение [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] отправляет данные ключевых показателей эффективности, настроенные администратором, в службу [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], и эти данные сохраняются в структурированном хранилище [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], а также в хранилище BLOB-объектов.  Аватар, пользовательские награды и логотип компании каждого пользователя хранятся в [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], но информация не возвращается в [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)].  
  
Обратите внимание, что администраторы и авторизованные пользователи могут использовать данные [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)], например вызовы, возможные сделки и зарезервированный доход, чтобы настраивать ключевые показатели эффективности для использования в играх. Служба [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] не инициирует вызовы [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] и реагирует только на данные, например игры, в которых используются ключевые показатели эффективности, которые возвращаются в [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)].  
  
Администратор также может разрешить сделать ТВ-поток [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] общедоступным. Руководители игр, которые настраивают ТВ-потоки [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] и включают общедоступную потоковую передачу, разрешат просмотр ТВ-потока всем пользователям в Интернете, имеющим ссылку на поток.  
  
Впоследствии администратор может отключить функцию [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)], удалив это решение из организации [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)].  
  
Компоненты и службы [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], используемые с [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)], подробно рассматриваются в следующих разделах.  
  
[!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
[Облачные службы](https://azure.microsoft.com/services/cloud-services/)  
  
 **Служба конструктора (веб-роль)**  
  
Эта веб-роль предоставляет несколько веб-служб для обмена данными между организацией [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] и компонентами [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], поддерживающими обслуживание нескольких развертываний одним экземпляром. Например, сведения о Gamification сохраняются в хранилище SQL [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  Расчеты игр используют очередь [!INCLUDE[pn_azure_service_bus](pn-azure-service-bus.md)] и возвращаются для хранения и отображения в службе.  Отправляемые пользователем и клиентом изображения сохраняются в [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)]. Подлинность всех запросов выполняется с помощью [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)].  
  
[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)  
  
Все службы хранят данные конфигурации в [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)].  
  
[База данных SQL Azure](https://azure.microsoft.com/services/sql-database/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] использует SQL [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для хранения:  
  
- Данные КПЭ  
  
- Расчеты игры  
  
- данных организаций (клиентов).  
  
[Хранилище BLOB-объектов Azure](https://azure.microsoft.com/services/storage/)  
  
Аватары, логотипы компании и другие отправляемые клиентом изображения сохраняются в [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)].  
  
[Сеть доставки содержимого (CDN) Azure](https://azure.microsoft.com/services/cdn/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] использует сеть доставки содержимого [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для предоставления статического содержимого в среду выполнения, например изображений (включая отправленные изображения, такие как логотипы клиентов), [!INCLUDE[pn_JavaScript](pn-javascript.md)] и CSS.  
  
[Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] использует [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] для проверки подлинности пользователей и определения их прав на использование платформы.