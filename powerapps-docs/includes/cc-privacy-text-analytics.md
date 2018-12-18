При включении функции текстовой аналитики включаются зависимые функции в [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], которые используют API текстовой аналитики в [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Cognitive Services для расширенного анализа. Это следующие зависимые функции:  
  
-   Предложения из базы знаний  
  
-   Анализ тем обращений  
  
-   Предложения подобных обращений  
  
 Администратор может включить функцию текстовой аналитики на вкладке **Параметры** > **Администрирование** > **Системные параметры** > **Предварительный просмотр** в организации [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)].  
  
 Если функция текстовой аналитики включена, при настройке предложений базы знаний на основе текстовой аналитики в [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] обращение и данные связанных с ним сущностей отправляются в API текстовой аналитики [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для извлечения ключевых слов или фраз. В API текстовой аналитики [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] никакие данные не сохраняются. В API текстовой аналитики [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для извлечения терминов отправляются только настроенные поля из конфигурации статьи базы знаний. Администратор или специалист по настройке может деактивировать конфигурацию статьи базы знаний, чтобы прекратить вызовы API текстовой аналитики [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Кроме того, специалист по настройке может прекратить использование основанных на текстовой аналитике предложений путем обратного переключения на предложения на основе полей в конфигурации формы сущности «Обращение».  
  
 Если функция текстовой аналитики включена, при настройке анализа тем обращений в [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] обращение и данные связанных с ним сущностей отправляются в API текстовой аналитики [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для определения темы. В API текстовой аналитики [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] никакие данные не сохраняются. В API текстовой аналитики [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для извлечения темы отправляются только настроенные поля из конфигурации модели темы. Администратор или специалист по настройке может деактивировать конфигурацию модели темы, чтобы прекратить вызовы API текстовой аналитики [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 Если функция текстовой аналитики включена, и при настройке предложений подобных обращений в [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] в правиле подобия включена функция расширенной текстовой аналитики, обращение и данные связанных с ним сущностей отправляются в API текстовой аналитики [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для извлечения ключевых слов и фраз. В API текстовой аналитики [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] отправляются только текстовые поля, настроенные в правиле подобия. В API текстовой аналитики [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] никакие данные не сохраняются. Администратор или специалист по настройке может деактивировать правило подобия, чтобы прекратить вызовы API текстовой аналитики [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 Компоненты и службы [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], необходимые для реализации функций, основанных на текстовой аналитике, подробно рассматриваются в следующих разделах.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Приложение Azure API](https://azure.microsoft.com/services/app-service/api/)  
  
 Приложение [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] API запускает веб-задания, которые считывают данные из организации [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] и отправляют данные в API текстовой аналитики для анализа темы. Приложение [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] API использует веб-задание для обработки фактических данных в фоновом режиме и записи выходных данных в хранилище больших двоичных объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Данные временно сохраняются в хранилище больших двоичных объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Затем, после определения темы, данные удаляются из хранилища [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 [Планировщик Azure](https://azure.microsoft.com/services/storage/)  
  
 Планировщик [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] служит для планового запуска веб-задания с целью анализа темы. Планировщик получает доступ только к расписанию создания модели темы.  
  
 [Таблица Azure](https://azure.microsoft.com/services/storage/)  
  
 Таблица [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] используется для передачи версии модели и контекста организации между приложением [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] API и веб-заданием.  
  
 [Хранилище BLOB-объектов Azure](https://azure.microsoft.com/services/storage/)  
  
 Веб-задания временно хранят данные в хранилище больших двоичных объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] и удаляют их после завершения работы конвейера логического приложения.  
  
 [API текстовой аналитики Azure](https://www.microsoft.com/cognitive-services/en-us/text-analytics-api)  
  
 API текстовой аналитики [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] передает данные на основе полей, настроенных в активных полях поиска в базе знаний, конфигурации модели темы или конфигурации правила подобия. Например, поля сущности «Обращение», такие как заголовок и описание, а также поле описания в связанных примечаниях и действиях, настраиваются в конфигурации поля поиска в базе знаний.  
  
 Поиск с сортировкой по релевантности [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]  
  
 Поиск с сортировкой по релевантности, если он включен администратором, можно использовать для поиска подобных записей для обращений. Заданные в правиле подобия поля текстового соответствия и поля точного соответствия используются для вызова API поиска с сортировкой по релевантности. Сведения об обработке данных см. в техническом описании поиска с сортировкой по релевантности для [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)].