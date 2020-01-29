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
ms.openlocfilehash: 86d28400e0eaea89b59286df173d0e67655bb7a5
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541251"
---
# <a name="trace-function"></a>Функция Trace 

При использовании с Test Studio функция Trace является необязательным выражением, которое можно использовать для предоставления дополнительных сведений в результатах теста из события **OnTestCaseComplete**. Сообщения событий трассировки, как и сообщения успешных и неудачных утверждений, содержатся в таблице Traces в записи TestCaseResult. Таблица Traces имеет два свойства: Message и Timestamp. 

Если вы разрешили приложению отправку данных телеметрии в Azure Application Insights, функцию Trace можно также использовать для отправки пользовательских событий или диагностических сведений в ресурс Application Insights. Эти данные можно просмотреть в Application Insights; они могут помочь в диагностике проблем или изучении использования приложений и функций. Сведения трассировки, используемые в тестах, будут также записаны в Application Insights. Все сообщения Trace также можно просмотреть в средстве мониторинга Power Apps, которое поможет при отладке или выявлении проблем в ходе диагностических сеансов в реальном времени для вашего приложения.   

## <a name="syntax"></a>Синтаксис

*Трассировка (сообщение, серьезность, пользовательская запись)*

- *Message* — обязательный аргумент. Сведения для отслеживания. В тестах это создает запись в таблице Traces в записи TestCaseResult. 
- *Серьезность* — необязательный аргумент. Степень серьезности трассировки, записанной в Application Insights. Варианты — сведения, предупреждение или ошибка. 
- *Пользовательская запись* — необязательный аргумент. Запись, содержащая настраиваемые данные, которые будут записаны в Application Insights. 
  

### <a name="see-also"></a>См. также

[Обзор Test Studio](../test-studio.md) <br>
[Использование Test Studio](../working-with-test-studio.md)
