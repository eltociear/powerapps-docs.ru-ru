---
title: Элемент набора свойств | Документация Майкрософт
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
ms.assetid: 996f10e5-8057-40ea-9680-555e4cd682ff
ms.openlocfilehash: 98e0bcf7588e72f001e45471c87f0050dd0846ba
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346240"
---
# <a name="property-set-element"></a>элемент Property-Set

[!INCLUDE [property-set-description](includes/property-set-description.md)]

## <a name="available-for"></a>Доступно для

Приложения на основе модели

## <a name="attributes"></a>Атрибуты

|Имя|Description|Тип|Требуется|
|--|--|--|--|
|`name`|Имя поля|`string`|Да|
|`display-name-key`|Используется на экранах настройки как локализованные строки, описывающие имя свойства.|`string`|Да|
|`description-key`|Используется на экранах настройки как локализованные строки, описывающие описание свойства.|`string`|Используемых|
|`of-type`|Определяет тип данных свойства|См. [Примечания](#remarks)|Используемых|
|`required`|Указывает, является ли свойство обязательным|`boolean`|Используемых|
|`of-type-group`|Имя группы типов, как определено в манифесте|`string`|Используемых|
|`usage`|Атрибут Usage определяет, должно ли свойство представлять атрибут сущности, который компонент может изменять (привязывать) или значения только для чтения (входные данные).|`bound` или `input`|Да|

## <a name="parent-elements"></a>Родительские элементы

|Элемент|Description|
|--|--|
|[data-set](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|

## <a name="child-elements"></a>Дочерние элементы

|Элемент|Description|Вхождений|
|--|--|--|
|[типов](types.md)||0 или более|

### <a name="remarks"></a>Примечания

Значение атрибута `of-type` должно быть одним из следующих:

[!INCLUDE [type-table](includes/type-table.md)]

### <a name="related-topics"></a>Связанные статьи

[Справочник по схеме манифеста платформы компонентов PowerApps](index.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)