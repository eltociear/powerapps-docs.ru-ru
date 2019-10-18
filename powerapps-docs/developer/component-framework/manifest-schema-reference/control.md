---
title: Control, элемент | Документация Майкрософт
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
ms.assetid: 4dacd337-c9df-458e-86f3-bfb3ab543ea7
ms.openlocfilehash: aa02b89ce1e032a3cf2fdedca8f0fdf79cb84045
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346631"
---
# <a name="control-element"></a>Control, элемент

[!INCLUDE [control-description](includes/control-description.md)]

## <a name="available-for"></a>Доступно для

Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия)

## <a name="attributes"></a>Атрибуты

|Имя|Description|Тип|Требуется|Доступно для|
|--|--|--|--|--------|
|`namespace`|Определяет прототип объекта компонента|[!INCLUDE [alphanumerictype-description](includes/alphanumerictype-description.md)]|Да|Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия) (экспериментальная Предварительная версия)|
|`constructor`|Метод инициализации объекта|[!INCLUDE [alphanumerictype-description](includes/alphanumerictype-description.md)]|Да|Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия) (экспериментальная Предварительная версия)|
|`control-type`|Standard|[!INCLUDE [controltype-description](includes/controltype-description.md)]|Нет|Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия) (экспериментальная Предварительная версия)|
|`description-key`|Определяет описание компонента, который будет отображаться в пользовательском интерфейсе.|`string`|Нет|Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия) (экспериментальная Предварительная версия)|
|`display-name-key`|Определяет имя элемента управления, отображаемого в пользовательском интерфейсе.|`string`|Да|Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия) (экспериментальная Предварительная версия)|
|`preview-image`|Изображение, которое будет использоваться на экранах настройки для отображения предварительного просмотра компонента.|`string`|Нет|Приложения на основе модели|
|`version`|Определяет версию компонента, определенного в [семантическом управлении версиями](https://semver.org)|`string`|Да|Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия) (экспериментальная Предварительная версия)|
<!--|`hidden`|Определяет, должен ли компонент быть скрытым|[!INCLUDE [booleantype-description](includes/booleantype-description.md)]| Нет|Приложения на основе модели|-->

## <a name="parent-elements"></a>Родительские элементы

|Элемент|Description|
|--|--|
|[manifest](manifest.md)|[!INCLUDE [manifest-description](includes/manifest-description.md)]|

## <a name="child-elements"></a>Дочерние элементы

|Элемент|Description|Вхождений|
|--|--|--|
|[data-set](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|0 или более|
|[property](property.md)|[!INCLUDE [property-description](includes/property-description.md)]|0 или более|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|1|
|[type-group](type-group.md)|[!INCLUDE [type-group-description](includes/type-group-description.md)]|0 или более|

## <a name="example"></a>Пример

```xml
<control namespace="MyNameSpace" constructor="JSHelloWorldControl" version="1.0.0"
 display-name-key="JS_HelloWorldControl_Display_Key" description-key="JS_HelloWorldControl_Desc_Key"
 control-type="standard" preview-image="img/preview.png">
</control>
  ```

### <a name="related-topics"></a>Связанные статьи

[Справочник по схеме манифеста платформы компонентов PowerApps](index.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)