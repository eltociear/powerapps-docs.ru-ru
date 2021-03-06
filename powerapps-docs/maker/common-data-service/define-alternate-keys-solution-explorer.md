---
title: Определение альтернативных ключей с помощью обозревателя решений | MicrosoftDocs
description: Узнайте, как определить альтернативные ключи, которые можно использовать для ссылки на записи в Common Data Service с помощью обозревателя решений
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
ms.openlocfilehash: c13838bdd957d78552d71636b4a165902154e82c
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2019
ms.locfileid: "2865769"
---
# <a name="define-alternate-keys-using-solution-explorer"></a>Определение альтернативных ключей с помощью обозревателя решений

Обозреватель решений предоставляет один способ просмотра и создания альтернативных ключей для Common Data Service.

[Портал Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) позволяет настроить самые распространенные параметры, но некоторые параметры можно задать только с помощью обозревателя решений. <br />Дополнительные сведения: 
- [Определение альтернативных ключей для ссылки на записи](define-alternate-keys-reference-records.md)<br />
- [Определение альтернативных ключей с помощью портала Power Apps](define-alternate-keys-portal.md)

## <a name="open-solution-explorer"></a>Откройте обозреватель решений

Часть имени любого создаваемого альтернативного ключа — это префикс настройки. Это настраивается с использованием издателя решений для решения, в котором выполняется работа. Если важен префикс настройки, убедитесь, что вы работаете с неуправляемым решением, префикс настройки в котором — тот, который нужен для данной сущности. Дополнительные сведения: [Изменение префикса издателя решения](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-alternate-keys"></a>Просмотр альтернативных ключей

1. В открытом обозревателе решений в разделе **Компоненты** разверните **Сущности** и выберите сущность, в которой требуется просмотреть альтернативные ключи.
2. Разверните сущность и выберите **Ключи**.

    ![Просмотр альтернативных ключей](media/view-alternate-keys-solution-explorer.png)

## <a name="create-an-alternate-key"></a>Создание альтернативного ключа

1. При [просмотре альтернативных ключей](#view-alternate-keys) выберите **Создать**.
1. В форме введите **Отображаемое имя**. Поле **Имя** будет заполнено автоматически на основе поля **Отображаемое имя**. 
2. Из списка **Доступные атрибуты** выберите каждый атрибут, затем **Добавить >**, чтобы переместить атрибут в список **Выбранные атрибуты**.
    ![Создание альтернативного ключа](media/create-alternate-key-solution-explorer.png)
1. Выберите **ОК**, чтобы закрыть форму.

### <a name="optional-view-the-system-job-tracking-creation-of-indexes"></a>(Необязательно) Просмотр системного задания, отслеживающего создание индексов
1. При [просмотре альтернативных ключей](#view-alternate-keys) после создания нового альтернативного ключа отображается строка с созданным ключом.
2. В столбце **Системное задание** можно найти ссылку на системное задание, которое контролирует создание индексов для поддержки альтернативных ключей. 
    
    Это системное задание будет иметь имя, соответствующее следующей схеме: `Create index for {0} for entity {1}`, где `0` — это **Отображаемое имя** альтернативного ключа, а `1` — это имя сущности.

    Ссылка на системное задание не отображается после того как системное задание завершится успешно. Дополнительные сведения: [Отслеживание хода выполнения системных заданий и управление им](/dynamics365/customer-engagement/admin/monitor-manage-system-jobs)


## <a name="delete-an-alternate-key"></a>Удаление альтернативного ключа

При [просмотре альтернативных ключей](#view-alternate-keys) выберите ![Удалить](media/delete.gif).

### <a name="see-also"></a>См. также

[Определение альтернативных ключей для ссылки на записи](define-alternate-keys-reference-records.md)<br />
[Определение альтернативных ключей с помощью портала Power Apps](define-alternate-keys-portal.md)<br />
[Документация для разработчиков. Определение альтернативных ключей для сущности](/dynamics365/customer-engagement/developer/define-alternate-keys-entity)
