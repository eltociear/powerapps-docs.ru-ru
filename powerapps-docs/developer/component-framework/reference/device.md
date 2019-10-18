---
title: Устройство | Документация Майкрософт
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
ms.assetid: a0f9abc5-c605-4433-bf5a-f8253eeeda3b
ms.openlocfilehash: 0558004b889df59c168cfe9bdcfc7b5b5414fc02
ms.sourcegitcommit: b8148ec3324b7ffed9fa5a28ea1f4df7e444a081
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72347344"
---
# <a name="device"></a>Модем

[!INCLUDE [device-description](includes/device-description.md)]

> [!IMPORTANT]
> Если вы хотите использовать методы API устройства, необходимо объявить использование этих методов в узле " [Использование компонентов](../manifest-schema-reference/feature-usage.md) " в файле манифеста.

## <a name="syntax"></a>Синтаксис

`context.device`

## <a name="available-for"></a>Доступно для 

Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия)

## <a name="methods"></a>Метод

|Method | Description |
| ------------- |-------------|
|[каптуреаудио](device/captureaudio.md)|[!INCLUDE [captureaudio-description](device/includes/captureaudio-description.md)]|
|[каптуреимаже](device/captureimage.md)|[!INCLUDE [captureimage-description](device/includes/captureimage-description.md)]|
|[каптуревидео](device/capturevideo.md)|[!INCLUDE [capturevideo-description](device/includes/capturevideo-description.md)]|
|[жетбаркодевалуе](device/getbarcodevalue.md)|[!INCLUDE [getbarcodevalue-description](device/includes/getbarcodevalue-description.md)]|
|[жеткуррентпоситион](device/getcurrentposition.md)|[!INCLUDE [getcurrentposition-description](device/includes/getcurrentposition-description.md)]|
|[пиккфиле](device/pickfile.md)|[!INCLUDE [pickfile-description](device/includes/pickfile-description.md)]|

### <a name="related-topics"></a>Связанные статьи

[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)