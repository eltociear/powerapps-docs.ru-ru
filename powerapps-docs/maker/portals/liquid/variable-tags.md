---
title: Использование тегов переменных для портала | Документация Майкрософт
description: Сведения о различных тегах переменных, доступных на портале
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: cdccf267000247a7363a05f72c3ccdd93abb6fd6
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2019
ms.locfileid: "2866282"
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
