---
title: Элемент Image | Документация Майкрософт
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
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 0e776647-a4a2-42c9-85e8-62718154052f
ms.openlocfilehash: f3abd4f6a4061161a86d270f1bb4d0037632880c
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346516"
---
# <a name="img-element"></a>IMG, элемент

[!INCLUDE [img-description](includes/img-description.md)]

## <a name="available-for"></a>Доступно для

Приложения на основе модели

## <a name="attributes"></a>Атрибуты

|Имя|Description|Тип|Требуется|Доступно для|
|--|--|--|--|-------|
|`path`|Относительный путь w. r. t манифеста, где расположены файлы изображений|`string`|Да|Приложения на основе модели|

## <a name="parent-elements"></a>Родительские элементы

|Элемент|Description|
|--|--|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|


### <a name="example"></a>Пример

```XML
<img path="img/default.png" />
```

### <a name="related-topics"></a>Связанные статьи

[Справочник по схеме манифеста платформы компонентов PowerApps](index.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)