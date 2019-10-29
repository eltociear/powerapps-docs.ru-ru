---
title: Использование тегов итерации для портала | MicrosoftDocs
description: Сведения о тегах итерации, доступных на портале
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 600ddb0ac6e016acf057e592ac638b4e07ddf8ba
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976514"
---
# <a name="iteration-tags"></a>Теги итераций

Теги итерации используются для многократного запуска или визуализации блока кода.

## <a name="for"></a>предмет

Многократно выполняет блок кода. Чаще всего он используется для итерации элементов в массиве или словаре.

В блоке for тега доступен [объект ForLoop](liquid-objects.md#forloop) .  

**Приведен**

```
{% for child_page in page.children %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Проверки**

```
<a href=/parent/child1/>Child 1</a>

<a href=/parent/child2/>Child 2</a>

<a href=/parent/child3/>Child 3</a>
```

### <a name="parameters"></a>Вход

Эти параметры для можно использовать отдельно или в сочетании.

**Размер**

Выходит из цикла после заданного числа элементов.

**Приведен**

```
{% for child_page in page.children limit:2 %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Проверки**

```
<a href=/parent/child1/>Child 1</a>

<a href=/parent/child2/>Child 2</a>
```

**собой**

Запускает цикл по заданному индексу.

**Приведен**

```
{% for child_page in page.children offset:1 %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Проверки**

```
<a href=/parent/child2/>Child 2</a>

<a href=/parent/child3/>Child 3</a>
```

**разнообраз**

Определяет диапазон чисел для выполнения цикла.

**Приведен**

```
{% assign n = 4 %}

{% for i in (2..n) %}

{{ i }}

{% endfor %}

{% for i in (10..14) %}

{{ i }}

{% endfor }}
```

**Проверки**

```
2 3 4

10 11 12 14
```

**обратном**

Выполняет перебор цикла в обратном порядке, начиная с последнего элемента.

**Приведен**

```
{% for child_page in page.children reversed %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Проверки**

```
<a href=/parent/child3/>Child 3</a>

<a href=/parent/child2/>Child 2</a>

<a href=/parent/child1/>Child 1</a>
```

## <a name="cycle"></a>жизненно

Просматривает группу строк и выводит их в том порядке, в котором они были переданы в качестве параметров. При каждом вызове цикла вызывается следующая строка, передаваемая в качестве параметра.

**Приведен**

```
{% for item in items %}

<div class={% cycle 'red', 'green', 'blue' %}> {{ item }} </div>

{% end %}
```

**Проверки**

```
<div class=red> Item one </div>

<div class=green> Item two </div>

<div class=blue> Item three </div>

<div class=red> Item four </div>

<div class=green> Item five</div>
```

## <a name="tablerow"></a>Cell

Создает таблицу HTML. Необходимо заключить в открывающую &lt;таблицу&gt; и закрыть &lt;/табле&gt; тегами HTML.

В блоке тегов TableRow доступен [таблеровлуп](liquid-objects.md#tablerowloop) .  

**Приведен**

```
<table>

{% tablerow child_page in page.children %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**Проверки**

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

### <a name="parameters"></a>Вход

Эти параметры таблеровкан можно использовать отдельно или в сочетании.

**Проверки**

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

**Приведен**

```
<table>

{% tablerow child_page in page.children cols:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

Определяет, сколько строк должна содержать создаваемая таблица.

**колс**

**Размер**

Выходит из цикла после заданного числа элементов.

**Приведен**

```
<table>

{% tablerow child_page in page.children limit:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**Проверки**

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

Запускает цикл по заданному индексу.

**Приведен**

```
<table>

{% tablerow child_page in page.children offset:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**Проверки**

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

**разнообраз**

Определяет диапазон чисел для выполнения цикла.

**Приведен**

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
[Теги шаблона](template-tags.md)
[теги общих сущностей службы данных PowerApps](portals-entity-tags.md)
