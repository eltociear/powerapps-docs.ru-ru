---
title: Настройка параметров поставщика SAML 2.0 для портала | MicrosoftDocs
description: Инструкции по добавлению и настройке параметров поставщика SAML 2.0 для портала.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 4126ba564027291d8bbcb853f0769aa67f0de7d7
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2020
ms.locfileid: "2979132"
---
# <a name="configure-saml-20-provider-settings-for-portals"></a>Настройка параметров поставщика SAML 2.0 для порталов

Для обеспечения внешней проверки подлинности можно добавить одного или нескольких поставщиков удостоверений (IdP), совместимых с [SAML 2.0](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html). В этом документе описывается, как настраивать различных поставщиков удостоверений для интеграции с порталом, работающим как поставщик услуг.  

## <a name="ad-fs-idp"></a>AD FS (IdP)

Параметры для поставщика удостоверений, такие как [!include[](../../../includes/pn-active-dir-fed-svcs-ad-fs.md)].

### <a name="create-an-ad-fs-relying-party-trust"></a>Создание отношения доверия с проверяющей стороной AD FS

> [!Note]
> См. раздел [Настройка AD FS с помощью PowerShell](#configure-ad-fs-by-using-powershell) ниже, в котором приведены дополнительные сведения о том, как выполнять эти шаги в сценарии [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)].

С помощью средства управления [!include[](../../../includes/pn-adfs-short.md)] перейдите к пункту **Служба** > **Описания требования**.

1.  Выберите **Добавить описание требования**.
2.  Укажите требование:

    -  Отображаемое имя: **Постоянный идентификатор**

    -  Идентификатор требования: **urn:oasis:names:tc:SAML:2.0:nameid-format:persistent**

    -  Флажок **Включить** для: Опубликовать это описание требования в метаданных федерации в качестве типа требования, который может принимать эта служба федерации

    -  Флажок **Включить** для: Опубликовать это описание требования в метаданных федерации в качестве типа требования, который может отправлять эта служба федерации

3.  Нажмите **ОК**.

С помощью средства управления [!include[](../../../includes/pn-adfs-short.md)] выберите **Отношения доверия** >**Отношения доверия с проверяющей стороной**.

1. Выберите **Добавить отношение доверия с проверяющей стороной**.
2. Добро пожаловать: выберите **Начало**.
3. Выберите источник данных: выберите **Ввести данные о проверяющей стороне вручную**, затем выберите **Далее**.
4. Укажите отображаемое имя: введите имя, затем выберите **Далее**.
   Пример: https://portal.contoso.com/
5. Выберите профиль: выберите **Профиль AD FS 2.0**, затем выберите **Далее**.
6. Настройте сертификат: выберите **Далее**.
7. Настройте URL-адрес: установите флажок **Включить поддержку протокола SAML 2.0 WebSSO**.
   URL-адрес службы SAML 2.0 SSO проверяющей стороны: введите https://portal.contoso.com/signin-saml2
   - Примечание. Для [!include[](../../../includes/pn-adfs-short.md)] требуется, чтобы портал использовал протокол HTTPS.

   > [!Note] 
   > Полученная конечная точка имеет следующие параметры: 
   > - Тип конечной точки: **Конечные точки потребления утверждения SAML**             
   > - Привязка: **POST**                                            
   > - Указатель: н/д (0)                                              
   > - URL-адрес: **https://portal.contoso.com/signin-saml2**

8. Настройка удостоверений: укажите https://portal.contoso.com/, выберите **Добавить**, затем выберите **Далее**.
   Если требуется, можно добавить больше удостоверений для каждого дополнительного портала проверяющей стороны. Пользователи смогут пройти аутентификацию через любые или все доступные удостоверения.
9. Выберите правила авторизации выпуска: выберите **Разрешить всем пользователям доступ к этой проверяющей стороне**, затем выберите **Далее**.
10. Готовность для добавления отношения доверия: выберите **Далее**.
11. Выберите **Закрыть**.

Добавление требования **Идентификатор имени** в отношение доверия с проверяющей стороной:

**Преобразовать имя учетной записи [!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)]** в **Идентификатор имени** (Преобразовать входящее требование):

- Тип входящего требования: **Имя учетной записи [!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)]**

- Тип исходящего требования: **Идентификатор имени**

- Исходящий формат идентификатора имени: **Постоянный идентификатор**

- Передавать все значения требования

### <a name="create-site-settings"></a>Создание параметров сайта

Примените параметры сайта портала, учитывая указанные выше отношение доверия с проверяющей стороной [!include[](../../../includes/pn-adfs-short.md)].

> [!Note]
> В стандартной конфигурации [!include[](../../../includes/pn-adfs-short.md)] (IdP) используются только следующие параметры (с примерами значений): Authentication/SAML2/ADFS/MetadataAddress — <https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml>  
> - Authentication/SAML2/ADFS/AuthenticationType — https://adfs.contoso.com/adfs/services/trust    
>   -   Используйте значение атрибута **entityID** в корневом элементе метаданных федерации (откройте **URL-адрес MetadataAddress** в браузере, т. е. значение приведенной выше настройки сайта) 
> - Authentication/SAML2/ADFS/ServiceProviderRealm — https://portal.contoso.com/  
> - Authentication/SAML2/ADFS/AssertionConsumerServiceUrl — https://portal.contoso.com/signin-saml2  
>   **Метаданные федерации** можно получить в **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]**, запустив следующий скрипт на сервере [!include[](../../../includes/pn-adfs-short.md)]: `Import-Module adfs`
>   `Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml`

Несколько служб IdP можно настроить, подставляя метку для тега поставщика [provider]. Каждая уникальная метка образует группу параметров, связанных с IdP. Примеры: ADFS, [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD, MyIdP


| Имя настройки сайта                                             | Описание                                                                                                                                                                                                                                                                                                                                                                                                                             |
|---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/ExternalLoginEnabled              | Включает или отключает вход и регистрацию внешней учетной записи. Значение по умолчанию: true                                                                                                                                                                                                                                                                                                                                                            |
| Authentication/SAML2/[provider]/MetadataAddress             | Обязательное. URL-адрес метаданных [WS-Federation](https://msdn.microsoft.com/library/bb498017.aspx) сервера [!include[](../../../includes/pn-adfs-short.md)] (STS). Обычно заканчивается на путь: /FederationMetadata/2007-06/FederationMetadata.xml . Пример: `https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml`. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx) |  
| Authentication/SAML2/[provider]/AuthenticationType          | Обязательное. Тип ПО промежуточного слоя для аутентификации OWIN. Укажите значение атрибута [entityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata) в корне XML метаданных федерации. Пример: `https://adfs.contoso.com/adfs/services/trust`. [!include[](../../../includes/proc-more-information.md)] [AuthenticationOptions.AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)                                                            |  
| Authentication/SAML2/[provider]/ServiceProviderRealm<br>или <br>Authentication/SAML2/[provider]/Wtrealm                      | Обязательное. Идентификатор проверяющей стороны [!include[](../../../includes/pn-adfs-short.md)]. Пример: `https://portal.contoso.com/`. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.Wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx)                       |  
| Authentication/SAML2/[provider]/AssertionConsumerServiceUrl<br>или<br>Authentication/SAML2/[provider]/Wreply                       | Обязательное. Конечная точка утверждения потребителя [!include[](../../../includes/pn-adfs-short.md)] SAML. Пример: https://portal.contoso.com/signin-saml2. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.Wreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx)                                                                                                                                                                                                  |  
| Authentication/SAML2/[provider]/Caption                     | Рекомендуемый. Текст, который пользователь может отображать в пользовательском интерфейсе входа. По умолчанию: [provider]. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.Caption](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx)                |  
| Authentication/SAML2/[provider]/CallbackPath                | Необязательный ограниченный путь, по которому будут обрабатываться обратные вызовы аутентификации. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.CallbackPath](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx)                                                                                                                                                                                                                      |  
| Authentication/SAML2/[provider]/BackchannelTimeout          | Значение времени ожидания для сообщений обратного канала. Пример: 00:05:00 (5 мин). [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx)                                                                                                                                                                                                                   |  
| Authentication/SAML2/[provider]/UseTokenLifetime            | Показывает, что время жизни сеанса аутентификации (например, файлов cookie) должно соответствовать времени жизни токена аутентификации. [WsFederationAuthenticationOptions.UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx).                                                                                                                                                                               |  
| Authentication/SAML2/[provider]/AuthenticationMode          | Режим ПО промежуточного слоя для аутентификации OWIN. [!include[](../../../includes/proc-more-information.md)] [AuthenticationOptions.AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)                                                                                                                                                                                                                                                                              |  
| Authentication/SAML2/[provider]/SignInAsAuthenticationType  | AuthenticationType, используемый при создании System.Security.Claims.ClaimsIdentity. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx)                                                                                                                                                                                                 |  
| Authentication/SAML2/[provider]/ValidAudiences              | Разделенный запятыми список URL-адресов аудитории. [!include[](../../../includes/proc-more-information.md)] [TokenValidationParameters.AllowedAudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx)                                                                                                                                                                                                                                                                          |  
| Authentication/SAML2/[provider]/ClockSkew                   | Расхождение часов, применяемое при проверки значений времени.                                                                                                                                                                                                                                                                                                                                                                                          |
| Authentication/SAML2/[provider]/RequireExpirationTime       | Значение, указывающее, должны ли токены иметь значение окончания срока действия.                                                                                                                                                                                                                                                                                                                                                                      |
| Authentication/SAML2/[provider]/ValidateAudience            | Логическое значение, которое определяет, будет ли проверяться аудитория во время проверки токена.                                                                                                                                                                                                                                                                                                                                                         |

### <a name="idp-initiated-sign-in"></a>Вход, инициированный IdP

[!include[](../../../includes/pn-adfs-short.md)] поддерживает профиль [единого входа, инициированного IdP](https://technet.microsoft.com/library/jj127245.aspx) из [спецификации SAML 2.0](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline). Чтобы портал (поставщик услуг) правильно реагировал на запрос SAML, инициированный IdP, параметр [RelayState](https://blogs.technet.com/b/askds/archive/2012/09/27/ad-fs-2-0-relaystate.aspx) должен быть правильно закодирован.  

Базовое строковое значение, подлежащее кодированию в параметр SAML RelayState, должно иметь формат: **ReturnUrl=/content/sub-content/**, где **/content/sub-content/** — путь к требуемой веб-странице, на которую надо перейти на портале (поставщик услуг). Путь может быть заменен любой действительной веб-страницей на портале. Строковое значение кодируется и помещается в строку-контейнер в формате: **RPID=&lt;RPID в кодировке URL&gt;&RelayState=&lt;RelayState в кодировке URL&gt;**. Вся эта строка еще раз кодируется и добавляется в другой контейнер в формате **<https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=&lt;URL>-кодированный RPID/RelayState&gt;**.

Например, если имеется путь к поставщику услуг: **/content/sub-content/** и идентификатор проверяющей стороны: **https://portal.contoso.com/**, URL-адрес формируется следующими шагами:

Закодируйте значение ReturnUrl=/content/sub-content/,

-   чтобы получить ReturnUrl%3D%2Fcontent%2Fsub-content%2F

<!-- -->

-   Закодируйте значение https://portal.contoso.com/

<!-- -->

-   чтобы получить https%3A%2F%2Fportal.contoso.com%2F

<!-- -->

-   Закодируйте значение RPID=https%3A%2F%2Fportal.contoso.com%2F&RelayState=ReturnUrl%3D%2Fcontent%2Fsub-content%2F,

<!-- -->

-   чтобы получить RPID%3Dhttps%253A%252F%252Fportal.contoso.com%252F%26RelayState%3DReturnUrl%253D%252Fcontent%252Fsub-content%252F

<!-- -->

-   Добавьте в начало путь единого входа, инициированный AD FS IdP, чтобы получить окончательный URL-адрес

<!-- -->

-   https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=RPID%3Dhttps%253A%252F%252Fportal.contoso.com%252F%26RelayState%3DReturnUrl%253D%252Fcontent%252Fsub-content%252F

Следующий сценарий [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] можно использовать для создания URL-адреса (сохраняется в файл с именем Get-IdPInitiatedUrl.ps1).

```
<#

.SYNOPSIS 

Constructs an IdP-initiated SSO URL to access a portal page on the service provider.

.PARAMETER path

The path to the portal page.

.PARAMETER rpid

The relying party identifier.

.PARAMETER adfsPath

The AD FS IdP initiated SSO page.

.EXAMPLE

PS C:\\> .\\Get-IdPInitiatedUrl.ps1 -path "/content/sub-content/" -rpid "https://portal.contoso.com/" -adfsPath "https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx"

#>

param

(

[parameter(mandatory=$true,position=0)]

$path,

[parameter(mandatory=$true,position=1)]

$rpid,

[parameter(position=2)]

$adfsPath = https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx

)

$state = ReturnUrl=$path

$encodedPath = [uri]::EscapeDataString($state)

$encodedRpid = [uri]::EscapeDataString($rpid)

$encodedPathRpid = [uri]::EscapeDataString("RPID=$encodedRpid&RelayState=$encodedPath")

$idpInitiatedUrl = {0}?RelayState={1} -f $adfsPath, $encodedPathRpid

Write-Output $idpInitiatedUrl
```

## <a name="saml-20-settings-for-pn-azure-active-directory"></a>Параметры SAML 2.0 для [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]

Предыдущий раздел, описывающий [!include[](../../../includes/pn-adfs-short.md)], также может применяться к [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD](https://msdn.microsoft.com/library/azure/mt168838.aspx), так как [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD ведет себя как стандартный [SAML 2.0](https://msdn.microsoft.com/library/azure/dn195591.aspx)&ndash;совместимый IdP. Чтобы начать работу, выполните вход на [Портал управления [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal) и создайте или выберите существующий каталог. Когда каталог будет доступен, следуйте инструкциям, чтобы [добавить приложение](https://msdn.microsoft.com/library/azure/dn132599.aspx) в каталог.  

1.  В меню **Приложения** этого каталога выберите **Добавить**.
2.  Выберите **Добавить приложение, разрабатываемое моей организацией**.
3.  Укажите настраиваемое имя для приложения, затем выберите тип **веб-приложения и/или веб-API**.
4.  Для параметров **URL-адрес входа** и **URI кода приложения** укажите URL-адрес портала для обоих полей https://portal.contoso.com/.
    Это соответствует значению настройки сайта **ServiceProviderRealm** (Wtrealm).
5. На этом этапе создается новое приложение. Перейдите в раздел **Настроить** в этом меню.

    В разделе **единый вход** обновите первую запись **URL-адрес ответа** для включения пути в URL-адрес https://portal.contoso.com/signin-azure-ad.

    Это соответствует значению настройки сайта **AssertionConsumerServiceUrl** (Wreply).

6. В меню нижнего колонтитула выберите **Просмотр конечных точек** и проверьте поле **Документ метаданных федерации**.

Это соответствует значению настройки сайта **MetadataAddress**.

-   Вставьте этот URL-адрес в окно браузера для просмотра XML-кода метаданных федерации и проверьте атрибут **entityID** корневого элемента.
-   Это соответствует значению настройки сайта **AuthenticationType**.

> [!Note]
> В стандартной конфигурации [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD используются только следующие параметры (с примерами значений): Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/MetadataAddress — <https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml> 
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AuthenticationType — <https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/>  
> - Используйте значение атрибута **entityID** в корневом элементе метаданных федерации (откройте **URL-адрес MetadataAddress** в браузере, т. е. значение приведенной выше настройки сайта) 
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/ServiceProviderRealm — <https://portal.contoso.com/>  
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AssertionConsumerServiceUrl - <https://portal.contoso.com/signin-azure-ad>                                                                                   |

## <a name="shibboleth-identity-provider-3"></a>Поставщик удостоверений Shibboleth 3

Используйте следующие рекомендации для правильной конфигурации [поставщика удостоверений Shibboleth](https://wiki.shibboleth.net/confluence/display/IDP30/Home) в качестве службы IdP. Следующее подразумевает, что IdP размещается в домене https://idp.contoso.com.  

URL-адрес метаданных федерации https://idp.contoso.com/idp/shibboleth

-   IdP должен быть настроен для создания или предоставления постоянного идентификатора. Следуйте инструкциям, чтобы включить [создание постоянного идентификатора](https://wiki.shibboleth.net/confluence/display/IDP30/NameIDGenerationConfiguration).  

-   Метаданные федерации IdP (&lt;IDPSSODescriptor&gt;) необходимо настроить для включения [привязки перенаправления единого входа (SSO)](https://shibboleth.net/about/advanced.html). [Пример](https://wiki.shibboleth.net/confluence/display/SHIB2/MetadataExample).  

```
<SingleSignOnService Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-Redirect"

Location=https://idp.contoso.com/idp/profile/SAML2/Redirect/SSO/>
```

Настройте поставщиков услуг (проверяющие стороны), настроив [metadata-providers.xml](https://wiki.shibboleth.net/confluence/display/IDP30/MetadataConfiguration).  

-   Каждые метаданные федерации поставщика услуг (&lt;SPSSODescriptor&gt;) должны включать привязку записи службы потребителя утверждения. Один из вариантов: использовать [FilesystemMetadataProvider](https://wiki.shibboleth.net/confluence/display/IDP30/FilesystemMetadataProvider) и задать ссылку на файл конфигурации, который содержит:  

```
<AssertionConsumerService index=1 isDefault=true

Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST"

Location=https://portal.contoso.com/signin-saml2/>
```

Атрибут "Расположение" соответствует настройке **AssertionConsumerServiceUrl** (Wreply).

-   Метаданные федерации поставщика услуг должны задавать атрибут **entityID** для EntityDescriptor, который соответствует настройке **AuthenticationType**.

**&lt;EntityDescriptor entityID=<https://portal.local.contoso.com/&gt>;...**

> [!Note] 
> Стандартная конфигурация Shibboleth использует только следующие параметры (с примерами значений):   
> Authentication/SAML2/Shibboleth/MetadataAddress — https://idp.contoso.com/idp/shibboleth   
> -   Authentication/SAML2/Shibboleth/AuthenticationType — https://idp.contoso.com/idp/shibboleth 
> -   Используйте значение атрибута **entityID** в корневом элементе метаданных федерации (откройте **URL-адрес MetadataAddress** в браузере, т. е. значение приведенной выше настройки сайта)  
> -   Authentication/SAML2/Shibboleth/ServiceProviderRealm — https://portal.contoso.com/ 
> -   Authentication/SAML2/Shibboleth/AssertionConsumerServiceUrl — https://portal.contoso.com/signin-saml2 

### <a name="idp-initiated-sign-in"></a>Вход, инициированный IdP

Shibboleth поддерживает профиль [единого входа, инициированного IdP](https://wiki.shibboleth.net/confluence/display/SHIB2/IdPUnsolicitedSSO) из [спецификации](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline) SAML 2.0. Чтобы портал (поставщик услуг) правильно реагировал на запрос SAML, инициированный IdP, параметр RelayState должен быть правильно закодирован.  

Базовое строковое значение, подлежащее кодированию в параметр SAML RelayState, должно иметь формат: **ReturnUrl=/content/sub-content/**, где **/content/sub-content/** — путь к требуемой веб-странице, на которую надо перейти на портале (поставщик услуг). Путь может быть заменен любой действительной веб-страницей на портале. Полный URL-адрес единого входа, инициированного IdP, должен иметь формат Идентификатор поставщика в кодировке <https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=&lt;URL>&gt;&target=&lt;Обратный путь в кодировке URL&gt;.

Например, если имеется путь к поставщику услуг **/content/sub-content/** и идентификатор проверяющей стороны **https://portal.contoso.com/**, конечный URL-адрес имеет вид https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=https%3A%2F%2Fportal.contoso.com%2F&target=ReturnUrl%3D%2Fcontent%2Fsub-content%2F

Следующий сценарий [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] можно использовать для создания URL-адреса (сохраните в файл с именем ShibbolethIdPInitiatedUrl.ps1).

```
<# 

.SYNOPSIS

Constructs an IdP initiated SSO URL to access a portal page on the service provider.

.PARAMETER path

The path to the portal page.

.PARAMETER providerId

The relying party identifier.

.PARAMETER shibbolethPath

The Shibboleth IdP-initiated SSO page.

.EXAMPLE

PS C:\\> .\\Get-ShibbolethIdPInitiatedUrl.ps1 -path "/content/sub-content/" -providerId "https://portal.contoso.com/" -shibbolethPath "https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO"

#>

param

(

[parameter(mandatory=$true,position=0)]

$path,

[parameter(mandatory=$true,position=1)]

$providerId,

[parameter(position=2)]

$shibbolethPath = https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO

)

$state = ReturnUrl=$path

$encodedPath = [uri]::EscapeDataString($state)

$encodedRpid = [uri]::EscapeDataString($providerId)

$idpInitiatedUrl = {0}?providerId={1}&target={2} -f $shibbolethPath, $encodedRpid, $encodedPath

Write-Output $idpInitiatedUrl
```

## <a name="configure-ad-fs-by-using-powershell"></a>Настройка AD FS с помощью PowerShell

Процесс добавления отношения доверия с проверяющей стороной в [!include[](../../../includes/pn-adfs-short.md)] можно также выполнить, запустив следующий скрипт [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] на сервере [!include[](../../../includes/pn-adfs-short.md)] (сохраните содержимое в файл с названием Add-AdxPortalRelyingPartyTrustForSaml.ps1). После запуска сценария переходите к настройке параметров сайта портала.

```
<# 

.SYNOPSIS

Adds a SAML 2.0 relying party trust entry for a website.

.PARAMETER domain

The domain name of the portal.

.EXAMPLE

PS C:\\> .\\Add-AdxPortalRelyingPartyTrustForSaml.ps1 -domain portal.contoso.com

#>

param

(

[parameter(Mandatory=$true,Position=0)]

$domain,

[parameter(Position=1)]

$callbackPath = /signin-saml2

)

$VerbosePreference = Continue

$ErrorActionPreference = Stop

Import-Module adfs

Function Add-CrmRelyingPartyTrust

{

param (

[parameter(Mandatory=$true,Position=0)]

$name

)

$identifier = https://{0}/ -f $name

$samlEndpoint = New-ADFSSamlEndpoint -Binding POST -Protocol SAMLAssertionConsumer -Uri (https://{0}{1} -f $name, $callbackPath)

$identityProviderValue = Get-ADFSProperties | % { $_.Identifier.AbsoluteUri }

$issuanceTransformRules = @'

@RuleTemplate = MapClaims

@RuleName = Transform [!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] Account Name to Name ID claim

c:[Type == "https://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname"]

=> issue(Type = "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier", Issuer = c.Issuer, OriginalIssuer = c.OriginalIssuer, Value = c.Value, ValueType = c.ValueType, Properties["https://schemas.xmlsoap.org/ws/2005/05/identity/claimproperties/format"] = "urn:oasis:names:tc:SAML:2.0:nameid-format:persistent");

@RuleTemplate = LdapClaims

@RuleName = Send LDAP Claims

c:[Type == "https://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname", Issuer == "AD AUTHORITY"]

=> issue(store = "[!INCLUDE[pn-active-directory](../../../includes/pn-active-directory.md)]", types = ("https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname", "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname", "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress"), query = ";givenName,sn,mail;{{0}}", param = c.Value);

'@ -f $identityProviderValue

$issuanceAuthorizationRules = @'

@RuleTemplate = AllowAllAuthzRule

=> issue(Type = https://schemas.microsoft.com/authorization/claims/permit, Value = true);

'@

Add-ADFSRelyingPartyTrust -Name $name -Identifier $identifier -SamlEndpoint $samlEndpoint -IssuanceTransformRules $issuanceTransformRules -IssuanceAuthorizationRules $issuanceAuthorizationRules

}

# add the 'Identity Provider' claim description if it is missing

if (-not (Get-ADFSClaimDescription | ? { $_.Name -eq Persistent Identifier })) {

Add-ADFSClaimDescription -name "Persistent Identifier" -ClaimType "urn:oasis:names:tc:SAML:2.0:nameid-format:persistent" -IsOffered:$true -IsAccepted:$true

}

# add the portal relying party trust

Add-CrmRelyingPartyTrust $domain
```

### <a name="see-also"></a>См. также

[Настройка проверки подлинности портала](configure-portal-authentication.md)  
[Задание удостоверения аутентификации для портала](set-authentication-identity.md)  
[Параметры поставщика OAuth2 для порталов](configure-oauth2-settings.md)  
[Параметры поставщика Open ID Connect для порталов](configure-openid-settings.md)  
[Параметры поставщика WS-Federation для порталов](configure-ws-federation-settings.md)  
