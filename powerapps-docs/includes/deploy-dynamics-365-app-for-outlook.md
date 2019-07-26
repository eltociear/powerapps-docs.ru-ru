---
title: Развертывание приложения Dynamics 365 для Outlook | Документы Майкрософт
ms.custom: ''
ms.date: 2017-04-20
ms.reviewer: ''
ms.service: powerapps
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
ms.openlocfilehash: d75ec08a1d4d594136ca3339daa819cf89ee910a
ms.sourcegitcommit: 982cab99d84663656a8f73d48c6fae03e7517321
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2019
ms.locfileid: "67456781"
---
# <a name="deploy-dynamics-365-app-for-outlook"></a>Развертывание приложения Dynamics 365 для Outlook
Пользователи могут использовать [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)], чтобы получить доступ к возможностям [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] при работе с [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] на настольной системе, планшете или в Интернете. Например, просмотреть сведения о получателях электронной почты или встречи или связать адрес электронной почты или встречу [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] с записью [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)], такой как возможность, учетная запись или обращение. Дополнительные сведения о том, что предлагает [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)], см. в разделе [Руководство пользователя по приложению Dynamics 365 для Outlook](http://go.microsoft.com/fwlink/p/?LinkID=613099).  
  
> [!IMPORTANT]
>  [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] — это не то же самое, что и [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]. В версии [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)] сопряжение [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)] с [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)] является предпочтительным способом интеграции [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] с [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]. **Обратите внимание, что операции отслеживания не поддерживаются, когда [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] и [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] совместно используются одним пользователем.** Сведения о надстройке [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] см. в разделе [Руководство пользователя по Dynamics 365 для Outlook](http://go.microsoft.com/fwlink/p/?LinkID=524751).  
>   
>  [Делегированные пользователи](https://support.office.com/article/Allow-someone-else-to-manage-your-mail-and-calendar-9684B670-7588-4EEA-8717-9E5799047540) не могут использовать [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] для отслеживания сообщений электронной почты. Мы рекомендуем использовать [отслеживание на уровне папки или автоматическое отслеживание](https://www.microsoft.com/en-us/dynamics/crm-customer-center/overview-of-tracking-records-in-dynamics-365-for-outlook.aspx) для делегированных пользователей.  
  
<a name="BKMK_Compare"></a>   
## <a name="comparing-dynamics-365-app-for-outlook-with-dynamics-365-for-outlook"></a>Сравнение приложения Dynamics 365 для Outlook с Dynamics 365 для Outlook  
 В следующей таблице функции [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] сравниваются с [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] (который также называют клиентом или надстройкой [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]) для версии [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)].  
  
||||  
|-|-|-|  
|**Функция**|**[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]**|**[!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]**|  
|Отслеживание и задание записей "В отношении" для электронной почты|Да|Да|  
|Отслеживание и задание записей "В отношении" для встреч|Да|Да|  
|Отслеживание и задание записей "В отношении" для контактов|Да|Да|  
|Отслеживание и задание записей "В отношении" для задач|Нет|Да|  
|Задание записей "В отношении" одним щелчком|Да|Нет|  
|Отображение сводки по получателям|Да|Нет|  
|Отображение сводки по записям "В отношении" в сообщении электронной почты/встрече|Да|Нет|  
|Работа с [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)]|Да|Нет|  
|Работа с [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] для настольных систем|Да|Да|  
|Работа с [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] для Mac|Да|Нет|  
|Работа с телефонами|Да|Нет|  
|Открытие и создание записи [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] напрямую|Да|Да|  
|Применение пользовательских форм и бизнес-логики|Да|Да|  
|Автономная работа|Нет|Да|  
|Применение шаблонов электронной почты|Да|Да|  
|Применение литературы|Да|Да|  
|Применение статей базы знаний|Да|Да|  
|Возможность отслеживания сообщений электронной почты после отправки|Да|Нет|  
|Сортировка, фильтрация, форматирование, группирование и упорядочивание представлений|Нет|Да|  
|Создание документов слияния Word|Нет|Да|  
|Синхронизация полей управления|Нет|Да|  
  
<a name="BKMK_Requirements"></a>   
## <a name="requirements"></a>Требования  
 Для использования [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] необходимо следующее:  
  
-   [!INCLUDE[pn_crm_online_2016_update](../includes/pn-crm-online-2016-update.md)] или [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)]  
  
-   Синхронизация входящей электронной почты посредством синхронизации на стороне сервера. [!INCLUDE[proc_more_information](../includes/proc-more-information.md)][Настройка синхронизации на стороне сервера для электронной почты, встреч, контактов и задач](../Topic/Set%20up%20server-side%20synchronization%20of%20email,%20appointments,%20contacts,%20and%20tasks.md)  
  
-   Необходимые разрешения, как описано ниже  
  
> [!NOTE]
>  Поддерживаемые конфигурации и требования для функций [!INCLUDE[pn_dyn_365](../includes/pn-dyn-365.md)] перечислены в нашей документации. Если конкретные конфигурации не указаны, их следует считать неподдерживаемыми.  
  
### <a name="required-privileges"></a>Необходимые привилегии  
 [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] предоставляет доступ к [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] с помощью привилегии **Использование приложения Dynamics 365 для Outlook**. Если у пользователя нет этой привилегии, он получит следующую ошибку:  
  
> "Вам не разрешено использование этого приложения. Обратитесь к администратору системы, чтобы изменить соответствующие настройки".  
  
 Пользователи также должны обладать правами на чтение и запись для указанных ниже сущностей.  
  
 Вкладка "Управление бизнесом":  
  
-   **Почтовый ящик**  
  
 Вкладка "Настройка":  
  
-   **Сущность**  
  
-   **Поле**  
  
-   **Отношение**  
  
-   **Метаданные системного приложения**  
  
-   **Системная форма**  
  
-   **Метаданные пользовательского приложения**  
  
-   **Просмотр**  
  
##### <a name="set-the-privileges-for-a-security-role"></a>Задание привилегий для роли безопасности  
  
1.  [!INCLUDE[proc_settings_security](../includes/proc-settings-security.md)]  
  
2.  Щелкните **Роли безопасности**.  
  
3.  Выберите роль безопасности и откройте вкладку **Управление бизнесом**.  
  
4.  В разделе **Сущность** просмотрите параметры привилегий **Почтовый ящик**. Роль безопасности должна иметь настройки уровня "Пользователь" или более высокого.  
  
5.  В разделе **Привилегии, связанные с конфиденциальностью** убедитесь, что для параметра **Использование приложения Dynamics 365 для Outlook** задано значение **Организация**. Если это не так, щелкните **Использование приложения Dynamics 365 для Outlook**.  
  
### <a name="supported-configurations-with-microsoft-exchange"></a>Поддерживаемые конфигурации с Microsoft Exchange  
 В версии [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)] вы можете использовать приложение с любой комбинацией [!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)] или [!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)] и [!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)] или [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (локальная версия), включая гибридные конфигурации. Это означает, что [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] можно использовать в любой из следующих конфигураций:  
  
|||  
|-|-|  
|[!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)]|[!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]|  
|[!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)]|[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (локальная версия)|  
|[!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]|[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (локальная версия)|  
|[!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]|[!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]|  
  
> [!NOTE]
>  Если вы используете [!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)], вам потребуется пройти проверку подлинности для развертывания с выходом в Интернет, как описано ниже.  
  
### <a name="supported-browsers-for-outlook-on-the-web"></a>Поддерживаемые браузеры для Outlook в Интернете  
 Вы можете использовать [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] с [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] в следующих браузерах:  
  
-   [!INCLUDE[pn_IE_10](../includes/pn-ie-10.md)], [!INCLUDE[pn_ie_11](../includes/pn-ie-11.md)]или[!INCLUDE[pn_microsoft_edge](../includes/pn-microsoft-edge.md)]  
  
     Поддерживается следующая конфигурация:  
  
    -   Защищенный режим включен для зоны безопасности **Интернет**. Чтобы включить защищенный режим, в Internet Explorer 10 или 11 перейдите в следующий раздел: **Сервис** > **Свойства браузера** > **Вкладка "Безопасность"**  > **Интернет**.  
  
    -   Защищенный режим включен для зоны безопасности **Местная интрасеть**. Чтобы включить защищенный режим, в Internet Explorer 10 или 11 перейдите в следующий раздел: **Сервис** > **Свойства браузера** > **Вкладка "Безопасность"**  > **Местная интрасеть**.  
  
    -   Ваш URL-адрес [!INCLUDE[pn_dyn_365](../includes/pn-dyn-365.md)] указан в списке надежных узлов зоны безопасности **Местная интрасеть**. В Internet Explorer 10 или 11 перейдите в раздел **Сервис** > **Свойства браузера** > **Вкладка "Безопасность"**  > **Местная интрасеть** > **Сайты** > **Дополнительно**.  
  
-   [!INCLUDE[tn_Google_Chrome](../includes/tn-google-chrome.md)] (последняя версия) в [!INCLUDE[pn_ms_Windows_short](../includes/pn-ms-windows-short.md)]  
  
-   [!INCLUDE[tn_Firefox](../includes/tn-firefox.md)] (последняя версия) в [!INCLUDE[pn_ms_Windows_short](../includes/pn-ms-windows-short.md)]  
  
-   [!INCLUDE[tn_apple](../includes/tn-apple.md)] [!INCLUDE[tn_Safari](../includes/tn-safari.md)] (версия 9 или 10) в Mac или OSX  
  
### <a name="supported-operating-systems-for-outlook-on-the-desktop"></a>Поддерживаемые операционные системы для Outlook на настольной системе  
 Вы можете использовать [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] на следующих версиях [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] для настольной системы:  
  
-   [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2013 и [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016.  
  
-   [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] для Mac*.  
  
     Требуется *[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] версии 15.0.847.32 или более поздней.  
  
### <a name="supported-mobile-devices"></a>Поддерживаемые мобильные устройства  
 Вы можете использовать [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] с [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] в браузере мобильного устройства на любом из следующих сочетаний телефонов и операционных систем:  
  
-   Устройства [!INCLUDE[tn_apple](../includes/tn-apple.md)] [!INCLUDE[tn_iphone](../includes/tn-iphone.md)] под управлением iOS версии 8, 9 или 10.  
  
-   Телефоны [!INCLUDE[tn_android](../includes/tn-android.md)] под управлением [!INCLUDE[tn_android](../includes/tn-android.md)] 4.4 (KitKat), 5.0 (Lollipop), 6 (Marshmallow) или 7 (Nougat).  
  
-   Устройства [!INCLUDE[pn_windows_phone](../includes/pn-windows-phone.md)] под управлением [!INCLUDE[pn_windows_8_1](../includes/pn-windows-8-1.md)] или [!INCLUDE[pn_windows_10](../includes/pn-windows-10.md)].  
  
### <a name="supported-clients-per-feature"></a>Поддерживаемые клиенты для отдельных функций  
 Поддерживаемые функции [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] зависят от используемого клиента. В следующей таблице перечислены компоненты, поддерживаемые для каждого сочетания клиента и конфигурации [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] и [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)].  
  
 ![Клиенты, поддерживаемые для каждой функции приложения Dynamics 365 для Outlook](media/clients-supported-for-each-dynamics-365-app-for-outlook-feature.png "Клиенты, поддерживаемые для каждой функции приложения Dynamics 365 для Outlook")  
  
 (1) [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] поддерживает [!INCLUDE[pn_IE_10](../includes/pn-ie-10.md)], [!INCLUDE[pn_ie_11](../includes/pn-ie-11.md)], [!INCLUDE[pn_microsoft_edge](../includes/pn-microsoft-edge.md)], [!INCLUDE[tn_Safari](../includes/tn-safari.md)] 9, [!INCLUDE[tn_Safari](../includes/tn-safari.md)] 10, [!INCLUDE[tn_Firefox](../includes/tn-firefox.md)] и [!INCLUDE[tn_chrome](../includes/tn-chrome.md)].  
  
 (2) Мобильная версия [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] поддерживает [!INCLUDE[pn_windows_8_1](../includes/pn-windows-8-1.md)], [!INCLUDE[pn_windows_10](../includes/pn-windows-10.md)], [!INCLUDE[tn_ios](../includes/tn-ios.md)] 8, [!INCLUDE[tn_ios](../includes/tn-ios.md)] 9, [!INCLUDE[tn_ios](../includes/tn-ios.md)] 10, [!INCLUDE[tn_android](../includes/tn-android.md)] KitKat (4.4), [!INCLUDE[tn_android](../includes/tn-android.md)] Lollipop, [!INCLUDE[tn_android](../includes/tn-android.md)] Marshmallow и [!INCLUDE[tn_android](../includes/tn-android.md)] Nougat.  
  
 (3) Для отслеживания электронной почты в режиме создания и отслеживания встреч требуется [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 2013 с накопительным пакетом обновления 14 или [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 2016.  
  
 (4) Отслеживание контактов поддерживается только в [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)]2016 с накопительным пакетом обновления 3 и [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016 16.0.6741.1000 и более поздних версиях.  
  
 (5) Добавление шаблонов сообщений электронной почты, статей по управлению знаниями и литературы не поддерживается в мобильной версии [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)].  
  
 (6) Поддерживается только в [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016 16.0.7426.1049 и более поздних версиях.  
  
 (7) Поддерживается только в 16.0.6741.1000 и более поздних версиях.  
  
> [!NOTE]
>  Планшеты сейчас не поддерживаются (ожидается в 2017 календарном году).  
  
 [Дополнительные сведения о поддерживаемых клиентах см. в следующей записи блога: Dynamics 365 App for Outlook Support Matrix (Таблица поддержки приложения Dynamics 365 для Outlook)](https://blogs.msdn.microsoft.com/crm/2016/12/13/dynamics-365-app-for-outlook-support-matrix/)  
  
### <a name="supported-servers"></a>Поддерживаемые серверы  
 [Для использования надстроек Office серверу требуется](https://dev.office.com/docs/add-ins/overview/requirements-for-running-office-add-ins) [!INCLUDE[pn_Exchange_Server_2013_short](../includes/pn-exchange-server-2013-short.md)], [!INCLUDE[pn_exchange_server_2016_short](../includes/pn-exchange-server-2016-short.md)] или [!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)].  
  
### <a name="supported-languages"></a>Поддерживаемые языки  
 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] поддерживает следующие языки:  
  
||||  
|-|-|-|  
|Болгарский (Болгария) — 1026|Хинди (Индия) — 1081|Португальский (Португалия) — 2070|  
|Китайский (Китайская Народная Республика) — 2052|Венгерский — 1038|Румынский — 1048|  
|Китайский (Тайвань) — 1028|Индонезийский — 1057|Русский — 1049|  
|Хорватский (Хорватия) — 1050|Итальянский — 1040|Сербский — 2074|  
|Чешский (Чешская Республика) — 1029|Японский — 1041|Словацкий — 1051|  
|Датский — 1030|Казахский — 1087|Словенский — 1060|  
|Голландский — 1043|Корейский — 1042|Испанский — 3082|  
|Английский — 1033|Латышский — 1062|Шведский — 1053|  
|Эстонский — 1061|Литовский — 1063|Тайский — 1054|  
|Финский — 1035|Малайзийский — 1086|Турецкий — 1055|  
|Французский — 1036|Норвежский — 1044|Украинский — 1058|  
|Немецкий — 1031|Польский — 1045|Вьетнамский — 1066|  
|Греческий — 1032|Португальский (Бразилия) — 1046||  
  
<a name="BKMK_Deploy"></a>   
## <a name="deploy-dynamics-365-app-for-outlook"></a>Развертывание приложения Dynamics 365 для Outlook  
 После настройки [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)] и задания необходимых разрешений вы можете также принудительно отправить [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] некоторым или всем пользователям или попросить их устанавливать его самостоятельно при необходимости.  
  
> [!NOTE]
>  Если вы используете [!INCLUDE[pn_dyn_365_op](../includes/pn-dyn-365-op.md)], см. раздел ниже:  [Развертывание для пользователей локальной версии Dynamics 365](#BKMK_DeployOnprem)  
  
#### <a name="to-push-the-app-to-users"></a>Принудительная отправка приложения пользователям  
  
1.  Выберите **Параметры** >  **Приложение Dynamics 365 для Outlook**.  
  
2.  На экране **Начало работы с приложением Dynamics 365 для Outlook** в разделе **Добавить для подходящих пользователей** (если вы открываете этот экран не первый раз, может потребоваться щелкнуть элемент **Параметры**) установите флажок **Автоматическое добавление приложения в [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]** , если хотите, чтобы пользователи получили приложение автоматически. Если пользователь обладает необходимыми привилегиями, а электронная почта синхронизируется через [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)], вам не придется ничего делать, чтобы отправить ему приложение. Например, если добавить необходимые разрешения в роль продавца и затем назначить ее новому пользователю, он получит приложение автоматически.  
  
3.  Используйте один из следующих вариантов:  
  
    -   Чтобы отправить приложение всем допустимым пользователям, щелкните **Добавить приложение для всех подходящих пользователей**.  
  
    -   Чтобы отправить приложение отдельным пользователям, выберите их в списке и щелкните **Добавить приложение в Outlook**.  
  
    > [!TIP]
    >  Если в списке указано, что пользователь находится в состоянии ожидания или не был добавлен, можно щелкнуть ссылку **Подробнее** рядом с ним, чтобы найти дополнительные сведения о состоянии.  
  
4.  Закончив процедуру, нажмите кнопку **Сохранить**.  
  
#### <a name="to-have-users-install-the-app-themselves"></a>Самостоятельная установка приложения пользователями  
  
1.  Пользователи нажимают кнопку **Параметры** ![кнопка "Параметры"](media/mp-ua-r16-settings.png "кнопка \"Параметры\"") и затем щелкают элемент **Приложения для Dynamics 365**.  
  
2.  На экране **Приложения для Dynamics 365** в разделе **[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]** пользователи щелкают элемент **Добавить приложение в [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]** .  
  
> [!NOTE]
>  При необходимости пользователи также могут самостоятельно отключить или удалить надстройку. Дополнительные сведения см. в разделе [Руководство пользователя по приложению Dynamics 365 для Outlook](http://go.microsoft.com/fwlink/p/?LinkID=613099).  
  
<a name="BKMK_DeployOnprem"></a>   
## <a name="to-deploy-to-dynamics-365-on-premises-users"></a>Развертывание для пользователей локальной версии Dynamics 365  
 Если вы используете локальную версию Dynamics 365, выполните указанные ниже действия.  
  
-   Настройте сервер Dynamics 365 для развертывания с выходом в Интернет. См. раздел [Настройка развертывания с выходом в Интернет для Microsoft Dynamics 365](https://technet.microsoft.com/library/dn609803.aspx).  
  
-   Если вы подключаетесь к локальной версии Exchange, настройте поставщик OAuth и зарегистрируйте клиентские приложения. См. раздел [Настройка Windows Server 2012 R2 для приложений Dynamics 365, использующих OAuth](https://technet.microsoft.com/library/hh699726.aspx).  
  
<a name="BKMK_Troubleshoot"></a>   
## <a name="troubleshooting-installation-problems"></a>Устранение неполадок при установке  
 Если у вас или ваших пользователей возникли проблемы при установке [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)], возможно, их почтовый ящик [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] сейчас связан с другой организацией [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)]. Почтовый ящик [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] (адрес электронной почты) позволяет синхронизировать встречи, контакты и задачи только с одной организацией, а пользователь, относящийся к этой организации, может синхронизировать встречи, контакты и задачи только с одним почтовым ящиком [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)].  Вы можете перезаписать параметры, хранимые в [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)], если хотите изменить первичную организацию для синхронизации. Дополнительные сведения см. в этой [статье базы знаний](https://support.microsoft.com/en-gb/help/3211627/incomingemailrejected-error-when-attempting-to-install-dynamics-365-app-for-outlook).  
  
<a name="BKMK_Explore"></a>   
## <a name="explore-the-users-guide-and-train-your-users"></a>Изучение руководства и обучение пользователей  
 Чтобы научиться работать с [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)], [см. руководство пользователя по приложению Dynamics 365 для Outlook](http://go.microsoft.com/fwlink/p/?LinkID=613099).  
  
 ![Страница руководства пользователя по приложению Dynamics 365 для Outlook](media/dynamics-365-app-for-outlook-user-s-guide-page.png "Страница руководства пользователя по приложению Dynamics 365 для Outlook")  
  
## <a name="see-also"></a>См. также  
 [Руководство пользователя по приложению Dynamics 365 для Outlook](http://go.microsoft.com/fwlink/p/?LinkID=613099)   
 [Дополнительные сведения о поддерживаемых клиентах см. в следующей записи блога: Dynamics 365 App for Outlook Support Matrix (Таблица поддержки приложения Dynamics 365 для Outlook)](https://blogs.msdn.microsoft.com/crm/2016/12/13/dynamics-365-app-for-outlook-support-matrix/)   
 [Настройка синхронизации на стороне сервера для электронной почты, встреч, контактов и задач](../Topic/Set%20up%20server-side%20synchronization%20of%20email,%20appointments,%20contacts,%20and%20tasks.md)   
 [Добавление пользователей, лицензий и ролей безопасности](https://msdn.microsoft.com/23612155-f92d-4871-a109-186419d5c19d)   
 [Добавление функций взаимодействия в Microsoft Dynamics 365 (Online)](../DocSets/CRMIGv9_Admin/Toc/Add%20interoperation%20features%20to%20Microsoft%20Dynamics%20365%20\(online\).md)