---
title: Внедрение отчета о проекте Power BI в SharePoint Online | Документация Майкрософт
description: В этой задаче мы внедрим отчет Power BI на тот же веб-сайт SharePoint Online, где размещены два наши списка.
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
ms.openlocfilehash: 92ae77237064d28e3070f7e7bc9cb94c4493a3c6
ms.sourcegitcommit: 90245baddce9d92c3ce85b0537c1ac1cf26bf55a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2019
ms.locfileid: "57799601"
---
# <a name="embed-the-power-bi-project-report-in-sharepoint-online"></a>Внедрение отчета о проекте Power BI в SharePoint Online
> [!NOTE]
> Эта статья входит в серию руководств по использованию PowerApps, Microsoft Flow и Power BI совместно с SharePoint Online. Обязательно просмотрите [вводные сведения](sharepoint-scenario-intro.md), чтобы получить общее представление о процессе и скачать связанные файлы.

Теперь мы внедрим отчет Power BI на тот же веб-сайт SharePoint Online, где размещены два наших списка. Power BI поддерживает разные способы внедрения, включая интеграцию непосредственно в страницы SharePoint для мобильных представлений и веб-представлений.

Используя этот подход, Power BI внедряет отчет в качестве веб-части, предоставляет соответствующие права доступа для пользователей и позволяет переходить от внедренного отчета к отчету на веб-сайте powerbi.com. Мы создадим в Power BI ссылку для внедрения, а затем используем эту ссылку на создаваемой странице. Дополнительные сведения см. в статье [Внедрение с помощью веб-части отчетов в SharePoint Online](https://docs.microsoft.com/power-bi/service-embed-report-spo).

## <a name="step-1-generate-an-embed-link"></a>Шаг 1. Создание ссылки для внедрения
1. Войдите в Power BI и в левой области навигации выберите имя отчета.
   
    ![Перейдите к отчету](./media/sharepoint-scenario-embed-report/08-01-01-reports.png)
2. Откройте меню **Файл** и выберите **Внедрить в SharePoint Online**.
   
    ![Внедрение в SharePoint Online](./media/sharepoint-scenario-embed-report/08-01-02-embed-spo.png)
3. Скопируйте из диалогового окна в файл ссылку для внедрения и нажмите кнопку **Закрыть**. Мы воспользуемся этой ссылкой после создания страницы SharePoint.
   
    ![Ссылка для внедрения для SharePoint](./media/sharepoint-scenario-embed-report/08-01-03-embed-url.png)

## <a name="step-2-embed-the-report"></a>Шаг 2. Внедрение отчета
1. Войдите в SharePoint и выберите **Содержимое сайта**.
   
    ![Содержимое сайта SharePoint](./media/sharepoint-scenario-embed-report/08-01-04-site-contents.png)
2. Можно просто включить отчет в домашнюю страницу команды, но мы создадим для него отдельную страницу. Нажмите кнопку **Создать**, а затем выберите параметр **Страница**.
   
    ![Новая страница SharePoint](./media/sharepoint-scenario-embed-report/08-01-05-new-page.png)
3. Введите имя страницы, например "Анализ проекта".
4. Нажмите ![Значок плюса](./media/sharepoint-scenario-embed-report/icon-plus.png) и выберите **Power BI**.
   
    ![Добавление части страницы Power BI](./media/sharepoint-scenario-embed-report/08-01-06-add-page-part.png)
5. Нажмите кнопку **Добавить отчет**.
   
    ![Добавление отчета](./media/sharepoint-scenario-embed-report/08-01-07-add-report.png)
6. В области справа скопируйте URL-адрес для внедрения в поле **Ссылка на отчет Power BI**. Присвойте параметрам **Показать область фильтров** и **Показать область навигации** значение **Вкл**.
   
    ![Параметры отчета](./media/sharepoint-scenario-embed-report/08-01-08-report-settings.png)
7. Теперь отчет внедрен в страницу. Нажмите кнопку **Опубликовать**, чтобы отчет стал доступным для всех, у кого есть доступ к базовому отчету.
   
    ![Завершение внедрения отчета](./media/sharepoint-scenario-embed-report/08-01-09-report-complete.png)

## <a name="step-3-grant-access-to-the-report"></a>Шаг 3. Предоставьте доступ к отчету.
Если вы, как и рекомендуется, используете группы Office 365, убедитесь, что пользователи, которым необходим доступ, являются членами рабочей области группы в службе Power BI. Так они смогут просматривать содержимое группы. Дополнительные сведения см. в разделе [Совместная работа в рабочей области приложения Power BI](https://docs.microsoft.com/power-bi/service-collaborate-power-bi-workspace).

На этом мы завершим работу в Power BI для текущего сценария. Мы начали с извлечения данных из списков SharePoint в Power BI и завершили полный цикл внедрением отчета Power BI назад в SharePoint.

## <a name="next-steps"></a>Дальнейшие действия
Следующий шаг в этой серии руководств — [сквозное выполнение созданного нами рабочего процесса](sharepoint-scenario-summary.md).

