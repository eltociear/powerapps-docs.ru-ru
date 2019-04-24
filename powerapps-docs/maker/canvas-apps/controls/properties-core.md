---
title: Основные свойства | Документация Майкрософт
description: Справочные сведения о свойствах Disabled, Visible и ReadOnly.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 16065dc29d74655cbede25cea20148b343b790e6
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61560353"
---
# <a name="core-properties-in-powerapps"></a>Основные свойства в PowerApps
Настройка возможности видеть элемент управления или взаимодействовать с ним для пользователя.

### <a name="properties"></a>Свойства
**Default** — начальное значение элемента управления до его изменения пользователем.

* Применяется к элементам управления **[Карта](control-card.md)**, **[Флажок](control-check-box.md)**, **[Раскрывающийся список](control-drop-down.md)**, **[Коллекция](control-gallery.md)**, **[Поле со списком](control-list-box.md)**, **[Переключатель](control-radio.md)**, **[Оценка](control-rating.md)**, **[Ползунок](control-slider.md)**, **[Текстовое поле](control-text-input.md)** и **[Переключатель](control-toggle.md)**.

**DelayOutput** — задайте значение true, чтобы отложить действие во время ввода текста.

* Применяется к элементам управления **[Текстовое поле](control-text-input.md)** и **[Карта](control-card.md)**.

**DisplayMode** — возможные значения: **Изменение, Просмотр** или **Отключено**. В зависимости от значения этого режима элемент управления разрешает пользователю вводить данные (**Изменение**), только отображает данные (**Просмотр**) или элемент вообще отключен (**Отключено**).  В режиме **Просмотр** элементы управления вводом, такие как **[Ввод текста](control-text-input.md)**, **[Раскрывающийся список](control-drop-down.md)**, **[Выбор даты](control-date-picker.md)**, отображают только текст и не обрабатывают интерактивные элементы или элементы оформления.  Благодаря этому они могут отображаться в элементе управления "Формы" в качестве выходных данных для чтения.

* Применяется к элементам управления **[Добавить изображение](control-add-picture.md)**, **[Звук](control-audio-video.md)**, **[Кнопка](control-button.md)**, **[Камера](control-camera.md)**, **[Флажок](control-check-box.md)**, **[Гистограмма](control-column-line-chart.md)**, **[Средство выбора даты](control-date-picker.md)**, **[Раскрывающийся список](control-drop-down.md)**, **[Экспорт](control-export-import.md)**, **[Коллекция](control-gallery.md)**, **[HTML-текст](control-html-text.md)**, **[Значок](control-shapes-icons.md)**, **[Изображение](control-image.md)**, **[Импорт](control-export-import.md)**, **[Метка](control-text-box.md)**, **[График](control-column-line-chart.md)**, **[Поле со списком](control-list-box.md)**, **[Микрофон](control-microphone.md)**, **[Средство просмотра PDF](control-pdf-viewer.md)**, **[Ввод с помощью пера](control-pen-input.md)**, **[Круговая диаграмма](control-pie-chart.md)**, **[Переключатель](control-radio.md)**, **[Оценка](control-rating.md)**, **[Форма](control-shapes-icons.md)**, **[Ползунок](control-slider.md)**, **[Текстовое поле](control-text-input.md)**, **[Таймер](control-timer.md)**, **[Переключатель](control-toggle.md)** и **[Видео](control-audio-video.md)**.

**Items** — источник данных, отображаемых в элементе управления, такой как коллекция, список или диаграмма.

* Применяется к элементам управления **[Гистограмма](control-column-line-chart.md)**, **[Раскрывающийся список](control-drop-down.md)**, **[Коллекция](control-gallery.md)**, **[График](control-column-line-chart.md)**, **[Поле со списком](control-list-box.md)**, **[Круговая диаграмма](control-pie-chart.md)** и **[Переключатель](control-radio.md)**.

**OnChange** — поведение приложения, когда пользователь изменяет значение элемента управления (например, перемещая ползунок).

* Применяется к элементам управления **[Добавить изображение](control-add-picture.md)**, **[Раскрывающийся список](control-drop-down.md)**, **[Поле со списком](control-list-box.md)**, **[Переключатель](control-radio.md)**, **[Оценка](control-rating.md)**, **[Ползунок](control-slider.md)**, **[Текстовое поле](control-text-input.md)** и **[Переключатель](control-toggle.md)**.

**OnSelect** — поведение приложения, когда пользователь щелкает элемент управления или касается его.

* Применяется к элементам управления **[Добавить изображение](control-add-picture.md)**, **[Кнопка](control-button.md)**, **[Камера](control-camera.md)**, **[Флажок](control-check-box.md)**, **[Гистограмма](control-column-line-chart.md)**, **[Средство выбора даты](control-date-picker.md)**, **[Раскрывающийся список](control-drop-down.md)**, **[Экспорт](control-export-import.md)**, **[HTML-текст](control-html-text.md)**, **[Значок](control-shapes-icons.md)**, **[Изображение](control-image.md)**, **[Импорт](control-export-import.md)**, **[Метка](control-text-box.md)**, **[График](control-column-line-chart.md)**, **[Поле со списком](control-list-box.md)**, **[Микрофон](control-microphone.md)**, **[Средство просмотра PDF](control-pdf-viewer.md)**, **[Ввод с помощью пера](control-pen-input.md)**, **[Круговая диаграмма](control-pie-chart.md)**, **[Переключатель](control-radio.md)**, **[Оценка](control-rating.md)**, **[Форма](control-shapes-icons.md)**, **[Ползунок](control-slider.md)**, **[Текстовое поле](control-text-input.md)**, **[Таймер](control-timer.md)** и **[Переключатель](control-toggle.md)**.

**Reset** — определяет, возвращается ли элемент управления к значению по умолчанию.  См. также сведения о функции **[Reset](../functions/function-reset.md)**.

* Применяется к элементам управления **[Звук](control-audio-video.md)**, **[Флажок](control-check-box.md)**, **[Раскрывающийся список](control-drop-down.md)**, **[Поле со списком](control-list-box.md)**, **[Микрофон](control-microphone.md)**, **[Переключатель](control-radio.md)**, **[Оценка](control-rating.md)**, **[Ползунок](control-slider.md)**, **[Текстовое поле](control-text-input.md)**, **[Таймер](control-timer.md)**, **[Переключатель](control-toggle.md)** и **[Видео](control-audio-video.md)**.

**Text** — текст, отображаемый в элементе управления, или текст, который пользователь вводит в элемент управления.

* Применяется к элементам управления **[Добавить изображение](control-add-picture.md)**, **[Кнопка](control-button.md)**, **[Флажок](control-check-box.md)**, **[Экспорт](control-export-import.md)**, **[Импорт](control-export-import.md)**, **[Метка](control-text-box.md)**, **[Текстовое поле](control-text-input.md)** и **[Таймер](control-timer.md)**.

**Tooltip** — пояснительный текст, отображаемый при наведении указателя мыши на элемент управления.

* Применяется к элементам управления **[Звук](control-audio-video.md)**, **[Кнопка](control-button.md)**, **[Камера](control-camera.md)**, **[Флажок](control-check-box.md)**, **[Раскрывающийся список](control-drop-down.md)**, **[HTML-текст](control-html-text.md)**, **[Изображение](control-image.md)**, **[Метка](control-text-box.md)**, **[Поле со списком](control-list-box.md)**, **[Микрофон](control-microphone.md)**, **[Средство просмотра PDF](control-pdf-viewer.md)**, **[Ввод с помощью пера](control-pen-input.md)**, **[Переключатель](control-radio.md)**, **[Оценка](control-rating.md)**, **[Ползунок](control-slider.md)**, **[Текстовое поле](control-text-input.md)**, **[Таймер](control-timer.md)**, **[Переключатель](control-toggle.md)** и **[Видео](control-audio-video.md)**.

**Value** — значение элемента управления для ввода.

* Применяется к элементам управления **[Флажок](control-check-box.md)**, **[Переключатель](control-radio.md)**, **[Ползунок](control-slider.md)** и **[Переключатель](control-toggle.md)**.

**Visible** — определяет, отображается элемент управления или он скрыт.

* Применяется к элементам управления **[Добавить изображение](control-add-picture.md)**, **[Звук](control-audio-video.md)**, **[Кнопка](control-button.md)**, **[Камера](control-camera.md)**, **[Карта](control-card.md)**, **[Флажок](control-check-box.md)**, **[Гистограмма](control-column-line-chart.md)**, **[Средство выбора даты](control-date-picker.md)**, **[Форма отображения](control-form-detail.md)**, **[Раскрывающийся список](control-drop-down.md)**, **[Форма изменения](control-form-detail.md)**, **[Экспорт](control-export-import.md)**, **[Коллекция](control-gallery.md)**, **[HTML-текст](control-html-text.md)**, **[Значок](control-shapes-icons.md)**, **[Изображение](control-image.md)**, **[Импорт](control-export-import.md)**, **[Метка](control-text-box.md)**, **[График](control-column-line-chart.md)**, **[Поле со списком](control-list-box.md)**, **[Микрофон](control-microphone.md)**, **[Средство просмотра PDF](control-pdf-viewer.md)**, **[Ввод с помощью пера](control-pen-input.md)**, **[Круговая диаграмма](control-pie-chart.md)**, **[Переключатель](control-radio.md)**, **[Оценка](control-rating.md)**, **[Форма](control-shapes-icons.md)**, **[Ползунок](control-slider.md)**, **[Текстовое поле](control-text-input.md)**, **[Таймер](control-timer.md)**, **[Переключатель](control-toggle.md)** и **[Видео](control-audio-video.md)**.

