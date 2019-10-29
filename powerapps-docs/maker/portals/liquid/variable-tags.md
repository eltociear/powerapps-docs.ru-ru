---
title: Использование тегов переменных для портала | MicrosoftDocs
description: Сведения о тегах переменных, доступных на портале
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: fa375909ad3e909e70b3477d4e7ba0f24691fc0c
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974421"
---
# <a name="variable-tags"></a>Теги переменных

Теги переменных используются для создания новых переменных ликвидности.

## <a name="assign"></a>назначать

Создает новую переменную. Назначения также могут использовать [фильтры](liquid-filters.md) для изменения значения.  

**Приведен**

```
{% assign is_valid = true %}

{% if is_valid %}

It is valid.

{% endif %}

{% assign name = dave bowman' | upcase %}

{{ name }}
```

**Проверки**

```
It is valid.

DAVE BOWMAN
```

## <a name="capture"></a>выделяем

Захватывает содержимое в блоке и присваивает его переменной. Затем это содержимое можно визуализировать позже с помощью выходных тегов.

**Приведен**

```
{% capture hello %}Hello, {{ user.fullname }}.{% endcapture %}

{{ hello }}

{{ hello }}
```

**Проверки**

```
Hello, DAVE BOWMAN.

Hello, DAVE BOWMAN.
```

### <a name="see-also"></a>См. также

[Теги потока управления](control-flow-tags.md)<br>
[Теги итерации](iteration-tags.md)<br>
[Теги шаблона](template-tags.md)<br>
[Теги сущности Common Data Service PowerApps](portals-entity-tags.md)
