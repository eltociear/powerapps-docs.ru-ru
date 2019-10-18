---
title: Форматкурренци | Документация Майкрософт
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
ms.assetid: 87e433e6-573f-414f-b49d-1213f2bd8cf4
ms.openlocfilehash: 6089e88ce5814ca24c8310435726bff07cc97894
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343250"
---
# <a name="formatcurrency"></a>formatCurrency

[!INCLUDE [formatcurrency-description](includes/formatcurrency-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия)

## <a name="syntax"></a>Синтаксис

`context.formatting.formatCurrency(value, precision, symbol)`

## <a name="parameters"></a>Вход

| Имя параметра|Тип|Требуется|Description|
| ------------- |----|--------|-----------|
|value|`number`|да| Форматируемое значение.|
|обеспечивают|`number`|да| Число цифр после десятичной запятой.|
|Знак|`string`|да| Символ валюты или код, который добавляется с денежным значением.|

## <a name="return-value"></a>Возвращаемое значение

Тип: `string`


### <a name="related-topics"></a>Связанные статьи

[Форматирование](../formatting.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)