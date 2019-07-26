---
ms.openlocfilehash: 1cdcb40245aae9a23ecb6d3392e412f8a60b95ba
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2019
ms.locfileid: "67212308"
---
Включив функцию "Рекомендации по продукту" при создании модели рекомендаций из [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)], исторические данные о транзакциях, основанные на сущностях данных корзины и их фильтре, будут отправлены в [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], обработаны в [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] и временно сохранены в хранилище [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], после чего отправлены в API рекомендаций Azure для создания модели машинного обучения. После создания модели с помощью API рекомендаций Azure данные удаляются из хранилища [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Обратите внимание, что для создания модели рекомендаций в [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] передаются только идентификаторы (идентификатор учетной записи, код продукта, идентификатор транзакции).

Администратор может включить функцию "Рекомендации по продукту" на вкладке **Параметры**&gt;**Администрирование**&gt;**Системные параметры**&gt;**Предварительная версия** в организации [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)]. Данные отправляются в API рекомендаций Azure только при создании модели рекомендаций. Системный администратор может удалить существующую модель, чтобы удалить данные, предоставляемые API рекомендаций Azure. Кроме того, системный администратор может удалить подключение к API рекомендаций Azure, чтобы отключить дальнейшее создание моделей рекомендаций.

Компоненты и службы [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], используемые с функцией "Рекомендации по продукту", подробно рассматриваются в следующих разделах.

[!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]

[Azure Logic Apps](https://azure.microsoft.com/services/app-service/logic/)

Эта служба обеспечивает конвейер организованных данных для синхронизации каталога продуктов и данных о транзакциях с API рекомендаций для создания версии модели рекомендаций. Этот конвейер выполняется в виде мультитенантной службы с несколькими приложениями API для обмена данными между организацией Dynamics 365 и API рекомендаций. Приложения логики запускаются из [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] с минимальным контекстом, таким как идентификатор версии модели и URL-адрес организации [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]. 

[Приложения API Azure](https://azure.microsoft.com/services/app-service/api/)

Это веб-приложения, которые активируют веб-задания, считывающие данные из организации [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] и отправляющие их в API рекомендаций для создания модели рекомендаций. Существует 3 приложения API и соответствующих веб-заданий — для чтения данных о продуктах, для чтения данных о транзакциях и для создания модели рекомендаций. Приложения API используют веб-задание для выполнения фактической обработки данных в фоновом режиме и записи выходных данных в хранилище BLOB-объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Данные временно хранятся в хранилище BLOB-объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. После создания модели данные удаляются из хранилища [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].

[Таблица Azure](https://azure.microsoft.com/services/storage/tables/)

Таблица [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] используется для передачи версии модели и контекста организации между приложения API и веб-заданием.

[Хранилище BLOB-объектов Azure](https://azure.microsoft.com/services/storage/) 

Данные временно сохраняются веб-заданиями в хранилище BLOB-объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] и удаляются после завершения выполнения конвейера приложения логики.

[API рекомендаций Azure](https://www.microsoft.com/cognitive-services/en-us/recommendations-api) В API рекомендаций Azure отправляется минимальный объем данных о кодах продуктов, идентификаторах транзакций и идентификаторах учетных записей для создания модели рекомендаций. Данные хранятся в службе API рекомендаций, пока не существует соответствующая версия модели.
