---
title: Операторы и идентификаторы | Документация Майкрософт
description: Справочные сведения, включая синтаксис и примеры, для операторов и идентификаторов в Power Apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/29/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8c7f982f4d2eca1b097a312f74aff70063bf3396
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79212683"
ms.PowerAppsDecimalTransform: true
---
# <a name="operators-and-identifiers-in-power-apps"></a>Операторы и идентификаторы в Power Apps

Некоторые из этих операторов зависят от языка, используемого на компьютере автора.  Дополнительные сведения см. в статье [Глобальная поддержка](../global-apps.md).


|                               Символ                                |                        Type                         |                                                                                    Синтаксис                                                                                    |                                                                                                                           Описание                                                                                                                            |
|---------------------------------------------------------------------|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                **.**                                |                  Выбор свойства                  |                                                               **Slider1.Value<br>Color.Red<br>Acceleration.X**                                                               |                                               Извлекает свойство из [таблицы](../working-with-tables.md), элемента управления, [сигнала](signals.md) или перечисления.  Вы можете также использовать символ **!** для обеспечения обратной совместимости.                                                |
| **,**<br>[[зависящий от языка](../global-apps.md)]  |                  Десятичный разделитель                  |                                                             **1.23**                                                           |                                                                              Разделитель между целой и дробной частью числа. Этот символ зависит от языка.                                                                              |
|                               **( )**                               |                     Круглые скобки                     |                                                               **Filter(T; A &lt; 10)**<br><br>**(1 + 2) \* 3**                                                               |                                                                                           Принудительно применяет порядок приоритета и группирует подвыражения в большом выражении.                                                                                           |
|                                **+**                                |                Арифметические операторы                 |                                                                                  **1 + 2**                                                                                   |                                                                                                                             Сложение                                                                                                                             |
|                                **-**                                |                       &nbsp;                        |                                                                                  **2 – 1**                                                                                   |                                                                                                                       Символ вычитания и знак                                                                                                                       |
|                              *                               |                       &nbsp;                        |                                                                                  **2 \* 3**                                                                                  |                                                                                                                          Умножение                                                                                                                          |
|                                **/**                                |                       &nbsp;                        |                                                                                  **2 / 3**                                                                                   |                                                                                                   Деление (см. также сведения о функции **[Mod](function-mod.md)** )                                                                                                    |
|                                **^**                                |                       &nbsp;                        |                                                                                  **2 ^ 3**                                                                                   |                                                                                          Возведение в степень (эквивалентно функции **[Power](function-numericals.md)** )                                                                                          |
|                                **%**                                |                       &nbsp;                        |                                                                                   **20%**                                                                                    |                                                                                                         Процент (эквивалентно &quot;\* 1/100&quot;)                                                                                                          |
|                                **=**                                |                Операторы сравнения                 |                                                                               **Price = 100**                                                                                |                                                                                                                             Равно                                                                                                                             |
|                              **&gt;**                               |                       &nbsp;                        |                                                                              **Price &gt; 100**                                                                              |                                                                                                                           Более                                                                                                                           |
|                              **&gt;=**                              |                       &nbsp;                        |                                                                             **Price &gt;= 100**                                                                              |                                                                                                                     Больше или равно                                                                                                                     |
|                              **&lt;**                               |                       &nbsp;                        |                                                                              **Price &lt; 100**                                                                              |                                                                                                                            Менее                                                                                                                             |
|                              **&lt;=**                              |                       &nbsp;                        |                                                                             **Price &lt;= 100**                                                                              |                                                                                                                      Меньше или равно                                                                                                                       |
|                            **&lt;&gt;**                             |                       &nbsp;                        |                                                                            **Price &lt;&gt; 100**                                                                            |                                                                                                                           Не равно                                                                                                                           |
|                              **&amp;**                              |            Оператор объединения строк            |                                                      **&quot;Hello&quot; &amp; &quot; &quot; &amp; &quot;мира&quot;**                                                       |                                                                                                             Непрерывно отображает несколько строк.                                                                                                             |
|                      **&amp;&amp;** или **And**                      |                  Логические операторы                  |                                       **Price &lt; 100 &amp;&amp; Slider1.Value = 20**<br>или **Price &lt; 100 And Slider1.Value = 20**                                       |                                                                                         Логическая конъюнкция (эквивалентна функции **[And](function-logicals.md)** ).                                                                                          |
|                     **&#124;&#124;** или **Or**                      |                       &nbsp;                        |                                        **Price &lt; 100 &#124;&#124; Slider1.Value = 20** или **Price &lt; 100 Or Slider1.Value = 20**                                        |                                                                                          Логическое сложение, эквивалентное функции **[Or](function-logicals.md)**                                                                                          |
|                          **!** или **Not**                           |                       &nbsp;                        |                                                              **!(Price &lt; 100)** или **Not (Price &lt; 100)**                                                               |                                                                                           Логическое отрицание (эквивалентно функции **[Not](function-logicals.md)** ).                                                                                           |
|                             **exactin**                             |  [Операторы принадлежности](#in-and-exactin-operators)  |                                                                   **Gallery1.Selected exactin SavedItems**                                                                   |                                                                                       Принадлежит [коллекции](../working-with-data-sources.md#collections) или таблице.                                                                                        |
|                             **exactin**                             |                       &nbsp;                        |                                           **&quot;Windows&quot; exactin "To display windows in the Windows operating system..."**                                            |                                                                                                                 Тестирование подстроки (с учетом регистра).                                                                                                                  |
|                               **in**                                |                       &nbsp;                        |                                                                     **Gallery1.Selected in SavedItems**                                                                      |                                                                                                               Принадлежит коллекции или таблице.                                                                                                               |
|                               **in**                                |                       &nbsp;                        |                                                      **&quot;The&quot; in &quot;The keyboard and the monitor...&quot;**                                                      |                                                                                                                Тестирование подстроки (без учета регистра).                                                                                                                 |
|                                **@**                                | [Оператор устранения неоднозначности](#disambiguation-operator) |                                                                           **MyTable [@fieldname]**                                                                            |                                                                                                                       Устранение неоднозначности для поля.                                                                                                                       |
|                                **@**                                |                       &nbsp;                        |                                                                              **[@MyVariable]**                                                                               |                                                                                                                      Глобальное устранение неоднозначности.                                                                                                                       |
| **;**<br>[[зависящий от языка](../global-apps.md)]  |                   Разделитель элементов списка                    | **If(X < 10; "Low"; "Good")**<br>**{X: 12; Y: 32}**<br>**[1; 2; 3]** | Разделяет: <ul><li>аргументы в вызовах функций;</li><li>поля в [записи](../working-with-tables.md#elements-of-a-table);</li><li>записи в [таблице](../working-with-tables.md#inline-value-tables)</li></ul> Этот символ зависит от языка. |
| **;;**<br>[[зависящий от языка](../global-apps.md)] |                  Объединение формул в цепочку                   |                                     **Collect(T; A);; Navigate(S1; &quot;&quot;)**                                     |                                                                          Отдельные вызовы функций в свойствах поведения. Оператор цепочки зависит от языка.                                                                          |
|                             **Parent**                              |         [Родительский оператор](#parent-operator)         |                                                                               **Parent.Fill**                                                                                |                                                                                                           Доступ к свойствам контейнера элемента управления.                                                                                                            |
|                            **ThisItem**                             |       [Оператор ThisItem](#thisitem-operator)       |                                                                            **ThisItem.FirstName**                                                                            |                                                                                                          Доступ к полям коллекции или элемента управления формы                                                                                                           |

## <a name="in-and-exactin-operators"></a>Операторы in и exactin
Чтобы найти строку в [источнике данных](../working-with-data-sources.md), например в коллекции или импортированной таблице, можно использовать операторы **[in](operators.md#in-and-exactin-operators)** и **[exactin](operators.md#in-and-exactin-operators)** . Оператор **[in](operators.md#in-and-exactin-operators)** определяет совпадения независимо от регистра, а оператор **[exactin](operators.md#in-and-exactin-operators)** определяет только те совпадения, которые начинаются с буквы в том же регистре. Ниже приведен пример:

1. Создайте или импортируйте коллекцию с именем **Inventory** (Товары) и отобразите ее, следуя инструкциям в первом разделе статьи [Отображение текста и изображений в коллекции, а также выбор, сортировка и фильтрация коллекции](../show-images-text-gallery-sort-filter.md).
2. Задайте для свойства **[Items](../controls/properties-core.md)** коллекции эту формулу:
   <br>**Filter(Inventory; "E" in ProductName)**

    В коллекции отображаются все товары, за исключением Callisto, так как имя этого товара является единственным, которое не содержит указанную букву.
3. Задайте для свойства **[Items](../controls/properties-core.md)** коллекции следующую формулу:
   <br>**Filter(Inventory; "E" exactin ProductName)**

    В коллекции отображается только имя Europa, так как оно единственное, которое содержит указанную букву.

## <a name="thisitem-operator"></a>Оператор ThisItem
Вы можете отобразить данные в элементах управления **[Коллекция](../controls/control-gallery.md)** , **[Форма редактирования](../controls/control-form-detail.md)** или **[Форма просмотра](../controls/control-form-detail.md)** , привязав их к таблице или коллекции.  Эти элементы управления являются контейнером для других карточек и элементов управления.  Каждая карточка или элемент управления в контейнере может получить доступ к связанным данным через оператор **[ThisItem](operators.md#thisitem-operator)** .   

Используйте оператор **[сиситем](operators.md#thisitem-operator)** , чтобы указать [столбец](../working-with-tables.md#columns) данных, отображаемых в каждой карточке или элементе управления внутри внешнего элемента управления. Например, в статье об [отображении изображений и текста в коллекции](../show-images-text-gallery-sort-filter.md) этот оператор в коллекции товаров указывает, что элемент управления "Изображение" показывает вид товара, верхняя метка — имя товара, а нижняя метка — количество единиц товара.

Для вложенных коллекций оператор **[ThisItem](operators.md#thisitem-operator)** обращается к элементам внутренней коллекции. При условии, что во внутренних и внешних коллекциях между полями строк не возникает конфликтов, вы также можете напрямую использовать неполные имена полей (столбцов). Это позволит правилам внутренней коллекции ссылаться на элементы внешней коллекции.

## <a name="parent-operator"></a>Родительский оператор
На некоторых элементах управления размещаются другие элементы управления. Например, элементы управления **[Экран](../controls/control-screen.md)** , **[Коллекция](../controls/control-gallery.md)** , **[Карточка](../controls/control-card.md)** , **[Форма редактирования](../controls/control-form-detail.md)** и **[Форма просмотра](../controls/control-form-detail.md)** являются контейнерами элементов управления. Элемент управления, в котором размещаются другие элементы управления, называется "родительским".

На любой элемент управления в Power Apps можно ссылаться по имени из любого места в приложении. **Screen1** может быть именем экрана в приложении. Чтобы получить цвет фона этого экрана, можно использовать **Screen1.Fill**.

Элементы управления на этом экране предоставляют еще одну возможность. Они могут использовать относительную ссылку: **Родитель. Fill**. Оператор **[Parent](operators.md#parent-operator)** обращается к родительскому элементу управления нужного элемента, предоставляя доступ ко всем его свойствам. Использование **[этого](operators.md#parent-operator)** оператора удобно тем, что он не зависит от имени элемента управления. Вы можете скопировать и вставить элемент управления контейнера без необходимости изменять все ссылки в контейнере. Этот оператор также обеспечивает четкую связь между дочерним и родительским элементами управления при считывании формул.

## <a name="identifier-names"></a>Имена идентификаторов

Имена переменных, источников данных, столбцов и других объектов могут содержать любые [символы Юникода](https://en.wikipedia.org/wiki/Unicode).

Заключите имя, содержащее пробел или другой специальный символ, в одинарные кавычки.  Используйте две одинарные кавычки вместе, чтобы представить одну одинарную кавычку в имени.  Имена, которые не содержат специальные символы, не занимают одинарные кавычки.

Ниже приведены примеры имен столбцов, которые могут встречаться в таблице, и их представления в формуле.

| Имя столбца в базе данных   | Ссылка на столбец в формуле |
|-----------------------------|-------------------------------|
| SimpleName                  | ```SimpleName``` |
| NameWith123Numbers          | ```NameWith123Numbers``` |
| Имя с пробелами            | ```'Name with spaces'``` |
| Имя с двойными кавычками   | ```'Name with "double" quotes'``` |
| Имя с кавычками "Single"   | ```'Name with ''single'' quotes'``` |
| Имя с символом @ at      | ```'Name with an @ at sign'``` |

Для [обозначения текстовых строк](data-types.md#embedded-text)используются двойные кавычки.  

## <a name="display-names-and-logical-names"></a>Отображение имен и логических имен
Некоторые источники данных, такие как SharePoint и Common Data Service, имеют два разных имени для ссылки на одну и ту же таблицу или столбец данных:

* **Логическое имя** — имя, которое гарантированно уникально, не изменяется после создания, обычно не допускает пробелов и других специальных символов и не локализуется на разные языки.  В результате имя может быть несколько понятным.  Эти имена используются профессиональными разработчиками.  Например **cra3a_customfield**.  Это имя также может называться **именем схемы** или просто **именем**.

* **Отображаемое имя** — понятное имя пользователя, которое должно быть видно конечным пользователям.  Это имя может быть неуникальным, может меняться со временем, может содержать пробелы и любой символ Юникода, а также может быть локализовано на разные языки.  В соответствии с приведенным выше примером отображаемое имя может быть **пользовательским полем** с пробелами между словами.
 
Поскольку отображаемые имена проще понять, приложения Canvas предлагают их как варианты выбора и не предлагают логические имена.  Хотя логические имена не предлагаются, они по-прежнему могут использоваться при вводе непосредственно.

Например, представьте, что вы добавили **настраиваемое поле** в сущность в Common Data Service.  Системе будет назначено логическое имя, которое можно изменить только при создании поля.  Результат будет выглядеть примерно так:

> [!div class="mx-imgBorder"]  
> сущность учетных записей ![с добавленным настраиваемым полем, отображающая отображаемое имя "настраиваемое поле" и логическое имя "cr5e3_customfield"](media/operators/customfield_portal.png)

При создании ссылки на поле учетных записей предложение будет использовать **"настраиваемое поле"** , так как это отображаемое имя.  Обратите внимание, что необходимо использовать одинарные кавычки, так как это имя содержит пробел.

> [!div class="mx-imgBorder"]  
> Строка формул ![Studio, в которой отображаются предложения для имен полей учетных записей с выделенным отображаемым именем "настраиваемое поле"](media/operators/customfield_suggest_display.png)

После выбора предложения в строке формул отображается "настраиваемое поле", и данные извлекаются: 

> [!div class="mx-imgBorder"]  
> Строка формул ![Studio, в которой показано использование отображаемого имени "настраиваемое поле" для поля](media/operators/customfield_display.png)

Хотя это не рекомендуется, можно также использовать логическое имя для этого поля.  Это приведет к получению одних и тех же данных.  Обратите внимание, что ни одна кавычка не требуется, так как это имя не содержит пробелов или специальных символов:

> [!div class="mx-imgBorder"]  
> ![строке формул Studio, в которой показано использование логического имени cr5e3_customfield для поля](media/operators/customfield_logical.png)

В фоновом режиме поддерживается сопоставление между отображаемыми именами в формулах и базовыми логическими именами.  Поскольку логические имена должны использоваться для взаимодействия с источником данных, это сопоставление используется для автоматического преобразования из текущего отображаемого имени в логическое имя, которое отображается в сетевом трафике.  Это сопоставление также используется для преобразования обратно в логические имена, чтобы можно было переключиться на новые отображаемые имена, например если отображаемое имя изменяется или кто-либо другой язык редактирует приложение.

> [!NOTE] 
> При перемещении приложения между средами логические имена не переводятся.  Для Common Data Service имен системных сущностей и полей это не должно быть проблемой, так как логические имена согласованы между средами.  Но все настраиваемые поля, такие как **cra3a_customfield** в этом примере выше, могут иметь другой префикс среды (в данном случае**cra3a** ).  Отображаемые имена являются предпочтительными, так как они могут быть сопоставлены с отображаемыми именами в новой среде. 

## <a name="name-disambiguation"></a>Уточнение имени
Поскольку отображаемые имена не являются уникальными, одно и то же отображаемое имя может появляться несколько раз в одной и той же сущности.  В этом случае логическое имя будет добавлено в конец отображаемого имени в круглых скобках для одного или нескольких конфликтующих имен.  Основываясь на приведенном выше примере, если существовало второе поле с тем же отображаемым именем **настраиваемого поля** с логическим именем **cra3a_customfieldalt** то предложения будут показаны:

> [!div class="mx-imgBorder"]  
> ![строке формул Studio, в которой показано использование логического имени cr5e3_customfieldalt для устранения неоднозначности двух версий "настраиваемого поля"](media/operators/customfield_suggest_alt.png)

Строки устранения неоднозначности имен добавляются в других ситуациях, когда возникает конфликт имен, например имена сущностей, наборов параметров и других Common Data Service элементов. 

## <a name="disambiguation-operator"></a>Оператор устранения неоднозначности
Некоторые функции создают [области записей](../working-with-tables.md#record-scope) для доступа к полям таблицы при обработке каждой записи, например **Filter**, **AddColumns** и **Sum**.  Имена полей, добавленные с помощью области записи, переопределяют такие же имена из любого другого места в приложении.  В этом случае с помощью оператора устранения неоднозначности **@** можно по-прежнему получать доступ к значениям за пределами области записи.

* Для доступа к значениям из вложенных областей записей используйте оператор **@** , указав имя нужной таблицы в формате:<br>_Таблица_ **[@** _FieldName_ **]**
* Чтобы получить доступ к глобальным значениям, таким как источники данных, коллекции и переменные контекста, используйте шаблон **[@** _ObjectName_ **]** (без обозначения таблицы).

Дополнительные сведения и примеры см. в разделе [Области записей](../working-with-tables.md#record-scope).

