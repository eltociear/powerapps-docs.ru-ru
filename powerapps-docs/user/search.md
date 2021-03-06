---
title: Варианты поиска в Common Data Service | Документация Майкрософт
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 1/27/2020
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 440241571f716fa1931b5c11935c70de5c85e7ee
ms.sourcegitcommit: 5bfd0448f1d5ca3d938e3bd928d1dd3d4042afff
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/28/2020
ms.locfileid: "76828599"
---
# <a name="compare-search-options-in-common-data-service"></a>Сравнение вариантов поиска в Common Data Service

Существует три способа поиска записей в Common Data Service.

-   Поиск с сортировкой по релевантности   
  
-   Быстрый поиск (с одной сущностью или несколькими)  

-   Расширенный поиск

> [!NOTE]
> Быстрый поиск с несколькими сущностями также называется поиском по категориям. 
  
В таблице ниже содержится краткое сравнение трех доступных вариантов.

|Функции|[Поиск с сортировкой по релевантности](relevance-search.md)|[Быстрый поиск](quick-find.md)|[Расширенный поиск](advanced-find.md)|  
|-------------------|---------------------------|----------------|-------------------|  
|Включен по умолчанию?|Нет. Администратор должен вручную включить его.|Да|Да|  
|Область поиска по одной сущности|Недоступно в сетке сущностей. Результаты поиска можно отфильтровать по сущности на странице результатов.|Доступно в сетке сущностей.|Доступно в сетке сущностей.|  
|Область поиска по нескольким сущностям|Максимальное количество сущностей, которые можно искать, неограниченно. **Примечание.**  Хотя максимальное количество сущностей, которые можно найти, неограниченно, фильтр типа записи отображает данные только для 10 сущностей.|Поиск поддерживает до 10 сущностей, сгруппированных по сущности.|Поиск по нескольким сущностям недоступен.|  
|Поведение поиска|Находит совпадения с любым словом в поисковом выражении в любом поле сущности.|Находит совпадения со всеми словами в поисковом выражении в одном поле сущности; при этом слова в поле могут быть сопоставлены в любом порядке.|Построитель запросов, в котором можно определить условия поиска для выбранного типа записи. Также может использоваться для подготовки данных для экспорта в Office Excel с целью анализа, суммирования или агрегирования данных или создания сводных таблиц для просмотра данных с разных точек зрения.|  
|Поля для поиска|Текстовые поля, такие как одиночная строка текста, несколько строк текста, уточняющие запросы и наборы параметров. Поиск в полях с типом данных "число" или "дата" не поддерживается.|Все поля для поиска.|Все поля для поиска.|  
|Результаты поиска|Возвращает результаты поиска, отсортированные по релевантности, в одном списке.|Для одной сущности возвращает результаты поиска в сетке сущности. Для нескольких сущностей возвращает результаты поиска, сгруппированные по категориям, например учетные записи, контакты или интересы.|Возвращает результаты поиска выбранного типа записи с указанными столбцами в настроенном порядке сортировки.|
|Подстановочные знаки (*)|Конечный подстановочный знак, поддерживаемый для завершения слов.|Поддерживается начальный подстановочный знак. Подстановочный знак в конце добавляется по умолчанию.|Не поддерживается.|  
