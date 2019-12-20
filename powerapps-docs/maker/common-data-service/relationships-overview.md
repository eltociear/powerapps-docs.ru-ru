---
title: Обзор сущностей в Power Apps | MicrosoftDocs
description: Узнайте, как создавать и изменять сущности с помощью портала Power Apps
ms.custom: ''
ms.date: 07/25/2018
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
caps.latest.revision: 0
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 199c7705bd283cbc316b6a2b8056eba7f7507ea1
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2019
ms.locfileid: "2865439"
---
# <a name="entity-relationships-overview"></a>Обзор отношений сущностей

Отношения между сущностями определяют способы, которыми записи сущности можно связать с записями в других сущностях или в той же самой сущности. Существует два типа отношений сущностей.
- **Отношения "один ко многим"**. В отношения сущностей "один ко многим" много ссылающихся (связанных) сущностей могут быть связаны с одной основной записью сущности (на которую задается ссылка). Указанная в ссылке запись сущности иногда называется "родительской", и записи ссылающейся сущности называются "дочерними".  Отношение "многие-к-одному" — это просто дочерняя перспектива отношения "один-ко-многим".
- **Отношения "многие-ко-многим"**. В отношении сущностей "многие-ко-многим" много записей сущности могут быть связаны с многими записями других сущностей. Записи, связанные с помощью отношения "многие ко многим", могут рассматриваться как равные, а отношения — равными. 

## <a name="see-also"></a>См. также
[Создание отношения между сущностями](data-platform-entity-lookup.md) <br/>
[Создание отношений сущностей "многие-ко-многим" в Common Data Service с помощью портала Power Apps](create-edit-nn-relationships-portal.md)
