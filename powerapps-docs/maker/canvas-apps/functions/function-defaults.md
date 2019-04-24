---
title: Функция Defaults | Документация Майкрософт
description: Справочные сведения о функции Defaults в PowerApps, включая описание синтаксиса и примеры.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/01/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 83021ff0d18eb5d7322ef40eaa2bc0839b56f452
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61551176"
---
# <a name="defaults-function-in-powerapps"></a>Функция Defaults в PowerApps
Возвращает значения по умолчанию для [источника данных](../working-with-data-sources.md).  

## <a name="description"></a>Описание
Используйте функцию **Defaults** для предварительного заполнения формы ввода данных, чтобы облегчить ее заполнение.

Эта функция возвращает [запись](../working-with-tables.md#records), которая содержит значения по умолчанию для источника данных.  Если [столбец](../working-with-tables.md#columns) в источнике данных не содержит значения по умолчанию, то это свойство не будет отображаться.

Источники данных различаются по объему предоставляемых по умолчанию сведений, включая возможность не предоставлять их совсем.  При работе с [коллекцией](../working-with-data-sources.md#collections) или другим источником данных, который не поддерживает значения по умолчанию, функция **Defaults** возвращает [пустую](function-isblank-isempty.md) запись.

Чтобы [создать запись](../working-with-data-sources.md), можно использовать функцию **Defaults** в сочетании с функцией **[Patch](function-patch.md)**.

## <a name="syntax"></a>Синтаксис
**Defaults**( *Источник_данных* )

* *Источник_данных* — обязательный аргумент. Источник данных, для которого необходимо получить значения по умолчанию.

## <a name="examples"></a>Примеры

| Формула | Описание | Возвращаемый результат |
| --- | --- | --- |
| **Defaults(&nbsp;Scores&nbsp;)** |Возвращает значения по умолчанию для источника данных **Scores**. |**{Score: 0 }** |

