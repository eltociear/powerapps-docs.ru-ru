---
title: Функция Concurrent | Документация Майкрософт
description: Справочные сведения, включая синтаксис, для функции Concurrent в PowerApps
author: gregli-msft
ms.service: powerapps
ms.topic: reference
ms.component: canvas
ms.date: 06/26/2018
ms.author: gregli
ms.openlocfilehash: 0c885322402d8afcd8391fb7eb3904d188129ff0
ms.sourcegitcommit: d68432b9e9b800c50c5e7fd0be6691e51fd725c6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874141"
---
# <a name="concurrent-function-in-powerapps"></a>Функция Concurrent в PowerApps
Оценивает несколько формул одновременно.

## <a name="description"></a>Описание
Функция **Concurrent** вычисляет несколько формул одновременно. Обычно несколько формул вычисляются последовательно путем их объединения в цепочку с помощью операторов [**;**](operators.md) (или [**;;**](operators.md)). Когда приложение выполняет операции одновременно, пользователи тратят меньше времени на ожидание результата.

В свойстве [**OnStart**](../controls/control-screen.md) в приложении используйте функцию **Concurrent**, чтобы повысить производительность при загрузке данных. Если вызов данных не начинается до завершения предыдущего вызова, время ожидания в приложении будет суммой времени выполнения всех запросов по очереди. Если вызовы данных запускаются одновременно, временем ожидания будет время выполнения самого долгого запроса. Веб-браузеры часто повышают производительность, одновременно выполняя операции с данными.

Невозможно предсказать порядок, в котором формулы в функции **Concurrent** начинают и завершают вычисление. Формулы в функции **Concurrent** не должны содержать зависимости от других формул в той же функции **Concurrent**. В противном случае в PowerApps возникнет ошибка. Вы можете спокойно создавать зависимости от формул за пределами функции **Concurrent**, поскольку они будут выполнены до запуска функции **Concurrent**. Формулы после функции **Concurrent** могут иметь зависимости от формул внутри функции, поскольку они будут выполнены до того, как функция **Concurrent** завершится и перейдет к следующей формуле в цепочке (если вы используете оператор **;** или **;;**). Остерегайтесь незаметных зависимостей от порядка, если вызываете функции или методы службы с побочными эффектами.

Вы можете объединять формулы в цепочку с помощью оператора **;** (или **;**) в аргументе для функции **Concurrent**. Например, **Concurrent( Set( a, 1 ); Set( b, a+1 ), Set( x, 2 ); Set( y, x+2 ) )** вычисляет **Set( a, 1 ); Set( b, a+1 )** одновременно с **Set( x, 2 ); Set( y, x+2 )**. В этом случае зависимости в формулах допускаются: **a** устанавливается до **b**, а **x** устанавливается до **y**.

В зависимости от устройства или браузера, в котором выполняется приложение, только некоторые формулы могут вычисляться одновременно. Функция **Concurrent** использует доступные возможности и не завершится, пока не будут вычислены все формулы.

Если вы включите **Управление ошибками на уровне формул** (в дополнительных параметрах), вернется первая ошибка, возникшая в порядке аргументов в функции **Concurrent**; в противном случае возвращается *пустая строка*. Если все формулы выполняются успешно, возвращается *true*. В случае сбоя одной формулы она останавливается, а остальные вычисляются дальше.

Функцию **Concurrent** можно использовать только в [формулах поведения](../working-with-formulas-in-depth.md).

## <a name="syntax"></a>Синтаксис
**Concurrent**( *Формула1*, *Формула2* [, ...] )

* *Формулы* — обязательный параметр. Формулы для одновременного вычисления. Необходимо указать по крайней мере две формулы.

## <a name="examples"></a>Примеры

#### <a name="loading-data-faster"></a>Ускоренная загрузка данных

1. Создайте приложение и добавьте четыре источника данных из службы Common Data Service для приложений, SQL Server или SharePoint. 

    В этом примере используется четыре таблицы из [образца базы данных Adventure Works для SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal). После создания базы данных подключитесь к ней из PowerApps, используя полное имя сервера (например, srvname.database.windows.net):

    ![Подключение к базе данных Adventure Works в Azure](media/function-concurrent/connect-database.png)

2. Добавьте элемент управления **[Кнопка](../controls/control-button.md)** и задайте следующую формулу в качестве значения свойства **OnSelect**:

    **ClearCollect( Product, '[SalesLT].[Product]' );<br> ClearCollect( Customer, '[SalesLT].[Customer]' );<br> ClearCollect( SalesOrderDetail, '[SalesLT].[SalesOrderDetail]' );<br> ClearCollect( SalesOrderHeader, '[SalesLT].[SalesOrderHeader]' )**

3. В [Microsoft Edge](https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide/network) или [Google Chrome](https://developers.google.com/web/tools/chrome-devtools/network-performance/) включите средства разработчика для отслеживания сетевого трафика во время работы приложения.

1. (необязательно) Включите регулирование сети, чтобы подчеркнуть результат этого сравнения.

4. Удерживая нажатой клавишу ALT, нажмите кнопку и следите за сетевым трафиком.

    Средства показывают четыре запроса, которые выполняются последовательно, как в этом примере.  Фактическое время не показано, так как оно зависит от многих факторов.  На диаграмме видно, что каждый вызов начинается после завершения предыдущего:

    ![Временная диаграмма четырех сетевых запросов, каждый из которых начинается после завершения предыдущего, увеличивая общий промежуток времени](media/function-concurrent/chained-network.png)

5. Сохраните, закройте и повторно откройте приложение.

    PowerApps кэширует данные, поэтому, если вы снова нажмете на кнопку, это не обязательно приведет к четырем новым запросам. Каждый раз, когда вы собираетесь протестировать производительность, закройте и снова откройте приложение. Если вы включили функцию регулирования в сети, стоит отключить ее до выполнения следующего теста.

1. Добавьте второй элемент управления **[Кнопка](../controls/control-button.md)** и задайте следующую формулу в качестве значения свойства **OnSelect**:

    **Concurrent(<br> &nbsp;&nbsp;&nbsp;&nbsp;ClearCollect( Product, '[SalesLT].[Product]' ),<br> &nbsp;&nbsp;&nbsp;&nbsp;ClearCollect( Customer, '[SalesLT].[Customer]' ),<br> &nbsp;&nbsp;&nbsp;&nbsp;ClearCollect( SalesOrderDetail, '[SalesLT].[SalesOrderDetail]' ),<br> &nbsp;&nbsp;&nbsp;&nbsp;ClearCollect( SalesOrderHeader, '[SalesLT].[SalesOrderHeader]' )<br> )**

    Обратите внимание, что вы добавили те же вызовы **ClearCollect** к первой кнопке, но на этот раз с функцией **Concurrent** и разделением запятыми.

2. Снимите флажок в сетевом мониторе в браузере.

1. Если вы использовали регулирования сети, включите его снова.

3. Удерживая нажатой клавишу ALT, нажмите вторую кнопку и следите за сетевым трафиком.

    Средства показывают четыре запроса, которые выполняются одновременно, как в этом примере.  Фактическое время снова не показано, так как оно зависит от многих факторов.  На диаграмме видно, что все вызовы начинаются одновременно и не ожидают завершения предыдущего:

    ![Временной график четырех сетевых запросов, выполняющихся одновременно, приблизительно в два раза быстрее](media/function-concurrent/concurrent-network.png)

    В диаграммах используется одна и та же шкала. С помощью функции **Concurrent** вам удалось в два раза сократить время выполнения этих операций. 

5. Сохраните, закройте и повторно откройте приложение.

#### <a name="race-condition"></a>Состояние гонки

1. Добавьте подключение к службе [Microsoft Translator](../connections/connection-microsoft-translator.md) в приложение.

2. Добавьте элемент управления [**Ввод текста**](../controls/control-text-input.md) и переименуйте его в **TextInput1**, если у него другое имя.

3. Добавьте элемент управления **Кнопка** и задайте следующую формулу в качестве значения свойства **OnSelect**:

    **Set( StartTime, Value(Now()) );<br> Concurrent(<br> &nbsp;&nbsp;&nbsp;&nbsp;Set(FRTrans, MicrosoftTranslator.Translate(TextInput1.Text,"fr")); Set(FRTransTime, Value(Now()) ),<br> &nbsp;&nbsp;&nbsp;&nbsp;Set(DETrans, MicrosoftTranslator.Translate(TextInput1.Text,"de")); Set(DETransTime, Value(Now()) )<br> ); <br> Collect( <br> &nbsp;&nbsp;&nbsp;&nbsp;Results, <br> &nbsp;&nbsp;&nbsp;&nbsp;{<br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Input: TextInput1.Text, <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;French: FRTrans, FrenchTime: FRTransTime-StartTime,<br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;German: DETrans, GermanTime: DETransTime-StartTime,<br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;FrenchFaster: FRTransTime < DETransTime <br> &nbsp;&nbsp;&nbsp;&nbsp;}<br> )**

4. Добавьте элемент управления [**Таблица данных**](../controls/control-data-table.md) и укажите для свойства **Items** значение **Результаты**.

1. На вкладке **Свойства** на правой панели выберите **Результаты**, чтобы открыть панель **Данные**.

1. В списке полей установите флажок для каждого поля, которое должно отображаться в таблице данных.

1. (необязательно) Перетащите поле **Input** в верхнюю часть списка, а поле **FrenchFaster** — в нижнюю.

    ![Список полей в коллекции результатов](media/function-concurrent/field-list.png) 

6. В элементе управления **Ввод текста** введите или вставьте фразу для перевода.

7. Удерживая нажатой клавишу ALT, несколько раз нажмите на кнопку, чтобы заполнить таблицу.

    Время указывается в миллисекундах.
  
    ![Отображение таблицы данных с результатам перевода строки "Hello World" на французский и немецкий. Иногда перевод на французский выполняется быстрее, чем на немецкий, а иногда наоборот.](media/function-concurrent/race-condition.png) 

    В некоторых случаях перевод на французский выполняется быстрее, чем на немецкий, и наоборот. Обе операции перевода начинаются одновременно, но одна возвращается раньше другой по нескольким причинам, включая задержки сети и обработку на сервере.

    [Состояние гонки](https://en.wikipedia.org/wiki/Race_condition) возникает в случае, если приложение зависит от того, что один перевод завершится быстрее. К счастью, PowerApps отмечает большинство зависимостей от времени, которые может обнаружить.