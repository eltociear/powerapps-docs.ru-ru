---
title: Использование тегов Liquid для портала | MicrosoftDocs
description: Узнайте о доступных тегах Liquid на портале.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b04c6447911d1a884627bd2cbb4ad7b74b9c5ce5
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "2708146"
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
