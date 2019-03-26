---
title: Просмотр или загрузка ресурсов для разработчиков | MicrosoftDocs
description: Узнайте URL-адреса конечных точек ресурсов и сервисов
keywords: ''
ms.date: 06/06/2018
ms.service: crm-online
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: e200d242-ff3f-48e5-af32-aed050e02441
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
<!-- TODO: The Developer Resources page have to be updated to match this page -->

# <a name="view-or-download-developer-resources"></a>Просмотр и загрузка ресурсов для разработчиков

На этой странице приведены ресурсы для разработчиков и сведения о конкретном экземпляре, с которым вы работаете. 

## <a name="view-the-developer-resources-page-for-your-environment"></a>Просмотр страницы ресурсов для разработчиков для вашей среды

1. На портале PowerApps выберите ![кнопку параметров](../../administrator/media/settings-button-nav-bar.png) кнопку "Параметры" и выберите **Дополнительные настройки**.

    ![Дополнительные настройки](media/advanced-customizations-menu.png)

1. На панели **Дополнительные настройки** выберите ссылку **Ресурсы для разработчиков**:<br />![Ссылка на ресурсы для разработчиков](media/developer-resources-link.png)

## <a name="getting-started"></a>Приступая к работе 

В этом разделе содержатся ссылки для разработчиков для поиска ресурсов. Доступны следующие ресурсы:


|Связать |Описание|
|---------|---------|
|[Центр разработчиков](https://go.microsoft.com/fwlink/?LinkId=551006)|Основная дочка входа для документации для разработчиков.|
|[Форумы разработчиков](https://go.microsoft.com/fwlink/?LinkId=550993)|Задавайте вопросы другим разработчикам и отвечайте на вопросы других разработчиков.|
|[Пакеты NuGet](https://go.microsoft.com/fwlink/?LinkId=550994)|Поиск пакетов NuGet для добавления сборок SDK в проекты.|
|[Средства загрузки](https://go.microsoft.com/fwlink/?LinkID=512122)|Инструменты, которые потребуются, доступны для загрузки из NuGet. Используйте скрипт PowerShell на этой странице для получения последних версий.|
|[Пример кода](https://go.microsoft.com/fwlink/?LinkId=553007)|Список доступных примеров.|
|[Обзор для разработчика](https://go.microsoft.com/fwlink/?LinkId=550995)|Ссылка на раздел, содержащий обзор для разработчиков.|

<!-- TODO update 512122 to go to https://docs.microsoft.com/dynamics365/customer-engagement/developer/download-tools-nuget -->


## <a name="connect-your-apps-to-this-instance-of-common-data-service-for-apps"></a>Свяжите свои приложения с этим экземпляром Common Data Service для приложений

В этом разделе представлена информация, необходимая для подключения к вашему экземпляру Common Data Service для приложений.

### <a name="instance-web-api"></a>Веб-API экземпляра

Это URL-адрес для веб-API для вашего экземпляра. Веб-API — это OData v4 RESTful API. Можно также загрузить документ сервиса, в которых описываются метаданные и операций, доступные в вашем экземпляре. Дополнительные сведения: [Документация для разработчиков. Использование веб-API Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-web-api)

### <a name="organization-service"></a>Служба организации

Это URL-адрес для конечной точки SOAP для сервиса организации для вашего экземпляра.
Вы можете скачать WSDL для данного сервиса здесь, но обычно будет использоваться средство создания кода CrmSvcUtil.exe для построения классов сущности для проектов .NET. Дополнительные сведения: 
- [Документация для разработчиков. Создание классов сущностей с ранним связыванием с помощью средства формирования кода (CrmSvcUtil.exe)](/dynamics365/customer-engagement/developer/org-service/create-early-bound-entity-classes-code-generation-tool)
- [Документация для разработчиков. Используйте службы организации, чтобы записывать и считывать метаданные](/dynamics365/customer-engagement/developer/org-service/use-organization-service-read-write-data-metadata)

### <a name="instance-reference-information"></a>Справочная информация экземпляра

Такая информация уникально описывает ваш экземпляр. Это **ID** и **Уникальное имя** GUID.
Эти сведения требуются при использовании расширений Azure с вашим экземпляром.
Дополнительные сведения: [Документация для разработчиков. Расширения Azure для Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/azure-extensions)

## <a name="connect-your-apps-to-the-common-data-service-for-apps-discovery-service"></a>Связывание приложения со службой обнаружения Common Data Service для приложений

Поскольку пользователи могут иметь доступ к нескольким средам CDS для приложений, службы обнаружения позволяют извлекать доступные среды, к которым пользователь может получить доступ на основе своих учетных данных пользователя.

### <a name="discovery-web-api"></a>Веб-API обнаружения

Это адрес конечной точки версии OData RESTful v4 сервиса обнаружения для использования для вашего экземпляра. Можно также загрузить документ сервиса здесь.
Дополнительные сведения: [Документация для разработчика. Открытие URL-адреса для своей организации с помощью веб-API](/dynamics365/customer-engagement/developer/webapi/discover-url-organization-web-api)


### <a name="discovery-service"></a>Служба обнаружения

Это адрес конечной точки версии SOAP сервиса обнаружения для использования для вашего экземпляра. Можно также загрузить документ сервиса здесь.
Дополнительные сведения: [Документация для разработчика. Обнаружение URL-адреса для вашей организации с помощью службы обнаружения](/dynamics365/customer-engagement/developer/org-service/discover-url-organization-organization-service)
  
### <a name="more-information"></a>Дополнительные сведения

[Документация для разработчиков. Страница ресурсов для разработчиков](/dynamics365/customer-engagement/developer/developer-resources-page)<br />
[Документация для разработчиков. Использование веб-API Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-web-api)<br />
[Документация для разработчиков. Используйте службы организации, чтобы записывать и считывать метаданные](/dynamics365/customer-engagement/developer/org-service/use-organization-service-read-write-data-metadata)<br />
[Документация для разработчиков. Расширения Azure для Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/azure-extensions)<br />
[Документация для разработчиков. Открытие URL-адреса для своей организации с помощью веб-API](/dynamics365/customer-engagement/developer/webapi/discover-url-organization-web-api)<br />
[Документация для разработчиков. Обнаружение URL-адреса для вашей организации с помощью службы обнаружения](/dynamics365/customer-engagement/developer/org-service/discover-url-organization-organization-service)
  

