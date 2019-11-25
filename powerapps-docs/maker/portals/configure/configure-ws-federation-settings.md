---
title: Настройка параметров поставщика WS-Federation для портала | MicrosoftDocs
description: Инструкции по добавлению и настройке параметров поставщика WS-Federation для портала.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 2a668f501a54472da0335344997c049794794783
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759615"
---
# <a name="configure-ws-federation-provider-settings-for-portals"></a>Настройка параметров поставщика WS-Federation для порталов

Один сервер службы федерации [!INCLUDE[pn-active-directory](../../../includes/pn-active-directory.md)] (или другую службу токенов безопасности, STS, удовлетворяющую требованиям [WS-Federation](https://msdn.microsoft.com/library/bb498017.aspx)) можно добавить в качестве поставщика удостоверений. Кроме того, одно пространство имен [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ACS](https://azure.microsoft.com/documentation/articles/active-directory-dotnet-how-to-use-access-control/) можно настроить в качестве набора отдельных поставщиков удостоверений. Настройки AD FS и ACS основаны на свойствах класса [WsFederationAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.aspx).

## <a name="create-an-ad-fs-relying-party-trust"></a>Создание отношения доверия с проверяющей стороной AD FS

С помощью средства управления AD FS перейдите к пункту **Отношения доверия** &gt; **Отношения доверия с проверяющей стороной**.

1.  Выберите **Добавить отношение доверия с проверяющей стороной**.
2.  Добро пожаловать: выберите **Начало**.
3.  Выберите источник данных: выберите **Ввести данные о проверяющей стороне вручную**, затем выберите **Далее**.
4.  Укажите отображаемое имя: введите **имя**, затем выберите **Далее**.
    Пример: https://portal.contoso.com/
5.  Выберите профиль: выберите **Профиль AD FS 2.0**, затем выберите **Далее**.
6.  Настройте сертификат: выберите **Далее**.
7.  Настройте URL-адрес: установите флажок **Включить поддержку пассивного протокола WS-Federation**.

URL-адрес пассивного протокола WS-Federation проверяющей стороны: введите https://portal.contoso.com/signin-federation

-   Примечание. Для AD FS требуется, чтобы портал использовал протокол **HTTPS**.

    > [!Note]
    > Полученная конечная точка имеет следующие параметры: тип конечной точки — **WS-Federation**
    > -   Привязка: **POST**
    > -   Указатель: н/д (0)
    > -   URL-адрес: **https://portal.contoso.com/signin-federation**

8.  Настройка удостоверений: укажите https://portal.contoso.com/, выберите **Добавить**, затем выберите **Далее**.
    Если требуется, можно добавить несколько удостоверений для каждого дополнительного портала проверяющей стороны. Пользователи смогут пройти аутентификацию через любые или все доступные удостоверения.
9.  Выберите правила авторизации выпуска: выберите **Разрешить всем пользователям доступ к этой проверяющей стороне**, затем выберите **Далее**.
10.  Готовность для добавления отношения доверия: выберите **Далее**.
11.  Выберите **Закрыть**.

Добавление требования **Идентификатор имени** в отношение доверия с проверяющей стороной:

**Преобразовать имя учетной записи [!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)]** в **Идентификатор имени** (Преобразовать входящее требование):
- Тип входящего требования: Имя учетной записи Windows
- Тип исходящего требования: Идентификатор имени
- Формат исходящего идентификатора имени: Не указано
- Передавать все значения требования

### <a name="create-ad-fs-site-settings"></a>Создание параметров сайта AD FS

Примените параметры сайта портала, учитывая указанные выше отношение доверия с проверяющей стороной AD FS.

> [!Note]
> Стандартная конфигурация AD FS (служба токенов безопасности) использует только следующие параметры (с примерами значений):
> - Authentication/WsFederation/ADFS/MetadataAddress — https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml
> - Authentication/WsFederation/ADFS/AuthenticationType — https://adfs.contoso.com/adfs/services/trust
>   - Используйте значение атрибута **entityID** в корневом элементе метаданных федерации ( откройте **URL-адрес MetadataAddress** в браузере, т. е. значение приведенной выше настройки сайта)
> - Authentication/WsFederation/ADFS/Wtrealm — https://portal.contoso.com/
> - Authentication/WsFederation/ADFS/Wreply — https://portal.contoso.com/signin-federation

**Метаданные WS-Federation** можно получить в **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]**, запустив следующий скрипт на сервере AD FS:

```
Import-Module adfs
Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml
```


|                      Имя настройки сайта                      |                                                                                                                                                                                                                                                 Описание                                                                                                                                                                                                                                                 |
|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      Authentication/Registration/ExternalLoginEnabled       |                                                                                                                                                                                                                Включает или отключает вход и регистрацию внешней учетной записи. Значение по умолчанию: true                                                                                                                                                                                                                 |
|      Authentication/WsFederation/ADFS/MetadataAddress       | Обязательное. URL-адрес метаданных [WS-Federation](https://msdn.microsoft.com/library/bb498017.aspx) сервера AD FS (STS). Обычно заканчивается на путь: /FederationMetadata/2007-06/FederationMetadata.xml . Пример: <https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml>. Дополнительные сведения: [WsFederationAuthenticationOptions.MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx). |
|     Authentication/WsFederation/ADFS/AuthenticationType     |            Обязательное. Тип ПО промежуточного слоя для аутентификации OWIN. Укажите значение атрибута [entityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata) в корне XML метаданных федерации. Пример: https://adfs.contoso.com/adfs/services/trust. Дополнительные сведения: [AuthenticationOptions.AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx).             |
|          Authentication/WsFederation/ADFS/Wtrealm           |                                                                                                              Обязательное. Идентификатор проверяющей стороны AD FS. Пример: `https://portal.contoso.com/`. Дополнительные сведения: [WsFederationAuthenticationOptions.Wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx).                                                                                                               |
|           Authentication/WsFederation/ADFS/Wreply           |                                                                                                     Обязательное. Конечная точка пассивного AD FS WS-Federation. Пример: https://portal.contoso.com/signin-federation. Дополнительные сведения: [WsFederationAuthenticationOptions.Wreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx).                                                                                                     |
|          Authentication/WsFederation/ADFS/Caption           |                                                                                                           Рекомендуемый. Текст, который пользователь может отображать в пользовательском интерфейсе входа. По умолчанию: ADFS. Дополнительные сведения: [WsFederationAuthenticationOptions.Caption](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx).                                                                                                            |
|        Authentication/WsFederation/ADFS/CallbackPath        |                                                                                                             Необязательный ограниченный путь, по которому будут обрабатываться обратные вызовы аутентификации. Дополнительные сведения: [WsFederationAuthenticationOptions.CallbackPath](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx).                                                                                                              |
|       Authentication/WsFederation/ADFS/SignOutWreply        |                                                                                                                               Значение "wreply", используемое при выходе. Дополнительные сведения: [WsFederationAuthenticationOptions.SignOutWreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signoutwreply.aspx).                                                                                                                               |
|     Authentication/WsFederation/ADFS/BackchannelTimeout     |                                                                                                         Значение времени ожидания для сообщений обратного канала. Пример: 00:05:00 (5 мин). Дополнительные сведения: [WsFederationAuthenticationOptions.BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx).                                                                                                         |
| Authentication/WsFederation/ADFS/RefreshOnIssuerKeyNotFound |                                                                                  Определяет, требуется ли пытаться обновить метаданные после SecurityTokenSignatureKeyNotFoundException. Дополнительные сведения: [WsFederationAuthenticationOptions.RefreshOnIssuerKeyNotFound](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.refreshonissuerkeynotfound.aspx).                                                                                  |
|      Authentication/WsFederation/ADFS/UseTokenLifetime      |                                                                                                   Показывает, что время жизни сеанса аутентификации (например, файлов cookie) должно соответствовать времени жизни токена аутентификации. [WsFederationAuthenticationOptions.UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx).                                                                                                   |
|     Authentication/WsFederation/ADFS/AuthenticationMode     |                                                                                                                                            Режим ПО промежуточного слоя для аутентификации OWIN. Дополнительные сведения: [AuthenticationOptions.AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx).                                                                                                                                             |
| Authentication/WsFederation/ADFS/SignInAsAuthenticationType |                                                                                            AuthenticationType, используемый при создании System.Security.Claims.ClaimsIdentity. Дополнительные сведения: [WsFederationAuthenticationOptions.SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx).                                                                                            |
|       Authentication/WsFederation/ADFS/ValidAudiences       |                                                                                                                                         Разделенный запятыми список URL-адресов аудитории. Дополнительные сведения: [TokenValidationParameters.AllowedAudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx).                                                                                                                                          |
|        Authentication/WsFederation/ADFS/ValidIssuers        |                                                                                                                                              Разделенный запятыми список URL-адресов издателя. Дополнительные сведения: [TokenValidationParameters.ValidIssuers](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.validissuers.aspx).                                                                                                                                               |
|         Authentication/WsFederation/ADFS/ClockSkew          |                                                                                                                                                                                                                               Расхождение часов, применяемое при проверки значений времени.                                                                                                                                                                                                                                |
|       Authentication/WsFederation/ADFS/NameClaimType        |                                                                                                                                                                                                                     Тип требования, используемый ClaimsIdentity для хранения требования имени.                                                                                                                                                                                                                      |
|       Authentication/WsFederation/ADFS/RoleClaimType        |                                                                                                                                                                                                                     Тип требования, используемый ClaimsIdentity для хранения требования роли.                                                                                                                                                                                                                      |
|   Authentication/WsFederation/ADFS/RequireExpirationTime    |                                                                                                                                                                                                                     Значение, указывающее, должны ли токены иметь значение "окончание срока действия".                                                                                                                                                                                                                      |
|    Authentication/WsFederation/ADFS/RequireSignedTokens     |                                                                                                                                                                       Значение, указывающее, может ли System.IdentityModel.Tokens.SecurityToken xmlns=<https://ddue.schemas.microsoft.com/authoring/2003/5> быть действительным, если не подписан.                                                                                                                                                                       |
|      Authentication/WsFederation/ADFS/SaveSigninToken       |                                                                                                                                                                                                               Логическое значение, определяющее, сохраняется ли исходный токен при создании сеанса.                                                                                                                                                                                                                |
|       Authentication/WsFederation/ADFS/ValidateActor        |                                                                                                                                                                                                   Значение, указывающее, должен ли System.IdentityModel.Tokens.JwtSecurityToken.Actor быть проверенным.                                                                                                                                                                                                    |
|      Authentication/WsFederation/ADFS/ValidateAudience      |                                                                                                                                                                                                               Логическое значение, которое определяет, будет ли проверяться аудитория во время проверки токена.                                                                                                                                                                                                               |
|       Authentication/WsFederation/ADFS/ValidateIssuer       |                                                                                                                                                                                                                Логическое значение, которое определяет, будет ли проверяться издатель во время проверки токена.                                                                                                                                                                                                                |
|      Authentication/WsFederation/ADFS/ValidateLifetime      |                                                                                                                                                                                                               Логическое значение, которое определяет, будет ли проверяться срок жизни во время проверки токена.                                                                                                                                                                                                               |
|  Authentication/WsFederation/ADFS/ValidateIssuerSigningKey  |                                                                                                                                                         Логическое значение, которое определяет, вызывается ли проверка System.IdentityModel.Tokens.SecurityKey, которым подписан securityToken xmlns=<https://ddue.schemas.microsoft.com/authoring/2003/5>.                                                                                                                                                          |
|            Authentication/WsFederation/ADFS/Whr             |                                                                                                                                       Определяет параметр "whr" в URL-адресе перенаправления поставщика удостоверений. Дополнительные сведения: [wsFederation](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation).                                                                                                                                       |

## <a name="ws-federation-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>Параметры WS-Federation для [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]

Предыдущий раздел, описывающий AD FS, также может применяться к [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)] ([[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD](https://msdn.microsoft.com/library/azure/mt168838.aspx)), так как [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD ведет себя как стандартная служба токенов безопасности, совместимая с [WS-Federation](https://docs.microsoft.com/azure/active-directory/develop/active-directory-developers-guide). Чтобы начать работу, выполните вход на [Портал управления [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal) и создайте или выберите существующий каталог. Когда каталог будет доступен, следуйте инструкциям, чтобы [добавить приложение](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) в каталог.

1.  В меню **Приложения** этого каталога выберите **Добавить**.
2.  Выберите **Добавить приложение, разрабатываемое моей организацией**.
3.  Укажите настраиваемое **имя** для приложения, затем выберите тип **Веб-приложение и/или веб-API**.
4.  Для параметров **URL-адрес входа** и **URI кода приложения** укажите URL-адрес портала для обоих полей https://portal.contoso.com/.
    - Это соответствует значению настройки сайта **Wtrealm**.
5.  На этом этапе создается новое приложение. Перейдите в раздел **Настроить** в этом меню.
6.  В разделе **единый вход** обновите первую запись **URL-адрес ответа** для включения пути в URL-адрес https://portal.contoso.com/signin-azure-ad.
    - Это соответствует значению настройки сайта **Wreply**.
7.  Выберите **Сохранить** в нижнем колонтитуле.
8.  В меню нижнего колонтитула выберите **Просмотр конечных точек** и проверьте поле **Документ метаданных федерации**.

    - Это соответствует значению настройки сайта **MetadataAddress**.
    - Вставьте этот URL-адрес в окно браузера для просмотра XML-кода метаданных федерации и проверьте атрибут **entityID** корневого элемента.
    - Это соответствует значению настройки сайта **AuthenticationType**.

> [!Note]
> Стандартная конфигурация [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD использует только следующие параметры (с примерами значений):
> - Authentication/WsFederation/ADFS/MetadataAddress — https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml
> - Authentication/WsFederation/ADFS/AuthenticationType — https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/
>   - Используйте значение атрибута **entityID** в корневом элементе метаданных федерации ( откройте **URL-адрес MetadataAddress** в браузере, т. е. значение приведенной выше настройки сайта)
> - Authentication/WsFederation/ADFS/Wtrealm — https://portal.contoso.com/
> - Authentication/WsFederation/ADFS/Wreply — https://portal.contoso.com/signin-azure-ad

### <a name="see-also"></a>См. также

[Настройка проверки подлинности портала](configure-portal-authentication.md)  
[Задание удостоверения аутентификации для портала](set-authentication-identity.md)  
[Параметры поставщика OAuth2 для порталов](configure-oauth2-settings.md)  
[Параметры поставщика Open ID Connect для порталов](configure-openid-settings.md)  
[Параметры поставщика SAML 2.0 для порталов](configure-saml2-settings.md)  
