---
title: Функции связывания и отсвязи | Документация Майкрософт
description: Справочные сведения, включая синтаксис и пример, для функций связывания и отсвязи в Power Apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/22/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e2b1d0e8ab264b9576c18aa7d5803be30c4a45e1
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730546"
ms.PowerAppsDecimalTransform: true
---
# <a name="relate-and-unrelate-functions-in-power-apps"></a>Функции связывания и отсвязи в Power Apps

Свяжите и отменяйте связи между записями двух сущностей с помощью связи «один ко многим» или «многие ко многим».

## <a name="description"></a>Description

Функция **Relate** связывает две записи через связь "один ко многим" или "многие ко многим" в Common Data Service. Функция **unrelate** обращается к процессу и удаляет ссылку.

Для связей "один ко многим" сущность имеет поле внешнего ключа, которое указывает на запись одной сущности. **Связать** задает это поле для указания определенной записи одной сущности, а **unrelate** устанавливает это поле в *пустое*значение. **Если поле** уже задано при вызове ссылки, существующая ссылка будет потеряна в пользу новой связи. Это поле также можно задать с помощью функции [**Patch**](function-patch.md) или элемента управления **[формы редактирования](../controls/control-form-detail.md)** . не нужно использовать функцию **Relate** .

Для связей "многие ко многим" система, связывающая записи, поддерживает скрытую таблицу соединения. Доступ к этой таблице соединение напрямую невозможен; его можно считать только с помощью проекции "один ко многим" и задать с помощью функций **связывания** и **отсвязи** . Ни одна из связанных сущностей не имеет внешнего ключа.

Данные для сущности, указанной в первом аргументе, будут обновлены, чтобы отразить изменение, но данные для сущности, указанной во втором аргументе, — нет. Эти данные необходимо обновить вручную, выполнив функцию **[Refresh](function-refresh.md)** , чтобы отобразить результат операции.

Эти функции никогда не создают и не удаляют записи. Они связаны только с двумя уже существующими записями или отменяют их связь.

Эти функции можно использовать только в [формулах поведения](../working-with-formulas-in-depth.md).

> [!NOTE]
> Эти функции являются частью функции предварительной версии, и их поведение доступно только в том случае, если включены **реляционные данные, наборы параметров и другие новые функции для работы с компакт-дисками** . Это параметр уровня приложения, который по умолчанию включен для новых приложений. Чтобы найти этот переключатель, откройте меню **файл** , выберите **Параметры приложения**, а затем щелкните **Дополнительные параметры**. Ваши отзывы очень ценны для нас. Сообщите нам о том, что вы думаете на [форумах сообщества Power Apps](https://powerusers.microsoft.com/t5/Expressions-and-Formulas/bd-p/How-To).

## <a name="syntax"></a>Синтаксис

**Связь**( *Entity1RelatedTable*; *Entity2Record* )

* *Entity1RelatedTable* — обязательный. Для записи *сущности Entity1*таблица записей *Entity2* , связанных с отношением «один ко многим» или «многие ко многим».
* *Entity2Record* — обязательный. Запись *Entity2* , которую необходимо добавить в связь.

**Unrelate**( *Entity1RelatedTable*; *Entity2Record* )

* *Entity1RelatedTable* — обязательный. Для записи *сущности Entity1*таблица записей *Entity2* , связанных с отношением «один ко многим» или «многие ко многим».
* *Entity2Record* — обязательный. Запись *Entity2* , которую необходимо удалить из связи.

## <a name="examples"></a>Примеры

Рассмотрим сущность **Products** со следующими связями, как показано в [средстве просмотра сущностей портала Power Apps](../../common-data-service/create-edit-entities-portal.md):

| Отображаемое имя связи | Связанная сущность | Тип связи |
| --- | --- |
| Резервирование продукта | Предваритель | Один ко многим |
| Контакт &harr; продукта | Связь | Многие ко многим |

**Продукты** и **резервирования** связаны через связь «один ко многим».  Чтобы связать первую запись сущности **резервирования** с первой записью сущности **Products** , выполните следующие действия.

`Relate( First( Products ).Reservations; First( Reservations ) )`

Чтобы удалить связь между этими записями, выполните следующие действия.

`Unrelate( First( Products ).Reservations; First( Reservations ) )`

В то время, когда мы не создали или удалили или запись, была изменена только связь между записями.

**Продукты** и **Контакты** связаны через связь «многие ко многим».  Чтобы связать первую запись сущности **Contacts** с первой записью сущности **Products** , выполните следующие действия.

`Relate( First( Products ).Contacts; First( Contacts ) )`

Так как связи «многие ко многим» являются симметричными, мы могли бы также сделать это в обратном направлении:

`Relate( First( Contacts ).Products; First( Products ) )`

Чтобы удалить связь между этими записями, выполните следующие действия.

`Unrelate( First( Products ).Contacts; First( Contacts ) )`

ни

`Unrelate( First( Contacts ).Products; First( Products ) )`

В следующем пошаговом руководстве выполняются именно эти операции с этими сущностями с помощью приложения с элементами управления " **коллекция** **" и "поле со списком"** для выбора задействованных записей.

Эти примеры зависят от образца данных, устанавливаемых в среде. Либо [создайте пробную среду, включая демонстрационные данные](../../model-driven-apps/overview-model-driven-samples.md#get-sample-apps) , либо [добавьте образец данных в существующую среду](../../model-driven-apps/overview-model-driven-samples.md#install-or-uninstall-sample-data).

### <a name="one-to-many"></a>Один ко многим

#### <a name="relate-function"></a>Функция **связывания**

Сначала вы создадите простое приложение для просмотра и повторного назначения резервирований, связанных с продуктом.

1. Создайте [приложение планшета с пустого](../data-platform-create-app-scratch.md)поля.

1. На вкладке **Вид** выберите **источники данных**.

1. На панели **данные** выберите **добавить источник данных** > **Common Data Service** > **продукты** > **Подключиться**.  

    Сущность Products является частью образца данных, загруженных выше.

     ![Добавление сущности Products в качестве источника данных](media/function-relate-unrelate/products-connect.png)

1. На вкладке **Вставка** добавьте пустой вертикальный элемент управления " **[коллекция](../controls/control-gallery.md)** ".

1. Убедитесь, что только что добавленный элемент управления называется **Gallery1**, а затем переместите его и измените его размер, чтобы заполнить левую сторону экрана.

1. На вкладке **Свойства** задайте для свойства **элементы** **Gallery1**значение **продукты** и его **Макет** в поле **изображение и заголовок**.

    ![Настройка Продуктсгаллери](media/function-relate-unrelate/products-gallery.png)

1. В **Gallery1**убедитесь, что элемент управления **Label** имеет имя **Title1**, а затем задайте для его свойства **Text** значение **ThisItem.Name**.

    ![Настройка метки в Gallery1](media/function-relate-unrelate/products-title.png)

1. Выберите экран, чтобы избежать вставки следующего элемента в **Gallery1**.  Добавьте второй пустой элемент управления **коллекции** и убедитесь, что он называется **Gallery2**.

    **Gallery2** будет показывать резервирование для любого продукта, выбранного пользователем в **Gallery1**.

1. Переместите и измените размер **Gallery2** , чтобы заполнить верхнюю правую квадрант экрана.

1. используемых Добавьте элемент управления "Синяя **Метка** " над **Gallery2**, как показано на следующем рисунке.

1. В строке формул задайте для свойства **Items** элемента **Gallery2** значение **Gallery1. Selected. резервирования**.

    ![Настройка элементов Gallery2](media/function-relate-unrelate/reservations-gallery.png)

1. В области Свойства установите для макета **Gallery2**значение **Title**.

    ![Настройка макета Gallery2](media/function-relate-unrelate/reservations-gallery-right.png)

1. В **Gallery2**добавьте элемент управления **["поле со списком"](../controls/control-combo-box.md)** , убедитесь, что он называется **ComboBox1**, а затем переместите его и измените его размер, чтобы избежать блокировки других элементов управления в **Gallery2**.

1. На вкладке **Свойства** установите для свойства **Items** элемента **ComboBox1**значение **Products**.

    ![Задание свойству Items значения Products](media/function-relate-unrelate/reservations-combo-right.png)

1. Прокрутите вниз на вкладке **Свойства** и задайте для свойства **ComboBox1** **Разрешить множественный выбор** значение **выкл**.

    ![Задать значение "Разрешить множественный выбор"](media/function-relate-unrelate/reservations-singleselect-right.png)

1. В строке формул задайте для свойства **Дефаултселектедитемс** **ComboBox1**значение **сиситем. ' резервирование продукта '** .

    ![Set Дефаултселектедитемс для Ресервекомбо](media/function-relate-unrelate/reservations-combo.png)

1. В **Gallery2**задайте для свойства **OnSelect** **NextArrow2**следующую формулу:

    ```powerapps-comma
    Relate( ComboBox1.Selected.Reservations; ThisItem )
    ```

    Когда пользователь выбирает этот значок, текущее резервирование изменяется на продукт, который пользователь выбрал в **ComboBox1**.

    ![Настройка NextArrow2](media/function-relate-unrelate/reservations-relate.png)

1. Нажмите клавишу F5, чтобы протестировать приложение в режиме предварительного просмотра.

С помощью этого приложения пользователь может переместить резервирование с одного продукта на другой. Для резервирования одного продукта пользователь может выбрать другой продукт в **ComboBox1** , а затем выбрать **NextArrow2** , чтобы изменить это резервирование.

![Демонстрация функции связывания в приложении "один ко многим"](media/function-relate-unrelate/reservations-reassign.gif)

#### <a name="unrelate-function"></a>Функция **unrelate**

На этом этапе связь может быть перемещена из одной записи в другую, но связь не может быть полностью удалена. Функцию **unrelate** можно использовать для отключения записи резервирования от любого продукта.

1. На вкладке **Вид** выберите **источники данных**.

1. На панели **данные** выберите **добавить источник данных** > **Common Data Service** > **резервирования** > **подключить**.

1. В **Gallery2**Задайте формулу **OnSelect** для **NextArrow2** в этой формуле:

    ```powerapps-comma
    If( IsBlank( ComboBox1.Selected );
        Unrelate( Gallery1.Selected.Reservations; ThisItem );
        Relate( ComboBox1.Selected.Reservations; ThisItem )
    );;
    Refresh( Reservations )
    ```
    ![Значок "настроить правый"](media/function-relate-unrelate/reservations-relate-unrelate.png)

1. Скопируйте **Gallery2** в буфер обмена, выбрав его и нажав клавиши CTRL + C.

1. Вставьте дубликат **Gallery2** на тот же экран, нажав клавиши CTRL + V, а затем переместите его в нижнюю правую четверть экрана.

1. используемых Если вы добавили метку выше **Gallery2**, повторите предыдущие два шага для этой метки.

1. Убедитесь, что дубликат **Gallery2** имеет имя **Gallery2_1**, а затем задайте для его свойства **Items** значение этой формулы:

    ```powerapps-comma
    Filter( Reservations; IsBlank( 'Product Reservation' ) )
    ```

    Отображается предупреждение о делегировании, но в этом примере не имеет значения небольшой объем данных.

    ![Задание свойства Items для Gallery2_1](media/function-relate-unrelate/reservations-lost.png)

После внесения этих изменений пользователи могут снять выделение в **ComboBox1** для контакта, если он не зарезервирован для продукта. Контакты, которые не зарезервированы, отображаются в **Gallery2_1** , где пользователи могут назначать каждый контакт с продуктом.

   ![Демонстрация функций связывания и отсвязи в приложении "один ко многим"](media/function-relate-unrelate/reservations-lostandfound.gif)

### <a name="many-to-many"></a>Многие ко многим

#### <a name="create-a-many-to-many-relationship"></a>Создание связи «многие ко многим»

Образец данных не включает связь «многие ко многим», но вы создадите ее между сущностью Products и сущностью Contacts. Пользователи могут связывать каждый продукт с несколькими контактами и с каждым из них на несколько продуктов.

1. На [этой странице](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)выберите **данные** на левой панели навигации, а затем выберите **сущности**.

    ![Открытие списка сущностей](media/function-relate-unrelate/entity-list.png)

1. Измените фильтр сущностей, включив в него все сущности.

    По умолчанию образцы сущностей не отображаются.

    ![Удалить фильтр сущностей](media/function-relate-unrelate/entity-all.png)

1. Прокрутите вниз, откройте сущность « **продукт** » и выберите « **связи**».

    ![Вкладка "связи" для сущности "продукт"](media/function-relate-unrelate/entity-relationships.png)

1. Выберите **Добавить связь** > " **многие ко многим**".

    ![Добавить связь "многие ко многим"](media/function-relate-unrelate/entity-manytomany.png)

1. Выберите сущность **Contact** для связи.

    ![Выбор сущности "контакт"](media/function-relate-unrelate/entity-contact.png)

1. Выберите **готово** > **Сохранить сущность**.

    ![Список отношений для сущности Products](media/function-relate-unrelate/entity-done.png)

#### <a name="relate-and-unrelate-contacts-with-one-or-more-products"></a>Связать и отвязать контакты с одним или несколькими продуктами

Вы создадите еще одно приложение, похожее на ранее созданное в этом разделе, но новое приложение будет предлагать связь «многие ко многим». Каждый контакт сможет резервировать несколько продуктов, а не только одну.

1. В пустом приложении для планшетов создайте **Gallery1** как [первую процедуру](#one-to-many) в этой статье.

1. Добавьте еще один пустой вертикальный элемент управления " **коллекция** ", убедитесь, что он называется **Gallery2**, а затем переместите его в правый верхний угол экрана.

    Далее в этом разделе вы добавите элемент управления **"поле со списком"** в раздел **Gallery2**.

1. В строке формул задайте для свойства **Items** **Gallery2**значение **Gallery1. Selected. Contacts**.

    ![Настройка Контактсгаллери](media/function-relate-unrelate/contacts-gallery.png)

1. На вкладке **Свойства** установите для параметра **Макет** значение **изображение и заголовок**.

    ![Настройка Контактсгаллери](media/function-relate-unrelate/contacts-gallery-right.png)

1. В **Gallery2**убедитесь, что элемент управления " **Метка** " имеет имя **Title2**, а затем задайте для его свойства **Text** значение **сиситем. "полное имя"** .

    Текст не будет отображаться в этом элементе управления до тех пор, пока вы не завершите эту процедуру и не назначите контакту продукт.

    ![Отображение имени контакта](media/function-relate-unrelate/contacts-title.png)

1. Удалите **NextArrow2**, вставьте значок **отмены** и убедитесь, что он называется **Icon1**.

1. Задайте в качестве значения свойства **OnSelect** значка **отмены** следующую формулу: 

    ```powerapps-comma
    Unrelate( Gallery1.Selected.Contacts; ThisItem )
    ```

    ![Настройка значка отмены](media/function-relate-unrelate/contacts-unrelate.png)

1. На вкладке **Вид** выберите **источники данных**.

1. На панели **данные** выберите **добавить источник данных** > **Common Data Service** > **Контакты** > **Подключиться**.

1. В **разделе Gallery2**добавьте элемент управления **"поле со списком"** , убедитесь, что он называется **ComboBox1**, а затем установите для свойства **Items** значение **Contacts**.

    ![Настройка свойства элементов поля со списком](media/function-relate-unrelate/contacts-combo.png)

1. На вкладке **Свойства** установите переключатель **Разрешить множественный выбор** в значение **выкл**.

    ![Настройка свойства макета поля со списком](media/function-relate-unrelate/contacts-combo-right.png)

1. Вставьте значок **добавления** и задайте для его свойства **OnSelect** значение этой формулы: 

    ```powerapps-comma
    Relate( Gallery1.Selected.Contacts; ComboBox1.Selected )
    ```

    ![Настройка значка добавления](media/function-relate-unrelate/contacts-relate.png)

В этом приложении пользователи теперь могут свободно связывать набор контактов с каждым продуктом и отменять связь с ним.

- Чтобы добавить контакт к продукту, выберите контакт в поле со списком в нижней части экрана, а затем щелкните значок **Добавить** .
- Чтобы удалить контакт из продукта, щелкните значок **отмены** для этого контакта.

    В отличие от "один ко многим", связь "многие ко многим" позволяет пользователям связывать один и тот же контакт с несколькими продуктами.

![Демонстрируются функции связывания и отсвязи в приложении "многие ко многим"](media/function-relate-unrelate/contacts-relate-unrelate.gif)

#### <a name="in-reverse-relate-and-unrelate-products-with-multiple-contacts"></a>В обратную: связывание и отмена связи продуктов с несколькими контактами

Связи «многие ко многим» являются симметричными. Вы можете расширить пример, добавив продукты к контакту, а затем переворачивать их между двумя экранами, чтобы продемонстрировать, как связь отображается в любом направлении.

1. Задайте для **Свойства** **Screen1** значение **Refresh (Products)** .

    При обновлении связи «один ко многим» или «многие ко многим» происходит обновление только данных сущности первого аргумента в вызове **связывания** или **отсвязи.** Второй необходимо обновить вручную, если требуется перевернуть экраны этого приложения.

    ![Задать свойство OnVisible для обновления функции](media/function-relate-unrelate/contacts-refresh.png)

1. Повторяющаяся **Screen1**.

    Дубликат будет называться **Screen1_1** и формирует базу для просмотра связей от стороны контактов.

    ![Дублирование экрана](media/function-relate-unrelate/contacts-duplicate.png)

1. Чтобы создать обратные представления, измените эти формулы в элементах управления **Screen1_1**:

    - Screen1_1. OnVisible = `Refresh( Contacts )`
    - Gallery1_1. Items = `Contacts`
    - Title1_1. Text = `ThisItem.'Full Name'`
    - Label1_1. Text = `"Selected Contact Products"`
    - Gallery2_1. Items = `Gallery1_1.Selected.Products`
    - Title2_1. Text = `ThisItem.Name`
    - Icon1_1. OnSelect = `Unrelate( Gallery1_1.Selected.Products; ThisItem )`
    - ComboBox1_1. Items = `Products`
    - Icon2_1. OnSelect = `Relate( Gallery1_1.Selected.Products; ComboBox1_1.Selected )`

    Результат будет очень похож на предыдущий экран, но поступает на связь со стороны **контактов** .

    ![Отображение связи "многие ко многим", начиная с контактов](media/function-relate-unrelate/reverse-screen.png)

1. Вставьте **стрелку "вверх** " и задайте для свойства **OnSelect** значение **Navigate (Screen1, None)** .  Сделайте то же самое в **Screen1** с формулой **навигации (Screen1_1, None)** .

    ![Добавление навигации между экранами](media/function-relate-unrelate/reverse-navigate.png)

С помощью этого нового экрана пользователи могут добавить контакт к продукту, а затем перевернуть его к представлению контактов и просмотреть связанный с ним продукт. Связи являются симметричными и являются общими для двух экранов.

![Показать связь "многие ко многим" с любой стороны](media/function-relate-unrelate/contacts-reverse.gif)
