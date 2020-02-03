---
title: Выпуск обновлений для порталов Power Apps | Документация Майкрософт
description: Узнайте об обновлениях выпуска порталов Power Apps.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/22/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: bbdc9a775c4bfaacc6f99217f6f24ce32db06bca
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "2884488"
---
# <a name="release-updates"></a>Обновления выпуска

В этой теме даны ресурсы, где вы можете узнать о недавно выпущенных функциях и новых функциях, которые будут выпущены в течение следующих нескольких месяцев.

## <a name="power-apps-portals-updates"></a>Обновления порталов Power Apps

Для получения информации о новых функциях, выпускаемых в течение следующих нескольких месяцев, которую вы можете использовать для планирования, см.:

- [План волны 2 выпуска за 2019 год](https://docs.microsoft.com/power-platform-release-plan/2019wave2/microsoft-powerapps/planned-features#portal-capabilities-for-power-apps)

## <a name="previous-portal-updates"></a>Предыдущие обновления портала

Вот список функций, добавленных для порталов Dynamics 365. Дополнительные сведения об обновлениях порталов Dynamics 365 на текущую дату см. в разделе [Возможности порталов для выпусков Microsoft Dynamics 365](https://support.microsoft.com/help/3181191).

> [!NOTE]
> Порталы Power Apps раньше назывались порталами Dynamics 365.

### <a name="dynamics-365-portals-version-914-for-the-model-driven-apps-in-dynamics-365"></a>Порталы Dynamics 365 версии 9.1.4 для приложений на основе модели в Dynamics 365

Порталы Dynamics 365 версии 9.1.4 для приложений на основе модели в Dynamics 365 содержат эти новые обновления и функции:

- **Режим обслуживания для портала**: как администратор портала, вы можете теперь настроить портал для отображения правильного сообщения для клиентов, когда выполняются действия по обслуживанию — например, выполняется обновление пакетов решений. Дополнительные сведения: [Режим обслуживания для портала](admin/enable-maintenance-mode.md)

- **Включение службы Power BI Embedded**: как настройщик портала, вы теперь можете внедрять панели мониторинга и отчеты, созданные в новой рабочей области Power BI, включив службу Power BI Embedded. Панели мониторинга и отчеты внедряются на веб-страницы на портале с помощью Liquid-тега powerbi. Дополнительные сведения: [Настройка интеграции Power BI](admin/set-up-power-bi-integration.md#enable-power-bi-embedded-service)

- **Включение модерирования содержимого идей**: как администратор портала, вы теперь можете создать политику модерирования содержимого, чтобы модерировать идеи, отправленные на ваш портал.

- **Последовательность операций неявного предоставления разрешений OAuth 2.0**: как разработчик портала, вы теперь можете делать вызовы API со стороны клиента и защищать их с помощью последовательности операций неявного предоставления разрешений OAuth 2.0. Дополнительные сведения: [Последовательность операций неявного предоставления разрешений OAuth 2.0](oauth-implicit-grant-flow.md)

- **Начальный портал Common Data Service (предварительная версия)**: как администратор портала, вы теперь можете настроить ваш портал для подключения к среде Common Data Service и разрешить вашим пользователям взаимодействовать с ним. Эта функция обеспечивает возможность подключить портал к среде Common Data Service, которая не содержит никаких предустановленных приложений на основе модели в Dynamics 365 (Dynamics 365 Sales, Dynamics 365 Service или Dynamics 365 Marketing).

### <a name="dynamics-365-portals-version-911-for-the-model-driven-apps-in-dynamics-365"></a>Порталы Dynamics 365 версии 9.1.1 для приложений на основе модели в Dynamics 365

Порталы Dynamics 365 версии 9.1.1 для приложений на основе модели в Dynamics 365 содержат эти новые обновления и функции:

- **Средство проверки порталов**: теперь можно использовать средство проверки порталов, чтобы обнаруживать проблемы с порталом, проверяя различные параметры конфигурации и приводя предложения о том, как их исправить. Дополнительные сведения: [Средство проверки порталов](admin/portal-checker.md)

### <a name="dynamics-365-portals-version-9010-for-the-model-driven-apps-in-dynamics-365"></a>Порталы Dynamics 365 версии 9.0.10 для приложений на основе модели в Dynamics 365

Порталы Dynamics 365 версии 9.0.10 для приложений на основе модели в Dynamics 365 содержат эти новые обновления и функции:

- **Миграция конфигурации порталов Dynamics 365**: теперь вы можете перенести свою конфигурацию порталов Dynamics 365 из среды разработки в среду тестирования или рабочую среду. Перенос данных включает в себя экспорт существующих данных конфигурации из исходного экземпляра Dynamics 365 последующий их импорт в целевой экземпляр Dynamics 365. Для миграции данных конфигурации понадобится использовать средство миграции конфигурации и файл схемы конфигурации, зависящий от портала. Дополнительные сведения: [Перенос конфигурации порталов Dynamics 365](admin/migrate-portal-configuration.md)

- **Добавление визуализации Power BI**: при настройке портала вы теперь можете внедрять визуализации Power BI (панель мониторинга, отчеты и плитки) на веб-страницы портала с помощью Liquid-тега powerbi. Дополнительные сведения: [Настройка интеграции Power BI](admin/set-up-power-bi-integration.md)

- **Ограничение доступа к порталу по IP-адресу**: администратор портала теперь может задать список IP-адресов, которым разрешен доступ к порталу. Если запрос на доступ к порталу создается пользователем, его IP-адрес оценивается в соответствии со списком разрешенных адресов. Если IP-адреса нет в списке, на портале отображается веб-страница с кодом состояния HTTP 403. Дополнительные сведения: [Ограничение доступа к порталу по IP-адресу](admin/ip-address-restrict.md)

- **Управление документами SharePoint**: порталы Dynamics 365 теперь поддерживают отправку и отображение документов SharePoint непосредственно в форме сущности или веб-форме на портале. Это позволит пользователям портала просматривать, загружать, добавлять и удалять документы на портале. Пользователи портала также могут создавать папки для организации документов. Дополнительные сведения: [Управление документами SharePoint](manage-sharepoint-documents.md).

- **Новый редактор содержимого портала (предварительная версия)**: в этой предварительной версии специалистам по настройке порталов Dynamics 365 доступен новый, упрощенный редактор портала, который поможет быстрее освоить настройку порталов Dynamics 365 и повысить продуктивность работы специалиста по настройке.

- **Включение голосование для причин состояния**: по умолчанию для идеи включается голосование только в том случае, если для причины состояния задано значение "Новая". Теперь можно включать голосование по идеям для различных причин состояния. Чтобы включить голосование для других причин состояния, необходимо создать параметр сайта "Идеи/EnableVotingForStatusReasons" и задать в его значении требуемые причины состояний. 

### <a name="dynamics-365-portals-version-906-for-the-model-driven-apps-in-dynamics-365"></a>Порталы Dynamics 365 версии 9.0.6 для приложений на основе модели в Dynamics 365

Порталы Dynamics 365 версии 9.0.6 для приложений на основе модели в Dynamics 365 содержат следующие последние обновления и функции:

- **Приложение порталов Dynamics 365**: приложение порталов Dynamics 365 обеспечивает новый интерфейс для настройки и управления сетевой платформой для связи и совместной работой с клиентами. При установке порталов Dynamics 365 версии 9.0 или выше приложение порталов Dynamics 365, построенное на платформе единого интерфейса, создается в готовом виде.

- **Сброс портала**: теперь можно сбросить портал, если планируется перенос в другое географическое расположение или в другой клиент и вы не хотите больше использовать этот портал. При сбросе портала размещенные ресурсы портала удаляются, и URL-адрес портала будет недоступен. Дополнительные сведения: [Сброс портала](admin/reset-portal.md)

- **Изменение базового URL-адреса портала**: теперь можно изменить базовый URL-адрес портала после его подготовки. Например, если вы выбрали contosocommunity.microsoftcrmportals.com в качестве базового URL-адреса при подготовке портала, позже можно изменить его на contosocommunityportal.microsoftcrmportals.com в соответствии с вашим требованием. Дополнительные сведения: [Изменение базового URL-адреса](admin/change-base-url.md)


### <a name="dynamics-365-portals-version-841-for-the-model-driven-apps-in-dynamics-365"></a>Порталы Dynamics 365 версии 8.4.1 для приложений на основе модели в Dynamics 365

Порталы Dynamics 365 версии 8.4.1 для приложений на основе модели в Dynamics 365 содержат исправление ряда ошибок, улучшение производительности, а также следующие функции:

- **Поиск в содержимом вложения статей базы знаний и веб-файлов**: теперь возможен поиск в содержимом статей базы знаний и веб-файлов для увеличения вероятности получения релевантных результатов поиска. Дополнительные сведения: [Поиск в содержимом вложенных файлов](configure/search-file-attachment.md)
- **Специальные возможности**: готовые порталы (портал сообщества, портал партнеров, портал клиентов, портал самообслуживания сотрудников) теперь доступны. Однако специалист по настройке должен гарантировать, что портал остается доступным после любых настроек или изменений.


### <a name="dynamics-365-portals-version-84-for-the-model-driven-apps-in-dynamics-365"></a>Порталы Dynamics 365 версии 8.4 для приложений на основе модели в Dynamics 365

Порталы Dynamics 365 версии 8.4 для приложений на основе модели в Dynamics 365 содержат исправление ряда ошибок, улучшение производительности, а также следующие функции:

- **Доступ к журналам ошибок портала**. Как разработчик портала, вы теперь можете получить доступ к подробным журналам ошибок для любых проблем на портале. Это помогает отладить проблемы при разработке портала. После ввода портала в эксплуатацию можно настроить портал таким образом, чтобы он отправлял все ошибки приложений на принадлежащую вам учетную запись хранилища больших двоичных объектов Azure. Это поможет отладить проблемы, о которых сообщают клиенты. Дополнительные сведения: [Доступ к журналам ошибок портала](admin/view-portal-error-log.md)
- **Обновление ключа проверки подлинности портала**. Портал подключается к среде Common Data Service с помощью приложения Azure Active Directory. Для этого ему требуется ключ проверки подлинности, подключенный к приложению Azure Active Directory. Этот ключ добавляется при подготовке портала, и его необходимо обновлять каждые два года. Эта версия портала дает возможность администраторам получать уведомления об истечении срока действия ключа и обновлять этот ключ из центра администрирования порталов Power Apps. Подробнее: [Обновление ключа проверки подлинности портала](admin/manage-auth-key.md)
- **Выполнение общих нормы по защите данных на порталах**. Как администратор портала, вы теперь можете настроить портал для выполнения требований стандартов GDPR. Можно также предоставить определенные условия, с которыми должны согласиться пользователи портала, чтобы они могли использовать портал. Можно также настроить проверки; например, если к порталу обращается несовершеннолетний пользователь, он должен обладать родительским согласием для доступа к порталу. Выполнение норм GDPR позволяют получать согласие у пользователей портала на использование их личных данных, выявлять несовершеннолетних пользователей и получать согласие родителей для несовершеннолетних пользователей. Дополнительные сведения: [Выполнение норм GDPR на порталах](configure/implement-gdpr.md)

### <a name="dynamics-365-portals-version-83-for-the-model-driven-apps-in-dynamics-365"></a>Порталы Dynamics 365 версии 8.3 для приложений на основе модели в Dynamics 365

Порталы Dynamics 365 версии 8.3 для приложений на основе модели в Dynamics 365 содержат множество новых обновлений и функций:

- **Возможность включать вложения в статьи базы знаний**: можно отображать вложения примечания вместе со статьями базы знаний. Для включения эту этой функции следует создать параметр сайта KnowledgeManagement/DisplayNotes и задать для него значение **true**. Пользователи портала также могут искать эти вложения. Дополнительные сведения: Отображение вложений файлов со статьями базы знаний

  > [!Note]
  > Поиск вложений может быть выполнен по описанию примечания и имени вложения файла. Содержимое вложенного файла недоступно для поиска.
  
- **Мастер администрирования для добавления сущности на портал**: эта функция представляет новый мастер администрирования для простого представления данных на портале. Сущность, созданная с помощью мастера, принимает данные от организации и делает подмножество этих данных доступным для всех клиентов портала на основании выбранной модели безопасности и разрешений.

- **Импорт перевода метаданных**: используйте эту функцию для импорта перевода метаданных новых активированных языков после установки портала. Дополнительные сведения: [Импорт перевода метаданных](admin/import-metadata-translation.md)

- **Доступность исходного кода для порталов**: одноразовый выпуск кода порталов Dynamics 365 выпущен в центр загрузки Майкрософт под лицензией MIT для загрузки разработчиками. Эта функция позволяет развертывать порталы в локальных или сетевых средах Dynamics 365 On-premises, а также позволяет разработчикам настраивать код в соответствии с конкретными бизнес-потребностями.

  > [!NOTE]
  > Исходный кода предлагается как рабочий пример и в зависимости от потребности. Непосредственная поддержка не будет предоставляться для каких-либо изменений в коде.

- **Усовершенствованная конфигурация и поддержка единого входа (SSO) для Azure Active Directory B2C (Azure AD B2C)**: для порталов, на которых требуется вход на основании потребителя, эта функция теперь поддерживает следующие возможности:
  - Настройка использования единого входа (SSO) при проверке подлинности портала. 
  - Поддержка Azure AD B2C для проверки подлинности клиентов.
  - Управление безопасностью портала в Azure.

  Дополнительные сведения: Параметры поставщика [Azure AD B2C для порталов](configure/azure-ad-b2c.md)

- **Поддержка форматов даты "Независимо от часового пояса" в формах порталов**: эта функция добавляет поддержку поведения **Только дата** и **Независимо от часового пояса** для полей даты и времени на порталах. Дополнительные сведения: [Поведение и формат поля "Дата и время"](configure/behavior-format-date-time-field.md)

- **Разрешение подготавливать портал для администраторов, которые не являются глобальными**: теперь можно подготавливать портал, если вам назначена роль системного администратора организации CRM, выбранной для портала. Теперь вы также можете управлять существующим порталом, если у вас есть любая из следующих ролей:
  - Администратор службы Dynamics 365
  - Системный администратор организации CRM, выбранной для портала

- **Храните пользовательского имени домена для портала**: эта функция хранит основное имя домена портала в записи веб-сайта. Если имя домена меняется в будущем, сохраняется последнее основное имя домена.

- **Отслеживание файлов cookie для порталов**: устойчивый файл cookie, Dynamics365PortalAnalytics, будет задаваться каждый раз, когда пользователь переходит на портал. Срок действия этого файла cookie заканчивается через 90 дней. Этот файл cookie не хранит никаких личных данных пользователя и используется корпорацией Майкрософт для сбора аналитики о службе портала. Дополнительные сведения о заявлении о конфиденциальности Microsoft Online Services см. [здесь](https://go.microsoft.com/fwlink/p/?linkid=856855).

- **Улучшенная производительность верхнего и нижнего колонтитулов на портале**: два новых параметр сайта, Header/OutputCache/Enabled и Footer/OutputCache/Enabled, добавлены для включения кэширования выходных данных верхнего/нижнего колонтитулов, если для них задано значение true. Для новых пользователей эти параметры сайта имеют значение true по умолчанию, что позволяет выполнять кэширование выходных данных верхнего и нижнего колонтитулов. Для существующих пользователей, которые выполняют обновление до более новой версии порталов Dynamics 365, кэширование выходных данных отключено по умолчанию. Это означает, что веб-шаблоны верхнего и нижнего колонтитулов анализируются и отрисовываются при каждой загрузке страницы. Чтобы включить кэширования выходных данных, необходимо обновить соответствующие веб-шаблоны и создать необходимые параметры сайта. Дополнительные сведения: [Включение кэширования выходных данных верхнего и нижнего колонтитулов](configure/enable-header-footer-output-caching.md)

### <a name="december-2016-updates"></a>Обновления за декабрь 2016 г.

Обновление за декабрь 2016 г. привнесло много новых функций в порталы Dynamics 365. Эти обновления улучшают взаимодействие между компаниями, партнерами и клиентами, а также ускоряют и упрощают навигацию по порталу. Некоторые из главных обновлений включают в себя:

- **Поддержка нескольких языков:** поддержка клиентов из нескольких регионов с помощью одного портала. Дополнительные сведения: [Включение поддержки нескольких языков](configure/enable-multiple-language-support.md)
- **Поддержка восточно-азиатских яыков:** теперь поддерживаются многобайтовые языки, например японский, китайский и корейский.
- **Фасетный поиск:** новые фильтры позволяют клиентам быстрее искать требуемое содержимое, одновременно обеспечивая больший контроль видимости содержимого. Дополнительные сведения: [Фасетный поиск](configure/improve-portal-search-faceted-search.md)
- **Фильтрация продуктов:** пользователи портала могут настраивать доступ к статьям базы знаний в соответствии с ответственностью за свои продукты, чтобы избежать избыточной информации.
- **Уровни доступа к содержимому:** новый уровень типа собственности, связанный с контактом, учетной записью или веб-ролью портала, можно использовать для управления доступом к статьям базы знаний, чтобы помочь в предоставлении правильной статьи для правильной аудитории и предотвратить отображение неуместных статей. Дополнительные сведения: [Уровни доступа к содержимому](https://docs.microsoft.com/dynamics365/portals/manage-knowledge-articles-content-levels)
- **Улучшение отчетности о статье базы знаний:** портал отслеживает, где использовалась статья базы знаний на портале.
- **Интеграция с Project Service Automation:** предоставляет доступ к активным и закрытым проектам на всех стадиях жизненного цикла проекта партнерам и клиентам. Участники рабочей группы, рецензенты и клиенты могут просматривать статус проекта, предложения с расценками, заказы, форумы и доступные для резервирования ресурсы на портале с этим решением. Дополнительные сведения: [Интеграция Project Service Automation](https://docs.microsoft.com/dynamics365/portals/integrate-project-service-automation)
- **Интеграция с Field Service:** предоставление информации об активных соглашениях, активах, заказах на работу, счетах и обращениях в службу поддержки партнерам и клиентам на портале с этим решением. Дополнительные сведения: [Интеграция Field Service](https://docs.microsoft.com/dynamics365/portals/integrate-field-service)
- **Адаптация партнеров:** привлекайте новых партнеров для улучшения продаж и сервиса для клиентов. Потенциальные партнеры могут подавать заявки на получение статуса партнера через портал.

### <a name="privacy-notice"></a>Уведомление о конфиденциальности

[!INCLUDE[cc-privacy-crm-portals-data-exposed](../../includes/cc-privacy-crm-portals-data-exposed.md)]

Подробнее о дополнительных предложениях службы [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] см. в разделе [[!INCLUDE[cc_privacy_note_azure_trust_center](../../includes/cc_privacy_note_azure_trust_center.md)]](https://azure.microsoft.com/support/trust-center/).  