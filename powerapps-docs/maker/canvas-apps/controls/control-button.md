---
title: Справка по элементу управления "Кнопка" | Документация Майкрософт
description: Сведения об элементе управления "Кнопка" с описанием его свойств и примерами
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/25/2016
ms.author: fikaradz
ms.reviewer: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d4cde32e52240e04a3499444d2c1325d0105a945
ms.sourcegitcommit: 4ed29d83e90a2ecbb2f5e9ec5578e47a293a55ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63320585"
---
# <a name="button-control-in-powerapps"></a>Элемент управления "Кнопка" в PowerApps
Элемент управления, который пользователь нажимает для взаимодействия с приложением.

## <a name="description"></a>Описание
Настройте свойство **[OnSelect](properties-core.md)** элемента управления **Кнопка** для выполнения одной или нескольких формул при нажатии элемента управления пользователем.

## <a name="key-properties"></a>Основные свойства
**[OnSelect](properties-core.md)**  — поведение приложения, когда пользователь щелкает элемент управления или касается его.

**[Text](properties-core.md)**  — текст, отображаемый в элементе управления, или текст, который пользователь вводит в элемент управления.

## <a name="additional-properties"></a>Дополнительные свойства
**[Align](properties-text.md)**  — расположение текста относительно центра элемента управления по горизонтали.

**AutoDisableOnSelect** — автоматическое отключение элемента управления при выполнении функции, назначенной свойству **OnSelect**.

**[BorderColor](properties-color-border.md)**  — цвет границы элемента управления.

**[BorderStyle](properties-color-border.md)**  — стиль границы элемента управления: **Сплошная**, **Штриховая**, **Пунктирная** или **Отсутствует**.

**[BorderThickness](properties-color-border.md)**  — толщина границы элемента управления.

**[Color](properties-color-border.md)**  — цвет текста в элементе управления.

**[DisplayMode](properties-core.md)** — в зависимости от значения этого режима элемент управления разрешает пользователю вводить данные (**Изменение**), только отображает данные (**Просмотр**) или элемент вообще отключен (**Отключено**).

**[DisabledBorderColor](properties-color-border.md)** — цвет границы элемента управления, если для его свойства **[DisplayMode](properties-core.md)** установлено значение **Отключено**.

**[DisabledColor](properties-color-border.md)** — цвет текста в элементе управления, если для его свойства **[DisplayMode](properties-core.md)** установлено значение **Отключено**.

**[DisabledFill](properties-color-border.md)** — цвет фона элемента управления, если для его свойства **[DisplayMode](properties-core.md)** установлено значение **Отключено**.

**[FocusedBorderColor](properties-color-border.md)** — цвет границы элемента управления при наведении фокуса.

**[FocusedBorderThickness](properties-color-border.md)** — толщина границы элемента управления при наведении фокуса.

**[Fill](properties-color-border.md)**  — цвет фона элемента управления.

**[Font](properties-text.md)**  — имя семейства шрифтов, используемых для отображения текста.

**[FontWeight](properties-text.md)**  — толщина текста в элементе управления: **Полужирным шрифтом**, **Semibold**, **обычный**, или **светлее**.

**[Height](properties-size-location.md)**  — расстояние между верхним и нижним краем элемента управления.

**[HoverBorderColor](properties-color-border.md)**  — цвет границы элемента управления при удерживании указателя мыши на нем.

**[HoverColor](properties-color-border.md)**  — цвет текста в элементе управления при удерживании указателя мыши на нем.

**[HoverFill](properties-color-border.md)**  — цвет фона элемента управления при удерживании указателя мыши на нем.

**[Italic](properties-text.md)** определяет, когда текст в элементе управления отображается курсивом.

**[PaddingBottom](properties-size-location.md)**  — расстояние между текстом в элементе управления и нижним краем элемента управления.

**[PaddingLeft](properties-size-location.md)**  — расстояние между текстом в элементе управления и левым краем элемента управления.

**[PaddingRight](properties-size-location.md)**  — расстояние между текстом в элементе управления и правым краем элемента управления.

**[PaddingTop](properties-size-location.md)**  — расстояние между текстом в элементе управления и верхним краем элемента управления.

**Pressed** — значение *true* при нажатии элемента управления и *false* в противном случае.

**[PressedBorderColor](properties-color-border.md)**  — цвет границы элемента управления при щелчке или касании.

**[PressedColor](properties-color-border.md)**  — цвет текста в элементе управления при щелчке или касании.

**[PressedFill](properties-color-border.md)**  — цвет фона элемента управления при щелчке или касании.

**[RadiusBottomLeft](properties-size-location.md)**  — градус скругления нижнего левого угла элемента управления.

**[RadiusBottomRight](properties-size-location.md)**  — градус скругления нижнего правого угла элемента управления.

**[RadiusTopLeft](properties-size-location.md)**  — градус, до которого округляется верхний левый угол элемента управления.

**[RadiusTopRight](properties-size-location.md)**  — градус скругления верхнего правого угла элемента управления.

**[Size](properties-text.md)**  — размер шрифта текста, отображаемого в элементе управления.

**[Strikethrough](properties-text.md)** определяет, когда через текст, отображаемый в элементе управления, проходит линия.

**[TabIndex](properties-accessibility.md)** — порядок навигации с помощью клавиатуры относительно других элементов управления.

**[Tooltip](properties-core.md)** — пояснительный текст, отображаемый при наведении указателя мыши на элемент управления.

**[Underline](properties-text.md)** определяет, когда под текстом, отображаемым в элементе управления, проходит линия.

**[VerticalAlign](properties-text.md)**  — расположение текста в элементе управления относительно центра этого элемента управления по вертикали.

**[Visible](properties-core.md)** определяет, отображается ли элемент управления или он скрыт.

**[Width](properties-size-location.md)**  — расстояние между левым и правым краем элемента управления.

**[X](properties-size-location.md)**  — расстояние между левым краем элемента управления и левым краем его родительского контейнера (или экрана, если родительского контейнера нет).

**[Y](properties-size-location.md)**  — расстояние между верхним краем элемента управления и верхним краем его родительского контейнера (или экрана, если родительского контейнера нет).

## <a name="related-functions"></a>Связанные функции
**[Navigate( *имя_экрана*, *тип_перехода* )](../functions/function-navigate.md)**

## <a name="examples"></a>Примеры
### <a name="add-a-basic-formula-to-a-button"></a>Добавление основной формулы для кнопки
1. Добавьте элемент управления **[Текстовое поле](control-text-input.md)** и назовите его **Source**.
   
    Не знаете, как [добавить, назвать и настроить элемент управления](../add-configure-controls.md)?
2. Добавьте элемент управления **Кнопка**, укажите для свойства **[Text](properties-core.md)** значение "Add", а для свойства **[OnSelect](properties-core.md)** следующую формулу:<br>
   **UpdateContext({Total:Total + Value(Source.Text)})**
   
    Нужны дополнительные сведения о функции **[UpdateContext](../functions/function-updatecontext.md)** или [других функциях](../formula-reference.md)?
3. Добавьте элемент управления **[Метка](control-text-box.md)**, укажите для свойства **[Text](properties-core.md)** значение **Total** и нажмите клавишу **F5**.
4. Удалите текст по умолчанию из поля **Source**, введите в нем число, а затем нажмите (коснитесь) кнопку **Add**.
   
    В элементе управления **[Метка](control-text-box.md)** отображается введенное число.
5. Удалите число из поля **Source**, введите в нем другое число, а затем нажмите (коснитесь) кнопку **Add**.
   
    В элементе управления **[Метка](control-text-box.md)** отображается сумма двух введенных чисел.
6. (Необязательно.) Повторите предыдущее действие еще один или несколько раз.
7. Чтобы вернуться в рабочую область по умолчанию, нажмите клавишу Esc (или щелкните (коснитесь) значок "Закрыть" в правом верхнем углу).

### <a name="configure-a-button-with-multiple-formulas"></a>Настройка кнопки с несколькими формулами
Добавьте формулу, которая очищает элемент управления **Текстовое поле** перед следующим вводом значения.

1. Для свойства **[HintText](control-text-input.md)** текстового поля **Source** задайте значение "Введите число".
2. Задайте для свойства **[OnSelect](properties-core.md)** кнопки **Add** эту формулу:
   
    **UpdateContext({Total:Total + Value(Source.Text)});<br>UpdateContext({ClearInput: ""})**
   
    > [!NOTE]
   > Если указывается несколько формул, их следует разделять точками с запятой (**;**).
3. Для свойства **[Default](properties-core.md)** текстового поля **Source** задайте значение **ClearInput**.
4. Нажмите клавишу **F5**, затем протестируйте приложение, сложив несколько чисел.

### <a name="add-another-button-to-reset-the-total"></a>Добавление кнопки для сброса итогового результата
Добавьте вторую кнопку для удаления итогового результата между вычислениями.

1. Добавьте еще один элемент управления **Кнопка**, задайте значение "Clear" для ее свойства **[Text](properties-core.md)** и задайте следующую формулу в качестве значения свойства **[OnSelect](properties-core.md)**:
   
    **UpdateContext({Total:0})**
2. Нажмите клавишу **F5**, сложите несколько чисел, а затем нажмите (коснитесь) кнопку **Clear**, чтобы сбросить итоговый результат.

### <a name="change-a-buttons-appearance"></a>Изменение внешнего вида кнопки
#### <a name="change-a-buttons-shape"></a>Изменение формы кнопки
По умолчанию PowerApps создает прямоугольный элемент управления **Кнопка** со скругленными углами. Можно внести простые изменения в форму элемента управления **Кнопка**, задав его свойства **[Height](properties-size-location.md)**, **[Width](properties-size-location.md)** и **[Radius](properties-size-location.md)**.

> [!NOTE]
> [Значки и фигуры](control-shapes-icons.md) обеспечивают широкий элементов выбор при оформлении и могут выполнять некоторые основные функции элемента управления **Кнопка**. Тем не менее у **[значков и фигур](control-shapes-icons.md)** нет свойства **[Text](properties-core.md)**.

1. Добавьте элемент управления **Кнопка** и задайте для его свойств **[Height](properties-size-location.md)** и **[Width](properties-size-location.md)** значение **300**, чтобы получить большую квадратную кнопку.
2. Измените свойства **[RadiusTopLeft](properties-size-location.md)**, **[RadiusTopRight](properties-size-location.md)**, **[RadiusBottomLeft](properties-size-location.md)** и  **[RadiusBottomRight](properties-size-location.md)**, чтобы изменить степень кривизны углов кнопки. Ниже приведены примеры различных фигур, созданных на основе квадратной кнопки 300 x 300.
   
   * Задайте **150** для всех значений **[Radius](properties-size-location.md)**, чтобы создать круг.
   * Задайте для свойств **[RadiusTopLeft](properties-size-location.md)** и **[RadiusBottomRight](properties-size-location.md)** значение **300**, чтобы создать листообразную **кнопку**.
   * Задайте для свойств **[RadiusTopLeft](properties-size-location.md)** и **[RadiusTopRight](properties-size-location.md)** значение **300**, а для свойств **[RadiusBottomLeft](properties-size-location.md)** и **[RadiusBottomRight](properties-size-location.md)** — значение **100**, чтобы создать кнопку в виде вкладки.

#### <a name="change-a-buttons-color-when-you-hover-over-it"></a>Изменение цвета кнопки при наведении указателя мыши
По умолчанию яркость цвета заливки элемента управления **Кнопка** уменьшается на 20 % при наведении на него указателя мыши. Это поведение можно настроить, изменив свойство **[HoverFill](properties-color-border.md)**, которое использует функцию **[ColorFade](../functions/function-colors.md)**. Если задать для формулы **[ColorFade](../functions/function-colors.md)** положительное процентное значение, то при наведении указателя на кнопку ее цвет будет становиться ярче, а если задать отрицательное значение, то кнопка будет темнеть.

* Измените процентное значение **[ColorFade](../functions/function-colors.md)** в свойстве **[HoverFill](properties-color-border.md)** одной из созданных кнопок и посмотрите, что получится.

Можно также указать цвет элемента управления **Кнопка**, задав для его свойства **[HoverFill](properties-color-border.md)** формулу, содержащую функцию **[ColorValue](../functions/function-colors.md)** вместо функции **[ColorFade](../functions/function-colors.md)**, например **ColorValue("Red")**.

> [!NOTE]
> Значением цвета может быть любое определение цвета CSS (имя или шестнадцатеричное значение).

* Замените функцию **[ColorFade](../functions/function-colors.md)** функцией **[ColorValue](../functions/function-colors.md)** в одной из созданных кнопок и посмотрите, что получится.


## <a name="accessibility-guidelines"></a>Руководство по настройке специальных возможностей
### <a name="color-contrast"></a>Контрастность
* Применяются [стандартные требования по цветовому контрасту](../accessible-apps-color.md).

### <a name="screen-reader-support"></a>Поддержка средства чтения с экрана
* Должен присутствовать элемент **[Text](properties-core.md)**.

### <a name="keyboard-support"></a>Поддержка клавиатуры
* Значение элемента **[TabIndex](properties-accessibility.md)** должно быть равно нулю или больше нуля, чтобы пользователи могли использовать навигацию с помощью клавиатуры.
* Индикаторы фокуса должны быть хорошо видны. Для этого используются элементы **[FocusedBorderColor](properties-color-border.md)** и **[FocusedBorderThickness](properties-color-border.md)**.
 
