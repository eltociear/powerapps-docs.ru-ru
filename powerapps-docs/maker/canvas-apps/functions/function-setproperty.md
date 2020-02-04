---
title: Функция SetProperty | Документация Майкрософт
description: Справочные сведения, включая синтаксис, для функции SetProperty в Power Apps Test Studio
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
ms.openlocfilehash: dac65ed25a9e286b056cf3c1408554ca79ea3e11
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541159"
ms.PowerAppsDecimalTransform: true
---
# <a name="setproperty-function-in-power-apps-test-studio"></a>Функция SetProperty в Power Apps Test Studio

Функция SetProperty имитирует взаимодействие с элементами управления вводом, как если бы пользователь указал или установил значение элемента управления. Эта функция доступна только при написании тестов в Power Apps Test Studio. Следующие свойства можно задать с помощью функции SetProperty.

## <a name="syntax"></a>Синтаксис

*SetProperty (свойство элемента управления, значение)*

- *Свойство элемента управления* — обязательный аргумент. Свойство элемента управления, выбираемое от имени пользователя.
- *Значение* — обязательный аргумент. Значение свойства, задаваемое от имени пользователя. 

## <a name="examples"></a>Примеры

| Управление   | Свойство  | Пример выражения
| :- | :- | :-
| TextInput | Текст  | ```SetProperty(TextInput1.Text; "Sample text")```
| RichTextEditor    | HtmlText  | ```SetProperty(RichTextEditor1.HtmlText; "<p>Sample text</p>")```
| Переключатель    | Значение | ```SetProperty(Toggle1.Value; false)```
| Флажок  | Значение | ```SetProperty(Checkbox1.Value; false)```
| "Ползунок"    | Значение | ```SetProperty(Slider1.Value; 10)```
| Оценка    | Значение | ```SetProperty(Rating1.Value; 5)```
| DatePicker    | SelectedDate  | ```SetProperty(DatePicker1.SelectedDate; Date(2020;3;10))```
| Переключатель | Выбрано  | ```SetProperty(Radio1.Selected; "Yes")```
| Переключатель | SelectedText | ```SetProperty(Radio1.SelectedText; "Yes")```
| Раскрывающийся список | Выбрано | ```SetProperty(Dropdown1.Selected; {Value:"Sample value"})```
| Раскрывающийся список | SelectedText | ```SetProperty(Dropdown1.SelectedText; {Value:"Sample value"})```
| Combobox | Выбрано | ```SetProperty(Dropdown1.Selected; {Value:"Sample value"})```
| Combobox | SelectedItems | ```SetProperty(ComboBox1.SelectedItems; Table({Value:"Sample value"};({Value:"Sample value"}))```
| ListBox | Выбрано | ```SetProperty(Listbox1.Selected; {'Value':"Sample value"})```
| ListBox | SelectedItems | ```SetProperty(Listbox1.SelectedItems; Table({Value:"Sample value"};({Value:"Sample value"}))```

### <a name="see-also"></a>См. также

[Обзор Test Studio](../test-studio.md) <br>
[Использование Test Studio](../working-with-test-studio.md)