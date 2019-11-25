---
title: Использование тегов потока управления для портала | Документация Майкрософт
description: Узнайте о тегах потоков управления, доступных на портале.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 77fcc7db0adf68cd6decbcc95e11d8e803761535
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "2708586"
---
# <a name="control-flow-tags"></a>Теги потока управления

Теги потока управления определяют, какой блок кода должен исполняться и какое содержимое должно отображаться на основе заданных условий. Условия построены с использованием доступных [операторов Liquid](liquid-operators.md), или только основанных на [правильности или ложности указанного значения](liquid-conditional-operators.md).  

## <a name="if"></a>if

Выполняет блок кода, если заданное условие выполнено.

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% endif %}
```

## <a name="unless"></a>unless

Как if, но выполняет блок кода, если заданное условие **не** выполнено.

```
{% unless page.title == 'Home' %}

This is not the Home page.

{% endunless %}
```

## <a name="elsifelse"></a>elsif/else

Добавляет больше условий в блок if или unless.

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% elsif user.fullname == 'John Smith' %}

Hello, Mr. Smith.

{% else %}

Hello, stranger.

{% endif %}
```

## <a name="casewhen"></a>case/when

Оператор переключателя для сравнения переменной с другими значениями и выполнения разных блоков кода для каждого значения.

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

[Теги итерирования](iteration-tags.md)<br>
[Переменные теги](variable-tags.md)<br>
[Теги шаблона](template-tags.md)<br>
[Теги сущности Common Data Service PowerApps](portals-entity-tags.md)
