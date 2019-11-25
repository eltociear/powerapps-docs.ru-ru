---
title: Просмотр или загрузка ресурсов для разработчиков для PowerApps и Common Data Service | Документация Майкрософт
description: Узнайте URL-адреса ресурсов разработчика и конечных точек службы PowerApps и Common Data Service
keywords: ''
ms.date: 09/25/2019
ms.service: powerapps
ms.custom: ''
ms.topic: article
ms.assetid: e200d242-ff3f-48e5-af32-aed050e02441
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ae293843c38e7077580effd1c7670762cec91e1e
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "2700446"
---
# <a name="view-or-download-developer-resources"></a>Просмотр и загрузка ресурсов для разработчиков

На этой странице приведены ресурсы для разработчиков и сведения о конкретном экземпляре, с которым вы работаете. 

## <a name="view-the-developer-resources-page-for-your-environment"></a>Просмотр страницы ресурсов для разработчиков для вашей среды

1. На портале PowerApps нажмите ![Параметры](../../administrator/media/settings-button-nav-bar.png) кнопку "Параметры" и выберите **Дополнительные настройки**.

    ![Дополнительные настройки](media/advanced-customizations-menu.png)

1. На панели **Дополнительные настройки** выберите ссылку **Ресурсы для разработчиков**:<br />![Ссылка на ресурсы для разработчиков](media/developer-resources-link.png)

## <a name="getting-started"></a>Приступая к работе 

В этом разделе содержатся ссылки для разработчиков для поиска ресурсов. Доступны следующие ресурсы:


|Связать |Описание|
|---------|---------|
|[Центр разработчиков](https://go.microsoft.com/fwlink/?LinkId=551006)|Начните здесь с документации для разработчиков по PowerApps и Common Data Service.|
|[Сообщество/Форумы PowerApps](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1)|Задавайте и отвечайте на вопросы в сообществе PowerApps.|
|[Пакеты NuGet](https://www.nuget.org/profiles/crmsdk)|Дополнительные сведения о пакетах NuGet для добавления сборок SDK в проекты.|
|[Средства загрузки](/powerapps/developer/common-data-service/download-tools-nuget)|Инструменты, которые потребуются, доступны для загрузки из NuGet. Используйте скрипт PowerShell на этой странице для получения последних версий.|
|[Пример кода](https://go.microsoft.com/fwlink/?LinkId=553007)|Репозиторий GitHub для примеры PowerApps.|
|[Обзор для разработчика](https://go.microsoft.com/fwlink/?LinkId=550995)|Ссылка на раздел, содержащий обзор для разработчиков.|

## <a name="connect-your-apps-to-this-instance-of-common-data-service"></a>Подключите приложения к этому экземпляру Common Data Service

В этом разделе представлена информация, необходимая для подключения к вашему экземпляру Common Data Service.

### <a name="instance-web-api"></a>Веб-API экземпляра

Это URL-адрес для веб-API для вашего экземпляра. Веб-API — это OData v4 RESTful API. Можно также загрузить документ сервиса, в которых описываются метаданные и операций, доступные в вашем экземпляре. Дополнительные сведения: [Документация для разработчика. Использование веб-API Common Data Service](/powerapps/developer/common-data-service/webapi/overview)

### <a name="organization-service"></a>Служба организации

Это URL-адрес для конечной точки SOAP для сервиса организации для вашего экземпляра.
Вы можете скачать WSDL для данного сервиса здесь, но обычно будет использоваться средство создания кода CrmSvcUtil.exe для построения классов сущности для проектов .NET. Дополнительные сведения: 
- [Документация для разработчика: Создание классов сущностей с ранним связыванием с помощью средства создания кода (CrmSvcUtil.exe)](/powerapps/developer/common-data-service/org-service/generate-early-bound-classes)
- [Документация для разработчиков. Используйте службы организации, чтобы записывать и считывать метаданные](/powerapps/developer/common-data-service/org-service/overview)

### <a name="instance-reference-information"></a>Справочная информация экземпляра

Такая информация уникально описывает ваш экземпляр. Это **ID** и **Уникальное имя** GUID.
Эти сведения требуются при использовании расширений Azure с вашим экземпляром.
Дополнительные сведения: [Документация для разработчиков. Расширения Azure для Dynamics 365](/dynamics365/customer-engagement/developer/azure-extensions)

## <a name="connect-your-apps-to-the-common-data-service-discovery-service"></a>Подключить приложения к службе обнаружения Common Data Service

Поскольку пользователи могут иметь доступ к нескольким средам Common Data Service, службы обнаружения позволяют извлекать доступные среды, к которым пользователь может получить доступ на основе своих учетных данных пользователя.

### <a name="discovery-web-api"></a>Веб-API обнаружения

Это адрес конечной точки версии OData RESTful v4 сервиса обнаружения для использования для вашего экземпляра. Можно также загрузить документ сервиса здесь.
Дополнительные сведения: [Документация для разработчика. Открытие URL-адреса для своей организации с помощью веб-API](/powerapps/developer/common-data-service/webapi/discover-url-organization-web-api)


### <a name="discovery-service"></a>Служба обнаружения

Это адрес конечной точки версии SOAP сервиса обнаружения для использования для вашего экземпляра. Можно также загрузить документ сервиса здесь.
Дополнительные сведения: [Документация для разработчика. Обнаружение URL-адреса для вашей организации с помощью службы обнаружения](/dynamics365/customer-engagement/developer/org-service/discover-url-organization-organization-service)
  
