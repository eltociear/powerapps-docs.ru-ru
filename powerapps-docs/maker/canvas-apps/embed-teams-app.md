---
title: Внедрение приложения PowerApps в группах | Документация Майкрософт
description: Вы можете внедрить приложение, созданное в PowerApps в Microsoft Teams для совместного использования.
author: jimholtz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/29/2019
ms.author: jimholtz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d17b02cc87bb219474aade955a2910f12fcf7f27
ms.sourcegitcommit: 2376c1f1f3431bca52a8deb9b966ce1fe9f88da0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/30/2019
ms.locfileid: "66381393"
---
# <a name="embed-a-powerapps-app-in-teams"></a>Внедрение приложения PowerApps в группах 

Вы можете использовать PowerApps, вы создали, внедряя его непосредственно в Microsoft Teams. После завершения, пользователи могут выбрать **+** добавить в приложение на любой из **вашей** team каналы или беседы в группе, в. Оно отображается как плитки в разделе **вкладки для вашей команды**. 

Администратор приложение можно отправить, он отображается в **все** команд в свой клиент **всех вкладок разделов**. См. в разделе [общий доступ к приложению в Microsoft Teams](https://review.docs.microsoft.com/en-us/power-platform/admin/embed-app-teams?branch=JimHoltzWorkBranch).

> [!NOTE]
> Политики командного пользовательское приложение должно быть присвоено разрешить передачи пользовательских приложений. Если не удается внедрить приложение в группах, обратитесь к администратору, чтобы увидеть, если они настроили [параметрах пользовательского приложения](https://docs.microsoft.com/MicrosoftTeams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings). 

## <a name="prerequisites"></a>Технические условия

- [Иметь лицензию PowerApps](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus)
- Создать приложение на основе холста

## <a name="locate-your-powerapps-guid"></a>Найдите к PowerApp GUID

Найдите и запишите к PowerApp GUID для использования в дальнейшем.

1. Войдите в [ https://web.powerapps.com ](https://web.powerapps.com), а затем выберите **приложений** в меню.

   > [!div class="mx-imgBorder"] 
   > ![Показать список приложений](./media/embed-teams-app/file-apps2.png "Показать список приложений")

2. Выберите **дополнительные команды** (...) для приложения, вы хотите совместно использовать в группах, а затем выберите **сведения**.

   > [!div class="mx-imgBorder"] 
   > ![Сведения о приложении](./media/embed-teams-app/app-details.png "сведения о приложении")

3. Запись **идентификатор приложения** для последующего использования.

   > [!div class="mx-imgBorder"] 
   > ![Сведения о приложении](./media/embed-teams-app/app-details2.png "сведения о приложении")

## <a name="install-app-studio"></a>Установка App Studio

Эти действия можно пропустить, если App Studio уже установлена. 

1. В Teams выберите **приложений** в левой нижней части меню команд (![значок приложения](./media/embed-teams-app/apps-icon.png "значок приложения")).

2. Поиск «App Studio» в поле поиска, а затем выберите его.

   > [!div class="mx-imgBorder"] 
   > ![App Studio](./media/embed-teams-app/store-app-studio.png "App Studio")

3. Выберите **установить**. 

   > [!div class="mx-imgBorder"] 
   > ![Установка App Studio](./media/embed-teams-app/install-app-studio.png "установить App Studio")

4. Выберите **откройте** для компонента приложения.

   > [!div class="mx-imgBorder"] 
   > ![Откройте App Studio](./media/embed-teams-app/open-app-studio.png "откройте App Studio")

## <a name="create-a-teams-app-for-your-powerapp"></a>Создание приложения команды для к PowerApp

1. В группах откройте App Studio.

   > [!div class="mx-imgBorder"] 
   > ![Откройте App Studio](./media/embed-teams-app/open-app-studio2.png "откройте App Studio")

2. Выберите **редактор манифеста** , а затем выберите **создать новое приложение** под начальной настройки.

   > [!div class="mx-imgBorder"] 
   > ![Создание нового приложения](./media/embed-teams-app/create-new-app.png "Создание нового приложения")

3. Заполните сведения о приложении в **сведения о приложении** страницы.  Идентификатор GUID приложения следует использовать идентификатор GUID приложения к PowerApp, записанные выше.  Это позволит избежать дублирования групп приложений для конкретного приложения powerapps ".
 
   > [!div class="mx-imgBorder"] 
   > ![Заполните сведения](./media/embed-teams-app/fill-in-info-about-app.png "заполните сведения")

   |Поля  |Описание  |
   |---------|---------|
   |**Имена приложений** |    |
   |Короткое имя     | Обязательно. Короткое отображаемое имя для приложения. 30 знаков.        |
   |Длинное имя     | Полное имя приложения, если имя полного приложения превышает 30 символов.       | 
   |**Идентификация**     |         |
   |Идентификатор приложения     | Обязательно. Уникальный созданный корпорацией Майкрософт идентификатор для этого приложения.        |
   |Имя пакета     | Обязательно. Уникальный идентификатор для этого приложения. Мы рекомендуем использовать нотацию обратного домена; например com.example. <AppName>.       |
   |Версия     | Обязательно. Версия конкретного приложения. Если вы обновляете что-то в манифесте, версии также необходимо увеличить.     |
   |**Описания**    |     |
   | Краткое описание    | Обязательно. Краткое описание работы приложения, используемые при ограниченном пространстве. ограничение в 80 символов.   |
   | Подробное описание    | Обязательно. Полное описание приложения.     |
   | **Сведения для разработчиков**    |     |
   | Имя    | Обязательно. Отображаемое имя компании или разработчика.     |
   | Веб-сайта    | Обязательно. URL-адрес https:// на веб-сайт для вашего приложения с помощью powerapps.com. Когда пользователь устанавливает приложение, «о приложении» будет отображаться страница. Его следует ссылку на веб-версию приложения на сайте powerapps.com.   |
   | **URL-адреса приложения**    | Эти ссылки будут отображаться в **о** страницы вместе с URL-адрес веб-сайта.     |
   | Заявление о конфиденциальности    | Обязательно. URL-адрес https:// политику конфиденциальности разработчика. [Пример](https://go.microsoft.com/fwlink/p/?LinkID=698505).   |
   | Условия использования    | Обязательно. URL-адрес https:// разработчика условия использования.  [Пример](https://go.microsoft.com/fwlink/p/?LinkID=698507).  |
   | **Фирменная символика**    |     |
   | Полный цвет    | Относительный путь к полной цвета значка PNG 192 x 192.    |
   | Прозрачный структуры    |Относительный путь к структуры значком прозрачный PNG 32 x 32.     |
   | Цвет элементов    | Цвет, используемый в сочетании с и в качестве фона для вашей структуры значков.     |

Дополнительные сведения см. в разделе [Редактор манифестов](https://docs.microsoft.com/microsoftteams/platform/get-started/get-started-app-studio#manifest-editor) и [схемы манифеста](https://docs.microsoft.com/microsoftteams/platform/resources/schema/manifest-schema).

4. Перейдите к разделу фирменной символики и добавьте Ваши логотипы и Цвет диакритических знаков, требуемого для вашего приложения.  Это логотипы, которые будут отображаться для вашего приложения в группах. 

   > [!div class="mx-imgBorder"] 
   > ![Фирменная символика и вкладки](./media/embed-teams-app/branding-tabs.png "фирменную символику и вкладки")

5. В разделе **возможности**выберите **вкладки**.

6. В разделе **вкладку команда** выберите **добавить**.

   > [!div class="mx-imgBorder"] 
   > ![Вкладка Team добавить](./media/embed-teams-app/team-tab-add.png "вкладку команда Add")

7. Добавьте URL-адрес настройки приложения в поле ввода «URL-адрес для конфигурации», используя следующий формат: `https://web.powerapps.com/webplayer/teamsapptabsettings?appid=<PowerApp ID>`

   Замените `<PowerApp ID>` с идентификатор GUID приложения, записанные выше.

   Выберите [область](https://docs.microsoft.com/microsoftteams/platform/concepts/tabs/tabs-overview#tab-scope) для отображаются в приложении. Убедитесь, **можно обновить конфигурацию** установлен, и затем нажмите кнопку **Сохранить**.

   > [!div class="mx-imgBorder"] 
   > ![URL-адрес конфигурации](./media/embed-teams-app/configuration-url.png "URL-адрес конфигурации")

8. В разделе **Готово**выберите **допустимые домены**. Добавить **apps.powerapps.com** и **apps.preview.powerapps.com** как допустимые домены для него команд.

   > [!div class="mx-imgBorder"] 
   > ![Добавьте допустимые домены](./media/embed-teams-app/add-valid-domains.png "добавьте допустимые домены")

9. В разделе **Готово**выберите **тестирования и распространения**. В разделе **установить**выберите **установить**.

   > [!div class="mx-imgBorder"] 
   > ![Выберите Install](./media/embed-teams-app/test-distribute-app.png "выберите Install")

10. Выберите команду, необходимо установить в приложение, а затем выберите **установить**.

    > [!div class="mx-imgBorder"] 
    > ![Добавить в установку team](./media/embed-teams-app/new-app-add-to-team.png "добавить для команды установки")

11. Если вы хотите добавить экземпляр этого приложения в канал прямо сейчас, выберите канал, вы хотите использовать приложение, которое в и выберите **Настройка**.

    > [!div class="mx-imgBorder"] 
    > ![Выберите](./media/embed-teams-app/app-now-available.png "выберите Настройка")

12. Щелкните **Сохранить**.

## <a name="add-the-app-as-a-tab"></a>Добавить приложение в виде вкладки

Чтобы добавить приложение в виде вкладки на любой канал или диалога, выберите **+** , а затем в разделе **вкладки для вашей команды** выберите свое приложение. 

> [!div class="mx-imgBorder"] 
> ![Добавление приложения в виде вкладки](./media/embed-teams-app/add-app-as-tab.png "Добавление приложения в виде вкладки")

Приложение теперь отображается на отдельной вкладке.

> [!div class="mx-imgBorder"] 
> ![Приложение как вкладка](./media/embed-teams-app/app-as-tab.png "приложения как вкладка")

### <a name="see-also"></a>См. также
[Добро пожаловать в Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/teams-overview)<br />
[Для администраторов: Внедрение приложения в Microsoft Teams](https://docs.microsoft.com/power-platform/admin/share-app-teams)