---
title: Элемент группы типов | Документация Майкрософт
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
ms.assetid: ec7c1ad4-b834-4755-8a04-2c8940f75674
ms.openlocfilehash: 7b09fad6097bb837c19116d59bb90afbde4d46b2
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345987"
---
# <a name="type-group-element"></a>элемент Type-Group

[!INCLUDE [type-group-description](includes/type-group-description.md)]

## <a name="available-for"></a>Доступно для

Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия)

## <a name="attributes"></a>Атрибуты

|Имя|Description|Тип|Требуется|
|--|--|--|--|
|`name`|Имя типа данных|`string`|Да|

## <a name="parent-elements"></a>Родительские элементы

|Элемент|Description|
|--|--|
|[control](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|


## <a name="child-elements"></a>Дочерние элементы

|Элемент|Description|Вхождений|
|--|--|--|
|[Тип](type.md)|[!INCLUDE [type-description](includes/type-description.md)]|1 или более|


В экспериментальной предварительной версии группы типов поддерживают ограниченную поддержку приложений Canvas. При попытке импортировать компоненты возникают следующие проблемы.

1. Если все типы, перечисленные в группе типов, имеют совместимые типы JavaScript, разработчик пытается выбрать наиболее общий вариант в списке. Ниже перечислены типы, которые считаются совместимыми.
   - Строки: SingleLine. Text, Multiple, SingleLine. TextArea, SingleLine. E-mail, SingleLine. Phone, SingleLine. URL, SingleLine. Tick.
   - Числа: Decimal, float, целых. None, Currency.
   - Даты: Датеандтиме. Датеандтиме, Датеандтиме. DateOnly.

2. Если типы, перечисленные в группе, не считаются совместимыми, то параметр будет рассматриваться как первый тип, указанный в группе типов.

### <a name="example"></a>Пример

```XML
<type-group name="numbers">
      <type>Whole.None</type>
      <type>Currency</type>
      <type>FP</type>
      <type>Decimal</type>
    </type-group>
```

### <a name="related-topics"></a>Связанные статьи

[Справочник по схеме манифеста платформы компонентов PowerApps](index.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)