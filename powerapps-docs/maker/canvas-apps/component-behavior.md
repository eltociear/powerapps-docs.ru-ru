---
title: Формулы поведения для компонентов | Документация Майкрософт
description: Активируйте приложению для выполнения одной или нескольких задач при выполнении действия на основе компонентов.
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 05/24/2019
ms.author: yifwang
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7275395a4c21afaebc60e9635461afc08f5e84a0
ms.sourcegitcommit: afe958805d8e1cfa4fdf02c7bceea947185f71f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/30/2019
ms.locfileid: "66420321"
---
# <a name="behavior-formulas-for-components"></a>Формулы поведения для компонентов

> [!IMPORTANT]
> Эта функция по-прежнему экспериментальных и отключен по умолчанию. Дополнительные сведения см. в разделе [экспериментальные и предварительной версий](working-with-experimental.md).

Укажите одно или несколько [формулах поведения](working-with-formulas-in-depth.md) , запускать, когда событие вносятся изменения в экземплярах компонента. Например, задать компонента **OnReset** свойство для одной или нескольких формул, выполнить инициализацию, Очистить входную и сброс значений, когда **Сброс** функция выполняется на экземплярах компонента.

## <a name="onreset"></a>OnReset ##

Компонент, выбранный, выберите **OnReset** в раскрывающемся списке свойств (справа от строки формул), а затем введите одной или нескольких формул.

> [!div class="mx-imgBorder"]
> ![Пример OnReset](./media/component-behavior/example-onreset.png)

Для тестирования **OnReset**, настроить элемент управления, чтобы сбросить компонента. Например, задать **OnSelect** свойства кнопки следующую формулу: **Сброс**(*ComponentName*)

> [!div class="mx-imgBorder"]
> ![Кнопку "сбросить"](./media/component-behavior/reset-button.png)
