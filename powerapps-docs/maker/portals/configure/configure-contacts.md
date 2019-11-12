---
title: Настройка контакта для использования на портале | MicrosoftDocs
description: Инструкции по добавлению и настройке контакта, который будет использоваться на портале.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 4a8c70304385007c132f2c13ec0ddca4b68e2231
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553194"
---
# <a name="configure-a-contact-for-use-on-a-portal"></a>Настройка контакта для использования на портале

После заполнения основных сведений о контакте (или при заполнении формы регистрации на портале) перейдите на вкладку "Проверка подлинности в Интернете" в форме "контакт" портала, чтобы настроить контакт с помощью локальной проверки подлинности. Дополнительные сведения о параметрах федеративной проверки подлинности см. [в разделе Настройка удостоверения проверки](set-authentication-identity.md)подлинности для портала. Чтобы настроить контакт для порталов с помощью локальной проверки подлинности, выполните следующие действия.  

1.  Введите **имя пользователя**.
2.  На ленте команд выберите **Дополнительные команды** &gt; **изменить пароль**.

Завершите рабочий процесс смены пароля, и необходимые поля будут настроены автоматически. После этого ваш контакт будет настроен для ваших порталов.

## <a name="change-password-for-a-contact-from-portal-management-app"></a>Изменение пароля для контакта из приложения управления порталом

1.  Откройте [приложение управления портала](configure-portal.md).

2.  Перейдите на **порталы** > **Контакты**и откройте контакт, для которого необходимо изменить пароль.
    Кроме того, можно также открыть страницу **Контакты** из панели [общий доступ](../manage-existing-portals.md#share) . 

3.  На панели инструментов в верхней части страницы выберите **последовательность задач** .

    > [!div class="mx-imgBorder"]
    > ![Значок потока задач](../media/task-flow.png "Значок потока задач")

4.  Выберите **изменить пароль для потока задач "Контактное лицо портала** ".

5.  В области **Сменить пароль для контакта портала** выберите или создайте контакт, чтобы изменить пароль, а затем нажмите кнопку **Далее**.

    > [!div class="mx-imgBorder"]
    > ![Выберите контакт для изменения пароля](../media/change-password-select-contact.png "Выберите контакт для изменения пароля")

6.  В поле **новый пароль** введите новый пароль, а затем нажмите кнопку **Далее**.

    > [!div class="mx-imgBorder"]
    > ![Введите новый пароль для контакта](../media/change-password-new-password.png "Введите новый пароль для контакта")

    Если не ввести пароль и нажать кнопку **Далее**, появится запрос на удаление пароля для выбранного контакта.

    > [!div class="mx-imgBorder"]
    > ![Удалить пароль для контакта](../media/change-password-remove-password.png "Удалить пароль для контакта")

7.  После внесения изменений нажмите кнопку **Готово**.


### <a name="see-also"></a>См. также
[Приглашение контактов на порталы](invite-contacts.md)  
[Настройка удостоверения для проверки подлинности на портале](set-authentication-identity.md)  