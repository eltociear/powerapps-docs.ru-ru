---
title: Отображение RSS-канала с использованием настраиваемого шаблона страницы для портала | MicrosoftDocs
description: Инструкции по созданию настраиваемого шаблона страницы и использованию его для отображения RSS-канала.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: d2c4956bd6d5e1a15e6308b4e40442ef15502178
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2020
ms.locfileid: "2981024"
---
# <a name="create-a-custom-page-template-to-render-an-rss-feed"></a>Создание настраиваемого шаблона страницы для отображения RSS-канала
В данном примере мы создадим настраиваемый шаблон страницы для отображения новостных статей [RSS-канала](https://en.wikipedia.org/wiki/RSS), используя Liquid и шаблон страницы веб-шаблона. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Сохранение содержимого источника с помощью веб-шаблонов](store-content-web-templates.md).  

## <a name="step-1-create-a-new-power-apps-view"></a>Шаг 1: Создать новое представление Power Apps

Во-первых, мы создадим новое представление Power Apps, которое будем использовать для загрузки данных для нашего веб-канала. В этом примере мы сделаем его представлением на веб-страницах и будем использовать эту сущность для хранения наших статей. Мы можем использовать это представление для настройки сортировки и фильтрации результатов, и можем включить в виде столбцов атрибуты сущности, которые должны быть доступны в нашем шаблоне Liquid.

![Изменение шаблона страницы](../media/edit-page-template.png "Изменение шаблона страницы")  

## <a name="step-2-create-a-web-template-for-rss-feed"></a>Шаг 2. Создание веб-шаблона для RSS-канала

На этом шаге мы создадим веб-шаблон для нашего RSS-канала. Этот шаблон будет применен к определенной веб-странице на нашем веб-сайте, поэтому мы будем использовать заголовок и сводку этой страницы в качестве заголовка и описания веб-канала. Затем мы используем тег entityview для загрузки нашего только что созданного представления новостных статей. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [теги сущности Common Data Service Power Apps](portals-entity-tags.md). Обратите внимание, что мы также устанавливаем в поле **Тип MIME** веб-шаблона значение application/rss+xml. Это указывает, каким может быть тип содержимого отклика при отображении нашего шаблона.  

![Настройка веб-шаблона для RSS-канала](../media/web-template-rss-feed.png "Настройка веб-шаблона для RSS-канала")  

### <a name="rss-feed-web-template"></a>RSS-канал (веб-шаблон)

```xml
<?xml version=1.0 encoding=UTF-8 ?>
<rss version=2.0>
  <channel>
    <title>{{ page.title | xml_escape }}</title>
    <description>{{ page.description | strip_html | xml_escape }}</description>
    <link>{{ request.url | xml_escape }}</link>
    {% entityview logical_name:'adx_webpage', name:'News Articles', page_size:20 -%}
      {% for item in entityview.records %}
        <item>
          <title>{{ item.adx_name | xml_escape }}</title>
          <description>{{ item.adx_copy | escape }}</description>
          <link>{{ request.url | base | xml_escape }}{{ item.url | xml_escape }}</link>
          <guid>{{ item.id | xml_escape }}</guid>
          <pubDate>{{ item.createdon | date_to_rfc822 }}</pubDate>
        </item>
      {% endfor -%}
    {% endentityview %}
  </channel>
</rss>
```

## <a name="step-3-create-a-page-template-to-assign-rss-feed-template"></a>Шаг 3. Создание шаблона страницы для назначения шаблону RSS-канала

Сейчас мы создадим новый шаблон страницы, что позволит назначить наш шаблон RSS-канала любой веб-странице нашего веб-сайта. Обратите внимание, что мы снимаем флажок **Использовать верхний и нижний колонтитулы веб-сайта**, так как нам нужно перехватить отображение отклика на всей странице для нашего веб-канала.

![Настройка шаблона страницы для RSS-канала](../media/page-template-rss-feed.png "Настройка шаблона страницы для RSS-канала")  

## <a name="step-4-create-a-web-page-to-host-rss-feed"></a>Шаг 4. Создание веб-страницы для размещения RSS-канала

Теперь осталось только создать новую веб-страницу с использованием шаблона RSS-канала для размещения канала. Когда мы запросим эту новую веб-страницу, мы получим XML-код RSS-канала:

![Пример RSS-канала](../media/rss-feed-example.png "Пример RSS-канала")  

В данном примере мы посмотрели, как можно объединять Liquid, веб-шаблоны, представления Power Apps и функции управления содержимом порталов CRM для создания настраиваемого RSS-канала. Сочетание этих функций добавляет мощные возможности настройки в любое портальное приложение.

### <a name="see-also"></a>См. также

[Создание настраиваемого шаблона страницы с помощью Liquid и шаблона страницы "Веб-шаблон"](create-custom-template.md)  
[Обработка списка сущностей, связанных с текущей страницей](render-entity-list-current-page.md)  
[Отображение заголовка веб-сайта и основной навигационной панели](render-site-header-primary-navigation.md)  
[Отображение до трех уровней иерархии страниц с помощью гибридной навигации](hybrid-navigation-render-page-hierachy.md)  

