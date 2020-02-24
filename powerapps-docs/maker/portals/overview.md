---
title: Что такое порталы Power Apps? | Microsoft Docs
description: Проектируйте и создавайте веб-сайты с помощью Power Apps, которые позволяют внешним пользователям взаимодействовать с данными, хранящимися в Common Data Service.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 01/17/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 4f8617c824037d8975514e809347cfaa6c0328c4
ms.sourcegitcommit: 2fd8b682e2d4c1e6a45c851b56f37f842ef18224
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2020
ms.locfileid: "2982516"
---
# <a name="what-is-power-apps-portals"></a>Что такое порталы Power Apps?

Разработчики Power Apps теперь могут создавать новый мощный тип взаимодействия: внешние веб-сайты, которые позволяют пользователям за пределами своих организаций входить в систему с различными именами, создавать и просматривать данные в Common Data Service, или даже просматривать содержимое анонимно. Полные возможности порталов Dynamics 365, ранее предлагавшиеся только как надстройка — в приложениях на основе моделей в Dynamics 365 теперь доступны полностью в автономном режиме в Power Apps.  

Эти возможности обеспечивают переработчикам комплексное решение, позволяющее быстро создавать веб-сайт и настраивать его в соответствии со страницами, макетом и содержимым. Разработчики могут использовать повторно разработки страницы с помощью шаблонов, добавить формы и представления для отображения ключевых данных из Common Data Service и опубликовать для пользователей.

> [!NOTE]
> - Порталы Power Apps основаны на Bootstrap 3.3.x за исключением [Портал событий](https://docs.microsoft.com/dynamics365/marketing/developer/event-management-web-application). Разработчики портала не должны заменять Bootstrap 3 другими библиотеками CSS, так как некоторые из сценариев на порталах Power Apps зависят от Bootstrap 3.3.x.
> - Некоторые взаимодействия могут иметь известные проблемы. Эти проблемы упоминаются в разделе [Известные проблемы](known-issues.md) далее в этом документе.  

## <a name="next-steps"></a>Дальнейшие шаги

[Создание начального портала](create-portal.md)

### <a name="see-also"></a>См. также

#### <a name="advanced-portal-administration"></a>Расширенное администрирование портала

- [Центр администрирования портала](admin/admin-overview.md)

#### <a name="advanced-portal-customization"></a>Расширенная настройка портала

- [Приложение управления порталом](configure/configure-portal.md)
- [Параметры сайта портала](configure/configure-site-settings.md)
