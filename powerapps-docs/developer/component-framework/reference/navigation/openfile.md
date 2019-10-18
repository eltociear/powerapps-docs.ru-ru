---
title: openFile | Документация Майкрософт
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
ms.assetid: ae94e467-d12c-4a74-96f0-05a09e03c5f8
ms.openlocfilehash: 5de6eefb37450fde50127829f2a922252d08a4fb
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342698"
---
# <a name="openfile"></a>openFile

[!INCLUDE [openfile-description](includes/openfile-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="syntax"></a>Синтаксис

`context.navigation.openFile(file, options)`

## <a name="parameters"></a>Вход

| Имя параметра|Тип|Требуется|Description|
| ------------- |----|--------|-----------|
|File|`FileObject`|Да|Объект, описывающий открываемый файл. Объект FileObject имеет следующие атрибуты: <br/>- **филеконтент**: `String`. Содержимое файла. <br/>- **имя файла**: `String`. Имя файла.<br/>- **Размер файла**: `Number`. Размер файла в КБ. <br/>- **MIMEType**: `String`. Тип MIME файла.|
|Параметры|`Object`|Нет|Объект, описывающий, следует ли открывать или сохранять файл. Объект имеет следующий атрибут: <br/>- **openMode**: укажите 1, чтобы открыть. 2 для сохранения. 
Если этот параметр не указан, то по умолчанию передается значение 1 (открыть). Этот параметр поддерживается только в едином интерфейсе.|

## <a name="return-value"></a>Возвращаемое значение

Тип: `Promise`

## <a name="remarks"></a>Примечания

См. статью о [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) и [FileObject](../fileobject.md)


### <a name="related-topics"></a>Связанные статьи

[Навигация](../navigation.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)