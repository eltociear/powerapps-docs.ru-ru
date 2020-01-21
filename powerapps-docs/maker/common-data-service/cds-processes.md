---
title: Применение бизнес-логики в Common Data Service | MicrosoftDocs
description: Узнайте о различных типах бизнес-логики, которые можно применять в вашем приложении
ms.custom: ''
ms.date: 12/20/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: 0b4e6602-5701-4859-81cc-6f6fe50901b2
caps.latest.revision: 44
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9267f8385e19d3c0b87a36b495a4ff2b88b4d420
ms.sourcegitcommit: f70be39855e4931312fe0035525586a15ed4487b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2019
ms.locfileid: "2922384"
---
# <a name="apply-business-logic-in-common-data-service"></a>Применение бизнес-логики в Common Data Service
Существует несколько вариантов, доступных для применения бизнес-логики в Common Data Service. 

## <a name="business-rules"></a>Бизнес-правила
Вы можете создать бизнес-правила и рекомендации, чтобы применить логику и проверку без написания кода или создания подключаемых модулей. Бизнес-правила предоставляют простой интерфейс для реализации и поддержки быстро меняющихся, широко используемых бизнес-правил.

Определите *бизнес-правила* для сущности, которые применяются ко всем формам сущностей и на уровне сервера. Бизнес-правила, определенные для сущности, применяются к *приложениям на основе холста* и *управляемым моделью приложениям*, если сущность используется в приложении. Дополнительные сведения: [Создание бизнес-правила для сущности](data-platform-create-business-rule.md)

> [!NOTE]
> Чтобы определить бизнес-правило, применяемое к форме в управляемом моделью приложении, см. раздел [Создание бизнес-правил для формы управляемого моделью приложения](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md).

## <a name="power-automate"></a>Power Automate
Power Automate имеет несколько различных потоков, которые можно использовать для создания автоматизированных рабочих процессов в Common Data Service или между Common Data Service и другим приложением или сервисом, затем можно использовать для синхронизации файлов, получения уведомлений, сбора данных и многого другого. 


|Тип потока  |Описание  |Дополнительные сведения  |
|---------|---------|---------|
|Последовательности операций бизнес-процесса     | Определите последовательность шагов, выполняемых в приложении на основе модели Power Apps, которым должны следовать пользователи, чтобы получить желаемый результат.        | [Подробнее](/power-automate/create-business-process-flow)     |
|Автоматизированные потоки     |  Создание потока, который выполняет одну или несколько задач автоматически после запуска событием.    | [Подробнее](/power-automate/get-started-logic-flow)        |
|Потоки кнопки   | Запускайте повторяющиеся задачи из любого места и в любое время с помощью потокового приложения на мобильном устройстве.        | [Подробнее](/power-automate/introduction-to-button-flows)        |
|Запланированные потоки   | Создайте поток, который выполняет одну или несколько задач по расписанию.    | [Подробнее](/power-automate/run-scheduled-tasks)        |
|Потоки пользовательского интерфейса   | Запишите и автоматизируйте воспроизведение ручных шагов на устаревшем программном обеспечении.    | [Подробнее](/power-automate/ui-flows/overview)     |


## <a name="classic-common-data-service-processes"></a>Классические процессы Common Data Service
Можно также использовать классические процессы Common Data Service, которые являются бизнес-процессами и действиями. Дополнительные сведения: [Power Automate: использование бизнес-процессов](/flow/workflow-processes) и [Power Automate: обзор действий](/flow/actions).

### <a name="see-also"></a>См. также

[Применение бизнес-логики в управляемых моделью приложениях](../model-driven-apps/guide-staff-through-common-tasks-processes.md)
