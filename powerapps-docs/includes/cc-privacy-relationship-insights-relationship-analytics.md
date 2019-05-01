---
ms.openlocfilehash: 864bb7bde775f88cdf43ba5c453bd1ff02f81b85
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61585231"
---
Если включить функцию анализа отношений, относящуюся ко встроенной аналитике,              данные клиента [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], включая личные сведения пользователей, будут отправлять и сохраняться в               службе [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] в Azure для вычисления КПЭ отношений между              клиентами и пользователями [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]. Данные также временно сохраняются в              [!INCLUDE[pn_azure_service_fabric](pn-azure-service-fabric.md)] и обрабатываются для получения дополнительных выходных данных, таких как тренды и работоспособность отношений, после чего эти сведения возвращаются в [!INCLUDE[pn_customerinsight_short](pn-customer-insights-short.md)], а затем — в              [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)].  
  
 Администратор может включить функцию анализа отношений, установив соответствующее решение в               организации [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)]. Кроме того, впоследствии администратор может отключить функцию, удалив это решение из              организации [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)].  
  
 Разрешив использовать                данные [!INCLUDE[pn_Exchange](pn-exchange.md)] в качестве источника данных, вы будете отправлять               данные клиента [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], включая личные сведения конечного пользователя, из              [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] в              [!INCLUDE[pn_Exchange_Online](pn-exchange-online.md)] для сбора дополнительных данных, которые будут использоваться для расчета КПЭ и создания других аналитических сведений.  Чтобы полностью включить эту функцию,               администратору [!INCLUDE[pn_Office_365](pn-office-365.md)][!INCLUDE[pn_Exchange](pn-exchange.md)] также потребуется принять отдельное заявление о согласии в              приложении [!INCLUDE[pn_Exchange](pn-exchange.md)].  Когда оба администратора предоставили свое согласие через соответствующие продукты,              [!INCLUDE[pn_Exchange](pn-exchange.md)] предоставит метаданные собраний и электронной почты, которые будут храниться              [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] и использовать для улучшения расчетов КПЭ, а, возможно, и других аналитических сведений, заданных              администратором [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]. Отключение              использования данных [!INCLUDE[pn_Exchange](pn-exchange.md)] в качестве источника данных в конфигурации анализа отношений не приведет к удалению              данных [!INCLUDE[pn_Exchange](pn-exchange.md)] из              [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)].  Удаление              данных [!INCLUDE[pn_Exchange](pn-exchange.md)] в              [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] можно осуществить только непосредственно из              [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)].  
  
 Компоненты и службы [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], используемые с функцией анализа отношений, подробно рассматриваются в следующих разделах.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 **[!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]**  
  
 Служба [!INCLUDE[pn_customerinsight_short](pn-customer-insights-short.md)], выполняющаяся в              [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], хранит              данные [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], включая личные сведения клиентов, для расчета выходных данных для функции анализа отношений. На предварительную версию [!INCLUDE[pn_customerinsight_short](pn-customer-insights-short.md)] распространяются эти [дополнительные условия использования предварительных версий функций](http://go.microsoft.com/fwlink/p/?LinkId=511446).  
  
 [Узнайте больше о предварительной версии Customer Insights](https://azure.microsoft.com/en-us/services/customer-insights/).  
  
 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)  
  
 [!INCLUDE[pn_azure_service_fabric](pn-azure-service-fabric.md)] используется для временного хранения              данных[!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)], включая личные сведения о клиентах, для расчета выходных данных функции анализа отношений.