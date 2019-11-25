---
title: Использование Power BI с приложениями на основе модели | MicrosoftDocs
ms.custom: ''
ms.date: 10/14/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
- admin
search.app:
- D365CE
- Powerplatform
ms.openlocfilehash: a05a163e8f946f35f0b3b52d8978b1bf9be4fe8b
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755963"
---
# <a name="use-power-bi"></a>Использование Power BI

Облачная служба Power BI работает совместно с приложениями Common Data Service для предоставления решения аналитики, работающего по принципу самообслуживания. Power BI автоматически обновляет отображаемые данные приложений . Используя Power BI Desktop или Microsoft Excel, Power Query для создания отчетов и Power BI для совместного использования панелей мониторинга и обновления данных из приложений на основе модели, пользователи получают новый эффективный способ работы с данными ваших приложений.  
  
<a name="PowerBIGetstarted"></a>   
## <a name="get-started-using-power-bi-with-model-driven-apps"></a>Начало использования Power BI с приложениями на основе модели  
 
Пакеты содержимого приложений Dynamics 365 для Power BI позволяют легко получить доступ и анализировать данные в приложениях на основе модели в Dynamics 365 (Dynamics 365 Sales, Dynamics 365 Customer Service, Dynamics 365 Field Service, Dynamics 365 Marketing, Dynamics 365 Project Service Automation).  
  
 Чтобы создать панель мониторинга Power BI с использованием пакета содержимого, соблюдайте следующие указания.  
  
1. Если вы еще этого не сделали, [зарегистрируйтесь для работы с Power BI](https://powerbi.com/).  
  
2. Выполнив вход в Power BI, в области **Наборы данных** выберите **Получить данные**, в области **Службы** выберите **Получить**, затем выберите один из следующих пакетов содержимого.  
  
   - **Аналитика продаж для Dynamics 365**  
  
   - **Аналитика обслуживания клиентов для Dynamics 365**  
  
   - **Microsoft Dynamics 365 - Social Engagement**  
  
3. Для пакетов содержимого "Аналитика продаж" и "Аналитика обслуживания" введите URL-адрес вашего экземпляра , например: *<https://OrganizationName.crm.dynamics.com>*, где *OrganizationName* — имя организации вашего экземпляра приложений , и выберите **Далее**.  
  
   > [!NOTE]
   >  Если ваш центр обработки данных расположен за пределами Северной Америки, имя домена может отличаться от crm.dynamics.com, например crm2.dynamics.com, crm3.dynamics.com, crm4.dynamics.com и т. д. Чтобы выяснить имя домена, в веб-приложении приложений выберите **Параметры** > **Настройки** > **Ресурсы для разработчиков**. Перечисленные URL-адреса будут отображать правильное имя домена.  
  
    Для пакета содержимого Marketing введите URL-адрес как *<https://OrganizationName.marketing.dynamics.com/analytics>*, где *OrganizationName* представляет собой название организации вашего экземпляра Dynamics 365, и нажмите кнопку **Далее**  
  
4. В разделе **Способ проверки подлинности** выберите **oAuth2**.  
  
5. Ваши данные экземпляра будут импортированы, после чего станут доступны несколько визуализаций.  
  
> [!TIP]
>  Если выбранный пакет содержимого не открывается в вашем веб-браузере, в левой панели рабочей области Power BI нажмите пакет содержимого в пункте **Панели мониторинга**.  
  
### <a name="content-packs-available-for-download"></a>Пакеты содержимого доступны для загрузки.  
 Пакеты содержимого Dynamics 365 поддерживают готовые сущности по умолчанию для приложений. Однако можно настроить следующие пакеты содержимого, загрузив файл .PBIX, а затем используя Power BI Desktop для настройки пакета содержимого перед его отправкой в службу Power BI.  
  
- [Загрузите файл PBIX для Dynamics CRM Online Sales Manager](https://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Sales%20Manager.pbix)  
  
- [Загрузка .PBIX менеджера по обслуживанию приложений Dynamics 365 for Customer Engagement (online)](https://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Customer%20Service%20Manager.pbix)  
  
  Power BI Report Template for Connected Field Service позволяет пользователям публиковать отчет Power BI, в котором в реальном времени отображается тактовый импульс подключенных устройств.  
  
- [Загрузка шаблона отчетности Power BI для захвата подключенныйField Service for Dynamics 365 для клиента](https://download.microsoft.com/download/E/B/5/EB5ED97A-A36A-4CAE-8C04-333A1E463B4F/PowerBI%20Report%20Template%20for%20Connected%20Field%20Service%20for%20Microsoft%20Dynamics%20365.pbix)  
  
 Дополнительные сведения о настройке пакетов содержимого см. в разделе [Настройка пакетов содержимого Power BI](customize-power-bi-content-packs.md). 
  
<a name="BPI_embed"></a>   
## <a name="embed-power-bi-visualizations-on-personal-dashboards"></a>Внедрение визуализации Power BI в личные панели мониторинга  
 Для того чтобы отдельные пользователи могли встраивать визуализации Power BI в свои личные панели мониторинга, сначала должен быть включен соответствующий параметр, общий для всей организации.  
  
> [!NOTE]
>  По умолчанию встраивание визуализации Power BI выключено и должно быть включено, прежде чем пользователи смогут встраивать плитки в личные панели мониторинга.  
  
### <a name="enable-power-bi-visualizations-in-the-organization"></a>Включение визуализации Power BI в организации  
  
1. Войдите в Dynamics 365 как пользователь с ролью безопасности "системный администратор".  
  
2. Перейдите в раздел **Параметры** > **Администрирование** > **Системные параметры**.  
  
3. На вкладке **Отчеты** для параметра **Разрешить встраивание визуализации Power BI** выберите вариант **Да** для включения или вариант **Нет** для выключения возможности встраивания плиток.  
  
4. Нажмите **ОК**.  
  
Дополнительные сведения о том, как добавить плитки Power BI на личные панели мониторинга, см. в разделе [Внедрение плиток Power BI в личные панели мониторинга](/powerapps/user/add-powerbi-dashboards#embed--power-bi-tiles-on-your-personal-dashboard).  
  
Дополнительные сведения о том, как добавить панели мониторинга Power BI на личные панели мониторинга, см. в разделе [Добавление или изменение визуализаций Power BI на панели мониторинга](/powerapps/user/add-powerbi-dashboards).  
  
<a name="CRMOnline_PBIDesktop"></a>   
## <a name="use-power-bi-desktop-to-connect-directly-to-your-instance"></a>Используйте Power BI Desktop для прямого связывания с вашим экземпляром  
 Можно подключиться к вашему экземпляру с помощью Power BI Desktop для создания пользовательских отчетов и панелей мониторинга для использования со службой Power BI.  
  
### <a name="requirements"></a>Требования  
  
- Регистрация службы Power BI  
  
- Power BI Desktop  
  
- Экземпляр Dynamics 365  
  
### <a name="connect"></a>Подключать .  
  
1. Запустите Power BI Desktop.  
  
2. На вкладке "Домашняя страница" выберите **Получить данные**, затем выберите **Дополнительно**.  
  
3. В списке "Получить данные" выберите **Dynamics 365 Online**.  
  
4. Введите URL-адрес конечной точки Dynamics 365 OData. Он должен выглядеть подобно этому URL-адресу, где *OrganizationName* — это имя организации , и **v9.0** — это версия. Нажмите **ОК**.  
  
    https://<em>OrganizationName</em>.api.crm.dynamics.com/api/data/*v9.0*  
  
> [!IMPORTANT]
> Дополнительные сведения о других версиях конечной точки см. в разделе [URL-адрес веб-API и версии](/powerapps/developer/common-data-service/webapi/compose-http-requests-handle-errors#web-api-url-and-versions).
 
> [!TIP]
>  Вы можете найти свой URL-адрес конечной точки OData. Перейдите в раздел **Параметры** > **Настройки** > **Ресурсы для разработчиков** и найдите URL-адрес в разделе **Веб-API экземпляра**.  
  
5. В диалогом окне "Доступ к каналу OData" выберите **Учетная запись организации**, затем выберите **Подключить**.  
  
   > [!NOTE]
   >  Если вы не выполнили вход в свой экземпляр , перед нажатием кнопки "Подключить" нажмите **Вход** в диалоговом окне "Доступ к каналу OData".  
  
6. Таблицы сущностей баз данных организации отображаются в окне навигации Power BI Desktop. Можно выбрать сущности по умолчанию и настраиваемые сущности. Дополнительные сведения о создании отчетов с помощью Power BI Desktop см. в разделе [Поддержка Power BI: представление отчета в Power BI Desktop](https://powerbi.microsoft.com/documentation/powerbi-desktop-report-view/).  
  
   ![Выбор таблицы сущности](media/pbi-select-entity-table.PNG "Выбор таблицы сущности")  
  
   > [!TIP]
   >  Аналогичным образом можно подключиться к Dynamics 365 с помощью Excel Power Query, выбрав **Из других источников** на вкладке **Power Query** в Excel.  
  

