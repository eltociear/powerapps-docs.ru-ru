---
title: 'Для разработчиков: рекомендации по работе с метаданными в службе Common Data Service для приложений | Документация Майкрософт'
description: Рекомендации для разработчиков по работе с метаданными службы Common Data Service для приложений в PowerApps.
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
ms.openlocfilehash: 938d3ea2337137b1c78a1f4849191a261ac7a30a
ms.sourcegitcommit: 11486fb4c16095e3fef785126003cac3e3e06c0d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2019
ms.locfileid: "54271569"
---
# <a name="best-practices-and-guidance-while-working-with-metadata-for-the-common-data-service-for-apps"></a>Рекомендации по работе с метаданными в службе Common Data Service для приложений

В списке ниже приводятся все рекомендации по взаимодействию и работе с метаданными в службе Common Data Service для приложений.


|Рекомендация  |Описание  |
|---------|---------|
|[Получите опубликованные метаданные](retrieve-published-metadata.md)     |Извлечение неопубликованных метаданных может приводить не только к увеличению накладных расходов на обработку запроса, из-за чего снижается производительность, но и к предоставлению метаданных, которые не требуются запрашивающей стороне.         |
|[Получите конкретные столбцы для сущности с помощью API запросов](retrieve-specific-columns-entity-via-query-apis.md)     |Отправляемые запросы на получение данных должны содержать определенные столбцы в экземпляре ColumnSet, связанном с запросом, а не все столбцы.         |

# <a name="see-also"></a>См. также
[Работа с метаданными с помощью кода](../../metadata-services.md)<br />