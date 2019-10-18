---
title: Использование функции | Документация Майкрософт
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
ms.assetid: 87f5e921-4114-4710-a362-db741426a69b
ms.openlocfilehash: fe4d384c8dd53fc0f9efcf5558252984a4be74a3
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345895"
---
# <a name="uses-feature-element"></a>использует элемент Feature

Указывает, какие функции их компоненты хотят использовать.

## <a name="available-for"></a>Доступно для

Приложения на основе модели

## <a name="parent-element"></a>Родительский элемент

|Элемент|Description|
|--|--|
|Использование компонентов|Элемент "использование компонентов" выступает в качестве обертки для элементов использования компонентов, которые сами позволяют разработчикам объявлять, какие функции их компонент хочет использовать. Если не определены элементы, использующие компонент, то элемент "использование компонентов" не требуется.|

## <a name="child-elements"></a>Дочерние элементы

|Элемент|Description|Тип|Требуется|
|--|--|---|----|
|Безымян|Имя компонента, объявленного в компоненте|`string`|Да|
|Обязательно|Указывает, требуется ли компонент для этого компонента|`boolean`|Да|

### <a name="example"></a>Пример 

```XML
<feature-usage>
    <uses-feature name="WebAPI" required="true" />
</feature-usage>
```

В следующей таблице показана связь между этими параметрами и тем, что происходит в коде во время выполнения, независимо от того, будет ли доступна функция функции для вызова на основе параметров использования компонента, определенных в манифесте.

|Явление|Если узел поддерживает|Если узел не поддерживает|
|----|----|-----|
|`uses-feature name="device.captureImage" required=”true"`|`Context.device.captureImage != null`, проверка не требуется.|Предупреждение во время разработки. Загрузка компонента завершится ошибкой во время выполнения.|
|`uses-feature name="device.captureImage" required=”false"`|`Context.device.captureImage != null`|`Context.device.captureImage == null`, компонент может адаптивно проверить это во время выполнения. |
|None|`Context.device.captureImage == null` |`Context.device.captureImage == null` |

### <a name="related-topics"></a>Связанные статьи

[Справочник по схеме манифеста платформы компонентов PowerApps](index.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)