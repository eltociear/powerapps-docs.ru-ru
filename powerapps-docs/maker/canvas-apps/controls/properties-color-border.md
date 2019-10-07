---
title: Свойства цвета и границы | Документация Майкрософт
description: Справочные сведения о таких свойствах, как BorderColor, HoverBorderColor, и PressedBorderColor.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 528dc54fe18971ff8971b4d0d7e87c3bf3c5367a
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "71986025"
---
# <a name="color-and-border-properties-in-powerapps"></a>Свойства цвета и границы в PowerApps

## <a name="overview"></a>Обзор

Настройка стиля элемента управления в зависимости от того, как с ним взаимодействует пользователь.

Цвета можно задавать различными способами.

- Перечисление [**цветов**](../functions/function-colors.md) : Укажите имена цветов из каскадных таблиц стилей, как показано в следующих примерах:

  - **Color.Red**
  - **Color.Indigo**

- Функция [**колорвалуе**](../functions/function-colors.md) : Укажите текстовые строки, такие как имена цветов из каскадных таблиц стилей и нотации шестнадцатеричного кода ( **#** ), как показано в следующих примерах:

  - **Колорвалуе ("AliceBlue")**
  - **ColorValue( "#ff00ff" )**

- Функция [**колорфаде**](../functions/function-colors.md) : Укажите, насколько проявление цвета — от полностью черного (-100%) до полного белого (100%), как в следующем примере:

  - **Колорфаде (цвет. красный, 50%)**

- Функция [**RGBA**](../functions/function-colors.md) : Укажите красный, зеленый и синий компоненты цвета от 0 до 255 и укажите альфа-канал от 0% (полностью прозрачный) до 100% (полностью непрозрачный), как показано в следующем примере:

  - **RGBA (255, 0, 255, 25%)**

Свойства цвета также могут ссылаться на другие свойства цвета. Например, **Label. пресседколор** может быть установлен в формулу **Label1. Color**, автоматически изменяя каскадное изменение из одного свойства на другое.

## <a name="normal"></a>Обычные условия

Обычно эти свойства применяются, если пользователь не взаимодействует с элементом управления.

**BorderColor** — цвет границы элемента управления.

- Применяется к элементам управления **[Добавить изображение](control-add-picture.md)** , **[Звук](control-audio-video.md)** , **[Кнопка](control-button.md)** , **[Камера](control-camera.md)** , **[Карта](control-card.md)** , **[Флажок](control-check-box.md)** , **[Гистограмма](control-column-line-chart.md)** , **[Средство выбора даты](control-date-picker.md)** , **[Форма просмотра](control-form-detail.md)** , **[Раскрывающийся список](control-drop-down.md)** , **[Форма редактирования](control-form-detail.md)** , **[Экспорт](control-export-import.md)** , **[Коллекция](control-gallery.md)** , **[HTML-текст](control-html-text.md)** , **[Изображение](control-image.md)** , **[Импорт](control-export-import.md)** , **[Метка](control-text-box.md)** , **[График](control-column-line-chart.md)** , **[Поле со списком](control-list-box.md)** , **[Микрофон](control-microphone.md)** , **[Средство просмотра PDF](control-pdf-viewer.md)** , **[Ввод с помощью пера](control-pen-input.md)** , **[Круговая диаграмма](control-pie-chart.md)** , **[Переключатель](control-radio.md)** , **[Оценка](control-rating.md)** , **[Ползунок](control-slider.md)** , **[Ввод текста](control-text-input.md)** , **[Таймер](control-timer.md)** , **[Переключатель](control-toggle.md)** и **[Видео](control-audio-video.md)** .

**BorderStyle** — стиль границы элемента управления: **Solid**, **Dashed**, **Dotted** или **None**.

- Применяется к элементам управления **[Добавить изображение](control-add-picture.md)** , **[Звук](control-audio-video.md)** , **[Кнопка](control-button.md)** , **[Камера](control-camera.md)** , **[Карта](control-card.md)** , **[Флажок](control-check-box.md)** , **[Гистограмма](control-column-line-chart.md)** , **[Средство выбора даты](control-date-picker.md)** , **[Форма просмотра](control-form-detail.md)** , **[Раскрывающийся список](control-drop-down.md)** , **[Форма редактирования](control-form-detail.md)** , **[Экспорт](control-export-import.md)** , **[Коллекция](control-gallery.md)** , **[HTML-текст](control-html-text.md)** , **[Изображение](control-image.md)** , **[Импорт](control-export-import.md)** , **[Метка](control-text-box.md)** , **[График](control-column-line-chart.md)** , **[Поле со списком](control-list-box.md)** , **[Микрофон](control-microphone.md)** , **[Средство просмотра PDF](control-pdf-viewer.md)** , **[Ввод с помощью пера](control-pen-input.md)** , **[Круговая диаграмма](control-pie-chart.md)** , **[Переключатель](control-radio.md)** , **[Оценка](control-rating.md)** , **[Ползунок](control-slider.md)** , **[Ввод текста](control-text-input.md)** , **[Таймер](control-timer.md)** , **[Переключатель](control-toggle.md)** и **[Видео](control-audio-video.md)** .

**BorderThickness** — толщина границы элемента управления.

- Применяется к элементам управления **[Добавить изображение](control-add-picture.md)** , **[Звук](control-audio-video.md)** , **[Кнопка](control-button.md)** , **[Камера](control-camera.md)** , **[Карта](control-card.md)** , **[Флажок](control-check-box.md)** , **[Гистограмма](control-column-line-chart.md)** , **[Средство выбора даты](control-date-picker.md)** , **[Форма просмотра](control-form-detail.md)** , **[Раскрывающийся список](control-drop-down.md)** , **[Форма редактирования](control-form-detail.md)** , **[Экспорт](control-export-import.md)** , **[Коллекция](control-gallery.md)** , **[HTML-текст](control-html-text.md)** , **[Изображение](control-image.md)** , **[Импорт](control-export-import.md)** , **[Метка](control-text-box.md)** , **[График](control-column-line-chart.md)** , **[Поле со списком](control-list-box.md)** , **[Микрофон](control-microphone.md)** , **[Средство просмотра PDF](control-pdf-viewer.md)** , **[Ввод с помощью пера](control-pen-input.md)** , **[Круговая диаграмма](control-pie-chart.md)** , **[Переключатель](control-radio.md)** , **[Оценка](control-rating.md)** , **[Ползунок](control-slider.md)** , **[Ввод текста](control-text-input.md)** , **[Таймер](control-timer.md)** , **[Переключатель](control-toggle.md)** и **[Видео](control-audio-video.md)** .

**Color** — цвет текста в элементе управления.

- Применяется к элементам управления **[Добавить изображение](control-add-picture.md)** , **[Кнопка](control-button.md)** , **[Флажок](control-check-box.md)** , **[Гистограмма](control-column-line-chart.md)** , **[Средство выбора даты](control-date-picker.md)** , **[Раскрывающийся список](control-drop-down.md)** , **[Экспорт](control-export-import.md)** , **[HTML-текст](control-html-text.md)** , **[Импорт](control-export-import.md)** , **[Метка](control-text-box.md)** , **[График](control-column-line-chart.md)** , **[Список](control-list-box.md)** , **[Микрофон](control-microphone.md)** , **[Ввод с помощью пера](control-pen-input.md)** , **[Круговая диаграмма](control-pie-chart.md)** , **[Переключатель](control-radio.md)** , **[Ввод текста](control-text-input.md)** и **[Таймер](control-timer.md)** .

**Fill** — цвет фона элемента управления.

- Применяется к элементам управления **[Добавить изображение](control-add-picture.md)** , **[Звук](control-audio-video.md)** , **[Кнопка](control-button.md)** , **[Карта](control-card.md)** , **[Флажок](control-check-box.md)** , **[Средство выбора даты](control-date-picker.md)** , **[Форма просмотра](control-form-detail.md)** , **[Раскрывающийся список](control-drop-down.md)** , **[Форма редактирования](control-form-detail.md)** , **[Экспорт](control-export-import.md)** , **[Коллекция](control-gallery.md)** , **[HTML-текст](control-html-text.md)** , **[Значок](control-shapes-icons.md)** , **[Изображение](control-image.md)** , **[Импорт](control-export-import.md)** , **[Метка](control-text-box.md)** , **[Список](control-list-box.md)** , **[Микрофон](control-microphone.md)** , **[Средство просмотра PDF](control-pdf-viewer.md)** , **[Ввод с помощью пера](control-pen-input.md)** , **[Переключатель](control-radio.md)** , **[Оценка](control-rating.md)** , **[Экран](control-screen.md)** , **[Форма](control-shapes-icons.md)** , **[Ввод текста](control-text-input.md)** , **[Таймер](control-timer.md)** , **[Переключатель](control-toggle.md)** и **[Видео](control-audio-video.md)** .

## <a name="focused"></a>Режим фокусировки

Эти свойства действуют при фокусировании на элементе управления.

**FocusedBorderColor** – цвет границы элемента управления при наведении фокуса.

**FocusedBorderThickness** — толщина границы элемента управления при наведении фокуса.

- Эти свойства применяются к элементам управления **[Add picture](control-add-picture.md)** , **[Attachments](control-attachments.md)** , **[Audio](control-audio-video.md)** , **[Button](control-button.md)** , **[Camera](control-camera.md)** , **[Check box](control-check-box.md)** , **[Combo box](control-combo-box.md)** , **[Date Picker](control-date-picker.md)** , **[Drop down](control-drop-down.md)** , **[Export](control-export-import.md)** , **[Gallery](control-gallery.md)** , **[Icon](control-shapes-icons.md)** , **[Image](control-image.md)** , **[Import](control-export-import.md)** , **[Label](control-text-box.md)** , **[List Box](control-list-box.md)** , **[Microphone](control-microphone.md)** , **[Radio](control-radio.md)** , **[Rating](control-rating.md)** , **[Shape](control-shapes-icons.md)** , **[Slider](control-slider.md)** , **[Text input](control-text-input.md)** , **[Timer](control-timer.md)** , **[Toggle](control-toggle.md)** и **[Video](control-audio-video.md)** .

## <a name="disabled"></a>Отключен

Эти свойства действуют, если элемент управления отключен.  Элемент управления может быть отключен, его свойству **[Disabled](properties-core.md)** присвоено значение *true*.

**DisabledBorderColor** — цвет границы элемента управления, если для его свойства **[DisplayMode](properties-core.md)** установлено значение **Отключено**.

- Применяется к элементам управления **[Добавить изображение](control-add-picture.md)** , **[Кнопка](control-button.md)** , **[Флажок](control-check-box.md)** , **[Гистограмма](control-column-line-chart.md)** , **[Средство выбора даты](control-date-picker.md)** , **[Раскрывающийся список](control-drop-down.md)** , **[Экспорт](control-export-import.md)** , **[HTML-текст](control-html-text.md)** , **[Изображение](control-image.md)** , **[Импорт](control-export-import.md)** , **[Метка](control-text-box.md)** , **[График](control-column-line-chart.md)** , **[Список](control-list-box.md)** , **[Микрофон](control-microphone.md)** , **[Средство просмотра PDF](control-pdf-viewer.md)** , **[Круговая диаграмма](control-pie-chart.md)** , **[Переключатель](control-radio.md)** , **[Ползунок](control-slider.md)** , **[Ввод текста](control-text-input.md)** , **[Таймер](control-timer.md)** и **[Переключатель](control-toggle.md)** .

**DisabledColor** — цвет текста в элементе управления, если для его свойства **[DisplayMode](properties-core.md)** установлено значение **Отключено**.

- Применяется к элементам управления **[Добавить изображение](control-add-picture.md)** , **[Кнопка](control-button.md)** , **[Флажок](control-check-box.md)** , **[Средство выбора даты](control-date-picker.md)** , **[Раскрывающийся список](control-drop-down.md)** , **[Экспорт](control-export-import.md)** , **[Импорт](control-export-import.md)** , **[Метка](control-text-box.md)** , **[Список](control-list-box.md)** , **[Микрофон](control-microphone.md)** , **[Переключатель](control-radio.md)** , **[Ввод текста](control-text-input.md)** и **[Таймер](control-timer.md)** .

**DisabledFill** — цвет фона элемента управления, если для его свойства **[DisplayMode](properties-core.md)** установлено значение **Отключено**.

- Применяется к элементам управления **[Добавить изображение](control-add-picture.md)** , **[Кнопка](control-button.md)** , **[Флажок](control-check-box.md)** , **[Средство выбора даты](control-date-picker.md)** , **[Раскрывающийся список](control-drop-down.md)** , **[Экспорт](control-export-import.md)** , **[HTML-текст](control-html-text.md)** , **[Изображение](control-image.md)** , **[Импорт](control-export-import.md)** , **[Метка](control-text-box.md)** , **[Список](control-list-box.md)** , **[Микрофон](control-microphone.md)** , **[Переключатель](control-radio.md)** , **[Ввод текста](control-text-input.md)** и **[Таймер](control-timer.md)** .

## <a name="hover"></a>При наведении указателя

Эти свойства действуют при наведении указателя мыши на элемент управления.

**HoverBorderColor** — цвет границы элемента управления при наведении на него указателя мыши.

- Применяется к элементам управления **[Добавить изображение](control-add-picture.md)** , **[Кнопка](control-button.md)** , **[Флажок](control-check-box.md)** , **[Гистограмма](control-column-line-chart.md)** , **[Раскрывающийся список](control-drop-down.md)** , **[Экспорт](control-export-import.md)** , **[HTML-текст](control-html-text.md)** , **[Изображение](control-image.md)** , **[Импорт](control-export-import.md)** , **[Метка](control-text-box.md)** , **[График](control-column-line-chart.md)** , **[Список](control-list-box.md)** , **[Микрофон](control-microphone.md)** , **[Средство просмотра PDF](control-pdf-viewer.md)** , **[Круговая диаграмма](control-pie-chart.md)** , **[Ползунок](control-slider.md)** , **[Ввод текста](control-text-input.md)** , **[Таймер](control-timer.md)** и **[Переключатель](control-toggle.md)** .

**HoverColor** — цвет текста в элементе управления при наведении на него указателя мыши.

- Применяется к элементам управления **[Добавить изображение](control-add-picture.md)** , **[Кнопка](control-button.md)** , **[Флажок](control-check-box.md)** , **[Раскрывающийся список](control-drop-down.md)** , **[Экспорт](control-export-import.md)** , **[Импорт](control-export-import.md)** , **[Метка](control-text-box.md)** , **[Список](control-list-box.md)** , **[Микрофон](control-microphone.md)** , **[Переключатель](control-radio.md)** , **[Ввод текста](control-text-input.md)** и **[Таймер](control-timer.md)** .

**HoverFill** — цвет фона элемента управления при наведении на него указателя мыши.

- Применяется к элементам управления **[Добавить изображение](control-add-picture.md)** , **[Кнопка](control-button.md)** , **[Флажок](control-check-box.md)** , **[Раскрывающийся список](control-drop-down.md)** , **[Экспорт](control-export-import.md)** , **[Значок](control-shapes-icons.md)** , **[Изображение](control-image.md)** , **[Импорт](control-export-import.md)** , **[Метка](control-text-box.md)** , **[Список](control-list-box.md)** , **[Микрофон](control-microphone.md)** , **[Переключатель](control-radio.md)** , **[Форма](control-shapes-icons.md)** , **[Ввод текста](control-text-input.md)** и **[Таймер](control-timer.md)** .

## <a name="pressed"></a>При нажатии

Эти свойства действуют при нажатии элемента управления кнопки или при щелчке графического элемента управления.

**PressedBorderColor** — цвет границы элемента управления при щелчке или касании.

- Применяется к элементам управления **[Добавить изображение](control-add-picture.md)** , **[Кнопка](control-button.md)** , **[Флажок](control-check-box.md)** , **[Гистограмма](control-column-line-chart.md)** , **[Раскрывающийся список](control-drop-down.md)** , **[Экспорт](control-export-import.md)** , **[Значок](control-shapes-icons.md)** , **[Изображение](control-image.md)** , **[Импорт](control-export-import.md)** , **[Метка](control-text-box.md)** , **[График](control-column-line-chart.md)** , **[Список](control-list-box.md)** , **[Микрофон](control-microphone.md)** , **[Средство просмотра PDF](control-pdf-viewer.md)** , **[Круговая диаграмма](control-pie-chart.md)** , **[Форма](control-shapes-icons.md)** , **[Ползунок](control-slider.md)** , **[Ввод текста](control-text-input.md)** , **[Таймер](control-timer.md)** и **[Переключатель](control-toggle.md)** .

**PressedColor** — цвет текста в элементе управления при щелчке или касании.

- Применяется к элементам управления **[Добавить изображение](control-add-picture.md)** , **[Кнопка](control-button.md)** , **[Флажок](control-check-box.md)** , **[Раскрывающийся список](control-drop-down.md)** , **[Экспорт](control-export-import.md)** , **[Импорт](control-export-import.md)** , **[Метка](control-text-box.md)** , **[Список](control-list-box.md)** , **[Микрофон](control-microphone.md)** , **[Переключатель](control-radio.md)** , **[Ввод текста](control-text-input.md)** и **[Таймер](control-timer.md)** .

**PressedFill** — цвет фона элемента управления при щелчке или касании.

- Применяется к элементам управления **[Добавить изображение](control-add-picture.md)** , **[Кнопка](control-button.md)** , **[Флажок](control-check-box.md)** , **[Раскрывающийся список](control-drop-down.md)** , **[Экспорт](control-export-import.md)** , **[Изображение](control-image.md)** , **[Импорт](control-export-import.md)** , **[Метка](control-text-box.md)** , **[Список](control-list-box.md)** , **[Микрофон](control-microphone.md)** , **[Переключатель](control-radio.md)** , **[Ввод текста](control-text-input.md)** и **[Таймер](control-timer.md)** .

## <a name="selection"></a>При выделении

Эти свойства действуют, когда пользователь выбирает элемент в элементе управления.

**SelectionColor** — цвет текста выбранного элемента или элементов списка или цвет инструмента выделения в элементе управления рукописным вводом.

- Применяется к элементам управления **[Раскрывающийся список](control-drop-down.md)** , **[Поле со списком](control-list-box.md)** и **[Ввод с помощью пера](control-pen-input.md)** .

**SelectionFill** — цвет фона выбранного элемента или элементов списка или выделенной области элемента управления рукописным вводом.

- Применяется к элементам управления **[Раскрывающийся список](control-drop-down.md)** и **[Поле со списком](control-list-box.md)** .