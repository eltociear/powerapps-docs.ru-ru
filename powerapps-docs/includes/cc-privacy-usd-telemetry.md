---
ms.openlocfilehash: 943aa1eb128341b960270d21a53cec47003bcec4
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61585217"
---
Функция "Помогите улучшить [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)]" отправляет сведения об использовании [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)], такие как сведения об операционной системе, браузере, приложениях [!INCLUDE[pn_unified_service_desk](../includes/pn-unified-service-desk.md)] и версии [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)], с компьютера, на котором вы устанавливаете клиент. [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] отправляет сведения в [!INCLUDE[cc_Microsoft](cc-microsoft.md)] через безопасное подключение с Аналитикой организации и сохраняет в Хранилище таблиц [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].
  
> [!NOTE]
>  Аналитика организации предоставляет системному администратору организации [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] краткий обзор ее использования. Системный администратор может просматривать список наиболее активных пользователей, число выполняемых запросов пакета SDK, а также количество просмотров пользователями пакета SDK.
  
 Ниже приведен список компонентов и служб [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], связанных с функцией "Помогите улучшить Unified Service Desk".  
  
> [!NOTE]
>  Дополнительные сведения о дополнительных предложениях служб [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] см. в разделе [Центр управления безопасностью Microsoft Azure](https://azure.microsoft.com/en-us/support/trust-center/).  
  
 REST API данных OrgInsights для [облачных служб](https://azure.microsoft.com/en-us/services/cloud-services/) (веб-роль)  
  
 Эта веб-роль принимает запросы от диаграмм, отображающих данные в Аналитике организации. API считывает агрегированные данные из таблиц [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] и возвращает их.  
  
 [Хранилище BLOB-объектов Azure](https://azure.microsoft.com/en-us/services/storage/blobs/)  
  
 Необработанные данные телеметрии организации [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] собираются агентом наблюдения (который выполняется на каждом компьютере группы масштабирования) и отправляются в формате Bond (двоичный формат) в хранилище BLOB-объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 [Хранилище таблиц Azure](https://azure.microsoft.com/en-us/services/storage/tables/)  
  
 Необработанные данные телеметрии в хранилище BLOB-объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] статистически обрабатываются и сохраняются в Хранилище таблиц Azure, откуда считывает сведения облачная служба.  
  
 [Azure Active Directory](https://azure.microsoft.com/en-us/services/active-directory/)  
  
 Аналитика организации использует службу [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] для проверки подлинности веб-служб.  
  
 [Служебная шина Azure](https://azure.microsoft.com/en-us/services/service-bus/)  
  
 Агент наблюдения создает и помещает в очередь сообщения каждый раз, когда отправляет данные в хранилище BLOB-объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Эти сообщения отбираются каналом CMA для статистической обработки передаваемых данных.