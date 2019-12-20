---
title: Использование средства проверки решений для проверки приложений в Power Apps | Документация Майкрософт
description: Использование средства проверки решений для проверки решения.
author: Mattp123
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: article
ms.date: 07/09/2019
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e9a3fb0c291678c5c571895c900bfde10a7f42ed
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "2885389"
---
# <a name="use-solution-checker-to-validate-your-model-driven-apps-in-power-apps"></a>Использование средства проверки решений для проверки управляемых моделью приложений в Power Apps

Чтобы обеспечивать сложные бизнес-требования, создатели управляемых моделью приложений часто могут в конечном счете создавать в высокой степени развитые приложения, которые настраивают и расширяют платформу Common Data Service. Со сложными реализациями возникает риск возникновения проблем производительности, устойчивости и надежности, что может отрицательно повлиять на опыт работы пользователя. Выявление этих проблем и разработка способов их устранения может быть сложной задачей, требующей много времени. С функцией проверки решения можно выполнить проверку решений с широким статическим анализом ваших решений по набору правил оптимальной работы и быстро выявить эти проблемные закономерности. После завершения проверки вы получите подробный отчет со списком выявленных проблем, затронутыми компонентами и кодом, а также со ссылками на документацию, в которой описываются способы решения каждой проблемы.

Средство проверки решений анализирует этих компоненты решений: 
- Подключаемые модули Common Data Service
- Действия настраиваемого рабочего процесса Common Data Service 
- Веб-ресурсы Common Data Service (HTML и JavaScript)
- Конфигурации Common Data Service, такие как шаги сообщения пакета SDK 

Средство проверки решений работает с неуправляемыми решениями, которые можно экспортировать из среды. 

> [!NOTE]
> - В этом разделе рассматривается порядок выполнения средства проверки решений из портала разработчика Power Apps. Модуль PowerShell также доступен, который можно использовать, чтобы взаимодействовать непосредственно с сервисом. Модуль Microsoft.PowerApps.Checker.PowerShell можно использовать для анализа управляемых и неуправляемых решений для поддерживаемых версии локальных и сетевых сред или чтобы автоматизировать и интегрировать сервис в каналы построения и выпуска. Дополнительные сведения: [Обзор Microsoft.PowerApps.Checker.PowerShell]( /powershell/powerapps/overview?view=pa-ps-latest#get-started-using-the-microsoftpowerappscheckerpowershell-module) 
> - Средство проверки решений не работает с решениями, содержащими JavaScript с использованием ECMAScript 6 (2015) или более поздних версий. При обнаружении кода JavaScript, который используется одну из этих версий, выводится сообщение об ошибке синтаксиса JS001 для веб-ресурса.

## <a name="enable-the-solution-checker"></a>Включение средства проверки решений
Средство проверки решений включено по умолчанию в каждой среде Common Data Service. Пункт меню **Средство проверки решений** доступно при выборе неуправляемого решения в области **Решения** в Power Apps. Если пункт **Выполнить** недоступен в меню **Средство проверки решений**, можно включить его, установив средство проверки решений Power Apps. Для установки выполните следующие шаги.   

1. Войдите в [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) и выберите среду Common Data Service, в которой необходимо включить средство проверки решений. 
2. В левой области навигации выберите **Решения**.
3. На панели инструментов выберите **Средство проверки решений**, затем выберите пункт **Установить** — откроется страница Microsoft AppSource. Необходимо включить всплывающие окна, если браузер блокирует открытие страницы. 

   > [!div class="mx-imgBorder"]
   > ![Установка средства проверки решений](media/solution-checker-install.png "Установка средства проверки решений")

4. Выберите **Бесплатная пробная версия** на странице AppSource. 

5. Если вы соглашаетесь, примите условия и выберите среду для установки средства проверки решений Power Apps. 
6. Когда установка завершена, обновите список **Решение** на сайте Power Apps, чтобы проверить доступность средства проверки решений.  
7. Чтобы проверить решение, [запустите сродство проверки решений](#run-the-solution-checker).


<!-- ### Components created with the Power Apps checker
When you install the Power Apps checker these solution specific components are created. 
- Entities: The entities that are created are required to store the results of solution analysis and the status of analysis jobs in your environment.
   - Analysis Component
   - Analysis Job
   - Analysis Result
- System job: A system job is created so admins can remove solution analysis data from the environment. The job contains a configuration value, currently set to remove the solution analysis data after 60 days, which an administrator can override. 
- Security Roles: Two security roles, **Export Customizations**, and **Solution Checker** are created. These roles are required to export the solution for analysis, and storing the analysis results to the entities in your environment.
- User principle: The **Power Apps Advisor** user is created that allows the checker to authenticate with your Common Data Service environment and assign the two security roles, Export Customizations and Solution Checker. The Power Apps Advisor is an application user and does not consume a license.  -->

## <a name="run-the-solution-checker"></a>Запуск средства проверки решений
После установки средства проверки Power Apps в вашу среду пункт меню **Средство проверки решений** будет доступно при выборе неуправляемого решения в области **Решения** Power Apps. 

1. Выполните вход в [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). 
2. В левой области выберите **Решения**. 
3. Рядом с неуправляемым решением, которое требуется проанализировать, выберите пункт **...**, укажите на пункт **Средство проверки решений**, затем выберите **Выполнить**. 

   > [!div class="mx-imgBorder"]
   > ![Выполнение команды средства проверки решений](media/solution-checker-run.png "Выполнение команды средства проверки решений")

4.  Панель состояния, расположенная в правом верхнем углу страницы **Решения**, показывает **Средство проверки решений выполняется**. 

    > [!div class="mx-imgBorder"]
    > ![Состояние средства проверки решений](media/solution-checker-status.png "Состояние средства проверки решений")
   
    Обратите внимание на следующее:
    - Средству проверки решений может потребоваться несколько минут для выполнения анализа. 
    
    - В это время отображается состояние **Выполняется...** в столбце **Средство проверки решений** столбца **Решение**. 
    
    - Вы получите уведомление по электронной почте и уведомление в области **Уведомления** сайта Power Apps после завершения проверки.  

5.  [Просмотрите отчет](#review-the-solution-checker-report), когда проверка будет завершена.

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
|Не удалось завершить. Результат на *дата и время*     | Самый последний запрос анализа не был успешно завершен. Последние успешные результаты можно загрузить.         |
|Проверено Microsoft     | Это решение управляется Microsoft. Анализ решения не разрешен для этих решений.         |
|Проверено издателем     | Это решение управляется третьей стороной. В настоящее время анализ решения недоступен для таких решений.        |


## <a name="review-the-solution-checker-report"></a>Просмотр отчета средства проверки решений
После завершения проверки решения можно просматривать отчет анализа на портале или можно загрузить отчет из веб-браузера. На портале имеется возможность фильтровать, сгруппировать результаты по параметру **Проблема**, **Местоположение** или **Важность**, а также просматривать подробные сведения для проблем, обнаруженных в решении. 

1. В левой области выберите **Решения**.
2. Рядом с неуправляемым решением, где нужно просмотреть отчет средства проверки решения, выберите **...**, укажите на **Средство проверки решений**, затем выберите **Показать результаты**.  
3. Выберите проблему для просмотра сведений и инструкций о возможных способах решения.

    > [!div class="mx-imgBorder"] 
    > ![](media/solution-checker-viewresults.png "Solution checker view results")

Результаты проверки решения также доступны для загрузки. ZIP-файл средства проверки решений загружается в папку, указанную браузером. Отчет загружается в формате [!INCLUDE [pn-excel-short](../../includes/pn-excel-short.md)] и содержит несколько элементов визуализации и столбцов, помогающих в идентификации влияния, типа и расположения каждой из проблем, обнаруженных в решении. Ссылка на детальную инструкцию о том, как устранить проблему, также предусмотрена. 

1. В левой области выберите **Решения**.
2. Рядом с неуправляемым решением, где нужно загрузить отчет средства проверки решения, выберите **...**, укажите на **Средство проверки решений**, затем выберите **Загрузить результаты**.  
3. ZIP-файл средства проверки решения загружается в папку, указанную веб-браузером.

Здесь приведена сводка каждого столбца в отчете.

|Поле отчета |Описание  |Относится к компоненту   |
|---------|---------|---------|
|Проблема     |   Заголовок проблемы, выявленной в решении.      | Все        |
|Категория     | Определение категории выявленной проблемы, например **Производительность**, **Использование** или **Удобство поддержки**.      |  Все     |
|Важность     | Представляет собой потенциальную воздействие определенной проблемы. Доступные типы неблагоприятного воздействия: **Высокий**, **Средний**, **Низкий** и **Информационный**.         |  Все       |
|Инструкция     |  Ссылка на статью с подробными сведениями о проблеме, ее влиянии и рекомендуемом действии.       |  Все       |
|Компонент     |  Компонент решения, в котором была выявлена проблема.        |   Все      |
|Location     |  Расположение и/или исходный файл компонента, в котором возникла выявленная проблема, например сборка или имя файла JavaScript.        |  Все       |
|№ строки     |  Ссылка на номер строки для проблемы в затронутом компоненте веб-ресурса.       |  Веб-ресурсы       |
|Модуль     | Имя модуля, в котором была обнаружена ошибка, выявленная в сборке.     |   Подключаемый модуль или настраиваемое действие бизнес-процесса      |
|Тип     | Тип проблемы, выявленной в сборке.        | Подключаемый модуль или настраиваемое действие бизнес-процесса        |
|Участник     |  Участник проблемы, выявленной в сборке.      | Подключаемый модуль или настраиваемое действие бизнес-процесса        |
|Оператор     | Оператор или конфигурация кода, которая привела к проблеме.        |  Все       |
|Комментарии     | Подробные сведения о проблеме, содержащие шаги разрешения высокого уровня.         |  Все       |


## <a name="best-practice-rules-used-by-solution-checker"></a>Правила рекомендаций, используемые средством проверки решений

|Компонент решения  |Имя правила  |Описание правила  |
|---------|---------|---------|
|Подключаемый модуль или действие бизнес-процесса   | [рис-указать-столбец](https://go.microsoft.com/fwlink/?LinkID=398563&error=il-specify-column&client=PAChecker&source=featuredocs)  | Избегайте выбора всех столбцов через API запросов Common Data Service.     |
|Подключаемый модуль или действие бизнес-процесса   | [мета-удалить-дублирующую-регистрацию](https://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-dup-reg&client=PAChecker&source=featuredocs)     | Избегайте дублирования регистрации подключаемых модулей Common Data Service.     |
|Подключаемый модуль или действие бизнес-процесса   | [рис-отключение-проверки-активности](https://go.microsoft.com/fwlink/?LinkID=398563&error=il-turn-off-keepalive&client=PAChecker&source=featuredocs)   | Задайте для KeepAlive значение false при взаимодействии с внешними узлами в подключаемом модуле Common Data Service.     |
|Подключаемый модуль или действие бизнес-процесса   | [рис-избегать-неопубликованных-метаданных](https://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-unpub-metadata&client=PAChecker&source=featuredocs)   | Избегайте извлечения неопубликованных метаданных Common Data Service.     |
|Подключаемый модуль или действие бизнес-процесса   | [рис-избегать-пакетного-режима-подключаемых-модулей](https://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-batch-plugin&client=PAChecker&source=featuredocs)   | Не используйте пакетные типы запросов в подключаемых модулях и действиях бизнес-процессов в Common Data Service.    |
|Подключаемый модуль или действие бизнес-процесса   | [мета-избегать-регистрации-без-атрибутов](https://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-reg-no-attribute&client=PAChecker&source=featuredocs)  | Включите атрибуты фильтрации в регистрации подключаемых модулей Common Data Service.    |
|Подключаемый модуль или действие бизнес-процесса   | [мета-избегать-регистрации-для-извлечения](https://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-reg-retrieve&client=PAChecker&source=featuredocs)  | Соблюдайте осторожность с подключаемыми модулями Common Data Service, зарегистрированными для сообщений Retrieve и RetrieveMultiple.    |
|Подключаемый модуль или действие бизнес-процесса   | [мета-удалить-неактивный](https://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-inactive&client=PAChecker&source=featuredocs)    | Удалите неактивные конфигурации в Common Data Service.    |
|Подключаемый модуль или действие бизнес-процесса   | [рис-мета-избегать-устаревших-сообщений-crm2011](https://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-crm2011-depr-message&client=PAChecker&source=featuredocs)  | Не используйте устаревшие сообщения Microsoft Dynamics CRM 2011.     |
|Подключаемый модуль или действие бизнес-процесса   | [мета-избегать-событие-crm4](https://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-crm4-event&client=PAChecker&source=featuredocs) | Не используйте этап регистрации подключаемого модуля Microsoft Dynamics CRM 4.0.    |
|Подключаемый модуль или действие бизнес-процесса   | [рис-избегать-специализированных-операций-обновления](https://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-specialized-update-ops&client=PAChecker&source=featuredocs)  | Не используйте специализированные запросы операции обновления в Common Data Service.    | 
| Подключаемый модуль или действие бизнес-процесса |  [рис-использование-функции-автонумерации](https://go.microsoft.com/fwlink/?LinkID=398563&error=il-use-autonumber-feature&client=PAChecker)  |Использование функции автоматической нумерации вместо настраиваемого решения автоматической нумерации. | 
| Подключаемый модуль или действие бизнес-процесса  | [рис-избегать-параллельного-режима-подключаемых-модулей](https://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-parallel-plugin&client=PAChecker)  | Следует избегать параллельных схем внутри подключаемых модулей.  |
| Подключаемый модуль или действие бизнес-процесса  | [рис-избегать-блокировки-подключаемых-модулей](https://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-lock-plugin&client=PAChecker)  | Не блокируйте статических участников в подключаемых модулях.  |
| Подключаемый модуль или действие бизнес-процесса  | [мета-избегать-извлечения-нескольких-аннотаций](https://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-retrievemultiple-annotation&client=PAChecker)  | Избегайте регистрации подключаемого модуля для RetrieveMultiple аннотации.  |
|Веб-ресурсы  | [веб-использовать-асинхронно](https://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-async&client=PAChecker&source=featuredocs)  |  Взаимодействуйте с ресурсами HTTP и HTTPS асинхронно.   |
|Веб-ресурсы  | [мета-удалить-недействительные-обработчики-форм](https://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-invalid-form-handler&client=PAChecker&source=featuredocs)  | Исправьте или удалите недействительные регистрации событий формы Common Data Service.   |
|Веб-ресурсы  | [мета-удалить-потерянные-элементы-форм](https://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-orphaned-form-element&client=PAChecker&source=featuredocs)  | Исправьте или удалите потерянные регистрации событий формы Common Data Service.   |
|Веб-ресурсы  | [веб-избегать-модальных-диалогов](https://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-modals&client=PAChecker&source=featuredocs)  | Не используйте модальные диалоги.   |
|Веб-ресурсы  | [веб-избегать-службу-odata-crm2011](https://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-crm2011-service-odata&client=PAChecker&source=featuredocs)   | Не используйте в качестве цели конечную точку Microsoft Dynamics CRM 2011 OData 2.0.     |
|Веб-ресурсы  | [веб-избегать-службы-soap-crm2011](https://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-crm2011-service-soap&client=PAChecker&source=featuredocs)  | Не используйте в качестве цели службы Microsoft Dynamics CRM 2011 SOAP.   |
|Веб-ресурсы  | [веб-избегать-специальные-api-браузера](https://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-browser-specific-api&client=PAChecker&source=featuredocs) | Не используйте устаревшие API-интерфейсы Internet Explorer или подключаемые модули браузера.   |
|Веб-ресурсы  | [веб-избегать-2011-api](https://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-2011-api&client=PAChecker&source=featuredocs)  | Не используйте устаревшую объектную модель Microsoft Dynamics CRM 2011.  |
|Веб-ресурсы  | [веб-используйте-относительный-uri](https://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-relative-uri&client=PAChecker&source=featuredocs)   | Не используйте абсолютные URL-адреса конечной точки Common Data Service.    |
|Веб-ресурсы  | [веб-используйте-контекст-клиента](https://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-client-context&client=PAChecker&source=featuredocs)  | Используйте контексты клиента.   |
|Веб-ресурсы  | [веб-использовать-параметры-api-диалога](https://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-dialog-api-param&client=PAChecker&source=featuredocs)   | Используйте параметры API-интерфейса диалога.   |
|Веб-ресурсы  | [веб-использовать-параметр-организации](https://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-org-setting&client=PAChecker&source=featuredocs)   | Используйте параметры организации.   |
|Веб-ресурсы  | [веб-использовать-api-сетки](https://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-grid-api&client=PAChecker&source=featuredocs)   | Используйте API-интерфейсы сетки.    |
|Веб-ресурсы  | [веб-избегать-isActivityType](https://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-isActivityType&client=PAChecker&source=featuredocs)   | Замените метод Xrm.Utility.isActivityType новым методом Xrm.Utility.getEntityMetadata и не используйте в правилах ленты.    |
|Веб-ресурсы  | [мета-избегать-Silverlight](https://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-silverlight&client=PAChecker&source=featuredocs)   | Использование веб-ресурса Silverlight устарело.   |
| Веб-ресурсы  | [интернет-удалите-отладочный-скрипт](https://go.microsoft.com/fwlink/?LinkID=398563&error=web-remove-debug-script&client=PAChecker)  | Не включайте отладочный скрипт в средах, отличных от среды разработки.  | 
| Веб-ресурсы  | [интернет-использование-строгого-режима](https://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-strict-mode&client=PAChecker)  | При возможности используйте строгий режим.  | 
| Веб-ресурсы  | [интернет-использование-операторов-строгого-равенства](https://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-strict-equality-operators&client=PAChecker)  | Используйте операторы строгого равенства.  | 
| Веб-ресурсы  | [интернет-избегайте-eval](https://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-eval&client=PAChecker)  | Не используйте функцию "eval" или ее функциональные эквиваленты.  | 


### <a name="see-also"></a>См. также
[Рекомендации и инструкции для Common Data Service](../../developer/common-data-service/best-practices/index.md)<br />
[Рекомендации и советы для управляемых моделью приложений](../../developer/model-driven-apps/best-practices/index.md)<br />
[Общие проблемы и их разрешение для средства проверки решений](common-issues-resolutions-solution-checker.md)<br />
