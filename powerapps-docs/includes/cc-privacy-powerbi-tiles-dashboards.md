---
ms.openlocfilehash: 41ec7aed42a950e5adf0b87783fc568dbe9d02af
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61588437"
---
Если разрешено внедрение панелей мониторинга и плиток Power BI, то когда пользователь внедряет панель мониторинга или плитку Power BI, его токен авторизации [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] для [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] используется для проверки подлинности в службе Power BI с неявным предоставлением разрешения, обеспечивая простую процедуру единого входа для конечного пользователя.  
  
 Администратор может отключить внедрение плиток и панелей мониторинга Power BI в любое время, чтобы прекратить использование токена авторизации [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] для проверки подлинности в службе Power BI. Все существующие плитки или панели мониторинга перестанут отображаться для конечного пользователя.  
  
 Служба или компонент [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)], связанные с внедрением плиток Power BI, подробно описаны в следующем разделе.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 Эта служба предоставляет токен проверки подлинности, используемый для обмена со службой Power BI для проверки подлинности API и пользовательского интерфейса.