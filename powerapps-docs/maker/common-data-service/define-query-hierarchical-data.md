---
title: Определение и запрос иерархических данных с помощью Common Data Service | MicrosoftDocs
description: Узнайте, как определять и запрашивать иерархически связанных данные
ms.custom: ''
ms.date: 06/02/2018
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
ms.assetid: 0cf62817-5ff5-40bb-ad17-e1f6b0921720
caps.latest.revision: 42
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c829665baf2688c755bdfba7debb19d7b69a1c46
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "2758691"
---
# <a name="define-and-query-hierarchically-related-data"></a>Определение и запрос иерархически связанных данных

Пользователь может получить ценную аналитическую бизнес-информацию, определяя и запрашивая иерархически связанные данные. Функции иерархического моделирования и визуализации предоставляют несколько преимуществ:  
  
- Просмотр и изучение сложной иерархической информации.  
- Просмотр ключевых показателей эффективности в контекстуальном представлении иерархии.  
- Визуальный анализ ключевой информации при работе с веб-сайтом и планшетами.  
  
Некоторые стандартные сущности уже имеют определенные иерархии. Для других сущностей, включая настраиваемые сущности, можно включить иерархию и создавать визуализации. 

## <a name="define-hierarchical-data"></a>Определение иерархических данных

С Common Data Service структуры иерархических данных поддерживаются *ссылающимися на себя* отношениями "один-ко-многим" (1:N) связанных записей. 

> [!NOTE]
> *Ссылка на себя* означает, что сущность связана сама с собой. Например, сущность "Организация" имеет поле подстановки для связи ее с записью другой сущности организации.

Если имеется отношение "один-ко-многим" (1: N) со ссылкой на себя, в определении отношения для параметра **Иерархический** можно задать значение **Да**.

![Иерархический параметр в определении отношения](media/self-referential-relationship-car-solution-explorer.png)

Чтобы запросить данные как иерархию, необходимо настроить ссылающиеся на себя отношения "один-ко-многим" (1:N) как иерархические. Это действие можно выполнить только с помощью обозревателя решений.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

Чтобы включить иерархию:  
  
1. Во время [просмотра отношений 1:N](create-edit-1n-relationships-solution-explorer.md#view-entity-relationships) выберите отношение со ссылкой на себя, которое следует изменить.
2. В разделе **Определение отношения** задайте в параметре **Иерархические** значение **Да**.  
  
> [!NOTE]
> - Некоторые готовые отношения (1:N) невозможно настроить. Это не позволит установить эти отношения как иерархические.  
> - Для системных отношений со ссылкой на себя можно задавать иерархическое отношение. К таким относятся отношения 1:N со ссылкой на себя системного типа, например, отношение «contact_master_contact».  

> [!IMPORTANT]
> Может иметься несколько отношений со ссылкой на себя, но только одно отношение в каждой сущности может быть определено как иерархическое. При попытке изменить параметр, после того как он уже применен, отображается предупреждение:
>
> - **При отключении:** Если отключить параметр иерархии для этого отношения, все определения сверток, процессы и представления, использующие эту иерархию, перестанут работать. Вы действительно хотите продолжить? 
> - **При включении:** Если включить параметр иерархии для этого отношения, все определения сверток, использующие существующую иерархию, станут недействительными. Вы действительно хотите продолжить?
>
> Если только вы не уверены, что нет других зависимостей в существующей иерархии, перед продолжением необходимо изучить всю документацию о развертывании или посовещаться с другими настройщиками, чтобы понять, как существующее иерархическое отношение используется.

<a name="BKMK_Querydata"></a> 
  
## <a name="query-hierarchical-data"></a>Запрос иерархических данных  

Без определенной иерархии для восстановления иерархических данных необходимо выполнить итеративный запрос связанных записей. С определенной иерархией можно запрашивать связанные данные в виде иерархии одним действием. Записи можно запросить с помощью логики **Менее** и **Не менее**. Иерархические операторы **Менее** и **Не менее** доступны при расширенном поиске и в редакторе бизнес-процесса. Дополнительные сведения о том, как использовать эти операторы, см. в разделе [Настройка шагов бизнес-процесса](/flow/configure-workflow-steps#setting-conditions-for-workflow-actions). Дополнительные сведения о расширенном поиске см. в разделе [Создание, изменение или сохранение расширенного поиска](https://docs.microsoft.com/dynamics365/customer-engagement/basics/save-advanced-find-search).  

> [!NOTE]
> Разработчики также смогут использовать данные операторы в коде. Дополнительные сведения см. в разделе [Документация для разработчиков: Запрос иерархических данных](/dynamics365/customer-engagement/developer/org-service/query-hierarchical-data).
  
В следующих примерах представлены сценарии для запроса иерархий.  
  
### <a name="query-account-hierarchy"></a>Запрос иерархии организации  
  
![Запрос организаций в иерархии организации](media/query-accounts.png)  
  
### <a name="query-account-hierarchy-including-related-activities"></a>Запрос иерархии организации, включая связанные действия  
  
![Запрос связанных действий организации](media/query-account-related-activities.png)  
  
###  <a name="query-account-hierarchy-including-related-opportunities"></a>Запрос иерархии организации, включая связанные возможные сделки  
  
![Запрос возможных сделок организации](media/query-account-related-opportunities.png)  
  
## <a name="see-also"></a>См. также 
[Создание и изменение отношений сущностей 1:N ("один-ко-многим") или N:1 ("многие-к-одному")](create-edit-1n-relationships.md)<br />
[Создание и изменение отношений сущностей 1:N (один-ко-многим) или N:1 (многие-к-одному) с помощью обозревателя решений](create-edit-1n-relationships-solution-explorer.md)<br />
[Визуализация иерархических данных с управляемыми моделью приложениями](visualize-hierarchical-data.md)<br />
[Видео: Моделирование иерархической безопасности](https://www.youtube.com/watch?v=kx5So32DrCo&index=10&list=PLC3591A8FE4ADBE07)<br />
[Видео: Визуализация иерархии](https://www.youtube.com/watch?v=_dGBE6icLNw&index=9&list=PLC3591A8FE4ADBE07)
