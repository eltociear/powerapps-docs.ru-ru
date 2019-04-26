---
title: Интеграция PowerApps, Microsoft Flow и Power BI с SharePoint Online (введение) | Документация Майкрософт
description: 'Этой серии руководств описано, как создать приложение на основе холста basic для управления проектами на основе списков SharePoint и три ключевые технологии, которые интегрируются с SharePoint Online: PowerApps, Microsoft Flow и Power BI.'
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
ms.openlocfilehash: 812a73163047914a8f0bcc651c831ee4022fcc28
ms.sourcegitcommit: 4ed29d83e90a2ecbb2f5e9ec5578e47a293a55ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63319421"
---
# <a name="integrate-powerapps-microsoft-flow-and-power-bi-with-sharepoint-online"></a>Интеграция PowerApps, Microsoft Flow и Power BI с SharePoint Online
Вы установили SharePoint Online и хотите больше автоматизировать и оптимизировать бизнес-процессы? Вы уже работали с PowerApps, Microsoft Flow или Power BI, но не знаете, как использовать их с SharePoint Online? Вы обратились по адресу! Этой серии руководств описано, как создать приложение на основе холста basic для управления проектами на основе списков SharePoint и три ключевые технологии, которые интегрируются с SharePoint Online: PowerApps, Microsoft Flow и Power BI. Эти технологии взаимосвязаны, что позволяет легко *анализировать* бизнес-процессы, *действовать* на основе результатов и *автоматизировать* рабочие процессы. В ходе работы с этой серией вы проработаете приблизительно такой сценарий:

![Схема готового сценария](./media/sharepoint-scenario-intro/composite-with-background.png)

## <a name="business-scenario"></a>Бизнес-сценарий
В этой серии руководств используется сайт SharePoint Online компании Contoso, созданный для управления жизненными циклами проектов — от запроса, утверждения, разработки и до окончательного анализа. *Запрашивающий проекты*, например руководитель отдела, отправляет запрос на ИТ-проект, добавляя элемент в список SharePoint. *Утверждающий проекты*, например руководитель ИТ-отдела, просматривает проект и утверждает или отклоняет его. Если проект утвержден, для него назначается *руководитель проекта* и добавляются дополнительные сведения во второй список с помощью того же приложения. *Бизнес-аналитик* просматривает текущие и выполненные проекты, используя отчеты Power BI, внедренные в SharePoint.  С помощью Microsoft Flow отправляются утверждения и ответы на оповещения Power BI.

## <a name="getting-started-quickly"></a>Быстрое начало работы
В этой серии руководств представлен упрощенный сценарий по сравнению с созданием полнофункционального приложения для управления проектами и анализа. Тем не менее вам потребуется некоторое время, чтобы выполнить все задачи. Вводные сведения об использовании PowerApps, Microsoft Flow и Power BI с SharePoint см. в следующих статьях.

* **PowerApps**: [Создание приложения из списка SharePoint с использованием PowerApps](app-from-sharepoint.md#generate-an-app-from-within-sharepoint-online) и [Создание приложения для управления данными в списке SharePoint](app-from-sharepoint.md)
* **Microsoft Flow**: [Ожидание утверждений в Microsoft Flow](https://docs.microsoft.com/flow/wait-for-approvals)
* **Power BI**: [Внедрение с помощью веб-части отчетов в SharePoint Online](https://docs.microsoft.com/power-bi/service-embed-report-spo)

Мы надеемся, что после прочтения перечисленных материалов вы ознакомитесь с этим сценарием.

Работая со сценарием, вы также можете сосредоточиться на интересующих вас задачах, выполняя остальные по мере возможности. Настроив списки SharePoint в задаче 1, вы сможете выполнять задачи 2–5 в любом порядке. Задачи 6–8 выполняются последовательно. Кроме того, в [пакет загрузки](https://aka.ms/o4ia0f) для этого сценария мы включили два полнофункциональных приложения и отчет Power BI Desktop. Вы можете ознакомиться с ними и поработать с примерами, даже не проходя все этапы каждой задачи.

## <a name="prerequisites"></a>Технические условия
Чтобы выполнить этот сценарий вам понадобятся следующие подписки и классические приложения: Подписка "Office 365 бизнес премиум" включает PowerApps и Microsoft Flow.

| **Подписка или средство** | **Ссылка** |
| --- | --- |
| Подписка Office 365 бизнес премиум |[Пробная подписка](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1) |
| Подписка Power BI Pro |[Пробная подписка](https://powerbi.microsoft.com/get-started/) (щелкните **Попробовать бесплатно**) |
| Power BI Desktop |[Бесплатная загрузка](https://powerbi.microsoft.com/get-started/) (щелкните **Скачать бесплатно**) |

Предполагается, что у вас есть базовые знания о каждой технологии. Но даже в противном случае вы сможете выполнить этот сценарий. Сведения о технологиях см. в следующих статьях:

* [Начало работы с SharePoint](https://support.office.com/article/Get-started-with-SharePoint-909ec2f0-05c8-4e92-8ad3-3f8b0b6cf261)
* [Пошаговое изучение PowerApps](../../guided-learning/index.md)
* [Пошаговое изучение Microsoft Flow](https://docs.microsoft.com/flow/guided-learning/)
* [Пошаговое изучение Power BI](https://docs.microsoft.com/power-bi/guided-learning/)

## <a name="next-steps"></a>Дальнейшие действия
Следующий шаг — [настройка списков SharePoint Online](sharepoint-scenario-setup.md), которые будут использоваться во всех руководствах серии.

