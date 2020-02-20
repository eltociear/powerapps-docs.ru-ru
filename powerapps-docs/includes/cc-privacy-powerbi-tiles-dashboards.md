---
ms.openlocfilehash: 162e914a6753e9fd95a8ec57857c280469308a68
ms.sourcegitcommit: 9576b34403634a8e960eb5f8e320a14c4a03746c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2019
ms.locfileid: "72517343"
---
Если разрешено внедрение панелей мониторинга и плиток Power BI, то, когда пользователь внедряет панель мониторинга или плитку Power BI, его токен авторизации [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] для службы Common Data Service используется для проверки подлинности в службе Power BI с неявным предоставлением разрешения, обеспечивая простую процедуру единого входа для конечного пользователя.  
  
 Администратор может отключить внедрение плиток и панелей мониторинга Power BI в любое время, чтобы прекратить использование токена авторизации [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] для проверки подлинности в службе Power BI. Все существующие плитки или панели мониторинга перестанут отображаться для конечного пользователя.  
  
 Служба или компонент [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], связанные с внедрением плиток Power BI, подробно описаны в следующем разделе.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 Эта служба предоставляет токен проверки подлинности, используемый для обмена со службой Power BI для проверки подлинности API и пользовательского интерфейса.
