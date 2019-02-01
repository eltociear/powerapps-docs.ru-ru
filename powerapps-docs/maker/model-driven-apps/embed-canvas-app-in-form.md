---
title: Внедрение приложения на основе холста в управляемую моделью форму | MicrosoftDocs
ms.custom: ''
ms.date: 12/10/2018
ms.reviewer: ''
ms.service: crm-online
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
  - PowerApps maker portal impact
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="embed-a-canvas-app-on-a-model-driven-form"></a>Внедрение приложения на основе холста в управляемую моделью форму

Приложения на основе холста позволяют создателям легко разрабатывать и создавать собственные макеты создать с помощью WYSIWYG-конструктора приложений на основе холста с малым количеством кода. Приложения на основе холста также позволяют создателям подключать и отображать в своих формах данные из более 200 источников данных.

> [!NOTE]
> Эта функция в настоящее время доступна для предварительного ознакомления. <br />
> [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]

С внедренными приложениями на основе холста создатели могут использовать мощь приложений на основе холста в своих управляемых моделью формах. С помощью внедренных приложений на основе холста можно легко создавать визуально насыщенные области в форме и отображать данные из различных источников непосредственно рядом с данными из Common Data Service.

   > [!div class="mx-imgBorder"] 
   > ![](media/embed-canvas-app-in-form.png "Внедренные приложения на основе холста в управляемых моделью формах приложения")

Приложения на основе холста внедряются в управляемые моделью формы таким же образом, каким добавляются другие настраиваемые элементы управления. Внедренное приложение на основе холста включает большие возможности интеграции данных, которые добавляют контекстные данные из управляемой моделью основной формы во внедренное приложение на основе холста.

Шаги по внедрению приложения на основе холста в управляемую моделью форму зависят от контекста данных, которые основная управляемая моделью форма должна предоставлять внедренному приложению на основе холста.
-   Передайте текущую запись в виде контекста данных. Дополнительные сведения: [Передача текущей записи в качестве контекста данных с внедренным приложением на основе холста](pass-current-embedded-canvas-app.md)
-   Передайте список записей, связанных с текущей записью, в качестве контекста данных. Дополнительные сведения: [Передача списка связанных записей в качестве контекста данных с внедренным приложением на основе холста](pass-related-embedded-canvas-app.md) 

<!-- After you have added an embedded canvas app to your model-driven form, learn how to share your embedded canvas app with other users (LINK TO ARTICLE #4).  -->

<!-- For things to keep in mind when working with embedded canvas apps and to help troubleshoot any issues you might encounter, see (LINK TO ARTICLE #5). -->

## <a name="see-also"></a>См. также
[Что такое приложения на основе холста в PowerApps?](../canvas-apps/getting-started.md) <br />
[Добавление и настройка элемента управления приложения на основе холста в PowerApps](../canvas-apps/add-configure-controls.md) <br />
[Обзор соединителей приложений на основе холста для PowerApps](../canvas-apps/connections-list.md) 
