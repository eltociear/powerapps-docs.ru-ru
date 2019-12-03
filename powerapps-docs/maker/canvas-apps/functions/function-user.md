---
title: Функция User | Документация Майкрософт
description: Справочные сведения, включая описание синтаксиса, о функции User в PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f95a6f7769cde01e99bc4c18fab0ae60ae6b8c96
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2019
ms.locfileid: "74680151"
---
# <a name="user-function-in-powerapps"></a>Функция User в PowerApps
Возвращает сведения о текущем пользователе.

## <a name="description"></a>Description
Функция **User** возвращает [запись](../working-with-tables.md#records) c информацией о текущем пользователе:

| Свойство | Description |
| --- | --- |
| **User().Email** |Адрес электронной почты текущего пользователя. |
| **User().FullName** |Полное имя текущего пользователя, то есть имя и фамилия. |
| **User().Image** |Изображение текущего пользователя. Здесь будет URL-адрес изображения в формате "blob:*идентификатор*". Чтобы отобразить это изображение в приложении, присвойте полученное значение параметру **[Image](../controls/properties-visual.md)** элемента управления **[Image](../controls/control-image.md)** . |

> [!NOTE]
> Возвращенная информация предназначена для текущего пользователя Power Apps.  Он будет соответствовать сведениям учетной записи, отображаемым в проигрывателях и студии Power Apps, которые можно найти за пределами всех созданных приложений.  Она может не совпадать с информацией о текущем пользователе Office 365 или других служб.

## <a name="syntax"></a>Синтаксис
**User**()

## <a name="examples"></a>Примеры
Текущий пользователь Power Apps имеет следующие сведения:

* полное имя — **John Doe**;
* адрес электронной почты — **"john.doe@contoso.com"** ;
* изображение — ![](media/function-user/john-doe-picture.png). 

|       Формула       |                                                                    Description                                                                    |                                                 Возвращаемый результат                                                  |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
|     **User()**      |                                             Запись всех сведений для текущего пользователя Power Apps.                                             |    {FullName:&nbsp;"John Doe", Email:&nbsp;"john.doe@contoso.com", Image:&nbsp;"blob:1234...5678"}    |
|  **User().Email**   |                                                 Адрес электронной почты текущего пользователя Power Apps.                                                  |                                         "john.doe@contoso.com"                                          |
| **User().FullName** |                                                   Полное имя текущего пользователя Power Apps.                                                    |                                               "John Doe"                                                |
|  **User().Image**   | URL-адрес изображения для текущего пользователя Power Apps.  Чтобы отобразить это изображение в приложении, присвойте полученное значение параметру **Image** элемента управления **Image**. | "blob:1234...5678"<br><br>С использованием **ImageControl.Image**:<br>![](media/function-user/john-doe-picture.png) |

