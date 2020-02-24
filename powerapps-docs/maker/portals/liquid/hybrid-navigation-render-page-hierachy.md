---
title: Использование гибридной навигации для отображения иерархии страницы для портала | MicrosoftDocs
description: Инструкции по использованию гибридной навигации для отображения иерархии страницы для портала.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 2fa7927d13a7cb940bb1d2d9b1281110a196b48f
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978956"
---
# <a name="render-up-to-three-levels-of-page-hierarchy-by-using-hybrid-navigation"></a>Отображение до трех уровней иерархии страниц с помощью гибридной навигации

Этот пример отображает тип гибридной навигации, основанный на карте сайта портала, который отображает до трех уровней иерархии страниц. Правила для этого компонента:

* Страницы-предшественники текущей страницы отображаются вплоть до домашней страницы (или до максимальной глубины, определенной необязательными параметром depth\_offset). 
* Если у текущей страницы имеются дочерние страницы, они отображаются.
* Если у текущей страницы нет дочерних страниц, отображаются страницы, находящиеся на одном уровне с текущей страницей.

```xml
{% assign depth_offset = depth_offset | default: 0 %}
{% assign current_page = current_page | default: page %}
{% assign current_depth = 0 %}

{% if current_page.children.size > 0 %}
  {% assign leaf_page = false %}
{% else %}
  {% assign leaf_page = true %}
{% endif %}

{% capture page_item %}
  <li class=active>
    <a href={{ current_page.url | h }} title={{ current_page.title | h }}>
      {% if leaf_page %}
        <span class=fa fa-fw aria-hidden=true></span>
      {% else %}
        <span class=fa fa-fw fa-caret-down aria-hidden=true></span>
      {% endif %}
      {{ current_page.title | h }}
    </a>
    {% unless leaf_page %}
      <ul>
        {% for child in current_page.children %}
          <li>
            <a href={{ child.url | h }} title={{ child.title | h }}>
              {% if child.children.size > 0 %}
                <span class=fa fa-fw fa-caret-right aria-hidden=true></span>
              {% else %}
                <span class=fa fa-fw aria-hidden=true></span>
              {% endif %}
              {{ child.title | h }}
              {% if child.entity.logical_name == 'adx_shortcut' %}
                &nbsp;<span class=fa fa-fw fa-external-link aria-hidden=true></span>
              {% elsif child.entity.logical_name == 'adx_webfile' %}
                &nbsp;<span class=fa fa-fw fa-file-o aria-hidden=true><span class=sr-only>(File)</span></span>
              {% endif %}
            </a>
          </li>
        {% endfor %}
      </ul>
    {% endunless %}
  </li>
{% endcapture %}

<ul class=side-nav role=navigation>
  {% assign crumb_count = 0 %}
  {% assign leaf_mode = false %}
  
  {% for crumb in current_page.breadcrumbs %}
    {% unless current_depth < depth_offset %}
      {% if forloop.last and leaf_page %}
        {% assign leaf_mode = true %}
      {% else %}
        <li>
          <a href={{ crumb.url | h }} title={{ crumb.title | h }}>
            <span class=fa fa-fw fa-caret-right aria-hidden=true></span>
            {{ crumb.title | h }}
          </a>
        </li>
      {% endif %}
      {% assign crumb_count = crumb_count | plus: 1 %}
    {% endunless %}
    {% assign current_depth = current_depth | plus: 1 %}
  {% endfor %}
  
  {% if crumb_count < 1 %}
    {{ page_item }}
  {% elsif crumb_count < 2 and leaf_mode %}
    {% for parent_sibling in current_page.parent.parent.children %}
      {% if parent_sibling.url == current_page.parent.url %}
        <li>
          <a href={{ current_page.parent.url | h }} title={{ current_page.parent.title | h }}>
            <span class=fa fa-fw fa-caret-down aria-hidden=true></span>
            {{ current_page.parent.title | h }}
          </a>
          <ul>
            {% for sibling in current_page.parent.children %}
              <li {% if sibling.url == current_page.url %}class=active{% endif %}>
                <a href={{ sibling.url | h }} title={{ sibling.title | h }}>
                  {% if sibling.children.size > 0 %}
                    <span class=fa fa-fw fa-caret-right aria-hidden=true></span>
                  {% else %}
                    <span class=fa fa-fw aria-hidden=true></span>
                  {% endif %}
                  {{ sibling.title | h }}
                  {% if sibling.entity.logical_name == 'adx_shortcut' %}
                    &nbsp;<span class=fa fa-fw fa-external-link aria-hidden=true></span>
                  {% elsif sibling.entity.logical_name == 'adx_webfile' %}
                    &nbsp;<span class=fa fa-fw fa-file-o aria-hidden=true><span class=sr-only>(File)</span></span>
                  {% endif %}
                </a>
              </li>
            {% endfor %}
          </ul>
        </li>
      {% else %}
        <li>
          <a href={{ parent_sibling.url | h }} title={{ parent_sibling.title | h }}>
            {% if parent_sibling.children.size > 0 %}
              <span class=fa fa-fw fa-caret-right aria-hidden=true></span>
            {% else %}
              <span class=fa fa-fw aria-hidden=true></span>
            {% endif %}
            {{ parent_sibling.title | h }}
            {% if parent_sibling.entity.logical_name == 'adx_shortcut' %}
              &nbsp;<span class=fa fa-fw fa-external-link aria-hidden=true></span>
            {% elsif parent_sibling.entity.logical_name == 'adx_webfile' %}
              &nbsp;<span class=fa fa-fw fa-file-o aria-hidden=true><span class=sr-only>(File)</span></span>
            {% endif %}
          </a>
        </li>
      {% endif %}
    {% endfor %}
  {% else %}
    <li>
      <ul>
        {% if leaf_mode %}
          {% for parent_sibling in current_page.parent.parent.children %}
            {% if parent_sibling.url == current_page.parent.url %}
              <li>
                <a href={{ current_page.parent.url | h }} title={{ current_page.parent.title | h }}>
                  <span class=fa fa-fw fa-caret-down aria-hidden=true></span>
                  {{ current_page.parent.title | h }}
                </a>
                <ul>
                  {% for sibling in current_page.parent.children %}
                    <li {% if sibling.url == current_page.url %}class=active{% endif %}>
                      <a href={{ sibling.url | h }} title={{ sibling.title | h }}>
                        {% if sibling.children.size > 0 %}
                          <span class=fa fa-fw fa-caret-right aria-hidden=true></span>
                        {% else %}
                          <span class=fa fa-fw aria-hidden=true></span>
                        {% endif %}
                        {{ sibling.title | h }}
                        {% if sibling.entity.logical_name == 'adx_shortcut' %}
                          &nbsp;<span class=fa fa-fw fa-external-link aria-hidden=true></span>
                        {% elsif sibling.entity.logical_name == 'adx_webfile' %}
                          &nbsp;<span class=fa fa-fw fa-file-o aria-hidden=true><span class=sr-only>(File)</span></span>
                        {% endif %}
                      </a>
                    </li>
                  {% endfor %}
                </ul>
              </li>
            {% else %}
              <li>
                <a href={{ parent_sibling.url | h }} title={{ parent_sibling.title | h }}>
                  {% if parent_sibling.children.size > 0 %}
                    <span class=fa fa-fw fa-caret-right aria-hidden=true></span>
                  {% else %}
                    <span class=fa fa-fw aria-hidden=true></span>
                  {% endif %}
                  {{ parent_sibling.title | h }}
                  {% if parent_sibling.entity.logical_name == 'adx_shortcut' %}
                    &nbsp;<span class=fa fa-fw fa-external-link aria-hidden=true></span>
                  {% elsif parent_sibling.entity.logical_name == 'adx_webfile' %}
                    &nbsp;<span class=fa fa-fw fa-file-o aria-hidden=true><span class=sr-only>(File)</span></span>
                  {% endif %}
                </a>
              </li>
            {% endif %}
          {% endfor %}
        {% else %}
          {% for sibling in current_page.parent.children %}
            {% if sibling.url == current_page.url %}
              {{ page_item }}
            {% else %}
              <li>
                <a href={{ sibling.url | h }} title={{ sibling.title | h }}>
                  {% if sibling.children.size > 0 %}
                    <span class=fa fa-fw fa-caret-right aria-hidden=true></span>
                  {% else %}
                    <span class=fa fa-fw aria-hidden=true></span>
                  {% endif %}
                  {{ sibling.title | h }}
                  {% if sibling.entity.logical_name == 'adx_shortcut' %}
                    &nbsp;<span class=fa fa-fw fa-external-link aria-hidden=true></span>
                  {% elsif sibling.entity.logical_name == 'adx_webfile' %}
                    &nbsp;<span class=fa fa-fw fa-file-o aria-hidden=true><span class=sr-only>(File)</span></span>
                  {% endif %}
                </a>
              </li>
            {% endif %}
          {% endfor %}
        {% endif %}
      </ul>
    </li>
  {% endif %}
</ul>

<style type=text/css>
  .side-nav {
    border-right: solid 1px #eee;
  }
  
  .side-nav,
  .side-nav ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }
  
  .side-nav ul {
    margin-left: 20px;
  }
  
  .side-nav a {
    display: block;
    line-height: 30px;
    overflow: hidden;
    text-decoration: none;
    white-space: nowrap;
  }
  
  .side-nav li > a:hover {
    border-right: solid 1px #23527c;
  }
  
  .side-nav li.active > a,
  .side-nav li.active > a:hover {
    border-right: solid 1px #333;
    color: #333;
    font-weight: bold;
  }
</style>
```
### <a name="see-also"></a>См. также

[Создание настраиваемого шаблона страницы с помощью Liquid и шаблона страницы "Веб-шаблон"](create-custom-template.md)  
[Создание настраиваемого шаблона страницы для отображения RSS-канала](render-rss-custom-page-template.md)  
[Обработка списка сущностей, связанных с текущей страницей](render-entity-list-current-page.md)  
[Отображение заголовка веб-сайта и основной навигационной панели](render-site-header-primary-navigation.md)  
