---
title: Настройка параметров поставщика OAuth2 для портала | MicrosoftDocs
description: Инструкции по добавлению и настройке параметров поставщика OAuth2 для портала.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: be576425067079549d3174e6d6306814a6ddb13a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542803"
---
# <a name="configure-oauth2-provider-settings-for-portals"></a>Настройка параметров поставщика OAuth2 для порталов

Внешние поставщики удостоверений на основе OAuth 2,0 подразумевают регистрацию "приложения" со сторонней службой для получения пары "идентификатор клиента" и "Секрет клиента". Часто это приложение требует указания URL-адреса перенаправления, который позволяет поставщику удостоверений передавать пользователей обратно на портал (проверяющая сторона). Идентификатор клиента и секрет клиента настраиваются как параметры сайта портала для установления безопасного подключения от проверяющей стороны к поставщику удостоверений. Параметры основаны на свойствах классов [[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]аккаунтаусентикатионоптионс](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.aspx), [твиттераусентикатионоптионс](https://msdn.microsoft.com//library/microsoft.owin.security.twitter.twitterauthenticationoptions.aspx), [фацебукаусентикатионоптионс](https://msdn.microsoft.com//library/microsoft.owin.security.facebook.facebookauthenticationoptions.aspx)и [GoogleOAuth2AuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.google.googleoauth2authenticationoptions.aspx) .  

Поддерживаются следующие поставщики:

- Учетная запись [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]
- Twitter
- Facebook
- Google
- LinkedIn
- Yahoo

## <a name="create-oauth-applications"></a>Создание приложений OAuth

В общем случае, если поставщик OAuth использует параметры приложения, для которых требуется значение URI перенаправления, укажите <https://portal.contoso.com/or> https://portal.contoso.com/signin-\ [поставщик\] в зависимости от того, как поставщик выполняет проверку URI перенаправления (некоторые поставщики нуждаются в указании полного URL-пути вместе с доменное имя). Замените имя поставщика вместо \[поставщика\] в URI перенаправления.

### <a name="google"></a>Google

[Инструкции по учетным данным API Google OAuth2](https://developers.google.com/accounts/docs/OpenIDConnect#appsetup)  

1. Открыть [консоль разработчиков Google](https://console.developers.google.com/)  
2. Создание проекта API или открытие существующего проекта
3. Перейдите к API-интерфейсам **& проверки подлинности** &gt;**API**, а затем в разделе **API социальных сетей**выберите**Google + API**, а затем —**Включить API** .
4. Перейдите в раздел**api & проверки подлинности** &gt;**согласия экрана**.
    - Укажите**адрес электронной почты**.
    - Укажите пользовательское**имя продукта**.
    - Нажмите кнопку**сохранить**.
5. Перейдите в раздел**api & Проверка подлинности** &gt;**учетные данные** и создайте новый идентификатор клиента.
   - Тип приложения:**веб-приложение**
   - Зарегистрированные источники [!INCLUDE[pn-javascript](../../../includes/pn-javascript.md)]: https://portal.contoso.com
   - Зарегистрированные URI перенаправления: https://portal.contoso.com/signin-google 
   - Выберите **создать идентификатор клиента**.

### <a name="facebook-app-settings"></a>Параметры приложения Facebook

1. Открыть [панель мониторинга приложений для разработчиков Facebook](https://developers.facebook.com/apps)  
2. Выберите **Добавить новое приложение**.
3. Выберите **веб-сайт**.
4. Выберите **Пропустить и создать идентификатор приложения**.
    - Укажите **Отображаемое имя**.
    - Выберите **категорию**.
    - Выберите **создать идентификатор приложения**.

5. На панели мониторинга для нового приложения перейдите в раздел **параметры** &gt;**Basic** (вкладка) и добавьте следующие сведения.
    - Домены приложений (необязательно): portal.contoso.com 
    - Контактный адрес электронной почты: *&lt;адреса электронной почты по своему усмотрению&gt;* 
    - Выберите **Добавить платформу**, а затем выберите **веб-сайт**. 
    - URL-адрес сайта: https://portal.contoso.com/ или https://portal.contoso.com/signin-facebook

6. Нажмите кнопку **сохранить изменения**.
7. Перейдите на вкладку **состояние & проверка** **состояния** &gt;.
8. При появлении запроса на предоставление общего доступа к приложению и всем его функциям выберите **Да** . Чтобы включить этот параметр, необходимо заполнить допустимые данные на шаге 5 выше.

### <a name="includecc-microsoftincludescc-microsoftmd-application-settings"></a>[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] параметры приложения

1. [Центр разработчиков[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] для учетных записей](https://account.live.com/developers/applications/index)  
2. Выберите **создать приложение** и укажите **имя приложения**.
3. Выберите **я принимаю** , чтобы принять условия.
4. Перейдите в раздел **параметры** &gt;**Параметры API**, а затем задайте для URL-адреса перенаправления значение https://portal.contoso.com/signin-microsoft 

### <a name="twitter-apps-settings"></a>Параметры приложений Twitter

1. Откройте [Управление приложениями Twitter](https://apps.twitter.com/). 
2. Выберите **создать новое приложение**.

    - Укажите **имя** и **Описание** приложения.
    - Задайте для URL-адреса веб-сайта https://portal.contoso.com.
    - Задайте URL-адрес обратного вызова как https://portal.contoso.com или https://portal.contoso.com/signin-twitter.

3. Выберите **создать приложение Twitter**.

### <a name="linkedin-app-settings"></a>Параметры приложения LinkedIn

1. Откройте [сеть для разработчиков LinkedIn](https://www.linkedin.com/secure/developer).  
2. Выберите **Добавить новое приложение**.

    - Укажите **имя приложения**, **Описание**и т. д.
    - Задайте для URL-адреса веб-сайта https://portal.contoso.com.
    - Задать соглашение пользователя OAuth/область по умолчанию: r\_басикпрофие и r\_EmailAddress
    - Укажите URL-адрес перенаправления OAuth 2,0: https://portal.contoso.com/signin-linkedin.

3. Выберите **Добавить приложение**.

### <a name="yahoo-ydn-app-settings"></a>Компании Параметры приложения ИДН

1. Откройте [сеть разработчиков Yahoo!](https://developer.yahoo.com/apps).
2. Выберите **создать приложение**.
    
    - Укажите **имя приложения**.
    - Тип приложения: **веб-приложение**.
    - Домен обратного вызова: portal.contoso.com

3. Выберите **создать приложение**.

## <a name="create-site-settings-by-using-oauth2"></a>Создание параметров сайта с помощью OAuth2

На панели мониторинга приложения для каждого поставщика будет отображаться идентификатор клиента (идентификатор приложения, ключ клиента) и секрет клиента (секрет приложения, секрет потребителя) для каждого приложения. Используйте эти два значения для настройки параметров сайта портала.

>[!Note]
> Для стандартной конфигурации OAuth2 требуются только следующие параметры (например, Facebook):
> - `Authentication/OpenAuth/Facebook/ClientId`
> - `Authentication/OpenAuth/Facebook/ClientSecret`

Замените тег `[provider]` в имени параметра сайта на определенное имя поставщика удостоверений: Facebook, Google, Yahoo,[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)], LinkedIn или Twitter.

|**Имя параметра сайта**                                           |**Description;**                                                                                                                                                                                                                                                                                                                                      |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Проверка подлинности/регистрация/Екстерналлогиненаблед                | Включает или отключает вход и регистрацию внешней учетной записи. Значение по умолчанию: true                                                                                                                                                                                                                                                                         |
| Поставщик проверки подлинности, OpenAuth и\[\]/Клиентид                   | Обязательно. Значение идентификатора клиента из приложения поставщика. Его также можно называть ИДЕНТИФИКАТОРом приложения или ключом потребителя.  Следующие имена параметров разрешены для обеспечения обратной совместимости: Authentication/OpenAuth/Twitter/ConsumerKey <ul><li>Authentication/OpenAuth/Facebook/AppId</li><li>Authentication/OpenAuth/LinkedIn/ConsumerKey</li> |
| Поставщик проверки подлинности, OpenAuth и\[\]/Клиентсекрет               | Обязательно. Значение секрета клиента из приложения поставщика. Он также может называться секретом приложения или секретом клиента.  Следующие имена параметров разрешены для обеспечения обратной совместимости: Authentication/OpenAuth/Twitter/ConsumerSecret <ul><li>Authentication/OpenAuth/Facebook/AppSecret</li><li>Authentication/OpenAuth/LinkedIn/ConsumerSecret</li> |
| Поставщик проверки подлинности, OpenAuth и\[\]/Аусентикатионтипе         | Тип по промежуточного слоя проверки подлинности OWIN. Пример: Yahoo. [authenticationoptions. AuthenticationType](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx).                                                                                                                                |  
| Поставщик проверки подлинности, OpenAuth и\[\]/Scope                      | Разделенный запятыми список разрешений для запроса. [микрософтаккаунтаусентикатионоптионс. Scope](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.scope.aspx).                                                                                                                |  
| Поставщик проверки подлинности, OpenAuth и\[\]/Каптион                    | Текст, который пользователь может отображать в пользовательском интерфейсе входа. [микрософтаккаунтаусентикатионоптионс. Caption](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.caption.aspx).                                                                                              |  
| Поставщик проверки подлинности, OpenAuth и\[\]/Баккчаннелтимеаут         | Значение времени ожидания в миллисекундах для обмена данными с обратным каналом. [микрософтаккаунтаусентикатионоптионс. баккчаннелтимеаут](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.backchanneltimeout.aspx).                                                                         |  
| Поставщик проверки подлинности, OpenAuth и\[\]/Каллбаккпас               | Путь запроса в базовом пути приложения, по которому будет возвращен агент пользователя. [микрософтаккаунтаусентикатионоптионс. каллбаккпас](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.callbackpath.aspx).                                                         |  
| Поставщик проверки подлинности, OpenAuth и\[\]/Сигнинасаусентикатионтипе | Имя другого промежуточного слоя проверки подлинности, которое будет отвечать за фактический выпуск**усерклаимсидентити**. [микрософтаккаунтаусентикатионоптионс. сигнинасаусентикатионтипе](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.signinasauthenticationtype.aspx). |  
| Поставщик проверки подлинности, OpenAuth и\[\]/Аусентикатионмоде         | Режим по промежуточного слоя для проверки подлинности OWIN. [Security. authenticationoptions. authenticationmode](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx).                                                                                                                                       |  

### <a name="see-also"></a>См. также

[Настройка проверки подлинности на портале](configure-portal-authentication.md)  
[Настройка удостоверения для проверки подлинности на портале](set-authentication-identity.md)  
[Параметры поставщика Connect Open ID для порталов](configure-openid-settings.md)   
[Параметры поставщика WS-Federation для порталов](configure-ws-federation-settings.md)  
[Параметры поставщика SAML 2,0 для порталов](configure-saml2-settings.md)
