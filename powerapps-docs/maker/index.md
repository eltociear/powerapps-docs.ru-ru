---
title: Общие сведения о создании приложений | Документы Майкрософт
description: Общие сведения о создании приложений в режиме холста или модели и включении службы Common Data Service
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.date: 03/18/2018
ms.author: anneta
ms.reviewer: ''
ms.openlocfilehash: c3e40df2d2ecc13e2c466aa91178ccb5d23548fe
ms.sourcegitcommit: 2300de0a0486187762f830068c872116d5b04c32
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49806095"
---
# <a name="overview-of-creating-apps-in-powerapps"></a>Общие сведения о создании приложений в PowerApps

PowerApps — это высокопроизводительная платформа разработки бизнес-приложений, состоящая из трех основных компонентов.

- [Приложения на основе холста](canvas-apps/getting-started.md). Отправной точкой является пользовательский интерфейс. На основе пустого холста можно создать интерфейс, подстроенный под потребности пользователей, и подключить его к более чем 200 источникам данных. Приложения на основе холста можно разрабатывать для браузеров, телефонов и планшетов.
- [Приложения на основе модели](model-driven-apps/model-driven-app-overview.md). Отправной точкой является модель данных. Вы начинаете с определения основных бизнес-данных и процессов в Common Data Service,а затем переходите к разработке форм, представлений и других компонентов модели. Для приложений на основе модели автоматически формируется отличный пользовательский интерфейс, который обеспечивает быструю работу на различных устройствах.
- [Common Data Service](common-data-service/data-platform-intro.md). Это платформа данных, которая поставляется с PowerApps и позволяет хранить и моделировать бизнес-данные. На этой платформе создаются приложения Dynamics 365. Если вы являетесь клиентом Dynamics, ваши данные уже хранятся в службе Common Data Service.

Создать первое приложение очень просто. Мы предлагаем 30-дневный пробный план и бесплатный план для участников сообщества. Решите, который из них лучше подходит вам, и приступайте к работе.

## <a name="canvas-apps"></a>Приложения на основе холста

Приложения на основе холста позволяют вам гибко компоновать пользовательский интерфейс в соответствии с потребностями. Внешний вид вашего приложения определяется вашим творческим взглядом и практической целесообразностью.

Начать создавать приложение можно на основе решений Майкрософт, в которых хранятся ваши данные, например:

- [на основе списка SharePoint;](canvas-apps/app-from-sharepoint.md#generate-an-app-from-within-sharepoint-online)
- [на основе информационной панели Power BI.](canvas-apps/embed-powerapps-powerbi.md)

Создать приложение на основе холста просто. С помощью PowerApps можно находить или создавать приложения несколькими способами:

- [на основе данных;](canvas-apps/app-from-sharepoint.md)
- [на основе образца;](canvas-apps/open-and-run-a-sample-app.md)
- [на основе источника Common Data Service;](canvas-apps/data-platform-create-app.md)
- [на основе пустого холста.](canvas-apps/data-platform-create-app-scratch.md)
- [посредством AppSource.](../user/app-source.md)

## <a name="model-driven-apps"></a>Приложения на основе модели

При создании приложения на основе модели можно использовать все возможности Common Data Service для быстрой настройки форм, бизнес-правил и последовательностей операций процессов. Приложение на основе модели создается на сайте PowerApps.

Приступить к работе с приложениями на основе модели просто. Начать можно со следующих статей.

- [Создание приложения](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-app)
- [Проектирование и создание форм](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-design-forms)
- [Создание и изменение представлений](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-views)
- [Создание и изменение системной диаграммы](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-system-chart)
- [Создание и изменение панелей мониторинга](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-dashboards)
- [Добавление функций безопасности](https://docs.microsoft.com/dynamics365/customer-engagement/customize/manage-access-apps-security-roles)
- [Добавление бизнес-логики](https://docs.microsoft.com/dynamics365/customer-engagement/customize/guide-staff-through-common-tasks-processes)

## <a name="common-data-service-for-apps"></a>Служба Common Data Service для приложений

Служба Common Data Service позволяет безопасно хранить данные и управлять ими с помощью набора стандартных и настраиваемых сущностей. Вы можете добавлять поля в эти сущности по мере необходимости.

Приступить к работе с Common Data Service просто. Например, можно начать со следующих задач.

- [Создание настраиваемой сущности](common-data-service/data-platform-create-entity.md)
- [Управление полями](common-data-service/data-platform-manage-fields.md)
- [Создание пользовательских наборов параметров](common-data-service/custom-picklists.md)
- [Создание бизнес-правила](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-business-rules-recommendations-apply-logic-form)

## <a name="canvas-and-model-driven-artifacts"></a>Артефакты на основе холста и модели

Несмотря на то, что мы объединили возможности работы с приложениями на основе холста и модели, эти артефакты будут применяться либо к одному, либо к другому типу приложений.

| Артефакт            | Тип приложения     |
|---------------------|--------------|
| Сущности > Представления      | На основе модели |
| Сущности > Формы      | На основе модели |
| Сущности > Панели мониторинга | На основе модели |
| Соединения         | На основе холста       |
| Шлюзы            | На основе холста       |
| Настраиваемые соединители   | На основе холста       |
| Приложения > Импорт       | На основе холста       |

Создав приложение, вы можете [предоставить доступ к нему](canvas-apps/share-app.md) участникам вашей команды.
