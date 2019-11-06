---
title: Справка по элементу управления "HTML-текст" | Документация Майкрософт
description: Сведения об элементе управления "HTML-текст" с описанием его свойств и примерами
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d514342bc51cdd6aa737da1b893530d702127bd1
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650471"
---
# <a name="html-text-control-in-powerapps"></a>Элемент управления "HTML-текст" в PowerApps
Поле, в котором отображается текст, а HTML-теги преобразуются в форматирование.

## <a name="description"></a>Description
Элемент управления **HTML-текст** не только отображает обычный текст и числа, но и преобразует HTML-теги, например неразрывные пробелы.

## <a name="key-properties"></a>Основные свойства
**[Color](properties-color-border.md)**  — цвет текста в элементе управления.

**[Font](properties-text.md)**  — имя семейства шрифтов, используемых для отображения текста.

**HtmlText**— это текст, который отображается в элементе управления "HtmlText" и который может содержать теги HTML.

## <a name="additional-properties"></a>Дополнительные свойства
**[BorderColor](properties-color-border.md)**  — цвет границы элемента управления.

**[BorderStyle](properties-color-border.md)**  — стиль границы элемента управления: **Сплошная**, **Штриховая**, **Пунктирная** или **Отсутствует**.

**[BorderThickness](properties-color-border.md)**  — толщина границы элемента управления.

**[DisplayMode](properties-core.md)** — в зависимости от значения этого режима элемент управления разрешает пользователю вводить данные (**Изменение**), только отображает данные (**Просмотр**) или элемент вообще отключен (**Отключено**).

**[DisabledBorderColor](properties-color-border.md)** — цвет границы элемента управления, если для его свойства **[DisplayMode](properties-core.md)** установлено значение **Отключено**.

**[DisabledFill](properties-color-border.md)** — цвет фона элемента управления, если для его свойства **[DisplayMode](properties-core.md)** установлено значение **Отключено**.

**[Fill](properties-color-border.md)**  — цвет фона элемента управления.

**[Height](properties-size-location.md)**  — расстояние между верхним и нижним краем элемента управления.

**[HoverBorderColor](properties-color-border.md)**  — цвет границы элемента управления при удерживании указателя мыши на нем.

**[OnSelect](properties-core.md)**  — поведение приложения, когда пользователь щелкает элемент управления или касается его.

**[PaddingBottom](properties-size-location.md)**  — расстояние между текстом в элементе управления и нижним краем элемента управления.

**[PaddingLeft](properties-size-location.md)**  — расстояние между текстом в элементе управления и левым краем элемента управления.

**[PaddingRight](properties-size-location.md)**  — расстояние между текстом в элементе управления и правым краем элемента управления.

**[PaddingTop](properties-size-location.md)**  — расстояние между текстом в элементе управления и верхним краем элемента управления.

**[Size](properties-text.md)**  — размер шрифта текста, отображаемого в элементе управления.

**[Tooltip](properties-core.md)** — пояснительный текст, отображаемый при наведении указателя мыши на элемент управления.

**[Visible](properties-core.md)** определяет, отображается ли элемент управления или он скрыт.

**[Width](properties-size-location.md)**  — расстояние между левым и правым краем элемента управления.

**[X](properties-size-location.md)**  — расстояние между левым краем элемента управления и левым краем его родительского контейнера (или экрана, если родительского контейнера нет).

**[Y](properties-size-location.md)**  — расстояние между верхним краем элемента управления и верхним краем его родительского контейнера (или экрана, если родительского контейнера нет).

## <a name="related-functions"></a>Связанные функции
[**Find**(*текст_для_поиска*, *в_тексте*)](../functions/function-find.md)

## <a name="example"></a>Пример
1. Добавьте элемент управления **[Метка](control-text-box.md)** , назовите его **Source** и укажите в качестве значения свойства **[Text](properties-core.md)** следующую строку:

"\<p>Мы\&nbsp;достигли необычайно \&quot;глубокого\&quot; уровня глобализации и локализации.\<p>"

Не знаете, как [добавить, назвать и настроить элемент управления](../add-configure-controls.md)?

1. Добавьте элемент управления **HTML-текст** и укажите для свойства **HtmlText** следующее значение:<br>
   **Source.Text**
   
     В элементе управления **HTML-текст** отображается тот же текст, что и в элементе управления **[Метка](control-text-box.md)** , но теги преобразуются в соответствующие символы.


## <a name="accessibility-guidelines"></a>Руководство по настройке специальных возможностей
Элемент **HtmlText** не обязательно должен быть интерактивным. Он должен использоваться только для отображения текста.

### <a name="color-contrast"></a>Контрастность
Необходимо настроить достаточный контраст для следующих элементов:
* **[Color](properties-color-border.md)** и **[Fill](properties-color-border.md)**
* Текст с пользовательскими цветами и фоном

### <a name="screen-reader-support"></a>Поддержка средства чтения с экрана
* Должен присутствовать элемент **HtmlText**.

### <a name="keyboard-support"></a>Поддержка клавиатуры
* Элемент **HtmlText** не должен содержать интерактивные элементы, такие как `<button>`, `<a>`, или `<input>`. Система **[TabIndex](properties-accessibility.md)** в PowerApps не обрабатывает элементы в **HtmlText**.
