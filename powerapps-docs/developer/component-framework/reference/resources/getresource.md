---
title: Ресурс | Документация Майкрософт
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
ms.assetid: 5c04ba7c-acfe-4375-8dd8-6c537ded9352
ms.openlocfilehash: 919606c7b6669265a8bdd4f7b43080564e87a80f
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341410"
---
# <a name="getresource"></a>getResource

[!INCLUDE [getresource-description](includes/getresource-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="syntax"></a>Синтаксис

`context.resources.getResource(id, success, failure)`

## <a name="parameters"></a>Вход

| Имя параметра|Тип|Требуется|Description|
| ------------- |----|--------|-----------|
|Id|`String`|Да|Идентификатор строки ресурса.|
|Загрузоч|`String`|Нет|Обратный вызов успешного выполнения. Данные ресурсов возвращаются в формате с кодировкой Base 64.|
|Состояние|`String`|Нет|Обратный вызов при сбое.|


### <a name="related-topics"></a>Связанные статьи

[Resources](../resources.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)