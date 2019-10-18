---
title: Элемент Code | Документация Майкрософт
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/4/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 44d9fcfb-0cd8-48cc-aace-dd589099dd79
ms.openlocfilehash: 2caf89a73dba006240c5bb6e8c874dfdd795d8c2
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346654"
---
# <a name="code-element"></a>элемент Code

[!INCLUDE [code-description](includes/code-description.md)]

## <a name="available-for"></a>Доступно для

Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия)

## <a name="attributes"></a>Атрибуты

|Имя|Description|Тип|Требуется|Доступно для|
|--|--|--|--|-----|
|`path`|Место расположения файлов ресурсов|`String`|Да|Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия) (экспериментальная Предварительная версия)|
|`order`|Порядок загрузки файлов ресурсов|`Positive integer`|Да|Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия) (экспериментальная Предварительная версия)|

## <a name="parent-elements"></a>Родительские элементы

|Элемент|Description|
|--|--|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

### <a name="example"></a>Пример

```XML
<code path="TS_IncrementControl.js" order="1" />
        <css path="css/TS_IncrementControl.css" order="1" />
      <resx path="strings/TSIncrementControl.1033.resx" version="1.0.0" />
```

### <a name="related-topics"></a>Связанные статьи

[Справочник по схеме манифеста платформы компонентов PowerApps](index.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)