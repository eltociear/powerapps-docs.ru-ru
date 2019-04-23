---
title: Добавление списка, раскрывающегося списка и переключателей в приложение на основе холста | Документация Майкрософт
description: Создание и настройка элементов множественного выбора в приложении на основе холста в PowerApps
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/24/2018
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 293c850c5af980a480a56cb9fb3b8c7866950580
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61555936"
---
# <a name="add-a-list-box-a-drop-down-list-or-radio-buttons-to-a-canvas-app"></a>Добавление списка, раскрывающегося списка и переключателей в приложение на основе холста

Один столбец с данными (например, из таблицы, включающей несколько столбцов) в приложении на основе холста позволяет пользователям выбрать один или несколько элементов в списке.

- Список позволяет выбрать несколько элементов.
- Раскрывающийся список занимает меньше места на экране.
- Набор переключателей позволяет добиться определенного эффекта в дизайне.

В этой статье описываются списки и переключатели, но те же принципы применимы и к раскрывающимся спискам.

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]

## <a name="create-a-simple-list"></a>Создание простого списка

1. Добавьте элемент управления **List box** (Список) с именем **MyListBox** и присвойте его свойству **Items** следующее выражение:

    ```["circle","triangle","rectangle"]```  <br/>

    Содержимое конструктора будет выглядеть примерно так:

    ![][4]

4. На вкладке **Insert** (Вставить) щелкните **Icons** (Значки), выберите кружок и переместите его под **MyListBox**:

    ![][5]  

5. Добавьте треугольник и прямоугольник, а затем расположите фигуры в ряд под **MyListBox**:

    ![][6]  

6. Установите для свойства **[Visible](controls/properties-core.md)** (Видимость) фигур указанные ниже функции.  

   | Фигура | Функция в свойстве Visible |
   | --- | --- |
   | круг |```If("circle" in MyListBox.SelectedItems.Value, true)``` |
   | треугольник |```If("triangle" in MyListBox.SelectedItems.Value, true)``` |
   | прямоугольник |```If("rectangle" in MyListBox.SelectedItems.Value, true)``` |

7. Удерживая клавишу ALT, выберите одну или несколько фигур в **MyListBox**.

    Вы увидите только фигуры, которые выбираете.

В этих шагах для создания списка элементов вы использовали выражение. Тот же метод можно применять и к другим элементам. Например, с помощью **раскрывающегося списка** можно выводить на экран изображения товаров, их описания и т. п.

## <a name="add-radio-buttons"></a>Добавление переключателей
1. На вкладке **Home** (Главная) выберите **New Screen** (Создать экран), а затем — **Blank** (Пустой).

2. На вкладке **Insert** (Вставка) выберите **Controls** (Элементы управления), а затем — **Radio** (Переключатель).

    ![][10]  

3. Переименуйте **переключатель** в **Choices** (Варианты выбора) и установите для свойства **[Items](controls/properties-core.md)** (Элементы) следующую формулу:  
   ```["red","green","blue"]```  <br/>

    ![][12]  

    При необходимости измените размер элемента управления таким образом, чтобы отображались все варианты.

4. На вкладке **Insert** (Вставка) выберите **Icons** (Значки), а затем — круг.

5. Установите для свойства **[Fill](controls/properties-color-border.md)** (Заливка) круга следующую функцию:  
   ```If(Choices.Selected.Value = "red", Red, Choices.Selected.Value = "green", Green, Choices.Selected.Value = "blue", Blue)```  

    В этой формуле цвет круга меняется в зависимости от того, какой переключатель установлен.

6. Переместите круг под **переключатель**, как в этом примере:

    ![][14]  

7. Удерживая клавишу ALT, выберите другой переключатель, чтобы изменить цвет кружка.

[1]: ./media/add-list-box-drop-down-list-radio-button/preview.png
[2]: ./media/add-list-box-drop-down-list-radio-button/listbox.png
[3]: ./media/add-list-box-drop-down-list-radio-button/renamelistbox.png
[4]: ./media/add-list-box-drop-down-list-radio-button/itemslistbox.png
[5]: ./media/add-list-box-drop-down-list-radio-button/circle.png
[6]: ./media/add-list-box-drop-down-list-radio-button/allshapes.png
[10]: ./media/add-list-box-drop-down-list-radio-button/radiobutton.png
[12]: ./media/add-list-box-drop-down-list-radio-button/itemsradio.png
[14]: ./media/add-list-box-drop-down-list-radio-button/radiocircle.png
[15]: ./media/add-list-box-drop-down-list-radio-button/dropdown.png
