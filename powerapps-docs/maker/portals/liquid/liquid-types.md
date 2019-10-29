---
title: Использование типов жидкостей для портала | MicrosoftDocs
description: Сведения о доступных типах ликвидности на портале.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: dd6da4788f6563c2026f57914c8156caedfadad3
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974950"
---
# <a name="available-liquid-types"></a>Доступные типы Liquid

Объекты жидкости могут возвращать один из семи базовых типов: **String**, **Number**, **Boolean**, **массив**, **Dictionary**, **DateTime**или **null**. Переменные ликвидности можно инициализировать с помощью тегов **Assign** или **Capture** .

## <a name="string"></a>Строка

Строка объявляется с помощью переноса текста в одинарные или двойные кавычки.

```
{% assign string_a = Hello World! %}

{% assign string_b = 'Single quotes work too.' %}
```

Возвращает число символов в строке с помощью свойства Size.

```
{{ string_a.size }} <!-- Output: 12 -->
```

## <a name="number"></a>Номер

Числа могут быть целыми числами или числом с плавающей запятой.

```
{% assign pi = 3.14 %}

{% if page.title.size > 100 %}

This page has a long title.

{% endif %}
```

## <a name="boolean"></a>Логическое значение

Логическое значение — true или false.

```
{% assign x = true %}

{% assign y = false %}

{% if x %}

This will be rendered, because x is true.

{% endif %}
```

## <a name="array"></a>inArray

Массив содержит список значений любого типа. Можно получить доступ к заданному элементу (от нуля) с помощью \[ \], выполнить итерацию по ним с помощью **тега for**и получить количество элементов в массиве с помощью свойства Size.

```
{% for view in entitylist.views %}

{{ view.name }}

{% endfor %}

{{ entitylist.views[0] }}

{% if entitylist.views.size > 0 %}

This entity list has {{ entitylist.views.size }} views.

{% endif %}
```

## <a name="dictionary"></a>Словаря

Словари содержат коллекцию значений, доступ к которым можно получить с помощью строкового ключа. Можно получить доступ к заданному элементу по строковому ключу с помощью \[ \], выполнить итерацию по ним с помощью **тега for**и получить количество элементов в словаре с помощью свойства Size.

```
{{ request.params[ID] }}

{% if request.params.size > 0 %}

The request parameters collection contains some items.

{% endif %}
```

## <a name="datetime"></a>Дата и время

Объект DateTime представляет определенные дату и время.

```
{{ page.modifiedon | date: 'f' }}
```

## <a name="null"></a>Заканчивающ

NULL представляет пустое или несуществующее значение. Все выходы, пытающиеся вернуть значение null, ничего не отображают. В условиях он будет считаться ложным.

```
{% if request.params[ID] %}

This will render if the ID request parameter is NOT null.

{% endif %}
```

### <a name="see-also"></a>См. также

[Хранение исходного содержимого с помощью веб-шаблонов](store-content-web-templates.md)  
[Общие сведения об операторах жидкостей](liquid-operators.md)  
[Условие](liquid-conditional-operators.md)  
[Объекты жидкостей](liquid-objects.md)  
[Теги жидкостей](liquid-tags.md)  
[Фильтры жидкостей](liquid-filters.md)  