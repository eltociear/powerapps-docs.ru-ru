---
title: Использование фильтров жидкостей для портала | MicrosoftDocs
description: Сведения о доступных фильтрах ликвидности на портале.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 68a595ee72704cf81241ecfee19f90728fb95aeb
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975157"
---
# <a name="available-liquid-filters"></a>Доступные фильтры Liquid

Фильтры жидкостей используются для изменения выходных данных строк, чисел, переменных и объектов. Они отделены от значения, к которому они применяются в |.

`{{ 'hal 9000' | upcase }} <!-- Output: HAL 9000 -->`

Некоторые фильтры принимают параметры. Фильтры также можно сочетать и применять в порядке слева направо.

```
{{ 2 | times: 2 | minus: 1 }} <!-- Output: 3 -->

{{ "Hello, " | append: user.firstname }} <!-- Output: Hello, Dave -->
```
В разделе ниже описываются различные фильтры. 

## <a name="array-filters"></a>Фильтры массива

Фильтры массивов используются для работы с [массивами](liquid-types.md#array).  

### <a name="batch"></a>разделах

Делит массив на несколько массивов заданного размера.

**Приведен**

```
{% assign batches = entityview.records | batch: 2 %}

{% for batch in batches %}

<ul>

{% for item in batch %}

<li>{{ item.fullname }}</li>

{% endfor %}

</ul>

{% endfor %}
```

**Проверки**

```
<ul>

<li>John Smith</li>

<li>Dave Thomas</li>

</ul>

<ul>

<li>Jake Johnson</li>

<li>Jack Robinson</li>

</ul>
```

### <a name="concat"></a>сцеплен

Сцепляет два массива в один новый массив.

При наличии одного элемента в качестве параметра Concat возвращает новый массив, состоящий из исходного массива с данным элементом в качестве последнего элемента.

**Приведен**

```
Group #1: {{ group1 | join: ', ' }}

Group #2: {{ group2 | join: ', ' }}

Group #1 + Group #2: {{ group1 | concat: group2 | join: ', ' }}

Group #1 + Leslie: {{ group1 | concat: 'Leslie' | join: ', ' }}
```

**Проверки**

```
Group #1: John, Pete, Hannah

Group #2: Joan, Bill

Group #1 + Group #2: John, Pete, Hannah, Joan, Bill

Group #1 + Leslie: John, Pete, Hannah, Leslie
```

### <a name="except"></a>варианта

Выберите все объекты в массиве, у которых у данного атрибута нет заданного значения. (Это обратная**часть.** )

**Приведен**

```
{% assign redmond = entityview.records | except: 'address1_city', 'Redmond' %}

{% for item in redmond %}

{{ item.fullname }}

{% endfor %}
```

**Проверки**

```
Jack Robinson
```

### <a name="first"></a>Началь

Возвращает первый элемент массива.

Сначала можно использовать с особой точечной нотацией, в случаях, когда ее нужно использовать внутри тега.

**Приведен**

```
{% assign words = This is a run of text | split:   %}

{{ words | first }}

{% if words.first == This %}

The first word is This.

{% endif %}
```

**Проверки**

```
This

The first word is This.
```

### <a name="group_by"></a>group_by

Группирование элементов в массиве по заданному атрибуту.

**Приведен**

```
{% assign groups = entityview.records | group_by: 'address1_city' %}

{% for group in groups %}

{{ group.key }}:

{% for item in group.items %}

{{ item.fullname }}

{% endfor %}

{% endfor %}
```

**Проверки**

```
Redmond:

John Smith

Dave Thomas

Jake Johnson

New York:

Jack Robinson
```

### <a name="join"></a>К

Соединяет элементы массива с символом, переданным в качестве параметра. Результатом является одна строка.

**Приведен**

```
{% assign words = This is a run of text | split:   %}

{{ words | join: ,  }}
```

**Проверки**

```
This, is, a, run, of, text
```

### <a name="last"></a>Последняя

Возвращает последний элемент массива.

Last можно также использовать с особой точечной нотацией в случаях, когда ее нужно использовать внутри тега.

**Приведен**

```
{% assign words = This is a run of text | split:   -%}

{{ words | last }}

{% if words.last == text -%}

The last word is text.

{% endif -%}
```

**Проверки**

```
text

The last word is text.
```

### <a name="order_by"></a>порядок\_

Возвращает элементы массива, упорядоченные по заданному атрибуту элементов массива.

При необходимости можно указать DESC в качестве второго параметра для сортировки элементов в убывающем порядке, а не по возрастанию.

**Приведен**

```
{{ entityview.records | order_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'fullname', 'desc' | join: ', ' }}
```

**Проверки**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="random"></a>имитаци

Возвращает один элемент из массива, выбираемый случайным образом.

**Приведен**

```
{{ group1 | join: ', ' }}

{{ group1 | random }}
```

**Проверки**

```
John, Pete, Hannah

Pete
```

### <a name="select"></a>Метьте

Выбирает значение заданного атрибута для каждого элемента в массиве и возвращает эти значения в виде массива.

**Приведен**

```
{{ entityview.records | select: 'address1_city' | join: ', ' }}
```

**Проверки**

```
Redmond, New York
```

### <a name="shuffle"></a>носить

При применении к массиву возвращает новый массив с теми же элементами в случайном порядке.

**Приведен**

```
{{ group1 | join: ', ' }}

{{ group1 | shuffle | join: ', ' }}
```

**Проверки**

```
John, Pete, Hannah

Hannah, John, Pete
```

### <a name="size"></a>Изменять

Возвращает количество элементов в массиве.

Размер также можно использовать с особой точечной нотацией, в случаях, когда ее нужно использовать внутри тега.

**Приведен**

```
{% assign words = This is a run of text | split:   -%}

{{ words | size }}

{% if words.size == 6 -%}

The text contains 6 words.

{% endif -%}
```

**Проверки**

```
6

The text contains 6 words.
```

### <a name="skip"></a>skip

Пропускает заданное число элементов в массиве и возвращает оставшуюся часть.

**Приведен**

```
{% assign words = This is a run of text | split:   %}

{{ words | skip: 3 | join: ', ' }}
```

**Проверки**

```
run, of, text
```

### <a name="take"></a>нимают

Принимает заданное число элементов из массива, возвращая полученные элементы.

**Приведен**

```
{% assign words = This is a run of text | split:   %}

{{ words | take: 3 | join: ', ' }}
```
**Проверки**

```

This, is, a
```

### <a name="then_by"></a>затем\_

Добавляет дополнительное последующее упорядочение к массиву, уже упорядоченному по**порядку\_by**.

При необходимости можно указать DESC в качестве второго параметра для сортировки элементов в убывающем порядке, а не по возрастанию.

**Приведен**

```
{{ entityview.records | order_by: 'address1_city' | then_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'address1_city' | then_by: 'fullname', 'desc' | join: ', ' }}
```

**Проверки**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="where"></a>Которому

Выберите все объекты в массиве, где заданный атрибут имеет заданное значение.

**Приведен**

```
{% assign redmond = entityview.records | where: 'address1_city', 'Redmond' %}

{% for item in redmond %}

{{ item.fullname }}

{% endfor %}
```

**Проверки**

```
John Smith

Dave Thomas

Jake Johnson
```


## <a name="date-filters"></a>Фильтры дат

Фильтры дат можно использовать для арифметики дат или для преобразования значений типа DateTime в различные форматы.

### <a name="date"></a>Дата

Форматирует значение даты и времени с помощью строки формата .NET.

[Строки стандартных форматов даты и времени](https://docs.microsoft.com/en-us/dotnet/standard/base-types/standard-date-and-time-format-strings)  

[Строки настраиваемых форматов даты и времени](https://docs.microsoft.com/en-us/dotnet/standard/base-types/custom-date-and-time-format-strings)  

**Приведен**

```
{{ now | date: 'g' }}

{{ now | date: 'MMMM dd, yyyy' }}
```

**Проверки**

```
5/7/2018 7:20 AM

May 07, 2018
```

### <a name="date_add_days"></a>Дата\_Добавление\_дней

Добавляет указанное число целых и неполных дней к значению DateTime. Параметр может быть положительным или отрицательным.

**Приведен**

```
{{ now }}

{{ now | date_add_days: 1 }}

{{ now | date_add_days: -2.5 }}
```

**Проверки**

```
5/7/2018 7:20:46 AM

5/8/2018 7:20:46 AM

5/4/2018 7:20:46 PM
```

### <a name="date_add_hours"></a>Дата\_Добавление\_ч

Добавляет указанное число целых и неполных часов к значению DateTime. Параметр может быть положительным или отрицательным.

**Приведен**

```
{{ now }}

{{ now | date_add_hours: 1 }}

{{ now | date_add_hours: -2.5 }}
```

**Проверки**

```
5/7/2018 7:20:46 AM

5/7/2018 8:20:46 AM

5/7/2018 4:50:46 AM
```

### <a name="date_add_minutes"></a>Дата\_Добавление\_минут

Добавляет указанное число полных и неполных минут в значение DateTime. Параметр может быть положительным или отрицательным.

**Приведен**

```
{{ now }}

{{ now | date_add_minutes: 10 }}

{{ now | date_add_minutes: -2.5 }}
```


**Проверки**

```
5/7/2018 7:20:46 AM

5/7/2018 7:30:46 AM

5/7/2018 7:18:16 AM
```

### <a name="date_add_months"></a>Дата\_Добавление\_месяцев

Добавляет указанное число целых месяцев к значению DateTime. Параметр может быть положительным или отрицательным.

**Приведен**

```
{{ now }}

{{ now | date_add_months: 1 }}

{{ now | date_add_months: -2 }}
```

**Проверки**

```
5/7/2018 7:20:46 AM

6/7/2018 7:20:46 AM

3/7/2018 7:20:46 AM
```

### <a name="date_add_seconds"></a>Дата\_Добавление\_секунд

Добавляет указанное число целых и долей секунд к значению DateTime. Параметр может быть положительным или отрицательным.

**Приведен**

```
{{ now }}

{{ now | date_add_seconds: 10 }}

{{ now | date_add_seconds: -1.25 }}
```

**Проверки**

```
5/7/2018 7:20:46 AM

5/7/2018 7:20:56 AM

5/7/2018 7:20:45 AM
```

### <a name="date_add_years"></a>Дата\_Добавление\_лет

Добавляет указанное число целых лет к значению DateTime. Параметр может быть положительным или отрицательным.

**Приведен**

```
{{ now }}

{{ now | date_add_years: 1 }}

{{ now | date_add_years: -2 }}
```

**Проверки**

```
5/7/2018 7:20:46 AM

5/7/2019 7:20:46 AM

5/7/2016 7:20:46 AM
```

### <a name="date_to_iso8601"></a>Дата\_\_ISO8601

Форматирует значение DateTime согласно стандарту [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) . Полезно при создании [*веб-каналов Atom*](http://tools.ietf.org/html/rfc4287)или в &lt;&gt; времени HTML5.  

**Приведен**

```
{{ now | date_to_iso8601 }}
```

**Проверки**

```
2018-05-07T07:20:46Z
```

### <a name="date_to_rfc822"></a>Дата\_\_RFC822

Форматирует значение DateTime согласно стандарту [RFC 822](https://www.ietf.org/rfc/rfc0822.txt) . Полезно при создании [*RSS-каналов*](http://cyber.law.harvard.edu/rss/rss.html).  

**Приведен**

```
{{ now | date_to_rfc822 }}
```

**Проверки**

```
Mon, 07 May 2018 07:20:46 Z
```


## <a name="entity-list-filters"></a>Фильтры списка сущностей

Фильтры списка сущностей используются для работы с определенными значениями атрибутов [ентитилист](liquid-objects.md#entitylist) , а также для помощи в создании представлений списка сущностей.  

### <a name="current_sort"></a>Текущая сортировка\_

При наличии выражения сортировки возвращает текущее направление сортировки для данного атрибута.

**Приведен**

```
{{ 'name ASC, createdon DESC' | current_sort: 'createdon' }}
```

**Проверки**

```
DESC
```

### <a name="metafilters"></a>метафилтерс

Анализирует фильтр [ентитилист](liquid-objects.md#entitylist)\_значение JSON определения в объекты группы параметров фильтра.  

метафилтерс можно дополнительно предоставить с текущим запросом фильтра атрибутов и текущим [ентитилист](liquid-objects.md#entitylist), позволяя пометить возвращенные объекты фильтра как выбранные или невыбранные.

**Приведен**

```
{% assign filters = entitylist | metafilters: params.mf, entityview %}
{% if filters.size > 0 %}
  <ul id=entitylist-filters>
    {% for filter in filters %}
      <li class=entitylist-filter-option-group>
        {% if filter.selection_mode == 'Single' %}
          {% assign type = 'radio' %}
        {% else %}
          {% assign type = 'checkbox' %}
        {% endif %}
        <h4 class=entitylist-filter-option-group-label
          data-filter-id={{ filter.id | h }}>
          {{ filter.label | h }}
        </h4>
        <ul>
          {% for option in filter.options %}
            <li class=entitylist-filter-option>
              {% if option.type == 'text' %}
                <div class=input-group entitylist-filter-option-text>
                  <span class=input-group-addon>
                    <span class=fa fa-filter aria-hidden=true></span>
                  </span>
                  <input class=form-control
                    type=text
                    name={{ filter.id | h }}
                    value={{ option.text | h }} />
                </div>
              {% else %}
                <div class={{ type | h }}>
                  <label>
                    <input
                      type={{ type | h }}
                      name={{ filter.id | h }}
                      value={{ option.id | h }}
                      {% if option.checked %}
                        checked=checked
                        data-checked=true{% endif %}
                      />
                    {{ option.label | h }}
                  </label>
                </div>
              {% endif %}
            </li>
          {% endfor %}
        </ul>
      </li>
    {% endfor %}
  </ul>
  <button class=btn btn-default data-serialized-query=mf data-target=#entitylist-filters>Apply Filters</button>
{% endif %}
```

### <a name="reverse_sort"></a>обратная сортировка\_

При указании направления сортировки возвращает противоположное направление сортировки.

**Приведен**

```
<!-- Sort direction is not case-sensitive -->

{{ 'ASC' | reverse_sort }}

{{ 'desc' | reverse_sort }}
```

**Проверки**

```
DESC

ASC
```


## <a name="math-filters"></a>Математические фильтры

Математические фильтры позволяют выполнять математические операции с [числами](liquid-types.md#number).  

Как и для всех фильтров, математические фильтры могут быть объединены в цепочку и применены в порядке слева направо.

**Приведен**

```
{{ 10 | times: 2 | minus: 5 | divided_by: 3 }}
```

**Проверки**

```
5
```

### <a name="ceil"></a>ceil

Округляет значение до ближайшего целого.

**Приведен**

```
{{ 4.6 | ceil }}

{{ 4.3 | ceil }}
```

**Проверки**

```
5

5
```

### <a name="divided_by"></a>деление\_

Делит число на другое число.

**Приведен**

```
{{ 10 | divided_by: 2 }}

{{ 10 | divided_by: 3 }}

{{ 10.0 | divided_by: 3 }}
```

**Проверки**

```
5

3

3.333333
```

### <a name="floor"></a>фабрич

Округляет значение до ближайшего целого.

**Приведен**

```
{{ 4.6 | floor }}

{{ 4.3 | floor }}
```

**Проверки**

```
4

4
```

### <a name="minus"></a>знак

Вычитает число из другого числа.

**Приведен**

```
<!-- entityview.page = 11 -->

{{ entityview.page | minus: 1 }}

{{ 10 | minus: 1.1 }}

{{ 10.1 | minus: 1 }}
```

**Проверки**

```
10

9

9.1
```

### <a name="modulo"></a>модуля

Делит число на другое число и возвращает остаток.

**Приведен**

```
{{ 12 | modulo: 5 }}
```

**Проверки**

```
2
```

### <a name="plus"></a>плюс

Добавляет число в другое число.

**Приведен**

```
<!-- entityview.page = 11 -->

{{ entityview.page | plus: 1 }}

{{ 10 | plus: 1.1 }}

{{ 10.1 | plus: 1 }}
```

**Проверки**

```
12

11

11.1
```

### <a name="round"></a>округло

Округляет значение до ближайшего целого или указанного числа десятичных знаков.

**Приведен**

```
{{ 4.6 | round }}

{{ 4.3 | round }}

{{ 4.5612 | round: 2 }}
```

**Проверки**

```
5

4

4.56
```

### <a name="times"></a>указанное

Умножает число на другое число.

**Приведен**

```
{{ 10 | times: 2 }}

{{ 10 | times: 2.2 }}

{{ 10.1 | times: 2 }}
```

**Проверки**

```
20

20

20.2
```


## <a name="string-filters"></a>Строковые фильтры

Строковые фильтры обрабатывают [строки](liquid-types.md#string).  

### <a name="append"></a>Добавление

Добавляет строку в конец другой строки.

**Приведен**

```
{{ 'filename' | append: '.js' }}
```

**Проверки**

```
filename.js
```

### <a name="capitalize"></a>**выгоду**

заполняет первое слово в строке прописными буквами.

**Приведен**

```
{{ 'capitalize me' | capitalize }}
```

**Проверки**

```
Capitalize Me
```

### <a name="downcase"></a>**довнкасе**

Преобразует строку в нижний регистр.

**Приведен**

```
{{ 'MIxed Case TExt' | downcase }}
```

**Проверки**

```
mixed case text
```

### <a name="escape"></a>**выполняет**

HTML — escape-последовательность строк.

**Приведен**

```
{{ '<p>test</p>' | escape }}
```

**Проверки**

```
&lt;p&gt;test&lt;/p&gt;
```

### <a name="newline_to_br"></a>**\_новой строки для\_br**

Вставляет &lt;тег "BR/&gt;" разрыв строки HTML при каждой разрыве строки в строке.

**Приведен**

```
{% capture text %}

A

B

C

{% endcapture %}

{{ text | newline_to_br }}
```

**Проверки**

```
A<br />

B<br />

C<br />
```

### <a name="prepend"></a>**соединяет**

Добавляет строку в начало другой строки.

**Приведен**

```
{{ 'Jane Johnson' | prepend: 'Dr. ' }}
```

**Проверки**

```
Dr. Jane Johnson
```

### <a name="remove"></a>**отменит**

Удалить все вхождения подстроки из строки.

**Приведен**

```
{{ 'Hello, Dave. How are you, Dave?' | remove: 'Dave' }}
```

**Проверки**

```
Hello, . How are you, ?
```

### <a name="remove_first"></a>**Сначала удалите\_**

Удаляет первое вхождение подстроки из строки.

**Приведен**

```
{{ 'Hello, Dave. How are you, Dave?' | remove_first: 'Dave' }}
```

**Проверки**

```
Hello, . How are you, Dave?
```

### <a name="replace"></a>**восстановить**

Заменяет все вхождения строки подстрокой.

**Приведен**

```
{{ 'Hello, Dave. How are you, Dave?' | replace: 'Dave', 'John' }}
```

**Проверки**

```
Hello, John. How are you, John?
```

### <a name="replace_first"></a>**Сначала замените\_**

Заменяет первое вхождение строки подстрокой.

**Приведен**

```
{{ 'Hello, Dave. How are you, Dave?' | replace_first: 'Dave', 'John' }}
```

**Проверки**

```
Hello, John. How are you, Dave?
```

### <a name="split"></a>**биваем**

Фильтр разбиения принимает в качестве параметра подстроку. Подстрока используется в качестве разделителя для разделения строки на массив.

**Приведен**

```
{% assign words = This is a demo of the split filter | split: ' ' %}

First word: {{ words.first }}

First word: {{ words[0] }}

Second word: {{ words[1] }}

Last word: {{ words.last }}

All words: {{ words | join: ', ' }}
```

**Проверки**

```
First word: This

First word: This

Second word: is

Last word: filter

All words: This, is, a, demo, of, the, split, filter
```

### <a name="strip_html"></a>**удалить\_HTML**

Удаляет все HTML-теги из строки.

**Приведен**

```
<p>Hello</p>
```

**Проверки**

```
Hello
```

### <a name="strip_newlines"></a>**удалить\_новой строки**

Удаляет все разрывы строк из строки.

**Приведен**

```
{% capture text %}

A

B

C

{% endcapture %}

{{ text | strip_newlines }}
```

**Проверки**

```
ABC
```

### <a name="text_to_html"></a>**Текстовая\_\_HTML**

Форматирует обычную текстовую строку как простой HTML. Весь текст будет закодирован в формате HTML, блоки текста, разделенные пустой строкой, будут заключены в абзац &lt;p&gt; теги, отдельные разрывы строк будут заменены &lt;BR&gt;, а URL-адреса будут преобразованы в гиперссылки.

**Приведен**

```
{{ note.notetext | text_to_html }}
```

**Проверки**

```
<p>This is the first paragraph of notetext. It contains a URL: <a href="http://example.com/" rel="nofollow">http://example.com</a></p>

<p>This is a second paragraph.</p>
```

### <a name="truncate"></a>**TRUNCATE**

Усекает строку до заданного количества символов. Многоточие (...) добавляется к строке и включается в число символов.

**Приведен**

```
{{ 'This is a long run of text.' | truncate: 10 }}
```

**Проверки**

```
This is...
```

### <a name="truncate_words"></a>**усечение\_слов**

Усекает строку до заданного числа слов. К усеченной строке добавляется многоточие (...).

**Приведен**

```
{{ 'This is a long run of text.' | truncate_words: 3 }}
```

**Проверки**

```
This is a...
```

### <a name="upcase"></a>**с учетом регистра**

Преобразует строку в верхний регистр.

**Приведен**

```
{{ 'MIxed Case TExt' | upcase }}
```

**Проверки**

```
MIXED CASE TEXT
```

### <a name="url_escape"></a>**Escape-\_URL**

URI — экранирование строки для включения в URL-адрес.

**Приведен**

```
{{ 'This & that//' | url_escape }}
```

**Проверки**

```
This+%26+that%2F%2F
```

### <a name="xml_escape"></a>**Escape-\_XML**

XML — escape-последовательность строки для включения в выходные данные XML.

**Приведен**

```
{{ '<p>test</p>' | xml_escape }}
```

**Проверки**

```
&lt;p&gt;test&lt;/p&gt;
```


## <a name="type-filters"></a>Фильтры типов

Фильтры типов позволяют преобразовать значения одного типа в другие типы.

### <a name="boolean"></a>**логическая**

Пытается преобразовать строковое значение в логическое. Если значение уже является логическим, оно будет возвращено без изменений. Если значение не может быть преобразовано в логическое, будет возвращено значение null.

Этот фильтр также будет принимать значения true, Enabled или Yes, а также не имеет значения false.

**Приведен**

```
{{ true | boolean }}

{{ 'false' | boolean }}

{{ 'enabled' | boolean }}

{{ settings['something/enabled'] | boolean | default: false }}
```

**Проверки**

```
true

false

true

false
```

### <a name="decimal"></a>**десятич**

Пытается преобразовать строковое значение в десятичное число. Если значение уже является десятичным числом, оно будет возвращено без изменений. Если значение не может быть преобразовано в десятичное число, будет возвращено значение null.

**Приведен**

```
{{ 10.1 | decimal }}

{{ '3.14' | decimal }}

{{ 'text' | decimal | default: 3.14 }}
```

**Проверки**

```
10.1

3.14

3.14
```

### <a name="integer"></a>**цело**

Пытается преобразовать строковое значение в целое число. Если значение уже является целым числом, оно будет возвращено без изменений. Если значение не может быть преобразовано в целое число, будет возвращено значение null.

**Приведен**

```
{{ 10 | integer }}

{{ '10' | integer }}

{{ '10.1' | integer }}

{{ 'text' | integer | default: 2 }}
```

**Проверки**

```
10

10


2
```

### <a name="string"></a>**Строка**

Пытается преобразовать значение в строковое представление. Если значение уже является строкой, оно будет возвращено без изменений. Если значение равно null, будет возвращено значение null.



## <a name="url-filters"></a>Фильтры URL-адресов

Фильтры URL-адресов позволяют создавать или извлекать части URL-адресов.

### <a name="add_query"></a>**Добавление\_запроса**

Добавляет параметр строки запроса к URL-адресу. Если параметр уже существует в URL-адресе, значение параметра будет обновлено.

Если фильтр применяется к полному абсолютному URL-адресу, то будет получен обновленный абсолютный URL-адрес. Если он применяется к пути, то в результате будет получен обновленный путь.

**Приведен**

```
{{ 'http://example.com/path?page=1' | add_query: 'foo', 'bar' }}

{{ '/path?page=1' | add_query: 'page', 2 }}
```

**Проверки**

```
http://example.com/path?page=1&foo=bar

/path?page=2
```

### <a name="base"></a>**из**

Возвращает базовый URL-адрес данного URL-адреса.

**Приведен**

```
{{ 'http://example.com/path?foo=bar&page=2' | base }}
```

**Проверки**

```
http://example.com
```

### <a name="host"></a>**хост**

Возвращает часть URL-адреса узла.

**Приведен**

```
{{ 'http://example.com/path?foo=bar&page=2' | host }}
```

**Проверки**

```
example.com
```

### <a name="path"></a>**путь**

Возвращает часть пути URL-адреса.

**Приведен**

```
{{ 'http://example.com/path?foo=bar&page=2' | path }}

{{ '/path?foo=bar&page=2' | path }}
```

**Проверки**

```
/path

/path
```

### <a name="path_and_query"></a>**\_пути и\_запроса**

Возвращает путь и часть URL-адреса.

**Приведен**

```
{{ 'http://example.com/path?foo=bar&page=2' | path_and_query }}

{{ '/path?foo=bar&page=2' | path_and_query }}
```

**Проверки**

```
/path?foo=bar&page=2

/path?foo=bar&page=2
```

### <a name="port"></a>**порту**

Возвращает номер порта URL-адреса.

**Приведен**

```
{{ 'http://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com:9000/path?foo=bar&page=2' | port }}
```

**Проверки**

```
80

443

9000
```

### <a name="remove_query"></a>**Удаление\_запроса**

Удаляет параметр строки запроса из URL-адреса. Если параметр не существует в URL-адресе, URL-адрес будет возвращен без изменений.

Если фильтр применяется к полному абсолютному URL-адресу, то будет получен обновленный абсолютный URL-адрес. Если он применяется к пути, то в результате будет получен обновленный путь.

**Приведен**

```
{{ 'http://example.com/path?page=1' | remove_query: 'page' }}

{{ '/path?page=1' | remove_query: 'page' }}
```

**Проверки**

```
http://example.com/path

/path
```

### <a name="scheme"></a>**Схема**

Возвращает часть схемы URL-адреса.

**Приведен**

```
{{ 'http://example.com/path?foo=bar&page=2' | scheme }}

{{ 'https://example.com/path?foo=bar&page=2' | scheme }}
```

**Проверки**

```
http

https
```


## <a name="additional-filters"></a>Дополнительные фильтры

Эти фильтры предоставляют полезные общие функциональные возможности.

### <a name="default"></a>**параметры**

Возвращает значение по умолчанию для любой переменной без присвоенного значения (т. е. null).

**Приведен**

```
{{ snippets[Header] | default: 'My Website' }}
```

**Проверки**

```
<!-- If a snippet with the name Header returns null -->

My Website
```

### <a name="file_size"></a>**Размер\_файла**

Применяется к числовому значению, представляющему число байтов, возвращает отформатированный размер файла с единицей соответствующего масштаба.

При необходимости можно передать параметр точности, чтобы управлять числом десятичных разрядов в результате. Точность по умолчанию равна 1.

**Приведен**

```
{{ 10000000 | file_size }}

{{ 2050 | file_size: 0 }}

{{ entity.notes.first.filesize | file_size: 2 }}
```

**Проверки**

```
9.5 MB

2 KB

207.14 KB
```

### <a name="has_role"></a>**имеет\_роль**

Функция, применяемая к [пользователю](liquid-objects.md#user), возвращает значение true, если пользователь принадлежит к данной роли. Возвращает значение false, если нет.  

**Приведен**

```
{% assign is_admin = user | has_role: 'Administrators' %}

{% if is_admin %}

User is an administrator.

{% endif %}
```

### <a name="liquid"></a>**Liquid**

Отображает строку в виде кода ликвидности. Этот код будет иметь доступ к текущему контексту выполнения ликвидности (переменным и т. д.).

> [!Note] 
> Этот фильтр следует использовать с осторожностью. его обычно следует применять только к значениям, которые находятся в монопольном управлении авторами содержимого портала или другими пользователями, которые могут быть доверенными для написания кода ликвидности.

**Приведен**

```
{{ page.adx_copy | liquid }}
```

### <a name="see-also"></a>См. также

[Хранение исходного содержимого с помощью веб-шаблонов](store-content-web-templates.md)  
[Общие сведения об операторах жидкостей](liquid-operators.md) 
[денежных типов](liquid-types.md)  
[Объекты жидкостей](liquid-objects.md)  
[Теги жидкостей](liquid-tags.md)  
[Фильтры жидкостей](liquid-filters.md)  
