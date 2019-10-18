---
title: Лукупобжектс | Документация Майкрософт
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
ms.assetid: d213b401-cfc4-44df-b55c-f040fb6d7072
ms.openlocfilehash: 0dca29df3537389decefe2584d2fc931cea8979c
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341157"
---
# <a name="lookupobjects"></a>lookupObjects

[!INCLUDE [lookupobjects-description](includes/lookupobjects-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="syntax"></a>Синтаксис

`context.utils.lookupObjects(lookupOptions)`

## <a name="parameters"></a>Вход

| Имя параметра|Тип|Требуется|Description|
| ------------- |----|--------|-----------|
|LookupOptions|`UtilityApi.LookupOptions`|Да|Определяет параметры для открытия диалогового окна поиска. LookupOptions имеет следующие атрибуты:<br/>- **алловмултиселект**: `Boolean`. Указывает, позволяет ли подстановка быть выбрана более одного элемента.<br/>- **дефаултентититипе**: `String`. Используемый по умолчанию тип сущности.<br/>- **дефаултвиевид**: `String`. Представление по умолчанию для использования.<br/>- **EntityType**: `String[]`. Типы сущностей для вывода.<br/>- **виевидс**: `String[]`. Представления, доступные в средстве выбора представлений. Поддерживаются только системные представления (не пользовательские представления).|

## <a name="return-value"></a>Возвращаемое значение

Тип: [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) <[Entityreference](../entityreference.md)[] >


### <a name="related-topics"></a>Связанные статьи

[Utility](../utility.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)