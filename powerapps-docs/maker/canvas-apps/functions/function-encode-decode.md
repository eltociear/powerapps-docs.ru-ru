---
title: Функции EncodeUrl и PlainText | Документация Майкрософт
description: Справочные сведения о функциях EncodeUrl и PlainText в PowerApps, включая описание синтаксиса и примеры.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c21cae9e39e3a9a1461ac3fafe576f40b70c0818
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "71985015"
---
# <a name="encodeurl-and-plaintext-functions-in-powerapps"></a>Функции EncodeUrl и PlainText в PowerApps
Кодируют и декодируют строки.

## <a name="description"></a>Описание
Функция **енкодеурл** кодирует строку URL-адреса, заменяя определенные символы, отличные от буквенно-цифровых, на% и шестнадцатеричное число.  

Функция с **открытым текстом** УДАЛЯЕТ теги HTML и XML, преобразуя некоторые теги, такие как, в соответствующий символ:

* **&amp;nbsp;**
* **&amp;quot;**

Возвращаемым значением этих функций является кодированная или декодированная строка. Эта функция не удаляет все теги HTML и XML. 

## <a name="syntax"></a>Синтаксис
**EncodeUrl**( *String* )

* *Строка* — обязательный аргумент.  URL-адрес, который необходимо кодировать.

**PlainText**( *String* )

* *строка* — обязательный аргумент. Строка, из которой будут удалены HTML- и XML-теги.

## <a name="examples"></a>Примеры
Если показать RSS-канал в коллекции текста, а затем задать свойству **[Text](../controls/properties-core.md)** метки в этой коллекции значение **ThisItem.description**, то метка может отобразить необработанный HTML- или XML-код, как в этом примере:

```html
    <p>We have done an unusually&nbsp;&quot;deep&quot; globalization and localization.<p>
```

Если задать свойству **[Text](../controls/properties-core.md)** метки значение **PlainText(ThisItem.description)** , то отображаемый текст будет иметь такой вид:

```
    We have done an unusually "deep" globalization and localization.
```