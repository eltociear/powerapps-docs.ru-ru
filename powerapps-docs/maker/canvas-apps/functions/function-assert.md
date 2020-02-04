---
title: Функция Assert | Документация Майкрософт
description: Справочные сведения, включая синтаксис, для функции Assert в Power Apps Test Studio
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
ms.openlocfilehash: e4319c3685db46f4277109e385a640e744402edc
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541297"
ms.PowerAppsDecimalTransform: true
---
# <a name="assert-function-in-power-apps-test-studio"></a>Функция Assert в Power Apps Test Studio

Утверждение — это условие или выражение, возвращающее значение True или False в ходе теста. Если выражение возвращает значение False, тестовый случай завершится ошибкой. Утверждения используются для проверки ожидаемого результата теста или шага теста относительного фактического. В случае расхождения возникает ошибка. Утверждения можно использовать для проверки состояния элементов управления в приложении, например значений меток, выбора в списке и других свойств элемента управления.  

Сообщения утверждений для успешных и неудачных утверждений также содержатся в таблице Traces в записи TestCaseResult. 

## <a name="syntax"></a>Синтаксис

*Assert(выражение, сообщение)*

- *Выражение* — обязательный аргумент. Выражение, возвращающее значение True или False.
- *Сообщение* — необязательный аргумент. Сообщение, которое описывает ошибку. 


## <a name="examples"></a>Примеры

```Assert(lblResult.Text = "Success"; "lblResult value Expected : Success , Actual : " & lblResult.Text)```<br>
```Assert(ListBox1.Selected.Value = "Success"; "ListBox1 selection Expected : Success,  Actual : " & ListBox1.Selected.Value)```<br>
```Assert(kudosAfterTest = kudosBeforeTest + 1; "Kudos count. Expected : " & kudosBeforeTest + 1  & " Actual :" & kudosAfterTest)```

### <a name="see-also"></a>См. также

[Обзор Test Studio](../test-studio.md) <br>
[Использование Test Studio](../working-with-test-studio.md)
