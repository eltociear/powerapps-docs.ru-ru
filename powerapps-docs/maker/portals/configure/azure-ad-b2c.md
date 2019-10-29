---
title: Параметры поставщика Azure AD B2C для порталов | MicrosoftDocs
description: Инструкции по включению параметров поставщика Azure AD B2C для порталов.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: aead447bbab7f6e5758cdea0a9c6be5c0e8f41e2
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72978400"
---
# <a name="azure-ad-b2c-provider-settings-for-portals"></a>Параметры поставщика Azure AD B2C для порталов

[!include[Azure](../../../includes/pn-azure-shortest.md)] Active Directory (Azure AD) включает в себя службы Office 365 и Dynamics 365 для сотрудника или внутренней проверки подлинности. [!include[Azure](../../../includes/pn-azure-shortest.md)] Active Directory B2C — это расширение этой модели проверки подлинности, которое обеспечивает вход внешних клиентов через локальные учетные данные и Федерацию с различными общими поставщиками удостоверений в социальных сетях.

Владелец портала может настроить на портале принятие [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C в качестве поставщика удостоверений. [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C поддерживает подключение Open ID Connect для Федерации.

В процессе настройки [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C в качестве поставщика удостоверений для портала создается несколько значений, которые будут использоваться позже при настройке портала. Эти значения можно отметить в следующей таблице. При настройке портала замените имя переменной на значения, которые вы запомните.

| Имя переменной     | Value | Description                                                           |
|-------------------|-------|-----------------------------------------------------------------------|
| Имя приложения  |       | Имя приложения, представляющего портал в качестве проверяющей стороны |
| Идентификатор приложения    |       | Идентификатор приложения, связанного с приложением, созданным в Azure Active Directory B2C.  |
| Policy-SignIn — URL-адрес |       | URL-адрес издателя (ISS), определенный в конечной точке метаданных.                |
| Имя Федерации   |       | Уникальное имя, идентифицирующее тип поставщика Федерации, например "B2C". Он будет использоваться в именах параметров сайта для группировки параметров конфигурации данного конкретного поставщика.                                                                      |
| | | |

### <a name="use-azure-ad-b2c-as-an-identity-provider-for-your-portal"></a>Использование Azure AD B2C в качестве поставщика удостоверений для портала

1. Войдите в [портал Azure](https://portal.azure.com/).
2. [Создание клиента Azure AD B2C](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-get-started).
3. Выберите **[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C** на самой левой панели навигации.
4. [Создайте приложение Azure](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-app-registration#register-a-web-application).

   > [!Note]
   > Необходимо выбрать **значение Да** для поля **разрешить неявное выполнение** и указать URL-адрес портала в поле **URL-адрес ответа** . Значение в поле **URL-адрес ответа** должно быть в формате [домен портала]/Сигнин-[Federation-name]. Например, `https://contosocommunity.microsoftcrmportals.com/signin-B2C`.

5. Скопируйте имя приложения и введите его в качестве значения имени приложения в приведенной выше таблице.
6. Скопируйте идентификатор приложения и введите его в качестве значения параметра Application-ID в приведенной выше таблице.
7. [Создайте политику регистрации или входа](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-reference-policies#create-a-sign-up-or-sign-in-policy).
8. Выберите политику и нажмите кнопку **изменить**.
9. Выберите **токен, сеанс & конфигурации единого входа**.
10. В списке **утверждение издателя (ISS)** выберите URL-адрес с **/ТФП** в пути.
11. Сохраните политику.
12. Выберите URL-адрес в **конечной точке метаданных для этого поля политики** .
13. Скопируйте значение поля Issuer и введите его в качестве значения параметра Policy-SignIn-URL в предыдущей таблице. 

## <a name="portal-configuration"></a>Конфигурация портала

После создания и настройки клиента B2C в [!include[Azure](../../../includes/pn-azure-shortest.md)]необходимо настроить портал для Федерации с [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C с помощью протокола Open ID Connect. Необходимо создать уникальное имя Федерации для [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C&mdash;например, B2C&mdash;и сохранить его в качестве значения переменной *Federation Name* в приведенной выше таблице.

### <a name="configure-your-portal"></a>Настройка портала
1. Откройте приложение управления портала.
2. Перейдите на **порталы** > **веб-сайты**.
3. Выберите запись веб-сайта, для которой необходимо включить [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C.
4. Перейдите к разделу **Параметры сайта**.
5. Создайте следующие параметры сайта.
   -   **Имя**: Authentication/OpenIdConnect/[Federation-name]/аусорити

       **Значение**: [Policy-SIGNIN-URL]
   -   **Имя**: Authentication/OpenIdConnect/[Federation-name]/клиентид

       **Значение**: [Application-ID]
   -   **Имя**: Authentication/OpenIdConnect/[Federation-name]/редиректури

       **Значение**: [домен портала]/Сигнин-[Federation-name]

       Например, `https://mysite.com/signin-b2c` 
6. Для поддержки федеративного выхода создайте следующий параметр сайта:
   - **Имя**: Authentication/OpenIdConnect/[Federation-name]/екстерналлогаутенаблед

     **Значение**: true
7. Чтобы жестко настроить портал для работы с одним поставщиком удостоверений, создайте следующий параметр сайта:
   - **Имя**: проверка подлинности, регистрация и логинбуттонаусентикатионтипе

     **Значение**: [Policy-SIGNIN-URL]

8. Для поддержки сброса пароля создайте необходимые параметры сайта, описанные [здесь](#password-reset).
9. Для поддержки сопоставления утверждений создайте необходимые параметры сайта, описанные [здесь](#claims-mapping).

Полный список связанных параметров сайта см. [здесь](#related-site-settings).

### <a name="password-reset"></a>Сброс пароля

Если требуется поддержка сброса пароля с локальными учетными записями [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C, требуются следующие параметры сайта:

| Параметр сайта                                                        | Description                                                                                                          |
|---------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| Authentication/OpenIdConnect/[Federation-Name/Пассвордресетполициид | Идентификатор политики сброса пароля.                                                                                     |
| Authentication/OpenIdConnect/[Federation-name]/Валидиссуерс         | Разделенный запятыми список издателей, включающий [Policy-SignIn-URL] и издатель политики сброса паролей. |
|Authentication/OpenIdConnect/[Federation-name]/Дефаултполициид | Идентификатор политики входа или регистрации.|
|||

### <a name="related-site-settings"></a>Параметры связанных сайтов

Вы можете создать или настроить следующие параметры сайта на порталах для поддержки [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C в качестве поставщика удостоверений.


| Параметр сайта                                                         | Description                                                                                                                                                                                                                                                        |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Проверка подлинности/регистрация/Профилередиректенаблед                   | Указывает, может ли портал перенаправлять пользователей на страницу профиля после успешного входа. По умолчанию задано значение true.                                                                                                                                            |
| Проверка подлинности/регистрация/Емаилконфирматионенаблед                 | Указывает, требуется ли проверка электронной почты. По умолчанию задано значение true.                                                                                     |
| Проверка подлинности/регистрация/Локаллогиненаблед                        | Указывает, требуется ли локальный вход. По умолчанию задано значение true.                                                                        |
| Проверка подлинности/регистрация/Екстерналлогиненаблед                     | Включает или отключает внешнюю проверку подлинности.       |
| Проверка подлинности/регистрация/Азуреадлогиненаблед                      | Включает или отключает [!include[Azure](../../../includes/pn-azure-shortest.md)] AD в качестве внешнего поставщика удостоверений. По умолчанию задано значение true.                                                                                                                                                                      |
| Authentication/OpenIdConnect/[Federation-name]/Екстерналлогаутенаблед | Включает или отключает федеративный выход. Если задано значение true, при выходе из портала пользователи будут перенаправляться к пользователю федеративного выхода. Если задано значение false, пользователи будут выписываться только с портала. По умолчанию он имеет значение false.               |
| Проверка подлинности и Логинтраккинженаблед                                  | Включает или отключает отслеживание последнего входа пользователя. Если задано значение true, Дата и время отображаются в поле **Последнее успешное выполнение входа** в записи Contact. По умолчанию задано значение false.                                                            |
| Authentication/OpenIdConnect/[Federation-name]/Регистратионенаблед   | Включает или отключает требование регистрации для существующего поставщика удостоверений. Если задано значение true, регистрация для существующего поставщика включается только в том случае, если для параметра сайта проверка подлинности/регистрация/включено также задано значение true. По умолчанию задано значение true. |
|Authentication/OpenIdConnect/[Federation-name]/Постлогаутредиректури |Указывает URL-адрес в портале для перенаправления после выхода пользователя. |
| | |

### <a name="related-content-snippet"></a>Связанный фрагмент содержимого

Если регистрация отключена для пользователя после того, как пользователь активировал приглашение, отобразится сообщение с помощью следующего фрагмента содержимого:

**Имя**: учетная запись, регистр или регистратиондисабледмессаже

**Значение**: регистрация отключена.

## <a name="customize-the-includeazureincludespn-azure-shortestmd-ad-b2c-user-interface"></a>Настройка пользовательского интерфейса [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C поддерживает настройку пользовательского интерфейса. Вы можете настроить пользовательский интерфейс для сценариев регистрации и входа.

### <a name="step-1-create-a-web-template"></a>Шаг 1. Создание веб-шаблона
Создайте веб-шаблон, используя следующие значения:

**Имя**: [!include[Azure](../../../includes/pn-azure-shortest.md)] настраиваемая страница AD B2C

**Источник**: используйте следующий образец HTML-кода исходного кода шаблона.

```html
<!DOCTYPE html>
<html lang=en-US>
  <head>
    <meta charset=utf-8>
    <meta name=viewport content=width=device-width, initial-scale=1.0>
    <meta http-equiv=X-UA-Compatible content=IE=edge>
    <title>
      {{ page.title | h }}
    </title>
                        <link href={{ request.url | base }}/bootstrap.min.css rel=stylesheet>
                        <link href={{ request.url | base }}/theme.css rel=stylesheet>
                        <style>
                          .page-heading {
            padding-top: 20px;
      }
      .page-copy {
            margin-bottom: 40px;
      }
      .highlightError {
        border: 1px solid #cb2027!important;
        background-color: #fce8e8!important;
      }
      .attrEntry .error.itemLevel {
        display: none;
        color: #cb2027;
        font-size: .9em;
      }
      .error {
        color: #cb2027;
      }
      .entry {
        padding-top: 8px;
        padding-bottom: 0!important;
      }
      .entry-item {
        margin-bottom: 20px;
      }
      .intro {
        display: inline;
        margin-bottom: 5px;
      }
      .pageLevel {
          width: 293px;
          text-align: center;
          margin-top: 5px;
          padding: 5px;
          font-size: 1.1em;
          height: auto;
      }
      #panel, .pageLevel, .panel li, label {
          display: block;
      }
      #forgotPassword {
          font-size: .75em;
          padding-left: 5px;
      }
      #createAccount {
          margin-left: 5px;
      }
      .working {
          display: none;
          background: url(data:image/gif;base64,R0lGODlhbgAKAPMAALy6vNze3PTy9MTCxOTm5Pz6/Ly+vNTS1Pz+/�N0Jp6BUJ9EBIISAQAh+QQJCQAKACxRAAIABgAGAAAEE1ClYU4RIIMTdCaegVCfRASCEgEAOw==) no-repeat;
          height: 10px;
          width: auto;
      }
      .divider {
        margin-top: 20px;
        margin-bottom: 10px;
      }
      .divider h2 {
        display: table;
        white-space: nowrap;
        font-size: 1em;
        font-weight: 700;
      }
      .buttons {
        margin-top: 10px;
      }
      button {
            width:auto;
            min-width:50px;
            height:32px;
            margin-top:2px;
            -moz-border-radius:0;
            -webkit-border-radius:0;
            border-radius:0;
            background:#2672E6;
            border:1px solid #FFF;
            color:#fff;
            transition:background 1s ease 0s;
            font-size:100%;
            padding:0 2px
      }

      button:hover {
            background:#0F3E83;
            border:1px solid #3079ed;
            -moz-box-shadow:0 0 0;
            -webkit-box-shadow:0 0 0;
            box-shadow:0 0 0
      }
      .password-label label {
        display: inline-block;
        vertical-align: baseline;
      }
      img {
            border:0
      }
      .divider {
            margin-top:20px;
            margin-bottom:10px
      }
      .divider h2 {
            display:table;
            white-space:nowrap;
            font-size:1em;
            font-weight:700
      }
      .divider h2:after,.divider h2:before {
            border-top:1px solid #B8B8B8;
            content:'';
            display:table-cell;
            position:relative;
            top:.7em;
            width:50%
      }
      .divider h2:before {
            right:1.8%
      }
      .divider h2:after {
            left:1.8%
      }
      .verificationErrorText {
            color:#D63301
      }
      .options div {
            display:inline-block;
            vertical-align:top;
            margin-top:7px
      }
      .accountButton,.accountButton:hover {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAh1BMVEX///9QUFBOTk5LS0tERERCQkI/Pz9ISEg6OjpGRkZNTU08PDyAgID09PSlpaWWlpZxcXFgYGBZWVlUVFT6+vrx8fHt7e3s7Ozo6Oji4uLJycnGxsa4uLiqqqqgoKCNjY2JiYmGhoZra2tmZmb7+/vu7u7d3d3U1NTNzc2+vr67u7usrKx7e3vprNQnAAAA8klEQVQ4y63Q127DMAxAUZpDwyMeSdqsNqu7/f/va6zahgGJKAr0vgk6DyQh+6V/BiTOOeNRA9zuAWBdM6WBlPDTvaUUoAuMrT0mgNvA1IJjQB3MKjACvp6DK0WAH+agtH8H9jQHLUUgz7Uhx8xOXzNESxirLCYA2mw8tacI5FyIYXq8A9ge2Qs6oTnw2e2ruho2rjBcXJ4ADh3jBOQLQnVhRFx2gNDZ4ACogbHXj/ft9Dj5AcgbJFu5AThQWuYBIGmgtAFQo4EFB+CPGthJAPypgY3BHsheA5UNwLyAvsYNoDyroKUe4EoFTQ/yDtTONvsGUJ8KTUYyH+UAAAAASUVORK5CYII=);
            background-repeat:no-repeat
      }
      .accountButton {
            border:1px solid #FFF;
            color:#FFF;
            margin-left:0;
            margin-right:2px;
            transition:background-color 1s ease 0s;
            -moz-border-radius:0;
            -webkit-border-radius:0;
            border-radius:0;
            text-align:center;
            word-wrap:break-word;
            height:34px;
            width:158px;
            padding-left:30px;
            background-color:#505050;
      }
      .accountButton:hover {
            background-color:#B9B9B9;
            border:1px solid #FFF;
            -moz-box-shadow:0 0 0;
            -webkit-box-shadow:0 0 0;
            box-shadow:0 0 0
      }
      .accountButton:focus {
            outline:gold solid 1px
      }
      #MicrosoftAccountExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAPFBMVEU1pe/////t+v4uoe5btvNixPVVwfUsoe9tyfXU7/y95vu24vrd9f5NtfLH6/ys3/o/sPE6qfD2/f+f2vnAysuQAAAAaElEQVQ4y93SORKAIAwFUEGCsoT1/nd1JkkDFhY24qt+8VMkk20lu6DAaVBOBsVKsuO8aYo08IqlYyxoRTQExfyKheRIgu5Yl4KoVhSUgNOhoiYRsmb5g2u+LtzXDNOhjKgoAZ9/8k8uZWsGqcIav5wAAAAASUVORK5CYII=);
            background-color:#33A7F2
      }
      #MicrosoftAccountExchange:hover {
            background-color:#ADDBF9
      }
      #GoogleExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAb1BMVEXcTkH////cTD/bSj3ZQDLYOyzaRDbeV0vbSDrZPS/66Obyv7rsnpfpkorjcWfgZlvXOCr++Pj5393haFz88/L88fD67Or319T1zsv1zsrxuLPuqaLuqKLoi4LlfXTgYlbWMyTWMiPwtrHwta/fXVH/sCIIAAAAmElEQVQ4y+2RyQ7DIBBDMcwAIXvovqXb/39jRaX0AEmr5px3tSV7PGLhX6TVRFpN61l9zPNS6kn9gDcXO67zDnCnO2BCiNIyMtgKKJgyY2zQ68JEDtqju0nFTcOsxPUMw1GDDUqt+tY51/YNVlhvacTgEfCDIY0Q/lkBSg4RaUmmDo4/JdMzHy1Q2ejMeCj6PrXQP5+1MI8X0Y4HL4c826EAAAAASUVORK5CYII=);
            background-color:#DC4E41
      }
      #GoogleExchange:hover {
            background-color:#F1B8B3
      }
      #TwitterExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAdVBMVEVgqd3///9Ypdtdp9xaptxSotpQodlNn9lWo9pUo9rX6Pa+2vGTw+iLvuZlqt79/P7K4PO62O+y0+6hyutysuD2+fzi7vne6/fT5PTE3fKs0O2lzeuZx+l7tuJqrd71+Pzz9vzn8PnQ4/SCueSAueNsrt9InNh7sQwBAAAAwklEQVQ4y92PRw6EMAwAXeIkdBbY3uv/n7gSAoLDD5hbPCPZgZVihEgYgNSUpmfS7bfbtHS2nReyL2Qoc+yp8ZRAwCEWjgGAPQ7sssKoAGsWBrrgyMZCwD77Uel+59E3Tt14xZ7qlY7BRf1CDgeMKMw8sBXGlKxWtLGvHCgkQ80m0YHpjjq4sQ74pn1mISLJVSAMiwJO98l/TWSNF1eGKzqKfZ7Vj0mnHHwodpP+WIYlZP373DTtVWxYr2FD3pOBdfIHhOAHYHQI9VgAAAAASUVORK5CYII=);
            background-color:#60A9DD
      }
      #TwitterExchange:hover {
            background-color:#BFDCF1
      }
      #FacebookExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAaVBMVEU7W5z///85Wps3WJsiRo8xU5fw8vYyUpY0VZiAj70pS5OBkb0vUpb7+fwsTpTR1ud6irllerBPaqX09fnx8vfs7fSQoMZxg7VsgLNGY6FCX58ZP4v++/7r7vTZ3OupstGIlsFWcalDYaCK3qwDAAAAnklEQVQ4y+XQyw7CIBAFUBgc5VUoWGtb3/7/RyoYkyZAiSsXvdt7kstA/hRg/B0GpZ6byQ3Dw0NBaH+lMYRle3T0kwayACRdBrr/gnN+QtpQWv8cR4DswiUAjozlz4RdF8AmlnmwjaDQImoZwQkRedoToUS7D+ColGoTwQidx8oEQDMHN1MBva5MOL70SCHuE1TOhOpHrRt0FWAOP4IX8PsG2qEOR30AAAAASUVORK5CYII=);
            background-color:#3B5B9C
      }
      #FacebookExchange:hover {
            background-color:#B0BDD7
      }
      #LinkedInExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAb1BMVEUAe7b///8AdrMklscAc7EAeLUAcbB5ttifzeMqmckAdLIAaqz7+/6PxeAShr0CgLkAba4nmMctksTv9Puw1eij0OWGvNtfrNJNo80YjMAeib/D4vGt3Oy82+yfzOOCvtyJvdx3tddirtI/ncoxmMj9KsrQAAAAw0lEQVQ4y9WSVw7DIAxAG8CkjJDVzO5x/zMWk0RNJaB/kfo+sGUeCMvstgI4J7F9aS5NxSLnTWLpZVDgexTqIiycUNBhgTxRyCKPYJ3dl7sITCkO+FyLXaWU310DscASOesf3ahWChGJ5cb4ASO5Joiu2EegWEmZa1c3yUwOHmHNuQgJup4CgF8YlKpcMhKvkNmb1REz6hdetsyziIBldv8lpH8ouGm28zQFCu2SOSAXlJYGYCgpFThEMFPm/zCryja8Acy7CRfMrcKPAAAAAElFTkSuQmCC);
            background-color:#0077B5
      }
      #LinkedInExchange:hover {
            background-color:#99CAE1
      }
      #AmazonExchange {
            background-image:url(https://images-na.ssl-images-amazon.com/images/G/01/lwa/btnLWA_gold_156x32.png);
            background-color:#FFF;
            color:transparent
      }

      #next {
            -moz-user-select:none;
            user-select:none;
            cursor:pointer;
            width:auto;
            padding-left:10px;
            padding-right:10px;
            height:30.5px;
            -moz-border-radius:0;
           -webkit-border-radius:0;
            border-radius:0;
            background:#2672E6;
            border:1px solid #FFF;
            color:#fff;
            transition:background 1s ease 0s;
            font-size:100%
      }
      #next:hover {
            background:#0F3E83;
            border:1px solid #FFF;
            box-shadow:0 0 0
      }
      #next:hover,.accountButton:hover {
            -moz-box-shadow:0 0 0;
            -webkit-box-shadow:0 0 0;
            box-shadow:0 0 0;
      }
                        </style>
  </head>
  <body>
    <div class=navbar navbar-inverse navbar-static-top role=navigation>
      <div class=container>
        <div class=navbar-header>
          <div class=visible-xs-block>
            {{ snippets[Mobile Header] }}
          </div>
          <div class=visible-sm-block visible-md-block visible-lg-block navbar-brand>
            {{ snippets[Navbar Left] }}
          </div>
        </div>
      </div>
    </div>
    <div class=container>
      <div class=page-heading>
        <ul class=breadcrumb>
          <li>
            <a href={{ request.url | base }} title=Home>Home</a>
          </li>
          <li class=active>{{ page.title | h}}</li>
        </ul>
        {% include 'Page Header' %}
     </div>
     <div class=row>
      <div class=col-md-12>
        {% include 'Page Copy' %}
        <div id=api></div>
      </div>
     </div>
    </div>
    <footer role=contentinfo>
      <div class=footer-top hidden-print>
        <div class=container>
          <div class=row>
            <div class=col-md-6 col-sm-12 col-xs-12 text-left>
               {{ snippets[About Footer] }}
            </div>
            <div class=col-md-6 col-sm-12 col-xs-12 text-right>
              <ul class=list-social-links>
                <li><a href=#><span class=sprite sprite-facebook_icon></span></a></li>
                <li><a href=#><span class=sprite sprite-twitter_icon></span></a></li>
                <li><a href=#><span class=sprite sprite-email_icon></span></a></li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div class=footer-bottom hidden-print>
        <div class=container>
          <div class=row>
            <div class=col-md-4 col-sm-12 col-xs-12 text-left>
               {{ snippets[Footer] | liquid }}
            </div>
            <div class=col-md-8 col-sm-12 col-xs-12 text-left >
            </div>   
          </div>
        </div>
      </div>
    </footer>
  </body>
</html>
```
### <a name="step-2-create-a-page-template"></a>Шаг 2. Создание шаблона страницы

Создайте следующий шаблон страницы:
- **Имя**: [!include[Azure](../../../includes/pn-azure-shortest.md)] настраиваемая страница AD B2C
- **Тип**: веб-шаблон
- **Веб-шаблон**: [!include[Azure](../../../includes/pn-azure-shortest.md)] настраиваемая страница AD B2C
- **Использовать верхний и нижний колонтитулы веб-сайта**: снимите этот флажок

### <a name="step-3-create-a-webpage"></a>Шаг 3. Создание веб-страницы

Создайте следующую веб-страницу:
- **Имя**: вход
- **Родительский элемент** Страница: Главная
- **Частичный URL-адрес**: Azure-AD-B2C-вход
- **Шаблон страницы**: [!include[Azure](../../../includes/pn-azure-shortest.md)] пользовательской страницы AD B2C
- **Состояние публикации**: Опубликовано

### <a name="step-4-create-site-settings"></a>Шаг 4. Создание параметров сайта

Параметры сайта необходимы для настройки общего доступа к ресурсам между источниками (CORS), чтобы [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C запрашивать пользовательскую страницу и внедрять пользовательский интерфейс входа или регистрации. Создайте следующие параметры сайта.

| Имя                              | Value                             |
|-----------------------------------|-----------------------------------|
| HTTP/Access-Control — методы Allow | ПОЛУЧЕНИЕ, ПАРАМЕТРЫ                      |
| HTTP/Access-Control-Allow-Origin  | `https://login.microsoftonline.com` |
| | |

Полный список других параметров CORS см. в разделе [Поддержка протокола CORS](../add-web-resource.md#cors-protocol-support).

### <a name="step-5-includeazureincludespn-azure-shortestmd-configuration"></a>Шаг 5. Настройка [!include[Azure](../../../includes/pn-azure-shortest.md)]

1. Войдите в [!include[Azure portal](../../../includes/pn-azure-portal.md)].
2. Перейдите в колонку **управления клиентом[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C** .
3. Перейдите в раздел **параметры** > **политики регистрации или входа**. Отобразится список доступных политик.
4. Выберите политику, которую нужно изменить.
5. Выберите **изменить**.
6. Выберите **изменить политику** > **страницу настройка интерфейса пользователя** > **единая страница регистрации или входа** .
7. Задайте для параметра **использовать пользовательскую страницу** значение **Да**.
8. Задайте для **URI настраиваемой страницы** URL-адрес веб-страницы настраиваемой страницы [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C, созданной на шаге 3 этой процедуры. Например, `https://mydomain.com/azure-ad-b2c-sign-in`.
9. Выберите **ОК**.

## <a name="claims-mapping"></a>Сопоставление утверждений

Когда пользователи входят в систему в первый раз или позже, федеративный поставщик удостоверений предоставляет заявки на основе своей базы данных о входе пользователей в систему. Эти утверждения можно настроить в поставщике удостоверений.

### <a name="includeazureincludespn-azure-shortestmd-ad-b2c-email-claims"></a>утверждения электронной почты [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C отправляет заявку по электронной почте в виде коллекции. Портал принимает первый адрес электронной почты, предоставленный в коллекции, в качестве основного адреса электронной почты контакта.

### <a name="claims-to-support-sign-up-scenarios"></a>Утверждения для поддержки сценариев регистрации

При подготовке нового клиента, который не существует в Common Data Service, можно использовать входящие утверждения для заполнения новой записи о контакте, которую будет создавать портал. К общим утверждениям могут относиться имя, фамилия, адрес электронной почты и номер телефона, но их можно настроить. Требуется следующий параметр сайта:

**Имя**: Authentication/OpenIdConnect/[Federation-name]/регистратионклаимсмаппинг

**Описание**: список пар "логическое имя/утверждение", которые будут использоваться для преобразования значений утверждений к атрибутам в записи контакта, созданной во время регистрации.

**Формат**: Атрибут1 = claim1, атрибут2 = claim2, attribute3 = claim3

Например: FirstName =<http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname,lastname=http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname,jobtitle=jobTitle>

> [!NOTE]
> Убедитесь, что адрес электронной почты сопоставлен с основной электронной почтой (emailaddress1) контакта. Если вы добавили дополнительный адрес электронной почты (emailAddress2) или запасной адрес электронной почты (emailAddress3) в запись контакта и сопоставили его с сообщением электронной почты, сведения об удостоверении не будут добавлены в контакт, а новый будет создан с адресом электронной почты, используемым для регистрации в основной адрес электронной почты (emailaddress1).

### <a name="claims-to-support-sign-in-scenarios"></a>Утверждения для поддержки сценариев входа

Данные в Common Data Service и в поставщике удостоверений не связываются напрямую, поэтому данные могут оказаться несинхронизированными. На портале должен быть список утверждений, которые необходимо принять из любого события входа для обновления в Common Data Service. Эти утверждения могут быть подмножеством (или равным) утверждениями, поступающими из сценария входа. Этот параметр должен быть настроен отдельно от сопоставления утверждений, так как может потребоваться не перезаписывать некоторые ключевые атрибуты портала. Требуется следующий параметр сайта:

**Имя**: Authentication/OpenIdConnect/[Federation-name]/логинклаимсмаппинг

**Описание**: список пар "логическое имя/заявка", которые будут использоваться для отображения значений утверждений для атрибутов в записи контакта, созданной после входа.

**Формат**: Атрибут1 = claim1, атрибут2 = claim2, attribute3 = claim3

Например: FirstName =<http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname,lastname=http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname,jobtitle=jobTitle> 

Имя утверждения — это поле типа утверждения, указанное рядом с атрибутом в утверждениях приложения политики входа.

### <a name="allow-auto-association-to-a-contact-record-based-on-email"></a>Разрешить автоматическое связывание с записью контакта на основе электронной почты 

Клиенты, имеющие контактную запись со связанными сообщениями электронной почты, запускают веб-сайт, где внешние пользователи будут входить с помощью [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C с помощью механизма проверки электронной почты. Новый вход должен быть связан с существующей записью контакта вместо создания повторяющейся записи. Эта функция успешно сопоставляет контакт, не имеющий активного удостоверения, и адрес электронной почты должен быть уникальным (не связан с несколькими записями контактов). Требуется следующий параметр сайта:

**Имя**: Authentication/[Протокол]/[поставщик]/алловконтактмаппингвисемаил

**Описание**: указывает, сопоставляются ли контакты с соответствующим адресом электронной почты. Если задано значение true, этот параметр связывает уникальную запись Contact с соответствующим адресом электронной почты, а затем автоматически назначает поставщику внешний идентификатор для контакта после успешного входа пользователя. По умолчанию он имеет значение false.
