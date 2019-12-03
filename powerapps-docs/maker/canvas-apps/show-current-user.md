---
title: Показ сведений о текущем пользователе в приложении на основе холста | Документы Майкрософт
description: В Power Apps отобразите имя и адрес электронной почты пользователя, выполнившего вход, в приложении Canvas.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/16/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f77ec80cfaf579c836277f0e29d3b84b325a0462
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2019
ms.locfileid: "74674608"
---
# <a name="show-information-about-a-power-apps-user-in-a-canvas-app"></a>Отображение сведений о пользователе Power Apps в приложении Canvas

В Power Apps отобразите полное имя, адрес электронной почты и рисунок, связанный с пользователем, который вошел в приложение Canvas. Эти сведения можно использовать, например, для автоматического заполнения какой-то формы.

Например, можно использовать эту функцию для следующего.

* Создание регистрационной формы для пользователей, предназначенной для посещения учебных занятий, добровольного участия в мероприятиях, регистрации в киоске и многого другого.
* Отображение полного имени в приложении для отдела кадров.
* Автоматически ввод электронного адреса при обращении в службу поддержки.

По сути, эту возможность можно применять везде, где пользователям удобно использовать формы или метки, которые заполняются автоматически.

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]

## <a name="show-user-details"></a>Отображение сведений о пользователе

1. На вкладке **Вставка** щелкните или коснитесь **Мультимедиа**, а затем — **Изображение**.
   
   ![][2]
2. Задайте для свойства **[Image](controls/properties-visual.md)** следующую формулу.
   <br>**User().Image**
   
    ![][3]
3. На вкладке **Вставка** щелкните или коснитесь **Текст**, а затем — **Метка**.  
   
    ![][4]
4. Для свойства **[Text](controls/properties-core.md)** задайте следующую формулу.
   <br>**User().FullName**
   
   ![][6]
   
   При этом в метке автоматически появится ваше полное имя. Переместите метку под элемент управления "Изображение", как показано ниже.
   
   ![][5]
5. Добавьте другую метку и установите в ее свойстве **[Text](controls/properties-core.md)** формулу:
   <br>**User().Email**  
   
    ![][8]
   
    При этом в метке автоматически появится ваш электронный адрес. Переместите метку под первую метку, как показано ниже.  
   
    ![][7]

[2]: ./media/show-current-user/add-image.png
[3]: ./media/show-current-user/imageproperty.png
[4]: ./media/show-current-user/insertlabel.png
[5]: ./media/show-current-user/label.png
[6]: ./media/show-current-user/textproperty.png
[7]: ./media/show-current-user/secondlabel.png
[8]: ./media/show-current-user/email.png
[9]: ./media/show-current-user/preview.png
