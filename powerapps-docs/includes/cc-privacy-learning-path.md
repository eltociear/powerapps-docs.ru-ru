Включив функцию плана обучения, статический HTML, вы разрешаете хранить изображения и скрипты в сети доставки содержимого (CDN) [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Кроме того, все отображаемое динамическое содержимое будет храниться в кэше Redis для [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], используемом для предварительного кэширования из базы данных SQL [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 Администратор может включить и отключить использование функции плана обучения в экземпляре [!INCLUDE[pn_crm_online_shortest](pn-crm-online-shortest.md)] с помощью параметра "Включить управляемую справку" в организации [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)].  
  
 Компоненты и службы [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], используемые с функцией плана обучения, подробно рассматриваются в следующих разделах.  
  
> [!NOTE]
>  Дополнительные сведения о других предлагаемых службах Azure см. в [центре управления безопасностью Microsoft Azure](https://azure.microsoft.com/support/trust-center/).  
  
 [Облачные службы](https://azure.microsoft.com/services/cloud-services/)  
  
 **Среда выполнения схемы обучения (веб-роль)**  
  
 Это веб-приложение, которое предоставляет содержимое для пользователей.  
  
 **Служба схемы обучения (рабочая роль)**  
  
 Рабочая роль отвечает за обработку данных из базы данных SQL [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] и их кэширование в кэше Redis для [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 [База данных SQL Azure](https://azure.microsoft.com/services/sql-database/)  
  
 Схема обучения использует базу данных SQL, чтобы хранить:  
  
-   Содержимое  
  
-   Метаданные содержимого  
  
-   Метаданные системы  
  
 [Хранилище BLOB-объектов Azure](https://azure.microsoft.com/services/storage/)  
  
 HTML, изображения, [!INCLUDE[pn_JavaScript](pn-javascript.md)] и CSS хранятся в хранилище больших двоичных объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 [Сеть доставки содержимого (CDN) Azure](https://azure.microsoft.com/services/cdn/)  
  
 Схема обучения использует сеть доставки содержимого [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для предоставления статического содержимого для среды выполнения опросов, такого как HTML, изображения, [!INCLUDE[pn_JavaScript](pn-javascript.md)] и CSS.  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 Схема обучения использует службу [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] для проверки подлинности веб-служб, в частности для конструктора. В настоящее время конструктор недоступен для клиентов и партнеров. Таким образом, проверка подлинности выполняется только в пределах домена [!INCLUDE[cc_Microsoft](cc-microsoft.md)].  
  
 [Кэш Redis для Azure](https://azure.microsoft.com/services/cache/)  
  
 Схема обучения использует кэш Redis для [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для кэширования динамического содержимого, предоставляемого пользователям.  
  
 [Диспетчер трафика Azure](https://azure.microsoft.com/services/traffic-manager/)  
  
 Схема обучения использует диспетчер трафика для повышения доступности важных приложений за счет отслеживания [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] или внешних сайтов и служб и автоматического направления пользователей в новое расположение в случае сбоя.  
  
 [Диспетчер ресурсов Azure](https://azure.microsoft.com/features/resource-manager/)  
  
 Схема обучения использует диспетчер ресурсов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для развертывания CDN, кэша Redis, базы данных SQL и облачных служб как групп ресурсов, чтобы они находились в согласованном состоянии и были доступны для повторного развертывания.