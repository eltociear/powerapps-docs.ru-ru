---
title: Добавление отчета или панели мониторинга Power BI на веб-страницу в портале | MicrosoftDocs
description: Инструкции по добавлению отчета или панели мониторинга Power BI на веб-страницу портала.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3735a0ef1a26fdd19b7bfb7f6db717cf9bd07861
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "2710082"
---
# <a name="add-a-power-bi-report-or-dashboard-to-a-web-page-in-portal"></a>Добавление отчета или панели мониторинга Power BI на веб-страницу портала

Чтобы добавить отчет или панель мониторинга Power BI на веб-страницу портала, используйте тег Liquid [powerbi](../liquid/portals-entity-tags.md#powerbi). Тег можно добавить в поле **Копия** на веб-странице или в поле **Источник** в веб-шаблоне. Если вы добавляете отчет или панель мониторинга Power BI, созданную в новой рабочей области в Power BI, необходимо указать тип проверки подлинности powerbiembedded в Liquid-теге powerbi.

Например: 

```
{% powerbi path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

> [!NOTE]
> Если указан тип проверки подлинности AAD в Liquid-теге powerbi, необходимо открыть к нему доступ для требуемых пользователей перед добавлением безопасного отчета или панели мониторинга Power BI на веб-страницу в портале. Дополнительные сведения: [Предоставление общего доступа к рабочей области Power BI](https://docs.microsoft.com/power-bi/service-how-to-collaborate-distribute-dashboards-reports#collaborate-with-coworkers-in-an-app-workspace) и [предоставление панели мониторинга и отчета Power BI](https://docs.microsoft.com/power-bi/service-share-dashboards).

## <a name="get-the-path-of-a-dashboard-or-report"></a>Получение пути к панели мониторинга или отчету

1.  Выполните вход в [Power BI](https://powerbi.microsoft.com/).

2.  Откройте панель мониторинга или отчет, который требуется встроить на портал.

3.  Скопируйте URL-адрес из адресной строки.

    > [!div class=mx-imgBorder]
    > ![Получение пути к панели мониторинга Power BI](../media/powerbi-dashboard-url.png "Получение пути к панели мониторинга Power BI")

## <a name="get-the-id-of-a-dashboard-tile"></a>Плитка "Получить ИД панели мониторинга"

1.  Выполните вход в [Power BI](https://powerbi.microsoft.com/).

2.  Откройте панель мониторинга, из которой требуется встроить плитку на портал.

3.  Наведите указатель мыши на плитку, выберите **Дополнительные параметры** и нажмите **Открыть в режиме фокуса**.

    > [!div class=mx-imgBorder]
    > ![Открытие плитки панели мониторинга Power BI в режиме фокуса](../media/powerbi-dashboard-tile-focus.png "Открытие плитки панели мониторинга Power BI в режиме фокуса")

4.  Скопируйте ИД плитки из URL-адреса в адресной строке. ИД плитки — это значение после /tiles/.

    > [!div class=mx-imgBorder]
    > ![ИД плитки панели мониторинга Power BI](../media/powerbi-dashboard-tile-id.png "ИД плитки панели мониторинга Power BI")


### <a name="see-also"></a>См. также


[тег powerbi Liquid](../liquid/portals-entity-tags.md#powerbi)<br> 
[Настройка интеграции Power BI](set-up-power-bi-integration.md)
