---
ms.openlocfilehash: ac90bfc27e03047cf422c44c83f550608d67b57e
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2019
ms.locfileid: "67212857"
---
При включении возможностей портала для [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] данные [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], такие как имя клиента, имя продукта, номер обращения или любые настраиваемые сущности данных, могут быть доступны извне через портал [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]. Все данные, к которым предоставлен доступ через портал, хранятся в памяти веб-приложений Microsoft [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] для кэширования, а также в виде файлов на локальном жестком диске для использования функции поиска на портале.

Администратор клиента включает портал [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] путем его настройки с помощью [!INCLUDE[pn_dyn_365_admin_center](../includes/pn-dyn-365-admin-center.md)], в результате чего также происходит установка пакета (с решениями и данными) в выбранный экземпляр [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]. Администратор клиента или пользователь [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], назначенный в качестве администратора портала, может затем указать данные, которые будут доступны на портале. Чтобы впоследствии отключить возможности портала, администратор клиента может отменить дополнительную подписку на портал в [!INCLUDE[pn_Office_365](pn-office-365.md)].

Важные компоненты и службы [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], связанные с возможностями портала:
- [Веб-приложения Azure](https://azure.microsoft.com/services/app-service/web/): [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]Веб-приложения используются для размещения портала в [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].
- [Диспетчер трафика Azure](https://azure.microsoft.com/services/traffic-manager/): [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]Диспетчер трафика используется для обеспечения высокой доступности службы путем маршрутизации пользователя в веб-приложения, которые работают и работают. 
- [Служебная шина Azure](https://azure.microsoft.com/services/service-bus/): [!INCLUDE[pn_azure_service_bus](pn-azure-service-bus.md)](Разделы и подписки) используется для недействительности кэша порталов. [!INCLUDE[pn_azure_service_bus](pn-azure-service-bus.md)] временно хранит сообщения, которые активируются при изменении в [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] любой записи, связанной с порталом, и передает их в веб-приложения для пометки кэша как недействительного. 
- [Azure Key Vault](https://azure.microsoft.com/services/key-vault/): Все службы хранят данные конфигурации в [!INCLUDE[pn_azure_key_vault](pn_azure_key_vault.md)].
- Служба [хранилища Azure](https://azure.microsoft.com/services/storage/): Данные, связанные с Организацией, клиентом и порталом, хранятся в [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] хранилище.
- [Azure Active Directory](https://azure.microsoft.com/services/active-directory/): Все веб-службы используют [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] для проверки подлинности.
