---
title: Опенеррордиалог | Документация Майкрософт
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
ms.assetid: 10c154b9-45a0-44ee-a621-73d6a9009c6d
ms.openlocfilehash: c3371b7c3ea8bde869acc261ab7d4fc8f28ba7da
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342445"
---
# <a name="openerrordialog"></a>openErrorDialog

[!INCLUDE [openerrordialog-description](includes/openerrordialog-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="syntax"></a>Синтаксис

`context.navigation.openErrorDialog(options)`

## <a name="parameters"></a>Вход

| Имя параметра|Тип|Требуется|Description|
| ------------- |----|--------|-----------|
|Параметры|`ErrorDialogOptions`|Да|Параметры диалогового окна "ошибка". Еррордиалогоптионс имеет следующие атрибуты: <br/>- **сведения**: `String`. Сведения об ошибке. При указании этого элемента в сообщении об ошибке появится кнопка **скачать файл журнала** , после чего пользователи смогут загрузить текстовый файл с содержимым, указанным в этом атрибуте.<br/>- **ErrorCode**: `Number`. Код ошибки. Если вы просто установили errorCode, сообщение для кода ошибки автоматически извлекается с сервера и отображается в диалоговом окне ошибки. Если задано значение **ErrorCode** , отображается диалоговое окно с сообщением об ошибке по умолчанию.<br/>- **сообщение**: `String`. Сообщение, отображаемое в диалоговом окне ошибки. Необходимо задать либо **код ошибки** , либо атрибут **сообщения** .|

## <a name="return-value"></a>Возвращаемое значение

Тип: `Promise`

## <a name="remarks"></a>Примечания

См. статью о [обещании](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) и [файле](https://developer.mozilla.org/docs/Web/API/File)


### <a name="related-topics"></a>Связанные статьи

[Навигация](../navigation.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)