---
title: Использование фильтров Liquid для портала | MicrosoftDocs
description: Узнайте о доступных фильтрах Liquid на портале.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 9d2bdad966b91bad9fa75dace484b54ece6e05f9
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980848"
---
# <a name="available-liquid-filters"></a>Доступные фильтры Liquid

Фильтры Liquid используются для изменения вывода строк, чисел, переменных и объектов. Они отделяются от значений, к которым применяются, с помощью символа |.

`{{ 'hal 9000' | upcase }} <!-- Output: HAL 9000 -->`

Некоторые фильтры принимают параметры. Фильтры можно также объединять, при этом они применяются в порядке слева направо.

```
{{ 2 | times: 2 | minus: 1 }} <!-- Output: 3 -->

{{ "Hello, " | append: user.firstname }} <!-- Output: Hello, Dave -->
```
В приведенном ниже разделе описаны разные фильтры. 

## <a name="array-filters"></a>Фильтры массива

Фильтры массива используются для работы с [массивами](liquid-types.md#array).  

### <a name="batch"></a>batch

Разделяет массив на несколько массивов указанного размера.

**Код**

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

**Вывод**

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

### <a name="concat"></a>concat

Объединяет два массива в один новый массив.

Если в качестве параметра указан один элемент, concat возвращает новый массив, состоящий из исходного массива с указанным элементом в качестве последнего элемента.

**Код**

```
Group #1: {{ group1 | join: ', ' }}

Group #2: {{ group2 | join: ', ' }}

Group #1 + Group #2: {{ group1 | concat: group2 | join: ', ' }}

Group #1 + Leslie: {{ group1 | concat: 'Leslie' | join: ', ' }}
```

**Вывод**

```
Group #1: John, Pete, Hannah

Group #2: Joan, Bill

Group #1 + Group #2: John, Pete, Hannah, Joan, Bill

Group #1 + Leslie: John, Pete, Hannah, Leslie
```

### <a name="except"></a>except

Выбирает все объекты в массиве, у которых указанный атрибут не имеет заданного значения. (Это противоположно **where**.)

**Код**

```
{% assign redmond = entityview.records | except: 'address1_city', 'Redmond' %}

{% for item in redmond %}

{{ item.fullname }}

{% endfor %}
```

**Вывод**

```
Jack Robinson
```

### <a name="first"></a>первая

Возвращает первый элемента массива.

first также можно использовать с особенной нотацией точки в случаях, когда его необходимо использовать внутри тега.

**Код**

```
{% assign words = This is a run of text | split:   %}

{{ words | first }}

{% if words.first == This %}

The first word is This.

{% endif %}
```

**Вывод**

```
This

The first word is This.
```

### <a name="group_by"></a>group_by

Группирование элементов в массиве по указанному атрибуту.

**Код**

```
{% assign groups = entityview.records | group_by: 'address1_city' %}

{% for group in groups %}

{{ group.key }}:

{% for item in group.items %}

{{ item.fullname }}

{% endfor %}

{% endfor %}
```

**Вывод**

```
Redmond:

John Smith

Dave Thomas

Jake Johnson

New York:

Jack Robinson
```

### <a name="join"></a>join

Объединение элементов массива с символом, переданным в качестве параметра. Результатом является одна строка.

**Код**

```
{% assign words = This is a run of text | split:   %}

{{ words | join: ,  }}
```

**Вывод**

```
This, is, a, run, of, text
```

### <a name="last"></a>последняя

Возвращает последний элемента массива.

last также можно использовать с особенной нотацией точки в случаях, когда его необходимо использовать внутри тега.

**Код**

```
{% assign words = This is a run of text | split:   -%}

{{ words | last }}

{% if words.last == text -%}

The last word is text.

{% endif -%}
```

**Вывод**

```
text

The last word is text.
```

### <a name="order_by"></a>order\_by

Возвращает элементы массива, упорядоченные по указанному атрибуту элементов массива.

При необходимости можно указать desc в качестве второго параметра для сортировки элементов в убывающем порядке, а не в восходящем.

**Код**

```
{{ entityview.records | order_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'fullname', 'desc' | join: ', ' }}
```

**Вывод**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="random"></a>random

Возвращает один случайно выбранный элемент из массива.

**Код**

```
{{ group1 | join: ', ' }}

{{ group1 | random }}
```

**Вывод**

```
John, Pete, Hannah

Pete
```

### <a name="select"></a>select

Выбирает значение указанного атрибута для каждого элемента в массиве и возвращает эти значения в виде массива.

**Код**

```
{{ entityview.records | select: 'address1_city' | join: ', ' }}
```

**Вывод**

```
Redmond, New York
```

### <a name="shuffle"></a>shuffle

При применении к массиву возвращает новый массив с теми же элементами, расположенными в случайном порядке.

**Код**

```
{{ group1 | join: ', ' }}

{{ group1 | shuffle | join: ', ' }}
```

**Вывод**

```
John, Pete, Hannah

Hannah, John, Pete
```

### <a name="size"></a>size

Возвращает число элементов в массиве.

size также можно использовать с особенной нотацией точки в случаях, когда его необходимо использовать внутри тега.

**Код**

```
{% assign words = This is a run of text | split:   -%}

{{ words | size }}

{% if words.size == 6 -%}

The text contains 6 words.

{% endif -%}
```

**Вывод**

```
6

The text contains 6 words.
```

### <a name="skip"></a>skip

Пропускает указанное число элементов в массиве и возвращает остальные.

**Код**

```
{% assign words = This is a run of text | split:   %}

{{ words | skip: 3 | join: ', ' }}
```

**Вывод**

```
run, of, text
```

### <a name="take"></a>take

Извлекает указанное число элементов из массива, возвращая эти элементы.

**Код**

```
{% assign words = This is a run of text | split:   %}

{{ words | take: 3 | join: ', ' }}
```
**Вывод**

```

This, is, a
```

### <a name="then_by"></a>then\_by

Добавляет дополнительную последующую сортировку к массиву, уже отсортированному с помощью **order\_by**.

При необходимости можно указать desc в качестве второго параметра для сортировки элементов в убывающем порядке, а не в восходящем.

**Код**

```
{{ entityview.records | order_by: 'address1_city' | then_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'address1_city' | then_by: 'fullname', 'desc' | join: ', ' }}
```

**Вывод**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="where"></a>где

Выбирает все объекты в массиве, у которых указанный атрибут имеет заданное значение.

**Код**

```
{% assign redmond = entityview.records | where: 'address1_city', 'Redmond' %}

{% for item in redmond %}

{{ item.fullname }}

{% endfor %}
```

**Вывод**

```
John Smith

Dave Thomas

Jake Johnson
```


## <a name="date-filters"></a>Фильтры по дате

Фильтры по дате можно использовать для арифметических действий с датами или для преобразования значений DateTime в различные форматы.

### <a name="date"></a>Дата

Форматирует значение DateTime с помощью строки формата .NET.

[Стандартные строки формата даты и времени](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)  

[Настраиваемые строки формата даты и времени](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings)  

**Код**

```
{{ now | date: 'g' }}

{{ now | date: 'MMMM dd, yyyy' }}
```

**Вывод**

```
5/7/2018 7:20 AM

May 07, 2018
```

### <a name="date_add_days"></a>date\_add\_days

Добавляет указанное целое или дробное число дней к значению DateTime. Параметр может быть положительным или отрицательным.

**Код**

```
{{ now }}

{{ now | date_add_days: 1 }}

{{ now | date_add_days: -2.5 }}
```

**Вывод**

```
5/7/2018 7:20:46 AM

5/8/2018 7:20:46 AM

5/4/2018 7:20:46 PM
```

### <a name="date_add_hours"></a>date\_add\_hours

Добавляет указанное целое или дробное число часов к значению DateTime. Параметр может быть положительным или отрицательным.

**Код**

```
{{ now }}

{{ now | date_add_hours: 1 }}

{{ now | date_add_hours: -2.5 }}
```

**Вывод**

```
5/7/2018 7:20:46 AM

5/7/2018 8:20:46 AM

5/7/2018 4:50:46 AM
```

### <a name="date_add_minutes"></a>date\_add\_minutes

Добавляет указанное целое или дробное число минут к значению DateTime. Параметр может быть положительным или отрицательным.

**Код**

```
{{ now }}

{{ now | date_add_minutes: 10 }}

{{ now | date_add_minutes: -2.5 }}
```


**Вывод**

```
5/7/2018 7:20:46 AM

5/7/2018 7:30:46 AM

5/7/2018 7:18:16 AM
```

### <a name="date_add_months"></a>date\_add\_months

Добавляет указанное целое или дробное число месяцев к значению DateTime. Параметр может быть положительным или отрицательным.

**Код**

```
{{ now }}

{{ now | date_add_months: 1 }}

{{ now | date_add_months: -2 }}
```

**Вывод**

```
5/7/2018 7:20:46 AM

6/7/2018 7:20:46 AM

3/7/2018 7:20:46 AM
```

### <a name="date_add_seconds"></a>date\_add\_seconds

Добавляет указанное целое или дробное число секунд к значению DateTime. Параметр может быть положительным или отрицательным.

**Код**

```
{{ now }}

{{ now | date_add_seconds: 10 }}

{{ now | date_add_seconds: -1.25 }}
```

**Вывод**

```
5/7/2018 7:20:46 AM

5/7/2018 7:20:56 AM

5/7/2018 7:20:45 AM
```

### <a name="date_add_years"></a>date\_add\_years

Добавляет указанное целое или дробное число лет к значению DateTime. Параметр может быть положительным или отрицательным.

**Код**

```
{{ now }}

{{ now | date_add_years: 1 }}

{{ now | date_add_years: -2 }}
```

**Вывод**

```
5/7/2018 7:20:46 AM

5/7/2019 7:20:46 AM

5/7/2016 7:20:46 AM
```

### <a name="date_to_iso8601"></a>date\_to\_iso8601

Форматирует значение DateTime в соответствии со стандартом [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601). Полезно при создании [*веб-каналов Atom*](https://tools.ietf.org/html/rfc4287) или элементов &lt;time&gt; HTML5.  

**Код**

```
{{ now | date_to_iso8601 }}
```

**Вывод**

```
2018-05-07T07:20:46Z
```

### <a name="date_to_rfc822"></a>date\_to\_rfc822

Форматирует значение DateTime в соответствии со стандартом [RFC 822](https://www.ietf.org/rfc/rfc0822.txt). Полезно при создании [*RSS-каналов*](https://cyber.law.harvard.edu/rss/rss.html).  

**Код**

```
{{ now | date_to_rfc822 }}
```

**Вывод**

```
Mon, 07 May 2018 07:20:46 Z
```


## <a name="entity-list-filters"></a>Фильтры списка сущностей

Фильтры списка сущностей используются для работы с определенными значениями атрибута [entitylist](liquid-objects.md#entitylist) и для помощи в создании представлений списка сущностей.  

### <a name="current_sort"></a>current\_sort

Получает выражение сортировки и возвращает текущее направление сортировки для указанного атрибута.

**Код**

```
{{ 'name ASC, createdon DESC' | current_sort: 'createdon' }}
```

**Вывод**

```
DESC
```

### <a name="metafilters"></a>metafilters

Разбирает значение JSON [entitylist](liquid-objects.md#entitylist) filter\_definition на объекты группы параметров фильтра.  

metafilters могут (необязательно) предоставляться с текущим запросом фильтра атрибутов и текущим [entitylist](liquid-objects.md#entitylist), позволяя, чтобы возвращаемые объекты фильтра помечались как выбранные или невыбранные.

**Код**

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

### <a name="reverse_sort"></a>reverse\_sort

Получает направление сортировки и возвращает противоположное направление сортировки.

**Код**

```
<!-- Sort direction is not case-sensitive -->

{{ 'ASC' | reverse_sort }}

{{ 'desc' | reverse_sort }}
```

**Вывод**

```
DESC

ASC
```


## <a name="math-filters"></a>Математические фильтры

Математические фильтры позволяют выполнять математические операции с [числами](liquid-types.md#number).  

Как и любые другие фильтры, математические фильтры можно последовательно объединять, при этом они применяются в порядке слева направо.

**Код**

```
{{ 10 | times: 2 | minus: 5 | divided_by: 3 }}
```

**Вывод**

```
5
```

### <a name="ceil"></a>ceil

Округляет значение вверх до ближайшего целого.

**Код**

```
{{ 4.6 | ceil }}

{{ 4.3 | ceil }}
```

**Вывод**

```
5

5
```

### <a name="divided_by"></a>divided\_by

Делит число на другое число.

**Код**

```
{{ 10 | divided_by: 2 }}

{{ 10 | divided_by: 3 }}

{{ 10.0 | divided_by: 3 }}
```

**Вывод**

```
5

3

3.333333
```

### <a name="floor"></a>floor

Округляет значение вниз до ближайшего целого.

**Код**

```
{{ 4.6 | floor }}

{{ 4.3 | floor }}
```

**Вывод**

```
4

4
```

### <a name="minus"></a>minus

Вычитает число из другого числа.

**Код**

```
<!-- entityview.page = 11 -->

{{ entityview.page | minus: 1 }}

{{ 10 | minus: 1.1 }}

{{ 10.1 | minus: 1 }}
```

**Вывод**

```
10

9

9.1
```

### <a name="modulo"></a>modulo

Делит число на другое число и возвращает остаток.

**Код**

```
{{ 12 | modulo: 5 }}
```

**Вывод**

```
2
```

### <a name="plus"></a>plus

Добавляет число к другому числу.

**Код**

```
<!-- entityview.page = 11 -->

{{ entityview.page | plus: 1 }}

{{ 10 | plus: 1.1 }}

{{ 10.1 | plus: 1 }}
```

**Вывод**

```
12

11

11.1
```

### <a name="round"></a>round

Округляет значение до ближайшего целого или до указанного числа знаков после запятой.

**Код**

```
{{ 4.6 | round }}

{{ 4.3 | round }}

{{ 4.5612 | round: 2 }}
```

**Вывод**

```
5

4

4.56
```

### <a name="times"></a>times

Умножает число на другое число.

**Код**

```
{{ 10 | times: 2 }}

{{ 10 | times: 2.2 }}

{{ 10.1 | times: 2 }}
```

**Вывод**

```
20

20

20.2
```


## <a name="string-filters"></a>Строковые фильтры

Строковые фильтры обрабатывают [строки](liquid-types.md#string).  

### <a name="append"></a>append

Добавляет строку в конец другой строки.

**Код**

```
{{ 'filename' | append: '.js' }}
```

**Вывод**

```
filename.js
```

### <a name="capitalize"></a>**capitalize**

Преобразует первое слово строки в прописные буквы.

**Код**

```
{{ 'capitalize me' | capitalize }}
```

**Вывод**

```
Capitalize Me
```

### <a name="downcase"></a>**downcase**

Преобразует строку в строчные буквы.

**Код**

```
{{ 'MIxed Case TExt' | downcase }}
```

**Вывод**

```
mixed case text
```

### <a name="escape"></a>**escape**

Кодирует строку с использованием escape-символов HTML.

**Код**

```
{{ '<p>test</p>' | escape }}
```

**Вывод**

```
&lt;p&gt;test&lt;/p&gt;
```

### <a name="newline_to_br"></a>**newline\_to\_br**

Вставит тег новой строки HTML &lt;br /&gt; для каждого разрыва строки в строке.

**Код**

```
{% capture text %}

A

B

C

{% endcapture %}

{{ text | newline_to_br }}
```

**Вывод**

```
A<br />

B<br />

C<br />
```

### <a name="prepend"></a>**prepend**

Добавляет строку в начало другой строки.

**Код**

```
{{ 'Jane Johnson' | prepend: 'Dr. ' }}
```

**Вывод**

```
Dr. Jane Johnson
```

### <a name="remove"></a>**remove**

Удаляет все вхождения подстроки из строки.

**Код**

```
{{ 'Hello, Dave. How are you, Dave?' | remove: 'Dave' }}
```

**Вывод**

```
Hello, . How are you, ?
```

### <a name="remove_first"></a>**remove\_first**

Удаляет первое вхождение подстроки из строки.

**Код**

```
{{ 'Hello, Dave. How are you, Dave?' | remove_first: 'Dave' }}
```

**Вывод**

```
Hello, . How are you, Dave?
```

### <a name="replace"></a>**replace**

Заменяет все вхождения строки на подстроку.

**Код**

```
{{ 'Hello, Dave. How are you, Dave?' | replace: 'Dave', 'John' }}
```

**Вывод**

```
Hello, John. How are you, John?
```

### <a name="replace_first"></a>**replace\_first**

Заменяет первое вхождение строки на подстроку.

**Код**

```
{{ 'Hello, Dave. How are you, Dave?' | replace_first: 'Dave', 'John' }}
```

**Вывод**

```
Hello, John. How are you, Dave?
```

### <a name="split"></a>**split**

Фильтр split принимает подстроку в качестве параметра. Эта подстрока используется в качестве разделителя, чтобы разделить строку в массив.

**Код**

```
{% assign words = This is a demo of the split filter | split: ' ' %}

First word: {{ words.first }}

First word: {{ words[0] }}

Second word: {{ words[1] }}

Last word: {{ words.last }}

All words: {{ words | join: ', ' }}
```

**Вывод**

```
First word: This

First word: This

Second word: is

Last word: filter

All words: This, is, a, demo, of, the, split, filter
```

### <a name="strip_html"></a>**strip\_html**

Удаляет все теги HTML из строки.

**Код**

```
<p>Hello</p>
```

**Вывод**

```
Hello
```

### <a name="strip_newlines"></a>**strip\_newlines**

Удаляет все знаки перевода строки из строки.

**Код**

```
{% capture text %}

A

B

C

{% endcapture %}

{{ text | strip_newlines }}
```

**Вывод**

```
ABC
```

### <a name="text_to_html"></a>**text\_to\_html**

Форматирует обычную текстовую строку как простой HTML. Весь текст будет закодирован в формате HTML, блоки текста, разделенные пустой строкой, будут заключены в теги абзаца &lt;p&gt;, одиночные разрывы строк будут заменены на &lt;br&gt;, а URL-адреса будут преобразованы в гиперссылки.

**Код**

```
{{ note.notetext | text_to_html }}
```

**Вывод**

```
<p>This is the first paragraph of notetext. It contains a URL: <a href="https://example.com/" rel="nofollow">https://example.com</a></p>

<p>This is a second paragraph.</p>
```

### <a name="truncate"></a>**truncate**

Обрезает строку до указанного числа знаков. Многоточие (...) добавляется к строке и включается в число символов.

**Код**

```
{{ 'This is a long run of text.' | truncate: 10 }}
```

**Вывод**

```
This is...
```

### <a name="truncate_words"></a>**truncate\_words**

Обрезает строку до указанного числа слов. Многоточие (...) добавляется в конец обрезанной строки.

**Код**

```
{{ 'This is a long run of text.' | truncate_words: 3 }}
```

**Вывод**

```
This is a...
```

### <a name="upcase"></a>**upcase**

Преобразует строку в заглавные буквы.

**Код**

```
{{ 'MIxed Case TExt' | upcase }}
```

**Вывод**

```
MIXED CASE TEXT
```

### <a name="url_escape"></a>**url\_escape**

Преобразует строку с использованием escape-символов для URI, для включения в URL-адрес.

**Код**

```
{{ 'This & that//' | url_escape }}
```

**Вывод**

```
This+%26+that%2F%2F
```

### <a name="xml_escape"></a>**xml\_escape**

Преобразует строку с использованием escape-символов для XML, для включения в выходные данные XML.

**Код**

```
{{ '<p>test</p>' | xml_escape }}
```

**Вывод**

```
&lt;p&gt;test&lt;/p&gt;
```


## <a name="type-filters"></a>Фильтры типов

Фильтры типов позволяют преобразовывать значения одного типа в другие типы.

### <a name="boolean"></a>**boolean**

Пытается преобразовать строковое значение в логическое. Если значение уже является логическим, оно возвращается без изменений. Если значение невозможно преобразовать в логическое, возвращается значение NULL.

Этот фильтр также принимает значения "вкл.", "включено" или "да" как true, и значения "откл.", "отключено" и "нет" как false.

**Код**

```
{{ true | boolean }}

{{ 'false' | boolean }}

{{ 'enabled' | boolean }}

{{ settings['something/enabled'] | boolean | default: false }}
```

**Вывод**

```
true

false

true

false
```

### <a name="decimal"></a>**десятичное**

Пытается преобразовать строковое значение в десятичное число. Если значение уже является десятичным числом, оно возвращается без изменений. Если значение невозможно преобразовать в десятичное число, возвращается значение NULL.

**Код**

```
{{ 10.1 | decimal }}

{{ '3.14' | decimal }}

{{ 'text' | decimal | default: 3.14 }}
```

**Вывод**

```
10.1

3.14

3.14
```

### <a name="integer"></a>**integer**

Пытается преобразовать строковое значение в целое число. Если значение уже является целым числом, оно возвращается без изменений. Если значение невозможно преобразовать в целое число, возвращается значение NULL.

**Код**

```
{{ 10 | integer }}

{{ '10' | integer }}

{{ '10.1' | integer }}

{{ 'text' | integer | default: 2 }}
```

**Вывод**

```
10

10


2
```

### <a name="string"></a>**string**

Пытается преобразовать значение в его строковое представление. Если значение уже является строкой, оно возвращается без изменений. Если значение равно NULL, возвращается значение NULL.



## <a name="url-filters"></a>Фильтры URL-адреса

Фильтры URL-адреса позволяют генерировать или извлекать части URL-адреса.

### <a name="add_query"></a>**add\_query**

Добавляет параметр строки запроса к URL-адресу. Если параметр уже существует в URL-адресе, значение параметра будет обновлено.

Если фильтр применяется к полному абсолютному URL-адресу, создается обновленный абсолютный URL-адрес. Если он применяется к пути, получается обновленный путь.

**Код**

```
{{ 'https://example.com/path?page=1' | add_query: 'foo', 'bar' }}

{{ '/path?page=1' | add_query: 'page', 2 }}
```

**Вывод**

```
https://example.com/path?page=1&foo=bar

/path?page=2
```

### <a name="base"></a>**base**

Получает базовый URL-адрес для указанного URL-адреса.

**Код**

```
{{ 'https://example.com/path?foo=bar&page=2' | base }}
```

**Вывод**

```
https://example.com
```

### <a name="host"></a>**host**

Получает часть URL-адреса, соответствующую узлу.

**Код**

```
{{ 'https://example.com/path?foo=bar&page=2' | host }}
```

**Вывод**

```
example.com
```

### <a name="path"></a>**path**

Получает часть URL-адреса, соответствующую пути.

**Код**

```
{{ 'https://example.com/path?foo=bar&page=2' | path }}

{{ '/path?foo=bar&page=2' | path }}
```

**Вывод**

```
/path

/path
```

### <a name="path_and_query"></a>**path\_and\_query**

Получает часть URL-адреса, представляющую путь и запрос.

**Код**

```
{{ 'https://example.com/path?foo=bar&page=2' | path_and_query }}

{{ '/path?foo=bar&page=2' | path_and_query }}
```

**Вывод**

```
/path?foo=bar&page=2

/path?foo=bar&page=2
```

### <a name="port"></a>**port**

Получает номер порта URL-адреса.

**Код**

```
{{ 'https://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com:9000/path?foo=bar&page=2' | port }}
```

**Вывод**

```
80

443

9000
```

### <a name="remove_query"></a>**remove\_query**

Удаляет параметр строки запроса из URL-адреса. Если параметр не существует в URL-адресе, URL-адрес возвращается без изменений.

Если фильтр применяется к полному абсолютному URL-адресу, создается обновленный абсолютный URL-адрес. Если он применяется к пути, получается обновленный путь.

**Код**

```
{{ 'https://example.com/path?page=1' | remove_query: 'page' }}

{{ '/path?page=1' | remove_query: 'page' }}
```

**Вывод**

```
https://example.com/path

/path
```

### <a name="scheme"></a>**scheme**

Получает часть URL-адреса, соответствующую схеме.

**Код**

```
{{ 'https://example.com/path?foo=bar&page=2' | scheme }}

{{ 'https://example.com/path?foo=bar&page=2' | scheme }}
```

**Вывод**

```
http

https
```


## <a name="additional-filters"></a>Дополнительные фильтры

Эти фильтры предоставляют полезные общие функции.

### <a name="default"></a>**default**

Возвращает значение по умолчанию для любой переменной, которой не назначено значение (т. е., NULL).

**Код**

```
{{ snippets[Header] | default: 'My Website' }}
```

**Вывод**

```
<!-- If a snippet with the name Header returns null -->

My Website
```

### <a name="file_size"></a>**file\_size**

При применении к числовому значению, представляющему число байтов, возвращает отформатированный размер файла с единицей измерения соответствующего масштаба.

Если требуется, можно передать параметр точности, чтобы управлять количеством десятичных знаков в результате. Точность по умолчанию — 1.

**Код**

```
{{ 10000000 | file_size }}

{{ 2050 | file_size: 0 }}

{{ entity.notes.first.filesize | file_size: 2 }}
```

**Вывод**

```
9.5 MB

2 KB

207.14 KB
```

### <a name="has_role"></a>**has\_role**

При применении к [user](liquid-objects.md#user) возвращает значение true, если пользователь принадлежит указанной роли. В противном случае возвращает значение false.  

**Код**

```
{% assign is_admin = user | has_role: 'Administrators' %}

{% if is_admin %}

User is an administrator.

{% endif %}
```

### <a name="liquid"></a>**liquid**

Представляет строку в виде кода Liquid. Этот код будет иметь доступ к текущему контексту выполнения Liquid (переменные и т. д.).

> [!Note] 
> Этот фильтр должен использоваться с осторожностью и обычно должен применяться только к значениям, находящимся под монопольным управлением авторов содержимого портала или других пользователей, которым можно доверить написание кода Liquid.

**Код**

```
{{ page.adx_copy | liquid }}
```

### <a name="see-also"></a>См. также

[Сохранение содержимого источника с помощью веб-шаблонов](store-content-web-templates.md)  
[Знакомство с операторами Liquid](liquid-operators.md) 
[Типы Liquid](liquid-types.md)  
[Объекты Liquid](liquid-objects.md)  
[Теги Liquid](liquid-tags.md)  
[Фильтры Liquid](liquid-filters.md)  
