---
title: Ентитиформоптионс | Документация Майкрософт
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
ms.assetid: 418871c0-59dc-4a7c-a8f9-9364a19f7662
ms.openlocfilehash: 7429a5bac040e3c20412ac0916743a57d9d5710f
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72344377"
---
# <a name="entityformoptions"></a>ентитиформоптионс

Предоставляет доступ ко всем сведениям о формах сущностей.

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="properties"></a>Свойства

### <a name="createfromentity"></a>креатефроментити

Определяет запись, которая будет предоставлять значения по умолчанию на основе сопоставленного значения атрибута. Объект Lookup имеет следующие свойства: тип сущности, идентификатор и имя.

**Тип**: [EntityReference](entityreference.md)

### <a name="entityid"></a>entityId

Уникальный идентификатор записи сущности, для которой отображается форма. 

**Тип**: `string`

### <a name="entityname"></a>entityName

Логическое имя сущности, для которой нужно отобразить форму. 

**Тип**: `string`

### <a name="formid"></a>формид

Идентификатор экземпляра формы для отображения.

**Тип**: `string`

### <a name="height"></a>height

Высота окна формы, отображаемая в пикселях.

**Тип**: `number`

### <a name="openinnewwindow"></a>опенинневвиндов

Следует ли отображать форму в новом окне.

**Тип**: `boolean`

### <a name="usequickcreateform"></a>усекуикккреатеформ

следует ли открывать форму быстрого создания. Если этого не указать, передается значение false по умолчанию. 

**Тип**: `boolean`

### <a name="width"></a>width

Ширина окна формы, отображаемая в пикселях.

**Тип**: `boolean`

### <a name="windowposition"></a>windowPosition

Задает расположение окна на экране.

**Тип**: `number`

Значение windowPosition является числом со следующими возможными значениями

|Value|Положение|
|---|---|
|1|Center|
|2|Сбоку|


### <a name="related-topics"></a>Связанные статьи

[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)