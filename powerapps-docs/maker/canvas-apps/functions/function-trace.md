---
title: Функция Trace | Документация Майкрософт
description: Справочные сведения, включая синтаксис, для функции Trace в Power Apps Test Studio
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/19/2018
ms.author: aheneay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 927b8dae59a4dc6fc55d74c1998b0d434eb8356c
ms.sourcegitcommit: d500f44e77747a3244b6691ad9b3528e131dbfa5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2020
ms.locfileid: "79133583"
---
# <a name="trace-function"></a>Функция Trace 

При использовании с Test Studio функция Trace является необязательным выражением, которое можно использовать для предоставления дополнительных сведений в результатах теста из события **OnTestCaseComplete**. Сообщения событий трассировки, как и сообщения успешных и неудачных утверждений, содержатся в таблице Traces в записи TestCaseResult. Таблица Traces имеет два свойства: Message и Timestamp. 

Сообщения трассировки также могут быть определены в приложении. Их можно просмотреть в средстве мониторинга Power Apps вместе с другими действиями приложения, чтобы упростить отладку или выявить проблемы с диагностической информацией в реальном времени для вашего приложения. Если вы разрешили приложению отправку данных телеметрии в Azure Application Insights, функцию Trace можно также использовать для отправки пользовательских событий или диагностических сведений в ресурс Application Insights. Эти данные можно просмотреть в Application Insights; они могут помочь в диагностике проблем или изучении использования приложений и функций. Сведения трассировки, используемые в тестах, будут также записаны в Application Insights. Сведения о трассировке тестов не будут доступны в средстве мониторинга, так как монитор подключен к приложению при его воспроизведении из App Studio. 

## <a name="syntax"></a>Синтаксис

*Трассировка (сообщение, trace_severity, custom_record)*

- *Message* — обязательный аргумент. Сведения для отслеживания. В тестах это создает запись в таблице Traces в записи TestCaseResult. 
- *Trace_severity* — необязательный. Степень серьезности трассировки, записанной в Application Insights. Возможные значения: Трацесеверити. Information, Трацесеверити. warning или Трацесеверити. Error. 
- *Пользовательская запись* — необязательный аргумент. Запись, содержащая настраиваемые данные, которые будут записаны в Application Insights. 
  

### <a name="see-also"></a>См. также

[Обзор Test Studio](../test-studio.md) <br>
[Использование Test Studio](../working-with-test-studio.md)
