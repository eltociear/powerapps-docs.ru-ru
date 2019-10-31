---
title: Использование тегов Liquid для портала | Документация Майкрософт
description: Узнайте о доступных тегах Liquid на портале.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="available-liquid-tags"></a>Доступные теги Liquid

Теги составляют логику программирования, которая сообщает шаблонам, что делать. Теги заключаются в символы {% %}.

```
{% if user.fullname == 'Dave Bowman' %} Hello, Dave. {% endif %}
```

## <a name="whitespace-control"></a>Управление пробельными символами

Обычно Liquid обрабатывает все данные вне переменных и блоков тегов дословно, с сохранением всех пробельных символов. Иногда дополнительные пробельные символы не требуются, но требуется аккуратное форматирование шаблона, для чего нужны пробельные символы.

Можно задать, чтобы механизм обработки удалял все начальные и конечные пробельные символы, добавив дефис (-) в начало или конец блока тегов.

**Код**

```
{% for i in (1..5) --%}

{{ i }}

{%-- endfor %}
```

**Вывод**

```
12345
```
### <a name="see-also"></a>См. также

[Типы Liquid](liquid-types.md)  
[Объекты Liquid](liquid-objects.md)  
[Фильтры Liquid](liquid-filters.md) 
