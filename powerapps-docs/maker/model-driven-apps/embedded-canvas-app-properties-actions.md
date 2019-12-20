---
title: Свойства и действия элемента управления ModelDrivenFormIntegration | MicrosoftDocs
ms.custom: ''
ms.date: 06/25/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: 00e62904-2ce9-4730-a113-02b1fedbf22e
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 674147425097d75b96e14bfbf76b3c937f9fd999
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2019
ms.locfileid: "2868464"
---
# <a name="modeldrivenformintegration-control-properties-and-actions"></a>Свойства и действия элемента управления ModelDrivenFormIntegration
Приложения холста, внедренные в управляемые моделью формы, содержат специальный элемент управления с именем **ModelDrivenFormIntegration**. Этот элемент управления не отвечает за перенос контекстных данных из управляемой моделью формы, в которой размещено приложение, во внедренное приложение на основе холста.  

В этом разделе рассматриваются свойства и действия, доступные для элемента управления ModelDrivenFormIntegration.

| Свойство или действие | Описание |
|:--------------|:-------------------------|
|**DataSource** | Должен быть задан источник данных, подключенный к родительской сущности хост-формы, управляемой моделью. <br />Автоматически задается при [внедрении нового приложения на основе холста](embedded-canvas-app-add-classic-designer.md). |
|**Элемент** | Доступное только для чтения свойство, которое позволяет внедренному приложению холста обращаться к записи из управляемой моделью хост-формы. <br />В качестве примера, чтобы получить значение поля с именем accountnumber и отображаемым именем Номер организации, можно использовать ModelDrivenFormIntegration.Item.accountnumber или ModelDrivenFormIntegration.Item.'Номер организации'. |
|**OnDataRefresh** | Формула в этом свойстве оценивается, когда управляемая моделью хост-форма сохраняет данные. <br />Используйте его, чтобы обновить источник данных, подключенный к родительской сущности управляемой моделью хост-формы, и чтобы выполнять другие действия, такие как задание или обновление переменных. <br /> В качестве примера, если задать для него приведенную ниже форму, будет обновляться источник данных "Организации" и для переменной с именем CurrentAccountNumber будет задано значение поля "Номер организации" текущей записи. <br /> Refresh(Accounts); Set(CurrentAccountNumber, ModelDrivenFormIntegration.Item.'Номер организации') |
|**RefreshForm** | Обновление данных в управляемой моделью хост-форме. <br />Подробнее см. раздел [Выполнение предопределенных действий в хост-форме](embedded-canvas-app-actions.md#refreshformshowprompt). |
|**SaveForm** | Сохранение данных в управляемой моделью хост-форме. <br />Подробнее см. раздел [Выполнение предопределенных действий в хост-форме](embedded-canvas-app-actions.md#saveform).  |
|**NavigateToMainForm** | Выполняет навигацию управляемой моделью хост-формы к главной форме и отображает указанную запись. <br />Подробнее см. раздел [Выполнение предопределенных действий в хост-форме](embedded-canvas-app-actions.md#navigatetomainformentityname-mainformname-recordid). |
|**NavigateToView** | Навигация управляемой моделью хост-формы в представление. <br />Подробнее см. раздел [Выполнение предопределенных действий в хост-форме](embedded-canvas-app-actions.md#navigatetoviewentityname-viewname).  |
|**OpenQuickCreateForm** | Открывает форму быстрого создания по умолчанию для сущности.  <br />Подробнее см. раздел [Выполнение предопределенных действий в хост-форме](embedded-canvas-app-actions.md#openquickcreateformentityname).  |
|**Data** | Доступное только для чтения свойство, используемое платформой для отправки некоторых основных данных из управляемой моделью хост-формы во внедренное приложение на основе холста.  <br /> Не используйте данное свойство. Используйте Item для получения доступа к записи из управляемой моделью хост-формы.  |

## <a name="see-also"></a>См. также
[Внедрение приложения на основе холста в управляемую моделью форму](embed-canvas-app-in-form.md) <br />
[Добавление внедренного приложения на основе холста в управляемую моделью форму](embedded-canvas-app-add-classic-designer.md) <br />
[Редактирование приложения на основе холста, внедренного в управляемую моделью форму](embedded-canvas-app-edit-classic-designer.md) <br />
[Настройка размера и ориентации экрана приложения на основе холста, внедренного на управляемую моделью форму](embedded-canvas-app-customize-screen.md) <br />
[Выполнение предопределенных действий в форме узла из внедренного приложения холста](embedded-canvas-app-actions.md) <br />
[Предоставление общего доступа к внедренному приложению на основе холста](share-embedded-canvas-app.md) <br />
[Рекомендации по работе с внедренными приложениями на основе холста](embedded-canvas-app-guidelines.md) <br />
[Перенос внедренных приложений на основе холста на управляемые моделью формы, созданных с помощью общедоступной предварительной версии, в последнюю версию](embedded-canvas-app-migrate-from-preview.md) <br />
