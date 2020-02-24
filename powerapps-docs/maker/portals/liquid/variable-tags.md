---
title: Использование тегов переменных для портала | Документация Майкрософт
description: Сведения о различных тегах переменных, доступных на портале
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: f9a56a9bccc8445dc7540f6ade402d5988ec1ffc
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978824"
---
# <a name="variable-tags"></a>Переменные теги

Переменные теги используются для создания новых переменных Liquid.

## <a name="assign"></a>назначить

Создает новую переменную. Назначения также могут использовать [фильтры](liquid-filters.md), чтобы изменить значение.  

**Код**

```
{% assign is_valid = true %}

{% if is_valid %}

It is valid.

{% endif %}

{% assign name = dave bowman' | upcase %}

{{ name }}
```

**Вывод**

```
It is valid.

DAVE BOWMAN
```

## <a name="capture"></a>захват

Захватывает содержимое в своем блоке и назначает его переменной. Это содержимое можно затем обрабатывать с помощью тегов вывода.

**Код**

```
{% capture hello %}Hello, {{ user.fullname }}.{% endcapture %}

{{ hello }}

{{ hello }}
```

**Вывод**

```
Hello, DAVE BOWMAN.

Hello, DAVE BOWMAN.
```

### <a name="see-also"></a>См. также

[Теги потока управления](control-flow-tags.md)<br>
[Теги итерирования](iteration-tags.md)<br>
[Теги шаблона](template-tags.md)<br>
[Теги сущности Common Data Service Power Apps](portals-entity-tags.md)
