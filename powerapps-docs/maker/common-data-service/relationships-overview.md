---
title: Обзор сущностей в PowerApps | MicrosoftDocs
description: Узнайте, как создавать и изменять сущности с помощью портала PowerApps
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
ms.openlocfilehash: 9fd6f2bf14a8007dd2b4f840a901316a0d3607cd
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "2701018"
---
# <a name="entity-relationships-overview"></a>Обзор отношений сущностей

Отношения между сущностями определяют способы, которыми записи сущности можно связать с записями в других сущностях или в той же самой сущности. Существует два типа отношений сущностей.
- **Отношения "один ко многим"**. В отношения сущностей "один ко многим" много ссылающихся (связанных) сущностей могут быть связаны с одной основной записью сущности (на которую задается ссылка). Указанная в ссылке запись сущности иногда называется "родительской", и записи ссылающейся сущности называются "дочерними".  Отношение "многие-к-одному" — это просто дочерняя перспектива отношения "один-ко-многим".
- **Отношения "многие-ко-многим"**. В отношении сущностей "многие-ко-многим" много записей сущности могут быть связаны с многими записями других сущностей. Записи, связанные с помощью отношения "многие ко многим", могут рассматриваться как равные, а отношения — равными. 

## <a name="see-also"></a>См. также
[Создание отношения между сущностями](data-platform-entity-lookup.md) <br/>
[Создание отношений сущностей "многие-ко-многим" в Common Data Service с помощью портала PowerApps](create-edit-nn-relationships-portal.md)
