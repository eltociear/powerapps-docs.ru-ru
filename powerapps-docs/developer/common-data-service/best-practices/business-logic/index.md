---
title: 'Для разработчиков: рекомендации по разработке подключаемых модулей и рабочих процессов для Common Data Service | Документация Майкрософт'
description: Рекомендации по разработке подключаемых модулей и рабочих процессов для службы Common Data Service в PowerApps.
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 1/15/2019
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 60e489ffd35f0e07f9a22f65336b242b7e0e2652
ms.sourcegitcommit: 5b2b70c3fc7bcba5647d505a79276bbaad31c610
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58357835"
---
# <a name="best-practices-and-guidance-regarding-plug-in-and-workflow-development-for-the-common-data-service"></a>Рекомендации по разработке подключаемых модулей и рабочих процессов для службы Common Data Service

В списке ниже приводятся все рекомендации по разработке подключаемых модулей и рабочих процессов в службе Common Data Service.

|Рекомендация  |Описание  |
|---------|---------|
|[Избегайте использовать типы пакетных запросов в подключаемых модулях и действиях рабочих процессов](avoid-batch-requests-plugin.md)     |Классы запросов сообщений ExecuteMultipleRequest и ExecuteTransactionRequest не следует использовать в контексте подключаемого модуля или действия рабочего процесса.         |
|[Разработка реализаций IPlugin без отслеживания состояния](develop-iplugin-implementations-stateless.md)     |Члены классов, реализующих интерфейс IPlugin, могут быть подвержены проблемам с потокобезопасностью, которые могут приводить к несогласованности данных или снижению производительности.         |
|[Не повторяйте регистрацию шага подключаемого модуля](do-not-duplicate-plugin-step-registration.md)     |Повторная регистрация шага подключаемого модуля приведет к многократному срабатыванию подключаемого модуля для одного сообщения или события.         |
|[Включите атрибуты фильтрации с регистрацией подключаемого модуля](include-filtering-attributes-plugin-registration.md)     |Если для шага регистрации подключаемого модуля не заданы атрибуты фильтрации, подключаемый модуль будет выполняться каждый раз при получении сообщения об обновлении данного события.         |
|[Ограничьте регистрацию подключаемых модулей для сообщений Retrieve и RetrieveMultiple](limit-registration-plugins-retrieve-retrievemultiple.md)     |Добавление синхронной логики в события сообщений Retrieve и RetrieveMultiple может замедлить работу подключаемого модуля.         |
|[Оптимизируйте разработку пользовательских сборок](optimize-assembly-development.md)     |Отдельные подключаемые модули и пользовательские действия рабочих процессов рекомендуется объединить в одну пользовательскую сборку, чтобы повысить производительность и удобство поддержки. Если размер сборки близок к предельному для изолированной сборки, подключаемые модули и пользовательские действия рабочих процессов следует разделить на несколько пользовательских сборок.         |
|[Присвойте параметру KeepAlive значение false при взаимодействии с внешними узлами в подключаемом модуле](set-keepalive-false-interacting-external-hosts-plugin.md)     |Если свойство KeepAlive в заголовке HTTP-запроса установлено в значение true или не определено явно как false, время выполнения подключаемых модулей может возрастать.         |
|[Используйте InvalidPluginExecutionException в подключаемых модулях и действиях рабочих процессов](use-invalidpluginexecutionexception-plugin-workflow-activities.md)     |Используйте InvalidPluginExecutionException при вызове ошибок в контексте подключаемого модуля или действия рабочего процесса.         |

# <a name="see-also"></a>См. также
[Применение бизнес-логики с помощью кода](../../apply-business-logic-with-code.md)<br />
[Расширение бизнес-процессов с помощью подключаемых модулей](../../plug-ins.md)<br />
[Расширения рабочего процесса](../../workflow/workflow-extensions.md)<br />