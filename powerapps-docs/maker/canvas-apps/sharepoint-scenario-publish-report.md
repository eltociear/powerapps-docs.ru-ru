---
title: Публикация отчета о проекте Power BI и создание панели мониторинга | Документация Майкрософт
description: В этом руководстве мы опубликуем набор данных и отчет в службе Power BI, а также создадим панель мониторинга на основе отчета.
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/30/2018
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 43e95b88cdf305e7c4b768def83a6b41fa0fcae7
ms.sourcegitcommit: 90245baddce9d92c3ce85b0537c1ac1cf26bf55a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2019
ms.locfileid: "57799371"
---
# <a name="publish-the-power-bi-project-report-and-create-a-dashboard"></a>Публикация отчета о проекте и создание панели мониторинга в Power BI
> [!NOTE]
> Эта статья входит в серию руководств по использованию PowerApps, Microsoft Flow и Power BI совместно с SharePoint Online. Обязательно просмотрите [вводные сведения](sharepoint-scenario-intro.md), чтобы получить общее представление о процессе и скачать связанные файлы.

В этом руководстве мы опубликуем набор данных и отчет в службе Power BI, а также создадим панель мониторинга на основе отчета. В большинстве случаев отчет включает множество визуализаций, из которых только часть используется на панели мониторинга. В этом примере мы добавим на панель мониторинга четыре визуализации.

## <a name="step-1-publish-the-dataset-and-report"></a>Шаг 1. Публикация набора данных и отчета
1. В Power BI Desktop на вкладке **Главная** щелкните **Опубликовать**.
   
    ![Публикация набора данных и отчета](./media/sharepoint-scenario-publish-report/06-01-01-publish.png)
2. Введите имя учетной записи службы Power BI, если вы еще не сделали это, и нажмите кнопку **Войти**.
   
    ![Вход в учетную запись](./media/sharepoint-scenario-publish-report/06-01-02-account.png)
3. Введите пароль и нажмите кнопку **Войти**.
   
    ![Ввод пароля учетной записи](./media/sharepoint-scenario-publish-report/06-01-03-password.png)
4. Выберите целевую рабочую область для отчета и нажмите кнопку **Выбрать**. Мы рекомендуем публиковать отчет в рабочей области группы, чтобы упростить доступ к нему в SharePoint. В этом примере мы опубликуем отчет в рабочей области группы **Управление проектами**. Дополнительные сведения см. в разделе [Совместная работа в рабочей области приложения Power BI](https://docs.microsoft.com/power-bi/service-collaborate-power-bi-workspace).
   
    ![Целевая рабочая область](./media/sharepoint-scenario-publish-report/06-01-04-workspace.png)
5. Опубликовав отчет, перейдите по ссылке **Открыть project-analysis.pbx в Power BI**.
   
    ![Публикация выполнена](./media/sharepoint-scenario-publish-report/06-01-05-open-report.png)
6. Служба Power BI загрузит отчет в браузер. Если панель навигации слева не развернута, откройте меню в левом верхнем углу **(а)**.
   
    ![Отчет в службе Power BI](./media/sharepoint-scenario-publish-report/06-01-06-service-report.png)
   
    Как видите, после публикации отчета в Power BI Desktop загружается набор **(г)** и отчет **(в)**. Панели мониторинга создаются в службе, а не приложении Power BI Desktop. В этой рабочей области еще нет панелей мониторинга **(б)**. Скоро мы создадим ее.

## <a name="step-2-configure-credentials-for-refresh"></a>Шаг 2. Настройка учетных данных для обновления
1. В правом верхнем углу службы щелкните ![Значок с шестеренкой](./media/sharepoint-scenario-publish-report/icon-gear.png) и выберите **Параметры**.
2. Перейдите на вкладку **Наборы данных** и выберите **project-analysis**.
   
    ![Набор данных project-analysis](./media/sharepoint-scenario-publish-report/06-01-07-dataset.png)
3. Разверните пункт **Учетные данные источников данных**, а затем нажмите кнопку **Изменить учетные данные**.
   
    ![Изменение учетных данных источников данных](./media/sharepoint-scenario-publish-report/06-01-08-credentials.png)
4. Выберите способ проверки подлинности **OAuth2** и нажмите кнопку **Войти**.
   
    ![Вход в SharePoint](./media/sharepoint-scenario-publish-report/06-01-09-sign-in.png)
5. Выберите учетную запись с разрешениями для списков SharePoint или войдите в нее.
   
    ![Вход в Office 365](./media/sharepoint-scenario-publish-report/06-01-10-account.png)
   
    По завершении процесса в службе появится следующее сообщение:
   
    ![Источник данных обновлен](./media/sharepoint-scenario-publish-report/06-01-11-updated.png)

## <a name="step-3-create-a-dashboard"></a>Шаг 3. Создание панели мониторинга

1. Чтобы вернуться к отчету, в разделе **Отчеты** выберите **project-analysis**.

1. В левом верхнем углу нажмите диаграмму, а затем — ![Значок булавки](./media/sharepoint-scenario-publish-report/icon-pin.png).
   
    ![Закрепление диаграммы](./media/sharepoint-scenario-publish-report/06-01-12-pin-projected.png)
2. Введите имя панели мониторинга, на которой нужно закрепить диаграмму, и нажмите кнопку **Закрепить**.
   
    ![Закрепление диаграммы на новой панели мониторинга](./media/sharepoint-scenario-publish-report/06-01-13-pin-new.png)
3. В правом верхнем углу нажмите диаграмму, а затем — ![Значок булавки](./media/sharepoint-scenario-publish-report/icon-pin.png).
   
    ![Закрепление диаграммы](./media/sharepoint-scenario-publish-report/06-01-14-pin-variance.png)
4. Выберите существующую панель мониторинга и нажмите кнопку **Закрепить**.
   
    ![Закрепление диаграммы на существующей панели мониторинга](./media/sharepoint-scenario-publish-report/06-01-15-pin-existing.png)

5. Закрепите остающиеся визуальные элементы (всего два).

6. На панели навигации щелкните имя панели мониторинга.
   
    ![Новая панель мониторинга на панели навигации сайта](./media/sharepoint-scenario-publish-report/06-01-16-dashboard-menu.png)

7. Просмотрите панель мониторинга. Если щелкнуть плитку, вы вернетесь к отчету.
   
    ![Готовая панель мониторинга](./media/sharepoint-scenario-publish-report/06-01-17-dashboard-completed.png)

Основная работа в Power BI выполнена. Если это ваши первые отчет и панель мониторинга, — поздравляем! Если вы уже делали это, надеемся, что вы быстро выполнили эти шаги. Теперь мы добавим оповещения, чтобы быть в курсе важных событий, связанных с панелью мониторинга.

## <a name="next-steps"></a>Дальнейшие действия
Следующий шаг в этой серии руководств — [настройка оповещений о данных для отчетов о проектах в Power BI](sharepoint-scenario-alerts-flow.md).

