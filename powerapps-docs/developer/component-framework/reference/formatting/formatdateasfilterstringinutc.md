---
title: Форматдатеасфилтерстрингутк | Документация Майкрософт
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
ms.assetid: a604fbbf-6d09-450d-b686-7a5cb3f3a2bc
ms.openlocfilehash: 2242e1badabd740bf414340ae3d11b29e6000ebb
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343158"
---
# <a name="formatdateasfilterstringinutc"></a>formatDateAsFilterStringInUTC

[!INCLUDE [formatdateasfilterstringinutc-description](includes/formatdateasfilterstringinutc-description.md)]

## <a name="syntax"></a>Синтаксис

`context.formatting.formatDateAsFilterStringInUTC(value, includeTime)`

## <a name="available-for"></a>Доступно для 

Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия)

## <a name="parameters"></a>Вход

| Имя параметра|Тип|Требуется|Description|
| ------------- |----|--------|-----------|
|value|`Date`|да|Дата для форматирования.|
|инклудетиме|`boolean`|да| Значение, если компонент времени должен быть указан в возвращаемом значении.|

## <a name="return-value"></a>Возвращаемое значение

Тип: `string`


### <a name="related-topics"></a>Связанные статьи

[Форматирование](../formatting.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)