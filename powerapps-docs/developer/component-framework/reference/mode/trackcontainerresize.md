---
title: Траккконтаинерресизе | Документация Майкрософт
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
ms.assetid: c5f482c2-dde2-460b-89a7-39e0efcc5704
ms.openlocfilehash: 8f9bc1ef17bdcb762e992d9f77dcdcd7ba1e8c50
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342560"
---
# <a name="trackcontainerresize"></a>trackContainerResize

[!INCLUDE [trackcontainerresize-description](includes/trackcontainerresize-description.md)].

Если родительский контекст, в котором размещается компонент, предоставляет ограничение на высоту в приложениях, управляемых моделью, то оно правильно применяется к дочернему компоненту. Однако в большинстве случаев родительский контекст не ограничивает высоту компонента, поэтому он получает «-1», чтобы показать, что он может расти дальше.

В приложениях Canvas родительский контекст всегда предоставляет компоненту высоту и ширину по природе редактора перетаскивания.

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="syntax"></a>Синтаксис

`context.mode.trackContainerResize(value)`

## <a name="parameters"></a>Вход

| Имя параметра|Тип|Требуется|Description|
| ------------- |----|--------|-----------|
|value|`Boolean`|Да|`True`, если элементам управления требуется отслеживание размера контейнера, компонент получит Аллокатедвидс или Аллокатедхеигхт.|


### <a name="related-topics"></a>Связанные статьи

[Mode](../mode.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)
