---
title: UserSettings | Документация Майкрософт
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
ms.assetid: c237ff96-9268-4068-9d61-aea0bdc79fc2
ms.openlocfilehash: 5325091d8f82ffd98cfc4e5fdab4e0228a5d541e
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341042"
---
# <a name="usersettings"></a>UserSettings

[!INCLUDE [usersettings-description](includes/usersettings-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="properties"></a>Свойства

### <a name="dateformattinginfo"></a>датеформаттингинфо

Сведения о форматировании даты, полученные с сервера.

**Тип**: [датеформаттингинфо](dateformattinginfo.md)

### <a name="isrtl"></a>исртл

Возвращает значение true, если язык расположен справа налево.

**Тип**: `boolean`

### <a name="languageid"></a>languageId

Идентификатор языка текущего пользователя.

**Тип**: `number`

### <a name="numberformattinginfo"></a>нумберформаттингинфо

Сведения о форматировании чисел, полученные с сервера.

**Тип**: [нумберформаттингинфо](numberformattinginfo.md)

### <a name="securityroles"></a>секуритиролес

Текущие роли пользователей.

**Тип**: `string[]`

### <a name="userid"></a>userId

Идентификатор текущего пользователя.

**Тип**: `string`

### <a name="username"></a>userName

Имя пользователя текущего пользователя.

**Тип**: `string`

## <a name="methods"></a>Метод

|Method | Description | 
| ------|-------------|
|[жеттимезонеоффсетминутес](usersettings/gettimezoneoffsetminutes.md)|[!INCLUDE [gettimezoneoffsetminutes-description](usersettings/includes/gettimezoneoffsetminutes-description.md)]|

### <a name="related-topics"></a>Связанные статьи

[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)