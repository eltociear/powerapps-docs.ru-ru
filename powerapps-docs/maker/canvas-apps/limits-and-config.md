---
title: Требования к системе, ограничения и значения конфигурации | Документы Майкрософт
description: Требования к системе, ограничения и значения конфигурации для PowerApps
services: ''
suite: PowerApps
documentationcenter: na
author: skjerland
manager: kfile
editor: ''
tags: ''
ms.service: PowerApps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/07/2018
ms.author: sharik
ms.openlocfilehash: 84115ea98ec5d7d0fd60d36fc0cd3cc9196980ff
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="system-requirements-limits-and-configuration-values"></a>Требования к системе, ограничения и значения конфигурации
В этой статье приводятся требования к платформе устройств и веб-браузеру, а также ограничения и значения конфигурации для PowerApps.

## <a name="supported-platforms-for-running-apps-using-the-powerapps-app"></a>Поддерживаемые платформы для запуска приложений с помощью PowerApps
| **Минимальные требования** | **Рекомендуется** |
| --- | --- |
| iOS 9.3 или более поздней версии |iOS 10 или более поздней версии с не менее чем 2 ГБ ОЗУ |
| Android 5 или более поздней версии |Android 7 или более поздней версии с не менее чем 4 ГБ ОЗУ |
| Windows 8.1 или более поздней версии (только ПК) |Windows 10 Fall Creators Update с не менее чем 8 ГБ ОЗУ|

## <a name="supported-browsers-for-running-apps"></a>Поддерживаемые браузеры для запуска приложений
| **Браузер** | **Операционная система** |
| --- | --- |
| Google Chrome (последняя версия)<br>(рекомендуется) |Windows 7 с пакетом обновления 1, 8.1 и 10 <br>Android 5 или более поздней версии <br>iOS 8 или более поздней версии<br>macOS |
| Microsoft Edge (последняя версия)<br>(рекомендуется) |Windows 10 |
| Microsoft Internet Explorer 11 (с отключенной функцией просмотра в режиме совместимости) |Windows 7 с пакетом обновления 1, 8.1 и 10 |
| Mozilla Firefox (последняя версия) |Windows 7 с пакетом обновления 1, 8.1 и 10 <br> Android 5 или более поздней версии <br>iOS 8 или более поздней версии <br>macOS |
| Apple Safari (последняя версия) |iOS 8 или более поздней версии <br>macOS |

## <a name="supported-browsers-for-powerapps-studio-for-web"></a>Поддерживаемые браузеры для PowerApps Studio для Web
| **Браузер** | **Операционная система** |
| --- | --- |
| Google Chrome (последняя версия)<br>(рекомендуется) |Windows 7 с пакетом обновления 1, 8.1 и 10 <br>macOS |
| Microsoft Edge (последняя версия)<br>(рекомендуется) |Windows 10 |
| Microsoft Internet Explorer 11 (с отключенной функцией просмотра в режиме совместимости) |Windows 7 с пакетом обновления 1, 8.1 и 10 |

## <a name="request-limits"></a>Ограничения запросов
Эти ограничения применяются к каждому исходящему запросу:

| Имя | Ограничение |
| --- | --- |
| Время ожидания |180 с |
| Повторные попытки |4 |

> [!NOTE]
> Значение повторной попытки может меняться. Для некоторых ошибок нет необходимости повторять попытки.

## <a name="ip-addresses"></a>IP-адреса
В запросах от PowerApps используются IP-адреса, которые зависят от региона [среды](../../administrator/environments-overview.md), в которой размещено приложение. Мы не публикуем полные доменные имена, доступные для сценариев PowerApps.

Вызовы из интерфейса API, подключенного через приложение (например, API SQL или API SharePoint), поступают с IP-адреса, указанного далее в этом разделе.

Например, следует использовать эти адреса, если вам необходимо добавить в список разрешений IP-адреса для базы данных SQL Azure.

| Регион | Исходящие IP-адреса |
| --- | --- |
| Азия |52.163.91.227, 52.163.89.40, 52.163.89.65, 52.163.95.29, 13.75.89.9, 13.75.91.198, 13.75.92.202, 13.75.92.124 |
| Австралия |13.77.7.172, 13.70.191.49, 13.70.189.7, 13.70.187.251, 13.70.82.210, 13.73.203.158, 13.73.207.42, 13.73.205.35 |
| Канада |52.233.30.222, 52.233.30.148, 52.233.30.199, 52.233.29.254, 52.232.130.205, 52.229.126.118, 52.229.126.28, 52.229.123.56 |
| Европа |52.166.241.149, 52.166.244.232, 52.166.245.173, 52.166.243.169, 40.69.45.126, 40.69.45.11, 40.69.45.93, 40.69.42.254 |
| Индия |52.172.54.172, 52.172.55.107, 52.172.55.84, 52.172.51.70, 52.172.158.185, 52.172.159.100, 52.172.158.2, 52.172.155.245 |
| Япония |104.214.137.186, 104.214.139.29, 104.214.140.23, 104.214.138.174, 13.78.85.193, 13.78.84.73, 13.78.85.200, 13.78.86.229 |
| США |104.43.232.28, 104.43.232.242, 104.43.235.249, 104.43.234.211, 52.160.93.247, 52.160.91.66, 52.160.92.131, 52.160.95.100, 40.117.101.91, 40.117.98.246, 40.117.101.120, 40.117.100.191 |
| США (ранний доступ) |52.161.26.191, 52.161.27.42, 52.161.29.40, 52.161.26.33, 13.66.213.240, 13.66.214.51, 13.66.210.166, 13.66.213.29 |

## <a name="required-services"></a>Необходимые службы
Этот список содержит все службы, к которым обращается PowerApps Studio, а также сведения об их применении. Сеть **не** должна блокировать эти службы.

| Домены | Протоколы | Применение |
| --- | --- | --- |
| management.azure.com |https |RP. |
| msmanaged-na.azure-apim.net |https |Среда выполнения соединителей или интерфейсов API. |
| login.microsoft.com<br>login.windows.net<br>login.microsoftonline.com<br>secure.aadcdn.microsoftonline-p.com |https |ADAL. |
| graph.microsoft.com<br>graph.windows.net |https |Azure Graph — для получения сведений о пользователе (например, фотографии профиля). |
| gallery.azure.com |https |Примеры и шаблоны приложений. |
| *.azure-apim.net |https |Концентраторы API — разные поддомены для каждого языкового стандарта. |
| *.powerapps.com |https |Веб-аутентификация и портал. |
| *.azureedge.net |https |Веб-аутентификация. |
| *.blob.core.windows.net |https |Хранилище BLOB-объектов |
| vortex.data.microsoft.com |https |Телеметрия |