---
title: Использование компонентов | Документация Майкрософт
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 87f5e921-4114-4710-a362-db741426a69b
ms.openlocfilehash: 21e76a2a17910fe36967364f063ff2fc9b25e153
ms.sourcegitcommit: 63ea15e2f861d43333aacda19230cd8922d7bdfd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2019
ms.locfileid: "72339639"
---
# <a name="feature-usage-element"></a>элемент "использование компонентов"

Элемент "использование компонентов" выступает в качестве обертки для элементов `uses-feature`, которые сами позволяют разработчикам объявлять, какие функции их компонент хочет использовать. Если не определены элементы, использующие компонент, то элемент "использование компонентов" не требуется.

## <a name="available-for"></a>Доступно для

Приложения на основе модели

## <a name="child-elements"></a>Дочерние элементы

|Элемент|Description|Доступно для|
|--|--|-----|
|[Использование функции](uses-feature.md)|Указывает, какие функции их компоненты хотят использовать.|Приложения на основе модели|


## <a name="example"></a>Пример

```XML
<feature-usage>
    <uses-feature name="Device.captureAudio" required="true" />
    <uses-feature name="Device.captureImage" required="true" />
    <uses-feature name="Device.captureVideo" required="true" />
    <uses-feature name="Device.getBarcodeValue" required="true" />
    <uses-feature name="Device.getCurrentPosition" required="true" />
    <uses-feature name="Device.pickFile" required="true" />
    <uses-feature name="Utility" required="true" />
    <uses-feature name="WebAPI" required="true" />
 </feature-usage>
```
