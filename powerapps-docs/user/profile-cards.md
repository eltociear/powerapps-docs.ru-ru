---
title: Просмотр карточки профиля для контакта или пользователя | Документация Майкрософт
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/03/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 276c7d3cbf95947306fab768da8af3c4c66b33e0
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543374"
---
# <a name="view-the-profile-card-for-a-contact-or-user"></a>Просмотр карточки профиля для контакта или пользователя

Используйте карточку профиля для получения кратких сведений о контакте или пользователе. При выборе поля контакта или пользователя в приложениях на основе модели в Dynamics 365, таких как Dynamics 365 Sales и Dynamics 365 Customer Service, можно найти сведения, связанные с ними, в карточке профиля. Дополнительные сведения о карточках профилей см. в статье [Карточки профиля в Office 365](https://support.office.com/article/Profile-cards-in-Office-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501).

> [!NOTE]
>  - Карточка профиля доступна для сущностей **Контакт** и **Пользователь**. Дополнительные сведения см. в разделе [Включение карточки профиля (для администраторов)](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-profile-card).
>  - Карточка профиля в Common Data Service не отображается, если для службы Office Delve включена многофакторная проверка подлинности в Azure Active Directory.

## <a name="view-a-contacts-profile"></a>Просмотр профиля контакта

1.  Выберите **Действия**.
2.  Создайте действие или выберите имеющееся.
3.  Наведите указатель мыши на поле **Позвонить**, если у него есть запись контакта. 

Вы можете просмотреть сведения о контакте, включая его фотографию, имя, должность и учетную запись.

4. Чтобы просмотреть дополнительные сведения, выберите **Показать больше** и разверните профиль контакта.
 
    > [!div class="mx-imgBorder"] 
    > ![Развертывание сведений карточки профиля контакта](media/profile1.png "Развертывание сведений карточки профиля контакта")
   
 ## <a name="view-a-users-profile"></a>Просмотр профиля пользователя
 
1.  Перейдите в раздел **Учетные записи**.
2.  Выберите запись учетной записи.
3.  Наведите указатель мыши на поле владельца, если оно содержит запись пользователя. Вы можете в любой момент просмотреть сведения о пользователе.
4.  Чтобы просмотреть дополнительные сведения, такие как сообщения электронной почты и общие файлы, выберите **Показать больше**, чтобы развернуть профиль контакта.
 
    > [!div class="mx-imgBorder"] 
    > ![Развертывание сведений карточки профиля пользователя](media/profile2.png "Развертывание сведений карточки профиля пользователя")


 ## <a name="faqs"></a>Вопросы и ответы
 
### <a name="where-can-i-see-profile-cards-in-dynamics-365"></a>Где можно просмотреть карточку профиля в Dynamics 365?
Карточки профиля можно просматривать в записях контактов и пользователей. Их можно просматривать, только если они содержатся в поиске.

### <a name="where-is-information-shown-in-the-profile-card-coming-from"></a>Откуда берется информация, отображаемая в карточке профиля?
Информация, отображаемая в карточке профиля контакта, извлекается из Common Data Service (а не Microsoft Exchange). Это означает, что контактные данные поступают из Dynamics 365.

Сведения, отображаемые в карточке профиля пользователя, извлекаются из Office 365 (Azure Active Directory). Дополнительные сведения о профилях см. в разделе [Карточки профиля в Office 365 (раздел для администраторов)](https://support.office.com/article/Profile-cards-in-Office-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501).

### <a name="how-can-i-customize-the-fields-shown-on-the-profile-card"></a>Как настроить поля, отображаемые в карточке профиля?
В настоящее время список полей, отображаемых в карточке профиля, нельзя настраивать.

### <a name="why-is-the-start-chat-option-on-the-profile-card-disabled-greyed-out"></a>Почему параметр **Начать чат** в карточке профиля отключен (выделен серым)?
Параметры **Начать чат** и **Отправить электронное сообщение** в карточке профиля открывают ваши приложения для обмена мгновенными сообщениями и электронной почты по умолчанию. Параметр **Начать чат** включен, если пользователь, с которым вы пытаетесь связаться, находится в той же среде Azure Active Directory, что и вы, или является федеративным контактом.


  
