---
title: Разработка лицензий для приложения | Документация Майкрософт
description: Описание проверки лицензии для выбранного приложения
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/24/2020
ms.author: alaug
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 495325949776b066ed30d629fb031730e4463179
ms.sourcegitcommit: be9b8c0f5c7c7e9992e93fa0d03e961b4ac7e3ae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2020
ms.locfileid: "80374996"
---
# <a name="how-to-check-license-designation-for-an-app"></a>Проверка лицензии для приложения

Начиная с 2019 октября, несколько соединителей переклассифицируются с уровня "Стандартный" на "Премиум".

[Вопросы и ответы по лицензированию Power Apps](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#office-365) описаны реклассифицированные соединители. Для приложений, использующих эти соединители до реклассификации, было предоставлено расширенное значение периода, позволяющее пользователям без лицензии Premium получать доступ к этим приложениям.

В следующей таблице описаны конструкции и лицензия, которую должен иметь конечный пользователь для доступа к приложению.

| **Обозначение** | **Определение**
|-|-|
| Стандартный | Приложение, использующее только стандартные соединители. Для доступа к этому приложению у конечного пользователя должно быть приложение Power Apps для Office 365, план для каждого приложения или план на пользователя.
| Расширенный | Приложение может использовать соединители, повышенные до уровня "Премиум", на 1 октября 2019 г. У конечного пользователя должно быть приложение Power Apps для Office 365, план приложений или план каждого пользователя.  [Вопросы и ответы по лицензированию Power Apps](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#office-365) описаны, какие соединители были изменены до уровня "Премиум" на 1 октября 2019 г.
| Расширенный | Приложение, использующее по крайней мере один соединитель Premium, настраиваемый соединитель или локальный шлюз. Для доступа конечный пользователь должен иметь план приложений или план каждого пользователя.

## <a name="check-app-license-designation-from-app-settings"></a>Проверка разработки лицензии приложения на основе параметров приложения

1. Выполните вход в [Power Apps](https://make.powerapps.com).

1. Выберите **приложения** с левой стороны.

1. Выберите приложение в списке приложений. Вы можете использовать параметр **Параметры** в верхней части или использовать **команды more** ( **...** ), а затем — **Параметры** из раскрывающегося меню:

    ![Параметр "Параметры"](media/license-designation/app-settings.png)

1. Выберите **Параметры** , чтобы просмотреть сведения о разработке лицензий.

    ![Разработка лицензий на основе параметров](media/license-designation/settings-license-designation.png)

## <a name="check-app-license-designation-from-app-details"></a>Проверить сведения о разработке лицензии приложения на основе сведений о приложении

1. Выполните вход в [Power Apps](https://make.powerapps.com).

1. Выберите **приложения** с левой стороны.

1. Выберите приложение в списке приложений. Можно использовать параметр **Details** Top или использовать **Дополнительные команды** ( **...** ), а затем в раскрывающемся меню выбрать следующие **сведения** .

    ![Сведения о приложении](media/license-designation/app-details.png)

1. Выберите **сведения**:

    ![Сведения о проектировании приложений](media/license-designation/app-details-page.png)

## <a name="pass-assignment"></a>Передача назначения

Сведения о назначении Pass см. [в статье Power Apps for App Plans](https://docs.microsoft.com/power-platform/admin/about-powerapps-perapp#step-three-set-up-apps-to-use-per-app-plans).

## <a name="next-steps"></a>Следующие шаги

- [Вопросы и ответы по лицензированию Power Apps](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq)

### <a name="see-also"></a>См. также:

- [Изменение приложения](edit-app.md)
- [Удаление приложения](delete-app.md)
