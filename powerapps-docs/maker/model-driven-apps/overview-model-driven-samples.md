---
title: Примеры приложений на основе модели
description: Узнайте, как получить, настроить и удалить примеры приложений на основе модели.
documentationcenter: na
author: mr-dang-msft
manager: kvivek
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 03/08/2018
ms.author: brdang
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 65a650b979c4196eff8c103717a63aea5309ec57
ms.sourcegitcommit: 551af7e0273862b28d9b2387671a4eeaf719eb37
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2020
ms.locfileid: "79084645"
---
# <a name="model-driven-sample-apps"></a>Примеры приложений на основе модели

Зайдите на сайт [powerapps.com](https://powerapps.com) и выберите пример приложения, чтобы ознакомиться с возможностями разработки и узнать общие принципы, которые можно применить при создании собственных приложений. Во всех примерах приложений используются вымышленные данные для демонстрации реальной ситуации. 

Обратитесь к документации по каждому примеру приложения, чтобы получить дополнительные сведения. 

![Пример приложения Fundraiser](media/overview-model-driven-samples/fundraiser-app1.png)


## <a name="get-sample-apps"></a>Получение примеров приложений

Для запуска или изменения примеров приложений на основе модели их необходимо сначала подготовить в базе данных Common Data Service. Сначала создайте пробную среду и базу данных и убедитесь, что выбраны **образцы приложений и данных деполи**.

> [!div class="mx-imgBorder"] 
> ![создать](media/overview-model-driven-samples/create-database1.png) базы данных

> [!IMPORTANT]
> При выборе этого варианта в базе данных устанавливаются все доступные примеры приложений. Примеры приложений предназначены для обучения и демонстрации. Мы не рекомендуем устанавливать их в рабочих базах данных. 

## <a name="customize-a-sample-app"></a>Настройка примера приложения

1. Вход в [powerapps.com](https://powerapps.com)  

2. На странице **Создание** выберите пример приложения и нажмите кнопку **создать**.

> [!div class="mx-imgBorder"] 
> Пример приложения ![Model](media/overview-model-driven-samples/model-driven-create-page-sample.png)

3. Откроется конструктор приложений, в котором доступно множество примеров для настройки приложения.

4. Для дополнительных параметров настройки нажмите кнопку **Дополнительно** на панели навигации слева на портале.

## <a name="remove-sample-apps-and-data"></a>Удаление примеров приложений и данных 
- Для удаления примера приложения требуется удалить соответствующее [управляемое решение](https://docs.microsoft.com/dynamics365/customer-engagement/developer/uninstall-delete-solution). 
- При удалении решения также удаляются все образцы данных, относящиеся к настраиваемым сущностям для приложения.
- Если в пример приложения были внесены изменения, могут существовать [зависимости](https://docs.microsoft.com/dynamics365/customer-engagement/developer/dependency-tracking-solution-components), которые необходимо удалить перед удалением решения.

### <a name="steps"></a>Шаги
1. Войдите на [портал администрирования Power Apps](https://admin.powerapps.com).

2. Выберите среду.

3. Щелкните **Центр администрирования Dynamics 365**. 

    ![Центр администрирования Dynamics 365](media/overview-model-driven-samples/admin-center.png)

4. Выберите в списке свою базу данных и нажмите кнопку **Открыть**.

    ![Выбор базы данных](media/overview-model-driven-samples/select-database.png)

5. Выберите **Параметры > Решения**.

6. Выберите решение, связанное с удаляемым приложением, и нажмите кнопку **Удалить**.

    ![Удаление решения](media/overview-model-driven-samples/delete-solution.png)

*Вы также можете перейти к списку решений, нажав **Дополнительно** на портале разработчика, и удалить всю последнюю часть URL-адреса после .dynamics.com/*

> [!IMPORTANT]
> Не удаляйте другие системные решения, если не знаете, какие могут быть последствия.

## <a name="install-or-uninstall-sample-data"></a>Установка и удаление образца данных
1. Выполните приведенные выше шаги 1–4.
2. Последовательно выберите **Параметры > Управление данными > Образец данных**.
3. Если образец данных установлен, команда удаления недоступна. В противном случае команда удаления доступна. 

    ![Удаление образца данных](media/overview-model-driven-samples/remove-sample-data.png)




