---
title: Функции EncodeUrl и PlainText | Документация Майкрософт
description: Справочные сведения, включая синтаксис и примеры, для функций Енкодеурл и обычного текста в Power Apps
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
ms.openlocfilehash: fe02683e0b420a97fe674543a2f0d16bb076f266
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731025"
---
# <a name="encodeurl-and-plaintext-functions-in-power-apps"></a>Функции Енкодеурл и обычного текста в Power Apps
Кодируют и декодируют строки.

## <a name="description"></a>Description
Функция **енкодеурл** кодирует строку URL-адреса, заменяя определенные символы, отличные от буквенно-цифровых, на% и шестнадцатеричное число.  

Функция с **открытым текстом** УДАЛЯЕТ теги HTML и XML, преобразуя некоторые теги, такие как, в соответствующий символ:

* **&amp;nbsp;**
* **&amp;quot;**

Возвращаемым значением этих функций является кодированная или декодированная строка. Эта функция не удаляет все теги HTML и XML. 

## <a name="syntax"></a>Синтаксис
**EncodeUrl**( *String* )

* *Строка* — обязательный аргумент.  URL-адрес, который необходимо кодировать.

**PlainText**( *String* )

* *Строка* — обязательный аргумент. Строка, из которой будут удалены HTML- и XML-теги.

## <a name="examples"></a>Примеры
Если показать RSS-канал в коллекции текста, а затем задать свойству **[Text](../controls/properties-core.md)** метки в этой коллекции значение **ThisItem.description**, то метка может отобразить необработанный HTML- или XML-код, как в этом примере:

```html
    <p>We have done an unusually&nbsp;&quot;deep&quot; globalization and localization.<p>
```

Если задать свойству **[Text](../controls/properties-core.md)** метки значение **PlainText(ThisItem.description)** , то отображаемый текст будет иметь такой вид:

```
    We have done an unusually "deep" globalization and localization.
```