---
title: Общие сведения о подключении Power BI | Документация Майкрософт
description: Просмотрите доступные подключения Power BI
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/12/2016
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5efcc877de7a16524c57121a91488189d4058437
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "71987159"
---
# <a name="connect-to-power-bi-from-powerapps"></a>Подключение к Power BI из PowerApps
![Power BI](./media/connection-powerbi/powerbiicon.png)

Power BI — это набор средств бизнес-аналитики для анализа данных и обмена сведениями. Отслеживайте свою бизнес-деятельность и быстро получайте ответы на вопросы, используя многофункциональные информационные панели на каждом устройстве. В приложении можно проверить состояние оповещений о данных, настроенных в службе Power BI. Дополнительные сведения об оповещениях о данных в Power BI см. на [странице документации](https://docs.microsoft.com/power-bi/service-set-data-alerts).

В этой статье показано, как использовать подключение Power BI в приложении, а также перечислены доступные функции.

## <a name="prerequisites"></a>Технические условия
* [Зарегистрируйтесь](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
* Добавьте [подключение](https://powerapps.microsoft.com/tutorials/add-manage-connections/) Power BI.
* Создайте приложение с помощью [шаблона](https://powerapps.microsoft.com/tutorials/get-started-test-drive/) или [данных](https://powerapps.microsoft.com/tutorials/get-started-create-from-data/) или создайте его с [нуля](https://powerapps.microsoft.com/tutorials/get-started-create-from-blank/).

## <a name="use-the-power-bi-connection-in-your-app"></a>Использование подключения Power BI в приложении
### <a name="list-the-alerts-that-youve-set-up-in-the-power-bi-service"></a>Перечисление оповещений, настроенных в службе Power BI
1. В меню **Вставка** выберите **Коллекция** и добавьте любую из коллекций текстов в поле **Коллекции текстов**.
2. Чтобы отобразить оповещения текущего пользователя, задайте для свойства [Items](../controls/properties-core.md) коллекции следующую формулу:

   `PowerBI.GetAlerts()`

В коллекции обновится список оповещений. Для каждого оповещения вы получите имя и код оповещения, а также идентификатор рабочей области группы, в которой настроено оповещение. Для получения дополнительных сведений об оповещении потребуется его идентификатор.

### <a name="view-the-status-of-an-alert"></a>Просмотр состояния оповещения
Чтобы просмотреть состояние оповещения, вызовите функцию CheckAlertStatus с помощью идентификатора оповещения, полученного на предыдущем шаге.

Идентификатор оповещения можно передать в виде строкового литерала (например, "1234") или ссылки на раздел коллекции, заполненной с помощью вызова GetAlerts() (например, Gallery1.Selected.alertId).

Чтобы продолжить, добавьте метку и задайте для ее свойства [Text](../controls/properties-core.md) одну из этих формул:

* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).alertTitle`
* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).currentTileValue`
* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).alertThreshold`
* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).isAlertTriggered`

В метке обновится текущее состояние оповещения.

## <a name="view-the-available-functions"></a>Просмотр доступных функций
Это подключение включает следующие функции:

| Имя функции | Описание |
| --- | --- |
| GetAlerts |Перечисление оповещений, настроенных в службе Power BI |
| CheckAlertStatus |Проверка состояния определенного оповещения |

## <a name="getalerts"></a>GetAlerts
Перечисление оповещений, настроенных в службе Power BI.

#### <a name="input-properties"></a>Входные свойства
Нет.

#### <a name="output-properties"></a>Выходные свойства

| Имя свойства | Тип данных | Требуется | Описание |
| --- | --- | --- | --- |
| value |массив |Нет |Массив оповещений о данных, настроенных в службе Power BI. Каждый элемент в массиве содержит следующее: <ul><li>alertTitle — заголовок оповещения;</li><li>alertId — идентификатор оповещения;</li><li>groupId — идентификатор группы, в которой создано оповещение.</li></ul> |

## <a name="checkalertstatus"></a>CheckAlertStatus
Проверка состояния оповещения.

> [!NOTE]
> Запросы к этой конечной точке будут регулироваться в зависимости от каждого оповещения, если вызывать их слишком часто.

#### <a name="input-properties"></a>Входные свойства

| Имя свойства | Тип данных | Требуется | Описание |
| --- | --- | --- | --- |
| alertId |целое число |Да |Идентификатор оповещения, возвращенный GetAlerts |

#### <a name="output-properties"></a>Выходные свойства

| Имя свойства | Тип данных | Требуется | Описание |
| --- | --- | --- | --- |
| tileValue |число |Нет |Значение плитки при активации оповещения |
| tileUrl |строка |Нет |URL-адрес плитки с оповещением |
| alertTitle |строка |Нет |Имя оповещения |
| isAlertTriggered |логическое значение |Нет |Определяет, активировано ли оповещение |
| alertThreshold |число |Нет |Пороговое значение, при достижении которого оповещение активируется |

## <a name="helpful-links"></a>Полезные ссылки
Сведения о всех доступных подключениях см. [здесь](../connections-list.md).  
Узнайте, как [добавлять подключения](../add-manage-connections.md) в приложения.

