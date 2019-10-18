---
title: FilterExpression | Документация Майкрософт
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
ms.assetid: 19ad54b8-e044-4f07-a18e-b00d26b75832
ms.openlocfilehash: 7b613238f28987b688d4f2299506fa91b72a99a7
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343986"
---
# <a name="filterexpression"></a>FilterExpression

[!INCLUDE [filterexpression-description](includes/filterexpression-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="properties"></a>Свойства

### <a name="conditions"></a>Состоянии

Набор условий, связанных с этим фильтром.

**Тип**: [кондитионекспрессион](conditionexpression.md)[]

### <a name="filteroperator"></a>филтероператор

Оператор, используемый для объединения условий в этом фильтре.

**Тип**: `enum`

@No__t_0 значение является перечислением со следующими возможными значениями

|Value|Участник|
|--|--|
|0|And|
|1|Or|

### <a name="filters"></a>Фильтрующ

Все дочерние фильтры, которые должны быть оценены после оценки этого фильтра.

**Тип**: [FilterExpression](filterexpression.md)[]<br />

### <a name="related-topics"></a>Связанные статьи

[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)