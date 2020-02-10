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
ms.openlocfilehash: 259ab99ca38a472fda5c8cd8cdf99533a5f5dfc2
ms.sourcegitcommit: 80120b59d440bb7a3ddca93cd51154607f749f6b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "77089749"
---
# <a name="encodeurl-and-plaintext-functions-in-power-apps"></a>Функции Енкодеурл и обычного текста в Power Apps
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

* *Строка* — обязательный аргумент. Строка, из которой будут удалены HTML- и XML-теги.

## <a name="examples"></a>Примеры
Если показать RSS-канал в коллекции текста, а затем задать свойству **[Text](../controls/properties-core.md)** метки в этой коллекции значение **ThisItem.description**, то метка может отобразить необработанный HTML- или XML-код, как в этом примере:

```html
    <p>We have done an unusually&nbsp;&quot;deep&quot; globalization and localization.</p>
```

Если задать свойству **[Text](../controls/properties-core.md)** метки значение **PlainText(ThisItem.description)** , то отображаемый текст будет иметь такой вид:

```
    We have done an unusually "deep" globalization and localization.
```