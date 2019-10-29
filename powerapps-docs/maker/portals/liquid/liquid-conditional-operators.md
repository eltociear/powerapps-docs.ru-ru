---
title: Использование условных операторов жидкости для портала | MicrosoftDocs
description: Сведения о доступных условных операторах ликвидности на портале.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: def132ebc0f8ef93121b10b221479a2452a1d4fb
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975019"
---
# <a name="available-liquid-conditional-operators"></a>Доступные условные операторы Liquid

При использовании в условных инструкциях (**Если** **нет**) некоторые ликвидные значения будут считаться истинными, а некоторые будут считаться ложными.

В Жидкостьх значение NULL и логическое значение false обрабатываются как false; все остальное обрабатывается как true. Пустые строки, пустые массивы и т. д. обрабатываются как true. Примеры

```
{% assign empty_string =  %}
{% if empty_string %}
<p>This will render.</p>
{% endif %}
```
При необходимости можно проверить пустые строки и массивы, используя специальное значение Empty.

```
{% unless page.title == empty %}
<h1>{{ page.title }}</h1>
{% endunless %}
```
Вы также можете проверить размер [типов жидкостей](liquid-types.md), [денежных типов](liquid-types.md)или [типов жидкости](liquid-types.md) с помощью свойства Специальный размер.

```
{% if page.children.size > 0 %}
<ul>
{% for child in page.children %}
<li>{{ child.title }}</li>
{% endfor %}
</ul>
{% endif %}
```

## <a name="summary"></a>Суммар

|                           | True | IsFalse |
|---------------------------|------|-------|
| True                      | ×    |       |
| IsFalse                     |      | ×     |
| Заканчивающ                      |      | ×     |
| Строка                    | ×    |       |
| Пустая строка              | ×    |       |
| 0                         | ×    |       |
| 1, 3,14                   | ×    |       |
| массив или словарь       | ×    |       |
| пустой массив или словарь | ×    |       |
| Объектами                    | ×    |       |

### <a name="see-also"></a>См. также

[Хранение исходного содержимого с помощью веб-шаблонов](store-content-web-templates.md)  
[Общие сведения об операторах жидкостей](liquid-operators.md)  
[Типы жидкостей](liquid-types.md)  
[Объекты жидкостей](liquid-objects.md)  
[Теги жидкостей](liquid-tags.md)  
[Фильтры жидкостей](liquid-filters.md)  
