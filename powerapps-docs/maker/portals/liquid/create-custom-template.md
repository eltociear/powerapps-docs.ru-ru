---
title: Создание пользовательского шаблона страницы с помощью жидкостного и шаблона страницы веб-шаблона для портала | MicrosoftDocs
description: Инструкции по созданию пользовательского шаблона страницы с помощью операторов жидкости.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 7717bd75fe7149ea3b0af957055975ad10e752ae
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975065"
---
# <a name="create-a-custom-page-template"></a>Создание пользовательского шаблона страницы

В этом примере мы создадим пользовательский шаблон страницы, используя жидкость и шаблон страницы, основанный на веб-шаблоне. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [хранения исходного содержимого с помощью веб-шаблонов](store-content-web-templates.md). Нашей целью является создание простого шаблона с двумя столбцами, который использует [набор веб-ссылок](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/manage-web-links) в качестве левой навигации с содержимым страницы справа. 

## <a name="step-1-create-a-web-template-and-write-the-liquid-template-code"></a>Шаг 1. Создание веб-шаблона и написание кода шаблона жидкости

Сначала мы создадим наш веб-шаблон и запишем код шаблона жидкости. Скорее всего, мы будем использовать некоторые распространенные элементы этого шаблона в будущих шаблонах. Итак, мы создадим общий базовый шаблон, который затем будет расширяться с помощью нашего конкретного шаблона. Наш базовый шаблон будет предоставлять ссылки на строки, заголовок и заголовок страницы, а также определять наш макет с одним столбцом:

> [!div class=mx-imgBorder]
![Шаблон веб-шаблона макет одного столбца]макет(../media/web-template-two-column-layout.png "одного столбца")

> [!TIP]
> Дополнительные сведения о наследовании шаблонов с помощью тегов Block и extends см. в статье [Теги шаблона](template-tags.md#extends) .

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

## <a name="step-2-create-a-new-web-template-that-extends-our-base-layout-template"></a>Шаг 2. Создание нового веб-шаблона, расширяющего основной шаблон макета

Используйте набор веб-ссылок навигации, связанный с текущей страницей, для наших навигационных ссылок, чтобы создать новый веб-шаблон, расширяющий базовый шаблон макета.

> [!div class=mx-imgBorder]
Web ![template веб-ссылки структура левой структуры навигации]веб-(../media/web-template-weblinks-left-navigation-layout.png "шаблон гиперссылка структура навигации слева")  

> [!TIP]
> Ознакомьтесь с инструкциями по загрузке наборов веб-ссылок с помощью объекта [Links](liquid-objects.md#weblinks) .

### <a name="weblinks-left-navigation-web-template"></a>Левая навигационная Навигация по гиперссылкам (веб-шаблон)

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

## <a name="step-3-create-a-new-page-template-based-on-the-web-template"></a>Шаг 3. Создание нового шаблона страницы на основе веб-шаблона

На этом шаге мы создадим новый шаблон страницы на основе веб-шаблона, созданного на предыдущем шаге.

> [!div class=mx-imgBorder]
![Веб-ссылки шаблона страницы макет левой панели навигации](../media/page-template-weblinks-left-navigation-layout.png "веб-ссылки шаблон левая структура навигации")  

## <a name="step-4-create-a-web-page-to-display-content"></a>Шаг 4. Создание веб-страницы для просмотра содержимого

Теперь осталось только создать веб-страницу, использующую наш шаблон страницы и имеющую связанный набор веб-ссылок, и наш результат.

> [!div class=mx-imgBorder]
![Веб-страница с левой навигацией](../media/web-page-left-navigation.png "на веб-странице с левой навигацией")  

### <a name="see-also"></a>См. также

[Создание пользовательского шаблона страницы для отображения RSS-канала](render-rss-custom-page-template.md)  
[Отображение списка сущностей, связанного с текущей страницей](render-entity-list-current-page.md)  
[Отображение заголовка веб-сайта и основной панели навигации](render-site-header-primary-navigation.md)  
[Отображение до трех уровней иерархии страниц с помощью гибридной навигации](hybrid-navigation-render-page-hierachy.md)  

