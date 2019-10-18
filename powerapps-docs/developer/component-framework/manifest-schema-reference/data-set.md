---
title: Элемент DataSet | Документация Майкрософт
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
ms.assetid: 9ffe8930-b290-4252-98d4-a1195b00205f
ms.openlocfilehash: adf672b036d1f49619cbc4a5ef72661fbeebf013
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346562"
---
# <a name="data-set-element"></a>элемент набора данных

[!INCLUDE [data-set-description](includes/data-set-description.md)]

## <a name="attributes"></a>Атрибуты

|Имя|Description|Тип|Требуется|Доступно для|
|--|--|--|--|-------|
|`description-key`|Определяет описание свойства.|`string`|Используемых|
|`display-name-key`|Определяет имя свойства.|`string`|Да|
|`name`|Имя сетки|`string`|Да|
|`cds-data-set-options`|Отображает панель CommandBar, Виевселектор, Куиккфиндсеарч, если задано значение true. |`boolean`|Да|

## <a name="parent-elements"></a>Родительские элементы

|Элемент|Description|
|--|--|
|[control](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|

## <a name="example"></a>Пример

```xml
 <data-set name="dataSetGrid" display-name-key="DataSetGridProperty" cds-data-set-options="displayCommandBar:true;displayViewSelector:true;displayQuickFindSearch:true">
 </data-set>
```

### <a name="related-topics"></a>Связанные статьи

[Справочник по схеме манифеста платформы компонентов PowerApps](index.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)