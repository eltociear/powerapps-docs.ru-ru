---
title: Опенвебресаурце | Документация Майкрософт
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
ms.assetid: 27a1e54c-71fe-450f-8f84-b4cc125970bf
ms.openlocfilehash: 577c26dd87149fabebafe32b77395029ef4df335
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342261"
---
# <a name="openwebresource"></a>openWebResource

[!INCLUDE [openwebresource-description](includes/openwebresource-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="syntax"></a>Синтаксис

`context.navigation.openWebResource(name, options, data)`

## <a name="parameters"></a>Вход

| Имя параметра|Тип|Требуется|Description|
| ------------- |----|--------|-----------|
|Безымян|`String`|Да|Имя открываемого веб-ресурса HTML.|
|Параметры|`OpenWebResourceOptions`|Нет|Параметры окна для открытия веб-ресурса. Опенвебресаурцеоптионс имеет следующие атрибуты:<br/>**высота**- : `Number`. Высота окна для вывода итоговой страницы в пикселях.<br/>**ширина**- : `Number`. Ширина окна для вывода итоговой страницы в пикселях.<br/>- **опенинневвиндов**: `Boolean`. Указывает, следует ли открывать веб-ресурс в новом окне.|
|Data|`String`|Нет|Данные, передаваемые в параметр данных.

### <a name="related-topics"></a>Связанные статьи

[Навигация](../navigation.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)