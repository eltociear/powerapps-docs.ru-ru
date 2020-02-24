---
title: Использование операторов Liquid для портала | MicrosoftDocs
description: Узнайте о доступных операторах Liquid на портале.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 77561ee8ad31a7c2ab21162edbb08779627d1e65
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2020
ms.locfileid: "2981200"
---
# <a name="understand-liquid-operators"></a>Знакомство с операторами Liquid

Liquid имеет доступ ко все распространенным логические операторам и операторам сравнения. Они могут использоваться в таких тегах, как **if** и **unless**.

## <a name="basic-operators"></a>Базовые операторы

| ==    | Равно                          |
|-------|---------------------------------|
| !=    | не равно                  |
| &gt;  | Больше                    |
| &lt;  | Меньше                       |
| &gt;= | Больше или равно        |
| &lt;= | Меньше или равно           |
| или    | Условие A **или** условие B  |
| и   | Условие A **и** условие B |

## <a name="contains"></a>содержит

contains проверяет наличие подстроки в строке.

```
{% if page.title contains 'Product' %}

The title of this page contains the word Product.

{% endif %}
```

contains также может проверить присутствия строки в массиве строк.

## <a name="startswith"></a>startswith

startswith проверяет, начинается ли строка с указанной подстроки.

```
{% if page.title startswith 'Profile' %}

This is a profile page.

{% endif %}
```

## <a name="endswith"></a>заканчивается на

endswith проверяет, заканчивается ли строка указанной подстрокой.

```
{% if page.title endswith 'Forum' %}

This is a forum page.

{% endif %}
```

### <a name="see-also"></a>См. также

[Сохранение содержимого источника с помощью веб-шаблонов](store-content-web-templates.md)  
[Типы Liquid](liquid-types.md)  
[Условный](liquid-conditional-operators.md)  
[Объекты Liquid](liquid-objects.md)  
[Теги Liquid](liquid-tags.md)  
[Фильтры Liquid](liquid-filters.md) 