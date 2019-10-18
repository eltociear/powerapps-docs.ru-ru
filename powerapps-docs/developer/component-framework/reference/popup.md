---
title: Popup | Документация Майкрософт
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
ms.assetid: b0af1803-ae3a-41c2-a8a5-b15970bd6f96
ms.openlocfilehash: bb28a979ac721eded06025a56588023c211ea6f9
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342215"
---
# <a name="popup"></a>Popup

[!INCLUDE [popup-description](includes/popup-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="properties"></a>Свойства

### <a name="closeonoutsideclick"></a>клосеонаутсидекликк

Указывает, закрывается ли всплывающее окно при внешнем щелчке мышью. Если задано значение `false`, всплывающее окно не будет закрыто при внешнем щелчке мышью.

**Тип**: `boolean`

### <a name="content"></a>Содержани

Вставленный статический элемент DOM.

**Тип**: [HTMLElement](https://developer.mozilla.org/docs/Web/API/HTMLElement)

### <a name="id"></a>Id

Идентификатор, заданный для компонента привязки, если таковой имеется.

**Тип**: `string`

### <a name="name"></a>Безымян

Имя всплывающего окна. Используется в качестве ссылки для открытия всплывающих окон.

**Тип**: `string`

### <a name="popuptoopen"></a>попуптупен

Имя всплывающего окна, которое должно быть открыто.

**Тип**: `string`

### <a name="remarks"></a>Примечания

Должно быть определено только в корневом всплывающем окне. Чтобы открыть вложенные всплывающие окна, необходимо указать строку, подобную `rootName.nestedName.[allOtherNestedNames]`. Чтобы закрыть всплывающие окна, необходимо предоставить пустую строку. Это свойство будет автоматически распространяться на дочерние элементы.

## <a name="type"></a>type

Тип всплывающего окна, описанного в перечислении Попуптипе. Для каждого набора всплывающих окон должно быть только одно всплывающее окно `root`.

**Тип**: `enum`

@No__t_0 значение является перечислением со следующими возможными значениями

|Value|Участник|
|--|--|
|1|Корневой|
|2|Вложенные|

### <a name="remarks"></a>Примечания

Для каждого набора всплывающих окон должен быть только один `Root` всплывающее окно.

### <a name="related-topics"></a>Связанные статьи

[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)