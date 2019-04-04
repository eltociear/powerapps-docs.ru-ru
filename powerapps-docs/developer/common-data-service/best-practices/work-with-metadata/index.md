---
title: 'Для разработчиков: рекомендации по работе с метаданными в службе Common Data Service | Документация Майкрософт'
description: Рекомендации по работе с метаданными для разработчиков службы Common Data Service в PowerApps.
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/12/2018
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 35e07c87e515759a6e61a0c0a027c190b11bef53
ms.sourcegitcommit: 5b2b70c3fc7bcba5647d505a79276bbaad31c610
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58358019"
---
# <a name="best-practices-and-guidance-while-working-with-metadata-for-the-common-data-service"></a>Рекомендации по работе с метаданными в службе Common Data Service

В списке ниже приводятся все рекомендации по взаимодействию и работе с метаданными в службе Common Data Service.


|Рекомендация  |Описание  |
|---------|---------|
|[Получите опубликованные метаданные](retrieve-published-metadata.md)     |Извлечение неопубликованных метаданных может приводить не только к увеличению накладных расходов на обработку запроса, из-за чего снижается производительность, но и к предоставлению метаданных, которые не требуются запрашивающей стороне.         |
|[Получите конкретные столбцы для сущности с помощью API запросов](retrieve-specific-columns-entity-via-query-apis.md)     |Отправляемые запросы на получение данных должны содержать определенные столбцы в экземпляре ColumnSet, связанном с запросом, а не все столбцы.         |

# <a name="see-also"></a>См. также
[Работа с метаданными с помощью кода](../../metadata-services.md)<br />