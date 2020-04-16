---
title: Использование решения для настройки Power Apps | Документация Майкрософт
description: Узнайте, как настроить Power Apps
ms.custom: ''
ms.date: 02/20/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: f993c4ed-1fc3-4e47-bef1-d38695ddb11a
caps.latest.revision: 57
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e32920e3a3ae2bd3c65bfaae6da4b875d4dff645
ms.sourcegitcommit: 3e6c499a65ada8a9f28022a02f64030b0c069a17
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2020
ms.locfileid: "3226440"
---
# <a name="use-a-solution-to-customize"></a>Использование решения для настройки
Мы рекомендуем вам создать решение для управления настройками. С помощью настраиваемого решения вы можете легко найти только те компоненты решения, которые вы настроили, согласовано применять префикс издатель решения и экспортировать свое решение для распространения в других средах.  

Если вы не используете настраиваемое решение, вы будете работать с решением по умолчанию в неуправляемом слое. Есть два решения по умолчанию в каждой среде Common Data Service:  
- Решение по умолчанию Common Data Service. Это базовое решение, которое доступно для создателей для использования по умолчанию для настроек в среде. Решение по умолчанию Common Data Service полезно, когда вы хотите оценить или изучить Power Apps.  
- Решение по умолчанию. Это специальное решение, которое содержит все компоненты в системе. Решение по умолчанию полезно для обнаружения всех компонентов и конфигураций в вашей системе.  

## <a name="why-you-shouldnt-use-the-default-solutions-to-manage-customizations"></a>Почему вы не должны использовать решение по умолчанию для управления настройками
Есть несколько причин, по которым вам не следует создавать приложения и выполнять настройки ни в каком решении по умолчанию:  
- Решение по умолчанию содержит все компоненты и настройки из всех решений в среде. 
- По умолчанию все включенные пользователи в среде могут создавать приложения и настраивать компоненты в решении по умолчанию Common Data Services. 
- Трудно найти или идентифицировать настройки, которые вы сделали в среде, используя какое-либо решение по умолчанию. 
- Используя какое-либо решение по умолчанию, при создании компонентов также будет использоваться назначенный ему издатель по умолчанию. Это может привести к тому, что к некоторым компонентам будет применен неправильный префикс издателя. 
- Решение по умолчанию не может быть экспортировано. Следовательно, вы не можете распространять решение по умолчанию в другую среду. 

<!-- Notice that if you have installed or imported other applications or solutions, additional solutions may be available in the solutions list. 

By default,  when you build or customize a model-driven app, you work with the solution called Common Data Services Default Solution. You can open the Common Data Services Default Solution to view and edit the components that are contained in it. To do this, follow these steps.
 
1.  On the left navigation pane select **Solutions**.

2.  In the list of solutions, select **Common Data Services Default Solution**.
  
> [!TIP]
>  If you plan to distribute the applications your make, consider changing the publisher customization prefix. More information: [Solution publisher prefix](change-solution-publisher-prefix.md).  -->
  
<a name="BKMK_PrivacyNotice"></a>   

## <a name="privacy-notices"></a>Уведомления о конфиденциальности  
 [!INCLUDE[cc_privacy_crm_gcc_solution_import](../../includes/cc-privacy-crm-gcc-solution-import.md)]  
  
 [!INCLUDE[cc_privacy_crm_customizations](../../includes/cc-privacy-crm-customizations.md)]  
  
### <a name="see-also"></a>См. также  
[Создание решения](create-solution.md) <br />
[Общие сведения о компонентах управляемых моделью приложений](../model-driven-apps/model-driven-app-components.md)


