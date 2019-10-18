---
title: Ретриеверекорд | Документация Майкрософт
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
ms.assetid: dddeecc9-5067-420d-8bd7-4c914218e969
ms.openlocfilehash: 9c77bf9975bd1f1f115df9385061c008975cc184
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341709"
---
# <a name="retrieverecord"></a>retrieveRecord

[!INCLUDE [retrieverecord-description](includes/retrieverecord-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="syntax"></a>Синтаксис

`context.webAPI.retrieveRecord(entityLogicalName, id, options).then(successCallback, errorCallback);`

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
<td>Логическое имя сущности записи, которую требуется получить. Например: &quot;account &quot;.</td>
</tr>
<tr>
<td>Id</td>
<td>Строка</td>
<td>Да</td>
<td>Идентификатор GUID записи сущности, которую требуется получить.</td>
</tr>
<tr>
<td>Параметры</td>
<td>Строка</td>
<td>Нет</td>
<td><p>Параметры запросов к системе OData, <b>$SELECT</b> и <b>$expand</b>, чтобы получить данные.</p>
<ul><li>Используйте параметр системного запроса <b>$SELECT</b> , чтобы ограничить свойства, возвращаемые, включая список имен свойств с разделителями-запятыми. Это важная рекомендация по повышению производительности. Если свойства не указаны с помощью <b>$SELECT</b>, будут возвращены все свойства.</li>
<li>Используйте параметр системного запроса <b>$expand</b> , чтобы управлять тем, какие данные из связанных сущностей возвращаются. Если вы просто включили имя свойства навигации, вы получите все свойства для связанных записей. Можно ограничить свойства, возвращаемые для связанных записей, с помощью параметра <b>$SELECT</b> системного запроса в круглых скобках после имени свойства навигации. Используйте это как для свойств навигации с <i>одним значением</i> , так и со <i>значениями, возвращающими коллекцию</i> .</li>
</ul>
<p>Необходимо указать параметры запроса, начинающиеся с <code>?</code>. Можно также указать несколько параметров запроса, используя <code>&amp;</code> для разделения параметров запроса. Пример.</p>
<code>?$select=name&amp;$expand=primarycontactid($select=contactid,fullname)</code>
<p>См. примеры далее в этом разделе, чтобы увидеть, как можно определить параметр <code>options</code> для различных сценариев получения.</td>
</tr>
<tr>
<td>сукцесскаллбакк</td>
<td>Функция</td>
<td>Нет</td>
<td><p>Функция, вызываемая при извлечении записи. Объект JSON с извлеченными свойствами и значениями будет передан функции.</p>
</td>
</tr>
<tr>
<td>ерроркаллбакк</td>
<td>Функция</td>
<td>Нет</td>
<td>Функция, вызываемая при сбое операции.</td>
</tr>
</table>

## <a name="return-value"></a>Возвращаемое значение

Тип: <[сущности](../entity.md) [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) >



### <a name="related-topics"></a>Связанные статьи

[Веб-API](../webapi.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)