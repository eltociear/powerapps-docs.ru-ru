---
title: Функция User | Документация Майкрософт
description: Справочные сведения, включая описание синтаксиса, о функции User в PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f452fedfbb26394bcaf4d490fa608f066469fb53
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61544568"
---
# <a name="user-function-in-powerapps"></a>Функция User в PowerApps
Возвращает сведения о текущем пользователе.

## <a name="description"></a>Описание
Функция **User** возвращает [запись](../working-with-tables.md#records) c информацией о текущем пользователе:

| Свойство | Описание |
| --- | --- |
| **User().Email** |Адрес электронной почты текущего пользователя. |
| **User().FullName** |Полное имя текущего пользователя, то есть имя и фамилия. |
| **User().Image** |Изображение текущего пользователя. Здесь будет URL-адрес изображения в формате "blob:*идентификатор*". Чтобы отобразить это изображение в приложении, присвойте полученное значение параметру **[Image](../controls/properties-visual.md)** элемента управления **[Image](../controls/control-image.md)** . |

> [!NOTE]
> Информация возвращается для текущего пользователя PowerApps.  Она будет совпадать с информацией раздела со сведениями об учетной записи, которая отображается в проигрывателях и студии PowerApps и доступна вне создаваемых приложений.  Она может не совпадать с информацией о текущем пользователе Office 365 или других служб.

## <a name="syntax"></a>Синтаксис
**User**()

## <a name="examples"></a>Примеры
Текущий пользователь PowerApps, о котором есть следующая информация:

* Полное имя: **«John Doe»**
* адрес электронной почты — **"john.doe@contoso.com"** ;
* изображение — ![](media/function-user/john-doe-picture.png). 

|       Формула       |                                                                    Описание                                                                    |                                                 Возвращаемый результат                                                  |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
|     **User()**      |                                             Запись со всеми данными для текущего пользователя PowerApps.                                             |    {FullName:&nbsp;"John Doe", Email:&nbsp;"john.doe@contoso.com", Image:&nbsp;"blob:1234...5678"}    |
|  **User().Email**   |                                                 Адрес электронной почты текущего пользователя PowerApps.                                                  |                                         "john.doe@contoso.com"                                          |
| **User().FullName** |                                                   Полное имя текущего пользователя PowerApps.                                                    |                                               "John Doe"                                                |
|  **User().Image**   | URL-адрес изображения текущего пользователя PowerApps.  Чтобы отобразить это изображение в приложении, присвойте полученное значение параметру **Image** элемента управления **Image**. | "blob:1234...5678"<br><br>С использованием **ImageControl.Image**:<br>![](media/function-user/john-doe-picture.png) |

