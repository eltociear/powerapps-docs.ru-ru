---
title: openForm | Документация Майкрософт
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
ms.assetid: bea56947-d976-4974-9ac7-2d5f5c7b6732
ms.openlocfilehash: d0754030de4880f0ad693105e96b47d785f1561b
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342376"
---
# <a name="openform"></a>openForm

[!INCLUDE [openform-description](includes/openform-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="syntax"></a>Синтаксис

`context.navigation.openForm(options, parameters)`

## <a name="parameters"></a>Вход

| Имя параметра|Тип|Требуется|Description|
| ------------- |----|--------|-----------|
|Параметры|`EntityFormOptions`|Да|Параметры формы сущности для открытия формы. Ентитиформоптионс имеет следующие атрибуты:<br/>- **креатефроментити**: `Lookup`. Определяет запись, которая будет предоставлять значения по умолчанию на основе сопоставленных значений атрибутов. Объект Lookup имеет следующие строковые свойства: `entityType`, `id` и `name`. <br/>- **EntityId**: `String`. Идентификатор записи сущности, для которой будет отображаться форма.<br/>- **entityName**: `String`. Логическое имя сущности, для которой нужно отобразить форму.<br/>- **формид**: `String`. Идентификатор экземпляра формы для отображения.<br/>**высота**- : `Number`. Высота окна формы, отображаемая в пикселях.<br/>- **опенинневвиндов**: `boolean`. следует ли отображать форму в новом окне.<br/>- **усекуикккреатеформ**: `Boolean`. следует ли открывать форму быстрого создания. Если этот параметр не указан, по умолчанию `false` передается.<br/>**ширина**- : `Number`. Ширина окна формы, отображаемая в пикселях.<br/>- **windowPosition**: `Number`. Укажите одно из следующих значений для расположения окна формы на экране: `1:center` <br/> `2:side`|
|Вход|`Object`|Нет|Объект Dictionary, который передает в форму дополнительные параметры. Недопустимые параметры приведут к ошибке. Дополнительные сведения [см. в разделе значения полей с использованием параметров, переданных в форму](https://docs.microsoft.com/en-us/powerapps/developer/model-driven-apps/set-field-values-using-parameters-passed-form) , и [Настройте форму для приема пользовательских параметров строки запроса](https://docs.microsoft.com/en-us/powerapps/developer/component-framework/sample-controls/navigation-api-control) .|

## <a name="return-value"></a>Возвращаемое значение

Тип: `Promise<OpenFormSuccessResponse>`

## <a name="remarks"></a>Примечания

См. статью о [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise)

### <a name="related-topics"></a>Связанные статьи

[Навигация](../navigation.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)