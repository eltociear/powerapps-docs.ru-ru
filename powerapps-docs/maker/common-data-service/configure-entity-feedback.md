---
title: Настройка сущности для отзыва с помощью Power Apps | MicrosoftDocs
description: Узнайте, как включить отзыв для сущности
ms.custom: ''
ms.date: 05/18/2018
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
ms.assetid: 5b25cf09-d43b-4165-9eaa-7549f4855e7c
caps.latest.revision: 13
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0ccf81df57754d6b111e3769d45d8398a9907eb2
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861662"
---
# <a name="configure-an-entity-for-feedbackratings"></a>Настройка сущности для отзывов/оценок

Включив поддержку отзывов для сущности, вы предоставите клиентам или сотрудникам возможность оставлять отзывы о любой записи сущности или оценивать записи сущности в пределах заданного диапазона оценок.  

Эта возможность часто используется в системе, которая собирает данные от клиентов через портал или опрос. Данные об удовлетворенности сервисом или продуктом можно применить в сущностях, представляющих этот тип данных.

Отзыв также может использоваться сотрудниками для предоставления отзывов по совместным усилиям.

> [!NOTE]
> Вам потребуется роль безопасности "Системный администратор", "Настройщик системы" или эквивалентные разрешения для выполнения этих шагов.
  
## <a name="enable-feedback"></a>Включение поддержки отзывов  
  
Измените сущность, чтобы включить **Отзывы**. Дополнительные сведения: [Изменение сущности](edit-entities.md)
  
## <a name="add-a-subgrid-for-feedback-on-the-entity-form"></a>Добавление вложенной сетки для отзыва в форму сущности  

По умолчанию, чтобы добавить отзыв о записи, пользователи должны перейти к списку связанных записей для этой записи. Чтобы пользователям было удобнее добавлять отзывы, рекомендуем добавить вложенную сетку отзыва в форму сущности, для которой вы включаете поддержку отзывов.  

<!-- This is the closest I could find to a topic about adding an subgrid to a form. -->
Дополнительные сведения: [Обзор свойств вложенной сетки](../model-driven-apps/sub-grid-properties-legacy.md)

## <a name="add-a-rollup-field--to-the-entity-form-to-show-the-ratings"></a>Добавление поля свертки в форму сущности для отображения оценок  

В зависимости от желаемого способа вычисления оценки для сущности можно создать поле свертки, вычисляющее оценку, и затем добавить его в форму сущности, для которой вы включаете поддержку отзывов. Дополнительные сведения: [Определение полей свертки, которые агрегируют значения](define-rollup-fields.md)
  
### <a name="see-also"></a>См. также  
 [Отправить отзыв или оценки для записей Dynamics 365](/dynamics365/customer-engagement/basics/submit-feedback-ratings)
