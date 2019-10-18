---
title: Элемент CSS | Документация Майкрософт
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
ms.assetid: b6119424-c0a4-4412-b25c-8239da6cbe36
ms.openlocfilehash: b7c96ba2bbb3e5d6d20df92e58ef0bc4005e7d37
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346585"
---
# <a name="css-element"></a>CSS, элемент

[!INCLUDE [css-description](includes/css-description.md)]

## <a name="available-for"></a>Доступно для

Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия)

## <a name="attributes"></a>Атрибуты

|Имя|Description|Тип|Требуется|Доступно для|
|--|--|--|--|-----|
|`path`|Относительный путь w. r. t manifest, где расположены файлы CSS|`string`|Да|Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия) (экспериментальная Предварительная версия)|
|`order`|Порядок загрузки файлов CSS|`Positive integer`|Используемых|Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия) (экспериментальная Предварительная версия)|

## <a name="parent-elements"></a>Родительские элементы

|Элемент|Description|
|--|--|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

## <a name="example"></a>Пример

```xml
<css path="css/JS_HelloWorldControl.css" order="1" />
```

### <a name="related-topics"></a>Связанные статьи

[Справочник по схеме манифеста платформы компонентов PowerApps](index.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)
