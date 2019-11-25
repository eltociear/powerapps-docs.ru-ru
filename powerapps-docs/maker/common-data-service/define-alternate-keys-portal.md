---
title: Определение альтернативных ключей с помощью портала PowerApps | MicrosoftDocs
description: Узнайте, как определять альтернативные ключи с помощью портала PowerApps
ms.custom: ''
ms.date: 05/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: fec01122ad00710507fb3e0976ec9f80115f06cf
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "2758907"
---
# <a name="define-alternate-keys-using-powerapps-portal"></a>Определение альтернативных ключей с помощью портала PowerApps

[Портал PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) обеспечивает простой способ просмотра и создания альтернативных ключей сущностей в Common Data Service.

Портал позволяет настроить самые распространенные параметры, но некоторые параметры можно задать только с помощью обозревателя решений. <br />Дополнительные сведения: 
- [Определение альтернативных ключей для ссылки на записи](define-alternate-keys-reference-records.md)
- [Определение альтернативных ключей с помощью обозревателя решений](define-alternate-keys-solution-explorer.md)

## <a name="view-alternate-keys"></a>Просмотр альтернативных ключей

1. На [портале PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) выберите режим конструирования **на основе модели** или **Холст**.
2. Выберите **Данные** > **Сущности** и выберите сущность, которую необходимо просмотреть.
3. Выберите **Ключи** для просмотра списка всех альтернативных ключей, которые определены.

    ![Просмотр альтернативных ключей](media/view-alternate-keys-portal.png)

## <a name="create-an-alternate-key"></a>Создание альтернативного ключа

1. При [просмотре альтернативных ключей](#view-alternate-keys) выберите **Добавить ключ**.
2. Используйте панель для задания поля **Отображаемое имя** и выберите поля для использования для создания альтернативного ключа.

    Поле **Имя** будет заполнено автоматически на основе отображаемого имени.

    ![Пример определения альтернативного ключа](media/alternate-key-account-number-sic-code.png)

1. Выберите **Готово**, чтобы закрыть панель.
2. Щелкните **Сохранить сущность** для создания альтернативного ключа.

> [!NOTE]
> Альтернативный ключ не будет сразу же доступным. Системное задание запускается при сохранении сущности для создания индексов базы данных для поддержки альтернативного ключа.

## <a name="delete-an-alternate-key"></a>Удаление альтернативного ключа

Во время [просмотра альтернативных ключей](#view-alternate-keys) выберите ключ, который нужно удалить, и выберите **Удалить ключ** на панели команд.

### <a name="see-also"></a>См. также

[Определение альтернативных ключей для ссылки на записи](define-alternate-keys-reference-records.md)<br />
[Определение альтернативных ключей с помощью обозревателя решений](define-alternate-keys-solution-explorer.md)<br />
[Документация для разработчиков. Определение альтернативных ключей для сущности](/dynamics365/customer-engagement/developer/define-alternate-keys-entity).
