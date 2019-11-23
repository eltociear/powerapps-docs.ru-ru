---
title: Настройка параметров поставщика SAML 2,0 для портала | MicrosoftDocs
description: Инструкции по добавлению и настройке параметров поставщика SAML 2,0 для портала.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: af5b0ae8eddb68127c7271fccb4696a23fedfc60
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542745"
---
# <a name="configure-saml-20-provider-settings-for-portals"></a>Настройка параметров поставщика SAML 2,0 для порталов

Чтобы обеспечить внешнюю проверку подлинности, можно добавить один или несколько поставщиков удостоверений, соответствующих [SAML 2,0](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html)(IDP). В этом документе описывается, как настроить различные поставщики удостоверений для интеграции с порталом, который выступает в качестве поставщика услуг.  

## <a name="ad-fs-idp"></a>AD FS (IdP)

Параметры для поставщика удостоверений, например [!include[](../../../includes/pn-active-dir-fed-svcs-ad-fs.md)].

### <a name="create-an-ad-fs-relying-party-trust"></a>Создание отношения доверия с проверяющей стороной AD FS

> [!Note]
> Сведения о том, как выполнить эти действия в скрипте [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)], см. в разделе [настройка AD FS с помощью PowerShell](#configure-ad-fs-by-using-powershell).

С помощью средства управления [!include[](../../../includes/pn-adfs-short.md)] перейдите к разделу **службы** > **описания утверждений**.

1.  Выберите **Добавить описание утверждения**.
2.  Укажите утверждение:

    -  Отображаемое имя: **постоянный идентификатор**

    -  Идентификатор утверждения: **urn: Oasis: Names: TC: SAML: 2.0: NameID-Format: persistent**

    -  **Включить** флажок для: опубликовать это описание утверждения в метаданных федерации как тип утверждения, который может принимать эта служба Федерации

    -  **Включить** флажок для: опубликовать это описание утверждения в метаданных федерации как тип утверждения, который может быть отправлен этой службой федерации

3.  Выберите **ОК**.

С помощью средства управления [!include[](../../../includes/pn-adfs-short.md)] выберите **отношения доверия** >**отношения доверия с проверяющей стороной**.

1. Выберите **Добавить отношение доверия с проверяющей стороной**.
2. Добро пожаловать: нажмите кнопку **запустить**.
3. Выбор источника данных: выберите **вручную ввести данные о проверяющей стороне**, а затем нажмите кнопку **Далее**.
4. Укажите отображаемое имя: введите имя, а затем нажмите кнопку **Далее**.
   Пример: https://portal.contoso.com/
5. Выберите профиль: выберите **AD FS профиль 2,0**, а затем нажмите кнопку **Далее**.
6. Настройка сертификата: нажмите кнопку **Далее**.
7. Настройка URL-адреса: установите флажок **включить поддержку для протокола SAML 2,0 WebSSO** .
   URL-адрес службы SAML 2,0 SSO проверяющей стороны: введите https://portal.contoso.com/signin-saml2
   - Примечание. для [!include[](../../../includes/pn-adfs-short.md)] требуется, чтобы портал выполнялся по протоколу HTTPS.

   > [!Note] 
   > Результирующая конечная точка имеет следующие параметры. 
   > - Тип конечной точки: **утверждение SAML использование конечных точек**             
   > - Привязка: **POST**                                            
   > - Индекс: н/д (0)                                              
   > - URL-адрес: **https://portal.contoso.com/signin-saml2**

8. Настройка удостоверений. Укажите https://portal.contoso.com/, выберите **Добавить**, а затем нажмите кнопку **Далее**.
   Если применимо, можно добавить дополнительные удостоверения для каждого дополнительного портала проверяющей стороны. Пользователи смогут проходить проверку подлинности в любом или всех доступных удостоверениях.
9. Выберите правила авторизации выдачи: выберите **разрешите всем пользователям доступ к этой проверяющей стороне**, а затем нажмите кнопку **Далее**.
10. Готово к добавлению отношения доверия: нажмите кнопку **Далее**.
11. Нажмите **Закрыть**.

Добавьте утверждение **идентификатора имени** в отношение доверия с проверяющей стороной:

**Преобразование[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] имя учетной записи** в утверждение **ИД имени** (преобразование входящего утверждения):

- Тип входящего утверждения: **[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] имя учетной записи**

- Тип исходящего утверждения: **ИД имени**

- Формат идентификатора исходящего имени: **постоянный идентификатор**

- Пройти по всем значениям утверждений

### <a name="create-site-settings"></a>Создание параметров сайта

Примените параметры сайта портала, ссылающиеся на указанные выше [!include[](../../../includes/pn-adfs-short.md)] отношения доверия с проверяющей стороной.

> [!Note]
> Стандартная конфигурация [!include[](../../../includes/pn-adfs-short.md)] (IdP) использует только следующие параметры (с примерами значений): Authentication/SAML2/ADFS/MetadataAddress-<https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml>  
> - Authentication/SAML2/ADFS/AuthenticationType- https://adfs.contoso.com/adfs/services/trust    
>   -   Используйте значение атрибута **entityID** в корневом элементе метаданных федерации (откройте **URL-адрес MetadataAddress** в браузере, который является значением указанного выше параметра сайта). 
> - Authentication/SAML2/ADFS/Сервицепровидерреалм- https://portal.contoso.com/  
> - Authentication/SAML2/ADFS/AssertionConsumerServiceUrl- https://portal.contoso.com/signin-saml2  
>   **Метаданные федерации** можно получить в **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]** , выполнив следующий скрипт на сервере [!include[](../../../includes/pn-adfs-short.md)]: `Import-Module adfs`
>   `Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml`

Можно настроить несколько служб IdP, подставив метку для тега [Provider]. Каждая уникальная метка образует группу параметров, связанных с IdP. Примеры: ADFS, [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD, Мидп


| Имя параметра сайта                                             | Описание                                                                                                                                                                                                                                                                                                                                                                                                                             |
|---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Проверка подлинности/регистрация/Екстерналлогиненаблед              | Включает или отключает вход и регистрацию внешней учетной записи. Значение по умолчанию: true                                                                                                                                                                                                                                                                                                                                                            |
| Authentication/SAML2/[поставщик]/Метадатааддресс             | Обязательно. URL-адрес метаданных [WS-Federation](https://msdn.microsoft.com/library/bb498017.aspx) сервера [!include[](../../../includes/pn-adfs-short.md)] (STS). Обычно она заканчивается путем:/FederationMetadata/2007-06/FederationMetadata. XML. Пример: `https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml`. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions. MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx) |  
| Authentication/SAML2/[поставщик]/Аусентикатионтипе          | Обязательно. Тип по промежуточного слоя проверки подлинности OWIN. Укажите значение атрибута [entityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata) в корне XML метаданных федерации. Пример: `https://adfs.contoso.com/adfs/services/trust`. [!include[](../../../includes/proc-more-information.md)] [AuthenticationOptions. AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)                                                            |  
| Authentication/SAML2/[поставщик]/Сервицепровидерреалм<br>или <br>Authentication/SAML2/[поставщик]/Втреалм                      | Обязательно. Идентификатор проверяющей стороны [!include[](../../../includes/pn-adfs-short.md)]. Пример: `https://portal.contoso.com/`. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions. wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx)                       |  
| Authentication/SAML2/[поставщик]/Ассертионконсумерсервицеурл<br>или<br>Authentication/SAML2/[поставщик]/Врепли                       | Обязательно. Конечная точка утверждения потребителя SAML [!include[](../../../includes/pn-adfs-short.md)]. Пример: https://portal.contoso.com/signin-saml2. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions. wreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx)                                                                                                                                                                                                  |  
| Authentication/SAML2/[поставщик]/Каптион                     | Такую. Текст, который пользователь может отображать в пользовательском интерфейсе входа. По умолчанию: [Provider]. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions. Caption](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx)                |  
| Authentication/SAML2/[поставщик]/Каллбаккпас                | Необязательный путь с ограничением для обработки обратного вызова проверки подлинности. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions. каллбаккпас](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx)                                                                                                                                                                                                                      |  
| Authentication/SAML2/[поставщик]/Баккчаннелтимеаут          | Значение времени ожидания для обмена данными между внутренним каналом. Пример: 00:05:00 (5 минут). [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions. баккчаннелтимеаут](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx)                                                                                                                                                                                                                   |  
| Authentication/SAML2/[поставщик]/Усетокенлифетиме            | Указывает, что время существования сеанса проверки подлинности (например, файлы cookie) должно соответствовать маркеру проверки подлинности. [WsFederationAuthenticationOptions. усетокенлифетиме](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx).                                                                                                                                                                               |  
| Authentication/SAML2/[поставщик]/Аусентикатионмоде          | Режим по промежуточного слоя для проверки подлинности OWIN. [!include[](../../../includes/proc-more-information.md)] [AuthenticationOptions. AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)                                                                                                                                                                                                                                                                              |  
| Authentication/SAML2/[поставщик]/Сигнинасаусентикатионтипе  | AuthenticationType, используемый при создании System. Security. Claims. ClaimsIdentity. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions. сигнинасаусентикатионтипе](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx)                                                                                                                                                                                                 |  
| Authentication/SAML2/[поставщик]/Валидаудиенцес              | Список URL-адресов аудитории с разделителями-запятыми. [!include[](../../../includes/proc-more-information.md)] [TokenValidationParameters. алловедаудиенцес](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx)                                                                                                                                                                                                                                                                          |  
| Authentication/SAML2/[поставщик]/Клоккскев                   | Отклонение часов, применяемое при проверке времени.                                                                                                                                                                                                                                                                                                                                                                                          |
| Authentication/SAML2/[поставщик]/Рекуирикспиратионтиме       | Значение типа, указывающее, должны ли маркеры иметь значение срока действия.                                                                                                                                                                                                                                                                                                                                                                      |
| Authentication/SAML2/[поставщик]/Валидатеаудиенце            | Логическое значение, определяющее, будет ли проверяться аудитория во время проверки маркера.                                                                                                                                                                                                                                                                                                                                                         |

### <a name="idp-initiated-sign-in"></a>Вход, инициированный IdP

[!include[](../../../includes/pn-adfs-short.md)] поддерживает профиль [единого входа, инициированный IDP (SSO)](https://technet.microsoft.com/library/jj127245.aspx) [спецификации](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline)SAML 2,0. Чтобы портал (поставщик услуг) правильно отвечал на запрос SAML, инициированный IdP, параметр [RelayState](https://blogs.technet.com/b/askds/archive/2012/09/27/ad-fs-2-0-relaystate.aspx) должен быть правильно закодирован.  

Базовое строковое значение, которое должно быть закодировано в параметре SAML RelayState, должно иметь формат **ReturnUrl =/контент/суб-контент/** , где **/контент/суб-контент/** — это путь к веб-странице, на которую вы хотите зайти на портале (поставщик услуг). Путь может быть заменен любой допустимой веб-страницей на портале. Строковое значение кодируется и помещается в строку контейнера в формате **рпид =&lt;URL-адрес, закодированный рпид&gt;& RelayState =&lt;URL-адрес RelayState&gt;** . Вся строка снова кодируется и добавляется в другой контейнер формата **<https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=&lt;URL> ENCODED рпид/RelayState&gt;** .

Например, если задан путь к поставщику службы **/контент/суб-контент/** и идентификатор проверяющей стороны **https://portal.contoso.com/** , создайте URL-адрес, выполнив следующие действия:

Кодирование значения ReturnUrl =/контент/суб-контент/

-   чтобы получить ReturnUrl% 3D% 2Fcontent% 2Fsub-Content% 2F

<!-- -->

-   Кодирование значения https://portal.contoso.com/

<!-- -->

-   чтобы получить HTTPS %3, %2 f %2 F Portal. contoso. com% 2F

<!-- -->

-   Кодирует значение РПИД = HTTPS %3 A %2 F %2 F Portal. contoso. com% 2F & RelayState = ReturnUrl% 3D% 2Fcontent% 2Fsub-Content% 2F

<!-- -->

-   чтобы получить РПИД %3 D HTTPS %2 5 3A %2 5 2F %2 5 2Fportal. contoso. com% 252F% 26RelayState% 3DReturnUrl% 253D% 252Fcontent% 252Fsub-Content% 252F

<!-- -->

-   В начале AD FS путь единого входа, инициированный IdP, чтобы получить окончательный URL-адрес.

<!-- -->

-   https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=RPID%3Dhttps%253A%252F%252Fportal.contoso.com%252F%26RelayState%3DReturnUrl%253D%252Fcontent%252Fsub-content%252F

Для создания URL-адреса можно использовать следующий скрипт [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] (сохранить в файл с именем жет-идпинитиатедурл. ps1).

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

## <a name="saml-20-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>Параметры SAML 2,0 для [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]

Предыдущий раздел, описывающий [!include[](../../../includes/pn-adfs-short.md)], можно также применить к [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD](https://msdn.microsoft.com/library/azure/mt168838.aspx), так как [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD ведет себя как стандартный [SAML&ndash;2,0](https://msdn.microsoft.com/library/azure/dn195591.aspx) , совместимый с IDP. Чтобы начать работу, войдите в [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] портал управления](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal) и создайте или выберите существующий каталог. Если каталог доступен, следуйте инструкциям по [добавлению приложения](https://msdn.microsoft.com/library/azure/dn132599.aspx) в каталог.  

1.  В меню**приложения** каталога выберите **Добавить**.
2.  Выберите **Добавить приложение, разрабатываемое моей организацией**.
3.  Укажите пользовательское имя для приложения, а затем выберите тип **веб-приложение и (или) веб-API**.
4.  Для **URL-адреса входа** и**URI идентификатора приложения**укажите URL-адрес портала для обоих полей https://portal.contoso.com/.
    Это соответствует значению параметра сайта **сервицепровидерреалм** (wtrealm).
5. На этом этапе создается новое приложение. Перейдите к разделу **Настройка** в меню.

    В разделе **единый вход** Обновите первую запись **URL-адреса ответа** , чтобы включить путь в URL-адрес https://portal.contoso.com/signin-azure-ad.

    Это соответствует значению параметра сайта **AssertionConsumerServiceUrl** (wreply).

6. В меню нижнего колонтитула выберите **просмотреть конечные точки** и обратите внимание на поле **документ метаданных федерации** .

Это соответствует значению параметра сайта **MetadataAddress** .

-   Вставьте этот URL-адрес в окно браузера, чтобы просмотреть XML-файл метаданных федерации, и обратите внимание на атрибут **entityID** корневого элемента.
-   Это соответствует значению параметра сайта**AuthenticationType** .

> [!Note]
> Стандартная конфигурация [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD использует только следующие параметры (с примерами значений): Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/MetadataAddress-<https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml> 
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AuthenticationType-<https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/>  
> - Используйте значение атрибута**entityID** в корневом элементе метаданных федерации (откройте**URL-адрес MetadataAddress** в браузере, который является значением указанного выше параметра сайта). 
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/Сервицепровидерреалм-<https://portal.contoso.com/>  
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AssertionConsumerServiceUrl-<https://portal.contoso.com/signin-azure-ad>                                                                                   |

## <a name="shibboleth-identity-provider-3"></a>Поставщик удостоверений Shibboleth 3

Используйте следующие рекомендации для правильной настройки [поставщика удостоверений Shibboleth](https://wiki.shibboleth.net/confluence/display/IDP30/Home) в качестве службы IDP. В следующем примере предполагается, что IdP размещается в https://idp.contoso.comдомена.  

URL-адрес метаданных федерации — https://idp.contoso.com/idp/shibboleth

-   IdP должен быть настроен для создания или обслуживания постоянного идентификатора. Следуйте инструкциям, чтобы включить [Создание постоянного идентификатора](https://wiki.shibboleth.net/confluence/display/IDP30/NameIDGenerationConfiguration).  

-   Метаданные федерации IdP (&lt;Идпссодескриптор&gt;) должны быть настроены для включения [привязки перенаправления единого входа](https://shibboleth.net/about/advanced.html). [Пример](https://wiki.shibboleth.net/confluence/display/SHIB2/MetadataExample).  

```
<SingleSignOnService Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-Redirect"

Location=https://idp.contoso.com/idp/profile/SAML2/Redirect/SSO/>
```

Настройте поставщиков услуг (проверяющие стороны), настроив [файл Метадата-провидерс. XML](https://wiki.shibboleth.net/confluence/display/IDP30/MetadataConfiguration).  

-   Метаданные федерации каждого поставщика услуг (&lt;Спссодескриптор&gt;) должны включать привязку службы утверждения, выполняемую после. Один из вариантов — использовать [филесистемметадатапровидер](https://wiki.shibboleth.net/confluence/display/IDP30/FilesystemMetadataProvider) и ссылаться на файл конфигурации, содержащий:  

```
<AssertionConsumerService index=1 isDefault=true

Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST"

Location=https://portal.contoso.com/signin-saml2/>
```

Атрибут Location соответствует параметру**AssertionConsumerServiceUrl** (wreply).

-   Метаданные федерации поставщика услуг должны указывать атрибут **entityID** для EntityDescriptor, соответствующий параметру **AuthenticationType** .

**&lt;EntityDescriptor entityID =<https://portal.local.contoso.com/&gt>;...**

> [!Note] 
> Стандартная конфигурация Shibboleth использует только следующие параметры (с примерами значений):   
> Authentication/SAML2/Shibboleth/MetadataAddress- https://idp.contoso.com/idp/shibboleth   
> -   Authentication/SAML2/Shibboleth/AuthenticationType- https://idp.contoso.com/idp/shibboleth 
> -   Используйте значение атрибута **entityID** в корневом элементе метаданных федерации (откройте **URL-адрес MetadataAddress** в браузере, который является значением указанного выше параметра сайта).  
> -   Authentication/SAML2/Shibboleth/Сервицепровидерреалм- https://portal.contoso.com/ 
> -   Authentication/SAML2/Shibboleth/AssertionConsumerServiceUrl- https://portal.contoso.com/signin-saml2 

### <a name="idp-initiated-sign-in"></a>Вход, инициированный IdP

Shibboleth поддерживает профиль [SSO, инициированный IDP](https://wiki.shibboleth.net/confluence/display/SHIB2/IdPUnsolicitedSSO) [спецификации](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline)SAML 2,0. Чтобы портал (поставщик услуг) правильно отвечал на запрос SAML, инициированный IdP, параметр RelayState должен быть правильно закодирован.  

Базовое строковое значение, которое должно быть закодировано в параметре SAML RelayState, должно иметь формат **ReturnUrl =/контент/суб-контент/** , где **/контент/суб-контент/** — это путь к веб-странице, на которую вы хотите зайти на портале (поставщик услуг). Путь может быть заменен любой допустимой веб-страницей на портале. Полный URL-адрес единого входа, инициированный IdP, должен быть в формате <https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=&lt;URL> закодированный поставщик ID&gt;& Target =&lt;URL-адрес возврата&gt;.

Например, если задан путь к поставщику службы **/контент/суб-контент/** и идентификатор проверяющей стороны **https://portal.contoso.com/** , последний URL-адрес https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=https%3A%2F%2Fportal.contoso.com%2F&target=ReturnUrl%3D%2Fcontent%2Fsub-content%2F

Для создания URL-адреса можно использовать следующий скрипт [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] (сохранить в файл с именем жет-шибболесидпинитиатедурл. ps1).

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

Процесс добавления отношения доверия с проверяющей стороной в [!include[](../../../includes/pn-adfs-short.md)] можно также выполнить, выполнив следующий сценарий [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] на [!include[](../../../includes/pn-adfs-short.md)] сервере (Сохраните содержимое в файл с именем адд-адкспорталрелингпартитрустфорсамл. ps1). После выполнения сценария продолжите настройку параметров сайта портала.

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

[Настройка проверки подлинности на портале](configure-portal-authentication.md)  
[Настройка удостоверения для проверки подлинности на портале](set-authentication-identity.md)  
[Параметры поставщика OAuth2 для порталов](configure-oauth2-settings.md)  
[Параметры поставщика Connect Open ID для порталов](configure-openid-settings.md)  
[Параметры поставщика WS-Federation для порталов](configure-ws-federation-settings.md)  
