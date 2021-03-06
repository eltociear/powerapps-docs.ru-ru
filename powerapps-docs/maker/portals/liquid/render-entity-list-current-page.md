---
title: Отобразить список сущностей, связанных с текущей страницей на портале | MicrosoftDocs
description: Пример кода для отображения списка сущностей, связанных с текущей страницей на портале.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 73149bc45d61f344b62f7a5e733848f11287c369
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980892"
---
# <a name="render-the-entity-list-associated-with-the-current-page"></a>Обработка списка сущностей, связанных с текущей страницей

Отображение списка сущностей, связанных с текущей страницей, в виде допускающей сортировку таблицы с разбиением на страницы. Использует параметры [entitylist](liquid-objects.md#entitylist), [entityview](liquid-objects.md#entityview), [теги сущностей Common Data Service Power Apps](portals-entity-tags.md), [страница](liquid-objects.md#page) и [запрос](liquid-objects.md#request), а также включает поиск и выбор нескольких представлений.  

```xml
{% entitylist id:page.adx_entitylist.id %}
  <div class="navbar navbar-default">
    <div class="container-fluid">
      <div class="navbar-header">
        <button type="button" class="navbar-toggle"
          data-toggle="collapse"
          data-target="#entitylist-navbar-{{ entitylist.id }}">
          <span class="sr-only">Toggle navigation</span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
        </button>
        <a class="navbar-brand" href="{{ page.url }}">{{ entitylist.adx_name }}</a>
      </div>
      <div class="collapse navbar-collapse" id="entitylist-navbar-{{ entitylist.id }}">

        {% if entitylist.views.size > 1 %}
          <ul class="nav navbar-nav">
            <li class="dropdown">
              <a href="#" class="dropdown-toggle" data-toggle="dropdown">
                <i class="fa fa-list"></i> Views <span class="caret"></span>
              </a>
              <ul class="dropdown-menu" role="menu">
                {% for view in entitylist.views -%}
                  <li{% if params.view == view.id %} class="active"{% endif %}>
                    <a href="{{ request.path | add_query:'view', view.id }}">{{view.name}}</a>
                  </li>
                {% endfor -%}
              </ul>
            </li>
          </ul>
        {% endif %}
      
        {% if entitylist.search_enabled %}
          <form class="navbar-form navbar-left" method="get">
            <div class="input-group">
              {% if params.search.size > 0 %}
                <div class="input-group-btn">
                  <a class="btn btn-default"
                    href="{{ request.path_and_query | remove_query:'search' }}">&times;</a>
                </div>
              {% endif %}
              <input name="search" class="form-control"
                value="{{ params.search }}"
                placeholder="{{ entitylist.search_placeholder | default: 'Search' }}"
                type="text" />
              <div class="input-group-btn">
                <button type="submit" class="btn btn-default"
                  title="{{ entitylist.search_tooltip }}">
                  <i class="fa fa-search">&nbsp;</i>
                </button>
              </div>
            </div>
          </form>
        {% endif %}
        
        {% if entitylist.create_enabled %}
          <ul class="nav navbar-nav navbar-right">
            <li>
              <a href="{{ entitylist.create_url }}">
                <i class="fa fa-plus"></i> {{ entitylist.create_label | default: 'Create' }}
              </a>
            </li>
          </ul>
        {% endif %}
        
      </div>
    </div>
  </div>
  
  {% entityview id:params.view, search:params.search, order:params.order, page:params.page, pagesize:params.pagesize, metafilter:params.mf %}
    {% assign order = params.order | default: entityview.sort_expression %}
    <table class="table" data-order="{{ order }}">
      <thead>
        <tr>
          {% for c in entityview.columns -%}
            <th width="{{ c.width }}" data-logicalname="{{ c.logical_name }}">
              {% if c.sort_enabled %}
                {% assign current_sort = order | current_sort:c.logical_name %}
                {% case current_sort %}
                {% when 'ASC' %}
                  <a href="{{ request.path_and_query | add_query:'order', c.sort_descending }}">
                    {{ c.name }} <i class="fa fa-sort-asc"></i>
                  </a>
                {% when 'DESC' %}
                  <a href="{{ request.path_and_query | add_query:'order', c.sort_ascending }}">
                    {{ c.name }} <i class="fa fa-sort-desc"></i>
                  </a>
                {% else %}
                  <a href="{{ request.path_and_query | add_query:'order', c.sort_ascending }}">
                    {{ c.name }} <i class="fa fa-unsorted"></i>
                  </a>
                {% endcase %}
              {% else %}
                {{ c.name }}
              {% endif %}
            </th>
          {% endfor -%}
          <th width="1"></th>
        </tr>
      </thead>

      <tbody>
        {% for e in entityview.records -%}
          <tr>

            {% for c in entityview.columns -%}
              {% assign attr = e[c.logical_name] %}
              {% assign attr_type = c.attribute_type | downcase %}

              <td data-logicalname="{{ c.logical_name }}">
                {% if attr.is_entity_reference -%}
                  {{ attr.name }}
                {% elsif attr_type == 'datetime' %}
                  {% if attr %}
                    <time datetime="{{ attr | date_to_iso8601 }}">
                      {{ attr }}
                    </time>
                  {% endif %}
                {% elsif attr_type == 'picklist' %}
                  {{ attr.label }}
                {% else %}
                  {{ attr }}
                {% endif -%}
              </th>
            {% endfor -%}

            <td>
              {% if entitylist.detail_enabled -%}
                <a class="btn btn-default btn-xs"
                  href="{{ entitylist.detail_url}}?{{ entitylist.detail_id_parameter }}={{ e.id }}"
                  title="{{ entitylist.detail_label }}">
                  <i class="fa fa-external-link"></i>
                </a>
              {% endif -%}
            </td>

          <tr>
        {% endfor -%}
      </tbody>
    </table>
    
    {% if entityview.pages.size > 0 %}
      {% assign first_page = entityview.first_page %}
      {% assign last_page = entityview.last_page %}
      {% assign page_offset = entityview.page | minus:1 | divided_by:10 | times:10 %}
      {% assign page_slice_first_page = page_offset | plus:1 %}
      {% assign page_slice_last_page = page_offset | plus:10 %}

      <ul class="pagination">
        <li {% unless first_page and entityview.page > 1 %}class="disabled"{% endunless %}>
          <a
            {% if first_page and entityview.page > 1 %}
              href="{{ request.url | add_query:'page', first_page | path_and_query }}"
            {% endif %}>
            &laquo;
          </a>
        </li>

        <li {% unless entityview.previous_page %}class="disabled"{% endunless %}>
          <a
            {% if entityview.previous_page %}
              href="{{ request.url | add_query:'page', entityview.previous_page | path_and_query }}"
            {% endif %}>
            &lsaquo;
          </a>
        </li>

        {% if page_slice_first_page > 1 %}
          {% assign previous_slice_last_page = page_slice_first_page | minus:1 %}
          <li>
            <a href="{{ request.url | add_query:'page', previous_slice_last_page | path_and_query }}">
              &hellip;
            </a>
          </li>
        {% endif %}

        {% for page in entityview.pages offset:page_offset limit:10 -%}
          <li{% if page == entityview.page %} class="active"{% endif %}>
            <a href="{{ request.url | add_query:'page', page | path_and_query }}">
              {{ page }}
            </a>
          </li>
        {% endfor -%}

        {% if page_slice_last_page < entityview.pages.size %}
          {% assign next_slice_first_page = page_slice_last_page | plus:1 %}
          <li>
            <a href="{{ request.url | add_query:'page', next_slice_first_page | path_and_query }}">
              &hellip;
            </a>
          </li>
        {% endif %}

        <li {% unless entityview.next_page %}class="disabled"{% endunless %}>
          <a
            {% if entityview.next_page %}
              href="{{ request.url | add_query:'page', entityview.next_page | path_and_query }}"
            {% endif %}>
            &rsaquo;
          </a>
        </li>

        <li {% unless last_page and entityview.page < last_page %}class="disabled"{% endunless %}>
          <a
            {% if last_page and entityview.page < last_page %}
              href="{{ request.url | add_query:'page', last_page | path_and_query }}"
            {% endif %}>
            &raquo;
          </a>
        </li>
      </ul>

    {% endif %}
    
  {% endentityview %}
{% endentitylist %}
```

### <a name="see-also"></a>См. также

[Создание настраиваемого шаблона страницы с помощью Liquid и шаблона страницы "Веб-шаблон"](create-custom-template.md)  
[Создание настраиваемого шаблона страницы для отображения RSS-канала](render-rss-custom-page-template.md)  
[Отображение заголовка веб-сайта и основной навигационной панели](render-site-header-primary-navigation.md)  
[Отображение до трех уровней иерархии страниц с помощью гибридной навигации](hybrid-navigation-render-page-hierachy.md)
