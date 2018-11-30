---
title: Функции First, FirstN, Last и LastN | Документация Майкрософт
description: Справочные сведения о функциях First, FirstN, Last и LastN в PowerApps, включая описание синтаксиса и примеры.
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
ms.openlocfilehash: b191e41db1b8d49d61b48a8a24dbf22101c18a68
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "42844191"
---
# <a name="first-firstn-last-and-lastn-functions-in-powerapps"></a>Функции First, FirstN, Last и LastN в PowerApps
Возвращает первый или последний набор [записей](../working-with-tables.md#records) таблицы.

## <a name="description"></a>Описание
Функция **First** возвращает первую запись [таблицы](../working-with-tables.md).

Функция **FirstN** возвращает первый набор записей таблицы; второй аргумент задает количество возвращаемых записей.

Функция **Last** возвращает последнюю запись таблицы.

Функция **LastN** возвращает последний набор записей таблицы; второй аргумент задает количество возвращаемых записей.

Функции **First** и **Last** возвращают одну запись.  Функции **FirstN** и **LastN** возвращают таблицу, даже если указать только одну запись.

[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>Синтаксис
**First**( *Таблица* )<br>**Last**( *Таблица* )

* *Таблица* — обязательный аргумент. Таблица, для которой выполняется операция.

**FirstN**( *Таблица* [, *Число_записей* ] )<br>**LastN**( *Таблица* [, *Число_записей* ] )

* *Table* — обязательный аргумент. Таблица, для которой выполняется операция.
* *Число_записей* — необязательный аргумент.  Количество возвращаемых записей. Если не указать этот аргумент, то функция возвратит одну запись.

## <a name="examples"></a>Примеры
Эта формула возвращает первую запись из таблицы с именем **Employees**:<br>
**First(Employees)**

Эта формула возвращает последние 15 записей из таблицы с именем **Employees**:<br>
**LastN(Employees, 15)**

