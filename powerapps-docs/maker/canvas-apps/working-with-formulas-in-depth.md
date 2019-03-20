---
title: Основные сведения о формулах поведения в приложении на основе холста | Документы Майкрософт
description: Справочные сведения о работе с формулами поведения, которые изменяют состояние приложения на основе холста в PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/10/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d48559ee3a54cbb723621a0e36f09cb4a1d0fe3b
ms.sourcegitcommit: 825daacc9a812637815afc1ce6fad28f0cebd479
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2019
ms.locfileid: "57803442"
---
# <a name="understand-behavior-formulas-for-canvas-apps-in-powerapps"></a>Основные сведения о формулах поведения в приложениях на основе холста в PowerApps

Большинство формул предназначены для вычисления значений.  Как и в электронной таблице Excel, повторное вычисление выполняется автоматически при изменении значений.  Например, можно сделать так, чтобы значение в элементе управления **[Метка](controls/control-text-box.md)** становилось красным, если оно меньше нуля, и черным в противном случае. Таким образом, вы можете задать в качестве значения свойства **[Color](controls/properties-color-border.md)** этого элемента управления такую формулу:

**If( Value(TextBox1.Text) >= 0, Color.Black, Color.Red )**

При этом, если пользователь выберет элемент управления **[Кнопка](controls/control-button.md)**,  значения не изменятся, поэтому новые вычисления не выполняются. В Excel нет эквивалента элементу управления **[Кнопка](controls/control-button.md)**.  

Выбрав элемент управления **[Кнопка](controls/control-button.md)**, пользователь инициирует последовательность действий или схем поведения, которые приводят к изменению состояния приложения.

* Изменение отображающегося экрана: **[Обратно](functions/function-navigate.md)**  и **[Navigate](functions/function-navigate.md)** функции.
* Элемент управления [сигнала](functions/signals.md): **[Включить](functions/function-enable-disable.md)**  и **[отключить](functions/function-enable-disable.md)** функции.
* Обновление, обновление или удаление элементов в [источника данных](working-with-data-sources.md): **[Обновить](functions/function-refresh.md)**,  **[обновление](functions/function-update-updateif.md)**,  **[UpdateIf](functions/function-update-updateif.md)**, **[Patch](functions/function-patch.md)**,  **[Удалить](functions/function-remove-removeif.md)**, **[RemoveIf](functions/function-remove-removeif.md)** функции.
* Обновление [переменной контекста](working-with-variables.md#use-a-context-variable):  **[UpdateContext](functions/function-updatecontext.md)**  функции.
* Создание, обновление или удаление элементов в [коллекции](working-with-data-sources.md#collections):  **[Собирать](functions/function-clear-collect-clearcollect.md)**,  **[Очистить](functions/function-clear-collect-clearcollect.md)**, **[ClearCollect](functions/function-clear-collect-clearcollect.md)** функции.

Поскольку эти функции изменяют состояние приложения, они не пересчитываются автоматически. Их можно использовать в формулах для **[OnSelect](controls/properties-core.md)**, **[OnVisible](controls/control-screen.md)**, **[OnHidden](controls/control-screen.md)** и других свойств, начинающихся на **On...**, которые называются формулами поведения.

### <a name="more-than-one-action"></a>Несколько действий
Чтобы создать список выполняемых действий, перечислите их через точку с запятой. Например, можно указать, что после обновления переменной контекста необходимо возвратиться на предыдущий экран:

* **UpdateContext( { x: 1}); Back()**

Действия выполняются в том порядке, в котором они указаны в формуле.  Следующая функция не выполняется до тех пор, пока не завершится выполнение текущей. В случае ошибки запуск последующих функций становится невозможным.

