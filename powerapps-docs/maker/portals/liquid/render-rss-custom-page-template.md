---
title: Подготовка RSS-канала с помощью пользовательского шаблона страницы для портала | MicrosoftDocs
description: Инструкции по созданию пользовательского шаблона страницы и его использованию для отображения RSS-канала.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 240af2f54e153490794358dc1598b72a16fe1c38
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543300"
---
# <a name="create-a-custom-page-template-to-render-an-rss-feed"></a>Создание пользовательского шаблона страницы для отображения RSS-канала
В этом примере мы создадим настраиваемый шаблон страницы для подготовки к просмотру [RSS-канала](https://en.wikipedia.org/wiki/RSS) новостей с использованием жидкостей и шаблона страницы веб-шаблона. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [хранения исходного содержимого с помощью веб-шаблонов](store-content-web-templates.md)  

## <a name="step-1-create-a-new-powerapps-view"></a>Шаг 1. Создание нового представления PowerApps

Сначала мы создадим новое представление PowerApps, которое будет использоваться для загрузки данных для нашего веб-канала. В этом примере мы сделаем его представлением на веб-страницах и используем эту сущность для хранения наших статей. С помощью этого представления можно настроить сортировку и фильтрацию результатов, а также включить в качестве столбцов атрибуты сущности, которые должны быть доступны в нашем шаблоне жидкости.

![Изменение шаблона страницы](../media/edit-page-template.png "Изменение шаблона страницы")  

## <a name="step-2-create-a-web-template-for-rss-feed"></a>Шаг 2. Создание веб-шаблона для канала RSS

На этом шаге мы создадим веб-шаблон для нашего канала RSS. Этот шаблон будет применен к конкретной веб-странице на нашем сайте, поэтому мы будем использовать заголовок и сводку этой страницы в качестве заголовка и описания канала. Мы будем использовать тег ентитивиев для загрузки только что созданного представления новостных статей. [теги сущности Common data service [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] PowerApps](portals-entity-tags.md). Обратите внимание, что для поля **типа MIME** веб-шаблона также задается значение Application/RSS + XML. Это указывает, что может быть типом содержимого ответа при подготовке к просмотру шаблона.  

![Настройка веб-шаблона для канала RSS](../media/web-template-rss-feed.png "Настройка веб-шаблона для канала RSS")  

### <a name="rss-feed-web-template"></a>Канал RSS (веб-шаблон)

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

## <a name="step-3-create-a-page-template-to-assign-rss-feed-template"></a>Шаг 3. Создание шаблона страницы для назначения шаблона RSS-канала

Теперь создадим новый шаблон страницы, чтобы мы смогли назначить шаблон RSS-канала любой веб-странице на нашем сайте. Обратите внимание, что мы **отменяем выбор верхнего и нижнего колонтитулов веб-сайта**, так как мы хотим выполнить визуализацию всего ответа страницы для нашего канала.

![Настройка шаблона страницы для RSS-канала](../media/page-template-rss-feed.png "Настройка шаблона страницы для RSS-канала")  

## <a name="step-4-create-a-web-page-to-host-rss-feed"></a>Шаг 4. Создание веб-страницы для размещения канала RSS

Теперь все, что осталось, — это создать веб-страницу с помощью шаблона канала RSS для размещения нашего канала. При запросе этой новой веб-страницы мы получаем XML-канал RSS:

![Пример RSS-канала](../media/rss-feed-example.png "Пример RSS-канала")  

В этом примере мы рассмотрели, как объединить в ликвидные, веб-шаблоны, представления PowerApps и функции управления содержимым порталов, чтобы создать пользовательский RSS-канал. Сочетание этих функций позволяет добавлять мощные возможности настройки в любое приложение портала.

### <a name="see-also"></a>См. также

[Создание пользовательского шаблона страницы с помощью жидкостного и шаблона страницы веб-шаблона](create-custom-template.md)  
[Отображение списка сущностей, связанного с текущей страницей](render-entity-list-current-page.md)  
[Отображение заголовка веб-сайта и основной панели навигации](render-site-header-primary-navigation.md)  
[Отображение до трех уровней иерархии страниц с помощью гибридной навигации](hybrid-navigation-render-page-hierachy.md)  

