---
title: Использование операторов Liquid для портала | Документация Майкрософт
description: Узнайте о доступных операторах Liquid на портале.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
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