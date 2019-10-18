---
title: Элемент Property | Документация Майкрософт
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
ms.assetid: 45f4872d-c1d2-4c5a-8721-251b96ede370
ms.openlocfilehash: ee4e0b0259d5978f3e84757d4023827ada45f01e
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346148"
---
# <a name="property-element"></a>элемент Property

[!INCLUDE [property-description](includes/property-description.md)]

## <a name="available-for"></a>Доступно для

Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия)

## <a name="attributes"></a>Атрибуты

|Имя|Description|Тип|Требуется|
|--|--|--|--|
|`name`|Имя свойства|`string`|Да|
|`display-name-key`|Используется на экранах настройки как локализованные строки, описывающие имя свойства.|`string`|Да|
|`of-type`|Определяет тип данных свойства|См. [Примечания](#remarks)|Используемых|
|`usage`|Атрибут Usage определяет, должно ли свойство представлять атрибут сущности, который компонент может изменять (привязывать) или значения только для чтения (входные данные).|`bound` или `input`|Используемых|
|`required`|Является ли свойство обязательным|`boolean`|Используемых|
|`of-type-group`|Имя группы типов, как определено в манифесте|`string`|Используемых|
|`description-key`|Используется на экранах настройки как локализованные строки, описывающие описание свойства.|`string`|Используемых|
|`default-value`|Значение конфигурации по умолчанию, предоставляемое компоненту. В приложениях, управляемых моделью, этот атрибут разрешен только для входных данных, так как связанные параметры предполагают наличие поля.|`string`|Используемых|

### <a name="remarks"></a>Примечания

Значение атрибута `of-type` должно быть одним из следующих:

[!INCLUDE [type-table](includes/type-table.md)]

## <a name="parent-elements"></a>Родительские элементы

|Элемент|Description|
|--|--|
|[manifest](manifest.md)|[!INCLUDE [manifest-description](includes/manifest-description.md)]|


## <a name="example"></a>Пример

```xml
<property name="myFirstProperty" display-name-key="myFirstProperty_Display_Key" 
description-key="myFirstProperty_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" />
```

### <a name="related-topics"></a>Связанные статьи

[Справочник по схеме манифеста платформы компонентов PowerApps](index.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)
