---
title: Упдатерекорд | Документация Майкрософт
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
ms.assetid: 179ced61-ff0f-45ef-aa14-835ce99532cf
ms.openlocfilehash: 96037bcd8ca43448e928abef714ae031222d8e98
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340697"
---
# <a name="updaterecord"></a>updateRecord

[!INCLUDE [updaterecord-description](includes/updaterecord-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="syntax"></a>Синтаксис

`context.webAPI.updateRecord(entityLogicalName, id, data).then(successCallback, errorCallback);`

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
<td>Логическое имя сущности записи, которую необходимо обновить. Например: &quot;account &quot;.</td>
</tr>
<tr>
<td>Id</td>
<td>Строка</td>
<td>Да</td>
<td>Идентификатор GUID записи сущности, которую требуется обновить.</td>
</tr>
<tr>
<td>Data</td>
<td>Объектами</td>
<td>Да</td>
<td><p>Объект JSON, содержащий пары <code>key: value</code>, где <code>key</code> является свойством сущности и <code>value</code> — Это значение свойства, которое необходимо обновить.</p>
<p>См. примеры далее в этом разделе, чтобы увидеть, как можно определить объект <code>data</code> для различных сценариев обновления.</td>
</tr>
<tr>
<td>сукцесскаллбакк</td>
<td>Функция</td>
<td>Нет</td>
<td><p>Функция, вызываемая при обновлении записи. Для обнаружения обновленной записи будут переданы объекты со следующими свойствами:</p>
<ul>
<li><b>EntityType</b>: String. Тип сущности обновленной записи.</li>
<li><b>идентификатор</b>: строка. Идентификатор GUID обновленной записи.</li>
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

Тип: [Promise] ((датеформаттингинфо. md) <[Entityreference](../entityreference.md) >

Описание: при успешном выполнении возвращает объект Promise, содержащий атрибуты, указанные ранее в описании параметра **сукцесскаллбакк** .


### <a name="related-topics"></a>Связанные статьи

[Веб-API](../webapi.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)