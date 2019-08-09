После включения​​ разработки схемы обучения для организации [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] создаваемое пользователями (с соответствующими привилегиями безопасности) содержимое схемы обучения (как опубликованное, так и черновики) будет сохраняться в [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)]. Кроме того, включение этой функции позволяет [!INCLUDE[pn_azure_cloud_services](pn-azure-cloud-services.md)] собирать следующие данные, связанные с организацией [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]:  
  
-   Список организаций для клиента  
  
-   Конфигурация клиента [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] и подходящих браузера и ОС конечных пользователей  
  
-   Данные об использовании для конечных пользователей, например время, проведенное в схеме обучения, или записанное количество щелчков  
  
-   Агрегированные данные конечных пользователей — расположение, роль безопасности, язык пользователя  
  
-   Агрегированные данные конечных пользователей — расположение, роль безопасности, язык пользователя  
  
-   Подробные отзывы конечных пользователей  
  
 Администратор может включить (а впоследствии и отключить) разработку схемы обучения с помощью параметра на вкладке **Общие** диалогового окна **Системные параметры**.  
  
 Компоненты и службы [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], используемые с функцией разработки схемы обучения, подробно рассматриваются в следующих разделах.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Облачные службы](https://azure.microsoft.com/services/cloud-services/)  
  
 **Веб-служба**  
  
 Веб-служба обслуживает элементы управления, которые отображаются у клиента средой выполнения схемы обучения. Кроме того, веб-служба поддерживает API конструктора, который используется функцией разработки схемы обучения. Элементы управления сохраняются службой в [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)].  
  
 **Компилятор (рабочая роль)**  
  
 Роль компилятора управляет публикацией элемента управления в группе публикации. Для хранения сообщений о задании публикации компилятор использует очередь. Результаты сохраняются в [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)].  
  
 [База данных SQL Azure](https://azure.microsoft.com/services/sql-database/)  
  
 Схема обучения использует [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)], чтобы хранить следующие элементы.  
  
-   Элементы управления, создаваемые с помощью схемы обучения.  
  
-   Разработка схемы обучения применительно к конфигурации.  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 Схема обучения использует [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] для проверки подлинности веб-службы.  
  
 [Диспетчер трафика Azure](https://azure.microsoft.com/services/traffic-manager/)  
  
 Схема обучения использует диспетчер трафика [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для балансировки нагрузки веб-службы с точки зрения доступности и производительности.  
  
 [Очередь службы хранилища Azure](https://azure.microsoft.com/services/storage/)  
  
 Очередь хранилища [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] служит для координации обмена данными между ролями веб-службы и компилятора.  
  
 [Хранилище BLOB-объектов Azure](https://azure.microsoft.com/services/storage/)  
  
 Схема обучения использует [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)] для хранения статического содержимого (клиентского кода [!INCLUDE[pn_JavaScript](pn-javascript.md)], изображений, содержимого CSS).  
  
 [Сеть доставки содержимого (CDN) Azure](https://azure.microsoft.com/services/cdn/)  
  
 Сеть CDN служит для кэширования клиентского статического содержимого ([!INCLUDE[pn_JavaScript](pn-javascript.md)], изображений и CSS-файлов), чтобы передавать их из глобальной сети CDN.