---
title: Использование средства проверки решений для проверки приложений в PowerApps | Microsoft Docs
description: Использование средства проверки решений для проверки решения.
author: Mattp123
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: article
ms.date: 12/04/2018
ms.author: matp
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="use-solution-checker-to-validate-your-model-driven-apps-in-powerapps"></a>Использование средства проверки решений для проверки управляемых моделью приложений в PowerApps

Чтобы обеспечивать сложные бизнес-требования, создатели управляемых моделью приложений часто могут в конечном счете создавать в высокой степени развитые приложения, которые настраивают и расширяют платформу Common Data Service (CDS) для приложений. Со сложными реализациями возникает риск возникновения проблем производительности, устойчивости и надежности, что может отрицательно повлиять на опыт работы пользователя. Выявление этих проблем и разработка способов их устранения может быть сложной задачей, требующей много времени. С функцией проверки решения можно выполнить проверку решений с широким статическим анализом ваших решений по набору правил оптимальной работы и быстро выявить эти проблемные закономерности. После завершения проверки вы получите подробный отчет со списком выявленных проблем, затронутыми компонентами и кодом, а также со ссылками на документацию, в которой описываются способы решения каждой проблемы.

Средство проверки решений анализирует этих компоненты решений. 
- Подключаемые модули CDS для приложений
- Настраиваемые действия бизнес-процесса CDS для приложений 
- Веб-ресурсы CDS для приложений (HTML и JavaScript)
- Конфигурации CDS для приложений, такие как шаги сообщения пакета SDK 

Средство проверки решений работает с неуправляемыми решениями, которые можно экспортировать из среды. Средство проверки решений не работает со следующими решениями. 
- Решения системы по умолчанию (решения по умолчанию и решение по умолчанию Common Data Service).
- Решения, которых содержат JavaScript, использующий ECMAScript 6 (2015) или более поздних версий. При обнаружении кода JavaScript, который используется одну из этих версий, выводится сообщение об ошибке синтаксиса JS001 для веб-ресурса.

> [!NOTE]
> Эта функция в настоящее время находится на этапе предварительного ознакомления и доступна только в регионе Северной Америки. 
> [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]


## <a name="enable-the-solution-checker"></a>Включение средства проверки решений
Средство проверки решений становится доступным в области решений PowerApps после установки решения средства проверки PowerApps. Обратите внимание, что вы не можете найти его с помощью просмотра или поиска в Microsoft AppSource. Его необходимо установить, следуя указанным действиям.  

1. Войдите в [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) и выберите среду Common Data Service, в которой необходимо включить средство проверки решений. 
2. В левой области навигации выберите **Решения**.
3. На панели инструментов выберите **Средство проверки решений**, затем выберите пункт **Установить** — откроется страница Microsoft AppSource. Необходимо включить всплывающие окна, если браузер блокирует открытие страницы. 

   ![Установка средства проверки решений](media/solution-checker-install.png)

4. Выберите **Бесплатная пробная версия** на странице AppSource. 
5. Если вы соглашаетесь, примите условия и выберите среду для установки средства проверки решений PowerApps. 
6.  Когда установка завершена, обновите список **Решение** на сайте PowerApps, чтобы проверить доступность средства проверки решений.  
7. Чтобы проверить решение, [запустите сродство проверки решений](#run-the-solution-checker).


<!-- ### Components created with the PowerApps checker
When you install the PowerApps checker these solution specific components are created. 
- Entities: The entities that are created are required to store the results of solution analysis and the status of analysis jobs in your environment.
   - Analysis Component
   - Analysis Job
   - Analysis Result
- System job: A system job is created so admins can remove solution analysis data from the environment. The job contains a configuration value, currently set to remove the solution analysis data after 60 days, which an administrator can override. 
- Security Roles: Two security roles, **Export Customizations**, and **Solution Checker** are created. These roles are required to export the solution for analysis, and storing the analysis results to the entities in your environment.
- User principle: The **PowerApps Advisor** user is created that allows the checker to authenticate with your CDS for Apps environment and assign the two security roles, Export Customizations and Solution Checker. The PowerApps Advisor is an application user and does not consume a license.  -->

## <a name="run-the-solution-checker"></a>Запуск средства проверки решений
После установки средства проверки PowerApps в вашу среду пункт меню **Средство проверки решений** будет доступно при выборе неуправляемого решения в области **Решения** PowerApps. 

1. Выполните вход в [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). 
2. В левой области выберите **Решения**. 
3. Рядом с неуправляемым решением, которое требуется проанализировать, выберите пункт **...**, укажите на пункт **Средство проверки решений**, затем выберите **Выполнить**. 

   ![Выполнение команды средства проверки решений](media/solution-checker-run.png)

4.  Панель состояния, расположенная в правом верхнем углу страницы **Решения**, показывает **Средство проверки решений выполняется**. 

    ![Состояние средства проверки решений](media/solution-checker-status.png)
   
     Обратите внимание на следующее:
       - Средству проверки решений может потребоваться несколько минут для выполнения анализа. 
    
       - В это время отображается состояние **Выполняется...** в столбце **Средство проверки решений** столбца **Решение**. 
    
       - Вы получите уведомление по электронной почте и уведомление в области **Уведомления** сайта PowerApps после завершения проверки.  

5.  [Просмотрите отчет](#reviewing-the-solution-checker-report), когда проверка будет завершена.

## <a name="cancel-a-check"></a>Отмена проверки

После отправки проверки решения в вашу среду проверку можно отменить через панель состояния в верхней правой области страницы **Решения**. 

Если вы отмените проверку, выполнение средства проверки решений прекращается, и состояние проверки решения возвращается к предыдущему состоянию. 

## <a name="solution-checker-states"></a>Состояния средства проверки решений
При установке средства проверки решений в среду столбец **Проверка решения** становится доступной в списке **Решения**. В этом столбце отображаются состояния анализа решения для решения. 

|область  |Описание  |
|---------|---------|
|Не запускалось    | Решение никогда не было проанализировано.        |
|Выполняется     | Решение анализируется.       |
|Не удалось завершить.     |  Анализ решения был запрошен, но анализ не удается завершить успешно.       |
|Результаты на *дата и время*   | Завершен анализ решения и результаты доступны для загрузки.      |
| Не удалось завершить. Результат на *дата и время*     | Самый последний запрос анализа не был успешно завершен. Последние успешные результаты можно загрузить.         |
|Проверено Microsoft     | Это решение управляется Microsoft. Анализ решения не разрешен для этих решений.         |
|Проверено издателем     |  Это решение управляется третьей стороной. В настоящее время анализ решения недоступен для таких решений.        |


## <a name="review-the-solution-checker-report"></a>Просмотр отчета средства проверки решений
После завершения проверки решения отчет анализа становится доступным для загрузки из веб-браузера. Отчет представлен в формате [!INCLUDE [pn-excel-short](../../includes/pn-excel-short.md)] и содержит несколько визуализаций и столбцов, помогающих в идентификации влияния, типа и расположения каждой проблемы, обнаруженной в решении. Ссылка на детальную инструкцию о том, как устранить проблему, также предусмотрена. 

1. В левой области выберите **Решения**.
2. Рядом с неуправляемым решением, где нужно загрузить отчет средства проверки решения, выберите **...**, укажите на **Средство проверки решений**, затем выберите **Загрузить последние результаты**.  
3. ZIP-файл средства проверки решения загружается в папку, указанную веб-браузером.

Здесь приведена сводка каждого столбца в отчете.

|Поле отчета |Описание  |Относится к компоненту   |
|---------|---------|---------|
|Проблема     |   Заголовок проблемы, выявленной в решении.      | Все        |
|Категория     | Определение категории выявленной проблемы, например **Производительность**, **Использование** или **Удобство поддержки**.      |  Все       |
|Важность     | Представляет собой потенциальную воздействие определенной проблемы. Доступные типы неблагоприятного воздействия: **Высокий**, **Средний**, **Низкий**, **Информационный**.         |  Все       |
|Инструкция     |  Ссылка на статью с подробными сведениями о проблеме, ее влиянии и рекомендуемом решении. действия.       |  Все       |
|Компонент     |  Компонент решения, в котором была выявлена проблема.        |   Все      |
|Location     |  Расположение и/или исходный файл компонента, в котором возникла выявленная проблема, например сборка или имя файла JavaScript.        |  Все       |
|№ строки     |  Ссылка на номер строки для проблемы в затронутом компоненте веб-ресурса.       |  Веб-ресурсы       |
|Модуль     | Имя модуля, в котором была обнаружена ошибка, выявленная в сборке.     |   Подключаемый модуль или настраиваемое действие бизнес-процесса      |
|Тип     | Тип проблемы, выявленной в сборке.        | Подключаемый модуль или настраиваемое действие бизнес-процесса        |
|Участник     |  Участник проблемы, выявленной в сборке.      | Подключаемый модуль или настраиваемое действие бизнес-процесса        |
|Оператор     | Оператор или конфигурация кода, которые привели к проблеме.        |  Все       |
|Комментарии     | Подробные сведения о проблеме, содержащие шаги разрешения высокого уровня.         |  Все       |



## <a name="best-practice-rules-used-by-solution-checker"></a>Правила рекомендаций, используемые средством проверки решений


|Компонент решения  |Имя правила  |Описание правила  |
|---------|---------|---------|
|Подключаемый модуль или действие бизнес-процесса   | [рис-указать-столбец](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-specify-column&client=PAChecker&source=featuredocs)  | Избегайте выбирать все столбцы с помощью API-интерфейсов запроса Dynamics 365 for Customer Engagement.     |
|Подключаемый модуль или действие бизнес-процесса   | [мета-удалить-дублирующую-регистрацию](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-dup-reg&client=PAChecker&source=featuredocs)     | Не допускайте дублирования регистраций подключаемого модуля в Dynamics 365 for Customer Engagement.     |
|Подключаемый модуль или действие бизнес-процесса   | [рис-отключение-проверки-активности](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-turn-off-keepalive&client=PAChecker&source=featuredocs)   | Задайте для KeepAlive значение false при взаимодействии с внешними узлами в подключаемом модуле Dynamics 365 for Customer Engagement.     |
|Подключаемый модуль или действие бизнес-процесса   | [рис-избегать-неопубликованных-метаданных](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-unpub-metadata&client=PAChecker&source=featuredocs)   | Не извлекайте неопубликованное метаданные Dynamics 365 for Customer Engagement.     |
|Подключаемый модуль или действие бизнес-процесса   | [рис-избегать-пакетного-режима-подключаемых-модулей](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-batch-plugin&client=PAChecker&source=featuredocs)   | Не используйте пакетные типы запросов в подключаемых модулях и действиях бизнес-процессов в Dynamics 365 Customer Engagement.    |
|Подключаемый модуль или действие бизнес-процесса   | [мета-избегать-регистрации-без-атрибутов](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-reg-no-attribute&client=PAChecker&source=featuredocs)  | Включайте атрибуты фильтрации с регистрациями подключаемых модулей Dynamics 365 for Customer Engagement.    |
|Подключаемый модуль или действие бизнес-процесса   | [мета-избегать-регистрации-для-извлечения](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-reg-retrieve&client=PAChecker&source=featuredocs)  | Соблюдайте осторожность с подключаемыми модулями Dynamics 365 for Customer Engagement, зарегистрированными для сообщений Retrieve и RetrieveMultiple.    |
|Подключаемый модуль или действие бизнес-процесса   | [мета-удалить-неактивный](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-inactive&client=PAChecker&source=featuredocs)    | Удалите неактивные настройки в Dynamics 365 for Customer Engagement.    |
|Подключаемый модуль или действие бизнес-процесса   | [Старайтесь не использовать window.top](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-window-top&client=PAChecker&source=featuredocs)   | Старайтесь не использовать window.top.    |
|Подключаемый модуль или действие бизнес-процесса   | [рис-мета-избегать-устаревших-сообщений-crm2011](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-crm2011-depr-message&client=PAChecker&source=featuredocs)  | Не используйте устаревшие сообщения Microsoft Dynamics CRM 2011.     |
|Подключаемый модуль или действие бизнес-процесса   | [мета-избегать-событие-crm4](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-crm4-event&client=PAChecker&source=featuredocs) | Не используйте этап регистрации подключаемого модуля Microsoft Dynamics CRM 4.0.    |
|Подключаемый модуль или действие бизнес-процесса   | [рис-избегать-специализированных-операций-обновления](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-specialized-update-ops&client=PAChecker&source=featuredocs)  | Не используйте специализированные запросы операций обновления в Dynamics 365 for Customer Engagement.        |
|Веб-ресурсы  | [веб-использовать-асинхронно](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-async&client=PAChecker&source=featuredocs)  |  Взаимодействуйте с ресурсами HTTP и HTTPS асинхронно.   |
|Веб-ресурсы  | [мета-удалить-недействительные-обработчики-форм](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-invalid-form-handler&client=PAChecker&source=featuredocs)  | Исправьте или удалите неправильные регистрации событий форм Dynamics 365 for Customer Engagement.   |
|Веб-ресурсы  | [мета-удалить-потерянные-элементы-форм](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-orphaned-form-element&client=PAChecker&source=featuredocs)  | Исправьте или удалите потерянные регистрации событий форм Dynamics 365 for Customer Engagement.   |
|Веб-ресурсы  | [веб-избегать-модальных-диалогов](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-modals&client=PAChecker&source=featuredocs)  | Не используйте модальные диалоги.   |
|Веб-ресурсы  | [веб-избегать-службу-odata-crm2011](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-crm2011-service-odata&client=PAChecker&source=featuredocs)   | Не используйте в качестве цели конечную точку Microsoft Dynamics CRM 2011 OData 2.0.     |
|Веб-ресурсы  | [веб-избегать-службы-soap-crm2011](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-crm2011-service-soap&client=PAChecker&source=featuredocs)  | Не используйте в качестве цели службы Microsoft Dynamics CRM 2011 SOAP.   |
|Веб-ресурсы  | [веб-избегать-специальные-api-браузера](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-browser-specific-api&client=PAChecker&source=featuredocs) | Не используйте устаревшие API-интерфейса Internet Explorer или подключаемые модули браузера.   |
|Веб-ресурсы  | [веб-избегать-2011-api](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-2011-api&client=PAChecker&source=featuredocs)  | Не используйте устаревшую объектную модель Microsoft Dynamics CRM 2011.  |
|Веб-ресурсы  | [веб-используйте-относительный-uri](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-relative-uri&client=PAChecker&source=featuredocs)   | Не используйте абсолютные URL-адреса конечной точки CDS для приложений.    |
|Веб-ресурсы  | [веб-используйте-контекст-клиента](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-client-context&client=PAChecker&source=featuredocs)  | Используйте контексты клиента.   |
|Веб-ресурсы  | [веб-использовать-параметры-api-диалога](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-dialog-api-param&client=PAChecker&source=featuredocs)   | Используйте параметры API-интерфейса диалога.   |
|Веб-ресурсы  | [веб-использовать-параметр-организации](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-org-setting&client=PAChecker&source=featuredocs)   | Используйте параметры организации.   |
|Веб-ресурсы  | [веб-использовать-api-сетки](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-grid-api&client=PAChecker&source=featuredocs)   | Используйте API-интерфейсы сетки.    |
|Веб-ресурсы  | [веб-избегать-isActivityType](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-isActivityType&client=PAChecker&source=featuredocs)   | Замените метод Xrm.Utility.isActivityType новым методом Xrm.Utility.getEntityMetadata и не используйте в правилах ленты.    |
|Веб-ресурсы  | [мета-избегать-Silverlight](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-silverlight&client=PAChecker&source=featuredocs)   | Использование веб-ресурса Silverlight устарело.   |


## <a name="see-also"></a>См. также
[Знакомство с экспериментальными функциями и функциями для предварительного ознакомления в PowerApps](../canvas-apps/working-with-experimental.md) <br/>
[Инструкция и рекомендации для построения решений PowerApps](https://docs.microsoft.com/dynamics365/customer-engagement/guidance/)