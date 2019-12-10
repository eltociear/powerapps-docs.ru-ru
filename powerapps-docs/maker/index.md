---
title: Общие сведения о создании приложений | Документы Майкрософт
description: Общие сведения о создании приложений в режиме холста или модели и включении службы Common Data Service
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.date: 12/05/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 79a1a5351bc3fe72a7558697e7cf8e8dfa079ce8
ms.sourcegitcommit: d194d2fa009ca7bfcbe95e5f31473832a130e0a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959410"
---
# <a name="overview-of-creating-apps-in-power-apps"></a>Общие сведения о создании приложений в PowerApps

Power Apps — это высокопроизводительная платформа для разработки бизнес-приложений, состоящая из четырех основных компонентов:

- [Приложения на основе холста](canvas-apps/getting-started.md). Отправной точкой является пользовательский интерфейс. На основе пустого холста можно создать интерфейс, подстроенный под потребности пользователей, и подключить его к более чем 200 источникам данных. Приложения на основе холста можно разрабатывать для браузеров, телефонов и планшетов.
- [Приложения на основе модели](model-driven-apps/model-driven-app-overview.md). Отправной точкой является модель данных. Вы начинаете с определения основных бизнес-данных и процессов в Common Data Service,а затем переходите к разработке форм, представлений и других компонентов модели. Для приложений на основе модели автоматически формируется отличный пользовательский интерфейс, который обеспечивает быструю работу на различных устройствах.
- [Порталы](portals/overview.md) начинают создавать внешние веб-сайты, которые позволяют пользователям за пределами организации входить в систему с использованием широкого спектра удостоверений, создавать и просматривать данные в Common Data Service и даже просматривать содержимое анонимно.
- [Common Data Service](common-data-service/data-platform-intro.md). Эта платформа данных поставляется с Power Apps. Она позволяет хранить и моделировать бизнес-данные. На этой платформе создаются приложения Dynamics 365. Если вы являетесь клиентом Dynamics, ваши данные уже хранятся в службе Common Data Service.

Создать первое приложение очень просто. Мы предлагаем 30-дневный пробный план и бесплатный план для участников сообщества. Решите, который из них лучше подходит вам, и приступайте к работе.

## <a name="canvas-apps"></a>Приложения на основе холста

Приложения на основе холста позволяют вам гибко компоновать пользовательский интерфейс в соответствии с потребностями. Внешний вид вашего приложения определяется вашим творческим взглядом и практической целесообразностью.

Начать создавать приложение можно на основе решений Майкрософт, в которых хранятся ваши данные, например:

- [на основе списка SharePoint;](canvas-apps/app-from-sharepoint.md#create-an-app-from-within-sharepoint-online)
- [на основе информационной панели Power BI.](canvas-apps/embed-powerapps-powerbi.md)

Создать приложение на основе холста просто. С помощью Power Apps можно находить или создавать приложения несколькими способами:

- [на основе данных;](canvas-apps/app-from-sharepoint.md)
- [на основе образца;](canvas-apps/open-and-run-a-sample-app.md)
- [на основе источника Common Data Service;](canvas-apps/data-platform-create-app.md)
- [на основе пустого холста.](canvas-apps/data-platform-create-app-scratch.md)
- [посредством AppSource.](../user/app-source.md)

## <a name="model-driven-apps"></a>Приложения на основе модели

При создании приложения на основе модели можно использовать все возможности Common Data Service для быстрой настройки форм, бизнес-правил и потоков процессов. Приложение на основе модели создается на сайте Power Apps.

Приступить к работе с приложениями на основе модели просто. Начать можно со следующих статей.

- [Создание приложения](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-app)
- [Проектирование и создание форм](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-design-forms)
- [Создание и изменение представлений](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-views)
- [Создание и изменение системной диаграммы](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-system-chart)
- [Создание и изменение панелей мониторинга](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-dashboards)
- [Добавление функций безопасности](https://docs.microsoft.com/dynamics365/customer-engagement/customize/manage-access-apps-security-roles)
- [Добавление бизнес-логики](https://docs.microsoft.com/dynamics365/customer-engagement/customize/guide-staff-through-common-tasks-processes)

## <a name="common-data-service"></a>Common Data Service

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
