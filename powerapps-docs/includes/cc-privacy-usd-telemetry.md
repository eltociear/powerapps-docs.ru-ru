---
ms.openlocfilehash: 7b58f302f694246564d7073a954ecd53b1b25361
ms.sourcegitcommit: 982cab99d84663656a8f73d48c6fae03e7517321
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2019
ms.locfileid: "67456894"
---
Функция "Помогите улучшить [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)]" отправляет сведения об использовании [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)], такие как сведения об операционной системе, браузере, приложениях [!INCLUDE[pn_unified_service_desk](../includes/pn-unified-service-desk.md)] и версии [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)], с компьютера, на котором вы устанавливаете клиент. [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] отправляет сведения в [!INCLUDE[cc_Microsoft](cc-microsoft.md)] через безопасное подключение с Аналитикой организации и сохраняет в Хранилище таблиц [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].
  
> [!NOTE]
>  Аналитика организации предоставляет системному администратору организации [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] краткий обзор ее использования. Системный администратор может просматривать список наиболее активных пользователей, число выполняемых запросов пакета SDK, а также количество просмотров пользователями пакета SDK.
  
 Ниже приведен список компонентов и служб [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], связанных с функцией "Помогите улучшить Unified Service Desk".  
  
> [!NOTE]
>  Дополнительные сведения о дополнительных предложениях служб [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] см. в разделе [Центр управления безопасностью Microsoft Azure](https://azure.microsoft.com/support/trust-center/).  
  
 REST API данных OrgInsights для [облачных служб](https://azure.microsoft.com/services/cloud-services/) (веб-роль)  
  
 Эта веб-роль принимает запросы от диаграмм, отображающих данные в Аналитике организации. API считывает агрегированные данные из таблиц [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] и возвращает их.  
  
 [Хранилище BLOB-объектов Azure](https://azure.microsoft.com/services/storage/blobs/)  
  
 Необработанные данные телеметрии организации [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] собираются агентом наблюдения (который выполняется на каждом компьютере группы масштабирования) и отправляются в формате Bond (двоичный формат) в хранилище BLOB-объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 [Хранилище таблиц Azure](https://azure.microsoft.com/services/storage/tables/)  
  
 Необработанные данные телеметрии в хранилище BLOB-объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] статистически обрабатываются и сохраняются в Хранилище таблиц Azure, откуда считывает сведения облачная служба.  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 Аналитика организации использует службу [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] для проверки подлинности веб-служб.  
  
 [Служебная шина Azure](https://azure.microsoft.com/services/service-bus/)  
  
 Агент наблюдения создает и помещает в очередь сообщения каждый раз, когда отправляет данные в хранилище BLOB-объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Эти сообщения отбираются каналом CMA для статистической обработки передаваемых данных.