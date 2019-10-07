---
title: Создание диаграммы в приложении на основе холста | Документы Майкрософт
description: Отображение категорий данных в виде графиков, круговых диаграмм или гистограмм в приложении на основе холста в PowerApps
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/23/2016
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9204c26cc54f4230496943d48934af75d21c5319
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "71994970"
---
# <a name="show-data-in-a-line-pie-or-bar-chart-in-powerapps"></a>Отображение данных в виде графика, круговой или линейчатой диаграммы в PowerApps

Используйте графики, круговые диаграммы и гистограммы для отображения данных в приложении на основе холста. При работе с диаграммами импортируемые данные должны быть структурированы с учетом следующих условий:

* Каждый ряд должен находиться в первой строке.
* Метки должны быть в первом столбце слева.

Например, данные должны выглядеть следующим образом:

![][9]

Вы можете создавать и использовать эти диаграммы в PowerApps. Приступим.

## <a name="prerequisites"></a>Технические условия

* [Зарегистрируйтесь](../signup-for-powerapps.md) в PowerApps, а затем [войдите в систему](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) с помощью учетных данных, использовавшихся при регистрации.
* Создайте приложение с помощью [шаблона](get-started-test-drive.md) или [данных](get-started-create-from-data.md) или создайте его с [нуля](get-started-create-from-blank.md).
* Узнайте, как [настроить элемент управления](add-configure-controls.md) в PowerApps.
* Скачайте файл [ChartData.zip](http://pwrappssamples.blob.core.windows.net/samples/ChartData.zip) с демонстрационными данными в виде XML-файла. Выполните действия, описанные в этом разделе, чтобы импортировать его непосредственно в приложение. Кроме того, вы можете распаковать ZIP-файл, открыть XML-файл в Excel и сохранить его в [учетной записи хранения в облаке](connections/cloud-storage-blob-connections.md).

## <a name="import-the-sample-data"></a>Импорт демонстрационных данных
Далее мы импортируем демонстрационные данные в коллекцию с именем **ProductRevenue**.

1. На вкладке **Вставка** выберите **Элементы управления**, а затем щелкните **Импорт**.  

    ![][11]  

2. Задайте для свойства элемента управления **[OnSelect](controls/properties-core.md)** следующую функцию.  

   ```Collect(ProductRevenue, Import1.Data)```

3. Нажмите клавишу F5, чтобы открыть режим предварительного просмотра, а затем нажмите кнопку **Импорт данных**.

4. В диалоговом окне **Открытие** выберите файл ChartData.zip, щелкните **Открыть** и нажмите клавишу ESC.

5. В меню **Файл** выберите **Коллекции**.

    Коллекция ProductRevenue указана с импортированными данными диаграммы:

    ![][1]  

   > [!NOTE]
   > Элемент управления "Импорт" позволяет импортировать данные, как в Excel, и создать коллекцию. Данные импортируются во время создания и предварительного просмотра приложения. Сейчас элемент управления "Импорт" не импортирует данные при публикации приложения.
   >

6. Нажмите клавишу ESC, чтобы вернуться в рабочую область по умолчанию.

## <a name="add-a-pie-chart"></a>Добавление круговой диаграммы
1. На вкладке **Вставка** выберите **Диаграммы**, а затем щелкните **Круговая диаграмма**.

2. Переместите круговую диаграмму под кнопку **Импорт данных**.

3. В элементе управления "Круговая диаграмма" выберите середину круговой диаграммы:   

    ![][10]

4. В качестве значения свойства **[Items](controls/properties-core.md)** круговой диаграммы задайте это выражение: `ProductRevenue.Revenue2014`

    ![][2]  

    На круговой диаграмме будут представлены данные о доходе за 2014 г.

    ![][3]  

## <a name="add-a-bar-chart-to-display-your-data"></a>Добавление линейчатой диаграммы для отображения данных
Теперь давайте используем коллекцию ProductRevenue на линейчатой диаграмме:

1. На вкладке **Главная** добавьте экран.]

2. На вкладке **Вставка** выберите **Диаграммы**, а затем щелкните **Гистограмма**.

3. Выберите середину гистограммы. Задайте для свойства гистограммы **[Items](controls/properties-core.md)** значение ```ProductRevenue```:

    ![][12]  

    На гистограмме будут представлены данные о доходе за 2012 г.

    ![][4]  

4. Выберите центральный квадрат на гистограмме:

    ![][5]

5. На вкладке **Диаграмма** выберите **Количество рядов**, а затем в строке формул введите **3**.

    ![][6]  

    На гистограмме будут показаны данные о доходах от продажи каждого товара за три года:

    ![][7]  

[1]: ./media/use-line-pie-bar-chart/productrevenuecollection.png
[2]: ./media/use-line-pie-bar-chart/itemsexpression.png
[3]: ./media/use-line-pie-bar-chart/piechart.png
[4]: ./media/use-line-pie-bar-chart/columnchart.png
[5]: ./media/use-line-pie-bar-chart/columnchartseries.png
[6]: ./media/use-line-pie-bar-chart/columnchartseriesfunction.png
[7]: ./media/use-line-pie-bar-chart/columnchartthreeyears.png
[8]: ./media/use-line-pie-bar-chart/preview.png
[9]: ./media/use-line-pie-bar-chart/tableformat.png
[10]: ./media/use-line-pie-bar-chart/middlepiechart.png
[11]: ./media/use-line-pie-bar-chart/import.png
[12]: ./media/use-line-pie-bar-chart/itemscolumnchart.png
