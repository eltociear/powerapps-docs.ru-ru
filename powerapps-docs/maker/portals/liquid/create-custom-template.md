---
title: Создание настраиваемого шаблона страницы с помощью Liquid и шаблона страницы "Веб-шаблон" для портала | Документация Майкрософт
description: Инструкции по созданию настраиваемого шаблона страницы с помощью операторов Liquid.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="create-a-custom-page-template"></a>Создание пользовательского шаблона страницы

В этом примере мы создадим настраиваемый шаблон страницы с помощью Liquid и шаблона страницы, который основан на веб-шаблоне. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Сохранение содержимого источника с помощью веб-шаблонов](store-content-web-templates.md) Наша цель — создать простой шаблон с двумя колонками, использующий [набор веб-ссылок](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/manage-web-links) для навигации с левой стороны и с содержимым страницы справа. 

## <a name="step-1-create-a-web-template-and-write-the-liquid-template-code"></a>Шаг 1. Создание веб-шаблона и написание кода шаблона Liquid.

Сначала мы создадим веб-шаблон и напишем код шаблона Liquid. Вероятно, некоторые общие элементы этого шаблона будут повторно использоваться в будущих шаблонах. Поэтому мы создадим общий базовый шаблон, который мы затем расширим с помощью нашего конкретного шаблона. Наш базовый шаблон будет предоставлять ссылки навигационной цепочки и заголовок/верхний колонтитул нашей страницы, а также определять наш макет с одной колонкой:

> [!div class=mx-imgBorder]
![Веб-шаблон с макетом с одной колонкой](../media/web-template-two-column-layout.png "Веб-шаблон с макетом с одной колонкой")

> [!TIP]
> Прочитайте о наследовании шаблона с помощью тегов block и extends: [Теги шаблона](template-tags.md#extends)

### <a name="two-column-layout-web-template"></a>Макет с двумя столбцами (веб-шаблон)

```xml
<div class=container>
  <div class=page-heading>
    <ul class=breadcrumb>
      {% for crumb in page.breadcrumbs -%}
        <li>
          <a href={{ crumb.url }}>{{ crumb.title }}</a>
        </li>
      {% endfor -%}
      <li class=active>{{ page.title }}</li>
    </ul>
    <div class=page-header>
      <h1>{{ page.title }}</h1>
    </div>
  </div>
  <div class=row>
    <div class=col-sm-4 col-lg-3>
      {% block sidebar %}{% endblock %}
    </div>
    <div class=col-sm-8 col-lg-9>
      {% block content %}{% endblock %}
    </div>
  </div>
</div>
```

## <a name="step-2-create-a-new-web-template-that-extends-our-base-layout-template"></a>Шаг 2. Создание нового веб-шаблона, который расширяет наш базовый шаблон макета

С помощью набора веб-ссылок навигации, связанного с текущей страницей для наших ссылок навигации создайте новый веб-шаблон, расширяющий наш базовый шаблон макета.

> [!div class=mx-imgBorder]
![Веб-шаблон с веб-ссылками на левой навигационной панели макета](../media/web-template-weblinks-left-navigation-layout.png "Веб-шаблон с веб-ссылками на левой навигационной панели макета")  

> [!TIP]
> Ознакомьтесь с тем, как загружать наборы веб-ссылок с помощью объекта ["веб-ссылки"](liquid-objects.md#weblinks).

### <a name="weblinks-left-navigation-web-template"></a>Веб-ссылки на левой навигационной панели (веб-шаблон)

```xml
{% extends 'Two Column Layout' %}

{% block sidebar %}
  {% assign weblinkset_id = page.adx_navigation.id %}
  {% if weblinkset_id %}
    {% assign nav = weblinks[page.adx_navigation.id] %}
    {% if nav %}
      <div class=list-group>
        {% for link in nav.weblinks %}
          <a class=list-group-item href={{ link.url }}>
            {{ link.name }}
          </a>
        {% endfor %}
      </div>
    {% endif %}
  {% endif %}
{% endblock %}

{% block content %}
  <div class=page-copy>
    {{ page.adx_copy }}
  </div>
{% endblock %}
```

## <a name="step-3-create-a-new-page-template-based-on-the-web-template"></a>Шаг 3. Создание шаблона страницы на основе веб-шаблона

На этом этапе мы создадим новый шаблон страницы, который основан на веб-шаблоне, созданном на предыдущем шаге.

> [!div class=mx-imgBorder]
![Шаблон страницы с веб-ссылками на левой навигационной панели макета](../media/page-template-weblinks-left-navigation-layout.png "Шаблон страницы с веб-ссылками на левой навигационной панели макета")  

## <a name="step-4-create-a-web-page-to-display-content"></a>Шаг 4. Создание веб-страницы для отображения содержимого

Теперь для получения конечного результата нам осталось только создать веб-страницу, использующую наш шаблон страницы и имеющую связанный набор веб-ссылок.

> [!div class=mx-imgBorder]
![Веб-страница с левой область навигации](../media/web-page-left-navigation.png "Веб-страница с левой область навигации")  

### <a name="see-also"></a>См. также

[Создание настраиваемого шаблона страницы для отображения RSS-канала](render-rss-custom-page-template.md)  
[Обработка списка сущностей, связанных с текущей страницей](render-entity-list-current-page.md)  
[Отображение заголовка веб-сайта и основной навигационной панели](render-site-header-primary-navigation.md)  
[Отображение до трех уровней иерархии страниц с помощью гибридной навигации](hybrid-navigation-render-page-hierachy.md)  

