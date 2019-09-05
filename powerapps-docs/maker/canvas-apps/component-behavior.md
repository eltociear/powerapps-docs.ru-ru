---
title: Формулы поведения для компонентов | Документация Майкрософт
description: Активация приложения для выполнения одной или нескольких задач при выполнении действия на основе компонента.
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 05/24/2019
ms.author: yifwang
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c8ec4edd835f12fb6fccf04ba0fb27f1e755cac0
ms.sourcegitcommit: ea3ab5926541c60a9e7c17f52f937c9812d48c71
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/05/2019
ms.locfileid: "70310057"
---
# <a name="behavior-formulas-for-components"></a>Формулы поведения для компонентов

> [!IMPORTANT]
> Эта функция по-прежнему является экспериментальной и отключенной по умолчанию. Дополнительные сведения см. в разделе [экспериментальные и предварительные версии функций](working-with-experimental.md).

Укажите одну или несколько [формул поведения](working-with-formulas-in-depth.md) , которые выполняются, когда событие вызывает изменение в экземплярах компонента. Например, можно установить свойство **OnReset** компонента в одну или несколько формул, выполняющих инициализацию, очистку входных данных и сброс значений при выполнении функции **Reset** в экземплярах компонента.

## <a name="onreset"></a>OnReset

Выбрав компонент, выберите в раскрывающемся списке свойств (в правой части строки формул) команду **OnReset** , а затем введите одну или несколько формул.

> [!div class="mx-imgBorder"]
> ![Пример OnReset](./media/component-behavior/example-onreset.png)

Чтобы проверить **OnReset**, настройте элемент управления для сброса компонента. Например, задайте в качестве значения свойства **OnSelect** кнопки следующую формулу: **Сброс параметров** (*ComponentName*)

> [!div class="mx-imgBorder"]
> ![Кнопка "Сброс"](./media/component-behavior/reset-button.png)
