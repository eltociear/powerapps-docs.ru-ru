---
title: Обзор создания приложения на основе модели с помощью Power Apps | Документация Майкрософт
description: Пошаговые инструкции для создания и настройки сущности для использования с приложением Power Apps.
documentationcenter: na
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 02/12/2020
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d29ec6ca429efb4a7c221b888c77f01841542a18
ms.sourcegitcommit: 6cffa70358fd2e388d64a01f906c8c196fbbdefb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/17/2020
ms.locfileid: "3069818"
---
# <a name="what-are-model-driven-apps-in-power-apps"></a>Что такое приложения на основе модели в Power Apps?

Разработка управляемого моделью приложения — это основанный на компонентах подход к разработке приложений. Разработка управляемых моделью приложений не требует написания кода, а создаваемые приложения могут быть простыми или очень сложными.  В отличие от приложений на основе холста, где разработчик имеет полный контроль над макетом приложения, в управляемых моделью приложениях значительная часть макета уже определена и в основном задается компонентами, добавляемыми к приложению.

![Пример управляемого моделью приложения](media/model-driven-app-overview/model-app-sample.png)

Дизайн управляемых моделью приложений предоставляет следующие преимущества:
- Насыщенная среда разработки, сфокусированная на компоненты и не требующая написания кода 
- Создание отзывчивых сложных приложений с подобным интерфейсом пользователя для различных устройств от компьютера до мобильных устройств
- Возможность расширенной разработки 
- Ваше приложение можно распространять как решение
 
## <a name="the-approach-to-model-driven-app-making"></a>Подход к созданию управляемых моделью приложений
На базовом уровне управляемое моделью приложение состоит из трех основных областей.

- Моделирование бизнес-данных 
- Определение бизнес-процессов 
- Составление приложения

### <a name="modeling-business-data"></a>Моделирование бизнес-данных
Для моделирования бизнес-данных требуется определить, какие данные будут нужны приложению и как эти данные будут связаны с другими данными. В разработке под управлением модели используется основанная на метаданных архитектура, что позволяет разработчикам дорабатывать приложения без написания программного кода. Метаданные означают "данные о данных" и определяют структуру данных, хранящихся в системе. [Учебник. Создание настраиваемой сущности с компонентами в Power Apps](../common-data-service/create-custom-entity.md)

### <a name="defining-business-processes"></a>Определение бизнес-процессов
Определение и реализация последовательных бизнес-процессов является важным аспектом разработки управляемых моделью приложений. Последовательные процессы помогают гарантировать, что пользователи вашего приложения могут сосредоточиться на своей работе, а не на том, что им следует выполнить набор действий вручную. Процессы могут быть простыми или сложными и часто могут меняться со временем. Чтобы создать процесс на PowerApps.com в области "Управляемые моделью" выберите ![Параметры](media/powerapps-gear.png) > **Дополнительные настройки** > **Открыть обозреватель решений**. Далее в левой навигационной панели в обозревателе решений выберите **Процессы**, затем выберите **Создать**. Дополнительные сведения: [Обзор последовательностей операций бизнес-процессов](/flow/business-process-flows-overview) и [Применение бизнес-логики с Common Data Service](../common-data-service/cds-processes.md). 

### <a name="composing-the-model-driven-app"></a>Создание управляемого моделью приложения
После моделирования данных и определения процессов приложение строится путем выбора и настройки требуемых компонентов с помощью конструктора приложений.

![Конструктор приложений](media/model-driven-app-overview/app-designer.png)

## <a name="next-steps"></a>Дальнейшие действия

[Создание первого управляемого моделью приложения](build-first-model-driven-app.md)

[Общие сведения о компонентах управляемых моделью приложений](model-driven-app-components.md)

