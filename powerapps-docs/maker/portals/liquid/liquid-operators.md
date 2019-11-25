---
title: Использование операторов Liquid для портала | MicrosoftDocs
description: Узнайте о доступных операторах Liquid на портале.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 4a27a5364a4ae12fecc3a72dbb52115e415dcdb8
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "2708190"
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