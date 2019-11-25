---
title: Управляемые свойства управляемого моделью приложения для представлений с PowerApps | MicrosoftDocs
description: Узнайте, как задавать управляемые свойства для представления
ms.custom: ''
ms.date: 06/12/2018
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
ms.assetid: a9014576-8fb2-4f28-b8bb-5d2d49d76e12
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b99fe00731066a4ee0f029bdba09c7eab9d8d67b
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "2702998"
---
# <a name="model-driven-app-managed-properties-for-views"></a>Управляемые свойства управляемого моделью приложения для представлений

<a name="BKMK_ManagedProperties"></a>   
 
 При создании настраиваемого общего представления в PowerApps, которое требуется включить в управляемое решение для распространения, вы можете запретить настраивать представление пользователям, устанавливающим решение.  
  
 По умолчанию управляемое свойство **Настраиваемое** большинства представлений имеет значение true, чтобы пользователи могли их настраивать. Если у вас нет серьезных причин блокировать эту возможность, рекомендуется разрешить пользователям настраивать представления в вашем приложении.  
  
## <a name="set-managed-properties-for-a-view"></a>Задание управляемых свойств для представления  
  
1.  Откройте [обозреватель решений](advanced-navigation.md#solution-explorer), разверните **Сущности**, выберите нужную сущность и выберите **Представления**.  
  
2.  Выберите настраиваемое общее представление.  
  
3.  В строке меню выберите **Другие действия** > **Управляемые свойства**.  

    > [!div class="mx-imgBorder"] 
    > ![Меню управляемых свойств](media/managed-properties.png)
  
4.  Задайте для параметров **Настраиваемый** или **Можно удалить** значение **True** или **False**.  

    > [!div class="mx-imgBorder"] 
    > ![Настройка управляемых свойств](media/set-managed-properties.png)
  
> [!NOTE]
> Этот параметр не вступит в силу, пока решение, содержащее представление, не будет экспортировано как управляемое решение и не будет установлено в другой среде.  

## <a name="next-steps"></a>Дальнейшие действия
[Сведения о представлениях](create-edit-views.md)
