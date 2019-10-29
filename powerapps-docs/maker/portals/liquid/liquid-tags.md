---
title: Использование тегов жидкостей для портала | MicrosoftDocs
description: Сведения о доступных тегах жидкостей на портале.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b04c6447911d1a884627bd2cbb4ad7b74b9c5ce5
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976560"
---
# <a name="available-liquid-tags"></a>Доступные теги Liquid

Теги составляют логику программирования, которая сообщает шаблонам, что делать. Теги упакованы в {%%}.

```
{% if user.fullname == 'Dave Bowman' %} Hello, Dave. {% endif %}
```

## <a name="whitespace-control"></a>Элемент управления "пробелы"

Как правило, жидкость отображает все, за пределами переменных и блоков тегов, и все пробелы как есть. Иногда вам не нужно излишних пробелов, но вы по-прежнему хотите форматировать шаблон аккуратно, что требует пробелов.

Можно указать обработчику удалить все начальные или конечные пробелы, добавив дефис (-) в тег начального или конечного блока.

**Приведен**

```
{% for i in (1..5) --%}

{{ i }}

{%-- endfor %}
```

**Проверки**

```
12345
```
### <a name="see-also"></a>См. также

[Типы жидкостей](liquid-types.md)  
[Объекты жидкостей](liquid-objects.md)  
[Фильтры жидкостей](liquid-filters.md) 
