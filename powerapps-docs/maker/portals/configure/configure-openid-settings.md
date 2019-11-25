---
title: Настройка параметров поставщика OpenID Connect для портала | MicrosoftDocs
description: Инструкции по добавлению и настройке параметров поставщика OpenID Connect для портала.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 2b4d31165ccd12b2cb5c8c2a4c8ec6f9dd04a7c7
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755370"
---
# <a name="configure-open-id-connect-provider-settings-for-portals"></a>Настройка параметров поставщика Open ID Connect для порталов

Внешние поставщики удостоверений [OpenID Connect](https://openid.net/connect/) — это службы, соответствующие [спецификациям Open ID Connect](https://openid.net/developers/specs/). Интеграция поставщика включает в себя поиск URL-адреса центра (или издателя), связанного с поставщиком. URL-адрес конфигурации может быть определен с помощью центра, который поставляет метаданные, необходимые в ходе бизнес-процесса проверки подлинности. Параметры поставщика основаны на свойствах класса [OpenIdConnectAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.aspx).

Примеры URL-адресов центра:

- [Google](https://developers.google.com/identity/protocols/OpenIDConnect): <https://accounts.google.com/><https://accounts.google.com/.well-known/openid-configuration>
- [[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]](https://msdn.microsoft.com/library/azure/mt168838.aspx): [https://login.microsoftonline.com/&lt;Приложение [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD &gt;/](https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration)

Каждый поставщик OpenID Connect также требует регистрации приложения (подобно поставщику OAuth 2.0) и получения идентификатора клиента. URL-адрес центра и созданный идентификатор клиента приложения необходимы для включения внешней проверки подлинности между порталом и поставщиком удостоверений.

> [!Note]
> Конечная точка Google OpenID Connect в настоящее время не поддерживается, поскольку лежащие в основе библиотеки еще находятся на ранних стадиях выпуска и требуют устранения проблем совместимости. Вместо этого можно использовать конечную точку [параметров поставщика OAuth2 для порталов](configure-oauth2-settings.md).

## <a name="openid-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>Параметры OpenID для [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]

Чтобы начать работу, выполните вход на [Портал управления [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal) и создайте или выберите существующий каталог. Когда каталог будет доступен, следуйте инструкциям, чтобы [добавить приложение](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) в каталог.  

1. В меню **Приложения** этого каталога выберите **Добавить**.
2. Выберите **Добавить приложение, разрабатываемое моей организацией**.
3. Укажите настраиваемое **имя** для приложения и выберите тип **Веб-приложение и/или веб-API**.
4. Для параметров **URL-адрес входа** и **URI кода приложения** укажите URL-адрес портала для обоих полей https://portal.contoso.com/
5. На этом этапе создается новое приложение. Перейдите в раздел **Настроить** в этом меню.

    В разделе **единый вход** обновите первую запись **URL-адрес ответа** для включения пути в URL-адрес: https://portal.contoso.com/signin-azure-ad. Это соответствует значению настройки сайта **RedirectUri**

6. В разделе **свойства** найдите поле **идентификатор клиента**. Это соответствует значению настройки сайта **ClientId**.
7. В меню нижнего колонтитула выберите **Просмотр конечных точек** и проверьте поле **Документ метаданных федерации**

Левая часть URL-адреса представляет собой значение **Центр** и имеет один из следующих форматов:

- https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/
- https://login.microsoftonline.com/contoso.onmicrosoft.com/

Чтобы получить URL-адрес конфигурации службы, замените конечную часть пути FederationMetadata/2007-06/FederationMetadata.xml на путь .well-known/openid-configuration. Например, <https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration>

Это соответствует значению настройки сайта **MetadataAddress**.

### <a name="related-site-settings"></a>Связанные параметры сайта

Примените параметры сайта портала, учитывая указанное выше приложение.

> [!Note]
> Стандартная конфигурация [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD использует только следующие параметры (с примерами значений):                                 
> - Authentication/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/Authority — <https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/>                                                    
> - Authentication/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/ClientId - fedcba98-7654-3210-fedc-ba9876543210                                      
>   Идентификатор клиента и URL-адрес центра не содержат одинакового значения и их следует получить отдельно.           
> - Authentication/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/RedirectUri — https://portal.contoso.com/signin-azure-ad
 
Несколько поставщиков удостоверений можно настроить, подставляя метку для тега \[provider\]. Каждая уникальная метка образует группу параметров, связанных с поставщиком удостоверений. Примеры: [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD, MyIdP


|                          Имя настройки сайта                           |                                                                                                                                                                                                         Описание                                                                                                                                                                                                          |
|----------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           Authentication/Registration/ExternalLoginEnabled           |                                                                                                                                                                         Включает или отключает вход и регистрацию внешней учетной записи. Значение по умолчанию: true                                                                                                                                                                         |
|         Authentication/OpenIdConnect/\[provider\]/Authority          |                                               Обязательное. Центр для использования при вызовах OpenIdConnect. Пример: `https://login.microsoftonline.com/contoso.onmicrosoft.com/`. Дополнительные сведения: [OpenIdConnectAuthenticationOptions.Authority](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.authority.aspx).                                                |
|      Authentication/OpenIdConnect/\[provider\]/MetadataAddress       | Конечная точка обнаружения для получения метаданных. Обычно заканчивается на путь: /.well-known/openid-configuration . Пример: `https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration`. Дополнительные сведения: [OpenIdConnectAuthenticationOptions.MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.metadataaddress.aspx). |
|     Authentication/OpenIdConnect/\[provider\]/AuthenticationType     |                                   Тип ПО промежуточного слоя для аутентификации OWIN. Укажите значение издателя в метаданных конфигурации службы. Пример: `https://sts.windows.net/contoso.onmicrosoft.com/`. Дополнительные сведения: [AuthenticationOptions.AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx).                                   |
|          Authentication/OpenIdConnect/\[provider\]/ClientId          |                                                  Обязательное. Значение кода клиента из приложения поставщика. Может также называться "Идентификатором приложения" или "Ключом потребителя". Дополнительные сведения: [OpenIdConnectAuthenticationOptions.ClientId](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.clientid.aspx).                                                   |
|        Authentication/OpenIdConnect/\[provider\]/ClientSecret        |                                              Значение секрета клиента из приложения поставщика. Может также называться "Секретом приложения" или "Секретом потребителя". Дополнительные сведения: [OpenIdConnectAuthenticationOptions.ClientSecret](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.clientsecret.aspx).                                              |
|        Authentication/OpenIdConnect/\[provider\]/RedirectUri         |                                                        Рекомендуемый. Конечная точка пассивного AD FS WS-Federation. Пример: https://portal.contoso.com/signin-saml2. Дополнительные сведения: [OpenIdConnectAuthenticationOptions.RedirectUri](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.redirecturi.aspx).                                                        |
|          Authentication/OpenIdConnect/\[provider\]/Caption           |                                                              Рекомендуемый. Текст, который пользователь может отображать в пользовательском интерфейсе входа. По умолчанию: \[provider\]. Дополнительные сведения: [OpenIdConnectAuthenticationOptions.Caption](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.caption.aspx).                                                               |
|          Authentication/OpenIdConnect/\[provider\]/Resource          |                                                                                                       "ресурс". Дополнительные сведения: [OpenIdConnectAuthenticationOptions.Resource](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.resource.aspx).                                                                                                        |
|        Authentication/OpenIdConnect/\[provider\]/ResponseType        |                                                                                                Тип "response\_type". Дополнительные сведения: [OpenIdConnectAuthenticationOptions.ResponseType](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.responsetype.aspx).                                                                                                 |
|           Authentication/OpenIdConnect/\[provider\]/Scope            |                                                                                Разделенный пробелами список разрешений запроса. Значение по умолчанию: openid. Дополнительные сведения: [OpenIdConnectAuthenticationOptions.Scope ](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.scope.aspx).                                                                                 |
|        Authentication/OpenIdConnect/\[provider\]/CallbackPath        |                      Необязательный ограниченный путь, по которому будут обрабатываться обратные вызовы аутентификации. Если не указан и доступен RedirectUri, это значение будет создано из RedirectUri. Дополнительные сведения: [OpenIdConnectAuthenticationOptions.CallbackPath](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.callbackpath.aspx).                      |
|     Authentication/OpenIdConnect/\[provider\]/BackchannelTimeout     |                                                                Значение времени ожидания для сообщений обратного канала. Пример: 00:05:00 (5 мин). Дополнительные сведения: [OpenIdConnectAuthenticationOptions.BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.backchanneltimeout.aspx).                                                                |
| Authentication/OpenIdConnect/\[provider\]/RefreshOnIssuerKeyNotFound |                                      Определяет, требуется ли пытаться обновить метаданные после SecurityTokenSignatureKeyNotFoundException. Дополнительные сведения: [OpenIdConnectAuthenticationOptions.RefreshOnIssuerKeyNotFound](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.refreshonissuerkeynotfound.aspx).                                       |
|      Authentication/OpenIdConnect/\[provider\]/UseTokenLifetime      |                                               Показывает, что время жизни сеанса аутентификации (например, файлов cookie) должно соответствовать времени жизни токена аутентификации. Дополнительные сведения: [OpenIdConnectAuthenticationOptions.UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.usetokenlifetime.aspx).                                               |
|     Authentication/OpenIdConnect/\[provider\]/AuthenticationMode     |                                                                                                     Режим ПО промежуточного слоя для аутентификации OWIN. Дополнительные сведения: [AuthenticationOptions.AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx).                                                                                                     |
| Authentication/OpenIdConnect/\[provider\]/SignInAsAuthenticationType |                                                   AuthenticationType, используемый при создании System.Security.Claims.ClaimsIdentity. Дополнительные сведения: [OpenIdConnectAuthenticationOptions.SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.signinasauthenticationtype.aspx).                                                   |
|   Authentication/OpenIdConnect/\[provider\]/PostLogoutRedirectUri    |                                                                                 "post\_logout\_redirect\_uri". Дополнительные сведения: [OpenIdConnectAuthenticationOptions.PostLogoutRedirectUri](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.postlogoutredirecturi.aspx).                                                                                 |
|       Authentication/OpenIdConnect/\[provider\]/ValidAudiences       |                                                                                                  Разделенный запятыми список URL-адресов аудитории. Дополнительные сведения: [TokenValidationParameters.AllowedAudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx).                                                                                                  |
|        Authentication/OpenIdConnect/\[provider\]/ValidIssuers        |                                                                                                       Разделенный запятыми список URL-адресов издателя. Дополнительные сведения: [TokenValidationParameters.ValidIssuers](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.validissuers.aspx).                                                                                                       |
|         Authentication/OpenIdConnect/\[provider\]/ClockSkew          |                                                                                                                                                                                        Расхождение часов, применяемое при проверки значений времени.                                                                                                                                                                                        |
|       Authentication/OpenIdConnect/\[provider\]/NameClaimType        |                                                                                                                                                                              Тип требования, используемый ClaimsIdentity для хранения требования имени.                                                                                                                                                                              |
|       Authentication/OpenIdConnect/\[provider\]/RoleClaimType        |                                                                                                                                                                              Тип требования, используемый ClaimsIdentity для хранения требования роли.                                                                                                                                                                              |
|   Authentication/OpenIdConnect/\[provider\]/RequireExpirationTime    |                                                                                                                                                                              Значение, указывающее, должны ли токены иметь значение "окончание срока действия".                                                                                                                                                                              |
|    Authentication/OpenIdConnect/\[provider\]/RequireSignedTokens     |                                                                                                                               Значение, указывающее, может ли System.IdentityModel.Tokens.SecurityToken xmlns=<https://ddue.schemas.microsoft.com/authoring/2003/5> быть действительным, если не подписан.                                                                                                                                |
|      Authentication/OpenIdConnect/\[provider\]/SaveSigninToken       |                                                                                                                                                                        Логическое значение, определяющее, сохраняется ли исходный токен при создании сеанса.                                                                                                                                                                        |
|       Authentication/OpenIdConnect/\[provider\]/ValidateActor        |                                                                                                                                                            Значение, указывающее, должен ли System.IdentityModel.Tokens.JwtSecurityToken.Actor быть проверенным.                                                                                                                                                            |
|      Authentication/OpenIdConnect/\[provider\]/ValidateAudience      |                                                                                                                                                                       Логическое значение, которое определяет, будет ли проверяться аудитория во время проверки токена.                                                                                                                                                                        |
|       Authentication/OpenIdConnect/\[provider\]/ValidateIssuer       |                                                                                                                                                                        Логическое значение, которое определяет, будет ли проверяться издатель во время проверки токена.                                                                                                                                                                         |
|      Authentication/OpenIdConnect/\[provider\]/ValidateLifetime      |                                                                                                                                                                       Логическое значение, которое определяет, будет ли проверяться срок жизни во время проверки токена.                                                                                                                                                                        |
|  Authentication/OpenIdConnect/\[provider\]/ValidateIssuerSigningKey  |                                                                                                                  Логическое значение, которое определяет, вызывается ли проверка System.IdentityModel.Tokens.SecurityKey, которым подписан securityToken xmlns=<https://ddue.schemas.microsoft.com/authoring/2003/5>.                                                                                                                  |
|                                                                      |                                                                                                                                                                                                                                                                                                                                                                                                                              |

## <a name="enable-authentication-using-a-multi-tenant-azure-active-directory-application"></a>Включение проверки подлинности с помощью приложения Azure Active Directory с несколькими клиентами

Можно настроить портал, чтобы он принимал пользователей [!include[](../../../includes/pn-azure-active-directory.md)] от любого клиента в [!include[](../../../includes/pn-azure-shortest.md)], а не только от конкретного клиента, с помощью приложения с несколькими клиентами, зарегистрированного в [!include[](../../../includes/pn-azure-active-directory.md)]. Чтобы включить поддержку нескольких клиентов, установите для переключателя **С несколькими клиентами** значение **Да** в приложении [!include[](../../../includes/pn-azure-active-directory.md)].

![Включение поддержки нескольких клиентов в приложении Azure Active Directory](../media/enable-multi-tenancy.png "Включение поддержки нескольких клиентов в приложении Azure Active Directory")

### <a name="related-site-settings"></a>Связанные параметры сайта

Несколько поставщиков удостоверений можно настроить, подставляя метку для тега [provider]. Каждая уникальная метка образует группу параметров, связанных с поставщиком удостоверений. Можно создать или настроить следующие параметры сайта в порталах для поддержки проверки подлинности по [!include[](../../../includes/pn-azure-active-directory.md)] с помощью приложения с несколькими клиентами:

|Имя настройки сайта    |Описание   |
|---|---|
|Authentication/OpenIdConnect/[provider]/Authority   |Центр для использования при вызовах OpenIdConnect. Например: `https://login.microsoftonline.com/common`   |
|Authentication/OpenIdConnect/[provider]/ClientId   |Значение кода клиента из приложения поставщика. Может также называться идентификатором приложения или ключом потребителя.   |
|Authentication/OpenIdConnect/[provider]/ExternalLogoutEnabled   |Включает или отключает выход и регистрацию внешней учетной записи. Задайте это значение как True.   |
|Authentication/OpenIdConnect/[provider]/IssuerFilter   |Фильтр на основе подстановочных знаков, который соответствует всем эмитентам по всем клиентам. В большинстве случаев используйте значение: `https://sts.windows.net/*/`   |
|Authentication/OpenIdConnect/[provider]/RedirectUri  |URL-адрес расположения ответа, по которому поставщик отправляет отклик проверки подлинности. Например: `https://portal.contoso.com/signin-oidc` |
|Authentication/OpenIdConnect/[provider]/ValidateIssuer   |Логическое значение, которое определяет, будет ли проверяться издатель во время проверки токена. Задайте это значение как False.   |
|||

### <a name="see-also"></a>См. также
[Настройка проверки подлинности портала](configure-portal-authentication.md)  
[Задание удостоверения аутентификации для портала](set-authentication-identity.md)  
[Параметры поставщика OAuth2 для порталов](configure-oauth2-settings.md)  
[Параметры поставщика WS-Federation для порталов](configure-ws-federation-settings.md)  
[Параметры поставщика SAML 2.0 для порталов](configure-saml2-settings.md)  

