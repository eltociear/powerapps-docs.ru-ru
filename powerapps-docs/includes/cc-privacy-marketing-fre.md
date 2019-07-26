---
ms.openlocfilehash: f331670a2fd6b051c91a7fe2bfa607c54c9ab41a
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2019
ms.locfileid: "67225250"
---
Включив [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)], вы даете согласие на разрешение потока данных из [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] в определенные службы [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] для выполнения некоторых маркетинговых процессов. Эти службы совместно называют "Службы [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)]".

Чтобы совершать взаимодействие с клиентами, [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] необходимо отправить определения взаимодействия с клиентами, электронной почты, формы отправки и маркетинговой страницы в эти службы [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)], работающие на [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]. Маркетинговые страницы далее отправляются на собственный экземпляр возможностей портала для [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)].

Чтобы персонализировать отправленные электронные письма [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)], необходимо включить поток данных в и из [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]. Дополнительные сведения о службах [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] см. ниже. Поток данных в [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] включает в себя синхронизацию контактов и учетных записей в [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]. Службы [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] используют эти данные для персонализации содержимого сообщений электронной почты. Данные, которые включены, зависят исключительно от определения электронной почты.

Чтобы пересчитать балл интереса моделей и сегменты маркетинга, [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] необходимо отправить определения балла интереса моделей и сегментов в [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] и использовать профили и взаимодействия в [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] в пределах этих вычислений.

Чтобы предоставить аналитические сведения взаимодействиям электронной почты и Интернета, захваченным службами [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)], собранные потоки данных переходят из служб [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] в [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] и [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)].

Если кроме этого включается интеграция управления событиями [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)], [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] синхронизирует события с [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] (напрямую через соединитель для [!INCLUDE[pn-crm-online-shortest](../includes/pn-crm-online-shortest.md)]) и с регистрациями событий и возвратами (через службы [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)], в качестве взаимодействий).

Поток данных, включающий [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)], является таковым.
- Данные сущности из [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] в [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)], использующие обычный соединитель входящей почты [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)], чтобы предоставить контент для персонализации электронной почты, оценки интересов и сегментации (в основном контактов и учетных записей, в конечном итоге потенциальных клиентов и событий)
- Данные сущности из [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] через службы [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] в [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)], чтобы предоставить идентификаторы для взаимодействий и аналитических сведений (взаимодействий с клиентом, маркетинговых писем, маркетинговых страниц)
- Взаимодействие из служб [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] в [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] (отслеживание электронной почты, веб-сайтов и ход выполнения взаимодействия с клиентом)
- Взаимодействия из [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] через службы [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] в [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] (регистрации и возвраты событий)
- [!INCLUDE[pn-insights](../includes/pn-insights.md)] (взаимодействия и ключевые показатели эффективности) из [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] через службы [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] в [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] (главным образом взаимодействия с клиентом, ход выполнения отправки электронной почты и результаты оценки интересов)
- Приложения [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] (сегментация и мини-приложения) из [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] непосредственно в выделенные и изолированные элементы пользовательского интерфейса в формах [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]

### <a name="marketing-services"></a>Службы маркетинга

[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] использует такие службы [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]:

- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Analytics
- [!INCLUDE[pn-azure-key-vault](../includes/pn-azure-key-vault.md)]
- [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] DocumentDB
- [!INCLUDE[pn-microsoft-azure-active-directory](../includes/pn-microsoft-azure-active-directory.md)]
- Хранилище [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]

> [!NOTE]
> Дополнительные сведения о дополнительных предложениях служб [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] см. в разделе [!INCLUDE[cc_privacy_note_azure_trust_center](../includes/cc_privacy_note_azure_trust_center.md)] (<https://azure.microsoft.com/support/trust-center/>).

### [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]

С помощью [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] активируется передача данных клиента в [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] для дальнейшей обработки. Для использования [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] для [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] может потребоваться соблюдение конкретных законов о конфиденциальности. Задавайте любые вопросы соответствующему представителю в вашей организации.

В настоящее время общедоступная предварительная версия [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] не обеспечивает тот же уровень безопасности и конфиденциальности взаимодействия с клиентами, что [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] или [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)]. [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] изначально встроена в службы [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)], а соответствующие стандарты безопасности и соответствия требованиям применяются для каждой службы [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]. Дополнительные сведения см. в Центре управления безопасностью [!INCLUDE[cc-microsoft](../includes/cc-microsoft.md)]: [https://azure.microsoft.com/support/trust-center/](https://azure.microsoft.com/support/trust-center/)

[!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] использует такие службы [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]:

- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Analytics
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] HDInsight (Spark, Phoenix, HBase)
- [!INCLUDE[pn-ms-azure-sql-database](../includes/pn-ms-azure-sql-database.md)]
- [!INCLUDE[pn-azure-key-vault](../includes/pn-azure-key-vault.md)]
- Хранилище секретов [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]
- Концентратор событий [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]
- [!INCLUDE[pn-azure-stream-analytics](../includes/pn-azure-stream-analytics.md)]
- Кэш Redis [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]
- [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]
- [!INCLUDE[pn-microsoft-azure-active-directory](../includes/pn-microsoft-azure-active-directory.md)]
- Мониторинг [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]
- Метрики [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]
- Веб-сайты [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]
- [!INCLUDE[pn_azure_service_bus](../includes/pn_azure_service_bus.md)]
- Хранилище [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)]
