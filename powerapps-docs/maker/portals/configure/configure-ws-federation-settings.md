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
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542701"
---
# <a name="configure-ws-federation-provider-settings-for-portals"></a>Настройка параметров поставщика WS-Federation для порталов

В качестве поставщика удостоверений можно добавить один [!INCLUDE[pn-active-directory](../../../includes/pn-active-directory.md)] сервер служб федерации (или другую службу маркеров безопасности, совместимую с [WS-Federation](https://msdn.microsoft.com/library/bb498017.aspx)). Кроме того, одно пространство имен [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ACS](https://azure.microsoft.com/documentation/articles/active-directory-dotnet-how-to-use-access-control/) может быть настроено как набор индивидуальных поставщиков удостоверений. Параметры для AD FS и ACS основываются на свойствах класса [WsFederationAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.aspx) .

## <a name="create-an-ad-fs-relying-party-trust"></a>Создание отношения доверия с проверяющей стороной AD FS

С помощью средства управления AD FS выберите **отношения доверия** &gt; **отношения доверия с проверяющей стороной**.

1.  Выберите **Добавить отношение доверия с проверяющей стороной**.
2.  Добро пожаловать: нажмите кнопку **запустить**.
3.  Выбор источника данных: выберите **вручную ввести данные о проверяющей стороне**, а затем нажмите кнопку **Далее**.
4.  Укажите отображаемое имя: введите **имя**, а затем нажмите кнопку **Далее**.
    Пример: https://portal.contoso.com/
5.  Выберите профиль: выберите **AD FS профиль 2,0**, а затем нажмите кнопку **Далее**.
6.  Настройка сертификата: нажмите кнопку **Далее**.
7.  Настройка URL-адреса: установите флажок **включить поддержку пассивного протокола WS-Federation** .

URL-адрес пассивного протокола WS-Federation проверяющей стороны: введите https://portal.contoso.com/signin-federation

-   Примечание. для AD FS требуется, чтобы портал выполнялся по **протоколу HTTPS**.

    > [!Note]
    > Результирующая конечная точка имеет следующие параметры: тип конечной точки: **WS-Federation** .
    > -   Привязка: **POST**
    > -   Индекс: н/д (0)
    > -   URL-адрес: **https://portal.contoso.com/signin-federation**

8.  Настройка удостоверений. Укажите https://portal.contoso.com/, выберите **Добавить**, а затем нажмите кнопку **Далее**.
    Если применимо, дополнительные удостоверения можно добавить для каждого дополнительного портала проверяющей стороны. Пользователи смогут проходить проверку подлинности в любом или всех доступных удостоверениях.
9.  Выберите правила авторизации выдачи: выберите **разрешите всем пользователям доступ к этой проверяющей стороне**, а затем нажмите кнопку **Далее**.
10.  Готово к добавлению отношения доверия: нажмите кнопку **Далее**.
11.  Нажмите **Закрыть**.

Добавьте утверждение **идентификатора имени** в отношение доверия с проверяющей стороной:

**Преобразование [!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] имя учетной записи** в утверждение **ИД имени** (преобразование входящего утверждения):
- Тип входящего утверждения: имя учетной записи Windows
- Тип исходящего утверждения: ИД имени
- Формат идентификатора исходящего имени: не указано
- Пройти по всем значениям утверждений

### <a name="create-ad-fs-site-settings"></a>Создание AD FS параметров сайта

Примените параметры сайта портала, ссылающиеся на указанные выше AD FS отношения доверия с проверяющей стороной.

> [!Note]
> Стандартная конфигурация AD FS (STS) использует только следующие параметры (с примерами значений):
> - Authentication/WsFederation/ADFS/MetadataAddress- https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml
> - Authentication/WsFederation/ADFS/AuthenticationType- https://adfs.contoso.com/adfs/services/trust
>   - Используйте значение атрибута **entityID** в корневом элементе метаданных федерации (откройте **URL-адрес MetadataAddress** в браузере, который является значением указанного выше параметра сайта).
> - Authentication/WsFederation/ADFS/wtrealm- https://portal.contoso.com/
> - Authentication/WsFederation/ADFS/wreply- https://portal.contoso.com/signin-federation

**Метаданные WS-Federation** можно получить в **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]** , выполнив следующий скрипт на сервере AD FS:

```
Import-Module adfs
Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml
```


|                      Имя параметра сайта                      |                                                                                                                                                                                                                                                 Description                                                                                                                                                                                                                                                 |
|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      Проверка подлинности/регистрация/Екстерналлогиненаблед       |                                                                                                                                                                                                                Включает или отключает вход и регистрацию внешней учетной записи. Значение по умолчанию: true                                                                                                                                                                                                                 |
|      Authentication/WsFederation/ADFS/MetadataAddress       | Обязательно. URL-адрес метаданных [WS-Federation](https://msdn.microsoft.com/library/bb498017.aspx) сервера AD FS (STS). Обычно заканчивается путем:/FederationMetadata/2007-06/FederationMetadata. XML. Пример:<https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml>. Дополнительные сведения: [WsFederationAuthenticationOptions. MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx). |
|     Authentication/WsFederation/ADFS/AuthenticationType     |            Обязательно. Тип по промежуточного слоя проверки подлинности OWIN. Укажите значение атрибута [entityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata) в корне XML метаданных федерации. Пример: https://adfs.contoso.com/adfs/services/trust. Дополнительные сведения: [AuthenticationOptions. AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx).             |
|          Authentication/WsFederation/ADFS/wtrealm           |                                                                                                              Обязательно. Идентификатор проверяющей стороны AD FS. Пример: `https://portal.contoso.com/`. Дополнительные сведения: [WsFederationAuthenticationOptions. wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx).                                                                                                               |
|           Authentication/WsFederation/ADFS/wreply           |                                                                                                     Обязательно. Пассивная конечная точка WS-Federation AD FS. Пример: https://portal.contoso.com/signin-federation. Дополнительные сведения: [WsFederationAuthenticationOptions. wreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx).                                                                                                     |
|          Проверка подлинности/WsFederation/ADFS/Caption           |                                                                                                           Такую. Текст, который пользователь может отображать в пользовательском интерфейсе входа. По умолчанию: ADFS. Дополнительные сведения: [WsFederationAuthenticationOptions. Caption](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx).                                                                                                            |
|        Authentication/WsFederation/ADFS/Каллбаккпас        |                                                                                                             Необязательный путь с ограничением для обработки обратного вызова проверки подлинности. Дополнительные сведения: [WsFederationAuthenticationOptions. каллбаккпас](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx).                                                                                                              |
|       Authentication/WsFederation/ADFS/Сигнаутврепли        |                                                                                                                               Значение "wreply", используемое при выходе. Дополнительные сведения: [WsFederationAuthenticationOptions. сигнаутврепли](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signoutwreply.aspx).                                                                                                                               |
|     Authentication/WsFederation/ADFS/Баккчаннелтимеаут     |                                                                                                         Значение времени ожидания для обмена данными с обратным каналом. Пример: 00:05:00 (5 минут). Дополнительные сведения: [WsFederationAuthenticationOptions. баккчаннелтимеаут](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx).                                                                                                         |
| Authentication/WsFederation/ADFS/Рефрешониссуеркэйнотфаунд |                                                                                  Определяет, следует ли пытаться обновить метаданные после Секурититокенсигнатурекэйнотфаундексцептион. Дополнительные сведения: [WsFederationAuthenticationOptions. рефрешониссуеркэйнотфаунд](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.refreshonissuerkeynotfound.aspx).                                                                                  |
|      Authentication/WsFederation/ADFS/Усетокенлифетиме      |                                                                                                   Указывает, что время существования сеанса проверки подлинности (например, файлы cookie) должно соответствовать маркеру проверки подлинности. [WsFederationAuthenticationOptions. усетокенлифетиме](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx).                                                                                                   |
|     Authentication/WsFederation/ADFS/AuthenticationMode     |                                                                                                                                            Режим по промежуточного слоя для проверки подлинности OWIN. Дополнительные сведения: [AuthenticationOptions. AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx).                                                                                                                                             |
| Authentication/WsFederation/ADFS/Сигнинасаусентикатионтипе |                                                                                            AuthenticationType, используемый при создании System. Security. Claims. ClaimsIdentity. Дополнительные сведения: [WsFederationAuthenticationOptions. сигнинасаусентикатионтипе](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx).                                                                                            |
|       Authentication/WsFederation/ADFS/Валидаудиенцес       |                                                                                                                                         Список URL-адресов аудитории, разделенных запятыми. Дополнительные сведения: [TokenValidationParameters. алловедаудиенцес](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx).                                                                                                                                          |
|        Authentication/WsFederation/ADFS/Валидиссуерс        |                                                                                                                                              Список URL-адресов издателей, разделенных запятыми. Дополнительные сведения: [TokenValidationParameters. валидиссуерс](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.validissuers.aspx).                                                                                                                                               |
|         Authentication/WsFederation/ADFS/ClockSkew          |                                                                                                                                                                                                                               Отклонение часов, применяемое при проверке времени.                                                                                                                                                                                                                                |
|       Authentication/WsFederation/ADFS/Намеклаимтипе        |                                                                                                                                                                                                                     Тип утверждения, используемый ClaimsIdentity для хранения утверждения имени.                                                                                                                                                                                                                      |
|       Authentication/WsFederation/ADFS/Ролеклаимтипе        |                                                                                                                                                                                                                     Тип утверждения, используемый ClaimsIdentity для хранения утверждения роли.                                                                                                                                                                                                                      |
|   Authentication/WsFederation/ADFS/Рекуирикспиратионтиме    |                                                                                                                                                                                                                     Значение типа, указывающее, должны ли маркеры иметь значение срока действия.                                                                                                                                                                                                                      |
|    Authentication/WsFederation/ADFS/Рекуиресигнедтокенс     |                                                                                                                                                                       Значение типа, указывающее, может ли элемент System. IdentityModel. tokens. SecurityToken xmlns =<https://ddue.schemas.microsoft.com/authoring/2003/5> быть допустимым, если он не подписан.                                                                                                                                                                       |
|      Authentication/WsFederation/ADFS/Савесигнинтокен       |                                                                                                                                                                                                               Логическое значение, определяющее, сохраняется ли исходный маркер при создании сеанса.                                                                                                                                                                                                                |
|       Authentication/WsFederation/ADFS/Валидатеактор        |                                                                                                                                                                                                   Значение типа, указывающее, следует ли проверять System. IdentityModel. tokens. Жвтсекурититокен. Actor.                                                                                                                                                                                                    |
|      Authentication/WsFederation/ADFS/Валидатеаудиенце      |                                                                                                                                                                                                               Логическое значение, определяющее, будет ли проверяться аудитория во время проверки маркера.                                                                                                                                                                                                               |
|       Authentication/WsFederation/ADFS/ValidateIssuer       |                                                                                                                                                                                                                Логическое значение, определяющее, будет ли проверяться издатель во время проверки маркера.                                                                                                                                                                                                                |
|      Authentication/WsFederation/ADFS/Валидателифетиме      |                                                                                                                                                                                                               Логическое значение, определяющее, будет ли проверяться время существования во время проверки маркера.                                                                                                                                                                                                               |
|  Authentication/WsFederation/ADFS/Валидатеиссуерсигнингкэй  |                                                                                                                                                         Логическое значение, определяющее, будет ли вызвана проверка System. IdentityModel. tokens. SecurityKey, который подписал маркер securityToken xmlns =<https://ddue.schemas.microsoft.com/authoring/2003/5>.                                                                                                                                                          |
|            Authentication/WsFederation/ADFS/Втч             |                                                                                                                                       Задает параметр "Втч" в URL-адресе перенаправления поставщика удостоверений. Дополнительные сведения: [wsfederation](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation).                                                                                                                                       |

## <a name="ws-federation-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>Параметры WS-Federation для [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]

Предыдущий раздел, описывающий AD FS, можно также применить к [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)] ([[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD](https://msdn.microsoft.com/library/azure/mt168838.aspx)), так как [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD ведет себя как стандартная служба маркеров безопасности, совместимая с [WS-Federation](https://docs.microsoft.com/azure/active-directory/develop/active-directory-developers-guide) . Чтобы приступить к работе, войдите в [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] портал управления](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal) и создайте или выберите существующий каталог. Если каталог доступен, следуйте инструкциям по [добавлению приложения](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) в каталог.

1.  В меню **приложения** каталога выберите **Добавить**.
2.  Выберите **Добавить приложение, разрабатываемое моей организацией**.
3.  Укажите пользовательское **имя** для приложения, а затем выберите тип **веб-приложение и (или) веб-API**.
4.  Для **URL-адреса входа** и **URI идентификатора приложения**укажите URL-адрес портала для обоих полей https://portal.contoso.com/.
    - Это соответствует значению параметра сайта **wtrealm** .
5.  На этом этапе создается новое приложение. Перейдите к разделу **Настройка** в меню.
6.  В разделе **единый вход** Обновите первую запись **URL-адреса ответа** , чтобы включить путь в URL-адрес https://portal.contoso.com/signin-azure-ad.
    - Это соответствует значению параметра сайта **wreply** .
7.  Выберите **сохранить** в нижнем колонтитуле.
8.  В меню нижнего колонтитула выберите **просмотреть конечные точки** и обратите внимание на поле **документ метаданных федерации** .

    - Это соответствует значению параметра сайта **MetadataAddress** .
    - Вставьте этот URL-адрес в окно браузера, чтобы просмотреть XML-файл метаданных федерации, и обратите внимание на атрибут **entityID** корневого элемента.
    - Это соответствует значению параметра сайта **AuthenticationType** .

> [!Note]
> Стандартная конфигурация [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD использует только следующие параметры (с примерами значений):
> - Authentication/WsFederation/ADFS/MetadataAddress- https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml
> - Authentication/WsFederation/ADFS/AuthenticationType- https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/
>   - Используйте значение атрибута **entityID** в корневом элементе метаданных федерации (откройте **URL-адрес MetadataAddress** в браузере, который является значением указанного выше параметра сайта).
> - Authentication/WsFederation/ADFS/wtrealm- https://portal.contoso.com/
> - Authentication/WsFederation/ADFS/wreply- https://portal.contoso.com/signin-azure-ad

### <a name="see-also"></a>См. также

[Настройка проверки подлинности на портале](configure-portal-authentication.md)  
[Настройка удостоверения для проверки подлинности на портале](set-authentication-identity.md)  
[Параметры поставщика OAuth2 для порталов](configure-oauth2-settings.md)  
[Параметры поставщика Connect Open ID для порталов](configure-openid-settings.md)  
[Параметры поставщика SAML 2,0 для порталов](configure-saml2-settings.md)  
