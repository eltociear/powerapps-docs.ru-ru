---
title: Настройка параметров поставщика OpenID Connect Connect для портала | MicrosoftDocs
description: Инструкции по добавлению и настройке параметров поставщика OpenID Connect Connect для портала.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 0dba1794f15a710e43feaec3ca6d4d2dbc9c5fc3
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72978492"
---
# <a name="configure-open-id-connect-provider-settings-for-portals"></a>Настройка параметров поставщика Connect Open ID для порталов

Внешние поставщики удостоверений [OpenID Connect Connect](http://openid.net/connect/) — это службы, соответствующие [спецификациям](http://openid.net/developers/specs/)Open ID Connect. Интеграция поставщика включает в себя поиск URL-адреса центра (или издателя), связанного с поставщиком. URL-адрес конфигурации можно определить по центру сертификации, предоставляющему метаданные, необходимые во время рабочего процесса проверки подлинности. Параметры поставщика основаны на свойствах класса [OpenIdConnectAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.aspx) .

Примеры URL-адресов полномочий:

- [Google](https://developers.google.com/identity/protocols/OpenIDConnect): <https://accounts.google.com/><https://accounts.google.com/.well-known/openid-configuration>
- [[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]](https://msdn.microsoft.com/library/azure/mt168838.aspx): [https://login.microsoftonline.com/&lt ;[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]&gt; приложений Active Directory/](https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration)

Каждый поставщик OpenID Connect Connect также включает регистрацию приложения (аналогично поставщику OAuth 2,0) и получение идентификатора клиента. URL-адрес центра и идентификатор созданного приложения являются параметрами, необходимыми для включения внешней проверки подлинности между порталом и поставщиком удостоверений.

> [!Note]
> Конечная точка Google OpenID Connect Connect сейчас не поддерживается, так как базовые библиотеки по-прежнему находятся на ранних стадиях выпуска с проблемами совместимости. Вместо этого можно использовать [Параметры поставщика OAuth2 для](configure-oauth2-settings.md) конечной точки портала.

## <a name="openid-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>Параметры OpenID Connect для [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]

Чтобы начать работу, войдите в [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] портал управления](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal) и создайте или выберите существующий каталог. Если каталог доступен, следуйте инструкциям по [добавлению приложения](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) в каталог.  

1. В меню **приложения** каталога выберите **Добавить**.
2. Выберите **Добавить приложение, разрабатываемое моей организацией**.
3. Укажите пользовательское **имя** для приложения и выберите тип **веб-приложение и (или) веб-API**.
4. Для **URL-адреса входа** и **URI идентификатора приложения**укажите URL-адрес портала для обоих полей https://portal.contoso.com/
5. На этом этапе создается новое приложение. Перейдите к разделу **Настройка** в меню.

    В разделе **единый вход** Обновите первую запись **URL-адреса ответа** , чтобы включить путь в url-адрес: http://portal.contoso.com/signin-azure-ad. Соответствует значению параметра сайта **RedirectUri**

6. В разделе **Свойства** выберите поле **идентификатор клиента** . Это соответствует значению параметра сайта **ClientID** .
7. В меню нижнего колонтитула выберите **просмотреть конечные точки** и обратите внимание на поле **документ метаданных федерации** .

Левая часть URL-адреса является значением **полномочий** и имеет один из следующих форматов:

- https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/
- https://login.microsoftonline.com/contoso.onmicrosoft.com/

Чтобы получить URL-адрес конфигурации службы, замените FederationMetadata/2007-06/FederationMetadata. XML Path на путь. хорошо известная/OpenID Connect-Configuration. Например, <https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration>

Это соответствует значению параметра сайта **MetadataAddress** .

### <a name="related-site-settings"></a>Параметры связанных сайтов

Примените параметры сайта портала, ссылающиеся на указанное выше приложение.

> [!Note]
> Стандартная конфигурация [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD использует только следующие параметры (с примерами значений):                                 
> - Проверка подлинности/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/Authority-<https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/>                                                    
> - Authentication/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/ClientId-fedcba98-7654-3210-fedc-ba9876543210                                      
>   Идентификатор клиента и URL-адрес центра не содержат одинаковое значение и должны извлекаться отдельно.           
> - Authentication/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/RedirectUri- https://portal.contoso.com/signin-azure-ad
 
Несколько поставщиков удостоверений можно настроить, подставив метку для тега \[поставщика\]. Каждая уникальная метка образует группу параметров, связанных с поставщиком удостоверений. Примеры: [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD, Мидп


|                          Имя параметра сайта                           |                                                                                                                                                                                                         Description                                                                                                                                                                                                          |
|----------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           Проверка подлинности/регистрация/Екстерналлогиненаблед           |                                                                                                                                                                         Включает или отключает вход и регистрацию внешней учетной записи. Значение по умолчанию: true                                                                                                                                                                         |
|         Поставщик проверки подлинности, OpenIdConnect и\[\]/аусорити          |                                               Обязательно. Полномочия, используемые при выполнении вызовов OpenIdConnect. Пример: `https://login.microsoftonline.com/contoso.onmicrosoft.com/`. Дополнительные сведения:[OpenIdConnectAuthenticationOptions. Authority](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.authority.aspx).                                                |
|      Поставщик проверки подлинности, OpenIdConnect и\[\]/Метадатааддресс       | Конечная точка обнаружения для получения метаданных. Обычно заканчивается путем:/. Велл-кновн/опенид-конфигуратион. Пример: `https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration`. Дополнительные сведения:[OpenIdConnectAuthenticationOptions. MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.metadataaddress.aspx). |
|     Поставщик проверки подлинности, OpenIdConnect и\[\]/Аусентикатионтипе     |                                   Тип по промежуточного слоя проверки подлинности OWIN. Укажите значение издателя в метаданных конфигурации службы. Пример: `https://sts.windows.net/contoso.onmicrosoft.com/`. Дополнительные сведения: [AuthenticationOptions. AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx).                                   |
|          Поставщик проверки подлинности, OpenIdConnect и\[\]/Клиентид          |                                                  Обязательно. Значение идентификатора клиента из приложения поставщика. Его также можно называть "ИДЕНТИФИКАТОРом приложения" или "ключом потребителя". Дополнительные сведения: [OpenIdConnectAuthenticationOptions. ClientID](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.clientid.aspx).                                                   |
|        Поставщик проверки подлинности, OpenIdConnect и\[\]/Клиентсекрет        |                                              Значение секрета клиента из приложения поставщика. Он также может называться "секретом приложения" или "секретом клиента". Дополнительные сведения: [OpenIdConnectAuthenticationOptions. ClientSecret](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.clientsecret.aspx).                                              |
|        Поставщик проверки подлинности, OpenIdConnect и\[\]/Редиректури         |                                                        Такую. Пассивная конечная точка WS-Federation AD FS. Пример: https://portal.contoso.com/signin-saml2. Дополнительные сведения: [OpenIdConnectAuthenticationOptions. RedirectUri](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.redirecturi.aspx).                                                        |
|          Поставщик проверки подлинности, OpenIdConnect и\[\]/Каптион           |                                                              Такую. Текст, который пользователь может отображать в пользовательском интерфейсе входа. По умолчанию:\]поставщика \[. Дополнительные сведения: [OpenIdConnectAuthenticationOptions. Caption](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.caption.aspx).                                                               |
|          Аутентификация, OpenIdConnect и поставщик\[\]/Resource          |                                                                                                       Ресурс. Дополнительные сведения: [OpenIdConnectAuthenticationOptions. Resource](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.resource.aspx).                                                                                                        |
|        Поставщик проверки подлинности, OpenIdConnect и\[\]/Респонсетипе        |                                                                                                Тип\_Response. Дополнительные сведения: [OpenIdConnectAuthenticationOptions. ResponseType](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.responsetype.aspx).                                                                                                 |
|           Поставщик проверки подлинности, OpenIdConnect и\[\]/Scope            |                                                                                Разделенный пробелом список разрешений для запроса. Значение по умолчанию: OpenID Connect. Дополнительные сведения: [OpenIdConnectAuthenticationOptions. Scope ](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.scope.aspx).                                                                                 |
|        Поставщик проверки подлинности, OpenIdConnect и\[\]/Каллбаккпас        |                      Необязательный путь с ограничением для обработки обратного вызова проверки подлинности. Если параметр не указан и RedirectUri доступен, это значение будет создано из RedirectUri. Дополнительные сведения: [OpenIdConnectAuthenticationOptions. каллбаккпас](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.callbackpath.aspx).                      |
|     Поставщик проверки подлинности, OpenIdConnect и\[\]/Баккчаннелтимеаут     |                                                                Значение времени ожидания для обмена данными с обратным каналом. Пример: 00:05:00 (5 минут). Дополнительные сведения: [OpenIdConnectAuthenticationOptions. баккчаннелтимеаут](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.backchanneltimeout.aspx).                                                                |
| Поставщик проверки подлинности, OpenIdConnect и\[\]/Рефрешониссуеркэйнотфаунд |                                      Определяет, следует ли пытаться обновить метаданные после Секурититокенсигнатурекэйнотфаундексцептион. Дополнительные сведения: [OpenIdConnectAuthenticationOptions. рефрешониссуеркэйнотфаунд](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.refreshonissuerkeynotfound.aspx).                                       |
|      Поставщик проверки подлинности, OpenIdConnect и\[\]/Усетокенлифетиме      |                                               Указывает, что время существования сеанса проверки подлинности (например, файлы cookie) должно соответствовать маркеру проверки подлинности. Дополнительные сведения: [OpenIdConnectAuthenticationOptions. усетокенлифетиме](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.usetokenlifetime.aspx).                                               |
|     Поставщик проверки подлинности, OpenIdConnect и\[\]/Аусентикатионмоде     |                                                                                                     Режим по промежуточного слоя для проверки подлинности OWIN. Дополнительные сведения: [AuthenticationOptions. AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx).                                                                                                     |
| Поставщик проверки подлинности, OpenIdConnect и\[\]/Сигнинасаусентикатионтипе |                                                   AuthenticationType, используемый при создании System. Security. Claims. ClaimsIdentity. Дополнительные сведения: [OpenIdConnectAuthenticationOptions. сигнинасаусентикатионтипе](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.signinasauthenticationtype.aspx).                                                   |
|   Поставщик проверки подлинности, OpenIdConnect и\[\]/Постлогаутредиректури    |                                                                                 \_Logout\_перенаправление\_URI. Дополнительные сведения: [OpenIdConnectAuthenticationOptions. постлогаутредиректури](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.postlogoutredirecturi.aspx).                                                                                 |
|       Поставщик проверки подлинности, OpenIdConnect и\[\]/Валидаудиенцес       |                                                                                                  Список URL-адресов аудитории с разделителями-запятыми. Дополнительные сведения: [TokenValidationParameters. алловедаудиенцес](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx).                                                                                                  |
|        Поставщик проверки подлинности, OpenIdConnect и\[\]/Валидиссуерс        |                                                                                                       Разделенный запятыми список URL-адресов издателя. Дополнительные сведения: [TokenValidationParameters. валидиссуерс](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.validissuers.aspx).                                                                                                       |
|         Поставщик проверки подлинности, OpenIdConnect и\[\]/Клоккскев          |                                                                                                                                                                                        Отклонение часов, применяемое при проверке времени.                                                                                                                                                                                        |
|       Поставщик проверки подлинности, OpenIdConnect и\[\]/Намеклаимтипе        |                                                                                                                                                                              Тип утверждения, используемый ClaimsIdentity для хранения утверждения имени.                                                                                                                                                                              |
|       Поставщик проверки подлинности, OpenIdConnect и\[\]/Ролеклаимтипе        |                                                                                                                                                                              Тип утверждения, используемый ClaimsIdentity для хранения утверждения роли.                                                                                                                                                                              |
|   Поставщик проверки подлинности, OpenIdConnect и\[\]/Рекуирикспиратионтиме    |                                                                                                                                                                              Значение типа, указывающее, должны ли маркеры иметь значение срока действия.                                                                                                                                                                              |
|    Поставщик проверки подлинности, OpenIdConnect и\[\]/Рекуиресигнедтокенс     |                                                                                                                               Значение типа, указывающее, может ли элемент System. IdentityModel. tokens. SecurityToken xmlns =<http://ddue.schemas.microsoft.com/authoring/2003/5> быть допустимым, если он не подписан.                                                                                                                                |
|      Поставщик проверки подлинности, OpenIdConnect и\[\]/Савесигнинтокен       |                                                                                                                                                                        Логическое значение, определяющее, сохраняется ли исходный маркер при создании сеанса.                                                                                                                                                                        |
|       Поставщик проверки подлинности, OpenIdConnect и\[\]/Валидатеактор        |                                                                                                                                                            Значение типа, указывающее, следует ли проверять System. IdentityModel. tokens. Жвтсекурититокен. Actor.                                                                                                                                                            |
|      Поставщик проверки подлинности, OpenIdConnect и\[\]/Валидатеаудиенце      |                                                                                                                                                                       Логическое значение, определяющее, будет ли проверяться аудитория во время проверки маркера.                                                                                                                                                                        |
|       Поставщик проверки подлинности, OpenIdConnect и\[\]/Валидатеиссуер       |                                                                                                                                                                        Логическое значение, определяющее, будет ли проверяться издатель во время проверки маркера.                                                                                                                                                                         |
|      Поставщик проверки подлинности, OpenIdConnect и\[\]/Валидателифетиме      |                                                                                                                                                                       Логическое значение, определяющее, будет ли проверяться время существования во время проверки маркера.                                                                                                                                                                        |
|  Поставщик проверки подлинности, OpenIdConnect и\[\]/Валидатеиссуерсигнингкэй  |                                                                                                                  Логическое значение, определяющее, будет ли вызвана проверка System. IdentityModel. tokens. SecurityKey, который подписал маркер securityToken xmlns =<http://ddue.schemas.microsoft.com/authoring/2003/5>.                                                                                                                  |
|                                                                      |                                                                                                                                                                                                                                                                                                                                                                                                                              |

## <a name="enable-authentication-using-a-multi-tenant-azure-active-directory-application"></a>Включение проверки подлинности с помощью приложения Azure Active Directory с несколькими клиентами

Вы можете настроить на портале принятие [!include[](../../../includes/pn-azure-active-directory.md)] пользователей от любого клиента в [!include[](../../../includes/pn-azure-shortest.md)], а не только для конкретного клиента с помощью приложения с несколькими клиентами, зарегистрированного в [!include[](../../../includes/pn-azure-active-directory.md)]. Чтобы включить мультитенантность, в приложении [!include[](../../../includes/pn-azure-active-directory.md)] задайте для коммутатора с **несколькими клиентами** значение **Да** .

![Включение мультитенантность в приложении Azure Active Directory](../media/enable-multi-tenancy.png "Включение мультитенантность в приложении Azure Active Directory")

### <a name="related-site-settings"></a>Параметры связанных сайтов

Несколько поставщиков удостоверений можно настроить, подставив метку для тега [Provider]. Каждая уникальная метка образует группу параметров, связанных с поставщиком удостоверений. Вы можете создать или настроить следующие параметры сайта на порталах для поддержки проверки подлинности в [!include[](../../../includes/pn-azure-active-directory.md)] с помощью приложения с несколькими клиентами:

|Имя параметра сайта    |Description   |
|---|---|
|Authentication/OpenIdConnect/[поставщик]/аусорити   |Полномочия, используемые при выполнении вызовов OpenIdConnect. Например: `https://login.microsoftonline.com/common`   |
|Authentication/OpenIdConnect/[поставщик]/Клиентид   |Значение идентификатора клиента из приложения поставщика. Его также можно называть ИДЕНТИФИКАТОРом приложения или ключом потребителя.   |
|Authentication/OpenIdConnect/[поставщик]/Екстерналлогаутенаблед   |Включает или отключает выход и регистрацию внешней учетной записи. Задайте для этого параметра значение true.   |
|Authentication/OpenIdConnect/[поставщик]/Иссуерфилтер   |Фильтр на основе шаблона, который соответствует всем издателям во всех клиентах. В большинстве случаев используйте значение: `https://sts.windows.net/*/`   |
|Authentication/OpenIdConnect/[поставщик]/Редиректури  |Расположение URL-адреса ответа, по которому поставщик отправляет ответ проверки подлинности. Например: `https://portal.contoso.com/signin-oidc` |
|Authentication/OpenIdConnect/[поставщик]/Валидатеиссуер   |Логическое значение, определяющее, будет ли проверяться издатель во время проверки маркера. Задайте для этого параметра значение false.   |
|||

### <a name="see-also"></a>См. также
[Настройка проверки подлинности на портале](configure-portal-authentication.md)  
[Настройка удостоверения для проверки подлинности на портале](set-authentication-identity.md)  
[Параметры поставщика OAuth2 для порталов](configure-oauth2-settings.md)  
[Параметры поставщика WS-Federation для порталов](configure-ws-federation-settings.md)  
[Параметры поставщика SAML 2,0 для порталов](configure-saml2-settings.md)  

