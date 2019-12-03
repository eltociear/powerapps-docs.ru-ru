---
title: Функция User | Документация Майкрософт
description: Справочные сведения, включая синтаксис, для пользовательской функции в Power Apps
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
ms.openlocfilehash: d4c558e40b9bb351f3ea6b4d202ef4849cb4e85d
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74729880"
---
# <a name="user-function-in-power-apps"></a>Пользовательская функция в Power Apps
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

