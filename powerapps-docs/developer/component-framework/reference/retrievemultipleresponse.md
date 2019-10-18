---
title: Ретриевемултиплереспонсе | Документация Майкрософт
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
ms.assetid: 08ea66d3-b4af-44af-a3ae-cb2ebad043e8
ms.openlocfilehash: 0e5b2cad047bcf91b0c63e27c4a7ceb35c1ed538
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341318"
---
# <a name="retrievemultipleresponse"></a>ретриевемултиплереспонсе

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="properties"></a>Свойства

### <a name="entities"></a>Объектах

Массив объектов JSON, где каждый объект представляет извлеченную запись сущности, содержащую атрибуты и их значения.

**Тип**: `Entity[]`

### <a name="nextlink"></a>nextLink

Если количество извлекаемых записей превышает значение, указанное в параметре `maxPageSize` в запросе, этот атрибут возвращает URL-адрес для возврата следующего набора записей.

**Тип**: `string`


### <a name="related-topics"></a>Связанные статьи

[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)