---
title: Функция Table | Документация Майкрософт
description: Справочные сведения, включая описание синтаксиса и примеры, относительно функции Table в PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2388df10fbc735f619497dc9b93dd049c8a46afa
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2019
ms.locfileid: "74680105"
ms.PowerAppsDecimalTransform: true
---
# <a name="table-function-in-powerapps"></a>Функция Table в PowerApps
Создание временной [таблицы](../working-with-tables.md).

## <a name="description"></a>Description
Функция **Table** создает таблицу на основе списка аргументов-[записей](../working-with-tables.md#records).

В [столбцах](../working-with-tables.md#columns) таблицы объединяются все свойства записей из списка аргументов. В столбец, для которого у записи нет значения, добавляется *пустое* значение.

Таблица — это значение в Power Apps, как строка или число. Таблицы можно использовать в качестве аргументов для функций, и функции могут возвращать таблицу. Функция **Table** не создает постоянную таблицу. Вместо этого она возвращает временную таблицу, сформированную на основе аргументов.  Эту временную таблицу можно передать в качестве аргумента другой функции, визуализировать в коллекции или встроить в другую таблицу.  Подробнее это описано [здесь](../working-with-tables.md).

Вы также можете создать таблицу из одного столбца с помощью синтаксической конструкции **[значение_1; значение_2; ...]** .

## <a name="syntax"></a>Синтаксис
**Table**(*запись_1*[; *запись_2*; ...])

* *Record(s)*  — обязательный аргумент. Записи, добавляемые в таблицу.

## <a name="examples"></a>Примеры
* Задайте для свойства **[Items](../controls/properties-core.md)** (Элементы) списка следующую формулу:
  <br>**Table({Color:"red"}; {Color:"green"}; {Color:"blue"})**
  
    В списке каждый цвет отображается в виде варианта для выбора.
* Добавьте текстовую коллекцию и установите для свойства **[Items](../controls/properties-core.md)** (Элементы) следующую функцию:<br>
  **Table({Item:"Violin123"; Location:"France"; Owner:"Fabrikam"}; {Item:"Violin456"; Location:"Chile"})**
  
    В коллекции две записи, обе из которых содержат наименование и местоположение объекта. При этом только одна запись содержит имя владельца.

