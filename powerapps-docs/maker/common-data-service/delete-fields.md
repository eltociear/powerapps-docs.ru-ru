---
title: Удаление полей в Power Apps | MicrosoftDocs
description: Узнайте, как удалять поля
ms.custom: ''
ms.date: 06/20/2018
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
ms.assetid: 578ac950-da16-4ec6-a0a4-25f3aaa3b96e
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 224c07600a13b0adf9cedd7592be7f1c2befec90
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2019
ms.locfileid: "2864085"
---
# <a name="delete-fields"></a>Удаление полей

<a name="BKMK_DeletingFields"></a>   
 
 Пользователь с ролью безопасности "Системный администратор" может удалить любые настраиваемые поля, которые не являются частью управляемого решения. При удалении поля все данные, хранящиеся в этом поле, теряются. Единственным способом восстановить данные удаленного поля — восстановить базу данных в момент времени до удаления поля.  
  
 Прежде чем удалить настраиваемую сущность, необходимо удалить все зависимости, которые могут существовать в других компонентах решения. Откройте поле и нажмите кнопку **Показать зависимости** в строке меню для просмотра всех значений **Зависимые компоненты**. Например, если поле используется в форме или представлении, сначала необходимо удалить ссылки на поле в этих компонентах решения.  
  
 При удалении поля поиска автоматически удаляется его отношение сущностей 1:N.  

 ## <a name="next-steps"></a>Дальнейшие действия

 [Удаление настраиваемой сущности](data-platform-delete-entity.md)
