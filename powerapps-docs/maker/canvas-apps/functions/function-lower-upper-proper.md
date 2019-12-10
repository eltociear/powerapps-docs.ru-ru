---
title: Функции Lower, Upper и Proper | Документация Майкрософт
description: Справочные сведения, включая синтаксис и примеры, для нижних, верхних и правильных функций в Power Apps
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
ms.openlocfilehash: 115b5e51f816778d763481999f8f487a1d64037a
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730590"
ms.PowerAppsDecimalTransform: true
---
# <a name="lower-upper-and-proper-functions-in-power-apps"></a>Нижние, верхние и правильные функции в Power Apps
Преобразуют буквы текстовой строки во все строчные, все прописные или в правильный регистр.

## <a name="description"></a>Description
Функции **Lower**, **Upper** и **Proper** преобразуют регистр букв в строках.

* **Lower** преобразует все прописные буквы в строчные.
* **Upper** преобразует все строчные буквы в прописные.
* **Proper** преобразует первую букву каждого слова в прописную, если она строчная, и преобразует все остальные прописные буквы в строчные.

Все три функции игнорируют символы, которые не являются буквами.

Если передать одну строку, возвращается преобразованная версия этой строки.  При передаче [таблицы](../working-with-tables.md) из одного столбца, содержащей строки, возвращается таблица из одного столбца с преобразованными строками. Таблицу с несколькими столбцами можно преобразовать в таблицу с одним столбцом, как описано в статье об [использовании таблиц](../working-with-tables.md).

## <a name="syntax"></a>Синтаксис
**Lower**( *строка* )<br>**Upper**( *строка* )<br>**Proper**( *строка* )

* *Строка* — обязательный аргумент. Строка для преобразования.

**Lower**( *таблица_из_одного_столбца* )<br>**Upper**( *таблица_из_одного_столбца* )<br>**Proper**( *таблица_из_одного_столбца* )

* *SingleColumnTable* — обязательный аргумент. Таблица из одного столбца со строками для преобразования.

## <a name="examples"></a>Примеры
### <a name="single-string"></a>Одна строка
Примеры в этом разделе используют элемент управления для ввода текста с именем **Author** в качестве [источника данных](../working-with-data-sources.md). Элемент управления содержит строку "И. И. ИваНОВ".

| Формула | Description | Возвращаемый результат |
| --- | --- | --- |
| **Lower(&nbsp;Author.Text&nbsp;)** |Преобразует все прописные буквы в строке в строчные. |"и. и. иванов" |
| **Upper(&nbsp;Author.Text&nbsp;)** |Преобразует все строчные буквы в строке в прописные. |"И. И. ИВАНОВ" |
| **Proper(&nbsp;Author.Text&nbsp;)** |Преобразует первую букву каждого слова в прописную, если она строчная, а остальные прописные буквы преобразует в строчные. |"И. И. Иванов" |

### <a name="single-column-table"></a>Для таблицы с одним столбцом
Примеры в этом разделе преобразуют строки из **столбца** [Address](../working-with-tables.md#columns) источника данных **People**, который содержит такие данные:

![](media/function-lower-upper-proper/people-table.png)

Каждая формула возвращает таблицу из одного столбца, содержащую преобразованные строки.

| Формула | Description | Возвращаемый результат |
| --- | --- | --- |
| **Lower( ShowColumns(&nbsp;People;&nbsp;"Address"&nbsp;) )** |Преобразует все строчные буквы в прописные. |<style> img { max-width:none; } </style> ![](media/function-lower-upper-proper/people-table-lower.png) |
| **Upper( ShowColumns(&nbsp;People;&nbsp;"Address"&nbsp;) )** |Преобразует все строчные буквы в прописные. |![](media/function-lower-upper-proper/people-table-upper.png) |
| **Proper( ShowColumns(&nbsp;People;&nbsp;"Address"&nbsp;) )** |Преобразует все первые буквы слов из строчных в прописные, а все другие буквы — из прописных в строчные. |![](media/function-lower-upper-proper/people-table-proper.png) |

### <a name="step-by-step-example"></a>Пошаговый пример
1. Добавьте элемент управления **[Текстовое поле](../controls/control-text-input.md)** и назовите его **Source**.
2. Добавьте метку и установите в ее свойстве **[Text](../controls/properties-core.md)** такую функцию:<br>**Proper(Source.Text)**
3. Нажмите клавишу F5, а затем введите **МЫ — ЛУЧШИЕ!** в поле **Source**.<br>На метке будет показано **Мы — Лучшие!**

