---
title: Использование тегов сущности Common Data Service Power Apps для портала | Документация Майкрософт
description: Сведения о тегах сущности Common Data Service Power Apps, доступных на портале.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/28/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 83247403a482f7ce980f83a5813be2fd158e1be0
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2020
ms.locfileid: "3108689"
---
# <a name="power-apps-common-data-service-entity-tags"></a>Теги сущности Common Data Service Power Apps

Теги сущностей Power Apps используются для загрузки и отображения данных Power Apps или использования других служб платформы порталов Power Apps. Эти теги являются специфичными для Power Apps расширениями языка Liquid.

## <a name="chart"></a>Диаграмма

Добавляет диаграммы Power Apps на веб-страницу. Тег "chart" можно добавить в поле "Копия" на веб-странице или в поле "Источник" на веб-шаблоне. Шаги для добавления диаграммы Power Apps на веб-страницу см. в разделе [Добавление диаграммы на веб-страницу на портале](../configure/add-chart.md).

```
{% chart id:"EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid:"00000000-0000-0000-00AA-000010001006" %}
```

### <a name="parameters"></a>Параметры

С тегом chart должны указываться два параметра: chart id and viewid.

**chart id**

ИД визуализации диаграммы. Его можно получить, экспортировав диаграмму.

**viewid**

Идентификатор сущности при открытии в редакторе представления. 

## <a name="powerbi"></a>powerbi

Добавляет панели мониторинга и отчеты Power BI на страницы. Тег можно добавить в поле **Копия** на веб-странице или в поле **Источник** в веб-шаблоне. Шаги для добавления отчета или панели мониторинга Power BI на веб-страницу портала см. в разделе [Добавление отчета или панели мониторинга Power BI](../admin/add-powerbi-report.md) на веб-страницу портала.

> [!NOTE]
> Чтобы тег работал, необходимо [включить интеграцию Power BI](../admin/set-up-power-bi-integration.md) в центре администрирования порталов Power Apps. Если интеграция Power BI не включена, панель мониторинга или отчет не будет отображаться.

### <a name="parameters"></a>Параметры

Тег powerbi принимает следующие параметры:

**path**

Путь к отчету или панели мониторинга Power BI. Если отчет или панель мониторинга Power BI безопасна, необходимо указать тип проверки подлинности.

```
{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

**authentication_type**

Типа проверки подлинности, необходимый для отчета или панели мониторинга Power BI. Допустимые значения для этого параметра:

- **Анонимный**: позволяет внедрять публикацию в отчеты Power BI. Тип проверки подлинности по умолчанию — Анонимный. При использовании типа аутентификации "Анонимно", вы должны получить URL-адрес отчета Power BI, как описано в: [Публикация в Интернете из Power BI](https://docs.microsoft.com/power-bi/service-publish-to-web)

- **AAD**: Позволяет передать безопасные отчеты или панели мониторинга Power BI удостоверенным пользователям Power BI Azure Active Directory.

- **powerbiembedded**: позволяет предоставлять общий доступ к безопасным отчетам или панелям мониторинга Power BI внешним пользователям, не имеющим лицензии Power BI или настройки проверки подлинности Azure Active Directory. Сведения об настройке службы Power BI Embedded см. в разделе [Включение службы Power BI Embedded](../admin/set-up-power-bi-integration.md#enable-power-bi-embedded-service). 

При добавлении безопасного отчета или панели мониторинга Power BI убедитесь, что к ней предоставлен общий доступ для Azure Active Directory или служб Power BI Embedded портала. 

> [!NOTE]
> Значения параметра `authentication_type` не учитывают регистр.

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

Можно также фильтровать отчет для одному или нескольким значениям. Синтаксис для фильтрации отчета следующий:

URL?filter=**Таблица**/**Поле** eq '**значение**'

Например, допустим, требуется отфильтровать отчет, чтобы просмотреть данные для контакта с именем Bert Hair. Необходимо добавить URL-адрес к следующему:

?filter=Executives/Executive eq 'Bert Hair'

Полный код будет следующий:

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq 'Bert Hair'" %}
```

Дополнительные сведения о фильтрации отчета: [Фильтрация отчета с использованием параметров строки запроса в URL-адресе](https://docs.microsoft.com/power-bi/service-url-filters)

> [!NOTE]
> Анонимный отчет не поддерживает фильтрацию. 

Также можно создать динамический путь с использованием переменной Liquid `capture `, как показано ниже:

```
{% capture pbi_path %}https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq '{{user.id}}'{% endcapture %}
{% powerbi authentication_type:"AAD" path:pbi_path %}
```

Дополнительные сведения о переменной Liquid: [Переменные теги](variable-tags.md)

**tileid**

Отображает определенную плитку панели мониторинга. Необходимо предоставить ИД плитки.

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/dashboards/00000000-0000-0000-0000-000000000001" tileid:"00000000-0000-0000-0000-000000000002" %}
```

**роли**

Роли, назначенные отчету Power BI. Этот параметр работает только когда параметр **authentication_type** настраивается на **powerbiembedded**.

Если вы определили роли в Power BI и назначили их отчетам, необходимо определить соответствующие роли в теге Liquid **powerbi**. Роли позволяют фильтровать данные, которые должны отображаться в отчете. Можно выбрать несколько ролей разделены запятой. Дополнительные сведения по этому определение ролей в Power BI, см. [Безопасность на уровне строки (RLS) с Power BI](https://docs.microsoft.com/power-bi/service-admin-rls).

```
{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:"Region_East,Region_West" %}
```

Если роль назначали отчету Power BI, и не указали параметр **роли** в теге Liquid или не указан роль в параметре, то отображается ошибка.

> [!TIP]
> Если требуется использовать роли сети определенные в вашем портале как роли Power BI, вы можете указать переменной и назначить роли сети ей. После этого можно использовать определенную переменную в теге Liquid.
>
> Предположим, вы определять 2 роли сети как Region_East и Region_West в вашем портале. Вы можете присоединиться к ним с помощью кода: `{% assign webroles = user.roles | join: ", " %}`
>
> В вышеуказанном фрагменте кода `webroles` это переменная и роли Region_East сети и Region_West будут храниться и в ней.
>
> Используйте переменную `webroles` следующим образом в теге Liquid:
>
> `{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:webroles%}`

## <a name="editable"></a>editable

Отображает указанный объект CMS порталов Power Apps как редактируемый на портале для пользователей с разрешением изменения содержимого для этого объекта. Доступные для редактирования объекты включают [page](liquid-objects.md#page), [snippets](liquid-objects.md#snippets) и [weblinks](liquid-objects.md#weblinks).  

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

### <a name="parameters"></a>Параметры

Первый параметр, передаваемый в editable, — это редактируемый объект. Например, это может быть набор веб-ссылок, фрагменты или текущая страница. Необязательный второй параметр указывает имя или ключ атрибута в этом объекте, который требуется отобразить и отредактировать. Например, это может быть имя атрибута сущности или имя фрагмента.

После этих исходных параметров тег поддерживает несколько необязательных именованных параметров.

**class**

Указывает значение атрибута class для корневого элемента, представляемого этим тегом.

**default**

Значение по умолчанию, отображаемое в случае, когда редактируемый элемента не имеет значения.

**escape**

Логического значение, указывающее, будет ли для значения, отображаемого этим тегом, использоваться HTML-кодирование. Значение по умолчанию: false.

**liquid**

Логическое значение, указывающее, будет ли обрабатываться какой-либо код шаблона Liquid, имеющийся в текстовом значении, отображаемом этим тегом. Значение по умолчанию: true.

**tag**

Имя контейнера тегов HTML, который будет отображаться этим тегом. По умолчанию этот тег отображает элементы div. Обычно рекомендуется в качестве значения этого параметра выбирать между div и span.

**title**

Указывает подпись для данного редактируемого элемента в интерфейсе редактирования содержимого. Если ничего не указано, понятная подпись будет создана автоматически.

**type**

Строковое значение, указывающее тип интерфейса редактирования, который предоставляется для редактируемых текстовых значений. Допустимые значения для этого параметра: html или text. Значение по умолчанию: html.

## <a name="entitylist"></a>entitylist

Загружает указанный список сущностей по имени или идентификатору. Доступ к свойствам списка сущностей можно затем получить с помощью [объекта entitylist](liquid-objects.md#entitylist), который будет доступен в блоке тега. Для отображения фактических записей результата для списка сущностей используйте тег [entityview](#entityview) в блоке.  

Если список сущностей загружен успешно, отображается содержимое внутри блока. Если список сущностей не найден, содержимое блока не отображается.

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```
По умолчанию объекту entitylist задается имя переменной entitylist. Если требуется, может быть указано другое имя переменной.

```
{% entitylist my_list = name:My Entity List %}

Loaded entity list {{ my_list.adx_name }}.

{% endentitylist %}
```

### <a name="parameters"></a>Параметры

Для выбора загружаемого списка сущностей укажите **только один** из параметров id, name или key.

**id**

Загружает список сущностей по идентификатору [GUID](https://en.wikipedia.org/wiki/Globally_unique_identifier). id должен быть строкой, которую можно анализировать как GUID.  

```
{% entitylist id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

Обычно литеральные строки GUID не используются. Вместо этого id указывается с помощью свойства GUID другой переменной.

```
{% entitylist id:page.adx_entitylist.id %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**name**

Загружает список сущностей по имени.

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**key**

Загружает список сущностей по идентификатору **или** по имени. Если предоставленное значение ключа можно анализировать как [GUID](https://en.wikipedia.org/wiki/Globally_unique_identifier), список сущностей будет загружен по идентификатору. В противном случае он будет загружен по имени.

```
<!-- key_variable can hold an ID or name -->

{% entitylist key:key_variable %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**language\_code**

Код языка Power Apps в виде целого числа для выбора загружаемых локализованных подписей списка сущностей. Если language\_code не указан, будет использоваться язык по умолчанию подключения Power Apps приложения портала.

```
{% entitylist name:"My Entity List", language_code:1033 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

## <a name="entityview"></a>entityview

Загружает указанное представление Power Apps по имени или идентификатору. Доступ к свойствам представления — метаданным столбца представления, записям результата разбиения на страницы и т. д., — можно затем получить с помощью [объекта entityview](liquid-objects.md#entityview), который будет доступен в блоке тега.  

Если представление загружено успешно, отображается содержимое внутри блока. Если представление не найдено, содержимое блока не отображается.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

По умолчанию объекту entityview задается имя переменной entityview. Если требуется, может быть указано другое имя переменной.

```
{% entityview my_view = logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ my_view.total_records }} total records.

{% endentityview %}
```

Если entityview вложен в блок entitylist, он наследует свою конфигурацию по умолчанию (размер страницы результатов, параметры фильтра и т. д.) от списка сущностей. Если параметры id или name представления не указаны для entityview, оно загружает представление из содержащего его entitylist.

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview %}

Loaded default view of the entity list associated with the current page, with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

### <a name="parameters"></a>Параметры

Для выбора загружаемого представления Power Apps укажите **или** id, **или** logical\_name с параметром name. Если ни один из этих параметров не указан и тег entityview находится внутри тега entitylist, будет загружено представление по умолчанию из окружающего entitylist.

**id**

id должен быть строкой, которую можно анализировать как GUID.

```
{% entityview id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity view {{ entityview.name }}.

{% endentityview %}
```

Обычно литеральные строки GUID не используются. Вместо этого id указывается с помощью свойства GUID другой переменной.

```
{% entityview id:request.params.view %}

Loaded entity view {{ entityview.name }} using view query string request parameter.

{% endentityview %}
```

**logical\_name**

Логическое имя сущности Power Apps для загружаемого представления. Должно использоваться в сочетании с параметром name.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**name**

Имя Power Apps для загружаемого представления. Должно использоваться в сочетании с logical\_name.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**filter**

Определяет, требуется ли фильтровать результаты представления по пользователю или учетной записи. Должно иметь строковое значение "пользователь" или "организация".

```
{% entityview id:request.params.view, filter:'user' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Распространенный случай использования состоит в задании этого параметра на основе [request](liquid-objects.md#request).  

```
{% entityview id:request.params.view, filter:request.params.filter %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**metafilter**

Указывает выражение фильтра метаданных списка сущностей для фильтрации результатов представления. Этот параметр действителен, только когда entityview используется в сочетании с entitylist. В большинстве случаев этот параметр задается на основе [request](liquid-objects.md#request).  

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview id:request.params.view, metafilter:request.params.mf %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

**order**

Указывает выражение сортировки для упорядочивания результатов представления. Выражение сортировки может содержать одно или несколько логических имен атрибутов сущности, за которым должно идти направление сортировки ASC или DESC.

```
{% entityview id:request.params.view, order:'name ASC, createdon DESC' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Распространенный случай использования состоит в задании этого параметра на основе [request](liquid-objects.md#request).  

```
{% entityview id:request.params.view, order:request.params.order %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**page**

Определяет загружаемую страницу результата представления. Если этот параметр не задан, будет загружена первая страница результатов.

В этот параметр необходимо передавать либо целое число, либо строку, которую можно проанализировать как целое число. Если указано значение для этого параметра, но оно равно NULL или по каким-то другим причинам не может быть проанализировано как целое число, будет загружена первая страница результатов.

```
{% entityview id:request.params.view, page:2 %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Распространенный случай использования состоит в задании этого параметра на основе [request](liquid-objects.md#request).  

```
{% entityview id:request.params.view, page:request.params.page %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**page\_size**

Указывает число результатов, загружаемых для текущей страницы результатов. Если значение этого параметра не указано и entityview используется в блоке [entitylist](#entitylist), будет использоваться размер страницы списка сущностей. Вне блока entitylist будут использоваться значение по умолчанию 10.

В этот параметр необходимо передавать либо целое число, либо строку, которую можно проанализировать как целое число. Если указано значение для этого параметра, но оно равно NULL или по каким-то другим причинам не может быть проанализировано как целое число, используется размер страницы по умолчанию.

```
{% entityview id:request.params.view, page_size:20 %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Распространенный случай использования состоит в задании этого параметра на основе [request](liquid-objects.md#request).  

```
{% entityview id:request.params.view, page_size:request.params.pagesize %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**search**

Указывает выражение поиска, по которому требуется фильтровать результаты представления. Простые выражения поиска по ключевым словам фильтруют по тому, начинается ли атрибут с ключевого слова. Подстановочные символы \* также можно включить в выражение.

```
{% entityview id:request.params.view, search:'John\*' %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

Обычно значение данного параметра задается на основе [request](liquid-objects.md#request), чтобы фильтр поиска можно было задать на основе данных, введенных пользователем.  
```
{% entityview id:request.params.view, search:request.params.search %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

**enable\_entity\_permissions**

Указывает, следует ли применить фильтрацию по разрешениям сущности в результатах представления. По умолчанию для этого параметра задано значение false. Если entityview используется в блоке entitylist, значение этого параметра будет наследоваться из конфигурации списка сущностей.

В этот параметр необходимо передавать либо значение [boolean](liquid-types.md#boolean), либо строку, которую можно проанализировать как логическое значение (true, false). Если указано значение для этого параметра, но оно равно NULL или по каким-то другим причинам не может быть проанализировано как логическое значение, используется значение false.  

```
{% entityview id:request.params.view, enable_entity_permissions:true %}

Loaded entity view with {{ entityview.total_records }} total records to which the user has read permission.

{% endentityview %}
```

**language\_code**

Код языка Power Apps в виде целого числа для выбора локализованных подписей представления сущности (подписи заголовков столбцов и т. д.) для загрузки. Если language\_code не указан, будет использоваться язык по умолчанию подключения Power Apps приложения портала.

Если entityview используется в блоке entitylist, entityview наследует конфигурацию кода языка из entitylist.

```
{% entityview logical_name:'contact', name:"Active Contacts", language_code:1033 %}

Loaded entity view {{ entityview.name }}.

{% endentitylist %}
```

## <a name="searchindex"></a>searchindex

Выполняет запрос по указателю поиска портала. Доступ к соответствующим результатам можно затем получить с помощью [searchindex](liquid-objects.md#searchindex), который будет доступен в блоке тега.  

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

По умолчанию объекту указателя поиска задается имя переменной searchindex. Если требуется, может быть указано другое имя переменной.

```
{% searchindex liquid_search = query: 'support', page: params.page, page_size: 10 %}

{% if liquid_search.results.size > 0 %}

...

{% endif %}

{% endsearchindex %}
```

### <a name="parameters"></a>Параметры

Тег searchindex принимает следующие параметры.

**query**

Запрос, используемый для поиска результатов. Этот параметр должен принимать указанную пользователем часть запроса указателя (если она имеется.)

```
{% searchindex query: 'support' %}

...

{% endsearchindex %}
```

Распространенный случай использования состоит в задании этого параметра на основе [request](liquid-objects.md#request).  

```
{% searchindex query: request.params.query %}

...

{% endsearchindex %}
```

Этот параметр поддерживает [синтаксис средства синтаксического анализа запросов Lucene](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html).

**filter**

Дополнительный запрос, используемый для поиска результатов. Этот параметр должен принимать указанный разработчиком фильтр для результатов, если требуется.

```
{% searchindex query: request.params.query, filter: '+statecode:0' %}

...

{% endsearchindex %}
```

Этот параметр поддерживает [синтаксис средства синтаксического анализа запросов Lucene](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html).  

> [!Note]     
> Разница между filter и query заключается в том, что хотя оба параметра принимают синтаксис средства синтаксического анализа запросов Lucene, параметр query предназначен для более свободного анализа этого синтаксиса ߝ так как предполагается, что большинство конечных пользователей не знакомы с этим синтаксисом. Поэтому в случае сбоя анализа параметра query согласно этому синтаксису, весь запрос представляется в виде escape-последовательности и передается как текст запроса. filter, с другой стороны, будет анализироваться строго и возвращает ошибку в случае недопустимого синтаксиса.

**logical\_names**

Логические имена сущностей Power Apps, которыми будут ограниченны соответствующие результаты, в виде строки с разделителями-запятыми. Если не указаны, возвращаются все соответствующие сущности.

```
{% searchindex query: request.params.query, logical_names: 'kbarticle,incident' %}

...
>
{% endsearchindex %}
```
**page**

Возвращаемая страница результатов поиска. Если не указана, возвращается первая страница (1).

```
{% searchindex query: request.params.query, page: 2 %}

...

{% endsearchindex %}
```

Распространенный случай использования состоит в задании этого параметра на основе [request](liquid-objects.md#request).  

```
{% searchindex query: request.params.query, page: request.params.page %}

...

{% endsearchindex %}
```

**page\_size**

Размер возвращаемой страницы результатов. Если не указан, будет использоваться размер по умолчанию 10.

```
{% searchindex query: request.params.query, page_size: 20 %}

...

{% endsearchindex %}
```

## <a name="entityform"></a>entityform

Полностью отображает настроенные в Power Apps формы сущности, по имени или идентификатору.  

> [!Note]
> Тег entityform доступен только для использования в содержимом, отображаемом внутри шаблона страницы, основанного на <em>[веб-шаблоне](store-content-web-templates.md)</em>. При попытке использовать этот тег внутри шаблона страницы, основанного на перезаписи, ничего не отображается. Может отображаться только один тег entityform или webform на одной странице. Теги entityform и webform после первого тега не будут отображаться.       

`{% entityform name: 'My Entity Form' %}`

### <a name="parameters"></a>Параметры

**name**

Имя формы сущности, которую требуется загрузить.

`{% entityform name:My Entity Form %}`

## <a name="webform"></a>webform

Полностью отображает настроенную в Power Apps веб-форму, по имени или идентификатору. Тег webform доступен только для использования в содержимом, отображаемом внутри шаблона страницы, основанного на [веб-шаблоне](store-content-web-templates.md). При попытке использовать этот тег внутри шаблона страницы, основанного на перезаписи, ничего не отображается. Может отображаться только один тег entityform или webform на одной странице. Теги entityform и webform после первого тега не будут отображаться.                
`{% webform name: 'My Web Form' %}`

### <a name="parameters"></a>Параметры

**name**

Имя веб-формы, которую требуется загрузить.

`{% webform name:My Web Form %}`


### <a name="see-also"></a>См. также

[Теги потока управления](control-flow-tags.md)<br>
[Теги итерирования](iteration-tags.md)<br>
[Переменные теги](variable-tags.md)<br>
[Теги шаблона](template-tags.md)
