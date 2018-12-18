Если включено внедрение плиток и панелей мониторинга Power BI, то когда пользователь внедряет плитку или панель мониторинга Power BI, токен авторизации [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] этого пользователя для [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] используется для проверки подлинности в службе Power BI с неявным предоставлением прав, обеспечивая удобный «единый вход» для конечного пользователя.  
  
 Администратор может в любое время отключить внедрение плиток и панелей мониторинга Power BI, чтобы прекратить использование токенов авторизации [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] для проверки подлинности в службе Power BI. Все существующие плитки и панели мониторинга больше не будут отображаться для конечного пользователя.  
  
 Компонент или служба [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], необходимая для внедрения плиток Power BI, подробно рассматривается в следующем разделе.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 Эта служба предоставляет токен проверки подлинности, который передается в службу Power BI для проверки подлинности в API или пользовательском интерфейсе.