---
title: Примеры управляемых моделью приложений
description: Сведения о получении, настройке и удалении примеров приложений, управляемых моделью.
documentationcenter: na
author: mr-dang-msft
manager: kvivek
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 03/09/2020
ms.author: brdang
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 995fc58d72031a6108573ba48cebcb30f1aecd79
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2020
ms.locfileid: "3136536"
---
# <a name="model-driven-sample-apps"></a>Примеры управляемых моделью приложений

На [powerapps.com](https://powerapps.com) используйте пример приложения для изучения возможностей дизайна и знакомства с концепциями, которые можно применять при разработке собственных приложений. Каждый пример приложение использует вымышленные данные для преставления реального сценария. 

Обязательно проверьте документацию по каждому конкретному примеру приложения, чтобы получить дополнительные сведения. 

> [!div class="mx-imgBorder"] 
> ![Образец приложения по сбору средств](media/overview-model-driven-samples/fundraiser-app1.png "Образец приложения по сбору средств")


## <a name="get-sample-apps"></a>Получение примеров приложений

Для изучения или редактирования примеров приложений, управляемых моделью, приложения необходимо сначала подготовить в базе данных Common Data Service. Сначала создайте пробную среду и базу данных и обязательно выберите **Развернуть примеры приложений и данные**.

> [!div class="mx-imgBorder"] 
> ![Создать базу данных](media/overview-model-driven-samples/create-database1.png "Создание базы данных")

> [!IMPORTANT]
> Этот параметр устанавливает все доступные образцы приложений в базу данных. Образцы приложений предназначены для образовательных и демонстрационных целей, и не рекомендуется устанавливать их в производственные базы данных. 

## <a name="customize-a-sample-app"></a>Настройка образца приложения

1. Войдите на [powerapps.com](https://powerapps.com)  

2. На странице **Создать** выберите пример приложения и нажмите **Создать**.

> [!div class="mx-imgBorder"]
> <img src="media/overview-model-driven-samples/model-driven-create-page-sample.png" alt="Create a model-driven sample app" height="427" width="674">

3. Откроется конструктор приложений с несколькими параметрами для настройки приложения.

4. Для дополнительных параметров настройки щелкните **Дополнительно** в левой панели навигации портала.

## <a name="remove-sample-apps-and-data"></a>Удаление образцов приложений и данных 
- Для удаления образца приложения требуется удалить соответствующее [управляемое решение](https://docs.microsoft.com/dynamics365/customer-engagement/developer/uninstall-delete-solution). 
- При удалении решения также удаляются все демонстрационные данные, относящиеся к настраиваемым сущностям для приложения.
- Если настройки были сделаны в примере приложения, могут иметься [зависимости](https://docs.microsoft.com/dynamics365/customer-engagement/developer/dependency-tracking-solution-components), которое необходимо удалить перед удалением решения.

### <a name="steps"></a>Шаги
1. Выполните вход на [портал администрирования Power Apps](https://admin.powerapps.com).

2. Выберите среду.

    > [!div class="mx-imgBorder"] 
    > ![Центр администрирования Dynamics 365](media/overview-model-driven-samples/admin-center.png "Выберите среду")

3. Щелкните **Центр администрирования Dynamics 365**.

4. Выберите свою базу данных в списке и щелкните **ОТКРЫТЬ**.

    > [!div class="mx-imgBorder"] 
    > ![Выберите базу данных](media/overview-model-driven-samples/select-database.png "Выберите базу данных")

5. Выберите **Параметры/Решения**.

6. Выберите решение для приложения, которое требуется удалить и нажмите **удалить**.

    > [!div class="mx-imgBorder"] 
    > ![Удаление решения](media/overview-model-driven-samples/delete-solution.png "Удаление решения")

*Можно также перейти к списку решений, щелкнув **Дополнительно** на портале создателя, и удалить все в URL-адресе после .dynamics.com/.*

> [!IMPORTANT]
> Не удаляйте другие системные решения, если вы не уверены в последствиях.

## <a name="install-or-uninstall-sample-data"></a>Установка и удаление демонстрационных данных
1. Выполните шаги 1–4 выше.
2. Перейдите в раздел **Параметры/Управление данными/Демонстрационные данные**.
3. Если установлены демонстрационные данные, то параметр для удаления доступен. В противном случае доступен параметр для установки. 

    > [!div class="mx-imgBorder"] 
    > ![удаление демонстрационных данных](media/overview-model-driven-samples/remove-sample-data.png "Удалить демонстрационные данные")




