---
title: Сетфуллскрин | Документация Майкрософт
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
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 1faf3e79-969e-4c1e-ac01-8e2155c609fa
ms.openlocfilehash: b7fb38bcb0102356d8d1ea2540edf0dd1f845cbd
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342629"
---
# <a name="setfullscreen"></a>setFullScreen

[!INCLUDE [setfullscreen-description](includes/setfullscreen-description.md)]

## <a name="syntax"></a>Синтаксис

`context.mode.setControlState(mode);`

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="parameters"></a>Вход

| Имя параметра|Тип|Требуется|Description|
| ------------- |----|--------|-----------|
|value|`Boolean`|Да|`True`, если компоненту необходимо автоматическое масштабирование до полного экрана. `False`, если компоненту требуется автоматическое масштабирование до выделенной ширины.|


### <a name="related-topics"></a>Связанные статьи

[Mode](../mode.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)