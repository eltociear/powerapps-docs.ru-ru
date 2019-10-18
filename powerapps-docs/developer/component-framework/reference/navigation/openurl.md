---
title: openUrl | Документация Майкрософт
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
ms.assetid: 590078f3-c604-4bd0-ac74-9cf6d8806802
ms.openlocfilehash: 21e097c739364b6cdb3935654ae9bf2b61143a06
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342284"
---
# <a name="openurl"></a>openUrl

[!INCLUDE [openurl-description](includes/openurl-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="syntax"></a>Синтаксис

`context.navigation.openUrl(url, options)`

## <a name="parameters"></a>Вход

| Имя параметра|Тип|Требуется|Description|
| ------------- |----|--------|-----------|
|URL-адрес|`string`|Да|URL-адрес для открытия.|
|Параметры|`OpenUrlOptions`|Нет|Параметры для открытия URL-адреса. Опенурлоптионс имеет следующие параметры: <br/>**высота**- : `Number`. Высота окна для вывода итоговой страницы в пикселях.<br/>**ширина**- : `Number`. Ширина окна для вывода итоговой страницы в пикселях.|


### <a name="related-topics"></a>Связанные статьи

[Навигация](../navigation.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)