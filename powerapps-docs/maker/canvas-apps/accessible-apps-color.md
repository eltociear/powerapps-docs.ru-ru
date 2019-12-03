---
title: Цвета высокой контрастности в приложениях на основе холста | Документы Майкрософт
description: Рекомендации по контрастам цветов для приложений Canvas в Power Apps
author: tahoon
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/23/2018
ms.author: tahoon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 26fd45efc56ad03bc37635c29ddc7a6dbbe71568
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74725374"
---
# <a name="accessible-colors-for-canvas-apps-in-power-apps"></a>Доступные цвета для приложений Canvas в Power Apps
Используемые в приложении на основе холста цвета должны восприниматься пользователями с цветовой слепотой и (или) слабым зрением. По умолчанию доступны все темы Power Apps. Если вы решите изменить цвета в приложении, соблюдайте эти рекомендации, чтобы обеспечить восприятие цветов. В Интернете можно найти ряд инструментов для выявления проблем с контрастностью цветов.

## <a name="minimum-contrast-for-text"></a>Минимальная контрастность текста
* Контрастность между текстом и фоном должна составлять не менее 4.5:1.
* Для крупного текста следует соблюдать контрастность не менее 3:1.
* К выключенному тексту не применяются требования по контрастности.

На практике это означает, что все интерактивные элементы управления должны иметь достаточную контрастность между следующими значениями:
* **[Color](controls/properties-color-border.md)** и **[Fill](controls/properties-color-border.md)**
* **[PressedColor](controls/properties-color-border.md)** и **[PressedFill](controls/properties-color-border.md)** ;
* **[HoverColor](controls/properties-color-border.md)** и **[HoverFill](controls/properties-color-border.md)** .

## <a name="minimum-contrast-for-non-text"></a>Минимальная контрастность для нетекстовых элементов

> [!NOTE]
> В стандарте [WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-contrast.html) требования к контрастности определены только для текста. Чтобы повысить читаемость, попробуйте применить еще не утвержденные [рекомендации по контрастности WCAG 2.1](https://www.w3.org/TR/WCAG21/#non-text-contrast), в которых описаны все важные элементы пользовательского интерфейса, например кнопки со значками. Для таких компонентов рекомендуется соблюдать соотношение не менее 3:1. Рекомендации, описанные в этом разделе, являются **необязательными** для соответствия рекомендациям WCAG 2,0.

### <a name="user-interface-components"></a>Компоненты пользовательского интерфейса
Все интерактивные элементы управления должны иметь достаточную контрастность между следующими значениями:
* **[FocusedBorderColor](controls/properties-color-border.md)** и цвета за пределами элемента.

Дополнительные требования по контрастности цветов применяются для тех элементов управления, у которых вся занимаемая область является интерактивной или информативной. К ним относятся, например, **[Button](controls/control-button.md)** и **[Icon](controls/control-shapes-icons.md)** (используемый в качестве кнопки). Эти требования нужны для того, чтобы элемент управления имел четкие границы и пользователь хорошо понимал, в какой зоне его можно щелкнуть или коснуться.

Если такой элемент управления имеет границу, нужно обеспечить достаточную контрастность между следующими значениями:
* **[BorderColor](controls/properties-color-border.md)** и цвета за пределами элемента;
* **[PressedBorderColor](controls/properties-color-border.md)** и цвета за пределами элемента;
* **[HoverBorderColor](controls/properties-color-border.md)** и цвета за пределами элемента.

Если граница не используется, нужно обеспечить достаточную контрастность между следующими значениями:
* **[Fill](controls/properties-color-border.md)** и цвета за пределами элемента;
* **[PressedFill](controls/properties-color-border.md)** и цвета за пределами элемента;
* **[HoverFill](controls/properties-color-border.md)** и цвета за его пределами.

### <a name="graphical-objects"></a>Графические объекты
Если изображение содержит важные сведения, мы рекомендуем применить к нему требования к контрастности. Это относится к элементам управления, которые могут отображать изображения: **[Audio](controls/control-audio-video.md)** , **[Image](controls/control-image.md)** , **[Microphone](controls/control-microphone.md)** или **[Video](controls/control-audio-video.md)** .

Также мы рекомендуем проверить контрастность для видео. Вместо этого или в дополнение к этому можно также предоставить [скрытые субтитры](controls/control-audio-video.md) с описанием видео.

## <a name="provide-other-visual-cues"></a>Предоставление других визуальных подсказок
Следите за тем, чтобы приложение никогда не передавало информацию только изменением цвета. Например, пользователи, не различающие красный и зеленый цвета, не смогут отличить красный цвет ошибки от зеленого сообщения об успешном завершении.

Чтобы передать такие сообщения, можно использовать дополнительные подсказки, например **[значки](controls/control-shapes-icons.md)** , или стили текста, такие как **[курсив](controls/properties-text.md)** и **[подчеркивание](controls/properties-text.md)** .

## <a name="next-steps"></a>Дальнейшие действия
Узнайте о [свойствах специальных возможностей](controls/properties-accessibility.md) в элементах управления Power Apps и попробуйте [воспользоваться средством проверки специальных возможностей](accessibility-checker.md).
