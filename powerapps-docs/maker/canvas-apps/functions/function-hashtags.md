---
title: Функция HashTags | Документация Майкрософт
description: Справочные сведения о функции HashTags в PowerApps, включая описание синтаксиса и примеры
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
ms.openlocfilehash: d29fa336ae96a164a6f189010c66deff970ba5a7
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "71984897"
---
# <a name="hashtags-function-in-powerapps"></a>Функция HashTags в PowerApps
Извлекает хэш-теги (#string — строки) из строки или текста.

## <a name="description"></a>Описание
Функция **HashTags** проверяет строку на наличие хэш-тегов. Хэш-теги начинаются с символа решетки (#), после которого следует комбинация из:

* прописных и строчных букв;
* цифр;
* символов подчеркивания;
* символов валют (например, $).

Функция **HashTags** возвращает [таблицу](../working-with-tables.md) с одним столбцом, в которой содержатся хэш-теги из строки.  Если в строке нет хэш-тегов, функция возвращает [пустую](function-isblank-isempty.md) таблицу с одним столбцом.

## <a name="syntax"></a>Синтаксис
**HashTags**( *String* )

* *String* — обязательный аргумент.  Строка, проверяемая на наличие хэш-тегов.

## <a name="examples"></a>Примеры
### <a name="step-by-step"></a>Шаг за шагом
1. Добавьте элемент управления **[Текстовое поле](../controls/control-text-input.md)** , назовите его **Tweet** и введите следующее предложение:
   
    **Это #приложение #ПРОСТО_СУПЕР и может #сЧитать123 или #123абв, но не #1–23 и не #$\*(#\@")**
2. Добавьте вертикальную пользовательскую коллекцию и задайте для свойства **[Items](../controls/properties-core.md)** следующую функцию:
   
    **HashTags(Tweet.Text)**
3. Добавьте элемент управления **[Метка](../controls/control-text-box.md)** к шаблону коллекции.
   
    В коллекции отобразятся такие хэш-теги:
   
   * **\#приложение**;
   * **\#ПРОСТО_СУПЕР**;
   * **\#сЧитать123**;
   * **\#123абв**;
   * **\#1**.

