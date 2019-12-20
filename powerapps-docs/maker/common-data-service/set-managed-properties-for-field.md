---
title: Задание управляемых свойств для полей в Power Apps | MicrosoftDocs
description: Узнайте, как задавать управляемые свойства для поля
ms.custom: ''
ms.date: 06/19/2018
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
ms.assetid: 4ddcfcf3-5604-4b93-a5ee-589d4fb97fa4
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0b14b5ab55fe6bbaeeb11fb2de548621eb66501a
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2019
ms.locfileid: "2865350"
---
# <a name="set-managed-properties-for-fields"></a>Задание управляемых свойств для полей

<a name="BKMK_SettingManagedProperties"></a>   

 Управляемые свойства применяются, только если добавить поля в управляемое решение и импортировать это решение в другую среду. Эти параметры позволяют создателю решения управлять тем, какие возможности настройки этого поля они хотят предоставить пользователям, устанавливающим данное управляемое решение. Чтобы задать управляемые свойства для поля, выберите **Управляемые свойства** в строке меню.  
  
 Параметр **Может быть настроен** контролирует все остальные параметры. Если этот параметр `False`, ни один из других параметров не применяется. Если параметр `True`, можно указать другие параметры настройки.  
  
 Если поле можно настроить, задайте для следующих параметров значение `True` или `False`.  
  
- **Отображаемое имя может быть изменено**  
  
- **Может изменить уровень требований**  
  
- **Можно изменять дополнительные свойства**  
  
 Эти параметры говорят сами за себя. Если для всех отдельных параметров задать значение `False`, можно также установить для параметра **Может быть настроен** значение `False`.  

 ## <a name="next-steps"></a>Дальнейшие действия

 [Создание и изменение полей](create-edit-fields.md)
