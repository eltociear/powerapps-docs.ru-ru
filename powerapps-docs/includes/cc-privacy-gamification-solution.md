---
ms.openlocfilehash: 747ea34b784b852261debe91f587d64ee3277804
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61582977"
---
Установив и включив решение [!INCLUDE[pn_gamification](pn-gamification.md)], идентификаторы учетной записи пользователя (например, имя, фамилия и адрес электронной почты) будут сохранены в [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], чтобы разрешить авторизацию с помощью службы [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)], которая размещена в [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Это относится ко всем пользователям, которые включены администратором в службу [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]. Решение [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] отправляет настроенные администратором данные ключевых показателей эффективности в службу [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Эти данные хранятся в структурированном хранилище [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], а также хранилище больших двоичных объектов.  Каждый пользовательский аватар, награды и логотип компании хранится в [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], но информация не возвращается в [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)].  
  
Обратите внимание, что администраторы и авторизованные пользователи могут использовать данные [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)], такие как телефонные звонки, возможности и забронированные доходы, чтобы настроить KPI для использования в играх. Служба [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] не инициирует вызовы [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] и отвечает только на данные, такие как игры, в которых используются KPI, которые возвращаются к [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)].  
  
Администратор также может разрешить публикацию телевизионного потока [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)]. Игровые менеджеры могут настроить телевизионные потоки [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] и включить общедоступную потоковую передачу для просмотра телевизионного потока всех пользователей Интернета, у которых есть ссылка на канал.  
  
После этого администратор может отключить функциональность [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)], удалив это решение из организации [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)].  
  
Компоненты и службы [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], используемые с функцией [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)], подробно рассматриваются в следующих разделах.  
  
[!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
[Облачные службы](https://azure.microsoft.com/services/cloud-services/)  
  
 **Служба конструктора (веб-роль)**  
  
Это обеспечивает несколько веб-служб для связи между [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] ​​организацией и многопользовательскими [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] компонентами. Например, сведения об игрофикации хранятся в [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] SQL Storage.  В игровых вычислениях используется очередь [!INCLUDE[pn_azure_service_bus](pn-azure-service-bus.md)] и возвращается для оценки и отображения в службе.  Пользовательские и загруженные пользователем образы хранятся в [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)]. Все запросы проходят проверку подлинности в [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)].  
  
[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)  
  
Все службы хранят данные конфигурации в [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)].  
  
[База данных SQL Azure](https://azure.microsoft.com/services/sql-database/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] использует SQL [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для хранения:  
  
- Данные ключевого показателя эффективности  
  
- Вычисления игры  
  
- данных организации (владельца).  
  
[Хранилище BLOB-объектов Azure](https://azure.microsoft.com/services/storage/)  
  
Аватары, логотипы компании и другие обновленные пользовательские образы хранятся в [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)].  
  
[Сеть доставки содержимого Azure (CDN)](https://azure.microsoft.com/services/cdn/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] использует [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] CDN во время выполнения статического содержимого, например образов (включая загруженные образы, такие как пользовательские логотипы), [!INCLUDE[pn_JavaScript](pn-javascript.md)] и CSS.  
  
[Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] использует [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] для проверки подлинности пользователей и определения права на использование платформы.