---
title: Получение инструментария для платформы компонентов PowerApps | Документация Майкрософт
description: Получите Microsoft PowerApps CLI для создания, отладки и развертывания компонентов кода с помощью платформы компонентов PowerApps.
keywords: Платформа компонентов PowerApps, компоненты кода, платформа компонентов
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f393f227-7a88-4f25-9036-780b3bf14070
ms.openlocfilehash: 496b7d443775da075dd8da52ac4b0a754121bf28
ms.sourcegitcommit: 4c35aedde46380d5438687ae6f61a3b0cc7e7e2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2019
ms.locfileid: "72340030"
---
# <a name="get-tooling-for-powerapps-component-framework"></a>Получение инструментария для платформы компонентов PowerApps

Используйте **Microsoft POWERAPPS CLI** (интерфейс командной строки) для создания, отладки и развертывания компонентов кода с помощью платформы компонентов PowerApps. Интерфейс командной строки PowerApps позволяет разработчикам быстро создавать компоненты кода. В будущем оно будет дополнено поддержкой дополнительных возможностей разработки и управления жизненным циклом приложений (ALM). 

## <a name="what-is-microsoft-powerapps-cli"></a>Что такое Microsoft PowerApps CLI 

Microsoft PowerApps CLI — это простой интерфейс командной строки разработчика с одним остановкой, который позволяет разработчикам и руководителям приложений создавать компоненты кода. Средства CLI PowerApps — это первый шаг к комплексной истории ALM, где разработчики и независимые поставщики программного обеспечения могут создавать, собирать, отлаживать и публиковать свои расширения и настройки быстро и эффективно.  

## <a name="install-microsoft-powerapps-cli"></a>Установка Microsoft PowerApps CLI

Чтобы получить Microsoft PowerApps CLI, выполните следующие действия.

1. Установите [NPM](https://www.npmjs.com/get-npm) (поставляется с Node. js) или [node. js](https://nodejs.org/en/) (поставляется с NPM). Мы рекомендуем LTS (долгосрочная поддержка) версии 10.15.3 LTS, так как она кажется наиболее стабильной.

1. Установите [пакет разработчика .NET Framework 4.6.2 для разработчиков](https://dotnet.microsoft.com/download/dotnet-framework/net462). 

1. Если у вас еще нет Visual Studio 2017 или более поздней версии, воспользуйтесь одним из следующих вариантов.
   - Вариант 1. Установите [Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2017) или более поздней версии.
   - Вариант 2. Установите [пакет SDK для .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) , а затем установите [Visual Studio Code](https://code.visualstudio.com/Download).

1. Установите [Microsoft POWERAPPS CLI](https://aka.ms/PowerAppsCLI).
1. Чтобы воспользоваться всеми новейшими возможностями, обновите средство командной строки PowerApps до последней версии с помощью следующей команды:

    ```CLI
    pac install latest
    ```

> [!NOTE]
> - Чтобы развернуть компонент кода с помощью PowerApps CLI, необходимо иметь среду Common Data Service с правами системного администратора или средства настройки системы.
> - В настоящее время интерфейс командной строки PowerApps поддерживается только в Windows 10.

## <a name="microsoft-powerapps-cli-telemetry"></a>Microsoft PowerApps телеметрии CLI

Специализированная группа выполняет статистическую обработку телеметрии, чтобы понять, какие функции или возможности разработчики чаще всего используют в средстве CLI PowerApps. Агрегированные данные позволяют нам обеспечить лучшее взаимодействие с клиентами, изменяя то, что важно.

> [!NOTE]
> Чтобы отключить сбор данных телеметрии, выполните команду `pac telemetry disable`. Чтобы вернуть данные телеметрии, используйте команду `pac telemetry enable`.


## <a name="uninstall-microsoft-powerapps-cli"></a>Удаление Microsoft PowerApps CLI

Чтобы удалить средства командной строки PowerApps, запустите MSI [отсюда.](https://aka.ms/PowerAppsCLI) 

Если вы являетесь частным участником предварительной версии и имеете более старую версию CLI, выполните следующие действия.

1. Чтобы узнать, где установлена утилита PowerApps CLI, откройте командную строку и введите `where pac`.
1. Удалите папку Повераппскли.
1. Откройте средство "переменные среды", выполнив команду `rundll32 sysdm.cpl,EditEnvironmentVariables` в командной строке.
1. Дважды щелкните `Path` в разделе `User variable for...`.
1. Выберите строку, содержащую путь Повераппскли, и нажмите кнопку **Удалить** в правой части.
1. Дважды нажмите кнопку **ОК** .

### <a name="see-also"></a>См. также

[Реализация компонентов с помощью TypeScript](implementing-controls-using-typescript.md)<br/>
