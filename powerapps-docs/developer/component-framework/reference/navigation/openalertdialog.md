---
title: Опеналертдиалог | Документация Майкрософт
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
ms.assetid: 4acd3f17-74c0-4de1-9326-3778ff413f1e
ms.openlocfilehash: f1f5a2a78faf3dd9c6a1d6d197fab61772969084
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342514"
---
# <a name="openalertdialog"></a>openAlertDialog

[!INCLUDE [openalertdialog-description](includes/openalertdialog-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="syntax"></a>Синтаксис

`context.navigation.openAlertDialog(alertStrings, options)`

## <a name="parameters"></a>Вход

| Имя параметра|Тип|Требуется|Description|
| ------------- |----|--------|-----------|
|алертстрингс|`AlertDialogStrings`|Да|Строки, используемые в диалоговом окне предупреждения. Алертдиалогстрингс имеет следующие атрибуты:<br/>- **текст**: `string`. Сообщение, отображаемое в диалоговом окне предупреждения. <br/>- **конфирмбуттонлабел**: `string`. Метка кнопки подтверждения. Если вы не укажете метку кнопки, в качестве метки кнопки используется значение **ОК** (в предпочитаемом языке пользователя).|
|Параметры|`AlertDialogOptions`|Да|Параметры диалогового окна. Алертдиалогоптионс имеет следующие атрибуты:<br/>**высота**- : `number`. Высота диалогового окна предупреждения (в пикселях). <br/>**ширина**- : `number`. Ширина диалогового окна предупреждения в пикселях|

## <a name="return-value"></a>Возвращаемое значение

Тип: `Promise`

## <a name="remarks"></a>Примечания

См. статью о [обещании](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) и [файле](https://developer.mozilla.org/docs/Web/API/File)

## <a name="example"></a>Пример 

```TypeScript
context.navigation.openAlertDialog({text:"This is an alert.", confirmButtonLabel : "Yes",}).then(
        function success()
        {
            document.getElementById("openAlertDialogButton")!.innerHTML = "Alert dialog closed";
        },
        function()
        {
            document.getElementById("openAlertDialogButton")!.innerHTML = "Error in Alert Dialog";
        }
    );
```

### <a name="related-topics"></a>Связанные статьи

[Навигация](../navigation.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)