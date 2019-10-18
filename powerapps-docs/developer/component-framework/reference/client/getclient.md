---
title: Клиент | Документация Майкрософт
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
ms.assetid: 4b7c18f8-cd00-4f39-8f88-ed9306d6a055
ms.openlocfilehash: 503d24d97061548132f912351a58fbce68082d18
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345757"
---
# <a name="getclient"></a>getClient

[!INCLUDE [getclient-description](includes/getclient-description.md)]

## <a name="syntax"></a>Синтаксис

`context.client.getClient()`

## <a name="available-for"></a>Доступно для 

Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия) 



## <a name="return-value"></a>Возвращаемое значение

Тип: `String`

Возвращает значение, указывающее, в каком клиенте выполняется скрипт.

|||
|-----|-----|
|Интернет| Веб-приложение или унифицированный интерфейс|
|Outlook 2013| Outlook 2013|
|сети| Мобильное приложение|



### <a name="related-topics"></a>Связанные статьи

[Клиент](../client.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)