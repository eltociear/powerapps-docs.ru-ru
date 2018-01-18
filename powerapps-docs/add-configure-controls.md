---
title: "Добавление и настройка элемента управления | Документация Майкрософт"
description: "Пошаговые инструкции по добавлению и настройке элементов управления напрямую, на панели инструментов, на вкладке свойств или в строке формул."
services: 
suite: powerapps
documentationcenter: na
author: skjerland
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 07/10/2017
ms.author: sharik
ms.openlocfilehash: 6173db69fadd35e179a667ba11e1258d08632968
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2017
---
# <a name="add-and-configure-a-control-in-powerapps"></a>Добавление и настройка элемента управления в PowerApps
Добавляйте различные элементы пользовательского интерфейса в приложение и настраивайте их внешний вид и поведение напрямую, на панели инструментов, на вкладке **Свойства** или в строке формул. Эти элементы пользовательского интерфейса называются элементами управления, а настраиваемые параметры — свойствами. 

**Предварительные требования**

1. [Зарегистрируйтесь](signup-for-powerapps.md) в службе PowerApps, [установите](http://aka.ms/powerappsinstall) и откройте ее, а затем войдите с помощью учетных данных, использованных при регистрации.
2. В PowerApps Studio в меню **Файл** (у левого края экрана) выберите **Создать**.
   
    ![Параметр "Создать" в меню "Файл"](./media/add-configure-controls/file-new.png)
3. На плитке **Blank app** (Пустое приложение) щелкните или нажмите **Phone layout** (Макет телефона).
   
    ![Создание приложения с нуля](./media/add-configure-controls/blank-app.png)
4. Если появится приглашение ознакомиться с кратким обзором основных областей интерфейса PowerApps, выберите **Next** (Далее) или **Skip** (Пропустить).
   
    ![Заставка краткого обзора](./media/add-configure-controls/quick-tour.png)
   
    Просмотреть обзор можно в любой момент. Для этого щелкните значок вопросительного знака в правом верхнем углу экрана, а затем выберите **Take the intro tour** (Ознакомиться с кратким обзором).

## <a name="add-a-control"></a>Добавление элемента управления
Чтобы добавить элемент управления (в различных категориях), перейдите на вкладку **Вставка** панели инструментов, выберите категорию, а затем — необходимый элемент управления. В этом разделе рассматриваются элементы управления по категориям, благодаря чему вы ознакомитесь с типами элементов управления, которые можно добавить, и узнаете, где находится каждый из них.

* На вкладке **Вставка** щелкните (коснитесь) любую из этих категорий, затем щелкните (коснитесь) элемент управления, который требуется добавить.
  
    **Текст**: "Метка", "Текстовое поле", "HTML-текст", "Ввод с помощью пера".<br>
    **Элементы управления**: "Кнопка", "Раскрывающийся список", "Выбор даты", "Поле со списком", "Флажок", "Переключатель", "Переключатель", "Ползунок", "Оценка", "Таймер".<br>
    **Коллекция**: "По вертикали", "По горизонтали", "Изменяющаяся высота", "Пустая, вертикальная", "Пустая, горизонтальная", "Пустая, горизонтальная, высота".<br>
    **Таблица данных**<br>
    **Формы**: "Изменить", "Отображать", "Форма сущности".<br>
    **Мультимедиа**: "Изображение", "Камера", "Штрихкод", "Видео", "Звук", "Микрофон", "Добавить изображение".<br>
    **Диаграммы**: "Гистограмма", "График", "Круговая диаграмма".<br>
    **Значки**

**Совет**. Если вам необходимо больше места для элементов управления, [добавьте экран](add-screen-context-variables.md).

## <a name="configure-a-control-directly"></a>Настройка элементов управления напрямую
В этом разделе вы добавите и настроите элемент управления **Метка**, но описанные здесь действия можно применять и к другим элементам управления.

1. Перейдите на вкладку **Вставка** панели инструментов и щелкните (коснитесь) **Метка**.
   
    ![Вкладка "Вставка"](./media/add-configure-controls/insert-text-box.png)
   
    Когда вы добавляете элемент управления, он выбран по умолчанию. Чтобы выбрать имеющийся элемент управления, щелкните или коснитесь его. После выбора вокруг него появится рамка выделения и отобразятся другие параметры изменения пользовательского интерфейса. С их помощью вы можете изменить выбранный элемент управления. Например, выбрав элемент управления **Метка**, вы увидите следующее:
   
    ![Выбранная метка](./media/add-configure-controls/selected-text-box.png)
   
    **Важно.** Если вы выбрали элемент управления, а затем выбрали другой или щелкнули свободное место на экране, выбор первого действия отменяется.
2. Сузьте элемент управления **Метка**, перетащив маркер края влево. (Средний маркер позволяет увеличить размер.)
   
    ![Метка с измененным размером](./media/add-configure-controls/shorter-text-box.png)
   
     Размер элемента управления можно также изменить с помощью свойств **[Height](controls/properties-size-location.md)** и **[Width](controls/properties-size-location.md)**, как описано далее в этой статье.
3. Переместите элемент управления **Метка**, перетащив рамку выделения (или с помощью свойств **[X](controls/properties-size-location.md)** и **[Y](controls/properties-size-location.md)**, как описано далее в этой статье).
4. Трижды щелкните текст, отображаемый в элементе управления **Метка**, а затем введите **Hello, World**.
   
    ![Метка с текстом](./media/add-configure-controls/change-text-directly.png)
   
     Этот текст можно изменить, задав для этого элемента управления свойство **[Text](controls/properties-core.md)**, как описано далее в этой статье.

## <a name="configure-a-control-from-the-toolbar"></a>Настройка элемента управления на панели инструментов
При настройке элемента управления на панели инструментов вы можете указать большее количество параметров по сравнению с его непосредственной настройкой.

1. Выберите элемент управления **Метка** и перейдите на вкладку **Главная** панели инструментов.
   
    ![Вкладка "Главная"](./media/add-configure-controls/home-tab.png)
2. Щелкните **Заливка**, а затем выберите цвет, например аквамариновый.
   
    ![Параметр "Заливка"](./media/add-configure-controls/fill-option.png)
   
    После этого в элементе управления **Метка** отобразятся изменения.
   
    ![Элемент управления "Метка" с аквамариновой заливкой](./media/add-configure-controls/change-fill.png)
3. Измените семейство шрифтов и размер текста (например, 18 пт, Georgia).
   
    ![Элементы управления шрифтом](./media/add-configure-controls/font-size.png)
   
    После этого в элементе управления **Метка** отобразятся изменения.
   
    ![18 пт, Georgia](./media/add-configure-controls/change-font.png)
4. Перейдите на вкладку **Метка**, щелкните или коснитесь **ВыровнятьПоВертикали**, а затем выберите **Top** (По верхнему краю).
   
    ![Вкладка "Текстовое поле"](./media/add-configure-controls/text-box-tab.png)
   
    После этого в элементе управления **Метка** отобразятся изменения.
   
    ![Метка с текстом, выровненным по верхнему краю](./media/add-configure-controls/change-align.png)

## <a name="configure-a-control-from-the-properties-tab"></a>Настройка элемента управления на вкладке "Свойства"
С помощью вкладки **Свойства** вы можете настроить элемент управления без необходимости писать формулу. В этом разделе вы добавите и настроите еще один элемент управления **Метка**, но описанные здесь действия можно применять и к другим элементам управления.

1. Добавьте еще один элемент управления **Метка**, как описано выше в этом разделе.
2. Выбрав созданный элемент управления, щелкните вкладку **Свойства** на панели справа.
   
    ![Панель свойств](./media/add-configure-controls/properties-panel.png)
3. В поле **Текст** введите **Вкладка "Свойства"**.
   
    ![Текст метки на панели свойств](./media/add-configure-controls/properties-panel-text.png)
   
    На элементе управления **Метка** отобразится введенный текст.
   
    ![Текст на холсте на панели свойств](./media/add-configure-controls/properties-panel-canvas-text.png)
4. На панели **Свойства** щелкните значок **Заливка** и выберите цвет.
   
    ![Цвет текста на панели свойств](./media/add-configure-controls/properties-panel-color.png)
   
    После этого в элементе управления **Метка** отобразятся изменения.
   
    ![Цвет холста на панели свойств](./media/add-configure-controls/properties-panel-canvas-color.png)
5. Выберите свойство **Color** на панели свойств.
   
    ![Свойство на панели свойств](./media/add-configure-controls/properties-panel-property.png)
   
    Значение свойства **Color** выделено в строке формул.
   
    ![Выражение свойства на панели свойств](./media/add-configure-controls/properties-panel-property-expression.png)
   
   1. Чтобы удалить второй элемент управления **Метка**, выберите его, а затем нажмите клавишу DELETE.

## <a name="configure-a-control-in-the-formula-bar"></a>Настройка элемента управления в строке формул
В строке формул вы можете задать свойства, которые невозможно задать напрямую, на вкладке **Свойства** или на панели инструментов. Например, вы можете задать подсказку, появляющуюся, когда пользователь наводит указатель мыши на элемент управления, но не щелкает его. Кроме того, вы также можете указать сложные формулы, позволяющие повысить производительность приложения.

Выполняя действия, описанные в этой статье, вы также изменяли значения [свойств](reference-properties.md) настроенного элемента управления.

* При изменении размера элемента управления вы изменили свойство **[Width](controls/properties-size-location.md)**.
* При перемещении элемента управления вы изменили свойства **[X](controls/properties-size-location.md)** и **[Y](controls/properties-size-location.md)**.
* При изменении параметров отображения текста элемента управления вы изменили свойство **[Text](controls/properties-core.md)**.

Чтобы не настраивать элемент управления напрямую, на вкладке **Свойства** или на панели инструментов, вы также можете обновить значение нужного свойства. Для этого выберите его в списке и укажите его значение в строке формул. Свойства сортируются по алфавиту. Используя этот подход, вы можете указать больше типов значений.

1. Выберите оставшийся элемент управления **Метка**. В списке свойств выберите **[Text](controls/properties-core.md)** и в строке формул введите **"My Company Name"** (вместе с кавычками).
   
    ![Строковый литерал в метке](./media/add-configure-controls/text-literal.png)
   
    Заключив строку текста в кавычки, вы указываете, что она должна рассматриваться точно так, как ее ввели. В качестве значения свойства можно также задать формулу.
2. Выберите элемент управления **Метка**. В списке свойств выберите **[Text](controls/properties-core.md)** и в строке формул введите **Today()** (без кавычек).
   
    В элементе управления отображается текущая дата.
   
    ![Функция Today](./media/add-configure-controls/today-function.png)
   
    **Совет.** Вы можете по-разному изменять [формат даты и времени](show-text-dates-times.md), а также выполнять с ними вычисления.

## <a name="configure-two-controls-to-interact-with-each-other"></a>Настройка взаимодействия между двумя элементами управления
В этом разделе вы добавите флажок, а затем настроите так, чтобы созданная метка отображалась только после установки этого флажка.

1. Перейдите на вкладку **Вставка**.
   
    ![Вкладка "Вставка"](./media/add-configure-controls/insert-tab.png)
2. Выберите **Элементы управления**, а затем щелкните **Флажок**.
   
    ![Добавление флажка](./media/add-configure-controls/insert-check-box.png)
3. Переместите элемент управления **Флажок** под элемент управления **Метка**, а затем для свойства **[Text](controls/properties-core.md)** элемента управления **Флажок** задайте значение **Show text**.
   
    ![Настройка флажка](./media/add-configure-controls/configure-check-box.png)
4. Выбрав элемент управления **Флажок**, щелкните его имя прямо над вкладкой **Свойства** и введите **MyCheckbox**.
   
    ![Изменение имени флажка](./media/add-configure-controls/properties-panel-rename.png)
5. Выберите элемент управления **Метка**.
6. На вкладке **Свойства** выберите свойство **Visible**.
   
    ![Свойство Visible](./media/add-configure-controls/properties-panel-visible-property.png)
7. В строке формул удалите значение **true**, а затем введите следующую формулу:
   
    **If(MyCheckbox.Value = true, true, false)**
   
    Эта **[функция If](functions/function-if.md)** указывает, что метка должна отображаться, только если установлен флажок. Так как флажок снят, элемент управления **Метка** не отображается (за исключением рамки выделения).
   
    ![Формула Visible](./media/add-configure-controls/visible-formula.png)
8. Щелкните элемент управления **Флажок**, чтобы добавить к нему рамку выделения, а затем щелкните еще раз, чтобы добавить отметку.
   
    После этого элемент управления **Метка** откроется снова:
   
    ![Метка отображается после установки флажка](./media/add-configure-controls/show-text.png)
9. Снимите **флажок**, чтобы скрыть элемент управления **Метка**.
   
    ![Метка исчезла после снятия флажка](./media/add-configure-controls/hide-text.png)

Это простой пример, но вы можете настроить внешний вид и более сложное поведение приложения, создав одну или несколько [формул](formula-reference.md).

## <a name="rename-a-screen-or-a-control"></a>Изменение имени экрана или элемента управления
Изменив имя экрана или элемента управления, вы можете создавать более удобные для чтения и изменения формулы.

1. Щелкните экран или элемент управления, который необходимо переименовать.
2. На панели справа щелкните имя элемента управления (прямо над вкладкой **Свойства**) и введите необходимое имя.
   
    ![Изменение имени флажка](./media/add-configure-controls/properties-panel-rename.png)

## <a name="find-and-select-a-screen-or-a-control"></a>Поиск и выбор экрана или элемента управления
Можно найти и выбрать определенный экран или элемент управления, даже если он скрыт или перекрыт другим элементом управления. Для этого можно найти его в левой области. В этой области отображается эскиз каждого экрана в приложении либо иерархическое представление всех экранов и элементов управления, которые оно содержит.

* **Чтобы переключиться между эскизами и иерархическим представлением**, щелкните (коснитесь) значок в правом верхнем углу области.
  
    ![Переключение представлений](./media/add-configure-controls/toggle-view.png)
* **Чтобы найти элемент управления**, введите один или несколько знаков, чтобы выделить имена элементов управления, которые содержат введенный вами текст.
  
    Если щелкнуть (коснуться) результат поиска, будет выбран соответствующий элемент управления в приложении.
  
    ![Поиск в представлении в виде дерева](./media/add-configure-controls/search.png)
* **Чтобы переместить экран вверх или вниз, скопировать, удалить или переименовать его**, щелкните этот экран правой кнопкой мыши (или щелкните (коснитесь) многоточие рядом с ним) и выберите необходимый параметр.
  
    ![Контекстное меню представления в виде дерева](./media/add-configure-controls/context.png)
* **Чтобы скопировать и вставить элемент управления, удалить или переименовать его**, щелкните этот элемент управления правой кнопкой мыши (или щелкните (коснитесь) многоточие рядом с ним) и выберите необходимый параметр.
