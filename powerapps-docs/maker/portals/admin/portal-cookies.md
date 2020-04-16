---
title: Файлы cookie в порталах Power Apps | Документация Майкрософт
description: Узнайте, как порталы Power Apps используют файлы cookie.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 03/10/2020
ms.author: nenandw
ms.reviewer: tapanm
ms.openlocfilehash: 13730a4faa284890136cc04d2f56ff50c46d42e2
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2020
ms.locfileid: "3136668"
---
# <a name="cookies-in-power-apps-portals"></a>Файлы cookie в порталах Power Apps

Файл cookie — это небольшой файл, отправляемый с веб-сайта на устройство посетителя браузером. Один веб-сеанс может использовать несколько файлов cookie.

Порталы Power Apps также используют файлы cookie для хранения информации в различных целях. В следующем разделе перечислены и описаны файлы cookie, которые порталы Power Apps используют:

## <a name="names-and-descriptions-of-cookies-used-by-portals"></a>Названия и описания файлов cookie, используемых порталами

#### <a name="arraffinity"></a>ARRAffinity

Добавляется автоматически веб-сайтами Azure и обеспечивает балансировку нагрузки между различными сайтами. Не хранит никакой пользовательской информации.

####  <a name="aspnet-session-id"></a>Идентификатор сеанса ASP.Net

Используется для поддержки сеанса вошедшего в систему пользователя, чтобы избежать повторного входа. Файл cookie не является постоянным и удаляется после закрытия сеанса.

#### <a name="dynamics-365-portal-analytics"></a>Аналитики портала Dynamics 365

Критический служебный файл cookie для анонимного анализа использования сервиса и агрегирования для статистических целей.

#### <a name="contextlanguagecode"></a>ContextLanguageCode

Хранит язык по умолчанию для пользователя, обращающегося к порталу в сеансе и на разных веб-страницах. Файл cookie удаляется после закрытия сеанса.

#### <a name="aspnetapplicationcookie"></a>.AspNet.ApplicationCookie

Используется для идентификации сеансов пользователя. Сеанс пользователя начинается, когда пользователь впервые просматривает портал. И заканчивается, когда сеанс закрыт. [Параметры аутентификации сайта](https://docs.microsoft.com/powerapps/maker/portals/configure/set-authentication-identity) может использоваться для изменения периода истечения сеанса.

#### <a name="__requestverificationtoken"></a>__RequestVerificationToken 

Используемые системой [против подделки](https://docs.microsoft.com/dotnet/api/system.web.helpers.antiforgeryconfig.cookiename).

#### <a name="adxpreviewunpublishedentities"></a>adxPreviewUnpublishedEntities

Содержит режим предварительного просмотра **ВКЛ/ВЫКЛ**, используемый в классической системе CMS для администраторов портала.

#### <a name="adx-notification"></a>adx-notification

Используется в действиях формы сущности для хранения оповещения, которое будет отображаться при перенаправлении.

#### <a name="timezonecode"></a>timezoneCode

Содержит значение поля *timezonecode* сущности *CRM timezonedefinition* для текущего часового пояса.

#### <a name="timezoneoffset"></a>timezoneoffset

Содержит [разница часовых поясов](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date/getTimezoneOffset) между временем UTC и местным временем в браузере.

#### <a name="isdstsupport"></a>isDSTSupport

Указывает, попадают ли указанная дата и время в диапазон летнего времени.

#### <a name="isdstobserved"></a>isDSTObserved

Сохраняет значение, чтобы указать, относится ли текущий момент к летнее время.

### <a name="see-also"></a>См. также

[Параметры сайта проверки подлинности файлов cookie](https://docs.microsoft.com/powerapps/maker/portals/configure/set-authentication-identity#cookie-authentication-site-settings)

