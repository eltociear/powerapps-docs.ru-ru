---
title: Форматтиме | Документация Майкрософт
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
ms.assetid: 148964b5-106e-4f2e-8038-9086d29dc54f
ms.openlocfilehash: cc2c7dfdbe9952d69dcda9fdd4c813965f539478
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343342"
---
# <a name="formattime"></a>formatTime

[!INCLUDE [formattime-description](includes/formattime-description.md)]

## <a name="syntax"></a>Синтаксис

`context.formatting.formatTime(value, behavior);`

## <a name="available-for"></a>Доступно для 

Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия)

## <a name="parameters"></a>Вход

| Имя параметра|Тип|Требуется|Description|
| ------------- |----|--------|-----------|
|value|`Date`|Да|Дата для форматирования.|
|Неполадок|`DateTimeFieldBehavior`|Да|Поведение форматируемого объекта DateTime. @No__t_0 имеет следующие атрибуты:<br/>-  `None =0`: неизвестное поведение DateTime <br/>-  `UserLocal =1`: соблюдение местного времени пользователя. Даты хранятся в формате UTC<br/>-  `TimeZoneIndependent =3`: даты и время, сохраненные без преобразования в UTC|

## <a name="return-value"></a>Возвращаемое значение

Тип: `string`


### <a name="related-topics"></a>Связанные статьи

[Форматирование](../formatting.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)