---
title: Поиск в содержимом файла вложения на портале | MicrosoftDocs
description: Узнайте, как настроить ваш портал, чтобы выполнить поиск в содержимом файла вложения на портале.
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
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "2760952"
---
# <a name="search-within-file-attachment-content"></a>Поиск в содержимом вложенных файлов

Можно использовать вложение примечаний для включения загружаемых файлов в статьи базы знаний. Можно также использовать веб-файлы для создания страниц вопросов и ответов с загружаемым содержимым.

Можно настроить портал, чтобы позволить пользователям портала выполнять поиск в содержимом вложений статей базы знаний. Это помогает пользователям находить информацию, которую они хотят найти.

В статьях базы знаний индексируются любые вложения примечаний с определенным префиксом. В веб-файлах индексируются последнее вложение примечания.

Для индексации вложений необходимо создать следующие параметры сайта и установить для них значение **True**:

|Параметр сайта|Описание|
|------------|-----------|
|Search/IndexNotesAttachments|Указывает, требуется ли индексация содержимого вложений примечаний в статьях базы знаний и веб-файлах. По умолчанию установлено значение **False**.|
|KnowledgeManagement/DisplayNotes|Указывает, требуется ли индексировать вложения статей базы знаний. По умолчанию установлено значение **False**.|
|||

> [!NOTE]
> Поиск возможен только в файлах, которые прикреплены к статьям базы знаний. Поиск в файлах, которые прикреплены к веб-файлам, невозможен.

При поиске термина результаты поиска также включают вложения. Если условие поиска соответствует вложению примечания, ссылка на соответствующую статью базы знаний также предоставляется. Чтобы посмотреть загружаемые вложения, выберите **Загрузки** в разделе **Тип записей** в левой панели. Чтобы изменить подпись **Загрузки**, измените фрагмент содержимого Search/Facet/Downloads. По умолчанию задано значение **Загрузки**.

![Скачать вложение](../media/search-attachment-content.png "Скачать вложение") 

> [!NOTE]
> - Чтобы использовать эту функцию, необходимо разрешить [поиск с сортировкой по релевантности](https://docs.microsoft.com/dynamics365/customer-engagement/admin/configure-relevance-search-organization). Подробнее: [Поиск с сортировкой по релевантности](https://docs.microsoft.com/dynamics365/customer-engagement/basics/relevance-search-results)
 
## <a name="update-portal-configurations"></a>Обновление конфигураций портала

Если у вас уже имелся портал до апреля 2018 и вы обновили портал до последней версии, необходимо использовать следующие конфигурации, чтобы пользовательский интерфейс был таким же, как и при новой установке портала.

**Фрагменты содержимого**

Чтобы изменить подписи, отображаемые в результатах поиска для аннотаций и загрузок веб-файлов, создайте фрагмент содержимого Search/Facet/Downloads, затем задайте для него требуемое значение. По умолчанию используется значение **Загрузки**.

**Веб-файлы**

Содержимое файловых вложений, связанных с веб-файлами, теперь можно индексировать. Можно обновить существующие веб-файлы, чтобы файлы CSS и графические файлы (например, bootstrap.min.css, theme.css и homehero.jpg), были исключены из поиска. 

1. Откройте [приложение управление порталами](configure-portal.md) и выберите **Порталы** > **Веб-файлы**.
2. Откройте файл, который нужно исключить из поиска.
3. В разделе **Разное** выберите значение **Да** в поле **Исключить из поиска**.

**Веб-шаблоны**

Веб-шаблон "Фасетный поиск — шаблон результатов" пересмотрен для отображения файлов, связанных со статьями базы знаний в качестве основных элементов результата поиска с соответствующей ссылкой на статью. Необходимо обновить "Фасетный поиск — шаблон результатов" до следующего источника:

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

Необходимо добавить значение `\_logicalname:annotation~0.9^0.25` в параметр сайта Search/Query. После добавления значение должно быть следующее:
```
+(@Query) \_title:(@Query) \_logicalname:knowledgearticle~0.9^0.3 \_logicalname:annotation~0.9^0.25 \_logicalname:adx_webpage~0.9^0.2 -\_logicalname:adx_webfile~0.9 adx_partialurl:(@Query) \_logicalname:adx_blogpost~0.9^0.1 -\_logicalname:adx_communityforumthread~0.9
```

Чтобы настроить фасетки для группирования заметкой, связанных со статьями базы знаний и веб-файлами в одну фасетку, измените имя параметра сайта Search/RecordTypeFacetsEntities и добавьте `;Downloads:annotation,adx_webfile` к его значению.

Чтобы позволить вложениям, связанным со статьями базы знаний, появляться на портале и в результатах поиска, измените параметр сайта **KnowledgeManagement/DisplayNotes** и задайте для него значение **True**. Параметр сайта **KnowledgeManagement/NotesFilter** содержит значение префикса, которое необходимо добавить в начало поля текста примечания в примечаниях; только примечания с указанным значением префикса будут отображаться на портале. По умолчанию значение равно \*WEB\*, однако его можно изменить с помощью параметра сайта.

Для включения индексирования файловых вложений, связанных с примечаниями, создайте параметр сайта **Search/IndexNotesAttachments** и установите для него значение **True**.
