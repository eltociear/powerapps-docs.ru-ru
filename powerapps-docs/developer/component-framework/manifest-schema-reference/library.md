---
title: Элемент Library | Документация Майкрософт
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
ms.assetid: 90f2b4c9-7396-4ab9-bc9f-810189dc18b7
ms.openlocfilehash: bd766864e6ef971b5245afad7d49af54b9369087
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346309"
---
# <a name="library-element"></a>элемент Library

[!INCLUDE [library-description](includes/library-description.md)]

## <a name="attributes"></a>Атрибуты

|Имя|Description|Тип|Требуется|
|--|--|--|--|
|`name`|Имя библиотеки|`string`|Да|
|`version`|Текущая версия библиотеки|Положительное целое число|Да|
|`order`|Порядок загрузки файлов библиотеки|Положительное целое число|Да|

## <a name="parent-elements"></a>Родительские элементы

|Элемент|Description|
|--|--|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

## <a name="child-elements"></a>Дочерние элементы

|Элемент|Description|Вхождений|
|--|--|--|
|[packaged_library]||0 или более|

## <a name="example"></a>Пример

```xml
<resources>
<library name="AngularJSCore" version=">=1" order="1">
<packaged_library path="libs/angular.min.js" version="1.5.8" />
</library>
  </resources>
```

### <a name="related-topics"></a>Связанные статьи

[Справочник по схеме манифеста платформы компонентов PowerApps](index.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)