---
title: Жеттимезонеоффсетминутес | Документация Майкрософт
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
ms.assetid: 86290d20-7dbb-4932-adaa-31121ae7a3f6
ms.openlocfilehash: bc621299b19b1387225b8532ee03ff65e0e6471f
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341019"
---
# <a name="gettimezoneoffsetminutes"></a>жеттимезонеоффсетминутес

[!INCLUDE [gettimezoneoffsetminutes-description](includes/gettimezoneoffsetminutes-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="syntax"></a>Синтаксис

`context.usersettings.getTimeZoneOffsetMinutes(date)`

## <a name="parameters"></a>Вход

| Имя параметра|Тип|Требуется|Description|
| ------------- |----|--------|-----------|
|Дата|`Date`|Да|Дата для получения смещения относительно времени в формате UTC.|

## <a name="return-value"></a>Возвращаемое значение

Тип: `Number` Description: смещение часового пояса в минутах.


### <a name="related-topics"></a>Связанные статьи

[Параметры пользователя](../usersettings.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)