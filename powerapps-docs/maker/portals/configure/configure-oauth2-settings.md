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
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755458"
---
# <a name="configure-oauth2-provider-settings-for-portals"></a>Настройка параметров поставщика OAuth2 для порталов

Внешние поставщики удостоверений на основе OAuth 2.0 включают регистрацию "приложения" в сторонней службе для получения пары "код клиента/секрет клиента". Часто это приложение требует указания URL-адреса перенаправления, который позволяет поставщику удостоверений отправлять пользователей обратно в портал (проверяющая сторона). Код клиента и секрет клиента настраиваются как параметры сайта портала для установки безопасного подключения от проверяющий стороны к поставщику удостоверений. Параметры основаны на свойствах классов [[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]AccountAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.aspx), [TwitterAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.twitter.twitterauthenticationoptions.aspx), [FacebookAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.facebook.facebookauthenticationoptions.aspx) и [GoogleOAuth2AuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.google.googleoauth2authenticationoptions.aspx).  

Поддерживаемые поставщики:

- Учетная запись [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]
- Twitter
- Facebook
- Google
- LinkedIn
- в Yahoo.

## <a name="create-oauth-applications"></a>Создание приложений OAuth

Обычно если поставщик OAuth используются параметры приложения, которые должны содержать значение URI перенаправления, укажите <https://portal.contoso.com/or> https://portal.contoso.com/signin-\ [поставщик \] в зависимости от того, как поставщик выполняет проверку URI перенаправления (некоторые поставщики требуются полный путь URL-адреса, вместе с именем домена). Подставьте имя поставщика вместо \[provider\] в URI перенаправления.

### <a name="google"></a>Google

[Учетные данные Google OAuth2 API — Инструкции](https://developers.google.com/accounts/docs/OpenIDConnect#appsetup)  

1. Откройте [Консоль разработчиков Google](https://console.developers.google.com/)  
2. Создайте проект API или откройте существующий проект
3. Перейдите в раздел **API и аутентификация** &gt;**API** и в разделе **Social API** нажмите **Google+ API**, затем нажмите **Включить API**
4. Перейдите к **API и аутентификация** &gt;**Экран согласия**.
    - Укажите **Адрес электронной почты**.
    - Укажите настраиваемое **Название продукта**.
    - Выберите **Сохранить**.
5. Перейдите в раздел **API и аутентификация** &gt;**Учетные данные** и создайте новый идентификатор клиента.
   - Тип приложения: **Веб-приложение**
   - Утвержденные источники [!INCLUDE[pn-javascript](../../../includes/pn-javascript.md)]: https://portal.contoso.com
   - Утвержденные URI перенаправления: https://portal.contoso.com/signin-google 
   - Выберите **Создать код клиента**.

### <a name="facebook-app-settings"></a>Настройки приложения Facebook

1. Откройте [Панель мониторинга приложения разработчиков Facebook](https://developers.facebook.com/apps)  
2. Выберите **Добавить новое приложение**.
3. Выберите **Веб-сайт**.
4. Выберите **Пропустить и создать код приложения**.
    - Укажите **Отображаемое имя**.
    - Выберите **Категория**.
    - Выберите **Создать код приложения**.

5. На панели мониторинга для нового приложения перейдите к **Параметры** &gt;**Базовые** (вкладка) и добавьте следующие сведения:
    - Домены приложения (необязательно): portal.contoso.com 
    - Электронная почта контакта: *&lt;выбранный вами адрес электронной почты&gt;* 
    - Выберите **Добавить платформу**, затем выберите **Веб-сайт**. 
    - URL-адрес сайта: https://portal.contoso.com/ или https://portal.contoso.com/signin-facebook

6. Выберите **Сохранить изменения**.
7. Перейдите к **Состояние и просмотр** &gt; вкладка **Состояние**.
8. Выберите **Да**, когда будет предложено сделать приложение и все его возможности доступными широкой публике. Необходимо заполнить допустимые данные на шаге 5 выше, чтобы можно было включить данный параметр.

### <a name="includecc-microsoftincludescc-microsoftmd-application-settings"></a>Параметры приложения [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]

1. Откройте [Центр разработки для учетных записей [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]](https://account.live.com/developers/applications/index)  
2. Выберите **Создать приложение** и укажите **Имя приложения**.
3. Выберите **Принимаю**, чтобы принять условия.
4. Выберите **Параметры** &gt;**Параметры API**, затем укажите URL-адрес перенаправления в виде https://portal.contoso.com/signin-microsoft 

### <a name="twitter-apps-settings"></a>Параметры приложений Twitter

1. Откройте [Управление приложением Twitter](https://apps.twitter.com/). 
2. Выберите **Создать новое приложение**.

    - Укажите **Имя** и **Описание** для вашего приложения.
    - Задайте URL-адрес веб-сайта как https://portal.contoso.com.
    - Задайте URL-адрес обратного вызова как https://portal.contoso.com или https://portal.contoso.com/signin-twitter.

3. Выберите **Создать приложение Twitter**.

### <a name="linkedin-app-settings"></a>Настройки приложения LinkedIn

1. Откройте [Сеть разработчиков LinkedIn](https://www.linkedin.com/secure/developer).  
2. Выберите **Добавить новое приложение**.

    - Укажите **Имя приложения**, **Описание** и т. д.
    - Задайте URL-адрес веб-сайта как https://portal.contoso.com.
    - Задайте соглашение пользователя OAuth/область по умолчанию: r\_basicprofie и r\_emailaddress
    - Задайте URL-адрес перенаправления OAuth 2.0: https://portal.contoso.com/signin-linkedin.

3. Выберите **Добавить приложение**.

### <a name="yahoo-ydn-app-settings"></a>Yahoo! Настройки приложения YDN

1. Откройте [Сеть разработчиков Yahoo!](https://developer.yahoo.com/apps).
2. Выберите **Создать приложение**.
    
    - Укажите **Имя приложения**.
    - Тип приложения: **Веб-приложение**.
    - Домен обратного вызова: portal.contoso.com

3. Выберите **Создать приложение**.

## <a name="create-site-settings-by-using-oauth2"></a>Создание параметров сайта с помощью OAuth2

Панель мониторинга приложения для каждого поставщика отображается код клиента (код приложения, ключ потребителя) и секрет клиента (секрет приложения, секрет потребителя) для каждого приложения. Используйте эти два значения, чтобы настроить параметры сайта портала.

>[!Note]
> Для стандартной конфигурации OAuth2 требуются только следующие параметры (в Facebook в качестве примера):
> - `Authentication/OpenAuth/Facebook/ClientId`
> - `Authentication/OpenAuth/Facebook/ClientSecret`

Замените тег `[provider]` в имени настройки сайта именем конкретного поставщика удостоверений: Facebook, Google, Yahoo, [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)], LinkedIn или Twitter.

|**Имя настройки сайта**                                           |**Описание**                                                                                                                                                                                                                                                                                                                                      |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/ExternalLoginEnabled                | Включает или отключает вход и регистрацию внешней учетной записи. Значение по умолчанию: true                                                                                                                                                                                                                                                                         |
| Authentication/OpenAuth/\[provider\]/ClientId                   | Обязательное. Значение кода клиента из приложения поставщика. Может также называться идентификатором приложения или ключом потребителя.  Следующие имена параметра допускаются для обратной совместимости: Authentication/OpenAuth/Twitter/ConsumerKey <ul><li>Authentication/OpenAuth/Facebook/AppId</li><li>Authentication/OpenAuth/LinkedIn/ConsumerKey</li> |
| Authentication/OpenAuth/\[provider\]/ClientSecret               | Обязательное. Значение секрета клиента из приложения поставщика. Может также называться секретом приложения или секретом потребителя.  Следующие имена параметра допускаются для обратной совместимости: Authentication/OpenAuth/Twitter/ConsumerSecret <ul><li>Authentication/OpenAuth/Facebook/AppSecret</li><li>Authentication/OpenAuth/LinkedIn/ConsumerSecret</li> |
| Authentication/OpenAuth/\[provider\]/AuthenticationType         | Тип ПО промежуточного слоя для аутентификации OWIN. Пример: yahoo. [authenticationoptions.authenticationtype](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx).                                                                                                                                |  
| Authentication/OpenAuth/\[provider\]/Scope                      | Разделенный запятыми список разрешений запроса. [microsoftaccountauthenticationoptions.scope](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.scope.aspx).                                                                                                                |  
| Authentication/OpenAuth/\[provider\]/Caption                    | Текст, который пользователь может отображать в пользовательском интерфейсе входа. [microsoftaccountauthenticationoptions.caption](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.caption.aspx).                                                                                              |  
| Authentication/OpenAuth/\[provider\]/BackchannelTimeout         | Значение времени ожидания в миллисекундах для сообщений обратного канала. [microsoftaccountauthenticationoptions.backchanneltimeout](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.backchanneltimeout.aspx).                                                                         |  
| Authentication/OpenAuth/\[provider\]/CallbackPath               | Путь запроса в базовом пути приложения, где будет возвращаться пользовательский агент. [microsoftaccountauthenticationoptions.callbackpath](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.callbackpath.aspx).                                                         |  
| Authentication/OpenAuth/\[provider\]/SignInAsAuthenticationType | Имя другого промежуточного программного обеспечения проверки подлинности, которое будет отвечать за фактический выпуск **userClaimsIdentity**. [microsoftaccountauthenticationoptions.signinasauthenticationtype](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.signinasauthenticationtype.aspx). |  
| Authentication/OpenAuth/\[provider\]/AuthenticationMode         | Режим ПО промежуточного слоя для аутентификации OWIN. [security.authenticationoptions.authenticationmode](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx).                                                                                                                                       |  

### <a name="see-also"></a>См. также

[Настройка проверки подлинности портала](configure-portal-authentication.md)  
[Задание удостоверения аутентификации для портала](set-authentication-identity.md)  
[Параметры поставщика Open ID Connect для порталов](configure-openid-settings.md)   
[Параметры поставщика WS-Federation для порталов](configure-ws-federation-settings.md)  
[Параметры поставщика SAML 2.0 для порталов](configure-saml2-settings.md)
