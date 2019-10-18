---
title: Пиккфиле | Документация Майкрософт
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
ms.assetid: aae27c64-33c4-47f1-b833-4c04161c01e2
ms.openlocfilehash: a36731edc7ee5cc8edede499fc791595bc00bc8c
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72344630"
---
# <a name="pickfile"></a>pickFile

[!INCLUDE[./includes/pickfile-description.md](./includes/pickfile-description.md)]

## <a name="syntax"></a>Синтаксис

`context.device.pickFile(options)`

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="parameters"></a>Вход

| Имя параметра|Тип|Требуется|Description|
| ------------- |----|--------|-----------|
|`options`|`Object`|Нет|Параметры для выбора файла.|

## <a name="return-value"></a>Возвращаемое значение

Тип: `Promise<FileObject[]>`

См. статью о [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) и [FileObject](../fileobject.md)

## <a name="remarks"></a>Примечания

Объект параметра `options` имеет следующие свойства:

|Имя|Тип|Description|
|--|--|--|
|`accept`|`String`|Типы файлов изображений для выбора. Допустимые значения: *аудио*, *видео*или *изображение*.|
|`allowMultipleFiles`|`Boolean`|Указывает, следует ли разрешить выбор нескольких файлов|
|`maximumAllowedFileSize`|`Number`|Максимальный размер выбранных файлов|


### <a name="related-topics"></a>Связанные статьи

[Модем](../device.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)