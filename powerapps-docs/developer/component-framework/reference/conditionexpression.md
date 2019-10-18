---
title: ConditionExpression | Документация Майкрософт
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
ms.assetid: bd90b3fd-a4b4-4999-8b53-d2a5dce4966b
ms.openlocfilehash: 10f7275643c0df4c2a4099a80b490fb5e27ce318
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345550"
---
# <a name="conditionexpression"></a>ConditionExpression

[!INCLUDE [conditionexpression-description](includes/conditionexpression-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="properties"></a>Свойства

### <a name="attributename"></a>attributeName

Имя столбца набора данных, для которого применяется фильтр.

**Тип**: `string`

### <a name="conditionoperator"></a>кондитионоператор

Оператор, используемый для вычисления условия.

**Тип**: `enum`

@No__t_0 значение является перечислением со следующими возможными значениями

|Value|Участник|
|--|--|
|-1|None|
|0|Равномерно|
|1|NotEqual|
|2|GreaterThan|
|3|LessThan|
|4|Загруженность|
|5|лессекуал|
|6|Например|
|8|In|
|К 12 столбцам.|Заканчивающ|
|14|Вчерашне|
|15|Today|
|глубин|Текает|
|широкоэкранны|Last7Days|
|стр|Next7Days|
|стр|ластвик|
|20|сисвик|
|максималь|ластмонс|
|выражения|сисмонс|
|размером|On|
|26|онорбефоре|
|превышать|онорафтер|
|8|ластеар|
|29|сисеар|
|33|ластксдайс|
|34|некстксдайс|
|37|ластксмонсс|
|38|некстксмонсс|
|49|содержащих|
|70|инфискалпериодандеар|
|75|Упомянут|
|76|Ниже|
|77|нотундер|
|78|абовеорекуал|
|79|ундерорекуал|
|87|контаинвалуес|

### <a name="entityaliasname"></a>ентитялиаснаме

Имя псевдонима сущности, поэтому для связанных сущностей можно использовать фильтрацию.

**Тип**: `string`

### <a name="value"></a>value

Значение, вычисленное условием.

**Тип**: `string | string[]`

### <a name="related-topics"></a>Связанные статьи

[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)