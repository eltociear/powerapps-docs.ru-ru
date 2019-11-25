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
ms.openlocfilehash: fa375909ad3e909e70b3477d4e7ba0f24691fc0c
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "2707750"
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
[Теги сущности Common Data Service PowerApps](portals-entity-tags.md)
