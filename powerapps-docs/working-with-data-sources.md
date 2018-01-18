---
title: "Общие сведения об источниках данных | Документация Майкрософт"
description: "Справочные сведения по работе с подключениями и источниками данных в Microsoft PowerApps."
services: 
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/08/2017
ms.author: gregli
ms.openlocfilehash: 0c8aa48d1e8d2b524d287b5a123117c764e22385
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2017
---
# <a name="understand-data-sources-in-powerapps"></a>Общие сведения об источниках данных в PowerApps
Большинство приложений PowerApps используют внешние сведения, хранящиеся в облачных службах, которые называются **источниками данных**. Типичный пример — это таблица в файле Excel, который хранится в OneDrive для бизнеса. Приложения получают доступ к источникам данных с помощью **подключений**.

В этой статье описаны различные типы источников данных, а также то, как работать с табличными источниками данных.

Вы можете легко создать приложение, выполняющее базовые операции чтения и записи в источнике данных. Но иногда требуется больший уровень контроля над передачей данных в приложение и из него.  В этой статье описываются функции **[Patch](functions/function-patch.md)**, **[DataSourceInfo](functions/function-datasourceinfo.md)**, **[Validate](functions/function-validate.md)** и  **[Errors](functions/function-errors.md)** , которые предоставляют дополнительные возможности управления.

## <a name="kinds-of-data-sources"></a>Типы источников данных
Источники данных можно подключить к облачной службе или они могут быть локальными для приложения.

### <a name="connected-data-sources"></a>Подключение источников данных
Самые распространенные источники данных — это **таблицы**, которые можно использовать для получения и хранения информации. **Подключения** к источникам данных можно использовать для чтения и записи данных в книгах Microsoft Excel, списках SharePoint, таблицах SQL и во многих ресурсах других форматов, которые могут храниться в облачных службах, таких как OneDrive для бизнеса, DropBox, SQL Server и другие.

Помимо таблиц существуют и другие источники данных, в том числе электронная почта, календари, Twitter и уведомления, но они не рассматриваются в данной статье.

### <a name="local-data-sources"></a>Локальные источники данных
С помощью элементов управления **[Коллекция](controls/control-gallery.md)**, **[Форма отображения](controls/control-form-detail.md)** и **[Форма редактирования](controls/control-form-detail.md)** можно крайне просто создать приложение, которое считывает и записывает данные из источника данных.  Чтобы начать работу, ознакомьтесь со статьей о [формах данных](working-with-forms.md).  

Эти элементы управления используются в PowerApps при запросе на создание приложения на основе данных. Приложение использует внутреннюю таблицу для хранения и обработки данных, поступающих из источника данных.

[Коллекции](working-with-data-sources.md#Collections) — это особый тип источника данных, который является локальным для приложения. Он не подключен к службе в облаке, поэтому данные невозможно использовать совместно на устройствах для одного или нескольких пользователей. Коллекции можно загрузить и сохранить локально.

### <a name="kinds-of-tables"></a>Типы таблиц
Внутренние таблицы приложения PowerApps представляют собой постоянные значения, так же, как число или строка представляет собой значение. Внутренние таблицы не хранятся, они просто находятся в памяти приложения. Нельзя напрямую изменять структуру и данные таблицы. Вместо этого вы можете создать новую таблицу по формуле, с помощью которой можно создать измененную копию исходной таблицы.

Внешние таблицы хранятся в источнике данных для последующего извлечения и совместного использования.  PowerApps предоставляет подключения для чтения и записи хранимых данных.  По подключению можно обращаться к нескольким таблицам данных.  Вы можете выбрать таблицы, требуемые для использования в приложении, каждая из которых станет отдельным *источником данных*.  

Дополнительные сведения о внутренних и внешних таблицах в облачной службе см. в статье [Общие сведения о таблицах и записях в PowerApps](working-with-tables.md).

## <a name="working-with-tables"></a>Работа с таблицами
Табличные источники данных можно использовать так же, как и внутреннюю таблицу PowerApps.  Так же как и внутренняя таблица, каждый источник данных имеет [записи](working-with-tables.md#records), [столбцы](working-with-tables.md#columns) и свойства, которые можно использовать в формулах. Кроме того:

* Источник данных имеет такие же имена столбцов и типы данных, что и в базовой таблице в подключении.
  
    **Примечание**. Для источников данных SharePoint и Excel, содержащих имена столбцов с пробелами, PowerApps заменит эти пробелы кодом **"\_x0020\_"**. Например, столбец **Имя столбца** из SharePoint или Excel будет отображаться как **Имя_x0020_столбца** в PowerApps при отображении в структуре данных или использовании в формуле.
* Источник данных загружается из службы автоматически при загрузке приложения.  Вы можете принудительно обновить данные с помощью функции **[Refresh](functions/function-refresh.md)**.
* Работая с приложением, пользователи могут создавать, изменять и удалять записи, а также передавать соответствующие изменения в базовую таблицу в службе.
  * Записи можно создавать с помощью функций **[Patch](functions/function-patch.md)** и **[Collect](functions/function-clear-collect-clearcollect.md)**.  
  * Записи можно изменять с помощью функций **[Patch](functions/function-patch.md)**, **[Update](functions/function-update-updateif.md)** и **[UpdateIf](functions/function-update-updateif.md)**.
  * Записи можно удалять с помощью функций **[Remove](functions/function-remove-removeif.md)** и **[RemoveIf](functions/function-remove-removeif.md)**.
  * Ошибки, возникающие при работе с источником данных, можно просмотреть с помощью функции **[Errors](functions/function-errors.md)**.
* Используя функции  **[DataSourceInfo](functions/function-datasourceinfo.md)**, **[Defaults](functions/function-defaults.md)** и **[Validate](functions/function-validate.md)**, можно получить сведения об источнике данных, которые позволяют оптимизировать взаимодействие с пользователем.

### <a name="creating-data-sources"></a>Создание источников данных
С помощью PowerApps невозможно создать подключенный источник данных или изменить его структуру. Источник данных должен существовать в службе. Например, чтобы создать таблицу в книге Excel, хранимой в OneDrive, сначала требуется создать книгу с помощью Excel Online в OneDrive. Затем следует подключить приложение к ней.  

Однако источники данных коллекции *можно* создавать и изменять внутри приложения. Но такие источники данных являются временными.

### <a name="display-one-or-more-records"></a>Отображение одной или нескольких записей
![](media/working-with-data-sources/reading-from-a-datasource.png) На схеме выше показана процедура передачи данных, когда приложение считывает сведения в источнике данных.

* Данные хранятся и совместно используются в службах хранения (в этом случае список SharePoint сайта Office 365).
* За счет подключения приложение получает доступ к этим сведениям.  Подключение служит для аутентификации пользователя с последующим получением доступа к данным.
* При запуске приложения или использовании функции **[Refresh](functions/function-refresh.md)** сведения извлекаются из подключения в источник данных в приложении для локального использования.
* Формулы используются для чтения сведений и их представления в отображаемых элементах управления. Чтобы отобразить записи источника данных, используйте коллекцию на экране и запишите свойство **[Items](controls/properties-core.md)** в источник данных: **Gallery.Items = DataSource**.  Вы связываете элементы управления в коллекции с ней, используя свойство элементов управления **[Default](controls/properties-core.md)**.  
* Источник данных также является таблицей.  Так что вы можете использовать функции **[Filter](functions/function-filter-lookup.md)**, **[Sort](functions/function-sort.md)**, **[AddColumns](functions/function-table-shaping.md)** и другие для доработки и расширения источника данных, прежде чем использовать его.  Вы также можете использовать функции **[Lookup](functions/function-filter-lookup.md)**, **[First](functions/function-first-last.md)**, **[Last](functions/function-first-last.md)** и другие для работы с отдельными записями.

### <a name="modify-a-record"></a>Изменение записи
В предыдущем разделе вы узнали, как выполнять чтение источника данных.  Обратите внимание, что стрелки на приведенной выше схеме односторонние.  Изменения источника данных не передаются с применением тех же формул, что и для получения данных.  Вместо этого используются новые формулы.  Часто для редактирования и поиска записей используются разные экраны, особенно на мобильных устройствах.

Обратите внимание, что можно изменить имеющуюся запись источника данных, которая изначально находилась в нем.  Запись могла использоваться в коллекции, [переменной контекста](working-with-variables.md#create-a-context-variable) и во множестве формул, но ее происхождение должно четко прослеживаться до источника данных.  Это важно, так как вместе с записью передается и уникально определяющая ее информация, которая гарантирует, что вы изменяете правильную запись.    

![](media/working-with-data-sources/writing-to-a-datasource.png) На схеме выше показана процедура передачи данных для обновления источника данных.

* Элемент управления **[Форма изменения](controls/control-form-detail.md)**  предоставляет контейнер для карт ввода, которые состоят из элементов управления пользовательского ввода, таких как поля ввода текста или ползунок.  Свойства **[DataSource](controls/control-form-detail.md)** и **[Item](controls/control-form-detail.md)**  определяют запись, которую следует изменить.
* Каждая карта ввода имеет свойство **[Default](controls/properties-core.md)**, которое обычно задается для поля записи **ThisItem** формы.  Элементы управления карты ввода принимают входные значения из свойства **[Default](controls/properties-core.md)**.  Обычно это не нужно менять.
* Каждая карта ввода предоставляет свойство **[Update](controls/control-card.md)**.  Это свойство сопоставляет ввод пользователя с конкретным полем записи для обратной записи в источник данных.  Обычно это не нужно менять.
* С помощью элемента управления "Кнопка" или "Изображение" на экране пользователь может сохранить изменения в записи.  Для этого формула **[OnSelect](controls/properties-core.md)** элемента управления вызывает функцию **[SubmitForm](functions/function-form.md)**.  **[SubmitForm](functions/function-form.md)** считывает все свойства **[Update](controls/control-card.md)** карт и использует этот процесс для обратной записи в источник данных.
* Иногда будут возникать проблемы.  Сетевое подключение может отключиться или проверку может выполнять служба, неизвестная приложению.  Свойства **Error** и **[ErrorKind](controls/control-form-detail.md)** элемента управления "Форма" предоставляют эти данные для отображения пользователю.  

Для более детализированного контроля над процессом можно также использовать функции **[Patch](functions/function-patch.md)** и **[Errors](functions/function-errors.md)**.  Элемент управления **[Форма редактирования](controls/control-form-detail.md)** предоставляет свойство **[Updates](controls/control-form-detail.md)** , позволяющее прочитать значения полей в форме.  Это свойство можно также использовать для вызова настраиваемого соединителя для подключения, чтобы полностью обойти функции **Patch** и **SubmitForm**.

### <a name="validation"></a>Проверка
Перед изменением записи приложение должно проверить его допустимость.  Это происходит по двум причинам:

* *Немедленный отзыв для пользователя.*  Лучше всего устранять проблему в момент ее возникновения, так сказать "по горячим следам".  Текст, выделенный красным цветом, может появиться при каждом касании или нажатии клавиши. По этому тексту можно понять, что при вводе произошла проблема.
* *Меньше сетевого трафика и меньше задержка пользователя.*  Чем больше обнаружено проблем в приложении, тем меньше нужно выполнять действий по сети для обнаружения и устранения проблем.  Каждое взаимодействие требует времени, в течение которого пользователь должен ждать, прежде чем продолжить работу.

В PowerApps предусмотрено два средства проверки:

* В источнике данных доступны сведения о допустимости.  Например, числа могут иметь минимальные и максимальные значения, а также может потребоваться одна или несколько записей.  Доступ к этой информации можно получить с помощью функции **[DataSourceInfo](functions/function-datasourceinfo.md)**.  
* Функция **[Validate](functions/function-validate.md)** использует эти же сведения для проверки значения одного столбца или всей записи.

### <a name="error-handling"></a>Обработка ошибок
Вы проверили запись. Отлично.  Самое время обновить ее с помощью функции **[Patch](functions/function-patch.md)**.

Но, увы, и на этом этапе могут возникнуть проблемы.  Сеть отключена, произошел сбой проверки в службе или у пользователя нет соответствующих разрешений. И это только некоторые из возможных ошибок в приложении.  Приложение должно соответствующим образом реагировать на ошибку, а также предоставлять пользователю отзыв и средства устранения проблемы.  

При возникновении ошибок с источником данных приложение автоматически записывает сведения об ошибках и делает их доступным с помощью функции **[Errors](functions/function-errors.md)**.  Ошибки связаны с проблемными записями.  Если пользователь может устранить проблему, например проблему с проверкой, он может повторно отправить запись и сведения об ошибках будут удалены.

Если ошибка возникает при создании записи с помощью функции **[Patch](functions/function-patch.md)** или **[Collect](functions/function-clear-collect-clearcollect.md)**, запись, с которой можно было бы связать ошибку, отсутствует.  В этом случае функция **[Patch](functions/function-patch.md)** вернет значение *blank*, которое может использоваться в качестве аргумента записи в функции **[Errors](functions/function-errors.md)**.  Ошибки при создании удаляются со следующей операцией.

Функция **[Errors](functions/function-errors.md)** возвращает таблицу сведений об ошибках.  Это могут быть сведения о столбце, если ошибку можно отнести к определенному столбцу.  Используйте сообщения об ошибках на уровне столбца в элементах управления "Метка", которые находятся возле столбца на экране редактирования.  Используйте сообщения об ошибках на уровне записей, где **столбец** в таблице ошибок является *пустым*, возле кнопки **Сохранить** для всей записи.  

### <a name="working-with-large-data-sources"></a>Работа с большими источниками данных
При создании отчетов из больших источников данных (возможно, миллионы записей) нужно максимально сократить объем сетевого трафика. Предположим, вам нужно сообщить обо всех пользователях, у которых в качестве свойства StatusCode указано Platinum в Нью-Йорке, а также о том, что в таблице "Клиенты" содержатся миллионы записей.

Вам **не** нужно переносить всех этих пользователей в приложение, а затем выбирать только нужных. Вам нужно, чтобы пользователи были выбраны в облачной службе, в которой хранится таблица, а по сети отправлялись только выбранные записи.

Многие (но не все) функции, которые можно использовать для выбора записей, можно *делегировать*. Это значит, что они выполняются в облачной службе. Дополнительные сведения о делегировании см. в [этой статье](delegation-overview.md).

## <a name="collections"></a>Коллекции
Коллекции — это особый тип источника данных,  который является локальным для приложения. Он не подключен к службе в облаке, поэтому данные невозможно использовать совместно на устройствах для одного или нескольких пользователей.  Они действуют так же, как и любые другие источники данных, за некоторыми исключениями:

* Коллекции можно создавать динамически с помощью функции **[Collect](functions/function-clear-collect-clearcollect.md)**.  Их не нужно устанавливать заранее, как источники данных на основе подключения.
* Столбцы коллекции можно изменить в любое время, используя функцию **[Collect](functions/function-clear-collect-clearcollect.md)**.
* В коллекциях можно использовать повторяющиеся записи.  В коллекции может существовать несколько копий одной записи.  Функции, такие как **[Remove](functions/function-remove-removeif.md)**, сработают при первом обнаруженном совпадении, если не указан аргумент **All**.
* С помощью функций **[SaveData](functions/function-savedata-loaddata.md)** и **[LoadData](functions/function-savedata-loaddata.md)** можно сохранить и перезагрузить копию коллекции.  Сведения хранятся в безопасном месте, к которому не могут получить доступ другие пользователи, приложения или устройства.
* С помощью элементов управления **[Экспорт](controls/control-export-import.md)** и **[Импорт](controls/control-export-import.md)**  можно сохранить и перезагрузить копию коллекции в файл, с которым пользователь может взаимодействовать.  

Дополнительные сведения о работе с коллекцией в качестве источника данных см. в статье о [создании и обновлении коллекции](create-update-collection.md).

Коллекции обычно используются для хранения сведений об общем состоянии приложения.  Дополнительные сведения о возможностях управления состоянием см. в статье о [работе с переменными](working-with-variables.md).
