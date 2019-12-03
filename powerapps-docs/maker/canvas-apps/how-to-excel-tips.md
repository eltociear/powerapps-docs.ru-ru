---
title: Форматирование таблицы в Excel | Документы Майкрософт
description: Чтобы использовать данные Excel в Power Apps, необходимо отформатировать данные как таблицу. Добавление ключевого слова "изображение" в имена столбцов
author: yifwang
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/03/2018
ms.author: yifwang
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7b620205ed3fdeaa61768b62ef2db27a850be374
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732152"
---
# <a name="format-a-table-in-excel-and-naming-tips"></a>Советы по форматированию таблицы в Excel и присвоению имен
В Power Apps можно создать приложение Canvas на основе данных Excel только в том случае, если оно форматировано как таблица. Прочитав эту статью, вы узнаете, как форматировать таблицу в Excel, и получите некоторые советы по именованию столбцов Excel.

## <a name="how-to-format-a-table-in-excel"></a>Форматирование таблицы в Excel
Данные можно преобразовать в таблицу, нажав кнопку **Форматировать как таблицу** на вкладке **Главная** в Excel.

!["Форматировать как таблицу" в Excel](./media/how-to-excel-tips/format-table.png)

Можно также создать таблицу, выбрав **Таблица** на вкладке **Вставка**.

![Вставка таблицы в Excel](./media/how-to-excel-tips/insert-table.png)

Чтобы найти таблицу, перейдите в подраздел **Конструктор** раздела **Работа с таблицами** и переименуйте таблицу. Рекомендуется давать таблицам понятные имена, особенно если в одном файле Excel существует несколько таблиц.

![Переименование таблицы в Excel](./media/how-to-excel-tips/rename-table.png)

## <a name="naming-tips-in-excel"></a>Советы об именовании в Excel
Если столбец в таблице содержит изображения, в имени столбца должно быть слово "image". Это ключевое слово привяжет столбец к элементу управления изображениями в галерее.

![Подключение таблицы Excel с изображениями](./media/how-to-excel-tips/connect-gallery.png)

## <a name="next-steps"></a>Дальнейшие действия
* [Создание приложения из Excel в Power Apps](get-started-create-from-data.md) на основе указанной таблицы. По умолчанию приложение будет включать три экрана: для просмотра записей, для отображения сведений об отдельной записи, а также для создания или обновления записи.
* [Создайте приложение с нуля](get-started-create-from-blank.md) с помощью отформатированной в Excel таблицы. Приложение можно создать и настроить вручную. В нем вы также сможете просматривать, искать и изменять данные в таблице.
