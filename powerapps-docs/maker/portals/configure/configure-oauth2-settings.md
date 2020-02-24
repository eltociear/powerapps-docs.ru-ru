---
title: Настройка параметров поставщика OAuth2 для портала | MicrosoftDocs
description: Инструкции по добавлению и настройке параметров поставщика OAuth2 для портала.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 01/17/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 6065c842831aa9aa0c225d12470a4469fe51146d
ms.sourcegitcommit: 4349eefb1fd788f5e27d91319bc878ee9aba7a75
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2020
ms.locfileid: "3012695"
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

## <a name="google-people-api-settings"></a>Настройки API-интерфейса Google People

> [!NOTE]
> [API-интерфейс Google+](https://developers.google.com/people/legacy) устарел. Мы настоятельно рекомендуем вам перейти на [API-интерфейс Google People](https://developers.google.com/people).

Выполните следующие шаги для настройки на вашем портале Power Apps [аутентификации Google Oauth 2.0] для аутентификации пользователей.

1. Откройте [Консоль разработчиков Google](https://console.developers.google.com/).  
1. Создайте проект API или откройте существующий проект.
1. Выберите **ВКЛЮЧИТЬ API И СЕРВИСЫ** на панели мониторинга API-интерфейсов и сервисов.
1. Найдите и включите API-интерфейс **Google People API**.
1. Внутри **Google APIs** выберите **Учетные данные** на левой панели навигации.

    > [!NOTE]
    > Если у вас уже настроен экран согласия с доменом верхнего уровня порталов, вы можете пропустить шаги с 6 по 14 и сразу перейти к шагу 15. Тем не менее, выполните шаг 11, прежде чем перейти к шагу 15, если ваш экран согласия настроен, но домен верхнего уровня порталов не добавлен.

1. Выберите **НАСТРОИТЬ ЭКРАН СОГЛАСИЯ**.
1. Выберите тип пользователя **Внешний**.
1. Выберите **Создать**.
1. Введите **Имя приложения** и отправьте изображение для логотипа, если требуется.
1. Выберите подходящий **Адрес электронной почты для поддержки**.
1. Введите **powerappsportals.com** в качестве домена верхнего уровня в пункте **Авторизованные домены**. Используйте **microsoftcrmportals.com**, если вы не [обновили свое доменное имя портала Power Apps](../admin/update-portal-domain.md). Вы также можете ввести [настраиваемое доменное имя](../admin/add-custom-domain.md), если вы его настроили. 
1. Укажите требуемые ссылки на домашнюю страницу, политику конфиденциальности и условия обслуживания. 
1. Нажмите кнопку **Сохранить**.
1. Выберите **Учетные данные** из левого меню навигации.
1. Выберите **Идентификатор клиента OAuth** в раскрывающемся меню **Создать учетные данные**.
1. Выберите тип приложения **Веб-приложение**.
1. Введите **Название** для идентификатора клиента Oauth.
1. Введите URL-адрес своего портала Power Apps в списке **Разрешенные источники JavaScript**.
1. Введите **Разрешенные URI перенаправления** как URL-адрес портала Power Apps с последующим **/signin-google**. Например, если URL-адрес портала https://contoso.powerappsportals.com, поле разрешенного URI перенаправления должно быть https://contoso.powerappsportals.com/signin-google.
1. Выберите **Создать**.
1. Скопируйте **Идентификатор клиента** и **секрет клиента** из диалогового окна **клиент Oauth** и настройте [параметры сайта OAuth2](https://docs.microsoft.com/powerapps/maker/portals/configure/configure-oauth2-settings#create-site-settings-by-using-oauth2) на порталах Power Apps.

## <a name="facebook-app-settings"></a>Настройки приложения Facebook

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

### <a name="cc-microsoft-application-settings"></a>Параметры приложения [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]

1. Откройте [Центр разработки для учетных записей [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]](https://account.live.com/developers/applications/index)  
2. Выберите **Создать приложение** и укажите **Имя приложения**.
3. Выберите **Принимаю**, чтобы принять условия.
4. Выберите **Параметры** &gt;**Параметры API**, затем укажите URL-адрес перенаправления в виде https://portal.contoso.com/signin-microsoft 

## <a name="twitter-apps-settings"></a>Параметры приложений Twitter

1. Откройте [Управление приложением Twitter](https://apps.twitter.com/). 
2. Выберите **Создать новое приложение**.

    - Укажите **Имя** и **Описание** для вашего приложения.
    - Задайте URL-адрес веб-сайта как https://portal.contoso.com.
    - Задайте URL-адрес обратного вызова как https://portal.contoso.com или https://portal.contoso.com/signin-twitter.

3. Выберите **Создать приложение Twitter**.

## <a name="linkedin-app-settings"></a>Настройки приложения LinkedIn

1. Откройте [Сеть разработчиков LinkedIn](https://www.linkedin.com/secure/developer).  
2. Выберите **Добавить новое приложение**.

    - Укажите **Имя приложения**, **Описание** и т. д.
    - Задайте URL-адрес веб-сайта как https://portal.contoso.com.
    - Задайте соглашение пользователя OAuth/область по умолчанию: r\_basicprofie и r\_emailaddress
    - Задайте URL-адрес перенаправления OAuth 2.0: https://portal.contoso.com/signin-linkedin.

3. Выберите **Добавить приложение**.

## <a name="yahoo-ydn-app-settings"></a>Yahoo! Настройки приложения YDN

> [!NOTE]
> Из-за текущих проблем совместимости между обновленной конечной точкой провайдера Yahoo YDN Oauth и порталами Power Apps пользователи временно не могут проходить аутентификацию с помощью провайдера идентификации Yahoo.

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
