---
title: Элемент RESX | Документация Майкрософт
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
ms.assetid: 38acfda3-4adc-4aa2-bb8b-f29ba572a6e5
ms.openlocfilehash: 29c89541c2519b36559ab49d2b0483f19b545573
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346033"
---
# <a name="resx-element"></a>элемент RESX

[!INCLUDE [resx-description](includes/resx-description.md)]

## <a name="available-for"></a>Доступно для

Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия)

## <a name="attributes"></a>Атрибуты

|Имя|Description|Тип|Требуется|
|--|--|--|--|
|`path`|Относительный путь w. r. t манифест, где находятся файлы RESX|`string`|Да|
|`version`|Текущая версия файла RESX|`string`|Да|

## <a name="parent-elements"></a>Родительские элементы

|Элемент|Description|
|--|--|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

## <a name="example"></a>Пример

```xml
<resources>
      <code path="TS_LocalizationAPI.js" order="1" />
        <css path="css/TS_LocalizationAPI.css" order="1" />
      <resx path="strings/TSLocalizationAPI.1033.resx" version="1.0.0" />
      <resx path="strings/TSLocalizationAPI.1035.resx" version="1.0.0" />
      <resx path="strings/TSLocalizationAPI.3082.resx" version="1.0.0" />
    </resources>
```

### <a name="related-topics"></a>Связанные статьи

[Справочник по схеме манифеста платформы компонентов PowerApps](index.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)
