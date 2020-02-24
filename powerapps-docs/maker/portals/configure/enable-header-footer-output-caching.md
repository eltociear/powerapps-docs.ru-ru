---
title: Включение кэширования выходных данных верхнего и нижнего колонтитулов на портале | MicrosoftDocs
description: Инструкции по включению кэширования выходных данных верхнего и нижнего колонтитулов на портале для существующих пользователей.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/11/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: e7a112c722e284f9060696d0fac5a3389b47b0d3
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977108"
---
# <a name="enable-header-and-footer-output-caching-on-a-portal"></a>Включение кэширования выходных данных верхнего и нижнего колонтитулов на портале

Для повышения эффективности обработки веб-шаблонов верхнего и нижнего колонтитулов на портале включите кэширование выходных данных верхнего и нижнего колонтитулов. Веб-шаблоны верхнего и нижнего колонтитулов анализируются и отрисовываются при каждой загрузке страницы. Кэширования выходных данных верхнего и нижнего колонтитулов значительно сокращает время обработки страницы.

Для нового пользователя кэширование выходных данных включено по умолчанию. Следующие параметры сайта доступны и имеют значение true по умолчанию для поддержки этой функции:
- Header/OutputCache/Enabled: установите значение true для включения кэширования выходных данных верхнего колонтитула.
- Footer/OutputCache/Enabled: установите значение true для включения кэширования выходных данных нижнего колонтитула.

Для пользователя, который обновился до новой версии порталов, кэширование выходных данных отключено по умолчанию &mdash; то есть веб-шаблоны верхнего и нижнего колонтитулов анализируются и отрисовываются при каждой загрузке страницы. Чтобы включить кэширования выходных данных, необходимо обновить веб-шаблоны "Верхний колонтитул", "Нижний колонтитул" и "Раскрывающийся список языков" и создать необходимые параметры сайта.

> [!Note]
> При включении кэширования выходных данных только путем создания параметров сайта части верхнего и нижнего колонтитулов будут отрисовываться неверно, и отобразятся сообщения об ошибках.

### <a name="enable-header-and-footer-output-caching-for-an-existing-user"></a>Включение кэширования выходных данных верхнего и нижнего колонтитулов для существующего пользователя

**Шаг 1. Обновление веб-шаблона "Верхний колонтитул"**

1. Откройте [Приложение управления порталом](configure-portal.md).
2. Откройте **Порталы** > **Веб-шаблоны**.
3. Откройте веб-шаблон "Верхний колонтитул".
4. В поле **Источник** выполните следующие действия:
    - Найдите следующий код и обновите его:
    
        **Существующий код**

        ```
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}/Account/Login/LogOff?returnUrl={{ request.raw_url_encode | escape }} title={{ snippets[links/logout] | default:resx[Sign_Out] | escape }}>
            {{ snippets[links/logout] | default:resx[Sign_Out] | escape }}
            </a>
        </li>
        </ul>
        </li>
        {% else %}
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}/SignIn?returnUrl={{ request.raw_url_encode }}>
            {{ snippets[links/login] | default:resx[Sign_In] }}
            </a>
        </li>
        ```
        
        **Обновленный код**

         ```
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}{{ website.sign_out_url_substitution }} title={{ snippets[links/logout] | default:resx[Sign_Out] | escape }}>
            {{ snippets[links/logout] | default:resx[Sign_Out] | escape }}
            </a>
        </li>
        </ul>
        </li>
        {% else %}
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}{{ website.sign_in_url_substitution }}>
            {{ snippets[links/login] | default:resx[Sign_In] }}
            </a>
        </li>
        ```
    - Найдите следующий код и обновите его:

        **Существующий код**
        ```
        {% assign current_page = page.adx_partialurl %}
        {% assign sr_page = sitemarkers[Search].url | remove: '/' %}
        {% assign forum_page = sitemarkers[Forums].url | remove: '/' %}
        {% if current_page == sr_page or current_page == forum_page %}
          <section class=page_section section-landing-{{ current_page }} color-inverse>
            <div class=container>
              <div class=row >
                <div class=col-md-12 text-center>
                  {% if current_page == sr_page %}
                    <h1 class=section-landing-heading>{% editable snippets 'Search/Title' default: resx['Discover_Contoso'] %}</h1>
                    {% include 'Search' %}
                  {% endif %}
                </div>
              </div>
            </div>
          </section>
        {% endif %}
        ```

        **Обновленный код**

        ```
        {% substitution %}
          {% assign current_page = page.id %}
          {% assign sr_page = sitemarkers[Search].id %}
          {% assign forum_page = sitemarkers[Forums].id %}
          {% if current_page == sr_page or current_page == forum_page %}
            {% assign section_class = section-landing-search %}
            {% if current_page == forum_page %}
              {% assign section_class = section-landing-forums %}
            {% endif %}
           <section class=page_section section-landing-{{ current_page }} {{ section_class | h }} color-inverse>
              <div class=container>
                <div class=row >
                  <div class=col-md-12 text-center>
                    {% if current_page == sr_page %}
                      <h1 class=section-landing-heading>{% editable snippets 'Search/Title' default: resx['Discover_Contoso'] %}</h1>
                      {% include 'Search' %}
                    {% endif %}
                  </div>
                </div>
              </div>
            </section>
          {% endif %}
        {% endsubstitution %}
        ```

5. Сохраните веб-шаблон.

**Шаг 2. Обновление веб-шаблона "Нижний колонтитул"**

1. Откройте [Приложение управления порталом](configure-portal.md).
2. Откройте **Порталы** > **Веб-шаблоны**.
3. Откройте веб-шаблон "Нижний колонтитул".
4. В поле **Источник** найдите следующий код и обновите его:
    
    **Существующий код**
    
    ```
    <section id=gethelp class=page_section section-diagonal-right color-inverse {% if page %}{% unless page.parent %}home-section{% endunless %}{% endif %} hidden-print>
    ```

    **Обновленный код**

    ```
    <section id=gethelp class=page_section section-diagonal-right color-inverse {% substitution %}{% if page %}{% unless page.parent %}home-section{% endunless %}{% endif %}{% endsubstitution %} hidden-print>
    ```

5. Сохраните веб-шаблон.

**Шаг 3. Обновление веб-шаблона "Раскрывающийся список языков"**

1. Откройте [Приложение управления порталом](configure-portal.md).
2. Откройте **Порталы** > **Веб-шаблоны**.
3. Откройте веб-шаблон "Раскрывающийся список языков".
4. В поле **Источник** найдите следующий код и обновите его:
    
    **Существующий код**

    ```
    <a href=/{{ language.url }} title={{ language.name }} data-code={{ language.code }}>{{ language.name }}</a>
    ```

    **Обновленный код**

    ```
    <a href=/{{ language.url_substitution }} title={{ language.name }} data-code={{ language.code }}>{{ language.name }}</a>
    ```

5. Сохраните веб-шаблон.

**Шаг 4. Создание параметров сайта**

Создайте следующие параметры сайта:

|Полное имя|Значение|
|----|-----|
|Header/OutputCache/Enabled|True|
|Footer/OutputCache/Enabled|True|
|||
