---
title: Использование потока неявного предоставления OAuth 2,0 на портале | MicrosoftDocs
description: Узнайте, как выполнять вызовы внешних API на стороне клиента и защищать их с помощью неявного потока предоставления OAuth на портале.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 06db149e5f86696ecffae38fe05e23198d72ecb5
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974513"
---
# <a name="use-oauth-20-implicit-grant-flow-within-your-portal"></a>Использование потока неявного предоставления OAuth 2,0 на портале 

Эта функция позволяет клиенту выполнять вызовы внешних интерфейсов API на стороне клиента и защищать их, используя неявный поток предоставления OAuth. Он предоставляет конечную точку для получения защищенных маркеров доступа, которые будут содержать сведения об удостоверении пользователя, используемые внешними API для авторизации после неявного потока предоставления OAuth 2,0. Сведения об удостоверении пользователя, выполнившего вход, передаются защищенным образом в внешние вызовы AJAX. Это не только помогает разработчикам передавать контекст проверки подлинности, но также помогает пользователям защищать свои интерфейсы API с помощью этого механизма.

Неявный поток предоставления OAuth 2,0 поддерживает конечные точки, которые клиент может вызвать для получения маркера идентификации. Для этой цели используются две конечные точки: [авторизация](#authorize-endpoint-details) и [токен](#token-endpoint-details).

## <a name="authorize-endpoint-details"></a>Авторизация сведений о конечной точке 

URL-адрес для авторизации конечной точки: `<portal_url>/_services/auth/authorize`. Точка авторизации поддерживает следующие параметры:

| Параметр   | Обязательно? | Description                             |
|---------------|-----------|---------------------------------------|
| client_id      | Да       | Строка, которая передается при выполнении вызова авторизации. Необходимо убедиться, что идентификатор клиента зарегистрирован на [портале](#register-client-id-for-implicit-grant-flow). В противном случае отображается сообщение об ошибке. Идентификатор клиента добавляется в утверждениях в маркере как `aud`, а также `appid` параметр и может использоваться клиентами для проверки того, что возвращенный токен предназначен для своего приложения.<br>Максимальная длина — 36 символов. Поддерживаются только буквенно-цифровые символы и дефисы. |
| redirect_uri      | Да       | URL-адрес портала, на котором можно отправлять и получать ответы на проверку подлинности. Он должен быть зарегистрирован для конкретного `client_id`, используемого в вызове, и должен быть точно таким же, как и зарегистрированный.            |
| С       | Нет        | Значение, включенное в запрос, которое также возвращается в ответе маркера. Это может быть строка любого содержимого, которое вы хотите использовать. Обычно для предотвращения подделки запросов между сайтами используется случайное уникальное значение.<br>Максимальная длина составляет 20 символов.              |
| требуем   | Нет        | Строковое значение, отправленное клиентом, включенное в результирующий маркер идентификации в качестве утверждения. Затем клиент может проверить это значение, чтобы устранить атаки, направленные на воспроизведение маркеров. Максимальная длина составляет 20 символов.      |
| response_type         | Нет        | Этот параметр поддерживает только `token` в качестве значения. Это позволяет приложению немедленно получать маркер доступа от конечной точки авторизации, не выполняя второй запрос для авторизации.                               |
|||

### <a name="successful-response"></a>Успешный ответ

Точка авторизации возвращает следующие значения в URL-адресе ответа как фрагмент:

- **Token**: токен возвращается в виде JSON Web Token (JWT) с цифровой подписью закрытого ключа портала.
- **State**: Если в запрос включен параметр состояния, то в ответе должно появиться то же значение. Приложение должно проверить, совпадают ли значения состояния в запросе и ответе.
- **expires_in**: период времени, в течение которого маркер доступа действителен (в секундах).

Например, успешный ответ выглядит следующим образом:

```
GET https://aadb2cplayground.azurewebsites.net/#token=eyJ0eXAiOiJKV1QiLCJhbGciOI1NisIng1dCI6Ik5HVEZ2ZEstZnl0aEV1Q&expires_in=3599&state=arbitrary_data_you_sent_earlier
```

### <a name="error-response"></a>Ошибочный ответ

Ошибка в авторизации Endpoint возвращается как документ JSON со следующими значениями:

- **Идентификатор ошибки**: уникальный идентификатор ошибки.
- **Сообщение об ошибке**: конкретное сообщение об ошибке, которое может помочь определить основную причину ошибки проверки подлинности.
- **Идентификатор корреляции**: идентификатор GUID, используемый для отладки. Если включено ведение журнала диагностики, идентификатор корреляции будет присутствовать в журналах ошибок сервера.
- **Timestamp**: Дата и время создания ошибки.

Сообщение об ошибке отображается на языке по умолчанию пользователя, выполнившего вход. Если пользователь не вошел в систему, отображается страница входа, на которой пользователь должен выполнить вход. Например, ответ на ошибку выглядит следующим образом:

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## <a name="token-endpoint-details"></a>Сведения о конечной точке токена

Вы также можете получить маркер, выполнив запрос к конечной точке `/token`. Она отличается от конечной точки авторизации тем, как конечная точка авторизации обрабатывает логику маркера на отдельной странице (redirect_uri), в то время как конечная точка токена обрабатывает логику маркера на той же странице. URL-адрес конечной точки токена: `<portal_url>/_services/auth/token`. Конечная точка токена поддерживает следующие параметры:

| Параметр   | Обязательно? | Description                             |
|---------------|-----------|---------------------------------------|
| client_id      | Нет       | Строка, которая передается при выполнении вызова авторизации. Необходимо убедиться, что идентификатор клиента зарегистрирован на [портале](#register-client-id-for-implicit-grant-flow). В противном случае отображается сообщение об ошибке. Идентификатор клиента добавляется в утверждениях в маркере как `aud`, а также `appid` параметр и может использоваться клиентами для проверки того, что возвращенный токен предназначен для своего приложения.<br>Максимальная длина — 36 символов. Поддерживаются только буквенно-цифровые символы и дефис. |
| redirect_uri      | Нет       | URL-адрес портала, на котором можно отправлять и получать ответы на проверку подлинности. Он должен быть зарегистрирован для конкретного `client_id`, используемого в вызове, и должен быть точно таким же, как и зарегистрированный.            |
| С       | Нет        | Значение, включенное в запрос, которое также возвращается в ответе маркера. Это может быть строка любого содержимого, которое вы хотите использовать. Обычно для предотвращения подделки запросов между сайтами используется случайное уникальное значение.<br>Максимальная длина составляет 20 символов.              |
| требуем   | Нет        | Строковое значение, отправленное клиентом, включенное в результирующий маркер идентификации в качестве утверждения. Затем клиент может проверить это значение, чтобы устранить атаки, направленные на воспроизведение маркеров. Максимальная длина составляет 20 символов.      |
| response_type         | Нет        | Этот параметр поддерживает только `token` в качестве значения. Это позволяет приложению немедленно получать маркер доступа от конечной точки авторизации, не выполняя второй запрос для авторизации.                               |
|||

> [!NOTE]
> Хотя параметры `client_id`, `redirect_uri`, `state`и `nonce` являются необязательными, рекомендуется использовать их, чтобы обеспечить безопасность интеграции.

### <a name="successful-response"></a>Успешный ответ

Конечная точка токена возвращает состояние и expires_in в виде заголовков ответа и маркера в тексте формы.

### <a name="error-response"></a>Ошибочный ответ

Ошибка в конечной точке маркера возвращается в виде документа JSON со следующими значениями:

- **Идентификатор ошибки**: уникальный идентификатор ошибки.
- **Сообщение об ошибке**: конкретное сообщение об ошибке, которое может помочь определить основную причину ошибки проверки подлинности.
- **Идентификатор корреляции**: идентификатор GUID, используемый для отладки. Если включено ведение журнала диагностики, идентификатор корреляции будет присутствовать в журналах ошибок сервера.
- **Timestamp**: Дата и время создания ошибки.

Сообщение об ошибке отображается на языке по умолчанию пользователя, выполнившего вход. Если пользователь не вошел в систему, отображается страница входа, на которой пользователь должен выполнить вход. Например, ответ на ошибку выглядит следующим образом:

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## <a name="validate-id-token"></a>Проверка токена идентификатора

Просто получить маркер идентификатора недостаточно для проверки подлинности пользователя; необходимо также проверить подпись маркера и проверить утверждения в маркере на основе требований вашего приложения. Конечная точка открытого маркера предоставляет открытый ключ портала, который можно использовать для проверки подписи токена, предоставленного порталом. URL-адрес конечной точки открытого маркера: `<portal_url>/_services/auth/publickey`.

## <a name="turn-implicit-grant-flow-on-or-off"></a>Включить или отключить неявный поток предоставления разрешений

По умолчанию неявный поток предоставления разрешений включен. Если вы хотите отключить неявный поток предоставления, присвойте параметру узла **Connector/имплиЦитгрантфловенаблед** значение **false**.

Если этот параметр сайта недоступен на портале, необходимо [создать новый параметр сайта](configure/configure-site-settings.md#manage-portal-site-settings) с соответствующим значением.

## <a name="configure-token-validity"></a>Настройка срока действия токена

По умолчанию маркер действителен в течение 15 минут. Если вы хотите изменить допустимость токена, присвойте параметру сайта **имплиЦитгрантфлов/токенекспиратионтиме** необходимое значение. Значение должно быть указано в секундах. Максимальное значение может быть равно 1 часу, а минимальное значение — 1 минута. Если указано неверное значение (например, буквенно-цифровые символы), то используется значение по умолчанию, равное 15 минутам. Если указать значение, превышающее максимальное значение, или меньше минимального значения, то по умолчанию будет использоваться максимальное и минимальное значения, соответственно.

Например, чтобы установить срок действия маркера равным 30 минутам, установите значение параметра сайта **имплиЦитгрантфлов/токенекспиратионтиме** равным **1800**. Чтобы установить срок действия маркера в 1 час, установите значение параметра сайта **имплиЦитгрантфлов/токенекспиратионтиме** равным **3600**.

## <a name="register-client-id-for-implicit-grant-flow"></a>Зарегистрировать идентификатор клиента для неявного потока предоставления разрешений

Необходимо зарегистрировать идентификатор клиента на портале, для которого разрешен этот поток. Чтобы зарегистрировать идентификатор клиента, необходимо создать следующие параметры сайта.

|Параметр сайта|Value|
|------|------|
|ИмплиЦитгрантфлов/Регистередклиентид|Допустимые значения идентификатора клиента, разрешенные для этого портала. Значения должны быть разделены точкой с запятой и содержать буквенно-цифровые символы и дефисы. Максимальная длина — 36 символов.|
|ИмплиЦитгрантфлов/{ClientId}/RedirectUri|Допустимые URI перенаправления, разрешенные для конкретного идентификатора клиента. Значения должны быть разделены точкой с запятой. Указанный URL-адрес должен быть допустимой веб-страницей портала.|
|||

## <a name="sample-code"></a>Пример кода

Вы можете использовать следующий пример кода, чтобы приступить к использованию неявного предоставления OAuth 2,0 с помощью API-интерфейсов порталов PowerApps.

### <a name="use-portal-oauth-token-with-an-external-web-api"></a>Использование маркера OAuth на портале с внешним веб-API

Этот пример является проектом на основе ASP.NET и используется для проверки маркера идентификации, выданного порталами PowerApps. Полный пример можно найти здесь: [Использование токена OAuth на портале с внешним веб-API](https://github.com/microsoft/PowerApps-Samples/tree/master/portals/ExternalWebApiConsumingPortalOAuthTokenSample).

### <a name="authorize-endpoint-sample"></a>Пример авторизации конечной точки

В этом примере показано, как авторизовать конечная точка возвращает маркер идентификации в виде фрагмента перенаправленного URL-адреса. Он также охватывает проверку состояния, поддерживаемую в неявном предоставлении. Этот пример можно найти здесь: [пример авторизации Endpoint](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/AuthorizeEndpoint.js).

### <a name="token-endpoint-sample"></a>Пример конечной точки токена

В этом примере показано, как можно использовать функцию Жетаусентикатионтокен для выборки маркера идентификации с помощью конечной точки маркера на порталах PowerApps. Пример можно найти здесь: [Пример конечной точки токена](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/TokenEndpoint.js).