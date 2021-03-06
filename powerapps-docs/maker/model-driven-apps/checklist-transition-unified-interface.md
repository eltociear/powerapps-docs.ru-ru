---
title: 'Контрольный список: переход на единый интерфейс | MicrosoftDocs'
description: Контрольный список, чтобы убедиться, что вы подготовлены для перехода на единый интерфейс.
ms.custom: ''
ms.date: 11/04/2019
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.author: haybass
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 20a64e12abc70e8c1b636ab5412e2a951b5ad612
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2019
ms.locfileid: "2869230"
---
# <a name="checklist-unified-interface-transition"></a>Контрольный список: переход на единый интерфейс

Выполните шаги в этой статье, чтобы убедиться, что вы подготовлены для перехода на единый интерфейс. Готовность к переходу на единый интерфейс будет зависеть от того, нацелены ли вы на базовую совместимость или на переработку для полного использования новых возможностей. Дополнительные сведения см. в документах [Сборник схем единого интерфейса](https://docs.microsoft.com/powerapps/maker/model-driven-apps/unified-interface-playbook) и [технический документ по работе с единым интерфейсом](https://docs.microsoft.com/powerapps/maker/model-driven-apps/approaching-unified-interface).

Инструкции применяются к следующим управляемым моделью приложениям в Dynamics 365:

- Dynamics 365 Sales

- Dynamics 365 Customer Service

- Dynamics 365 Field Service

- Dynamics 365 Project Service Automation

## <a name="run-the-power-apps-solution-checker-on-your-solutions"></a>Выполнение средства проверки решений Power Apps для решения

[Средство проверки решений Power Apps](https://docs.microsoft.com/powerapps/maker/common-data-service/use-powerapps-checker) выполняет широкий статический анализ ваших решений по набору правил оптимальной работы для быстрого выявления проблемных закономерностей. После завершения проверки вы получите подробный отчет со списком выявленных проблем, затронутыми компонентами и кодом, а также со ссылками на документацию, в которой описываются способы решения каждой проблемы.

Средство проверки решений анализирует этих компоненты решений:

-   Подключаемые модули Common Data Service

-   Действия настраиваемого рабочего процесса Common Data Service

-   Веб-ресурсы Common Data Service (HTML и JavaScript)

-   Конфигурации Common Data Service, такие как шаги сообщения пакета SDK

**Следует учесть...** 

-   Возможные проблемы, обнаруженные средством проверки решений, может относится не только к единому интерфейсу, помните о том, что повлияет на переход при рассмотрении результатов.

-   Как и при любой автоматизированной проверке кода, некоторые проблемы могут быть ложными тревогами и не означать, что приложении нельзя будет запустить в едином интерфейсе.

-   Логика, исполненная на стороне сервера, такая как подключаемые модули, настраиваемые действия бизнес-процессов и конфигурация шагов сообщений пакета SDK, не должны влиять на пользовательский интерфейс и, следовательно, не должны влиять на переход к единому интерфейсу.

-   Даже если все проблемы не связаны непосредственно с единым интерфейсом, рекомендуется затратить время на рассмотрение их, чтобы улучшить общую работоспособность приложения.

## <a name="check-third-party-solutions-compatibility-with-unified-interface"></a>Проверка совместимости решений сторонних производителей с единым интерфейсом


Перед переходом на единый интерфейс важно убедиться, что любое решение сторонних производителей, которое используется в вашем приложении, работает в едином интерфейсе.

-   Если установлены модули независимых поставщиков программного обеспечения (ISV) через [AppSource](https://appsource.microsoft.com), проверьте, нет ли доступных обновлений в [Центре администрирования Power Platform](https://admin.powerplatform.microsoft.com), выбрав **Среды** > [имя_среды] > **Управление решениями**.

-   Если вы используете решения сторонних разработчиков, которые были предоставлены не через AppSource, обратитесь к поставщику (партнеру или независимому поставщику программного обеспечения) для получения новой версии, которая обновляет приложения до единого интерфейса.

> [!NOTE]
> Если нет планов по обновлению решений сторонних разработчиков до версии, совместимой с единым интерфейсом, важно определить путь для замены этих возможностей либо собственными возможностями платформы, либо совместимыми альтернативными решениями.

## <a name="identify-replacements-for-deprecated-client-api-code-and-features"></a>Определение замены для устаревшего кода API и функций клиента

Исходя из выходных данных **средства проверки решений Power Apps** и сведений, содержащихся в документе [Важные изменения (устаревшие функции), которые ожидаются](https://docs.microsoft.com/power-platform/important-changes-coming) по устаревшим интерфейсам API и функциям клиента, необходимо иметь правильное понимание настроек и функций, которые должны быть исправлены или заменены в вашем проекте единого интерфейса.

Ниже приведены некоторые из наиболее общих областей, требующих внимания:

-   **API клиента**: рекомендуемые способы замены задокументированы [здесь](https://docs.microsoft.com/power-platform/important-changes-coming#some-client-apis-are-deprecated).

-   **Диалоги процесса**: рекомендуемые для замены диалогов задокументированы [здесь](https://docs.microsoft.com/flow/replace-dialogs).

-   **Потоки задач**: используйте [Последовательности операций бизнес-процесса](https://docs.microsoft.com/power-platform-release-plan/2019wave2/microsoft-flow/business-process-immersive-experiences) для замены потоков задач.

-   **Планирование сервиса**: используйте [Universal Resource Scheduling](https://docs.microsoft.com/dynamics365/common-scheduler/schedule-anything-with-universal-resource-scheduling) для замены старого планирования сервиса.

> [!NOTE]
> Можно также рассмотреть замену Dynamics 365 for Outlook (надстройка COM) на облегченное приложение [Dynamics 365 App for Outlook](https://docs.microsoft.com/dynamics365/outlook-app/overview).

## <a name="test-your-application-in-unified-interface"></a>Тестирование приложения в едином интерфейсе

Один из самых простых способов протестировать приложение в едином интерфейсе — это включить параметр [**Включить только единый интерфейс**](https://docs.microsoft.com/power-platform/admin/enable-unified-interface-only) в копии производственной среды. После включения единого интерфейса у вас должна быть возможность получить доступ к приложению с помощью приложения **Dynamics 365 – Custom** и протестировать варианты использования, относящиеся к вашему контексту.

### <a name="test-your-business-and-technical-scenarios"></a>Тестирование бизнес-сценариев и технических сценариев

Фокус на то, что может быть потенциально затронуто:

-   **Бизнес-процессы**, такие как последовательности операций бизнес-процесса, бизнес-правила

-   **Настройки**, такие как формы, представления, кнопки панели команд, веб-ресурсы и диаграммы

> [!TIP]
> Проверка взаимодействия пользователей одновременно с выполнением этих предварительных тестов: все ли понятно и добавляет ценность? Что должно быть удалено, улучшено или добавлено? Например, уместен ли текущий список представлений? Или моим пользователям приходится создавать собственные представления?

### <a name="identify-gaps"></a>Выявление недостающих элементов

-   Все возможные регрессии, которые не были обнаружены средством проверки решений и обновлениями решений сторонних производителей.

-   Проблемные вопросы пользователя, которые могут привести к оптимизациям (например, новое отображение формы с переработанными разделами и вкладками) или определенному обучению.

-   Все остальные зависимости в старом веб-клиенте, такие как использование старой настройки Outlook COM вместо облегченного приложения Dynamics 365 App for Outlook.

## <a name="define-your-app-strategy-and-settings"></a>Определение стратегии и параметров приложения

Вместо использования приложения **Dynamics 365 – Custom**, которое не оптимизировано для единого интерфейса и запускается в режиме совместимости, рекомендуется использовать приложения от первого лица, созданные Майкрософт, или создать собственные приложения.

Приложения Dynamics 365 от первого лица, которые уже были оптимизированы для единого интерфейса, следующие:

-   Центр продаж Dynamics 365

-   Центр обслуживания клиентов Dynamics 365

-   Dynamics 365 Marketing

-   Dynamics 365 Field Service (версия 8.x и новее)

-   Dynamics 365 Project Service Automation (версия 3.x и новее)

### <a name="what-are-model-driven-apps"></a>Что такое приложения на основе модели?

**Управляемые моделью приложения** — это тип приложения, которое можно создать с помощью Power Apps, который помогает предоставлять настроенное взаимодействие пользователям в зависимости от их роли в организации. Например, продавец может иметь совершенно другое взаимодействие, чем представитель по обслуживанию клиентов, с помощью различных управляемых моделью приложений, даже если они используют данные из одной и той же среды. Несколько управляемых моделью приложений можно создавать в среде Common Data Service. Дополнительные сведения: [Что такое управляемые моделью приложения?](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview)

Приложения Dynamics 365 от первого лица, перечисленные ранее, являются примерами управляемых моделью приложений.

### <a name="how-to-define-your-app-strategy"></a>Как определить стратегию приложения?

Ответьте на следующие вопросы:

1.  Вы можете разделить пользователей на несколько групп в определенных бизнес-процессах?

2.  Эти группы имеют разные требования к тому, что они должны видеть и делать?

3.  Для вас трудно обеспечить различное взаимодействие пользователей без использования приложений?

Если вы ответили на эти вопросы "Да", рассмотрите возможность поддержки нескольких приложений.

Это возможность переосмыслить взаимодействие в контексте бизнес-процессов для каждой группы или роли.

### <a name="out-of-the-box-apps-for-example-sales-hub-or-customized-apps"></a>Готовые приложения (например, Центр продаж) или настраиваемые приложения?

-   Это зависит от того, насколько настроенным должно был взаимодействие.

-   Если имеется несколько настроек или вы хотите получать преимущества от обновлений от первого лица, рассмотрите возможность использовать исходные приложения.

-   Если нужно больше контроля над взаимодействием и обновлением стандартных приложений и настроек, то создавайте собственные приложения.

### <a name="once-you-have-defined-your-app-strategy-what-should-be-the-next-steps"></a>Что должно быть следующими действиями после определения стратегии приложения?

1.  Настройте целевые приложения и включите только то, что пользователям необходимо. Чем меньше, тем лучше. Сократите лишнее, чтобы пользователи могли эффективно работать.

2.  Уберите роли безопасности из неиспользуемых приложений.

## <a name="review-your-apps-settings-and-user-experience-fundamentals"></a>Проверка параметров приложений и принципов взаимодействия пользователей

### <a name="app-settings"></a>Параметры приложения

-   Включите все требуемые сущности в ваше приложение, даже если они отсутствуют на карте сайта.  
    
-   Предоставьте привилегию **Чтение** для **Приложение на основе модели** на вкладке **Настройка** в диалоговом окне **Роль безопасности**.

-   Включите режим **Только единый интерфейс**, если пользователям не требуется использовать старый веб-клиент. Вы по-прежнему можете получить доступ к функциям администрирования, выбрав **Параметры** > **Дополнительные параметры**.

-   Создайте более простой URL-адрес приложения. Например: https://\*.crm.dynamics.com/apps/MyApp*

-   Попробуйте ограничить число приложений, к которым пользователь может получить доступ.  
    
    > [!TIP]
    > Когда для параметра **Использовать только единый интерфейс** задано значение **Да** и пользователи имеют доступ только к одному приложению, они автоматически перенаправляются на приложение, когда получают доступ к корневому URL-адресу (https://\*.crm.dynamics.com)*

### <a name="optimize-navigation-sitemap"></a>Оптимизация навигации (карта сайта)

-   Определите одну главную **область** с самыми используемыми **подобластями** (панель мониторинга, сущности и т. д.), организованными в **группы**

-   Создайте одну или несколько дополнительных областей для менее используемых функций (конфигурация, параметры и т. д.). Идея в том, чтобы помочь пользователям сосредоточиться только на том, что важно для их работы.

### <a name="update-icons"></a>Обновление значков

-   Перевод на единый интерфейс — хорошая возможность обновить значки.

-   Рекомендуется формат **SVG**, так как он хорошо отображается независимо от разрешения экрана.

    > [!TIP]
    > Пример значка в формате SVG:  
    > Ширина и высота: 16px; Заполнение: 0px; Фон: прозрачный; Цвет значка: \#FF000000  
    Чтобы избежать проблем отображения, откройте файл SVG в редакторе (например, в Блокноте) и fill="\#000000"

## <a name="enrich-your-app-with-unified-interface-exclusive-features"></a>Обогащение приложения с эксклюзивными функциями единого интерфейса

-   Создайте страницу **Страница приветствия**, которую пользователи видят, когда они получают доступ к каждому приложению. Это замечательная возможность направлять пользователей на начальных этапах.

-   Используйте существующие **настраиваемые элементы управления**, чтобы повысить удобство использования большинства типов полей, особенно на мобильных устройствах. Например, замените поле оценки от 0 до 5 звездочками, замените представление встреч представлением календаря, замените представление вложенной сетки на формы карточек.

-   Используйте **Справочные панели** в формах для связывания несколько представлений, быстрых представлений и функции поиска в базе значений в одном месте.

-   Используйте [Power Apps Component Framework](https://docs.microsoft.com/powerapps/developer/component-framework/overview) для добавления даже большего числа настраиваемых элементов управления. Можно получить некоторые от сообщества или от партнеров и независимых поставщиков программных продуктов.

-   Внедрите [приложения холста](https://docs.microsoft.com/powerapps/maker/canvas-apps/getting-started) в формы, чтобы легко расширить возможности приложения. Расширение приложения без кода или с малым количеством кода без необходимости разработки настраиваемых веб-ресурсов HTML/JS.

-   Внедрите отчеты и плитки **Power BI** в формы: консолидируйте данные из нескольких систем в одном представлении.

-   Рассмотрите использование **интерактивных панелей мониторинга** для настройки универсального рабочего места, которое позволяет глобальную фильтрацию между компонентами панели мониторинга.

-   Настройте **панели настраиваемой справки и управляемые задачи** таким образом, чтобы пользователи быстро получат справку и указания.

## <a name="conduct-user-acceptance-testing"></a>Выполните приемочное тестирование пользователями

Очень важно, чтобы приложения, бизнес-сценарии и технические сценарии были протестированы бизнес-пользователями в едином интерфейсе в условиях, которые схожи с производственной средой. Эти пользователи могут действовать как бизнес-чемпионы, что масштабировать знания во всем бизнесе.

Тестирование поможет определить оставшиеся вопросы, которые требуется разрешить перед переводом всех пользователей на единый интерфейс.

## <a name="update-user-training-materials"></a>Обновление учебных материалов пользователей

Выполите проверку существующих и планируемых учебных материалов для обеспечения того, чтобы они содержали новейшие снимки экраном и отражали все изменения, внесенные в последовательность работы пользователей.

## <a name="check-your-transition-date"></a>Проверьте дату перехода

С 1-го октября 2020 г. [старый веб-клиент станет недоступен](https://docs.microsoft.com/power-platform/important-changes-coming#legacy-web-client-is-deprecated).
Необходимо заранее выполнить переход для обеспечения достаточного времени для устранения всех возможных проблем.
