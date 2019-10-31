---
title: Использование типов Liquid для портала | Документация Майкрософт
description: Узнайте о доступных типах Liquid на портале.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="available-liquid-types"></a>Доступные типы Liquid

Объекты Liquid могут возвращать один из основных 7 типов: **String**, **Number**, **Boolean**, **Array**, **Dictionary**, **DateTime** или **Null**. Переменные Liquid могут инициализировать с помощью тегов **assign** или **capture**.

## <a name="string"></a>String

Строка объявляется путем заключения текста в одинарные или двойные кавычки.

```
{% assign string_a = Hello World! %}

{% assign string_b = 'Single quotes work too.' %}
```

Число знаков в строке можно получить с помощью свойства size.

```
{{ string_a.size }} <!-- Output: 12 -->
```

## <a name="number"></a>Число

Числа могут быть целыми или с плавающей запятой.

```
{% assign pi = 3.14 %}

{% if page.title.size > 100 %}

This page has a long title.

{% endif %}
```

## <a name="boolean"></a>Boolean

Логическое значение может быть истинным или ложным.

```
{% assign x = true %}

{% assign y = false %}

{% if x %}

This will be rendered, because x is true.

{% endif %}
```

## <a name="array"></a>Массив

Массив содержит список значений любого типа. Можно получить доступ к определенному элементу по индексу (с отсчетом с нуля) с помощью \[ \], выполнять итерации по элементам с помощью **тега for** и получать количество элементов в массиве с помощью свойства size.

```
{% for view in entitylist.views %}

{{ view.name }}

{% endfor %}

{{ entitylist.views[0] }}

{% if entitylist.views.size > 0 %}

This entity list has {{ entitylist.views.size }} views.

{% endif %}
```

## <a name="dictionary"></a>Словарь

Словари содержат коллекцию значений, к которым можно получить доступ с помощью ключа строки. Можно получить доступ к определенному элементу по ключу строки с помощью \[ \], выполнять итерации по элементам с помощью **тега for** и получать количество элементов в словаре с помощью свойства size.

```
{{ request.params[ID] }}

{% if request.params.size > 0 %}

The request parameters collection contains some items.

{% endif %}
```

## <a name="datetime"></a>Дата и время

Объект DateTime представляет определенную дату и время.

```
{{ page.modifiedon | date: 'f' }}
```

## <a name="null"></a>Null

NULL представляет пустое или несуществующее значение. Все выходные данные, которые пытаются вернуть значение NULL, не отображают ничего. В условиях это значение обрабатывается как ложное.

```
{% if request.params[ID] %}

This will render if the ID request parameter is NOT null.

{% endif %}
```

### <a name="see-also"></a>См. также

[Сохранение содержимого источника с помощью веб-шаблонов](store-content-web-templates.md)  
[Знакомство с операторами Liquid](liquid-operators.md)  
[Условный](liquid-conditional-operators.md)  
[Объекты Liquid](liquid-objects.md)  
[Теги Liquid](liquid-tags.md)  
[Фильтры Liquid](liquid-filters.md)  