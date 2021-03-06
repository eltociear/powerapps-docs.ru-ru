Когда функция "Мнение клиента" активирована для Dynamics 365, при публикации опроса из Dynamics 365 определение опроса будет отправлено в Azure и сохранено в службе хранилища Azure. Когда респондент отправляет опрос (предварительно перейдя по ссылке с приглашением пройти опрос, отправленной ему по электронной почте), ответы на опрос временно сохраняются в служебной шине Azure, а затем извлекаются и сохраняются в Dynamics 365. После сохранения ответов в Dynamics 365 они удаляются из Azure.  
  
 Обратите внимание, что при обработке опроса для показа его респонденту в опрос можно включать данные Dynamics 365, такие как имя клиента, имя продукта, номер обращения и т. д. (внутри элементов опроса, таких как вопросы, ответы и т. д.). При создании ссылки — приглашения пройти опрос — эти данные Dynamics 365 будут отправлены из Dynamics 365 и сохранены в базе данных SQL Azure в обмен на идентификатор, который используется в ссылке-приглашении. Этот идентификатор используется для отображения данных Dynamics 365 в опросе после открытия опроса по ссылке-приглашению. Идентификаторы в ссылке на опрос, отправленной респонденту по электронной почте, хранятся в системе электронной почты респондента.  
  
 Администратор может включить функцию "Мнение клиента" для Dynamics 365, установив ее как решение в организации Dynamics 365. Впоследствии администратор может отключить эту функцию, удалив это решение из организации Dynamics 365.  
  
 Компоненты и службы Azure, необходимые для реализации функции "Мнение клиента" в Dynamics 365, подробно рассматриваются в следующих разделах.  
  
 Примечание. Дополнительные сведения о других предлагаемых службах Azure см. в центре управления безопасностью Microsoft Azure ([https://azure.microsoft.com/support/trust-center/](https://azure.microsoft.com/support/trust-center/)).  
  
 **Облачные службы** ([https://azure.microsoft.com/services/cloud-services/](https://azure.microsoft.com/services/cloud-services/))  
  
 **Служба конструктора (веб-роль)**  
  
 Эта веб-роль предоставляет несколько веб-служб для обмена данными между организацией Dynamics 365 и компонентами Azure "Мнение клиента" для Dynamics 365, поддерживающими обслуживание нескольких развертываний одним экземпляром.  Например, опросы публикуются и хранятся в хранилище BLOB-объектов Azure.  Ответы на опросы извлекаются из очереди служебной шины Azure и возвращаются для сохранения в организации Dynamics 365.  Аутентификация всех запросов выполняется с помощью Azure Active Directory.  
  
 **Среда выполнения опроса (веб-роль)**  
  
 Это веб-приложение, которое обслуживает опросы респондентов.  Отправленные ответы на опросы временно сохраняются в очереди служебной шины Azure, после чего они обрабатываются и извлекаются асинхронной службой Dynamics 365.  
  
 **Обработчик ответов (рабочая роль)**  
  
 Эта рабочая роль отвечает за обработку исходных результатов заполненных опросов и их преобразование в ответы, которые соответствуют требованиям Dynamics 365.  
  
 **Обработчик push-уведомлений (рабочая роль)**   Эта рабочая роль отвечает за обработку действительных ответов опросов и их обновление как записей сущностей Dynamics 365. 
 
 **Azure Key Vault** ([https://azure.microsoft.com/services/key-vault/](https://azure.microsoft.com/services/key-vault/))  
  
 Все облачные службы хранят данные конфигурации в Azure Key Vault.  Данные организаций и клиентов хранятся в SQL Azure.  
  
 **База данных SQL Azure** ([https://azure.microsoft.com/services/sql-database/](https://azure.microsoft.com/services/sql-database/))  
  
 Решение "Мнение клиента" для Dynamics 365 использует SQL Azure для хранения:  
  
-   передаваемых данных;  
  
-   метаданных опросов;  
  
-   данных организаций (клиентов).  
  
 **Хранилище BLOB-объектов Azure** ([https://azure.microsoft.com/services/storage/](https://azure.microsoft.com/services/storage/))  
  
 Определения опросов и не до конца заполненные (сохраненные) ответы сохраняются в хранилище BLOB-объектов Azure.  
  
 **Сеть доставки содержимого (CDN) Azure** ([https://azure.microsoft.com/services/cdn/](https://azure.microsoft.com/services/cdn/))  
  
 Решение "Мнение клиента" для Dynamics 365 использует сеть доставки содержимого Azure для передачи статического содержимого в среду выполнения опроса, например изображений (в том числе отправленных изображений, таких как логотипы клиентов), кода JavaScript и CSS.  
  
 **Azure Active Directory** ([https://azure.microsoft.com/services/active-directory/](https://azure.microsoft.com/services/active-directory/))  
  
 Решение "Мнение клиента" для Dynamics 365 использует службу Azure Active Directory для аутентификации веб-служб.  
  
 **Служебная шина Azure** ([https://azure.microsoft.com/services/service-bus/](https://azure.microsoft.com/services/service-bus/))  
  
 Сообщения, создаваемые при отображении и отправке опросов, временно сохраняются в очереди служебной шины Azure организации (клиента), пока рабочая роль Azure не отправит ответы опроса в экземпляр Dynamics 365 организации и не сохранит их как записи сущностей Dynamics 365.
