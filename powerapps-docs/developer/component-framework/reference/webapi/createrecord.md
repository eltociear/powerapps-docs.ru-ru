---
title: СоздатьЗапись | Документация Майкрософт
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
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 9179f03b-9d26-4253-9535-13ab544d58ac
ms.openlocfilehash: f3a2b860f17d7efaaf8efebcf2418aef04478947
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340835"
---
# <a name="createrecord"></a>createRecord

[!INCLUDE [createrecord-description](includes/createrecord-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="syntax"></a>Синтаксис

`context.webAPI.createRecord(entityLogicalName, data).then(successCallback, errorCallback);`

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
<td>Логическое имя сущности, которую необходимо создать. Например: &quot;account &quot;.</td>
</tr>
<tr>
<td>Data</td>
<td>Объектами</td>
<td>Да</td>
<td><p>Объект JSON, определяющий атрибуты и значения для новой записи сущности.</p>
<p>См. примеры далее в этом разделе, чтобы узнать, как можно определить объект <code>data</code> для различных сценариев создания.</td>
</tr>
<tr>
<td>сукцесскаллбакк</td>
<td>Функция</td>
<td>Нет</td>
<td><p>Функция, вызываемая при создании записи. Для задания новой записи будут переданы объекты со следующими свойствами:</p>
<ul>
<li><b>EntityType</b>: String. Логическое имя сущности для новой записи.</li>
<li><b>идентификатор</b>: строка. Идентификатор GUID новой записи.</li>
</ul></td>
</tr>
<tr>
<td>ерроркаллбакк</td>
<td>Функция</td>
<td>Нет</td>
<td>Функция, вызываемая при сбое операции. Будет передан объект со следующими свойствами:
<ul>
<li><b>код ошибки</b>: число. Код ошибки.</li>
<li><b>сообщение</b>: строка. Сообщение об ошибке с описанием проблемы.</li>
</ul></td>
</tr>
</table>

## <a name="return-value"></a>Возвращаемое значение

Тип: [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) <[EntityReference](../entityreference.md) >

Описание: при успешном выполнении возвращает объект Promise, содержащий атрибуты, указанные ранее в описании параметра **сукцесскаллбакк** .

### <a name="related-topics"></a>Связанные статьи

[Веб-API](../webapi.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)