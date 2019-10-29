---
title: Использование тегов потока управления для портала | MicrosoftDocs
description: Сведения о тегах потока управления, доступных на портале.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 77fcc7db0adf68cd6decbcc95e11d8e803761535
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975111"
---
# <a name="control-flow-tags"></a>Теги потока управления

Теги потока управления определяют, какой блок кода следует выполнить и какое содержимое должно быть визуализировано на основе заданных условий. Условия создаются с помощью доступных [операторов ликвидности](liquid-operators.md)или только на основе [истинности или фалсехуд заданной величины](liquid-conditional-operators.md).  

## <a name="if"></a>наличии

Выполняет блок кода, если заданное условие выполнено.

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% endif %}
```

## <a name="unless"></a>иное

Like, если, за исключением того, что выполняет блок кода, если заданное условие**не** выполнено.

```
{% unless page.title == 'Home' %}

This is not the Home page.

{% endunless %}
```

## <a name="elsifelse"></a>елсиф/else

Добавляет дополнительные условия в блок if или, если он не указан.

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% elsif user.fullname == 'John Smith' %}

Hello, Mr. Smith.

{% else %}

Hello, stranger.

{% endif %}
```

## <a name="casewhen"></a>Регистр/когда

Оператор switch для сравнения переменной с различными значениями и выполнения другого блока кода для каждого значения.

```
{% case user.fullname %}

{% when 'Dave Bowman' %}

Hello, Dave.

{% when 'John Smith' %}

Hello, Mr. Smith.

{% else %}

Hello, stranger.

{% endcase %}
```

### <a name="see-also"></a>См. также

[Теги итерации](iteration-tags.md)<br>
[Теги переменных](variable-tags.md)<br>
[Теги шаблона](template-tags.md)<br>
[Теги сущности Common Data Service PowerApps](portals-entity-tags.md)
