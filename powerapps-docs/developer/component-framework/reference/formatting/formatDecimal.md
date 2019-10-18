---
title: ФорматдеЦимал | Документация Майкрософт
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
ms.assetid: 05c1c54d-14b5-4dad-9cd8-eec07e750c00
ms.openlocfilehash: 02f31ce76df0300fae517bbf4699c6d559b04591
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343503"
---
# <a name="formatdecimal"></a>formatDecimal

[!INCLUDE [formatdecimal-description](includes/formatdecimal-description.md)]

## <a name="syntax"></a>Синтаксис

`context.formatting.formatDecimal(value, precision);`

## <a name="available-for"></a>Доступно для 

Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия)

## <a name="parameters"></a>Вход

| Имя параметра|Тип|Требуется|Description|
| ------------- |----|--------|-----------|
|value|`number`|Да|Дата для форматирования.|
|обеспечивают|`number`|Да|Число цифр после десятичной запятой.|

## <a name="return-value"></a>Возвращаемое значение

Тип: `string`


### <a name="related-topics"></a>Связанные статьи

[Форматирование](../formatting.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)