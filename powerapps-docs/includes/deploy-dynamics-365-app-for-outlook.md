---
title: Развертывание приложения Dynamics 365 App for Outlook | MicrosoftDocs
ms.custom: ''
ms.date: '2017-04-20'
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 09736e14-e744-48ca-a755-1b05bb55340e
caps.latest.revision: 39
author: jimholtz
ms.author: jimholtz
manager: brycho
---
# <a name="deploy-dynamics-365-app-for-outlook"></a>Развертывание приложения Dynamics 365 App for Outlook
[!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)] позволяет получить доступ к возможностям [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] при работе с [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] на компьютере, в Интернете или на планшете. Например, вы можете просматривать сведения о получателях электронной почты или встреч, а также связывать сообщения электронной почты или встречи в [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] с записью в [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)], такой как возможная сделка, организация или обращение. Подробнее о том, что можно делать в [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)], см. в [руководстве пользователя приложения Dynamics 365 App for Outlook](http://go.microsoft.com/fwlink/p/?LinkID=613099).  
  
> [!IMPORTANT]
>  [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] — не то же самое, что [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]. В [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)] [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)] в паре с[!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)] — это предпочтительный способ интеграции [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] с[!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]. **Обратите внимание, что отслеживание действий не поддерживается, когда [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] и [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] используются совместно одним и тем же пользователем.** Сведения о надстройке [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] см. в [руководстве пользователя Dynamics 365 for Outlook](http://go.microsoft.com/fwlink/p/?LinkID=524751).  
>   
>  [Делегированные пользователи](https://support.office.com/article/Allow-someone-else-to-manage-your-mail-and-calendar-9684B670-7588-4EEA-8717-9E5799047540) не могут использовать [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] для отслеживания сообщений электронной почты. Мы рекомендуем делегированным пользователям использовать [отслеживание на уровне папок или автоматическое отслеживание](https://www.microsoft.com/en-us/dynamics/crm-customer-center/overview-of-tracking-records-in-dynamics-365-for-outlook.aspx).  
  
<a name="BKMK_Compare"></a>   
## <a name="comparing-dynamics-365-app-for-outlook-with-dynamics-365-for-outlook"></a>Сравнение приложения Dynamics 365 App for Outlook с Dynamics 365 for Outlook  
 В следующей таблице приводится сравнение функций [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] с [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] (также называется клиентом или надстройкой [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]) для [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)].  
  
||||  
|-|-|-|  
|**Функция**|**[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]**|**[!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]**|  
|Отслеживание и задание значения "В отношении" для электронной почты|Да|Да|  
|Отслеживание и задание значения "В отношении" для встреч|Да|Да|  
|Отслеживание и задание значения "В отношении" для контактов|Да|Да|  
|Отслеживание и задание значения "В отношении" для задач|Нет|Да|  
|Задание значения "В отношении" одним щелчком мыши|Да|Нет|  
|Отображение сводки по получателям|Да|Нет|  
|Отображение сводки записи "В отношении" в сообщении электронной почты или встрече|Да|Нет|  
|Работа с [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)]|Да|Нет|  
|Работа с классическим приложением [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]|Да|Да|  
|Работа с [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] для Mac|Да|Нет|  
|Работа с телефонами|Да|Нет|  
|Открытие и создание записей [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] напрямую|Да|Да|  
|Применение настраиваемых форм и бизнес-логики|Да|Да|  
|Автономная работа|Нет|Да|  
|Применение шаблонов электронной почты|Да|Да|  
|Применение литературы|Да|Да|  
|Применение статей базы знаний|Да|Да|  
|Возможность отслеживать сообщения электронной почты после отправки|Да|Нет|  
|Сортировка, фильтрация, форматирование, группирование и классификация представлений|Нет|Да|  
|Создание документов слияния почты в Word|Нет|Да|  
|Управление синхронизацией полей|Нет|Да|  
  
<a name="BKMK_Requirements"></a>   
## <a name="requirements"></a>Требования  
 Для использования [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] необходимо следующее:  
  
-   [!INCLUDE[pn_crm_online_2016_update](../includes/pn-crm-online-2016-update.md)] или[!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)]  
  
-   Синхронизация входящей электронной почты путем синхронизации на стороне сервера. [!INCLUDE[proc_more_information](../includes/proc-more-information.md)][Настройка синхронизации электронной почты, встреч, контактов и задач на стороне сервера](../Topic/Set%20up%20server-side%20synchronization%20of%20email,%20appointments,%20contacts,%20and%20tasks.md)  
  
-   Привилегии, описанные ниже  
  
> [!NOTE]
>  Поддерживаемые конфигурации и требования для функций [!INCLUDE[pn_dyn_365](../includes/pn-dyn-365.md)] перечислены в различных местах документации. Конфигурации, не отраженные в документации, считаются неподдерживаемыми.  
  
### <a name="required-privileges"></a>Необходимые привилегии  
 [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] обеспечивает доступ к [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] при наличии привилегии **Использование приложения Dynamics 365 App for Outlook**. Если у пользователя нет этой привилегии, он увидит следующую ошибку:  
  
> "Вам не разрешено использование этого приложения. Обратитесь к системному администратору, чтобы изменить соответствующие настройки".  
  
 Пользователи также должны иметь привилегии на чтение и запись для следующих сущностей.  
  
 Вкладка "Управление бизнесом":  
  
-   **Почтовый ящик**  
  
 Вкладка "Настройка":  
  
-   **Сущность**  
  
-   **Поле**  
  
-   **Отношение**  
  
-   **Метаданные системного приложения**  
  
-   **Системная форма**  
  
-   **Метаданные пользовательского приложения**  
  
-   **Представление**  
  
##### <a name="set-the-privileges-for-a-security-role"></a>Задание привилегий для роли безопасности  
  
1.  [!INCLUDE[proc_settings_security](../includes/proc-settings-security.md)]  
  
2.  Щелкните **Роли безопасности**.  
  
3.  Выберите роль безопасности и перейдите на вкладку **Управление бизнесом**.  
  
4.  В разделе **Сущность** просмотрите настройки привилегий **Почтовый ящик**. Роль безопасности должна иметь значение "Пользователь" или более высокое.  
  
5.  В разделе **Привилегии, связанные с конфиденциальностью** проверьте, что параметр **Использование приложения Dynamics 365 App for Outlook** установлен в значение **Организация**. Если нет, щелкните **Использование приложения Dynamics 365 App for Outlookk**.  
  
### <a name="supported-configurations-with-microsoft-exchange"></a>Поддерживаемые конфигурации в Microsoft Exchange  
 Начиная с [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)] приложение можно использовать вместе с любым сочетанием [!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)] или [!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)] и [!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)] или [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (локальная версия), включая гибридные конфигурации. Это означает, что [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] можно использовать в любой из следующих конфигураций:  
  
|||  
|-|-|  
|[!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)]|[!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]|  
|[!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)]|[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (локальная версия)|  
|[!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]|[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (локальная версия)|  
|[!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]|[!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]|  
  
> [!NOTE]
>  Если вы используете [!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)], вам нужно будет пройти проверку подлинности с помощью аутентификации развертывания с выходом в Интернет (IFD), как описано ниже.  
  
### <a name="supported-browsers-for-outlook-on-the-web"></a>Поддерживаемые браузеры для Outlook в Интернете  
 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] с [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] можно использовать в следующих браузерах:  
  
-   [!INCLUDE[pn_IE_10](../includes/pn-ie-10.md)], [!INCLUDE[pn_ie_11](../includes/pn-ie-11.md)] или [!INCLUDE[pn_microsoft_edge](../includes/pn-microsoft-edge.md)]  
  
     Поддерживается следующая конфигурация:  
  
    -   Защищенный режим включен для зоны безопасности **Интернет**. Чтобы включить защищенный режим, в IE 10 или 11 перейдите в раздел **Сервис** > **Свойства обозревателя** > **Безопасность** > **Интернет**.  
  
    -   Защищенный режим включен для зоны безопасности **Местная интрасеть**. Чтобы включить защищенный режим, в IE 10 или 11 перейдите в раздел **Сервис** > **Свойства обозревателя** > **Безопасность** > **Местная интрасеть**.  
  
    -   Ваш URL-адрес [!INCLUDE[pn_dyn_365](../includes/pn-dyn-365.md)] находится в списке доверенных веб-сайтов зоны безопасности **Местная интрасеть**. В IE 10 или 11 перейдите в раздел **Сервис** > **Свойства обозревателя** > **вкладка Безопасность** > **Местная интрасеть** > **Сайты** > **Дополнительно**.  
  
-   [!INCLUDE[tn_Google_Chrome](../includes/tn-google-chrome.md)] (последняя версия) в [!INCLUDE[pn_ms_Windows_short](../includes/pn-ms-windows-short.md)]  
  
-   [!INCLUDE[tn_Firefox](../includes/tn-firefox.md)] (последняя версия) в [!INCLUDE[pn_ms_Windows_short](../includes/pn-ms-windows-short.md)]  
  
-   [!INCLUDE[tn_apple](../includes/tn-apple.md)] [!INCLUDE[tn_Safari](../includes/tn-safari.md)] (версия 9 или версия 10) на Mac или в OS X  
  
### <a name="supported-operating-systems-for-outlook-on-the-desktop"></a>Поддерживаемые операционные системы для Outlook на компьютере  
 Использовать [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] можно в следующих версиях [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] для компьютеров:  
  
-   [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2013 и [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016.  
  
-   [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] для Mac*.  
  
     *Требуется версия [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 15.0.847.32 или более поздняя.  
  
### <a name="supported-mobile-devices"></a>Поддерживаемые мобильные устройства  
 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] с [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] можно использовать в мобильном браузере на следующих телефонах и в следующих операционных системах:  
  
-   Устройства [!INCLUDE[tn_apple](../includes/tn-apple.md)] [!INCLUDE[tn_iphone](../includes/tn-iphone.md)] c iOS версий 8, 9 и 10.  
  
-   Телефоны [!INCLUDE[tn_android](../includes/tn-android.md)] с ОС [!INCLUDE[tn_android](../includes/tn-android.md)] 4.4 (KitKat), 5.0 (Lollipop), 6 (Marshmallow) или 7 (Nougat).  
  
-   Устройства [!INCLUDE[pn_windows_phone](../includes/pn-windows-phone.md)] с [!INCLUDE[pn_windows_8_1](../includes/pn-windows-8-1.md)] или [!INCLUDE[pn_windows_10](../includes/pn-windows-10.md)].  
  
### <a name="supported-clients-per-feature"></a>Поддерживаемые клиенты по функциям  
 Поддерживаемые функции [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] зависят от используемого клиента. В следующей таблице перечислены функции, которые поддерживаются для каждого клиента/конфигурации [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] и [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)].  
  
 ![Клиенты, поддерживаемые для каждой функции приложения Dynamics 365 App for Outlook](media/clients-supported-for-each-dynamics-365-app-for-outlook-feature.png "Клиенты, поддерживаемые для каждой функции приложения Dynamics 365 App for Outlook")  
  
 (1) [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] поддерживает [!INCLUDE[pn_IE_10](../includes/pn-ie-10.md)], [!INCLUDE[pn_ie_11](../includes/pn-ie-11.md)], [!INCLUDE[pn_microsoft_edge](../includes/pn-microsoft-edge.md)], [!INCLUDE[tn_Safari](../includes/tn-safari.md)] 9, [!INCLUDE[tn_Safari](../includes/tn-safari.md)] 10, [!INCLUDE[tn_Firefox](../includes/tn-firefox.md)] и [!INCLUDE[tn_chrome](../includes/tn-chrome.md)].  
  
 (2) Mobile [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] поддерживает [!INCLUDE[pn_windows_8_1](../includes/pn-windows-8-1.md)], [!INCLUDE[pn_windows_10](../includes/pn-windows-10.md)], [!INCLUDE[tn_ios](../includes/tn-ios.md)] 8, [!INCLUDE[tn_ios](../includes/tn-ios.md)] 9, [!INCLUDE[tn_ios](../includes/tn-ios.md)] 10, [!INCLUDE[tn_android](../includes/tn-android.md)] KitKat (4.4), [!INCLUDE[tn_android](../includes/tn-android.md)] Lollipop, [!INCLUDE[tn_android](../includes/tn-android.md)] Marshmallow и [!INCLUDE[tn_android](../includes/tn-android.md)] Nougat.  
  
 (3) Для отслеживания электронной почты в режиме создания и отслеживания встреч требуется накопительное обновление 14 для [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 2013 или [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 2016.  
  
 (4) Отслеживание контактов поддерживается только в накопительном обновлении 3 для [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 2016 и [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016 16.0.6741.1000 и более поздних версиях.  
  
 (5) Добавление шаблонов электронной почты, статей управления знаниями и литературы не поддерживается в Mobile [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)].  
  
 (6) Поддерживается только в [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016 16.0.7426.1049 и более поздних версиях.  
  
 (7) Поддерживается только в 16.0.6741.1000 и более поздних версиях.  
  
> [!NOTE]
>  Планшеты в настоящее время не поддерживаются (их поддержка планируется в обновлении 2017 г.).  
  
 [Дополнительные сведения о поддерживаемых клиентах см. в этом блоге: "Матрица поддержки приложения Dynamics 365 App for Outlook".](https://blogs.msdn.microsoft.com/crm/2016/12/13/dynamics-365-app-for-outlook-support-matrix/)  
  
### <a name="supported-servers"></a>Поддерживаемые серверы  
 [Требуемые серверы для использования надстроек Office](https://dev.office.com/docs/add-ins/overview/requirements-for-running-office-add-ins) — это [!INCLUDE[pn_Exchange_Server_2013_short](../includes/pn-exchange-server-2013-short.md)], [!INCLUDE[pn_exchange_server_2016_short](../includes/pn-exchange-server-2016-short.md)] или [!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)].  
  
### <a name="supported-languages"></a>Поддерживаемые языки  
 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] поддерживает следующие языки:  
  
||||  
|-|-|-|  
|Болгарский (Болгария) — 1026|Хинди (Индия) — 1081|Португальский (Португалия) — 2070|  
|Китайский (КНР) — 2052|Венгерский — 1038|Румынский — 1048|  
|Китайский (Тайвань) — 1028|Индонезийский — 1057|Русский — 1049|  
|Хорватский (Хорватия) — 1050|Итальянский — 1040|Сербский — 2074|  
|Чешский (Чешская республика) — 1029|Японский — 1041|Словацкий — 1051|  
|Датский — 1030|Казахский — 1087|Словенский — 1060|  
|Голландский — 1043|Корейский — 1042|Испанский — 3082|  
|Английский — 1033|Латышский — 1062|Шведский — 1053|  
|Эстонский — 1061|Литовский — 1063|Тайский — 1054|  
|Финский — 1035|Малайский — 1086|Турецкий — 1055|  
|Французский — 1036|Норвежский — 1044|Украинский — 1058|  
|Немецкий — 1031|Польский — 1045|Вьетнамский — 1066|  
|Греческий — 1032|Португальский (Бразилия) — 1046||  
  
<a name="BKMK_Deploy"></a>   
## <a name="deploy-dynamics-365-app-for-outlook"></a>Развертывание приложения Dynamics 365 App for Outlook  
 После настройки [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)] и настройки необходимых привилегий можно отправить [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] некоторым или всем пользователям, либо позволить пользователям самим выполнить установку по необходимости.  
  
> [!NOTE]
>  Если вы используете [!INCLUDE[pn_dyn_365_op](../includes/pn-dyn-365-op.md)], см. раздел ниже: [Развертывание для пользователей локальной версии Dynamics 365](#BKMK_DeployOnprem)  
  
#### <a name="to-push-the-app-to-users"></a>Отправка приложения пользователям  
  
1.  Выберите **Параметры** >  **Dynamics 365 App for Outlook**.  
  
2.  На экране **Приступая к работе с приложением Dynamics 365 App for Outlook** в разделе **Добавить для подходящих пользователей** (может потребоваться нажать **Параметры**, если этот экран открыт не в первый раз) установите флажок **Автоматическое добавление приложения в [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]**, если пользователи должны получать приложение автоматически. Если у пользователя есть соответствующие привилегии и электронная почта синхронизируется через [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)], больше ничего для отправки приложения этому пользователю делать не нужно. Например, если вы добавите необходимые привилегии в роль "Продавец", а затем назначите эту роль новому пользователю, он автоматически получит приложение.  
  
3.  Выполните одно из следующих действий:  
  
    -   Чтобы отправить приложение всем подходящим пользователям, щелкните **Добавить приложение для всех подходящих пользователей**.  
  
    -   Чтобы отправить приложение определенным пользователям, выберите этих пользователей в списке, а затем щелкните **Добавить приложение в Outlook**.  
  
    > [!TIP]
    >  Если в списке указано, что пользователь находится в состоянии ожидания или не был добавлен, можно нажать ссылку **Подробнее** рядом с пользователем, чтобы получить дополнительные сведения о его состоянии.  
  
4.  Закончив, нажмите кнопку **Сохранить**.  
  
#### <a name="to-have-users-install-the-app-themselves"></a>Самостоятельная установка приложения пользователями  
  
1.  Пользователям нужно нажать кнопку **Параметры** ![Кнопка "Параметры"](media/mp-ua-r16-settings.png "Кнопка \"Параметры\""), а затем щелкнуть **Приложения для Dynamics 365**.  
  
2.  На экране **Приложения для Dynamics 365** в разделе **[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]** пользователям нужно щелкнуть **Добавить приложение в [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]**.  
  
> [!NOTE]
>  Пользователи также могут отключить или удалить надстройку самостоятельно при необходимости. Дополнительные сведения см. в [руководстве пользователя приложения Dynamics 365 App for Outlook](http://go.microsoft.com/fwlink/p/?LinkID=613099).  
  
<a name="BKMK_DeployOnprem"></a>   
## <a name="to-deploy-to-dynamics-365-on-premises-users"></a>Развертывание для пользователей локальной версии Dynamics 365  
 Если вы используете локальную версию Dynamics 365, выполните следующие действия.  
  
-   Настройте сервер Dynamics 365 Server для развертывания с выходом в Интернет. См. [Настройка IFD для Microsoft Dynamics 365](https://technet.microsoft.com/library/dn609803.aspx).  
  
-   Если вы подключаетесь к Exchange локально, настройте поставщика OAuth и зарегистрируйте клиентские приложения. См. [Настройка Windows Server 2012 R2 для приложений Dynamics 365, в которых используется OAuth](https://technet.microsoft.com/library/hh699726.aspx).  
  
<a name="BKMK_Troubleshoot"></a>   
## <a name="troubleshooting-installation-problems"></a>Устранение неполадок при установке  
 Если у вас или ваших пользователей возникают проблемы при установке [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)], возможно, почтовый ящик пользователя [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] в настоящее время связан с другой организацией [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)]. Почтовый ящик (адрес электронной почты) [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] может синхронизировать встречи, контакты и задачи только с одной организацией, поэтому пользователь, который относится к этой организации, может синхронизировать встречи, контакты и задачи только с одним почтовым ящиком [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)].  Вы можете перезаписать параметры, хранящиеся в [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)], чтобы изменить основную организацию для синхронизации. Дополнительные сведения см. в [этой статье базы знаний](https://support.microsoft.com/en-gb/help/3211627/incomingemailrejected-error-when-attempting-to-install-dynamics-365-app-for-outlook).  
  
<a name="BKMK_Explore"></a>   
## <a name="explore-the-users-guide-and-train-your-users"></a>Знакомство с руководством пользователя и обучение пользователей  
 Инструкции по использованию [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] можно найти в [руководстве пользователя приложения Dynamics 365 App for Outlook](http://go.microsoft.com/fwlink/p/?LinkID=613099).  
  
 ![Страница руководства пользователя приложения Dynamics 365 App for Outlook](media/dynamics-365-app-for-outlook-user-s-guide-page.png "Страница руководства пользователя приложения Dynamics 365 App for Outlook")  
  
## <a name="see-also"></a>См. также  
 [Руководство пользователя приложения Dynamics 365 App for Outlook](http://go.microsoft.com/fwlink/p/?LinkID=613099)   
 [Дополнительные сведения о поддерживаемых клиентах см. в этом блоге: "Матрица поддержки приложения Dynamics 365 App for Outlook".](https://blogs.msdn.microsoft.com/crm/2016/12/13/dynamics-365-app-for-outlook-support-matrix/)   
 [Настройка синхронизации электронной почты, встреч, контактов и задач на стороне сервера](../Topic/Set%20up%20server-side%20synchronization%20of%20email,%20appointments,%20contacts,%20and%20tasks.md)   
 [Добавление пользователей, лицензий и ролей безопасности](http://msdn.microsoft.com/en-us/23612155-f92d-4871-a109-186419d5c19d)   
 [Добавление функций взаимодействия в Microsoft Dynamics 365 (сетевая версия)](../DocSets/CRMIGv9_Admin/Toc/Add%20interoperation%20features%20to%20Microsoft%20Dynamics%20365%20\(online\).md)