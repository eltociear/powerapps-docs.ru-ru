---
title: Paging | Документация Майкрософт
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
ms.assetid: 12891e96-972c-4289-bbde-2bc261cd1f12
ms.openlocfilehash: ccf68c94e0b11f8a1227199609a9c21c1923ad7b
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342192"
---
# <a name="paging"></a>Paging

[!INCLUDE [paging-description](includes/paging-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="properties"></a>Свойства

### <a name="totalresultcount"></a>тоталресулткаунт

Общее количество результатов на сервере для текущего запроса.

**Тип**: `number`

### <a name="hasnextpage"></a>хаснекстпаже

Может ли результирующий набор передаваться по страницам назад.

**Тип**: `boolean`

### <a name="haspreviouspage"></a>хаспревиауспаже

Может ли результирующий набор передаваться по страницам назад.

**Тип**: `boolean`

## <a name="methods"></a>Метод

|Method | Description |
| ------|-------------|
|[лоаднекстпаже](paging/loadnextpage.md)|[!INCLUDE [loadnextpage-description](paging/includes/loadnextpage-description.md)]|
|[лоадпревиауспаже](paging/loadpreviouspage.md)|[!INCLUDE [loadpreviouspage-description](paging/includes/loadpreviouspage-description.md)]|
|[перезапуск](paging/reset.md)|[!INCLUDE [reset-description](paging/includes/reset-description.md)]|
|[setPageSize](paging/setpagesize.md)|[!INCLUDE [setpagesize-description](paging/includes/setpagesize-description.md)]|
|pageSize|Число записей, возвращаемых на страницу набора данных. В формах набор данных pageSize имеет форматирование (число строк), а на других можно выбрать личные параметры.|


### <a name="related-topics"></a>Связанные статьи

[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)