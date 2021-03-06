---
title: Использование примера приложения | Документация Майкрософт
description: Пошаговые инструкции по созданию приложения на основе холста с помощью образца в Power Apps
author: wimcoor
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/22/2020
ms.author: wimcoor
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 555651715109585bec0214e95ec105a067d061ce
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2020
ms.locfileid: "76536773"
---
# <a name="create-a-canvas-app-from-a-sample-in-power-apps"></a>Создание приложения на основе холста с помощью образца в PowerApps
В этом кратком руководстве вы создадите приложение на основе холста из образца, чтобы изучить возможности проектирования и принципы, которые можно применять при разработке собственных приложений на основе холста.

Во всех примерах используются вымышленные данные для демонстрации реальной ситуации. 

Если у вас нет лицензии на Power Apps, вы можете [зарегистрироваться для получения бесплатной версии](../signup-for-powerapps.md).

## <a name="open-a-sample-app"></a>Открытие примера приложения
1. Выполните вход в [Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

1. Выберите **Все шаблоны**.

1. Выберите пример приложения из списка примеров приложений, например **Оценщик затрат**.

    ![](./media/open-and-run-a-sample-app/cost-estimator-app.png)

1. Измените имя приложения и выберите **Создать**, чтобы создать приложение.

    > [!NOTE]
    > Некоторые примеры приложений могут быть доступны только в макетах для телефона или планшета. Дополнительные сведения о макетах см. в статье [Создание макетов с быстрым реагированием в приложениях на основе холста](create-responsive-layout.md). Если выбранный пример приложения имеет параметры макета "Телефон" и "Планшет", выберите нужный макет.

1. Откройте режим предварительного просмотра, нажав клавишу F5 или кнопку воспроизведения в правом верхнем углу.

    ![](./media/open-and-run-a-sample-app/open-preview-app.png)

    Каждый пример представляет особую ситуацию и поэтому содержит разные экраны и другие элементы управления. Если вы открыли пример Cost Estimator, то можете использовать приложение по умолчанию для выполнения указанных ниже задач.

    - Вы можете создать встречу для оценки стоимости укладки пола в помещении с заданными размерами.
    - Приложение позволяет собрать такие сведения, как адрес и площадь объекта, и рассчитать стоимость с учетом скидки и ставки налога.
    - Также можно отфильтровать список встреч. Таким образом, на экране можно отобразить либо полный список встреч, либо только те встречи, для которых оценка уже выполнена, либо только те встречи, для которых оценка еще не выполнена.
    
1. Завершив изучение приложения, закройте режим предварительного просмотра, нажав клавишу ESC (либо значок закрытия в правом верхнем углу под строкой заголовка Power Apps).

## <a name="save-the-app"></a>Сохранение приложения
1. В левом верхнем углу экрана выберите вкладку **Файл**.

1. На странице **Параметры** просмотрите параметры по умолчанию.

    ![](./media/open-and-run-a-sample-app/settings-app.png)

1. У левого края экрана выберите **Сохранить**. 

## <a name="next-steps"></a>Дальнейшие действия
В этом кратком руководстве вы создали пример, использующий фиктивные данные. Вы также можете автоматически создать приложение на основе данных из других источников, таких как Common Data Service, SharePoint или Excel.

> [!div class="nextstepaction"]
> [Создание приложения](data-platform-create-app.md)
