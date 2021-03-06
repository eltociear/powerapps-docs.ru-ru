---
title: Что такое Common Data Service? | Microsoft Docs
description: Введение в Common Data Service, сущности, серверная логика, безопасность и возможности разработчиков.
author: clwesene
manager: kvivek
ms.service: powerapps
ms.topic: overview
ms.component: cds
ms.date: 06/21/2019
ms.reviewer: matp
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bbc56604668a82582092ed305876618651118403
ms.sourcegitcommit: 3066c2800a939fbcaaac4262c802843e2d80b88c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2020
ms.locfileid: "3134134"
---
# <a name="what-is-common-data-service"></a>Что такое Common Data Service?
Common Data Service позволяет безопасно хранить используемые бизнес-приложениями данные и управлять ими. Данные в Common Data Service хранятся в наборе сущностей. *Сущность* — это набор записей, используемый для хранения данных, аналогично тому, как в таблице хранятся данные внутри базы данных. Common Data Service включает базовый набор стандартных сущностей, которые охватывают типичные ситуации, но можно также создавать пользовательские сущности, относящиеся к организации, и заполнять их с данными с помощью Power Query. Создатели приложения затем могут использовать Power Apps для построения богатых приложений, используя эти данные.

![Снимок экрана с обзором Power Platform](./media/data-platform-cds-intro/platform.png "Common Data Service в Power Platform")

Для получения сведений о покупке плана для использования Common Data Service см. раздел [Сведения о ценах](../../administrator/pricing-billing-skus.md).

## <a name="why-use-common-data-service"></a>Зачем использовать Common Data Service?
Стандартные и настраиваемые сущности в Common Data Service обеспечивают возможность безопасного облачного хранения ваших данных. Сущности позволяют создавать бизнес-ориентированное определение данных вашей организации для использования в приложениях. Если вы точно не знаете, являются ли сущности оптимальным вариантом, рассмотрите их преимущества:

* **Простота управления** &ndash; метаданные и данные хранятся в облаке. Нет необходимости беспокоиться о деталях их хранения.
* **Простота обеспечения безопасности** &ndash; данные безопасно хранятся таким образом, чтобы пользователи могли видеть их, только если вы предоставили им доступ. Основанная на ролях система безопасности позволяет управлять доступом к сущностям для разных пользователей внутри организации.
* **Доступ к вашим данным Dynamics 365** &ndash; данные из ваших приложений Dynamics 365 также сохраняются в Common Data Service, позволяя вам быстро создавать приложения, используются данные Dynamics 365 и расширять ваши приложений с помощью Power Apps.
* **Богатые метаданные** &ndash; типы данных и отношений используются напрямую с Power Apps.
* **Логика и проверка** &ndash; определяйте вычисляемые поля, бизнес-правила, бизнес-процессы и последовательности операций бизнес-процессов для обеспечения качества данных и управления бизнес-процессами.
* **Средства обеспечения производительности** &ndash; сущности доступны с надстройками для Microsoft Excel для увеличения производительности и обеспечения доступа к данным.

## <a name="dynamics-365-and-common-data-service"></a>Dynamics 365 и Common Data Service

Приложения Dynamics 365, такие как Dynamics 365 Sales, Dynamics 365 Customer Service или Dynamics 365 Talent, также используют Common Data Service для хранения и обеспечении безопасности данных, используемых приложениями. Это позволяет создавать приложения с помощью Power Apps и Common Data Service непосредственно из ваших основных бизнес-данных, уже используемых в Dynamics 365, без необходимости интеграции.

* **Создание приложений, работающих с данными Dynamics 365** &ndash; быстро создавайте приложения, использующие ваши бизнес-данные, внутри Power Apps или с помощью пакета SDK для разработчиков Pro Developer.
* **Управление многоразовой бизнес-логикой и бизнес-правилами** &ndash; бизнес-правила и логика, уже определенные в ваших сущностях Dynamics 365, применяются к Power Apps для обеспечения согласованности данных независимо от того, как ваши пользователи получают доступ к данным или через какое приложение.
* **Многократно используемых навыки в Dynamics 365 и PowerAppsPower Apps** &ndash; пользователи с имеющимися навыками в Power Apps или Dynamics 365 могут теперь использовать эти навыки во всей новой платформе Common Data Service. Создание сущностей, форм, диаграмм и т. п. теперь общее во всех ваших приложениях.

    > [!NOTE]
    > Для приложений Finance and Operations в настоящее время требуется конфигурации [интегратора данных](/power-platform/admin/data-integrator), чтобы ваши бизнес-данные из приложений Finance and Operations были доступны в Common Data Service.

## <a name="integrating-data-into-the-common-data-service"></a>Интеграция данных в Common Data Service

Построение приложения обычно включает данные из более чем одного источника; хотя это иногда можно сделать на уровне приложения, существуют также случаи, когда интеграция этих данных вместе в общее хранилище позволяет упростить создание приложения, а также обеспечивает один набор логики для поддержки данных и управления ими. Common Data Service позволяет интегрировать данные из нескольких источников в одно хранилище, которое можно затем использовать в Power Apps, Power Automate, Power BI и Power Virtual Agents вместе с данными, уже доступными из приложений Dynamics 365.

* **Плановая интеграция с другими системами** &ndash; данные из другого приложения можно регулярно синхронизировать с Common Data Service, чтобы предоставить возможность использовать данные других приложений в Power Apps.
* **Преобразование и импорт данных с использованием PowerQuery** &ndash; преобразование данных при импорте в Common Data Service можно выполнять через PowerQuery из многих источников данных в сети, это общее средство, которое используется с Excel и Power BI.
* **Единовременный импорт данных** &ndash; простой импорт и экспорт файлов Excel и CSV можно использовать для однократного или нечастого импорта данных в Common Data Service.

Дополнительные сведения о интеграции данных в Common Data Service см. в разделе [Добавление данных в сущность в Common Data Service с помощью Power Query](data-platform-cds-newentity-pq.md).

## <a name="interacting-with-entities"></a>Взаимодействие с сущностями
При разработке приложения можно использовать стандартные сущности, настраиваемые сущности или оба варианта. Common Data Service предоставляет стандартные сущности по умолчанию. Они разработаны в соответствии с наилучшими практиками для реализации самых распространенных концепций и сценариев в организации.

![Снимок экрана со списком сущностей](./media/data-platform-cds-intro/entitylist.png "Список сущностей")

Полный список сущностей см. в разделе [Справочник по сущностям](https://docs.microsoft.com/powerapps/developer/common-data-service/reference/about-entity-reference).

Можно расширить функциональность стандартных сущностей, создав одну или нескольких настраиваемых сущностей для хранения информации, которая уникальна для организации. Дополнительные сведения см. в статье [Как создать настраиваемую сущность](create-custom-entity.md).

## <a name="logic-and-validation"></a>Логика и проверка
Сущности в Common Data Service могут использовать развитую логику на стороне сервера для обеспечения качества данных и снижения повторного кодирования в каждом приложении, которое создает и использует данные в сущности.

* **Бизнес-правила** проверяют данные в нескольких полях и сущностях и обеспечивают предупреждения и сообщения об ошибках, вне зависимости от приложения, используемого для создания данных. Чтобы получить дополнительные сведения, см. раздел [Создание бизнес-правила](./data-platform-create-business-rule.md).
* **Последовательности операций бизнес-процесса** помогают пользователям для обеспечения согласованного ввода данных и выполнения одних и тех же действий каждый раз. Последовательности операций бизнес-процесса в настоящее время поддерживаются только для приложений, управляемых моделью. Дополнительные сведения см. в разделе [Обзор последовательности операций бизнес-процесса](/dynamics365/customer-engagement/customize/business-process-flows-overview)
* **Бизнес-процессы** позволяют автоматизировать бизнес-процессы без вмешательства пользователей. Дополнительные сведения см. в разделе [Обзор бизнес-процессов](/dynamics365/customer-engagement/customize/workflow-processes).
* **Бизнес-логика с кодом** поддерживает сложные сценарии разработчика, чтобы расширить приложение непосредственно с помощью кода. Чтобы получить дополнительные сведения, см. раздел [Применение бизнес-логики с помощью кода](../../developer/common-data-service/apply-business-logic-with-code.md).

## <a name="security"></a>Безопасность
Common Data Service имеет богатую модель безопасности для защиты целостности данных и конфиденциальности пользователей, а также поддержки эффективного доступа к данным и совместной работы. Возможно объединение подразделений, безопасности ролей, безопасности на базе записей и безопасности на базе полей с целью определения общего доступа к информации для пользователей в среде Common Data Service. Дополнительные сведения: [Роли безопасности в Common Data Service](/power-platform/admin/wp-security). 

## <a name="developer-capabilities"></a>Возможности разработчика
В дополнение к функциям, доступным через портал [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), Common Data Service также включает функции для разработчиков для программного доступа к метаданным и данным для создания сущностей и бизнес-логики, а также для взаимодействия с данными. Дополнительные сведения см. в разделе [Обзор Common Data Service для разработчиков](../../developer/common-data-service/overview.md).

## <a name="next-steps"></a>Дальнейшие шаги
Чтобы начать использовать Common Data Service:
- [Создайте приложение на основе холста с использованием базы данных Common Data Service](../canvas-apps/data-platform-create-app-scratch.md).
- [Создайте настраиваемую сущность](create-custom-entity.md), затем [создайте приложение на основе холста, которое использует эту сущность](../canvas-apps/data-platform-create-app.md).
- [Создайте управляемое моделью приложение](/powerapps/maker/model-driven-apps/build-first-model-driven-app) на основе Common Data Service.
- [Используйте Power Query](./data-platform-cds-newentity-pq.md) для подключения с сетевому или локальному источнику данных и импорта данных непосредственно в Common Data Service.

## <a name="privacy-notice"></a>Уведомление о конфиденциальности
С общей моделью данных Microsoft Power Apps Майкрософт выполняет сбор и сохраняет имена настраиваемых сущностей и полей в наших диагностических системах. Мы используем это знания, чтобы улучшить общую модель данных для наших клиентов. Имена сущностей и полей, которые создают создатели приложений, помогают нам понять сценарии, часто встречающиеся в сообществе Microsoft Power Apps и заполнить пробелы в охвате стандартных сущностей сервиса, например схемы, связанные с организациями. Данных в таблицах базы данных, связанные с этими сущностями, не получаются и не используются корпорацией Майкрософт и не дублируются за пределами региона, в которой эта база данных подготовлена. Однако обратите внимание, что имена настраиваемых сущностей и полей могут реплицироваться между регионами и удаляются в соответствии с нашими политиками хранения данных. Майкрософт считает своим долгом сохранять вашу конфиденциальность, как полнее описано в нашем [Центре управления безопасностью](https://www.microsoft.com/trustcenter/Privacy/default.aspx).
