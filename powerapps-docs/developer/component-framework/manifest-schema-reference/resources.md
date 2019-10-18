---
title: Resources, элемент | Документация Майкрософт
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
ms.assetid: 66599c2f-6651-4b27-92da-a38897acdfb5
ms.openlocfilehash: a7df2dde98667fd0de8489943094ad6f4ff210f0
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346079"
---
# <a name="resources-element"></a>Resources, элемент

[!INCLUDE [resources-description](includes/resources-description.md)]

## <a name="available-for"></a>Доступно для

Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия)

## <a name="parent-elements"></a>Родительские элементы

|Элемент|Description|
|--|--|
|[control](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|

## <a name="child-elements"></a>Дочерние элементы

|Элемент|Description|Вхождений|
|--|--|--|
|[code](code.md)|[!INCLUDE [code-description](includes/code-description.md)]|1|
|[css](css.md)|[!INCLUDE [css-description](includes/css-description.md)]|0 или более|
|[img](img.md)|[!INCLUDE [img-description](includes/img-description.md)]|0 или более|
|[html](html.md)|[!INCLUDE [html-description](includes/html-description.md)]|0 или более|
|[resx](resx.md)|[!INCLUDE [resx-description](includes/resx-description.md)]|0 или более|

## <a name="example"></a>Пример

```xml
<resources>
  <code path="JS_HelloWorldControl.js" order="1" />
<css path="css/JS_HelloWorldControl.css" order="1" />
        </resources>
```

### <a name="related-topics"></a>Связанные статьи

[Справочник по схеме манифеста платформы компонентов PowerApps](index.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)