---
title: Обзор приложения Canvas для базы данных Northwind | Документация Майкрософт
description: ''
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/17/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 48966659ca12ada12448543492731fff8431fbde
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/29/2019
ms.locfileid: "71995806"
---
# <a name="overview-of-the-canvas-app-for-northwind-traders"></a>Общие сведения о приложении Canvas для "Борей"

Сведения о приложении Canvas для управления реляционными данными в базе данных Northwind Trader, [установленной в среде](northwind-install.md). Затем выполните пошаговые инструкции в последующих разделах, чтобы создать это приложение с нуля, тем самым получая практический опыт работы с реляционными данными.

В этом разделе вы узнаете:

- Как пользователь приложения показывает и управляет реляционными данными в приложении.
- Типы данных, которые дискируют в приложении.
- Как создаются связи между этими типами данных.

На одном экране пользователь приложения может отображать, обновлять, создавать и удалять заказы.

> [!div class="mx-imgBorder"]
> ![завершения](media/northwind-orders-canvas-part1/orders-finished.png) приложения Canvas

## <a name="explore-the-user-interface"></a>Знакомство с пользовательским интерфейсом

### <a name="order-gallery"></a>Коллекция заказов

На левой границе приложения в галерее отображается список заказов, включая номер заказа, состояние, имя клиента и общую стоимость заказа... Пользователь может прокручивать список, чтобы найти заказ, а затем отобразить дополнительные сведения о нем, щелкнув стрелку заказа. Дополнительные сведения: [Создание коллекции заказов](northwind-orders-canvas-part1.md).

### <a name="summary-form"></a>Форма сводки

В правом верхнем углу формы обобщены сведения о порядке, выбранном пользователем в коллекции заказов. Сводка включает большую часть тех же сведений, что и эта коллекция, но в сводке также отображаются даты создания и оплаты заказа, а также имя и изображение сотрудника, который управлял заказом. Пользователь может изменить данные в форме, сохранить эти изменения, отменить их или удалить заказ, щелкнув значок рядом с правым краю заголовка окна. Дополнительные сведения: [Создание формы сводки](northwind-orders-canvas-part2.md).

### <a name="detail-gallery"></a>Коллекция сведений

В правом нижнем углу в другой коллекции отображаются сведения о том, какие продукты содержатся в выбранном заказе и в каком количестве. Каждый элемент в этой коллекции называется сведениями о заказе. Пользователь приложения может добавлять и удалять любой элемент в этой коллекции с помощью элементов управления в и. Дополнительные сведения: [Создание коллекции сведений](northwind-orders-canvas-part3.md).

> [!div class="mx-imgBorder"]
> ![определения областей экрана](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="explore-the-data-sources"></a>Просмотр источников данных

Чтобы создать это приложение, можно отобразить данные из пяти сущностей и набор параметров. Фактически в большинстве областей этого приложения отображаются данные из нескольких сущностей. Например, коллекция заказов содержит следующие сведения:

- Номер заказа является полем в сущности **Orders** .
- Состояние — это другое поле в сущности **Orders** , которое является параметром из набора параметров **Orders Status** .
- Имя клиента — это поле в сущности **Customers** .
- Общая стоимость вычисляется на основе данных в сущности **Order Details** .

Сводка содержит некоторые из тех же сведений, что и список заказов, но также содержит имя и изображение сотрудника, который управлял заказом. Эти сведения извлекаются из полей в сущности **Employees** . В коллекции сведений отображаются записи в сущности « **сведения о заказе** », а каждый продукт в этих деталях — запись в сущности « **заказ товаров** ».

## <a name="explore-the-relationships"></a>Изучение связей

Можно отобразить данные из различных источников (например, сущностей) в одной коллекции или форме, так как эти сущности имеют связи, созданные в базе данных.

### <a name="many-to-one-relationships"></a>Связи «многие к одному»

Например, сведения о клиенте и сотруднике для каждого заказа находятся в сущностях « **Заказчик** » и « **сотрудники** ». Таким образом, сущность **Orders** имеет связи "многие к одному" с этими сущностями, так как существует много заказов, каждая из которых может быть размещена только одним клиентом и управляться только одним сотрудником.

Каждый заказ также содержит один или несколько элементов строк, представляющих товары, которые содержатся в заказе, и их количество. Каждый элемент строки является записью в сущности **Order Details** , которая извлекает сведения о каждом продукте из сущности **заказ продуктов** . Каждая деталь идентифицирует только один продукт, но каждый продукт может отображаться в нескольких деталях. Таким образом, сущность **Order Details** имеет связь «многие к одному» с сущностью « **заказ товаров** ».

### <a name="one-to-many-relationships"></a>Связи «один ко многим»

Каждый заказ может содержать несколько элементов строк, но каждый элемент строки относится только к одному заказу. Таким образом, сущность **Orders** имеет связь «один ко многим» с сущностью « **Order Details** ».

### <a name="dot-notation-for-relationships"></a>Точечная нотация для связей 

Чтобы отобразить данные на основе связи между сущностями, можно использовать селектор свойств точки для прохода по связям между сущностями.  Например, каждая запись в сущности « **заказы** » извлекает сведения из сущности « **Клиенты** », чтобы коллекция заказов могла отображать имена клиентов. В этой коллекции вы настраиваете это поведение, присвоив свойству **Text** метки следующее выражение:<br>`ThisItem.Customer.Company`

**Сиситем** указывает запись в сущности **Orders** и извлекает сведения из сущности **Customers** о клиенте, который разместил заказ. В этом случае выражение указывает, что отображается название компании клиента. Тем не менее вся запись для этого клиента извлекается, поэтому можно было бы легко отобразить, например, адрес электронной почты для этого клиента.

В качестве другого примера анализа одной сущности в другую можно указать, что коллекция должна отображать записи в одной сущности на основе записи, выбранной пользователем в другой коллекции и находящиеся в другой сущности. Чтобы отобразить сведения о заказе, в качестве значения свойства **Items** коллекции сведений задайте следующее выражение:<br>`Gallery1.Selected.'Order Details'`

В этом случае **Gallery1. Selected** указывает запись в сущности **Orders** , точно так же, как **сиситем** в предыдущем примере. Однако это выражение не извлекает только одну запись, как в предыдущем выражении. Вместо этого он извлекает всю таблицу записей для отображения имени и стоимости каждого продукта (как отражается в сущности « **заказ товаров** ») и количества (как отражается в сущности « **Order Details** »).

## <a name="do-it-yourself"></a>Самостоятельное

Вы можете выполнить пошаговые инструкции, чтобы создать приложение Canvas Orders "Борей".  Инструкции делятся на три части:

1. [Создайте коллекцию заказов](northwind-orders-canvas-part1.md).
1. [Создайте сводную форму](northwind-orders-canvas-part2.md).
1. [Создание коллекции сведений](northwind-orders-canvas-part3.md).

Если вы хотите пропустить, решение содержит приложение начальной точки для каждой части.  В списке приложений найдите **заказы Northwind (Canvas), начиная с первой части** и т. д.

> [!div class="nextstepaction"]
> [Продолжайте создание коллекции заказов](northwind-orders-canvas-part1.md)
