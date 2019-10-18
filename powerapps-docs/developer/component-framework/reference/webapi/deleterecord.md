---
title: Делетерекорд | Документация Майкрософт
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5c9968bf-d535-425c-b1f1-0db6b7822de1
ms.openlocfilehash: f6c8dd6ea7d156e28ab3ae54d7fe37dad6c4546a
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340766"
---
# <a name="deleterecord"></a>deleteRecord

[!INCLUDE [deleterecord-description](includes/deleterecord-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="syntax"></a>Синтаксис

`context.webAPI.deleteRecord(entityLogicalName, id).then(successCallback, errorCallback);`

## <a name="parameters"></a>Вход

<table style="width:100%">
<tr>
<th>Имя</th>
<th>Тип</th>
<th>Требуется</th>
<th>Description</th>
</tr>
<tr>
<td>ентитилогикалнаме</td>
<td>Строка</td>
<td>Да</td>
<td>Логическое имя сущности записи, которую необходимо удалить. Например: &quot;account &quot;. </td>
</tr>
<tr>
<td>Id</td>
<td>Строка</td>
<td>Да</td>
<td>Идентификатор GUID записи сущности, которую необходимо удалить.</td>
</tr>
<tr>
<td>сукцесскаллбакк</td>
<td>Функция</td>
<td>Нет</td>
<td><p>Функция, вызываемая при удалении записи. Для задания удаленной записи будут переданы объекты со следующими свойствами:</p>
<ul>
<li><b>EntityType</b>: String. Тип сущности записи.</li>
<li><b>идентификатор</b>: строка. Идентификатор GUID записи.</li>
<li><b>имя</b>: строка. Имя записи.</li>
</ul></td>
</tr>
<tr>
<td>ерроркаллбакк</td>
<td>Функция</td>
<td>Нет</td>
<td>Функция, вызываемая при сбое операции.</td>
</tr>
</table>

## <a name="return-value"></a>Возвращаемое значение

Тип: [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) <[EntityReference](../entityreference.md) >

### <a name="related-topics"></a>Связанные статьи

[Веб-API](../webapi.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)