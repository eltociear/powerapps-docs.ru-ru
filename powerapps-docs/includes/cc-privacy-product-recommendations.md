Если функция "Рекомендации по продукту" включена, при создании модели рекомендации в [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] исторические данные о транзакциях, основанные на настроенных сущностях данных корзины и их фильтре, отправляются в [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], обрабатываются в [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], временно сохраняются в хранилище [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] и, наконец, отправляются в API рекомендаций Azure для создания модели машинного обучения. После создания модели с помощью API рекомендаций Azure данные удаляются из хранилища [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Обратите внимание, что для создания модели рекомендаций в [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] отправляются только идентификаторы (код организации, артикул, код транзакции).

Администратор может включить функцию "Рекомендации по продукту" на вкладке **Параметры** &gt; **Администрирование** &gt; **Системные параметры** &gt; **Предварительный просмотр** в организации [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)]. Данные отправляются в API рекомендаций Azure только при создании модели рекомендаций. Системный администратор может удалить существующую модель, чтобы удалить данные, переданные в API рекомендаций Azure. Кроме того, системный администратор может удалить подключение к API рекомендаций Azure, чтобы исключить создание каких-либо моделей рекомендаций в будущем.

Компоненты и службы [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], которые задействует функция "Рекомендации по продукту", подробно рассматриваются в следующих разделах.

[!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]

[Приложения логики Azure](https://azure.microsoft.com/services/app-service/logic/)

Обеспечивают согласованный конвейер данных для синхронизации каталога продуктов и данных транзакций с API рекомендаций для создания версии модели рекомендаций. Этот конвейер выполняется как мультитенантная служба с несколькими приложениями API для передачи данных между организацией Dynamics 365 и API рекомендаций. Приложения логики запускаются из [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] с минимальным контекстом, таким как код версии модели и URL-адрес организации [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]. 

[Приложения Azure API](https://azure.microsoft.com/services/app-service/api/)

Это веб-приложения, которые запускают веб-задания, считывающие данные из организации [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] и отправляющие данные в API рекомендаций для создания модели рекомендаций. Предусмотрено три приложения API с соответствующими веб-заданиями — одно для чтения данных о продуктах, второе для чтения данных о транзакциях и третье для создания модели рекомендаций. Приложения API используют веб-задание для обработки фактических данных в фоновом режиме и записи выходных данных в хранилище больших двоичных объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Данные временно сохраняются в хранилище больших двоичных объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. В конце, после создания модели данных, данные удаляются из хранилища [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].

[Таблица Azure](https://azure.microsoft.com/services/storage/tables/)

Таблица [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] используется для передачи версии модели и контекста организации между приложением API и веб-заданием.

[Хранилище BLOB-объектов Azure](https://azure.microsoft.com/services/storage/) 

Данные временно сохраняются веб-заданиями в хранилище больших двоичных объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] и удаляются после завершения работы конвейера приложения логики.

[API рекомендаций Azure](https://www.microsoft.com/cognitive-services/recommendations-api) В API рекомендаций Azure для создания модели рекомендаций передаются минимальные данные в виде артикулов, кодов транзакций и кодов организаций. Данные хранятся в службе API рекомендаций в течение времени существования соответствующей версии модели.
