---
title: Поиск в содержимом вложенных файлов на портале | MicrosoftDocs
description: Узнайте, как настроить портал для поиска в содержимом вложенных файлов на портале.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 52d7701ac84072c84886ea86969f28809d0e7960
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551653"
---
# <a name="search-within-file-attachment-content"></a>Поиск в содержимом вложенных файлов

Можно использовать вложение Notes, чтобы включить загружаемые файлы в статьи базы знаний. Также можно использовать веб-файлы для создания страницы вопросов и ответов с загружаемым содержимым.

Вы можете настроить портал, чтобы разрешить пользователям портала выполнять поиск в содержимом вложений в статьях базы знаний. Это помогает пользователям найти нужные сведения.

В статьях базы знаний все вложения примечаний с определенным префиксом индексируются. В веб-файлах индексируются последние заметки о вложениях.

Чтобы индексировать вложения, необходимо создать следующие параметры сайта и задать для них значение **true**:

|Параметр сайта|Description|
|------------|-----------|
|Поиск и Индекснотесаттачментс|Указывает, следует ли индексировать содержимое вложений Notes в статьях базы знаний и веб-файлы. По умолчанию он имеет значение **false**.|
|Формы knowledgemanagement/Дисплайнотес|Указывает, следует ли индексировать вложения статей базы знаний. По умолчанию он имеет значение **false**.|
|||

> [!NOTE]
> Поиск возможен только для файлов, присоединенных к статьям базы знаний. Файлы, присоединенные к веб-файлам, недоступны для поиска.

При поиске термина в результаты поиска также включаются вложения. Если условие поиска соответствует вложению Notes, также предоставляется ссылка на соответствующую статью базы знаний. Чтобы просмотреть загружаемые вложения, в левой области выберите **загрузки** в разделе **тип записи** . Чтобы изменить метку **downloads** , измените фрагмент содержимого для поиска/аспекта/downloads. По умолчанию устанавливается значение **downloads**.

![Скачать вложение](../media/search-attachment-content.png "Скачать вложение") 

> [!NOTE]
> - Чтобы использовать эту функцию, необходимо [включить поиск релевантности](https://docs.microsoft.com/dynamics365/customer-engagement/admin/configure-relevance-search-organization). Дополнительные сведения: [Поиск релевантности](https://docs.microsoft.com/dynamics365/customer-engagement/basics/relevance-search-results)
 
## <a name="update-portal-configurations"></a>Обновление конфигураций портала

Если у вас уже есть портал до 2018 апреля и вы обновили портал до последней версии, необходимо использовать следующие конфигурации для того, чтобы тот же пользовательский интерфейс, что и при установке нового портала.

**Фрагменты содержимого**

Чтобы изменить метку, отображаемую в результатах поиска для заметок и загрузок веб-файлов, создайте фрагмент содержимого/аспект/downloads, а затем задайте для него значение. Значение по умолчанию — **downloads**.

**Веб-файлы**

Содержимое вложенных файлов, связанных с веб-файлами, теперь можно индексировать. Можно обновить существующие веб-файлы для файлов CSS и файлов изображений (например, начальной загрузки. min. CSS, Theme. CSS и хомехеро. jpg), которые будут исключены из поиска. 

1. Откройте [приложение управления портала](configure-portal.md) и перейдите на **порталы** > **веб-файлы**.
2. Откройте файл, который будет исключен из поиска.
3. В разделе **Разное**выберите **Да** в поле **исключить из поиска** .

**Веб-шаблоны**

Веб-шаблон шаблона "область поиска с аспектами" изменен для вывода файлов, связанных со статьями базы знаний в качестве первичных элементов результатов поиска, со ссылкой на связанную статью. Необходимо обновить веб-шаблон шаблона "аспектный поиск-результаты" в следующем источнике:

```
{% assign openTag = '{{' %}
{% assign closingTag = '}}' %}
{%raw%}
  <script id=search-view-results type=text/x-handlebars-template>
   {{#if items}}
    <div class=page-header>
     <h3>{%endraw%}{{openTag}} stringFormat {{ resx.Search_Results_Format_String }} firstResultNumber lastResultNumber itemCount {{closingTag}}{%raw%}
      <em class=querytext>{{{query}}}</em>
      {{#if isResetVisible}}
       <a class="btn btn-default btn-sm facet-clear-all" role="button" title="{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}" tabIndex="0">{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}</a>
      {{/if}}
     </h3>
    </div>
   <ul>
    {{#each items}}
     <li>
      <h3><a title={{title}} href={{url}}>{{#if parent}}<span class=glyphicon glyphicon-file pull-left text-muted aria-hidden=true></span>{{/if}}{{title}}</a></h3>
      <p class=fragment>{{{fragment}}}</p>
      {{#if parent}}
       <p class=small related-article>{%endraw%}{{ resx.Related_Article }}{%raw%}: <a title={{parent.title}} href={{parent.absoluteUrl}}>{{parent.title}}</a></p>
      {{/if}}
      <ul class=note-group small list-unstyled>
       {{#if relatedNotes}}
        {{#each relatedNotes}}
         <li class=note-item>
         {{#if isImage}}
          <a target=_blank title={{title}} href={{absoluteUrl}}><span class=glyphicon glyphicon-file aria-hidden=true></span>&nbsp;{{title}}</a>
         {{else}}
          <a title={{title}} href={{absoluteUrl}}><span class=glyphicon glyphicon-file aria-hidden=true></span>&nbsp;{{title}}</a>
         {{/if}}
         <p class=fragment text-muted>{{{fragment}}}</p>
         </li>
        {{/each}}
        {{/if}}
      </ul>
     </li>
    {{/each}}
   </ul>
   {{else}}
    <h2>{%endraw%}{{ resx.Search_No_Results_Found }}{%raw%}<em class=querytext>{{{query}}}</em>
     {{#if isResetVisible}}
      <a class="btn btn-default btn-sm facet-clear-all" role="button" title="{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}" tabIndex="0">{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}</a>
     {{/if}}
    </h2>
   {{/if}}
  </script>
{%endraw%}
```

**Параметры сайта**

Необходимо добавить `\_logicalname:annotation~0.9^0.25` значение в параметр сайта поиска и запроса. После добавления значение должно быть следующим:
```
+(@Query) \_title:(@Query) \_logicalname:knowledgearticle~0.9^0.3 \_logicalname:annotation~0.9^0.25 \_logicalname:adx_webpage~0.9^0.2 -\_logicalname:adx_webfile~0.9 adx_partialurl:(@Query) \_logicalname:adx_blogpost~0.9^0.1 -\_logicalname:adx_communityforumthread~0.9
```

Чтобы настроить аспекты для группирования заметок, связанных с статьями базы знаний и веб-файлами, в одном аспекте, измените имя параметра поиска или Рекордтипефацетсентитиес узла и добавьте `;Downloads:annotation,adx_webfile` к его значению.

Чтобы разрешить отображение вложений, связанных со статьями базы знаний, на портале и результаты поиска, измените параметр сайта **формы knowledgemanagement/дисплайнотес** и присвойте ему значение **true**. Параметр сайта **формы knowledgemanagement/нотесфилтер** содержит префиксное значение, которое должно быть предваряться текстовым полем примечания в заметках; на портале будут отображаться только заметки с указанным значением префикса. Значение по умолчанию — \*веб-\*, но его можно изменить с помощью параметра сайта.

Чтобы включить индексирование вложенных файлов, связанных с заметками, создайте параметр сайта **Search/индекснотесаттачментс** и присвойте ему значение **true**.
