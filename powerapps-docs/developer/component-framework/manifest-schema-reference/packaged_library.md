---
title: Упакованный элемент библиотеки | Документация Майкрософт
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
ms.assetid: 41c50db2-3096-4990-ac2b-e702c161bf4f
ms.openlocfilehash: 011aa2ab527cc2bd16fc99842e2388a3a6b0918e
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346194"
---
# <a name="packaged_library-element"></a>packaged_library, элемент

[!INCLUDE [packaged_library-description](includes/packaged_library-description.md)]

## <a name="available-for"></a>Доступно для

Приложения на основе модели

## <a name="attributes"></a>Атрибуты

|Имя|Description|Тип|Требуется|Доступно для|
|--|--|--|--|-------|
|`path`|Место расположения файлов упакованной библиотеки|`string`|Да|Приложения на основе модели|
|`version`|Текущая версия упакованной библиотеки|`string`|Да|Приложения на основе модели|

## <a name="parent-elements"></a>Родительские элементы

|Элемент|Description|
|--|--|
|[Библиотечная](library.md)|[!INCLUDE [library-description](includes/library-description.md)]|

## <a name="example"></a>Пример

```xml
<resources>
    <library name="AngularJSCore" version=">=1" order="1">
    <packaged_library path="libs/angular.min.js" version="1.5.8" />
    </library>
```

### <a name="related-topics"></a>Связанные статьи

[Справочник по схеме манифеста платформы компонентов PowerApps](index.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)
