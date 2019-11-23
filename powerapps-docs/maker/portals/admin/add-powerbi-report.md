---
title: Добавление Power BI отчета или панели мониторинга на веб-страницу портала | MicrosoftDocs
description: Инструкции по добавлению Power BI отчета или панели мониторинга на веб-страницу на портале.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3735a0ef1a26fdd19b7bfb7f6db717cf9bd07861
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976169"
---
# <a name="add-a-power-bi-report-or-dashboard-to-a-web-page-in-portal"></a>Добавление отчета или панели мониторинга Power BI на веб-страницу на портале

Вы можете добавить Power BI отчет или панель мониторинга на веб-страницу на портале с помощью тега жидкости [powerbi](../liquid/portals-entity-tags.md#powerbi) . Тег можно добавить в поле **Копировать** на веб-странице или в поле **источник** веб-шаблона. При добавлении Power BI отчета или панели мониторинга, созданной в новой рабочей области в Power BI, необходимо указать тип проверки подлинности повербиембеддед в метке жидкостьи powerbi.

Пример. 

```
{% powerbi path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

> [!NOTE]
> Если вы указали AAD в качестве типа проверки подлинности в теге жидкости powerbi, необходимо предоставить доступ к нему необходимым пользователям, прежде чем добавлять Power BI отчет или панель мониторинга в веб-страницу на портале. Дополнительные сведения: [общий доступ к Power BI рабочей области](https://docs.microsoft.com/power-bi/service-how-to-collaborate-distribute-dashboards-reports#collaborate-with-coworkers-in-an-app-workspace) и [общий доступ к Power BI панели мониторинга и отчет](https://docs.microsoft.com/power-bi/service-share-dashboards).

## <a name="get-the-path-of-a-dashboard-or-report"></a>Получение пути к панели мониторинга или отчету

1.  Войдите в [Power BI](https://powerbi.microsoft.com/).

2.  Откройте панель мониторинга или отчет, которые необходимо внедрить на портал.

3.  Скопируйте URL-адрес из адресной строки.

    > [!div class=mx-imgBorder]
    > ![Получение пути к Power BI панели мониторинга](../media/powerbi-dashboard-url.png "Получение пути к панели мониторинга Power BI")

## <a name="get-the-id-of-a-dashboard-tile"></a>Получение идентификатора плитки панели мониторинга

1.  Войдите в [Power BI](https://powerbi.microsoft.com/).

2.  Откройте панель мониторинга, из которой необходимо внедрить плитку на портале.

3.  Наведите указатель на плитку, выберите **Дополнительные параметры**, а затем щелкните **Открыть в режиме фокусировки**.

    > [!div class=mx-imgBorder]
    > ![Открытие плитки панели мониторинга Power BI в режиме фокусировки](../media/powerbi-dashboard-tile-focus.png "Открытие плитки Power BI панели мониторинга в режиме фокусировки")

4.  Скопируйте идентификатор плитки из URL-адреса в адресной строке. Идентификатор плитки — это значение после/Тилес/.

    > [!div class=mx-imgBorder]
    > ![Идентификатор плитки Power BI панели мониторинга](../media/powerbi-dashboard-tile-id.png "Power BI идентификатор плитки панели мониторинга")


### <a name="see-also"></a>См. также


[Тег Ликвидя powerbi](../liquid/portals-entity-tags.md#powerbi)<br> 
[Настройка интеграции Power BI](set-up-power-bi-integration.md)
