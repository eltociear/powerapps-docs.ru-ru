---
title: Шаблон экрана собрания | Документация Майкрософт
description: Понять, как работает шаблон экрана собрания для приложений на основе холста и расширять на экране для собственных вариантов использования
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/30/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 24f04ff9ce95f603f5f7d4dc7d217146b9eebef8
ms.sourcegitcommit: 5e15a1033a68289781f8092fb65c57432501f911
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54459419"
---
# <a name="overview-of-the-meeting-screen-template-for-canvas-apps"></a>Общие сведения о шаблоне собрания экрана для приложений на основе холста

В приложение на основе холста добавьте экран собрания, позволяет пользователям создавать и отправлять приглашения на собрания из учетной записи Office 365 Outlook. Пользователей можно найти участников в своей организации и добавьте внешние адреса электронной почты. Если у клиента есть помещений для собраний встроенный в Outlook, пользователи могут выбрать расположение также.

Вы также можете добавить другие экраны на базе шаблона, такие как отображение различных данных из Office 365, [электронной почты](email-screen-overview.md), [людей](people-screen-overview.md) в организации и пользователя [календаря](calendar-screen-overview.md).

В этом обзоре изучении общие функциональные возможности экрана.

Подробные сведения о функции по умолчанию этот экран, см. в разделе [собрания экранах](meeting-screen-reference.md).

## <a name="prerequisite"></a>Необходимое условие

Знакомство с тем, как добавить и настроить экраны и другие элементы управления, как вы [Создание приложения в PowerApps](../data-platform-create-app-scratch.md).

## <a name="default-functionality"></a>Стандартная функциональность

Добавление экрана собрания из шаблона:

1. [Войдите в](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) в PowerApps, для создания приложения или откройте существующее приложение в PowerApps Studio.

    В этом разделе показано приложение для телефона, но те же принципы применимы к приложение для планшета.

1. На **Главная** вкладке на ленте выберите **новый экран** > **собрания**.

  При заполнении обеих вкладках экрана собрания выглядеть примерно следующим образом:

  ![Экран собрания, обеих вкладках](media/meeting-screen/meeting-screen-full-both.png)

Несколько полезные примечания:

* На экране собрания позволяет пользователю приложения создавать встречи в Outlook.
  Пользователи могут искать и добавлять участников и, при необходимости добавьте конференц-зала на собрание.
* Для поиска пользователя в организации, начните вводить его имя в поле ввода текста в группе «Участники».
* Когда поиск людей, возвращаются только 15 результатов.
* Добавьте адреса электронной почты для участников за пределами вашей организации, введите адрес электронной почты полное, допустимые и выберите значок «+», который отображается справа от адрес электронной почты.
* Чтобы создать встречу, необходимо добавить по крайней мере один пользователь в качестве участника, укажите тему и времени собрания в **расписание** вкладки.
* После отправки приглашения на собрание, все данные для этого собрания очищается.
* **OnSelect** инструкция значка отправки (в правом верхнем углу) содержит следующую формулу:
    ```powerapps-dot
    Set( _myCalendarName, 
        LookUp( 'Office365'.CalendarGetTables().value, DisplayName = "Calendar" ).Name 
    );
    ```
* «Calendar» — отображаемое имя по умолчанию для большинства Office календарей пользователя, но организации могут отличаться. Если Да, «Calendar» можно изменить на соответствующий срок использования вашей организации.
* Сообщение об ошибке при попытке назначить встречу, возникающее в прошлом или добавить более 20 человек на собрание.

## <a name="next-steps"></a>Дальнейшие действия

* [Для этого экрана справочной документации по](./meeting-screen-reference.md).
* [Дополнительные сведения о соединителе Office 365 Outlook](../connections/connection-office365-outlook.md).
* [Дополнительные сведения о соединителе пользователи Office 365](../connections/connection-office365-users.md).