---
title: Создание портала в среде, содержащий приложения на основе модели в Dynamics 365 | Microsoft Docs
description: Инструкции по созданию портала в среде, содержащий приложения на основе модели в Dynamics 365.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 98fab91cb8be63ec307977e89fb7147f5561fcc8
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977504"
---
# <a name="create-a-portal-in-an-environment-containing-model-driven-apps-in-dynamics-365"></a>Создание портала в среде, содержащий приложения на основе модели в Dynamics 365

Если вы выбираете среду, которая содержит приложения на основе модели в Dynamics 365 (например, Dynamics 365 Sales и Dynamics 365 Customer Service), можно создать порталы, упомянутые в разделе [Шаблоны порталов](portal-templates.md).

1.  Выполните вход в [Power Apps](https://make.powerapps.com).

2.  Выберите **Создать** в левой панели и введите **портал** в поле **Поиск шаблонов** для отображения всех шаблонов порталов Dynamics 365.

    > [!div class=mx-imgBorder]
    > ![Шаблоны порталов Dynamics 365](media/dynamics-portals.png "Шаблоны порталов Dynamics 365")  

3.  Выберите соответствующий портальный шаблон.

4.  В окне создания портала введите название портала и адрес веб-сайта, и выберите язык с помощью раскрывающегося списка. По завершении нажмите **Создать**. Процесс создания такой же, как описано в разделе [Создать начальный портал Common Data Service](create-portal.md).

> [!NOTE]
> - Если вы приобрели более старую надстройку портала и хотите подготовить портал, используя это расширение, необходимо перейти на страницу **Центр администрирования Dynamics 365**. Дополнительные сведения: [Подготовка портала с помощью более старой надстройки портала](provision-portal-add-on.md)
> - Если вы подготовили портал с помощью старой надстройки портала, все равно можно будет настроить и управлять им с сайта [make.powerapps.com](https://make.powerapps.com).
> - Подготовка порталов с сайта [make.powerapps.com](https://make.powerapps.com) не использует более старые надстройки портала. Кроме того, эти порталы не указаны на вкладке **Приложения** на странице **Центр администрирования Dynamics 365**.
> - Начальный портал Common Data Service не может быть создан из страницы **Центр администрирования Dynamics 365**.
> - Чтобы выключить создание портала в клиенте, см. раздел [Отключение создания портала в клиенте](create-portal.md#disable-portal-creation-in-a-tenant).
> - При создании портала устанавливается несколько решений и импортируются образцы данных.

