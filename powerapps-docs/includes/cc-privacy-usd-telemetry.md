Функция "Помочь улучшить [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)]" отправляет сведения об использовании [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)], такие как сведения об операционной системе, сведения о браузере, сведения об определенном приложении [!INCLUDE[pn_unified_service_desk](../includes/pn-unified-service-desk.md)] и версия [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)], с компьютера, на котором установлен клиент. [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] отправляет сведения в [!INCLUDE[cc_Microsoft](cc-microsoft.md)] через безопасное подключение к аналитике организации, и сведения хранятся в хранилище таблиц [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].
  
> [!NOTE]
>  В аналитики организации системный администратор организации [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] может просмотреть краткий обзор использования организации. Системный администратор может просматривать большинство активных пользователей, а также число запросов SDK, которые были инициированы и просмотрены пользователями SDK.
  
 Ниже представлен список компонентов и служб [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], используемых с функцией "Помочь улучшить Unified Service Desk".  
  
> [!NOTE]
>  Дополнительные сведения о других предлагаемых службах [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] см. в [центре управления безопасностью Microsoft Azure](https://azure.microsoft.com/support/trust-center/).  
  
 [Облачные службы](https://azure.microsoft.com/services/cloud-services/) REST API данных OrgInsights (веб-роль)  
  
 Эта веб-роль принимает запросы от диаграмм, на которых отображаются данные в аналитике организации. API считывает агрегированные данные из таблиц [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] и возвращает их.  
  
 [Хранилище BLOB-объектов Azure](https://azure.microsoft.com/services/storage/blobs/)  
  
 Необработанные данные телеметрии организации [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] собираются агентом мониторинга (который запускается на каждом компьютере тарифной группы) и отправляются в формате Bond (двоичный формат) в хранилище больших двоичных объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)].  
  
 [Хранилище таблиц Azure](https://azure.microsoft.com/services/storage/tables/)  
  
 Необработанные данные телеметрии в хранилище больших двоичных объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] агрегируются и сохраняются в хранилище таблиц Azure, которое считывается облачной службой.  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 Аналитика организации использует службу [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] для проверки подлинности веб-служб.  
  
 [Служебная шина Azure](https://azure.microsoft.com/services/service-bus/)  
  
 Агент мониторинга создает и помещает в очередь сообщения при каждой оправке данных в хранилище больших двоичных объектов [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]. Эти сообщения выбираются каналом CMA для агрегирования отправленных данных.