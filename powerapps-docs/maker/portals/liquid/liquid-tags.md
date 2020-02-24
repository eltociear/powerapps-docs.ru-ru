---
title: Использование тегов Liquid для портала | MicrosoftDocs
description: Узнайте о доступных тегах Liquid на портале.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 3f85e4b86b305696f5b155c7e9e3b773f8ba2103
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2020
ms.locfileid: "2981112"
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
