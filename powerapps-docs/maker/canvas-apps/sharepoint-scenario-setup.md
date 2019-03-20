---
title: Настройка списков для интеграции SharePoint Online с PowerApps, Microsoft Flow и Power BI | Документация Майкрософт
description: В этом примере мы настроим списки SharePoint, чтобы использовать их в качестве источника данных для приложений, потоков, отчетов и панелей мониторинга.
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 12/19/2017
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7be4a0574c1a81684188eaede4b6e80b02e7b7cc
ms.sourcegitcommit: 90245baddce9d92c3ce85b0537c1ac1cf26bf55a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2019
ms.locfileid: "57799187"
---
# <a name="set-up-lists-for-sharepoint-online-integration-with-powerapps-microsoft-flow-and-power-bi"></a>Настройка списков для интеграции SharePoint Online с PowerApps, Microsoft Flow и Power BI
> [!NOTE]
> Эта статья входит в серию руководств по использованию PowerApps, Microsoft Flow и Power BI совместно с SharePoint Online. Обязательно просмотрите [вводные сведения](sharepoint-scenario-intro.md), чтобы получить общее представление о процессе и скачать связанные файлы.

В SharePoint доступно много возможностей для совместной работы, но мы сосредоточимся на одной из них для этого сценария: [Списки SharePoint](https://support.office.com/article/Introduction-to-lists-0A1C3ACE-DEF0-44AF-B225-CFA8D92C52D7). Список — это коллекция данных с возможностью совместного использования с участниками группы и другими пользователями сайта. Сначала мы рассмотрим возможности списков, используемых в этом сценарии, а затем создадим их на сайте SharePoint Online.

## <a name="step-1-understand-the-lists"></a>Шаг 1. Понять списки
Первый список — **Project Requests** (Запросы проекта), в который пользователь, запрашивающий проекты, добавляет запрос. Пользователь, утверждающий проекты, просматривает запрос, а затем утверждает или отклоняет его.

| **Столбец в списке** | **Тип данных** | **Примечания** |
| --- | --- | --- |
| Title |Однострочный текст |Столбец по умолчанию, используемый для имени проекта. |
| Description |Однострочный текст | |
| ProjectType |Однострочный текст |Значения: новое оборудование, обновленное оборудование, новое программное обеспечение, обновленное программное обеспечение. |
| RequestDate |Date | |
| Requestor |Однострочный текст | |
| EstimatedDays |Номер |Позволяет сравнить результаты оценки запрашивающего с результатами руководителя проекта и фактическими результатами. |
| Approved |Однострочный текст |Значения: в ожидании, да, нет. |

> [!NOTE]
> Также мы используем скрытый по умолчанию столбец **ID**, который автоматически создается в SharePoint. Для простоты мы будем использовать базовые типы данных. Но в реальных приложениях могут использоваться более сложные типы, например **пользователь или группа** для столбца **Requestor**. Сведения о типах данных, поддерживаемых в PowerApps, см. в статье [Подключение Microsoft PowerApps к SharePoint](connections/connection-sharepoint-online.md#known-issues).

Второй список — **Project Details** (Сведения о проекте), в котором отслеживаются сведения обо всех утвержденных проектах (например, о назначенном руководителе проекта).

| **Столбец в списке** | **Тип данных** | **Примечания** |
| --- | --- | --- |
| Title |Однострочный текст |Столбец по умолчанию, используемый для имени проекта. |
| RequestID |Номер |Совпадает со значением в столбце **ID** списка **Project Requests**. |
| ApprovedDate |Date | |
| Состояние |Однострочный текст |Значения: не начато, выполняется, завершено. |
| ProjectedStartDate |Date |Рассчитанная руководителем дата начала проекта. |
| ProjectedEndDate |Дата |Рассчитанная руководителем дата завершения проекта. |
| ProjectedDays |Номер |Рабочие дни; как правило, вычисляются, но не в нашем примере. |
| ActualDays |Номер |Для завершенных проектов. |
| PMAssigned |Однострочный текст |Руководитель проекта. |

## <a name="step-2-create-and-review-the-lists"></a>Шаг 2. Создание и просмотр списков
Для работы с этим примером нам нужно создать два списка SharePoint и заполнить их примерами данных. Мы покажем, как это сделать, создав список и вставив примеры данных. Убедитесь, что у вас есть файлы Excel из [скачиваемого пакета](https://aka.ms/o4ia0f).

> [!NOTE]
> На этом этапе используйте Internet Explorer.

### <a name="create-the-lists"></a>Создание списка

1. В Internet Explorer на сайте SharePoint нажмите кнопку **Создать**, а затем щелкните **Список**.
   
    ![Создание списка SharePoint](./media/sharepoint-scenario-setup/01-01-01-new-list.png)

2. Введите имя "Project Requests" и нажмите кнопку **Создать**.
   
    ![Выбор имени для нового списка](./media/sharepoint-scenario-setup/01-01-02-create-list.png)
   
    Список **Project Requests** создан со столбцом **Title** по умолчанию.
   
    ![Список "Project Requests"](./media/sharepoint-scenario-setup/01-01-03-initial-list.png)

### <a name="add-columns-to-the-list"></a>Добавление столбцов в список

1. Щелкните ![Значок создания элемента](./media/sharepoint-scenario-setup/icon-new.png) и выберите **Single line of text** (Однострочный текст).
   
    ![Поле однострочного текста](./media/sharepoint-scenario-setup/01-01-04-add-column.png)

2. Введите имя "Description" и нажмите **Сохранить**.
   
3. Повторите шаги **1** и **2** для других столбцов в списке:
   
   1. **Single line of text** (Однострочный текст) > "ProjectType"
   2. **Date** (Дата) > "RequestDate"
   3. **Single line of text** (Однострочный текст) > "Requestor"
   4. **Number** (Число) > "EstimatedDays"
   5. **Single line of text** (Однострочный текст) > "Approved"

### <a name="copy-data-into-the-list"></a>Копирование данных в список
1. Нажмите кнопку **Быстрое редактирование**.
   
    ![Быстрое редактирование списка](./media/sharepoint-scenario-setup/01-01-06-quick-edit.png)
2. Выделите ячейки в сетке.
   
    ![Список со всеми столбцами](./media/sharepoint-scenario-setup/01-01-07-empty-grid.png)
3. Откройте книгу project-requests.xlsx и выделите все данные (без заголовков).
   
    ![Таблица Excel списка "Project Requests"](./media/sharepoint-scenario-setup/01-01-08-excel-table.png)
4. Скопируйте данные, вставьте их в сетку в SharePoint и нажмите кнопку **Готово**.
   
    ![Список, заполненный данными](./media/sharepoint-scenario-setup/01-01-09-full-grid.png)
5. Повторите создание и копирование для списка "Project Details", используя книгу project-details.xlsx. См. в таблице Project Details в [шаг 1: Понять списки](#step-1-understand-the-lists) для столбцов имена и типы данных.

## <a name="step-3-update-connections-to-samples---optional"></a>Шаг 3. Обновление подключения к примерам (необязательно)
Как отмечено во введении, мы включили в [скачиваемый пакет](https://aka.ms/o4ia0f) два примера приложений и пример отчета. Это руководство можно пройти и без этих примеров. Но если вы решили их использовать, вам нужно обновить подключения к спискам SharePoint. Так примеры приложений смогут использовать как источник данных *ваши* списки вместо наших.

### <a name="update-connections-for-the-sample-apps"></a>Обновление подключения для примеров приложений

1. В [PowerApps Studio](https://create.powerapps.com/studio/) нажмите **Открыть** в области слева. 

2. Выберите **Обзор**, затем откройте скачанный ранее файл **project-management-app.msapp**.

3. Щелкните **Allow** (Разрешить), чтобы служба PowerApps могла использовать SharePoint.

4. На ленте откройте вкладку **View** (Представление) и щелкните **Data sources** (Источники данных).

    ![Источники данных в PowerApps](./media/sharepoint-scenario-setup/01-03-01-data-sources.png)
5. На панели **Данные** нажмите символ многоточия (**...**) рядом с элементом **Сведения о проекте**, а затем выберите **Удалить**.
   
    ![Удаление источника данных "Project Details"](./media/sharepoint-scenario-setup/01-03-02-remove.png)
6. Выберите **Добавить источник данных**.
   
    ![Добавление источника данных](./media/sharepoint-scenario-setup/01-03-03-add.png)

7. Есть два способа подключиться к списку. Выбор способа зависит от того, установлено ли подключение PowerApps к SharePoint. 

    * Если подключение SharePoint уже отображается, выберите его.

        ![Существующее подключение](./media/sharepoint-scenario-setup/01-03-03aa-existing-connection.png)

    * Если подключения SharePoint здесь нет, выберите **Новое подключение**.

        ![Создание подключения](./media/sharepoint-scenario-setup/01-03-03a-new-connection.png)

        Затем выберите **SharePoint** и нажмите **Создать**.
   
        ![Подключение к SharePoint](./media/sharepoint-scenario-setup/01-03-03b-sharepoint.png)

8. Введите URL-адрес сайта SharePoint Online, который содержит созданные списки, и нажмите кнопку **Go** (Перейти).
   
    ![URL-адрес сайта SharePoint](./media/sharepoint-scenario-setup/01-03-03c-sharepoint-url.png)
9. Выберите список **Project Details** (Сведения о проекте), а затем нажмите кнопку **Connect** (Подключить).
   
    ![Список "Project Details" (Сведения о проекте)](./media/sharepoint-scenario-setup/01-03-03d-project-details.png)
   
    Теперь на панели **Данные** появится созданное подключение.
   
    ![Источники данных](./media/sharepoint-scenario-setup/01-03-03e-data-sources.png)

10. Нажмите значок многоточия (**...**) рядом с элементом **Сведения о проекте**, а затем выберите **Обновить**.
    
    ![Обновление источника данных "Project Details"](./media/sharepoint-scenario-setup/01-03-02-remove.png)

11. В правом верхнем углу щелкните ![Значок запуска приложения](./media/sharepoint-scenario-setup/icon-run-arrow.png) для запуска приложения. Убедитесь, что подключение работает правильно.

12. Щелкните меню **Файл** или коснитесь его и сохраните приложение в облаке. 

12. Повторите шаги в этом разделе с файлом **project-requests-app.msapp**, используя список **Project Requests** (Запросы проекта).

### <a name="update-connections-for-the-sample-report"></a>Обновление подключений для примера отчета
1. Откройте файл **project-analysis.pbix** в Power BI Desktop.

2. На ленте откройте вкладку **Главная**, щелкните **Изменить запросы** и выберите **Параметры источника данных**.
   
    ![Элемент "Изменить запросы"](./media/sharepoint-scenario-setup/01-03-04-edit-queries.png)

3. Нажмите кнопку **Изменить источник**.
   
    ![Окно "Параметры источника данных"](./media/sharepoint-scenario-setup/01-03-05-settings.png)

4. Введите URL-адрес сайта SharePoint Online и нажмите **ОК**, затем выберите **Закрыть**.
   
    ![URL-адрес списка SharePoint](./media/sharepoint-scenario-setup/01-03-06-list-url.png)

5. В Power BI Desktop под лентой отобразится баннер, который позволяет применить изменения и перенести данные из нового источника. Нажмите кнопку **Применить изменения**.
   
    ![Применение изменений запроса](./media/sharepoint-scenario-setup/01-03-07-apply.png)

6. Войдите с корпоративной учетной записью (с которой вы входите в SharePoint Online) и выберите **Подключить**.
   
    ![Подключение к SharePoint Online](./media/sharepoint-scenario-setup/01-03-08-connect.png)

## <a name="next-steps"></a>Дальнейшие действия
Следующий этап в этой серии руководств — [создание приложения для обработки запросов проекта](sharepoint-scenario-generate-app.md).

