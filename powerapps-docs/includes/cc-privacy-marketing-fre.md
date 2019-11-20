При включении [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] вы даете согласие на передачу данных из [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] в определенные службы [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] для выполнения некоторых маркетинговых процессов. Все эти службы называются "службами [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]".

Для реализации цикла взаимодействия с клиентом [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] необходимо передавать адрес электронной почты, электронные формы и определения маркетинговых страниц в эти службы [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)], работающие в [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]. Затем маркетинговые страницы пересылаются в собственный экземпляр портала [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] клиента.

Для персонализации отправленных сообщений необходимо разрешить для [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] передачу данных в [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] и обратно. Дополнительные сведения о службе [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] см. ниже. Передача данных в [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] включает синхронизацию контактов и организация с [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]. Службы [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] используют эти сведения для персонализации содержимое электронной почты. Используемые данные зависят исключительно от определений сообщений электронной почты.

Для перерасчета моделей показателей интересов и маркетинговых сегментов [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] необходимо отправить определения моделей показателей интересов и сегментов в [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)], а также использовать в расчетах профили и взаимодействия в [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)].

Для анализа взаимодействия через Интернет и по электронной почте, регистрируемого службами [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)], собранные данные передаются из [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] в [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] и [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)].

Если в дополнение к этому включена интеграция управления мероприятиями [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)], [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] синхронизирует мероприятия с [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] (напрямую или через соединитель для [!INCLUDE[pn-crm-online-shortest](../includes/pn-crm-online-shortest.md)]), а также синхронизирует регистрации и входы в мероприятия (через службы [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)], в качестве взаимодействий).

Поток данных [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] содержит следующие данные.
- Данные сущностей из [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] в [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] с использованием регулярного входного соединителя [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] с целью предоставления содержимого для персонализации электронной почты, оценки интересов и сегментации (главным образом контактов и организаций, а в конечном счете также интересов и мероприятий)
- Данные сущностей из [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] через службы [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] в [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] с целью предоставления идентификаторов для взаимодействий и анализа (цикл взаимодействия с клиентом, маркетинговые сообщения электронной почты, маркетинговые страницы)
- Взаимодействия из служб [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] в [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] (отслеживание электронной почты, отслеживание веб-сайтов, отслеживание цикла взаимодействия с клиентом)
- Взаимодействия из [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] через службы [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] в [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] (регистрации и входы в мероприятия)
- [!INCLUDE[pn-insights](../includes/pn-insights.md)] (взаимодействия и КПЭ) из [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] через службы [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] в [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] (главным образом отслеживание цикла взаимодействия с клиентом и отправки сообщений электронной почты, а также результаты оценки интересов)
- [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] приложения (сегментация и мини-приложения) из [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] напрямую в выделенные и изолированные элементы интерфейса в формах [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]

### <a name="marketing-services"></a>Службы маркетинга

[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] использует следующие службы [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]:

- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Analytics
- [!INCLUDE[pn-azure-key-vault](../includes/pn-azure-key-vault.md)]
- [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] DocumentDB
- [!INCLUDE[pn-microsoft-azure-active-directory](../includes/pn-microsoft-azure-active-directory.md)]
- Служба хранилища [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]

> [!NOTE]
> Дополнительные сведения о других предлагаемых службах [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] см. на сайте [!INCLUDE[cc_privacy_note_azure_trust_center](../includes/cc_privacy_note_azure_trust_center.md)] (<https://azure.microsoft.com/support/trust-center/>).

### [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]

Используя [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)], вы активируете передачу данных о клиентах в [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] для дальнейшей обработки. Для использования [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] для [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] может потребоваться соблюдение определенного законодательства о конфиденциальности. Обращайтесь по всем вопросам к соответствующему представителю в своей организации.

В настоящее время приложение [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] находится в состоянии предварительной версии и не обеспечивает такой же уровень защиты конфиденциальности, как [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] или Common Data Service. Приложение [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] разработано на базе служб [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)], поэтому к нему применимы стандарты безопасности и соблюдения нормативных требований соответствующих служб [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]. Дополнительные сведения см. в центре управления безопасностью [!INCLUDE[cc-microsoft](../includes/cc-microsoft.md)]: [https://azure.microsoft.com/support/trust-center/](https://azure.microsoft.com/support/trust-center/)

[!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] использует следующие службы [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]:

- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Analytics
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] HDInsight (Spark, Phoenix, HBase)
- [!INCLUDE[pn-ms-azure-sql-database](../includes/pn-ms-azure-sql-database.md)]
- [!INCLUDE[pn-azure-key-vault](../includes/pn-azure-key-vault.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Secret Store
- Центр событий [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]
- [!INCLUDE[pn-azure-stream-analytics](../includes/pn-azure-stream-analytics.md)]
- Кэш Redis для [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]
- [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]
- [!INCLUDE[pn-microsoft-azure-active-directory](../includes/pn-microsoft-azure-active-directory.md)]
- Мониторинг [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]
- Показатели [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]
- Веб-сайты [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]
- [!INCLUDE[pn_azure_service_bus](../includes/pn_azure_service_bus.md)]
- Служба хранилища [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]
