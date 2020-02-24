---
title: Использование тегов итерации для портала | Документация Майкрософт
description: Сведения о различных тегах итерации, доступных на портале
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 3240b06c54b24778a8327d403a36902a3b3e0da4
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980760"
---
# <a name="iteration-tags"></a>Теги итерирования

Теги итерирования используются для многократного выполнения или обработки блока кода.

## <a name="for"></a>для

Многократное выполнение блока кода. Наиболее часто используется для повторения с элементами массива или словаря.

В блоке тега for доступен [объект forloop](liquid-objects.md#forloop).  

**Код**

```
{% for child_page in page.children %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Вывод**

```
<a href=/parent/child1/>Child 1</a>

<a href=/parent/child2/>Child 2</a>

<a href=/parent/child3/>Child 3</a>
```

### <a name="parameters"></a>Параметры

Эти параметры для тега for можно использовать самостоятельно или в сочетании.

**limit**

Выход из цикла после заданного числа элементов.

**Код**

```
{% for child_page in page.children limit:2 %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Вывод**

```
<a href=/parent/child1/>Child 1</a>

<a href=/parent/child2/>Child 2</a>
```

**offset**

Запуск цикла с конкретного индекса.

**Код**

```
{% for child_page in page.children offset:1 %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Вывод**

```
<a href=/parent/child2/>Child 2</a>

<a href=/parent/child3/>Child 3</a>
```

**range**

Задает диапазон номеров для выполнения цикла.

**Код**

```
{% assign n = 4 %}

{% for i in (2..n) %}

{{ i }}

{% endfor %}

{% for i in (10..14) %}

{{ i }}

{% endfor }}
```

**Вывод**

```
2 3 4

10 11 12 14
```

**reversed**

Итерация в цикле выполняется в обратном порядке, начиная с последнего элемента.

**Код**

```
{% for child_page in page.children reversed %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Вывод**

```
<a href=/parent/child3/>Child 3</a>

<a href=/parent/child2/>Child 2</a>

<a href=/parent/child1/>Child 1</a>
```

## <a name="cycle"></a>cycle

Циклическая обработка группы строк и их вывод в порядке, в котором они были переданы в качестве параметров. При каждом вызове цикла выводится следующая строка, которая была передана в виде параметра.

**Код**

```
{% for item in items %}

<div class={% cycle 'red', 'green', 'blue' %}> {{ item }} </div>

{% end %}
```

**Вывод**

```
<div class=red> Item one </div>

<div class=green> Item two </div>

<div class=blue> Item three </div>

<div class=red> Item four </div>

<div class=green> Item five</div>
```

## <a name="tablerow"></a>tablerow

Создает таблицу HTML. Должен находится внутри открывающего &lt;table&gt; и закрывающего &lt;/table&gt; HTML-тегов.

В блоке тега tablerow доступен [tablerowloop](liquid-objects.md#tablerowloop).  

**Код**

```
<table>

{% tablerow child_page in page.children %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**Вывод**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 1

</td>

<td class=col2>

Child Page 2

</td>

<td class=col3>

Child Page 3

</td>

<td class=col4>

Child Page 4

</td>

</tr>

</table>
```

### <a name="parameters"></a>Параметры

Эти параметры тега tablerowcan можно использовать самостоятельно или в сочетании.

**Вывод**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 1

</td>

<td class=col2>

Child Page 2

</td>

</tr>

<tr class=row2>

<td class=col3>

Child Page 3

</td>

<td class=col4>

Child Page 4

</td>

</tr>

</table>
```

**Код**

```
<table>

{% tablerow child_page in page.children cols:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

Задает количество строк в создаваемой таблице.

**cols**

**limit**

Выход из цикла после заданного числа элементов.

**Код**

```
<table>

{% tablerow child_page in page.children limit:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**Вывод**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 1

</td>

<td class=col2>

Child Page 2

</td>

</tr>

</table>

offset
```

Запуск цикла с конкретного индекса.

**Код**

```
<table>

{% tablerow child_page in page.children offset:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**Вывод**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 3

</td>

<td class=col2>

Child Page 4

</td>

</tr>

</table>
```

**range**

Задает диапазон номеров для выполнения цикла.

**Код**

```
<table>

{% tablerow i in (1..3) %}

{{ i }}

{% endtablerow %}

</table>
```

### <a name="see-also"></a>См. также

[Теги потока управления](control-flow-tags.md)
[Теги переменных](variable-tags.md)
[Теги шаблонов](template-tags.md)
[Теги сущностей Common Data Service Power Apps](portals-entity-tags.md)
