---
ms.openlocfilehash: 80997689e9d4ebca8eb4809cc3e94dab549482b5
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2019
ms.locfileid: "67224730"
---
Включив функцию анализа текста, вы разрешаете зависимым компонентам в [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], использующим API анализа текста [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Cognitive Services, предоставлять расширенные аналитические сведения. Эти зависимые компоненты приведены ниже:  
  
-   Предложения знаний  
  
-   Анализ тем обращений  
  
-   Предложения подобных обращений  
  
 Администратор может включить функцию анализа текста на вкладке **Параметры** > **Администрирование** > **Системные параметры** > **Предварительная версия** в организации [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)].  
  
 Когда вы, включив функцию анализа текста, настраиваете предложения знаний на основе анализа текста в [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)], обращение и данные связанных с ним сущностей отправляются в API анализа текста [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для извлечения ключевых слов или фраз. Никакие данные в API анализа текста [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] не сохраняются. В API анализа текста [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для извлечения терминов отправляются только поля, настроенные в конфигурации статьи базы знаний. Администратор или настройщик может отключить конфигурацию статьи базы знаний, чтобы прекратить выполнение вызовов к API анализа текста [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Кроме того, настройщик может прекратить использование предложений на основе анализа текста, переключившись обратно на предложения на основе поля в конфигурации форм сущностей обращений.  
  
 Когда вы, включив функцию анализа текста, настраиваете анализ тем обращений в [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)], обращение и данные связанных с ним сущностей отправляются в API анализа текста [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для определения темы. Никакие данные в API анализа текста [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] не сохраняются. Для извлечения темы в API анализа текста [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] отправляются только поля, настроенные в конфигурации модели тем. Администратор или настройщик может отключить модель тем, чтобы прекратить выполнение вызовов к API анализа текста [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 Если в правиле подобия включен параметр сложного анализа данных, когда вы, включив функцию анализа текста, настраиваете предложения подобных обращений в [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)], обращение и данные связанных с ним сущностей отправляются в API анализа текста [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для извлечения ключевых слов или фраз. В API анализа текста [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] отправляются только текстовые поля, настроенные в правиле подобия. Никакие данные в API анализа текста [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] не сохраняются. Администратор или настройщик может отключить правило подобия, чтобы прекратить выполнение вызовов к API анализа текста [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 Компоненты и службы [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], используемые с функцией анализа текста, подробно рассматриваются в следующих разделах.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Приложение Azure API](https://azure.microsoft.com/services/app-service/api/)  
  
 Приложение API [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] активирует веб-задания, считывающие данные из организации [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] и отправляющие их в API анализа текста для анализа тем. Приложение API [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] использует веб-задание для выполнения фактической обработки данных в фоновом режиме и записи выходных данных в хранилище BLOB-объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Данные временно хранятся в хранилище BLOB-объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. После завершения определения темы данные удаляются из хранилища [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 [Планировщик Azure](https://azure.microsoft.com/services/storage/)  
  
 Планировщик [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] используется для запуска веб-задания по расписанию для выполнения анализа тем. Планировщик распространяет только расписание сборки модели тем.  
  
 [Таблица Azure](https://azure.microsoft.com/services/storage/)  
  
 Таблица [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] используется для передачи версии модели и контекста организации между приложением API [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] и веб-заданием.  
  
 [Хранилище BLOB-объектов Azure](https://azure.microsoft.com/services/storage/)  
  
 Веб-задания временно хранят данные в хранилище BLOB-объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] и удаляют их после завершения выполнения конвейера приложения логики.  
  
 [API анализа текста Azure](https://www.microsoft.com/cognitive-services/en-us/text-analytics-api)  
  
 Данные отправляются в API анализа текста [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] на основе полей, настроенные в активных полях поиска в базе знаний, конфигурации модели тем или конфигурации правила подобия. Например, поля сущностей обращений, такие как заголовок и описание, а также поле описания в связанных заметках и действиях настраиваются в конфигурации поля поиска по статьям базы знаний.  
  
 Поиск с сортировкой по релевантности [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]  
  
 Если эта возможность включена администратором, вы можете использовать поиск с сортировкой по релевантности, чтобы искать схожие записи для обращений. Поля соответствия текста и точного соответствия, используемые в правиле подобия, применяются для вызова API поиска с сортировкой по релевантности. Дополнительные сведения об обработке данных см. в технических материалах о поиске с сортировкой по релевантности [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)].