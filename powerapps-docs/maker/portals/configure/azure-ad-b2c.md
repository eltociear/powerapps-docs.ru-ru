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
ms.openlocfilehash: 5f902dd900e074c2e6b3f08f8848475dcd907ee4
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755502"
---
# <a name="azure-ad-b2c-provider-settings-for-portals"></a>Параметры поставщика Azure AD B2C для порталов

[!include[Azure](../../../includes/pn-azure-shortest.md)]Active Directory (Azure AD) предоставляет Office 365 и службы Dynamics 365 для сотрудников или внутренней аутентификации. [!include[Azure](../../../includes/pn-azure-shortest.md)] Active Directory B2C — это расширение данной модели проверки подлинности, которое позволяет внешнему клиенту выполнять вход с помощью локальных учетных данных и федерации с различными общими поставщиками социальных удостоверений.

Владелец портала может настроить портал так, чтобы принимать [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C как поставщика удостоверений. [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C поддерживает Open ID Connect для федерации.

В процессе настройки [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C как поставщика удостоверений для портала создается несколько значений, которые будут использоваться позднее при настройке портала. Вы можете просмотреть эти значения в следующей таблице. При настройке портала замените имя переменной на указанные здесь значения.

| Имя переменной     | Значение | Описание                                                           |
|-------------------|-------|-----------------------------------------------------------------------|
| Application-Name  |       | Имя приложения, представляющее портал как проверяющую сторону |
| Application-ID    |       | Идентификатор приложения, связанный с приложением, созданным в Azure Active Directory B2C.  |
| Policy-Signin-URL |       | URL-адрес издателя, указанный в конечной точке метаданных.                |
| Federation-Name   |       | Уникальное имя для определения типа поставщика федерации, например 'B2C'. Оно используются в именах параметров сайта для группировки параметров конфигурации данного конкретного поставщика.                                                                      |
| | | |

### <a name="use-azure-ad-b2c-as-an-identity-provider-for-your-portal"></a>Использование Azure AD B2C в качестве поставщика удостоверений для портала

1. Войдите на [портал Azure](https://portal.azure.com/).
2. [Создание клиента Azure AD B2C](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-get-started).
3. Выберите **[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C** на самой левой панели навигации.
4. [Создание приложения Azure](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-app-registration#register-a-web-application).

   > [!Note]
   > Следует выбрать значение **Да** для поля **Разрешить явный поток** и указать URL-адрес портала в поле **URL-адрес ответа**. Значение в поле **URL-адрес ответа** должно указываться в формате [домен портала]/signin-[Federation-Name]. Например: `https://contosocommunity.microsoftcrmportals.com/signin-B2C`.

5. Скопируйте имя приложения и введите его как значение параметра Application-Name в таблице выше.
6. Скопируйте идентификатор приложения и введите его как значение параметра Application-ID в таблице выше.
7. [Создание политики регистрации и входа](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-reference-policies#create-a-sign-up-or-sign-in-policy).
8. Выберите политику, затем выберите **Изменить**.
9. Выберите **Настройка токена, сеанса и SSO**.
10. В списке **Требование издателя** выберите URL-адрес, имеющий **/tfp** в своем пути.
11. Сохраните политику.
12. Выберите URL-адрес в поле **Конечная точка метаданных для этой политики**.
13. Скопируйте значение поля издателя и введите его как значение параметра Policy-Signin-URL в таблице выше. 

## <a name="portal-configuration"></a>Настройка портала

После создания и настройки клиента B2C в [!include[Azure](../../../includes/pn-azure-shortest.md)] необходимо настроить портал для объединения в федерацию с [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C с помощью протокола Open ID Connect. Необходимо создать уникальное имя федерации для [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C &mdash; например B2C &mdash; и сохранить его как значение переменной *Federation-Name* в таблице выше.

### <a name="configure-your-portal"></a>Настройка портала
1. Откройте приложение управления порталом.
2. Перейдите в раздел **Порталы** > **Веб-сайты**.
3. Выберите запись веб-сайта, для которой необходимо включить [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C.
4. Перейдите к разделу **Параметры сайта**.
5. Создайте следующие параметры сайта:
   -   **Имя**: Authentication/OpenIdConnect/[Federation-Name]/Authority

       **Значение**: [Policy-Signin-URL]
   -   **Имя**: Authentication/OpenIdConnect/[Federation-Name]/ClientId

       **Значение**: [Application-ID]
   -   **Имя**: Authentication/OpenIdConnect/[Federation-Name]/RedirectUri

       **Значение**: [домен портала]/signin-[Federation-Name]

       Например: `https://mysite.com/signin-b2c` 
6. Для поддержки объединенного в федерацию выхода создайте следующий параметр сайта:
   - **Имя**: Authentication/OpenIdConnect/[Federation-Name]/ExternalLogoutEnabled

     **Значение**: true
7. Чтобы жестко задать одного поставщика удостоверений для портала, создайте следующий параметр сайта:
   - **Имя**: Authentication/Registration/LoginButtonAuthenticationType

     **Значение**: [Policy-Signin-URL]

8. Для поддержки сброса пароля создайте необходимые параметры сайта, описанные [здесь](#password-reset).
9. Для поддержки сопоставления утверждений создайте необходимые параметры сайта, описанные [здесь](#claims-mapping).

Полный список связанных параметров сайта см. [здесь](#related-site-settings).

### <a name="password-reset"></a>Сброс пароля

Требуются следующие параметры сайта, если требуется обеспечить поддержку сброса пароля с помощью локальных учетных записей [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C:

| Параметр сайта                                                        | Описание                                                                                                          |
|---------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| Authentication/OpenIdConnect/[Federation-Name/PasswordResetPolicyId | Идентификатор политики сброса пароля.                                                                                     |
| Authentication/OpenIdConnect/[Federation-Name]/ValidIssuers         | Разделенный запятыми список издателей, содержащий [Policy-Signin-URL] и издателя политики сброса пароля. |
|Authentication/OpenIdConnect/[Federation-Name]/DefaultPolicyId | ИД политики входа или регистрации.|
|||

### <a name="related-site-settings"></a>Связанные параметры сайта

Можно создать или настроить следующие параметры сайта на порталах для поддержки [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C как поставщика удостоверений:


| Параметр сайта                                                         | Описание                                                                                                                                                                                                                                                        |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/ProfileRedirectEnabled                   | Определяет, может ли портал перенаправлять пользователей на страницу профиля после успешного входа в систему. По умолчанию установлено значение true.                                                                                                                                            |
| Authentication/Registration/EmailConfirmationEnabled                 | Определяет, требуется ли проверка электронной почты. По умолчанию установлено значение true.                                                                                     |
| Authentication/Registration/LocalLoginEnabled                        | Определяет, требуется ли локальный вход в систему. По умолчанию установлено значение true.                                                                        |
| Authentication/Registration/ExternalLoginEnabled                     | Включает или отключает внешнюю проверку подлинности.       |
| Authentication/Registration/AzureADLoginEnabled                      | Включает или отключает [!include[Azure](../../../includes/pn-azure-shortest.md)] AD как внешнего поставщика удостоверений. По умолчанию установлено значение true.                                                                                                                                                                      |
| Authentication/OpenIdConnect/[Federation-Name]/ExternalLogoutEnabled | Включает или отключает объединенный в федерацию выход. Если задано значение true, пользователи перенаправляются на страницу объединенного в федерацию выхода, на которой они выходят из портала. Если задано значение false, пользователи выходят только из портала. По умолчанию установлено значение false.               |
| Authentication/LoginTrackingEnabled                                  | Включает или отключает отслеживание последнего входа пользователя в систему. Если задано значение true, дата и время отображаются в поле **Последний успешный вход** в записи контакта. По умолчанию установлено значение false.                                                            |
| Authentication/OpenIdConnect/[Federation-Name]/RegistrationEnabled   | Включает или отключает требование регистрации для существующего поставщика удостоверений. Если задано значение true, регистрация включается для существующего поставщика, только если для параметра Authentication/Registration/Enabled также задано значение true. По умолчанию установлено значение true. |
|Authentication/OpenIdConnect/[Federation-Name]/PostLogoutRedirectUri |Определяет URL-адрес на портале для перенаправления после выхода пользователя. |
| | |

### <a name="related-content-snippet"></a>Связанный фрагмент содержимого

Если регистрация отключена для пользователя, после того как пользователь активировал приглашение, отобразите сообщение с помощью следующего фрагмента содержимого:

**Имя**: Account/Register/RegistrationDisabledMessage

**Значение**: Регистрация была отключена.

## <a name="customize-the-includeazureincludespn-azure-shortestmd-ad-b2c-user-interface"></a>Настройка пользовательского интерфейса [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C поддерживает настройку пользовательского интерфейса. Можно настроить взаимодействие с пользователей для сценариев регистрации и входа.

### <a name="step-1-create-a-web-template"></a>Шаг 1. Создание веб-шаблона
Создайте веб-шаблон с помощью следующих значений:

**Имя**: настраиваемая страница [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C

**Источник**: используйте следующий пример HTML источника веб-шаблона.

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
- **Имя**: настраиваемая страница [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C
- **Тип**: веб-шаблон
- **Веб-шаблон**: настраиваемая страница [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C
- **Использовать верхний и нижний колонтитулы веб-сайта**: снимите этот флажок

### <a name="step-3-create-a-webpage"></a>Шаг 3. Создание веб-страницы

Создайте следующую веб-страницу:
- **Имя**: вход в систему
- **Родительская** страница: домашняя
- **Частичный URL-адрес**: azure-ad-b2c-sign-in
- **Шаблон страницы**: настраиваемая страница [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C
- **Состояние публикации**: опубликовано

### <a name="step-4-create-site-settings"></a>Шаг 4. Создание параметров сайта

Параметры сайта необходимы для настройки общего доступа к ресурсам независимо от источника (CORS), чтобы разрешить [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C запрашивать настраиваемую страницу и вставлять пользовательский интерфейс входа или регистрации. Создайте следующие параметры сайта.

| Имя                              | Значение                             |
|-----------------------------------|-----------------------------------|
| HTTP/Access-Control-Allow-Methods | GET, OPTIONS                      |
| HTTP/Access-Control-Allow-Origin  | `https://login.microsoftonline.com` |
| | |

Полный список других параметров CORS см. на странице [службы поддержки протокола CORS](../add-web-resource.md#cors-protocol-support).

### <a name="step-5-includeazureincludespn-azure-shortestmd-configuration"></a>Шаг 5. Настройка [!include[Azure](../../../includes/pn-azure-shortest.md)]

1. Выполните вход в [!include[Azure portal](../../../includes/pn-azure-portal.md)].
2. Перейдите к колонке **Управление клиентом [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C**.
3. Перейдите в раздел **Параметры** > **Политики регистрации и входа**. Отобразится список доступных политик.
4. Выберите политику, которую нужно изменить.
5. Выберите **Изменить**.
6. Выберите **Изменить политику** > **Настройка пользовательского интерфейса страницы** > **Единения страница регистрации и входа**.
7. Задайте для параметра **Использовать настраиваемую страницу** значение **Да**.
8. Задайте для параметра **URI настраиваемой страницы** URL-адрес веб-страницы настраиваемой страницы [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C, созданный на шаге 3 данной процедуры. Например: `https://mydomain.com/azure-ad-b2c-sign-in`.
9. Нажмите **ОК**.

## <a name="claims-mapping"></a>Сопоставление утверждений

При входе пользователей в систему в первый раз или в последующем поставщик объединенных в федерацию удостоверений предоставляет требования на основании базы данных в отношении входа пользователей. Эти требования можно настроить в поставщике удостоверений.

### <a name="includeazureincludespn-azure-shortestmd-ad-b2c-email-claims"></a>Утверждения электронной почты [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C отправляет утверждение электронной почты как коллекцию. Портал принимает первый адрес электронной почты, указанный в коллекции, как основной адрес электронной почты контакта.

### <a name="claims-to-support-sign-up-scenarios"></a>Утверждения для поддержки сценариев регистрации

Если предоставлен новый клиент, который не существует в Common Data Service, входящие утверждения можно использовать для отсеивания новой записи контакта, которую создаст портал. Распространенные утверждения могут включать имя и фамилию, адрес электронной почты и номер телефона, но их можно настроить. Требуется следующий параметр сайта:

**Имя**: Authentication/OpenIdConnect/[Federation-Name]/RegistrationClaimsMapping

**Описание**: список логических пар "имя/утверждение", которые будут использоваться для сопоставления значений с атрибутами в записи контакта, созданной во время регистрации.

**Формат**: attribute1=claim1, attribute2=claim2, attribute3=claim3

Например: firstname=<https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname,lastname=https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname,jobtitle=jobTitle>

> [!NOTE]
> Обязательно сопоставьте адрес электронной почты с основным адресом электронной почты (emailaddress1) контакта. Если в запись контакта добавлен дополнительный адрес электронной почты (emailaddress2) или альтернативный адрес электронной почты (emailaddress3) и этот адрес сопоставлен с электронной почтой, данные удостоверения не будут добавлены в контакт, и будет создан новый контакт с адресом электронной почты, использованным для регистрации, заданным в качестве основного адреса электронной почты (emailaddress1).

### <a name="claims-to-support-sign-in-scenarios"></a>Утверждения для поддержки сценариев входа в систему

Данные в Common Data Service и у поставщика удостоверений не связаны напрямую, поэтому возможно нарушение синхронизации данных. Портал должен иметь список утверждений, которые вы хотите принять от любого события входа для обновления в Common Data Service. Эти утверждения могут быть подмножеством или равны утверждениям, поступающим из сценария входа. Это следует настраивать отдельно от сопоставления утверждений входа в систему, поскольку вам может потребоваться перезаписать некоторые ключевые атрибуты портала. Требуется следующий параметр сайта:

**Имя**: Authentication/OpenIdConnect/[Federation-Name]/LoginClaimsMapping

**Описание**: список логических пар "имя/утверждение", которые будут использоваться для сопоставления значений с атрибутами в записи контакта, созданной после входа.

**Формат**: attribute1=claim1, attribute2=claim2, attribute3=claim3

Например: firstname=<https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname,lastname=https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname,jobtitle=jobTitle> 

Именем утверждения является поле ТИП УТВЕРЖДЕНИЯ, приведенное рядом с атрибутом в утверждениях приложения политик входа в систему.

### <a name="allow-auto-association-to-a-contact-record-based-on-email"></a>Разрешение автоматической связи с записью контакта на основе электронной почты 

Клиенты, имеющие записи контактов со связанными адресами электронной почты, запускают веб-сайт, на котором внешние пользователи будут выполнять вход с помощью [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C с использованием механизма проверки электронной почты. Новый вход в систему должен быть связан с существующей записью контакта вместо создания повторяющейся записи. Эта функция успешно сопоставляет только контакты, не имеющие активного удостоверения, и адрес электронной почты должен быть уникален (не связан с несколькими записями контактов). Требуется следующий параметр сайта:

**Имя**: Authentication/[Protocol]/[Provider]/AllowContactMappingWithEmail

**Описание**: определяет, сопоставляются ли контакты с соответствующей электронной почтой. Если задано значение true, этот параметр связывает уникальную запись контакта с соответствующим адресом электронной почты, а затем автоматически назначает внешнего поставщика удостоверений контакту после успешного входа пользователя в систему. По умолчанию установлено значение false.
