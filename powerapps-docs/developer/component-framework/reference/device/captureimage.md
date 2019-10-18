---
title: Каптуреимаже | Документация Майкрософт
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
ms.assetid: 1d9c0063-add2-4002-acab-1be07ca1f6b6
ms.openlocfilehash: e642af17e02334b45041df87386885536e1810af
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345688"
---
# <a name="captureimage"></a>captureImage

[!INCLUDE[./includes/captureimage-description.md](./includes/captureimage-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="syntax"></a>Синтаксис

`context.device.captureImage(options)`

## <a name="parameters"></a>Вход

| Имя параметра|Тип|Требуется|Description|
| ------------- |----|--------|-----------|
|`options`|`Object`|Нет|Параметры для записи образа.|

## <a name="return-value"></a>Возвращаемое значение

Тип: `Promise<FileObject>`

См. статью о [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) и [FileObject](../fileobject.md)

## <a name="remarks"></a>Примечания

Объект параметра `options` имеет следующие свойства:

|Имя|Тип|Description|
| ---|----|-----------|
|`allowEdit`|`Boolean`|Указывает, следует ли редактировать образ перед сохранением.|
|`height`|`Number`|Высота изображения для записи.|
|`preferFrontCamera`|`Boolean`|Указывает, следует ли записывать изображение, используя переднюю камеру устройства.|
|`quality`|`Number`|Качество файла изображения в процентах.|
|`width`|`Number`|Ширина изображения для записи.|


### <a name="related-topics"></a>Связанные статьи

[Модем](../device.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)