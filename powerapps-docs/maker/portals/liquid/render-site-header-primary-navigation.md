---
title: Отображение заголовка веб-сайта и основной навигационной панели в портале | MicrosoftDocs
description: Инструкции и пример кода для отображения верхнего колонтитула и основной панели навигации веб-сайта на портале.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: d7725c5e577f7b2bc5f30d78cf3b13c6cd6d494d
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2020
ms.locfileid: "2981068"
---
# <a name="render-a-website-header-and-primary-navigation-bar"></a>Отображение заголовка веб-сайта и основной навигационной панели

Отображение заголовка веб-сайта и основной навигационной панели с помощью параметров порталов, фрагментов кода, веб-ссылок и маркеров сайта. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Сохранение содержимого источника с помощью веб-шаблонов](store-content-web-templates.md).  

> [!Note]
> Пример в этом разделе будет работать правильно только в том случае, если в вашем приложении отключено кэширование заголовков перекрестных запросов. В версии 7.0.0019 и более новых оно по умолчанию включено. Его можно отключить, создав настройку сайта с именем Header/OutputCache/Enabled и задав для нее значение false.


```xml
<div class=masthead hidden-xs>
  <div class=container>
    <div class=toolbar>
      <div class=toolbar-row>

        {% assign search_enabled = settings['search/enabled'] | boolean | default:true %}
        {% assign search_page = sitemarkers['Search'] %}
        {% if search_enabled and search_page %}
          <div class=toolbar-item toolbar-search>
            <form method=GET action={{ search_page.url }} role=search>
              <label for=q class=sr-only>
                  {{ snippets[Header/Search/Label] | default:Search }}
              </label>
              <div class=input-group>
                <input type=text class=form-control id=q name=q
                  placeholder={{ snippets[Header/Search/Label] | default:Search }}
                  value={{ params.q }}
                  title={{ snippets[Header/Search/Label] | default:Search }}>
                <div class=input-group-btn>
                  <button type=submit class=btn btn-default
                    title={{ snippets[Header/Search/ToolTip] | default:Search }}>
                    <span class=fa fa-search aria-hidden=true></span>
                  </button>
                </div>
              </div>
            </form>
          </div>
        {% endif %}

        <div class=toolbar-item>
          <div class=btn-toolbar role=toolbar>
            {% if user %}
              <div class=btn-group>
                <a href=# class=btn btn-default dropdown-toggle data-toggle=dropdown>
                  <span class=fa fa-user aria-hidden=true></span>
                  <span class=username>{{ user.fullname }}</span>
                  <span class=caret></span>
                </a>
                <ul class=dropdown-menu pull-right role=menu>
                  {% assign show_profile_nav = settings[Header/ShowAllProfileNavigationLinks] | boolean | default:true %}
                  {% if show_profile_nav %}
                    {% assign profile_nav = weblinks[Profile Navigation] %}
                    {% if profile_nav %}
                      {% for link in profile_nav.weblinks %}
                        <li>
                          <a href={{ link.url }}>{{ link.name }}</a>
                        </li>
                      {% endfor %}
                    {% endif %}
                  {% else %}
                    <li><a href={{ sitemarkers['Profile'].url }}>{{ snippets[Profile Link Text] | default:Profile }}</a></li>
                  {% endif %}
                  <li class=divider></li>
                  <li>
                    <a href=/account-signout?returnUrl={{ request.raw_url }}>
                      {{ snippets[links/logout] | default:Sign Out }}
                    </a>
                  </li>
                </ul>
              </div>
            {% else %}
              <div class=btn-group>
                <a class=btn btn-primary
                  href={{ sitemarkers['Login'].url | add_query:'returnurl', request.path_and_query }}>
                  <span class=fa fa-sign-in aria-hidden=true></span>
                  {{ snippets[links/login] | default:Sign In }}
                </a>
              </div>
            {% endif %}
          </div>
        </div>

      </div>
    </div>
    {% editable snippets 'Header' type: 'html' %}
  </div>
</div>
<div class=header-navbar navbar navbar-default navbar-static-top role=navigation>
  <div class=container>
    <div class=navbar-header>
      <button type=button class=navbar-toggle data-toggle=collapse data-target=#header-navbar-collapse>
        <span class=sr-only>Toggle navigation</span>
        <span class=icon-bar></span>
        <span class=icon-bar></span>
        <span class=icon-bar></span>
      </button>
      <div class=navbar-left visible-xs>
        {% editable snippets 'Mobile Header' type: 'html' %}
      </div>
    </div>
    <div id=header-navbar-collapse class=navbar-collapse collapse>
      <div class=navbar-left hidden-xs>
        {% editable snippets 'Navbar Left' type: 'html' %}
      </div>
      {% assign primary_nav = weblinks[Primary Navigation] %}
      {% if primary_nav %}
        <div class=navbar-left {% if primary_nav.editable %}xrm-entity xrm-editable-adx_weblinkset{% endif %} data-weblinks-maxdepth=2>
          <ul class=nav navbar-nav weblinks>
            {% for link in primary_nav.weblinks %}
              {% if link.display_page_child_links %}
                {% assign sublinks = sitemap[link.url].children %}
              {% else %}
                {% assign sublinks = link.weblinks %}
              {% endif %}
              <li class=weblink {% if sublinks.size > 0 %} dropdown{% endif %}>
                <a
                  {% if sublinks.size > 0 %}
                    href=# class=dropdown-toggle data-toggle=dropdown
                  {% else %}
                    href={{ link.url }}
                  {% endif %}
                  {% if link.nofollow %}rel=nofollow{% endif %}
                  {% if link.tooltip %}title={{ link.tooltip }}{% endif %}>
                  {% if link.image %}
                    {% if link.image.url startswith '.' %}
                      <span class={{ link.image.url | split:'.' | join }} aria-hidden=true></span>
                    {% else %}
                      <img src={{ link.image.url }}
                        alt={{ link.image.alternate_text | default:link.tooltip }}
                        {% if link.image.width %}width={{ link.image.width }}{% endif %}
                        {% if link.image.height %}height={{ link.image.height }}{% endif %}
                      />
                    {% endif %}
                  {% endif %}
                  {% unless link.display_image_only %}
                    {{ link.name }}
                  {% endunless %}
                  {% if sublinks.size > 0 %}
                    <span class=caret></span>
                  {% endif %}
                </a>
  
                {% if sublinks.size > 0 %}
                  <ul class=dropdown-menu role=menu>
                    {% if link.url %}
                      <li>
                        <a href={{ link.url }}
                          {% if link.nofollow %}rel=nofollow{% endif %}
                          {% if link.tooltip %}title={{ link.tooltip }}{% endif %}>{{ link.name }}</a>
                      </li>
                      <li class=divider></li>
                    {% endif %}
                    {% for sublink in sublinks %}
                      <li>
                        <a href={{ sublink.url }}
                          {% if sublink.nofollow %}rel=nofollow{% endif %}
                          {% if sublink.tooltip %}title={{ link.tooltip }}{% endif %}>
                          {{ sublink.name | default:sublink.title }}
                        </a>
                      </li>
                    {% endfor %}
                  </ul>
                {% endif %}
                
              </li>
            {% endfor %}
          </ul>
          {% editable primary_nav %}
        </div>
      {% endif %}
      <div class=navbar-right hidden-xs>
        {% editable snippets 'Navbar Right' type: 'html' %}
      </div>
    </div>
  </div>
</div>
```

### <a name="see-also"></a>См. также

[Создание настраиваемого шаблона страницы с помощью Liquid и шаблона страницы "Веб-шаблон"](create-custom-template.md)  
[Создание настраиваемого шаблона страницы для отображения RSS-канала](render-rss-custom-page-template.md)  
[Обработка списка сущностей, связанных с текущей страницей](render-entity-list-current-page.md)  
[Отображение до трех уровней иерархии страниц с помощью гибридной навигации](hybrid-navigation-render-page-hierachy.md)  

