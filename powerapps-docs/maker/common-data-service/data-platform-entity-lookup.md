---
title: Краткое руководство по установлению отношений между сущностями через поле подстановки | Документы Майкрософт
description: Краткое руководство по созданию отношения между сущностями с помощью поля подстановки
services: powerapps
documentationcenter: na
author: clwesene
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 3/21/2018
ms.author: clwesene
ms.openlocfilehash: 37450b6e9f43780deaed4ff34b005472501bdb23
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="quickstart-create-a-relationship"></a>Краткое руководство. Создание отношения
Данные в одной сущности часто связаны с данными в другой. Например, у вас могут быть сущности **Учителя** и **Занятие**, а сущность **Занятие** может быть связана отношением подстановки с сущностью **Учителя** для показа информации о том, кто из учителей ведет занятие. Поле подстановки можно использовать для отображения данных из сущности **Учителя**. Такое поле также называется полем для поиска.

## <a name="define-a-relationship"></a>Установка связи
Вы можете создать несколько типов связей от одной сущности к другой (или внутри самой сущности). Для каждой сущности можно установить связи с несколькими сущностями. Кроме того, одна сущность может иметь несколько связей с другой. Ниже перечислены некоторые распространенные типы связей:


* **Многие к одному**. При таком типе отношения каждая запись в сущности A может соответствовать нескольким записям в сущности Б, но каждая запись в сущности Б может соответствовать только одной записи в сущности A. Например, занятие проводится в одной аудитории. Это наиболее распространенный тип отношения, который представлен в списке полей **полем подстановки**.
* **Многие к одному**. При таком типе отношения каждая запись в сущности Б может соответствовать нескольким записям в сущности А, но каждая запись в сущности А может соответствовать только одной записи в сущности Б. Например, один учитель ведет несколько занятий.
* **Многие ко многим**. При таком типе связи каждая запись в сущности A может соответствовать нескольким записям в сущности Б, и наоборот. Например, учащиеся посещают несколько занятий, и на каждом занятии может быть несколько учащихся.

## <a name="add-a-lookup-field-many-to-one-relationship"></a>Добавление поля подстановки (отношение "многие к одному")

Чтобы добавить в сущность отношение подстановки, необходимо создать связь на вкладке **Relationships** (Связи) и указать другую сущность, с которой вы хотите связать текущую.

1. На сайте [powerapps.com](https://web.powerapps.com) разверните раздел **Данные** и выберите элемент **Сущности** в области навигации слева.

    ![Сведения о сущности](./media/data-platform-cds-create-entity/entitylist.png "Список сущностей")

2. Выберите существующую сущность или [создайте новую](data-platform-create-entity.md).

3. Нажмите **Отношения**.

4. Нажмите кнопку **Добавить отношение**. Откроется новая панель, на которой можно выбрать сущность, отношение с которой необходимо создать. Выберите сущность в раскрывающемся списке **Связанная сущность**.

    ![Отношение "многие к одному"](./media/data-platform-cds-newrelationship/manytoone-1.png "Отношение "многие к одному"")

5. После выбора сущности поля подстановки будут отображаться в первичной сущности. По умолчанию их имена совпадают с именем сущности (в этом примере это "Аудитория"), но при необходимости их можно изменить.

    ![Отношение "многие к одному"](./media/data-platform-cds-newrelationship/manytoone-2.png "Отношение "многие к одному"")

6. Нажмите кнопку **Готово**, чтобы добавить отношение к сущности, а затем нажмите кнопку **Сохранить сущность**.

    ![Отношение "многие к одному"](./media/data-platform-cds-newrelationship/manytoone-3.png "Отношение "многие к одному"")

## <a name="add-a-one-to-many-relationship"></a>Добавление отношения "один ко многим"

Чтобы добавить отношение "один ко многим", создайте отношение на вкладке **Отношения** и укажите другую сущность, с которой необходимо установить отношение.

1. На сайте [powerapps.com](https://web.powerapps.com) разверните раздел **Данные** и выберите элемент **Сущности** в области навигации слева.

    ![Сведения о сущности](./media/data-platform-cds-create-entity/entitylist.png "Список сущностей")

2. Выберите существующую сущность или [создайте новую](data-platform-create-entity.md).

3. Нажмите **Отношения**.

4. Нажмите стрелку вниз справа от кнопки **Добавить отношение**, чтобы выбрать один из двух типов отношений. Выберите пункт **Один ко многим**. Откроется новая панель, на которой можно выбрать сущность, отношение с которой необходимо создать. Выберите сущность в раскрывающемся списке **Связанная сущность**.

    ![Отношение "один ко многим"](./media/data-platform-cds-newrelationship/onetomany-1.png "Отношение "один ко многим"")

5. После выбора сущности поля подстановки будут отображаться в первичной сущности. По умолчанию их имена совпадают с именем сущности (в этом примере это "Занятие"), но при необходимости их можно изменить.

    > [!NOTE]
    > В случае отношения "один ко многим" поле подстановки создается в связанной сущности, а не в текущей выбранной сущности. Если требуется поле подстановки в текущей сущности, создайте отношение "многие к одному".

    ![Отношение "один ко многим"](./media/data-platform-cds-newrelationship/onetomany-2.png "Отношение "один ко многим"")

6. Нажмите кнопку **Готово**, чтобы добавить отношение к сущности, а затем нажмите кнопку **Сохранить сущность**.

    ![Отношение "один ко многим"](./media/data-platform-cds-newrelationship/onetomany-3.png "Отношение "один ко многим"")

## <a name="add-a-many-to-many-relationship"></a>Добавление отношения "многие ко многим"

В настоящее время это можно сделать только через меню "Дополнительно". На домашней странице PowerApps в меню слева выберите "Дополнительно". Сведения о создании такого отношения см. в статье [Создание отношений N:N (многие ко многим)](/dynamics365/customer-engagement/customize/create-and-edit-nn-many-to-many-relationships).

## <a name="use-a-lookup-field-in-an-app"></a>Использование поля подстановки в приложении
При [автоматическом создании приложения](../canvas-apps/data-platform-create-app.md) из сущности, содержащей поле подстановки, отображается **раскрывающийся список**, который содержит данные из поля **первичного имени** сущности.

## <a name="next-steps"></a>Дальнейшие действия
* [Создание приложения с помощью базы данных Common Data Service](../canvas-apps/data-platform-create-app.md)
* [Create an app from scratch using a Common Data Service database](../canvas-apps/data-platform-create-app-scratch.md) (Создание приложения "с нуля" с помощью базы данных Common Data Service)
