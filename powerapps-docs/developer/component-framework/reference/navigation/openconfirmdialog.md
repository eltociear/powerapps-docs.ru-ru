---
title: Опенконфирмдиалог | Документация Майкрософт
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
ms.assetid: 83f2c208-696c-48b1-b65c-2ba7374d6cfc
ms.openlocfilehash: 8b7bda89b9c8d83614a4a95281853676db9cf568
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342491"
---
# <a name="openconfirmdialog"></a>openConfirmDialog

[!INCLUDE [openconfirmdialog-description](includes/openconfirmdialog-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="syntax"></a>Синтаксис

`context.navigation.openConfirmDialog(confirmStrings, options)`

## <a name="parameters"></a>Вход

| Имя параметра|Тип|Требуется|Description|
| ------------- |----|--------|-----------|
|конфирмстрингс|`ConfirmDialogStrings`|Да|Строки, используемые в диалоговом окне. Конфирмдиалогстрингс имеет следующие атрибуты:<br/>**заголовок**- : `String`. Заголовок, отображаемый в диалоговом окне подтверждения. <br/>**подзаголовок**- : `String`. Подзаголовок, который будет использоваться в диалоговом окне подтверждения.<br/>- **текст**: `String`. Сообщение, отображаемое в диалоговом окне подтверждения.<br/>- **конфирмбуттонлабел**: `String`. Метка кнопки подтверждения. Если вы не укажете метку кнопки, в качестве метки кнопки используется значение **ОК** (в предпочитаемом языке пользователя).<br/>- **значение cancelbuttonlabel как**: `String` метку кнопки отмены. Если вы не укажете метку кнопки "Отмена", в качестве метки кнопки используется **Cancel** .|
|Параметры|`ConfirmDialogOptions`|Нет|Параметры для диалогового окна. Конфирмдиалогоптионс имеет следующие атрибуты:<br/>**высота**- : `Number`. Высота диалогового окна подтверждения (в пикселях). <br/>**ширина**- : `Number`. Ширина диалогового окна подтверждения в пикселях|

## <a name="return-value"></a>Возвращаемое значение

Тип: `Promise<ConfirmDialogResponse>`

Описание: Возвращает объект с заданным атрибутом (Boolean), который указывает, была ли нажата кнопка подтверждения для закрытия диалогового окна.

## <a name="remarks"></a>Примечания

См. статью о [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) 


### <a name="related-topics"></a>Связанные статьи

[Навигация](../navigation.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)