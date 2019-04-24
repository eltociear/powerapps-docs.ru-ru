---
title: Функции EncodeUrl и PlainText | Документация Майкрософт
description: Справочные сведения о функциях EncodeUrl и PlainText в PowerApps, включая описание синтаксиса и примеры.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9956332c35b4df2773b2634cb7f66d2ea96469e4
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61551061"
---
# <a name="encodeurl-and-plaintext-functions-in-powerapps"></a>Функции EncodeUrl и PlainText в PowerApps
Кодируют и декодируют строки.

## <a name="description"></a>Описание
**EncodeUrl** функция кодирует строку URL-адреса, заменив некоторые отличные от буквенно-цифровые символы % и шестнадцатеричные числа.  

**Открытым текстом** функция удаляет HTML и XML-теги, преобразуя определенные теги, подобные этим в соответствующие символы:

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

    <p>We have done an unusually&nbsp;&quot;deep&quot; globalization and localization.<p>

Если задать свойству **[Text](../controls/properties-core.md)** метки значение **PlainText(ThisItem.description)**, то отображаемый текст будет иметь такой вид:

    We have done an unusually "deep" globalization and localization.
