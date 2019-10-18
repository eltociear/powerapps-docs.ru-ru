---
title: Жетентитиметадата | Документация Майкрософт
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
ms.assetid: 6a334af7-ca5b-449c-b90f-0901824654d2
ms.openlocfilehash: 89dc2e9d567b8ff38c41df2074d2a85d6bcaf467
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340973"
---
# <a name="getentitymetadata"></a>getEntityMetadata

[!INCLUDE [getentitymetadata-description](includes/getentitymetadata-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="syntax"></a>Синтаксис

`context.utils.getEntityMetadata(entityName, attributes)`

## <a name="parameters"></a>Вход

| Имя параметра|Тип|Требуется|Description|
| ------------- |----|--------|-----------|
|entityName|`String`|Да|Логическое имя сущности.|
|Атрибута|`String[]`|Нет|Атрибуты, для которых необходимо получить метаданные.|

## <a name="return-value"></a>Возвращаемое значение

Тип: `Promise<EntityMetadata>`


### <a name="related-topics"></a>Связанные статьи

[Utility](../utility.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)