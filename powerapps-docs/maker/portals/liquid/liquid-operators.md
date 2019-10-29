---
title: Использование операторов жидкостей для портала | MicrosoftDocs
description: Сведения о доступных операторах ликвидности на портале.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 4a27a5364a4ae12fecc3a72dbb52115e415dcdb8
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976537"
---
# <a name="understand-liquid-operators"></a>Общие сведения об операторах Liquid

Жидкость имеет доступ ко всем общим логическим операторам и. Их можно использовать в таких тегах, как **If** и **.**

## <a name="basic-operators"></a>Основные операторы

| ==    | Прошлом                          |
|-------|---------------------------------|
| !=    | Не равно                  |
| &gt;  | Более                    |
| &lt;  | Менее                       |
| &gt;= | Больше или равно        |
| &lt;= | Меньше или равно           |
| или    | Условие а **или** условие б  |
| перетаскивани   | Условие а **и** условие б |

## <a name="contains"></a>содержащих

содержит тесты для присутствия подстроки в строке.

```
{% if page.title contains 'Product' %}

The title of this page contains the word Product.

{% endif %}
```

Contains также может проверять наличие строки в массиве строк.

## <a name="startswith"></a>StartsWith

StartsWith проверяет, начинается ли строка с заданной подстроки.

```
{% if page.title startswith 'Profile' %}

This is a profile page.

{% endif %}
```

## <a name="endswith"></a>EndsWith

EndsWith проверяет, заканчивается ли строка данной подстрокой.

```
{% if page.title endswith 'Forum' %}

This is a forum page.

{% endif %}
```

### <a name="see-also"></a>См. также

[Хранение исходного содержимого с помощью веб-шаблонов](store-content-web-templates.md)  
[Типы жидкостей](liquid-types.md)  
[Условие](liquid-conditional-operators.md)  
[Объекты жидкостей](liquid-objects.md)  
[Теги жидкостей](liquid-tags.md)  
[Фильтры жидкостей](liquid-filters.md) 