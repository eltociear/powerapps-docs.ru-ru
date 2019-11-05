---
title: Использование PowerApps Common Data Service тегов сущностей для портала | MicrosoftDocs
description: Сведения о тегах сущностей Common Data Service PowerApps, доступных на портале.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b6efc3e176602d366315b9b54b66593005051e55
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543259"
---
# <a name="powerapps-common-data-service-entity-tags"></a>Теги сущностей Common Data Service PowerApps

Теги сущностей PowerApps используются для загрузки и вывода данных PowerApps, а также для использования других служб инфраструктуры порталов PowerApps. Эти теги являются расширениями PowerApps для языка жидкости.

## <a name="chart"></a>Диаграммы

Добавляет диаграмму PowerApps на веб-страницу. Тег диаграммы можно добавить в поле Копировать на веб-странице или в поле источник веб-шаблона. Действия по добавлению диаграммы PowerApps на веб-страницу см. [в разделе Добавление диаграммы на веб-страницу на портале](../configure/add-chart.md).

```
{% chart id:"EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid:"00000000-0000-0000-00AA-000010001006" %}
```

### <a name="parameters"></a>Вход

С тегом диаграммы можно указать два параметра: идентификатор диаграммы и ViewID.

**Идентификатор диаграммы**

Идентификатор визуализации диаграммы. Это можно сделать, экспортировав диаграмму.

**viewId**

Идентификатор сущности при открытии в редакторе представления. 

## <a name="powerbi"></a>powerbi

Добавляет Power BI панели мониторинга и отчеты на страницах. Тег можно добавить в поле **Копировать** на веб-странице или в поле **источник** веб-шаблона. Действия по добавлению Power BI отчета или панели мониторинга на веб-страницу на портале см. в разделе [добавление Power BI отчета или панели мониторинга на веб-страницу на портале](../admin/add-powerbi-report.md).

> [!NOTE]
> Чтобы тег работал, необходимо [включить интеграцию Power BI](../admin/set-up-power-bi-integration.md) из центра администрирования порталов PowerApps. Если Power BI интеграция не включена, панель мониторинга или отчет отображаться не будут.

### <a name="parameters"></a>Вход

Тег powerbi принимает следующие параметры:

**путь**

Путь к Power BI отчету или панели мониторинга. Если Power BI отчет или панель мониторинга являются безопасными, необходимо указать тип проверки подлинности.

```
{% powerbi path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

**authentication_type**

Тип проверки подлинности, необходимый для Power BI отчета или панели мониторинга. Допустимые значения для этого параметра:

- **Anonymous**: позволяет внедрять отчеты о публикации в веб-Power BI. Тип проверки подлинности по умолчанию — Anonymous.

- **AAD**: позволяет совместно использовать безопасные Power BI отчеты и панели мониторинга для Power BI Azure Active Directory пользователей, прошедших проверку подлинности.

- **повербиембеддед**: позволяет предоставлять доступ к защищенным Power BI отчетам или панелям мониторинга внешним пользователям, у которых нет Power BI лицензий или настройки проверки подлинности Azure Active Directory. Дополнительные сведения о настройке службы Power BI Embedded см. в разделе [Включение службы Power BI Embedded](../admin/set-up-power-bi-integration.md#enable-power-bi-embedded-service). 

Добавляя отчет или панель мониторинга безопасного Power BI, убедитесь, что они используются совместно с порталом Azure Active Directory или Power BI Embedded служб. 

> [!NOTE]
> Значения параметра `authentication_type` не чувствительны к регистру.

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

Можно также отфильтровать отчет по одному или нескольким значениям. Для фильтрации отчета используется следующий синтаксис:

URL? Filter =**таблица**/**поле** EQ "**значение**"

Например, предположим, что необходимо отфильтровать отчет, чтобы увидеть данные для контакта с названием Берт волосы. Необходимо добавить URL-адрес следующим образом:

? фильтр = руководители-руководителей/Бертные волосы "

Полный код будет следующим:

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq 'Bert Hair'" %}
```

Дополнительные сведения о фильтрации отчета: [Фильтрация отчета с помощью параметров строки запроса в URL-адресе](https://docs.microsoft.com/power-bi/service-url-filters)

> [!NOTE]
> Анонимный отчет не поддерживает фильтрацию. 

Динамический путь можно также создать с помощью `capture ` переменной ликвидности, как показано ниже:

```
{% capture pbi_path %}https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq '{{user.id}}'{% endcapture %}
{% powerbi authentication_type:"AAD" path:pbi_path %}
```

Дополнительные сведения о переменной жидкости: [Теги переменных](variable-tags.md)

**тилеид**

Отображает указанную плитку панели мониторинга. Необходимо указать идентификатор плитки.

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/dashboards/00000000-0000-0000-0000-000000000001" tileid:"00000000-0000-0000-0000-000000000002" %}
```

**роли**

Роли, назначенные отчету Power BI. Этот параметр работает только в том случае, если для параметра **authentication_type** задано значение **повербиембеддед**.

Если вы определили роли в Power BI и назначили их отчетам, необходимо указать соответствующие роли в теге жидкостя **powerbi** . Роли позволяют фильтровать данные, отображаемые в отчете. Можно указать несколько ролей, разделенных запятыми. Дополнительные сведения об определении ролей в Power BI см. в разделе [безопасность на уровне строк (RLS) с Power BI](https://docs.microsoft.com/power-bi/service-admin-rls).

```
{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:"Region_East,Region_West" %}
```

Если вы назначили роль для Power BI отчета и не указали параметр **roles** в теге жидкости или не указали роль в параметре, отображается сообщение об ошибке.

> [!TIP]
> Если вы хотите использовать веб-роли, определенные на портале в качестве ролей Power BI, можно определить переменную и назначить ей веб-роли. Затем можно использовать определенную переменную в теге жидкости.
>
> Предположим, вы определили две веб-роли в качестве Region_East и Region_West на портале. Их можно объединить с помощью кода: `{% assign webroles = user.roles | join: ", " %}`
>
> В приведенном выше фрагменте кода `webroles` — это переменная, и в ней будут храниться веб-роли Region_East и Region_West.
>
> Используйте переменную `webroles`, как показано в теге жидкости:
>
> `{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:webroles%}`

## <a name="editable"></a>редактирования

Отображает заданный объект CMS-порталов PowerApps в качестве редактируемого на портале для пользователей с разрешением на редактирование содержимого для этого объекта. Изменяемые объекты включают страницы, [фрагменты](liquid-objects.md#snippets)и [веб-](liquid-objects.md#page) [ссылки](liquid-objects.md#weblinks).  

```
{% editable page 'adx_copy' type: 'html', title: 'Page Copy', escape: false, liquid: true %}

{% editable snippets Header type: 'html' %}

<!--

An editable web link set required a specific DOM structure, with

certain classes on the containing element, as demonstrated here.

-->

{% assign primary_nav = weblinks[Primary Navigation] %}

{% if primary_nav %}

<div {% if primary_nav.editable %}class=xrm-entity xrm-editable-adx_weblinkset{% endif %}>

<ul>

<!-- Render weblinks... -->

</ul>

{% editable primary_nav %}

</div>

{% endif %}
```

### <a name="parameters"></a>Вход

Первый параметр, предоставленный для изменения, является редактируемым объектом. Например, это может быть набор веб-ссылок, фрагменты или текущая страница. Необязательный второй параметр заключается в указании имени или ключа атрибута в объекте, который должен быть визуализирован и изменен. Это может быть имя атрибута сущности или имя фрагмента, например.

После этих начальных параметров тег поддерживает ряд необязательных именованных параметров.

**см**

Задает значение атрибута класса для корневого элемента, отображаемого этим тегом.

**параметры**

Значение по умолчанию, которое подготавливается к просмотру в случае, если изменяемый элемент не имеет значения.

**выполняет**

Логическое значение, указывающее, будет ли значение, отображаемое этим тегом, закодировано в формате HTML. По умолчанию это значение равно false.

**Liquid**

Логическое значение, указывающее, будет ли обрабатываться код шаблона жидкости в текстовом значении, отображаемом этим тегом. Это справедливо по умолчанию.

**тегами**

Имя контейнера HTML-тегов, которые будут подготавливаться к просмотру с помощью этого тега. По умолчанию этот тег будет отображать элементы div. Обычно рекомендуется выбрать тег div или span в качестве значения для этого параметра.

**Титуль**

Задает метку для этого изменяемого элемента в интерфейсе редактирования содержимого. Если значение не указано, будет автоматически создана понятная метка.

**Тип**

Строковое значение, указывающее тип отображаемого интерфейса правки для редактируемых текстовых значений. Допустимые значения для этого параметра: HTML или Text. по умолчанию используется HTML.

## <a name="entitylist"></a>ентитилист

Загружает указанный список сущностей по имени или ИДЕНТИФИКАТОРу. Доступ к свойствам списка сущностей можно получить с помощью [объекта ентитилист](liquid-objects.md#entitylist) , который будет доступен в блоке тегов. Чтобы отобразить фактические результирующие записи списка сущностей, используйте тег [ентитивиев](#entityview) в блоке.  

Если список сущностей загружен успешно, содержимое в блоке будет визуализировано. Если список сущностей не найден, содержимое блока не будет подготовлено к просмотру.

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```
По умолчанию объекту ентитилист будет присвоено имя переменной ентитилист. При необходимости можно указать другое имя переменной.

```
{% entitylist my_list = name:My Entity List %}

Loaded entity list {{ my_list.adx_name }}.

{% endentitylist %}
```

### <a name="parameters"></a>Вход

Укажите **только один** идентификатор, имя или ключ, чтобы выбрать список сущностей для загрузки.

**удостоверения**

Загружает список сущностей по идентификатору [GUID](https://en.wikipedia.org/wiki/Globally_unique_identifier) . Идентификатор должен быть строкой, которая может быть проанализирована как идентификатор GUID.  

```
{% entitylist id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

Как правило, строки GUID литерала не будут использоваться. Вместо этого идентификатор будет указан с помощью свойства GUID другой переменной.

```
{% entitylist id:page.adx_entitylist.id %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**безымян**

Загружает список сущностей по имени.

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**раздел**

Загружает список сущностей по ИДЕНТИФИКАТОРу **или** имени. Если указанное значение ключа может быть проанализировано как [идентификатор GUID](https://en.wikipedia.org/wiki/Globally_unique_identifier), список сущностей будет ЗАГРУЖЕН по идентификатору. В противном случае он будет загружен по имени.

```
<!-- key_variable can hold an ID or name -->

{% entitylist key:key_variable %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**код языка\_**

Код языка PowerApps, чтобы выбрать локализованные метки списка сущностей для загрузки. Если язык\_не указан, будет использоваться язык по умолчанию для подключения к PowerApps приложения портала.

```
{% entitylist name:"My Entity List", language_code:1033 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

## <a name="entityview"></a>ентитивиев

Загружает заданное представление PowerApps по имени или ИДЕНТИФИКАТОРу. Свойства представления ߝ Просмотр метаданных столбца, разбивка на страницы результатов и т. д. можно получить с помощью [объекта ентитивиев](liquid-objects.md#entityview) , который будет доступен в блоке тегов.  

Если представление загружено успешно, содержимое в блоке будет визуализировано. Если представление не найдено, содержимое блока не будет подготовлено к просмотру.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

По умолчанию объекту ентитивиев будет присвоено имя переменной ентитивиев. При необходимости можно указать другое имя переменной.

```
{% entityview my_view = logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ my_view.total_records }} total records.

{% endentityview %}
```

Если ентитивиев вложен в блок ентитилист, он будет наследовать конфигурацию по умолчанию (размер страницы результатов, параметры фильтра и т. д.) из списка сущностей. Если для ентитивиев не указаны параметры ID или Name представления, будет загружено представление по умолчанию из включающего ентитилист.

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview %}

Loaded default view of the entity list associated with the current page, with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

### <a name="parameters"></a>Вход

Укажите **идентификатор** **или** имя логического\_с именем, чтобы выбрать представление PowerApps для загрузки. Если ни один из них не указан и тег ентитивиев вложен в тег ентитилист, будет загружено представление по умолчанию включающего ентитилист.

**удостоверения**

Идентификатор должен быть строкой, которая может быть проанализирована как идентификатор GUID.

```
{% entityview id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity view {{ entityview.name }}.

{% endentityview %}
```

Как правило, строки GUID литерала не будут использоваться. Вместо этого идентификатор будет указан с помощью свойства GUID другой переменной.

```
{% entityview id:request.params.view %}

Loaded entity view {{ entityview.name }} using view query string request parameter.

{% endentityview %}
```

**имя логического\_**

Логическое имя сущности PowerApps для загружаемого представления. Необходимо использовать в сочетании с именем.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**безымян**

Имя PowerApps для загружаемого представления. Необходимо использовать в сочетании с именем логического\_.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**Фильтрация**

Указывает, следует ли фильтровать результаты представления по пользователю или по учетной записи. Должно иметь строковое значение "пользователь" или "учетная запись".

```
{% entityview id:request.params.view, filter:'user' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Распространенным вариантом использования является установка этого параметра на основе [запроса](liquid-objects.md#request).  

```
{% entityview id:request.params.view, filter:request.params.filter %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**метафилтер**

Указывает выражение фильтра метаданных списка сущностей, по которому фильтруются результаты представления. Этот параметр допустим только в том случае, если ентитивиев используется в сочетании с ентитилист. В большинстве случаев этот параметр задается на основе [запроса](liquid-objects.md#request).  

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview id:request.params.view, metafilter:request.params.mf %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

**порядок**

Задает выражение сортировки для упорядочивания результатов представления. Выражение сортировки может содержать один или несколько логических имен атрибутов сущности, за которыми следует направление сортировки либо ASC, либо DESC.

```
{% entityview id:request.params.view, order:'name ASC, createdon DESC' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Распространенным вариантом использования является установка этого параметра на основе [запроса](liquid-objects.md#request).  

```
{% entityview id:request.params.view, order:request.params.order %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**страниц**

Указывает загружаемую страницу результатов представления. Если этот параметр не указан, будет загружена первая страница результатов.

Этот параметр должен передавать либо целочисленное значение, либо строку, которая может быть проанализирована как целое число. Если для этого параметра указано значение, но значение равно null или не может быть проанализировано как целое число, будет загружена первая страница результатов.

```
{% entityview id:request.params.view, page:2 %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Распространенным вариантом использования является установка этого параметра на основе [запроса](liquid-objects.md#request).  

```
{% entityview id:request.params.view, page:request.params.page %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**Размер страницы\_**

Указывает количество результатов для загрузки для текущей страницы результатов. Если для этого параметра не указано значение и ентитивиев используется в блоке [ентитилист](#entitylist) , будет использоваться размер страницы списка сущностей. Если не находится в блоке ентитилист, будет использоваться значение по умолчанию, равное 10.

Этот параметр должен передавать либо целочисленное значение, либо строку, которая может быть проанализирована как целое число. Если для этого параметра указано значение, но значение равно null или не может быть проанализировано как целое число, будет использоваться размер страницы по умолчанию.

```
{% entityview id:request.params.view, page_size:20 %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Распространенным вариантом использования является установка этого параметра на основе [запроса](liquid-objects.md#request).  

```
{% entityview id:request.params.view, page_size:request.params.pagesize %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**осуществлять**

Задает выражение поиска, по которому фильтруются результаты представления. Простые выражения поиска ключевых слов будут фильтроваться, если атрибуты начинаются с ключевого слова. В выражение также можно включать подстановочные знаки \*.

```
{% entityview id:request.params.view, search:'John\*' %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

Распространенным вариантом использования является установка этого параметра на основе [запроса](liquid-objects.md#request), чтобы фильтр поиска мог быть установлен на основе вводимых пользователем данных.  
```
{% entityview id:request.params.view, search:request.params.search %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

**включить\_разрешения\_сущности**

Указывает, следует ли применять фильтрацию разрешений сущности к результатам представления. По умолчанию этот параметр имеет значение false. Если ентитивиев используется в блоке ентитилист, значение этого параметра будет унаследовано из конфигурации списка сущностей.

Этот параметр должен передаваться либо на [логическое](liquid-types.md#boolean) значение, либо в виде строки, которая может быть проанализирована в качестве логического значения (true, false). Если для этого параметра указано значение, но значение равно null или не может быть проанализировано в качестве логического значения, будет использовано значение по умолчанию false.  

```
{% entityview id:request.params.view, enable_entity_permissions:true %}

Loaded entity view with {{ entityview.total_records }} total records to which the user has read permission.

{% endentityview %}
```

**код языка\_**

Код языка PowerApps, позволяющий выбрать локализованные метки представления сущностей (метки заголовков столбцов и т. д.) для загрузки. Если язык\_не указан, будет использоваться язык по умолчанию для подключения к PowerApps приложения портала.

Если ентитивиев используется в блоке ентитилист, ентитивиев наследует свою конфигурацию кода языка из ентитилист.

```
{% entityview logical_name:'contact', name:"Active Contacts", language_code:1033 %}

Loaded entity view {{ entityview.name }}.

{% endentitylist %}
```

## <a name="searchindex"></a>сеарчиндекс

Выполняет запрос к индексу поиска на портале. Затем можно получить доступ к соответствующим результатам с помощью [сеарчиндекс](liquid-objects.md#searchindex) , который будет доступен в блоке тегов.  

```
{% searchindex query: 'support', page: params.page, page_size: 10 %}

{% if searchindex.results.size > 0 %}

<p>Found about {{ searchindex.approximate_total_hits }} matches:</p>

<ul>

{% for result in searchindex.results %}

<li>

<h3><a href={{ result.url | escape }}>{{ result.title | escape }}</a></h3>

<p>{{ result.fragment }}</p>

</li>

{% endfor %}

</ul>

{% else %}

<p>Your query returned no results.</p>

{% endif %}

{% endsearchindex %}
```

По умолчанию объекту индекса поиска будет присвоено имя переменной сеарчиндекс. При необходимости можно указать другое имя переменной.

```
{% searchindex liquid_search = query: 'support', page: params.page, page_size: 10 %}

{% if liquid_search.results.size > 0 %}

...

{% endif %}

{% endsearchindex %}
```

### <a name="parameters"></a>Вход

Тег сеарчиндекс принимает следующие параметры.

**Выбор**

Запрос, используемый для сопоставления результатов. Этот параметр предназначен для принятия указанной пользователем части запроса индекса (при наличии).

```
{% searchindex query: 'support' %}

...

{% endsearchindex %}
```

Распространенным вариантом использования является установка этого параметра на основе [запроса](liquid-objects.md#request).  

```
{% searchindex query: request.params.query %}

...

{% endsearchindex %}
```

Этот параметр поддерживает [синтаксис синтаксического анализатора запросов Lucene](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html).

**Фильтрация**

Дополнительный запрос, используемый для сопоставления результатов. Этот параметр предназначен для принятия результатов фильтра, заданных разработчиком, при необходимости.

```
{% searchindex query: request.params.query, filter: '+statecode:0' %}

...

{% endsearchindex %}
```

Этот параметр поддерживает [синтаксис синтаксического анализатора запросов Lucene](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html).  

> [!Note]     
> Различие между фильтром и запросом состоит в том, что хотя оба варианта будут принимать синтаксис синтаксического анализатора запросов Lucene, запрос будет более терпим отношению о том, как этот синтаксис анализируется ߝ, как ожидалось, что большинство конечных пользователей не будет знать о синтаксисе. Таким образом, в случае сбоя синтаксического анализа запроса в соответствии с этим синтаксисом весь запрос будет экранирован и отправлен как текст запроса. с другой стороны, фильтр будет анализироваться строго и возвращать ошибку в случае недопустимого синтаксиса.

**имена логических\_**

Логические имена сущностей PowerApps, к которым соответствующие результаты будут ограничены, в виде строки с разделителями-запятыми. Если не указано, будут возвращены все соответствующие сущности.

```
{% searchindex query: request.params.query, logical_names: 'kbarticle,incident' %}

...
>
{% endsearchindex %}
```
**страниц**

Возвращаемая страница результатов поиска. Если он не указан, возвращается первая страница (1).

```
{% searchindex query: request.params.query, page: 2 %}

...

{% endsearchindex %}
```

Распространенным вариантом использования является установка этого параметра на основе [запроса](liquid-objects.md#request).  

```
{% searchindex query: request.params.query, page: request.params.page %}

...

{% endsearchindex %}
```

**Размер страницы\_**

Размер возвращаемой страницы результатов. Если не указано, будет использоваться размер по умолчанию 10.

```
{% searchindex query: request.params.query, page_size: 20 %}

...

{% endsearchindex %}
```

## <a name="entityform"></a>ентитиформ

Полностью отображает настроенные в PowerApps формы сущностей по имени или ИДЕНТИФИКАТОРу.  

> [!Note]
> Тег ентитиформ доступен только для использования в содержимом, отображаемом в шаблоне страницы на основе  <em>[веб-шаблона](store-content-web-templates.md)</em>. Попытка использовать тег внутри шаблона страницы, основанного на перезаписи, не будет отображать ничего. Вы можете отобразить только один тег ентитиформ или веб-формы на странице. Теги ентитиформ или WebForms после первого не будут подготовлены к просмотру.       

`{% entityform name: 'My Entity Form' %}`

### <a name="parameters"></a>Вход

**безымян**

Имя формы сущности, которую вы хотите загрузить.

`{% entityform name:My Entity Form %}`

### <a name="webform"></a>**WebForm**

Полностью отображает настроенную в PowerApps веб-форму по имени или ИДЕНТИФИКАТОРу. Тег веб-формы можно использовать только в содержимом, отображаемом в шаблоне страницы на основе [веб-шаблона](store-content-web-templates.md) . Попытка использовать тег внутри шаблона страницы, основанного на перезаписи, не будет отображать ничего. Вы можете отобразить только один тег ентитиформ или веб-формы на странице. Теги ентитиформ или WebForms после первого не будут подготовлены к просмотру.                
`{% webform name: 'My Web Form' %}`

### <a name="parameters"></a>Вход

**безымян**

Имя веб-формы, которую вы хотите загрузить.

`{% webform name:My Web Form %}`

### <a name="see-also"></a>См. также

[Теги потока управления](control-flow-tags.md)<br>
[Теги итерации](iteration-tags.md)<br>
[Теги переменных](variable-tags.md)<br>
[Теги шаблона](template-tags.md)
