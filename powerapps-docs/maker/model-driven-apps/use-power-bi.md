---
title: Использование Power BI с приложениями Dynamics 365 | Документация Майкрософт
ms.custom: null
ms.date: 12/07/2018
ms.reviewer: null
ms.service: crm-online
ms.suite: null
ms.tgt_pltfrm: null
ms.topic: article
applies_to:
  - Dynamics 365 for Customer Engagement  (online)
  - Dynamics 365 for Customer Engagement  Version 9.x
ms.assetid: 48997010-a47c-4e16-b7d2-f55d7a52ba19
caps.latest.revision: 36
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - admin
search.app:
  - D365CE
  - Powerplatform
---
# <a name="use-power-bi"></a>Использование Power BI

Облачная служба Power BI работает совместно с приложениями Common Data Service для предоставления решения аналитики, работающего по принципу самообслуживания. Power BI автоматически обновляет отображаемые данные приложений . Используя Power BI Desktop или Microsoft Excel, Power Query для создания отчетов и Power BI для совместного использования панелей мониторинга и обновления данных из приложений на основе модели, пользователи получают новый эффективный способ работы с данными ваших приложений.  
  
<a name="PowerBIGetstarted"></a>   
## <a name="get-started-using-power-bi-with-dynamics-365-for-customer-engagement-apps-online"></a>Начало работы с Power BI с приложениями Dynamics 365 for Customer Engagement (сетевая версия)  
 Пакеты содержимого приложений Dynamics 365 для Power BI позволяют легко получать доступ к данным о продажах, услугах или маркетинге и анализировать их.  
  
 Чтобы создать панель мониторинга Power BI с использованием пакета содержимого, соблюдайте следующие указания.  
  
1. Если вы еще этого не сделали, [зарегистрируйтесь для работы с Power BI](http://powerbi.com/).  
  
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
  
- [Загрузите файл PBIX для Dynamics CRM Online Sales Manager](http://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Sales%20Manager.pbix)  
  
- [Загрузка .PBIX менеджера по обслуживанию приложений Dynamics 365 for Customer Engagement (online)](http://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Customer%20Service%20Manager.pbix)  
  
  Power BI Report Template for Connected Field Service позволяет пользователям публиковать отчет Power BI, в котором в реальном времени отображается тактовый импульс подключенных устройств.  
  
- [Загрузка шаблона отчетности Power BI для захвата подключенныйField Service for Dynamics 365 для клиента](http://download.microsoft.com/download/E/B/5/EB5ED97A-A36A-4CAE-8C04-333A1E463B4F/PowerBI%20Report%20Template%20for%20Connected%20Field%20Service%20for%20Microsoft%20Dynamics%20365.pbix)  
  
 Дополнительные сведения о настройке пакетов содержимого см. в разделе [Настройка пакетов содержимого Power BI приложений Dynamics 365 for Customer Engagement](customize-power-bi-content-packs.md). 
  
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
  
Дополнительные сведения о том, как добавить плитки Power BI на личные панели мониторинга, см. в разделе [Внедрение плиток Power BI в личные панели мониторинга ](/dynamics365/customer-engagement/on-premises/basics/add-edit-power-bi-visualizations-dashboard.md#embed--power-bi-tiles-on-your-personal-dashboard).  
  
Дополнительные сведения о том, как добавить панели мониторинга Power BI на личные панели мониторинга, см. в разделе [Добавление панелей мониторинга Power BI на личные панели мониторинга](/dynamics365/customer-engagement/on-premises/basics/add-edit-power-bi-visualizations-dashboard.md).  
  
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
  
4. Введите URL-адрес конечной точки Dynamics 365 OData. Он должен выглядеть подобно этому URL-адресу, где *OrganizationName* — это имя организации , и **v8.1** — это версия. Нажмите **ОК**.  
  
    https://<em>OrganizationName</em>.api.crm.dynamics.com/api/data/*v8.1*  
  
> [!IMPORTANT]
> Дополнительные сведения о других версиях конечной точки см. в разделе [URL-адрес веб-API и версии]( https://msdn.microsoft.com/library/gg334391.aspx#bkmk_url_and_versions).
 
> [!TIP]
>  Вы можете найти свой URL-адрес конечной точки OData. Перейдите в раздел **Параметры** > **Настройки** > **Ресурсы для разработчиков** и найдите URL-адрес в разделе **Веб-API экземпляра**.  
  
5. В диалогом окне "Доступ к каналу OData" выберите **Учетная запись организации**, затем выберите **Подключить**.  
  
   > [!NOTE]
   >  Если вы не выполнили вход в свой экземпляр , перед нажатием кнопки "Подключить" нажмите **Вход** в диалоговом окне "Доступ к каналу OData".  
  
6. Таблицы сущностей баз данных организации отображаются в окне навигации Power BI Desktop. Можно выбрать сущности по умолчанию и настраиваемые сущности. Дополнительные сведения о создании отчетов с помощью Power BI Desktop см. в разделе [Поддержка Power BI: представление отчета в Power BI Desktop](https://powerbi.microsoft.com/documentation/powerbi-desktop-report-view/).  
  
   ![Таблица "Выберите сущность"](media/pbi-select-entity-table.PNG "Таблица \"Выберите сущность\"")  
  
   > [!TIP]
   >  Аналогичным образом можно подключиться к Dynamics 365 с помощью Excel Power Query, выбрав **Из других источников** на вкладке **Power Query** в Excel.  
  

