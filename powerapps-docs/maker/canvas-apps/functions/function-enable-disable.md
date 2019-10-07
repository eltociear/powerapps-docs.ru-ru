---
title: Функции Enable и Disable | Документация Майкрософт
description: Справочные сведения о функциях Enable и Disable в PowerApps, включая описание синтаксиса и примеры.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1b58b57ae880f54fc7fccb5aa4c49f0e2fcad6d0
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992764"
---
# <a name="enable-and-disable-functions-in-powerapps"></a>Функции Enable и Disable в PowerApps
Включает или отключает [сигнал](signals.md).

## <a name="overview"></a>Обзор
Некоторые сигналы могут часто изменяться, при этом требуется, чтобы приложение выполняло повторное вычисление.  Частые изменения в течение длительного периода времени могут привести к разрядке батареи устройства. Эти функции можно использовать, чтобы вручную включать или отключать сигнал.

Когда сигнал не используется, он автоматически отключается.

## <a name="description"></a>Описание
Функции **Enable** и **Disable** включают и отключают сигнал соответственно.

В настоящее время эти функции работают только для сигнала **[Location](signals.md)** .

Эти функции не возвращают никаких значений. Их можно использовать только в [формулах поведения](../working-with-formulas-in-depth.md).

## <a name="syntax"></a>Синтаксис
**Enable**( *Сигнал* )<br>**Disable**( *Сигнал* )

* *Сигнал* — обязательный аргумент.  Сигнал, который необходимо включить или отключить.

