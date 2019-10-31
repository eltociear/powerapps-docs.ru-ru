---
title: Использование условных операторов Liquid для портала | Документация Майкрософт
description: Узнайте о доступных условных операторах Liquid на портале.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="available-liquid-conditional-operators"></a>Доступные условные операторы Liquid

При использовании в условных операторах (**if**, **unless**) некоторые значения Liquid считаются истинными значениями (true), а другие значения обрабатываются как ложные значения (false).

В Liquid null и логическое значение false рассматриваются как ложные значения; все остальные значения считаются истинными (true). Пустые строки, пустые массивы и т. д. считаются истинными значениями (true). Например,

```
{% assign empty_string =  %}
{% if empty_string %}
<p>This will render.</p>
{% endif %}
```
Если требуется, можно проверять пустые строки и массивы с помощью специального пустого значения.

```
{% unless page.title == empty %}
<h1>{{ page.title }}</h1>
{% endunless %}
```
Размер [типы Liquid](liquid-types.md), [типы Liquid](liquid-types.md) или [типы Liquid](liquid-types.md) можно проверить с помощью специального свойства.

```
{% if page.children.size > 0 %}
<ul>
{% for child in page.children %}
<li>{{ child.title }}</li>
{% endfor %}
</ul>
{% endif %}
```

## <a name="summary"></a>Сводка

|                           | True | False |
|---------------------------|------|-------|
| True                      | ×    |       |
| False                     |      | ×     |
| Null                      |      | ×     |
| String                    | ×    |       |
| пустая строка              | ×    |       |
| 0                         | ×    |       |
| 1, 3,14                   | ×    |       |
| массив или словарь       | ×    |       |
| пустой массив или словарь | ×    |       |
| Объект                    | ×    |       |

### <a name="see-also"></a>См. также

[Сохранение содержимого источника с помощью веб-шаблонов](store-content-web-templates.md)  
[Знакомство с операторами Liquid](liquid-operators.md)  
[Типы Liquid](liquid-types.md)  
[Объекты Liquid](liquid-objects.md)  
[Теги Liquid](liquid-tags.md)  
[Фильтры Liquid](liquid-filters.md)  
