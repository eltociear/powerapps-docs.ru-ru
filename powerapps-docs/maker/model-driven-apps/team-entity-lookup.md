---
title: Добавление сущности рабочей группы в качестве элемента подстановки в вашем приложении | MicrosoftDocs
description: Узнайте, как добавить сущность рабочей группы в качестве элемента подстановки в вашем приложении
ms.custom: ''
ms.date: 07/24/2019
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
ms.assetid: ''
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 81b20a326be239445422cce51a54b2e0b991d5c4
ms.sourcegitcommit: a7f2313a048d3b8a03516a2e4c349f3fb08f4a22
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2019
ms.locfileid: "2805708"
---
# <a name="add-an-entity-as-a-lookup-option-in-your-app"></a>Добавление сущности в качестве элемента подстановки в вашем приложении

С приложениями единого интерфейса, чтобы сущность была доступна в списке подстановки, она должна быть добавлена в приложение. Например, записи контакты могут назначаться пользователю или рабочей группе.  

> [!div class="mx-imgBorder"] 
> ![](media/entity-lookup-teams.png "Entity lookup with both users and teams available")

Однако если сущность пользователя включена в приложение, а сущность рабочей группы — нет, только записи пользователей отображаются в списке подстановки. 

> [!div class="mx-imgBorder"] 
> ![](media/entity-lookup-user-only.png "Entity lookup with users only")

## <a name="add-the-team-entity-to-an-app"></a>Добавление сущности рабочей группы в приложение

1. Откройте приложение в конструкторе приложений. 
2. Выберите вкладку **Компоненты**, выберите **Сущности**, затем выберите **Рабочая группа**.    

    > [!div class="mx-imgBorder"] 
    > ![](media/add-team-entity-app.png "Add the team entity to the app")

3. Выберите **Сохранить** и выберите **Опубликовать**, чтобы сделать изменение доступным пользователям приложения.   

