---
title: 'Ограниченные сущности, требующие лицензии Dynamics 365 | Microsoft Docs'
description: 'Список ограниченных сущностей в Common Data Service, которым требуются лицензии Dynamics 365.'
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: reference
ms.date: 05/01/2018
ms.author: lanced
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="restricted-entities-requiring-dynamics-365-licenses"></a>Ограниченные сущности, требующие лицензии Dynamics 365
Создатели приложений могут использовать большую часть сущностей, доступных в Common Data Service, для создания приложений и потоков для пользователей, имеющих только лицензию PowerApps, план 1. Однако некоторые сущности содержат сложную бизнес-логику, которая требует, чтобы пользователи приложения имели лицензию PowerApps, план 2, или Microsoft Flow, план 2 (чтобы получить дополнительные сведения, см. раздел [Требования к лицензии сущности](data-platform-entity-licenses.md)). Даже еще меньший набор сущностей, связанных с продуктами Dynamics 365, требует, чтобы у пользователей приложений на основе хоста или управляемых моделью, имелась лицензия для соответствующего продукта Dynamics 365, если им необходимо создавать, обновлять или удалять записи в сущности. Они называются *ограниченными* сущностями.

Сущности могут быть ограничены до лицензии Dynamics 365 по следующим причинам:

* Сущность используется для хранения и ведения данных конфигурации конкретного продукта, которые обычно не используются вне этого приложения.
* Сущность сопровождается расширенной логикой, которая создает и ведет данные определенным способом при использовании в продукте Dynamics 365.

Если приложение или поток только считывают данные из сущности, лицензия на Dynamics 365 не требуется, и соответствующая лицензия на PowerApps или Microsoft Flow — это все, что требуется. 

## <a name="restricted-entities-for-create-update-and-delete-operations"></a>Ограниченные сущности для операций создания, обновления и удаления
В таблице перечислено ограниченные сущности и связанные требования лицензирования Dynamics 365 для пользователей PowerApps и Microsoft Flow, которые создают, обновляют или удаляют данные, хранящиеся в сущностях. 

|Сущность  |Логическое имя  |Требуется лицензия  |
|---------|---------|---------|
Фактические |msdyn_actual |Dynamics 365 for Field Service <br> **или** Dynamics 365 for Project Service Automation<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Бизнес-процесс соглашения |msdyn_bpf_baa0a411a239410cb8bded8b5fdd88e3 |Dynamics 365 for Field Service<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Журнал резервирования | msdyn_bookingjournal|Dynamics 365 for Field Service<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Метаданные настройки резервирования | msdyn_bookingsetupmetadata|Dynamics 365 for Field Service <br> **или** Dynamics 365 for Project Service Automation<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Отметка времени резервирования | msdyn_bookingtimestamp|Dynamics 365 for Field Service<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Обращение | инцидент | Dynamics 365 for Customer Service, Enterprise edition <br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Бизнес-процесс преобразования обращения в заказ на работу |msdyn_bpf_989e9b1857e24af18787d5143b67523b |Dynamics 365 for Field Service<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Настройка |msdyn_configuration |Dynamics 365 for Field Service <br> **или** Dynamics 365 for Project Service Automation<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Объем обслуживания | объем обслуживания | Dynamics 365 for Customer Service, Enterprise edition <br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Строка оценки|msdyn_estimateline|Dynamics 365 for Project Service Automation<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Оценка|msdyn_estimate |Dynamics 365 for Project Service Automation<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Факт|msdyn_fact |Dynamics 365 for Project Service Automation<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Настройка Field Service |msdyn_fieldservicesetting |Dynamics 365 for Field Service<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Системное задание Field Service |msdyn_fieldservicesystemjob |Dynamics 365 for Field Service<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Цель | goal | Dynamics 365 for Sales Professional, <br>**или** Dynamics 365 for Sales, Enterprise edition, <br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Журнал запасов |msdyn_inventoryjournal |Dynamics 365 for Field Service<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Процесс обработки счета |msdyn_bpf_d8f9dc7f099f44db9d641dd81fbd470d |Dynamics 365 for Project Service Automation<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Цикл взаимодействия | journey | Dynamics 365 for Marketing <br> **или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Статья базы знаний | knowledgearticle | Dynamics 365 for Customer Service, Enterprise edition <br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Подразделение |msdyn_organizationalunit |Dynamics 365 for Field Service <br> **или** Dynamics 365 for Project Service Automation<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Запасы продукта |msdyn_productinventory |Dynamics 365 for Field Service<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Параметр проекта|msdyn_projectparameter |Dynamics 365 for Project Service Automation<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Стадии проекта| msdyn_bpf_665e73aa18c247d886bfc50499c73b82|Dynamics 365 for Project Service Automation<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Зависимость задач проекта|msdyn_projecttaskdependency |Dynamics 365 for Project Service Automation<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Задача проекта|msdyn_projecttask |Dynamics 365 for Project Service Automation<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Участник проектной группы|msdyn_projecteam |Dynamics 365 for Project Service Automation<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Бизнес-процесс заказа на покупку | msdyn_bpf_2c5fe86acc8b414b8322ae571000c799|Dynamics 365 for Field Service<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Сведения о назначении ресурса (устарело)|msdyn_resourceassignmentdetail |Dynamics 365 for Project Service Automation<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Назначение ресурса|msdyn_resourceassignment |Dynamics 365 for Project Service Automation<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Ограничение ресурса (устарело) |msdyn_workorderresourcerestriction | Dynamics 365 for Field Service<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Набор правил маршрутизации | routingrule | Dynamics 365 for Customer Service, Enterprise edition <br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Настройка таблицы расписаний |msdyn_scheduleboardsetting |Dynamics 365 for Field Service <br> **или** Dynamics 365 for Project Service Automation<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Параметр планирования |msdyn_schedulingparameter |Dynamics 365 for Field Service <br> **или** Dynamics 365 for Project Service Automation<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Соглашение об уровне обслуживания| sla | Dynamics 365 for Customer Service, Enterprise edition <br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Параметр планировщика системного пользователя |msdyn_systemuserschedulersetting|Dynamics 365 for Field Service <br> **или** Dynamics 365 for Project Service Automation<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Подключение проводки|msdyn_transactionconnection |Dynamics 365 for Project Service Automation<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Происхождение проводки|msdyn_transactionorigin |Dynamics 365 for Project Service Automation<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Тип проводки|msdyn_transactiontype |Dynamics 365 for Project Service Automation<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Уникальный номер|msdyn_uniquenumber |Dynamics 365 for Field Service<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Бизнес-процесс заказа на работу |msdyn_bpf_d3d97bac8c294105840e99e37a9d1c39 |Dynamics 365 for Field Service<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365
Очередь создания сведений заказа на работу (устарело)|msdyn_workorderdetailsgenerationqueue |Dynamics 365 for Field Service<br>**или** план Dynamics 365 Customer Engagement <br> **или** план Dynamics 365

## <a name="licensing"></a>Лицензирование
Дополнительные сведения о лицензиях PowerApps и Dynamics 365 см. на странице [Обзор лицензирования](../../administrator/pricing-billing-skus.md).

