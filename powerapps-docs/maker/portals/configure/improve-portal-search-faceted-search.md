---
title: Использование аспектного поиска для улучшения поиска на портале | MicrosoftDocs
description: Инструкции по включению или отключению поиска с аспектом.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6b605acf1d11ecbc98760810f390f63c9a27a0a6
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552343"
---
# <a name="use-faceted-search-to-improve-portal-search"></a>Использование аспектного поиска для улучшения поиска на портале

Для поиска содержимого портала можно использовать фильтры на основе характеристик содержимого. Фильтры, реализованные с помощью поиска на портале с различными аспектами, позволяют клиентам находить содержимое, которое они хотят быстрее, чем обычный поиск.

## <a name="enable-or-disable-faceted-search"></a>Включение или отключение поиска с аспектами

На порталах включен встроенный поиск с аспектом. Для управления или включения выполните следующие действия.

1. Откройте [приложение управления портала](configure-portal.md) и перейдите на **порталы** &gt; **веб-сайт** &gt; **Параметры сайта**.
2. Выберите параметр **поиска и фацетедвиев** сайта. 
3. Измените **значение** на **true** **, чтобы включить или отключить** Поиск с аспектом.

Чтобы отключить одну часть представления с аспектом, сделайте следующее:

1. Откройте [приложение управления портала](configure-portal.md) и перейдите на **порталы** &gt; **веб-шаблоны**.
2. Выберите представление для отключения (т. е. Управление знаниями — лучшие оценки статей)
3. В верхней части страницы выберите **Отключить** .

## <a name="group-entities-as-part-of-a-record-type-for-faceted-view"></a>Группирование сущностей как часть типа записи для представления с аспектами

Параметр сайта **Search/рекордтипефацетсентитиес** позволяет группировать аналогичные сущности, чтобы пользователи имели логические способы фильтрации результатов поиска. Например, вместо отдельных параметров для форумов, сообщений форума и обсуждений на форумах эти сущности группируются под типом записи форумов.

Перейдите на **порталы** &gt; **веб-сайты** &gt; **Параметры сайта** и откройте параметр **Поиск/рекордтипефацетсентитиес** сайта. 

Обратите внимание, что к различным сущностям предшествуют **форумы**по словам:. Это связано с тем, что первое значение — это имя, в котором они группируются как. Это слово будет переведено на основе языка, используемого на портале.

## <a name="use-faceted-search-to-improve-knowledge-search-results"></a>Использование аспектного поиска для улучшения результатов поиска по базе знаний

Поиск с аспектом позволяет порталам использовать фильтры поиска на самой левой стороне, позволяя выбирать элементы, такие как форумы, блоги и статьи базы знаний. Для конкретных типов поиска добавляются дополнительные фильтры. Например, статьи базы знаний можно фильтровать по типу записи, дате изменения, оценке и продуктам, чтобы помочь клиентам найти необходимое содержимое. У крайней правой стороны также есть раскрывающийся список, в котором результаты сортируются по выбору клиента и количеству представлений (относится к статьям базы знаний). Ниже приведен снимок экрана с примерами некоторых доступных фильтров.

![Использование фильтров для улучшения результатов поиска](../media/faceted-search-filter.png "Использование фильтров для улучшения результатов поиска")