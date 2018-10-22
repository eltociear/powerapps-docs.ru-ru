---
title: Создание и изменение виртуальных сущностей с помощью Common Data Service для приложений | MicrosoftDocs
description: Инструкции по созданию виртуальных сущностей
ms.custom: ''
ms.date: 06/27/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: 44834893-0bf6-4a64-8f06-7583fe08330d
caps.latest.revision: 11
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-and-edit-virtual-entities-that-contain-data-from-an-external-data-source"></a>Создание и изменение виртуальных сущностей, содержащих данные из внешнего источника данных

Виртуальная сущность — это настраиваемая сущность в Common Data Service для приложений, которая имеет поля, содержащие данные из внешнего источника данных. Виртуальные сущности в вашем приложении выглядят для пользователей как обычные записи сущности, но содержат данные из внешней базы данных, например базы данных Azure SQL. Записи, основанные на виртуальных сущностях, доступны для всех клиентов, включая настраиваемые клиенты, разработанные с помощью веб-служб CDS для приложений.  
  
В прошлом чтобы интегрировать разрозненные источники данных требовалось создать соединитель, чтобы переместить данные, или разработать настраиваемый подключаемый модуль на стороне клиента или сервера. Однако с виртуальными сущностями можно подключиться напрямую к внешнему источнику данных во время выполнения, чтобы определенные данные из внешнего источника данных были доступны в среде без необходимости репликации данных.  

Виртуальные сущности состоят из трех основных компонентов: *поставщик данных*, запись *источника данных* и *виртуальная сущность*. Поставщик данных состоит из подключаемых модулей и сущность источника данных. Источник данных представляет собой запись сущности в CDS для приложений, которая включает метаданные, отражающие схему параметров подключения. Каждая виртуальная сущность ссылается на источник данных в определении сущности.  
  
CDS для приложений включает поставщика данных OData, который можно использовать для подключения к веб-службе OData v4, которая получает доступ к внешним данным. 
  
В качестве альтернативы разработчики могут создавать собственных поставщиков данных. Поставщики данных устанавливаются в среде в качестве решения. Дополнительные сведения: [Документация для разработчиков. Начало работы с виртуальными сущностями](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve)
  
 ![Диаграмма виртуальной сущности](media/virtual-entity-diagram.png "Диаграмма виртуальной сущности")  
  
<a name="benefits"></a> 
  
## <a name="virtual-entity-benefits"></a>Преимущества виртуальных сущностей  
  
- Разработчики могут реализовывать подключаемые модули для чтения внешних данных с помощью веб-служб CDS для приложений и средства регистрации подключаемых модулей .  
- Настройщики системы используют обозреватель решений PowerApps для конфигурирования записи источника данных и создания виртуальных сущностей, которые используются для доступа к внешним данным без написания кода.  
- Конечные пользователи работают с записями, созданными виртуальной сущностью, для просмотра данных в полях, сетках, результатах поиска, а также в отчетах и на панелях мониторинга на основе Fetch XML.  
  
<a name="AddDataSource"></a> 
  
## <a name="add-a-data-source-to-use-for-virtual-entities"></a>Добавление источника данных для использования для виртуальных сущностей 
 
 Разработчики могут создать настраиваемый подключаемый модуль для использования в качестве поставщика данных для виртуальной сущности. Кроме того, можно использовать предусмотренный поставщик данных OData v4. Дополнительные сведения: [Конфигурация, требования и рекомендации для поставщика данных OData v4](virtual-entity-odata-provider-requirements.md)  
  
1. Перейдите в раздел **[Параметры](../model-driven-apps/advanced-navigation.md#settings)** > **Администрирование** > **Источники данных виртуальных сущностей**.  
1. На панели инструментов действий выберите **Создать**.  
1. В диалоговом окне **Выберите поставщика данных** выберите одного из следующих поставщиков данных, затем выберите **ОК**.
 
    |Поставщик данных|Описание|
    |--|--|
    |*Настраиваемый поставщик данных*|Если был импортирован подключаемый модуль поставщика данных, этот поставщик данных будет отображаться здесь. Дополнительные сведения: [Документация для разработчиков. Начало работы с виртуальными сущностями](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve)|
    |**Поставщик данных OData v4**|CDS для приложений включает поставщика данных OData, который может использоваться с веб-службами OData v4. Дополнительные сведения: [Конфигурация, требования и рекомендации для поставщика данных OData v4](virtual-entity-odata-provider-requirements.md)|

  
### <a name="add-a-secured-field-to-a-data-source"></a>Добавление защищенного поля в источник данных

Поля для источника данных создаются таким же образом, как и для любой другой сущности. Для данных, которые зашифрованы или конфиденциальны, включите атрибут "Секрет источника данных" в настраиваемом поле источника данных. Например, чтобы защитить поле, которое содержит строку подключения базы данных. 

> [!NOTE]
> Атрибут "Секрет источника данных" доступен только для полей, добавленных в форму источника данных.

> [!div class="mx-imgBorder"] 
> ![Атрибут секрета источника данных](media/datasourcesecret.png)
  
<a name="createVirtualEntity"></a> 
  
## <a name="create-a-virtual-entity"></a>Создание виртуальной сущности
  
Виртуальная сущность создается точно так же, как и любая другая сущность в CDS для приложений, с добавлением нескольких дополнительных атрибутов, описанных здесь. Виртуальные сущности должны создаваться с помощью обозревателя решений.

> [!NOTE]
>  Хотя можно создать виртуальную сущность, выбрав значение **Нет** в качестве источника данных, чтобы получить данные, виртуальной сущности требуется источник данных. Дополнительные сведения: [Добавление источника данных для использования для виртуальных сущностей](#AddDataSource)

### <a name="open-solution-explorer"></a>Откройте обозреватель решений

Часть имени любой создаваемой виртуальной сущности — это префикс настройки. Это настраивается с использованием издателя решений для решения, в котором выполняется работа. Если важен префикс настройки, убедитесь, что вы работаете с неуправляемым решением, префикс настройки в котором — тот, который нужен для данной виртуальной сущности. Дополнительные сведения: [Изменение префикса издателя решения](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="create-a-virtual-entity"></a>Создание виртуальной сущности
  
1. В обозревателе решений создайте новую сущность. Для этого выберите **Сущности** в левой области переходов, затем выберите **Создать**.  
2. На вкладке **Общие сведения** раздела **Определение сущности** выберите **Виртуальная сущность**, затем в раскрывающемся списке **Источник данных** выберите требуемый источник данных.  

    > [!div class="mx-imgBorder"] 
    > ![Параметр виртуальной сущности в определении сущности](media/virtual-entity-click-option.png)  
  
1. В определении сущности заполните следующие обязательные поля.
  
    |Поле|Описание|
    |--|--|
    |**Внешнее имя**|Введите имя таблицы во внешнем источнике данных, с которым сопоставляется эта сущность.|
    |**Имя внешней коллекции**|Введите имя таблицы во множественном числе во внешнем источнике данных, с которым сопоставляется эта сущность.|
      
    Ниже приведен пример виртуальной сущности с названием *Фильм*, которая использует поставщика данных Azure Cosmos DB для получения доступа к файлам документов.  
      
    > [!div class="mx-imgBorder"] 
    > ![Определение виртуальной сущности с помощью поставщика данных Azure Cosmos DB](media/virtual-entity-definition.PNG)  
      
    > [!IMPORTANT]
    > С виртуальными сущностями недоступны некоторые возможности, такие как доступ к группы доступа, очереди и быстрое создание. Дополнительные сведения: [Замечания при использовании виртуальных сущностей](#considerations)  
      
    По мере необходимости заполните дополнительные обязательные и необязательные свойства, такие как отображаемое имя и имя во множественном числе. Дополнительные сведения об этих свойствах см. в разделе [Создание и изменение сущностей](create-edit-entities.md).  
  
1. Создание и добавление одного или нескольких полей для виртуальной сущности. В дополнение к стандартным свойствам полей, необходимым для создания настраиваемого поля, следующие необязательные свойства доступны для каждого настраиваемого поля, создаваемого для виртуальной сущности.

    |Поле|Описание|
    |--|--|
    |**Внешнее имя**|Обычно это уникальное имя для определения данных, которые требуется показывать в поле.|
    |**Имя внешнего типа**|Если создается поле типа OptionSet: данное свойство сопоставляется внешнему имени набора значений во внешнем сервисе для набора параметров.  Как правило, это может быть перечисление или класс со строковым значением. Имя внешнего типа можно использовать, если требуется полное имя.  Например, в качестве параметра *Имя типа* с OData, где параметры в запросе требуют полного имени, например [*Имя типа*].[*Значение*].|
    |**Внешнее значение**|Если создается поле типа OptionSet: данное свойство сопоставляется соответствующему значению во внешнем источнике данных для элемента набора параметров.  Это введенное значение используется для определения, какой элемент набора параметров должен отображаться в приложении.  |

    Заполните дополнительные свойства по мере необходимости. Дополнительные сведения об этих свойствах см. в разделе [Создание и изменение полей](create-edit-fields.md).  
  
1. Выберите **Сохранить и закрыть** на странице свойств **Поле**.  
1. На панели инструментов обозревателя решений выберите **Сохранить**.  
1. На панели инструментов обозревателя решений выберите **Опубликовать**.  
1. Закройте обозреватель решений.  

<a name="considerations"></a>
   
## <a name="considerations-when-you-use-virtual-entities"></a>Замечания при использовании виртуальных сущностей  

Виртуальные сущности имеют следующие ограничения.  
  
- Все виртуальные сущности доступны только для чтения.  
- Существующие сущности нельзя преобразовать в виртуальные сущности.  
- По умолчанию виртуальные сущности содержат только имя и поле идентификатора.  Никакие другие поля, управляемые системой, такие как состояние или дата создания/изменения, не поддерживаются.
- Виртуальные сущности не поддерживают настраиваемые поля с типами валюты, изображения и данных клиентов.
- Виртуальные сущности не поддерживают аудит.  
- Поля виртуальных сущностей нельзя использовать в свертках или вычисляемых полях.
- Виртуальная сущность не может иметь тип "Действие".  
- Многие функции, которые влияют на строки таблицы сущности, нельзя включить с виртуальными сущностями.  Примеры включают очереди, управление знаниями, соглашения SLA, обнаружение повторов, отслеживание изменений, возможность работы в автономном режиме Mobile Offline, безопасность полей, поиск с сортировкой по релевантности, порталы для решений веб-порталов Dynamics 365 и отношения N:N между виртуальными сущностями.  
- Виртуальные сущности принадлежат организации и не поддерживают концепции безопасности Common Data Service для приложений уровня строки. Рекомендуется реализовать собственную модель безопасности для внешнего источника данных.  
- При использовании виртуальных сущностей в расширенном поиске рекомендуется использовать один источник данных. Например, не поддерживается создание расширенного поиска, который в конечном счете создает связь между собственными данными Common Data Service для приложений и внешними данными виртуальной сущности.  
- Свойства метаданных поля, которые проверяются при обновлении, не будут применяться к виртуальным сущностям. Например, для поля "Целое число" в поле виртуальной сущности можно настроить, что минимальное значение равно нулю. Однако поскольку значение поступает из внешнего источника данных, запрос вернет значения, меньшие нуля, при извлечении из виртуальной сущности.  Свойство минимального значения не подразумевается в запросе.  Вам все равно потребуется фильтровать значения, которые больше 0, если это вам требуется.
- Виртуальные сущности не поддерживают отслеживание изменений и не могут быть синхронизированы с помощью функции CDS для приложений, такой как служба экспорта данных.
  
### <a name="see-also"></a>См. также  

[Требования и рекомендации для поставщика данных OData v4](virtual-entity-odata-provider-requirements.md)</br> 
[Создание и изменение сущностей](create-edit-entities.md)</br>
[Создание и изменение полей](create-edit-fields.md)