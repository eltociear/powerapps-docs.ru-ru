---
title: "Настройка макета коллекции | Документация Майкрософт"
description: "Укажите, какие элементы управления и поля в каждом из них необходимо отображать, а также какие столбцы нужно использовать для сортировки и поиска записей."
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
ms.date: 05/02/2017
ms.author: sharik
ms.openlocfilehash: c581abad70012eb66413a31bd765437df69b7a70
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2017
---
# <a name="customize-a-gallery-layout-in-powerapps"></a>Настройка макета коллекции в PowerApps
После автоматического создания приложения в PowerApps можно настроить экран обзора, который отображается по умолчанию. Укажите, какой макет следует использовать и какие столбцы нужно отображать и использовать при сортировке и фильтрации записей.

* Дополнительные сведения об автоматическом создании приложения см. в статье [Создание приложения для управления данными в списке SharePoint](app-from-sharepoint.md).
* Если вы еще не работали с PowerApps, см. статью [Знакомство с PowerApps](getting-started.md).

## <a name="prerequisites"></a>Технические условия
В этом руководстве вы можете ознакомиться с общими понятиями для работы с формами. Если вы хотите в точности выполнить все инструкции, необходимо сначала сделать следующее.

1. [Создайте подключение](connect-to-sharepoint.md) из PowerApps к SharePoint.
2. Создайте список SharePoint с именем **AppGen**, содержащий следующие столбцы.
   
    ![Примеры столбцов SharePoint](./media/customize-layout-sharepoint/list-columns.png)
3. Добавьте эти элементы к только что созданному списку.
   
    ![Образцы данных](./media/customize-layout-sharepoint/sample-data.png)
4. [Запустите автоматическое создание приложения](app-from-sharepoint.md) на основе только что созданного списка.
5. На панели навигации слева щелкните (коснитесь) значок, расположенный в правом верхнем углу, чтобы переключиться на представление эскиза.
   
    ![Переключение представлений](./media/customize-layout-sharepoint/toggle-view.png)

## <a name="customize-the-gallery"></a>Настройка коллекции
1. На панели навигации слева щелкните верхний эскиз или коснитесь его, чтобы выбрать экран **BrowseScreen1**.
   
    ![Эскиз BrowseScreen1](./media/customize-layout-sharepoint/browse-thumbnail.png)
   
    На экране **BrowseScreen1** отображается **идентификатор учетной записи** и **название** каждого элемента в списке SharePoint.
   
    ![Экран обзора, на котором отображаются заголовки и идентификаторы учетных записей](./media/customize-layout-sharepoint/browse-accountid.png)
   
    Далее необходимо указать, что для каждого элемента должно отображаться свойство **OrderDate**, а не **AccountID**.
2. На экране щелкните или коснитесь **AccountID** для первого элемента.
   
    При выборе элемента пользовательского интерфейса (или элемента управления) вокруг него отобразится граница выделения с маркерами изменения размера.
   
    ![Выбор текста первого элемента](./media/customize-layout-sharepoint/select-body.png)
3. На панели справа откройте список **Title1** и щелкните **OrderDate**.
   
    ![Отображение заголовка](./media/customize-layout-sharepoint/bind-data.png)
   
    После этого на экране **BrowseScreen1** отобразятся изменения.
   
    ![Макет с датами](./media/customize-layout-sharepoint/browse-dates.png)

Дополнительные сведения о коллекциях см. в статье [Отображение списка элементов в PowerApps](add-gallery.md).

## <a name="set-the-sort-and-search-columns"></a>Настройка столбцов для поиска и сортировки
1. Выберите элемент управления **Коллекция**, щелкнув любую запись, кроме первой, или коснувшись ее.
   
    ![Выбор коллекции](./media/customize-layout-sharepoint/select-gallery.png)
2. Убедитесь, что возле левого верхнего угла в списке свойств отображается **Items**.
   
    ![Свойство Items](./media/customize-layout-sharepoint/items-property.png)
   
    Значение этого свойства, отображаемое в строке формул, определяет не только источник данных, который отображается на экране, но и столбцы для фильтрации и сортировки.
   
    Например, строка формул может содержать такую формулу по умолчанию:
   
    ![Свойство Items со значением по умолчанию](./media/customize-layout-sharepoint/default-items.png)
   
    С помощью этой формулы пользователи могут отобразить только записи, которые начинаются на одну или несколько букв в столбце **AccountID**.
   
    ![Столбцы поиска по умолчанию](./media/customize-layout-sharepoint/default-search.png)
   
    Например, если пользователь введет в строке поиска букву A, на экране отобразится запись Europa. Заголовок этой записи соответствует идентификатору учетной записи, но не условию поиска. Далее в этой процедуре вы измените формулу для фильтрации записей по столбцу **Title**.
   
    В любом созданном приложении пользователи могут сортировать записи в алфавитном порядке по возрастанию или убыванию, нажав кнопку сортировки в правом верхнем углу. Эта формула указывает, что записи отсортируются по столбцу **AccountID**.
   
    ![Столбец сортировки по умолчанию](./media/customize-layout-sharepoint/default-sort.png)
   
    Далее в этой процедуре вы измените формулу для сортировки записей по столбцу **Заголовок**.
3. В строке формул замените экземпляры **AccountID** и **Title** (в том числе двойные кавычки вокруг второго экземпляра).
   
    Теперь в строке формул должна отобразиться следующая формула:<br>
    **SortByColumns(Filter(AppGen, StartsWith(Title, TextSearchBox1.Text)), "Title", If(SortDescending1, Descending, Ascending))**
   
    **Примечание.** Число, которое отображается после **TextSearchBox**, может быть больше, в зависимости от того, какие действия были выполнены ранее. Тем не менее это не повлияет на выполнение формулы.

## <a name="test-sorting-and-searching"></a>Тестирование функций поиска и сортировки
1. Откройте режим предварительного просмотра, нажав клавишу F5 (или нажав кнопку воспроизведения в правом верхнем углу).
   
    ![Открытие режима предварительного просмотра](./media/customize-layout-sharepoint/open-preview.png)
2. В правом верхнем углу экрана **BrowseScreen1** нажмите кнопку сортировки один или несколько раз для изменения порядка сортировки по возрастанию или по убыванию.
   
    ![Тестирование работы кнопки сортировки](./media/customize-layout-sharepoint/test-sort.png)
3. В поле поиска введите еще одну букву, чтобы отобразить только те записи, заголовок которых начинается на эту букву или буквы.
   
    ![Тестирование строки поиска](./media/customize-layout-sharepoint/test-search.png)
4. Удалите весь текст в строке поиска, а затем закройте режим предварительного просмотра, нажав клавишу ESC (либо щелкните значок закрытия или коснитесь его *в* строке заголовка PowerApps).
   
    ![Закрытие режима предварительного просмотра](./media/customize-layout-sharepoint/close-preview.png)

## <a name="change-the-title-of-the-screen"></a>Изменение заголовка экрана
1. Щелкните заголовок экрана или коснитесь его.
   
    ![Выбор заголовка экрана](./media/customize-layout-sharepoint/select-screen-title.png)
2. Убедитесь, что в списке свойств отображается **Text**, а затем введите необходимое имя, заключенное в двойные кавычки, в строке формул.
   
    ![Обновление заголовка экрана](./media/customize-layout-sharepoint/update-screen-title.png)
   
    После этого на экране **BrowseScreen1** отобразятся изменения.
   
    ![Новый заголовок экрана](./media/customize-layout-sharepoint/new-screen-title.png)

## <a name="next-steps"></a>Дальнейшие действия
* Нажмите клавиши CTRL+S, чтобы сохранить изменения.
* [Настройте формы](customize-forms-sharepoint.md) в приложении, указав поля, которые необходимо отобразить или скрыть, либо изменив порядок отображения полей.
