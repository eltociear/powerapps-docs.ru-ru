---
title: Общие сведения о подключении к Dynamics 365 | Документация Майкрософт
description: Создание приложения для управления данными в Dynamics 365
author: Mattp123
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 11/27/2019
ms.author: matp
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4285a80d3751285929378336aa9806b3639f3457
ms.sourcegitcommit: 54d52a9c3c9242f95be54f4444054d9c41ed577c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2020
ms.locfileid: "75928960"
ms.PowerAppsDecimalTransform: true
---
# <a name="connect-to-dynamics-365-from-power-apps"></a>Подключение к Dynamics 365 из Power Apps
Power Apps позволяет быстро создавать, настраивать, совместно использовать и запускать мобильные приложения с небольшим объемом кода или без него. При помощи соединителя Dynamics 365 можно быстро создавать полезные мобильные приложения для совместного использования с другими сотрудниками вашей организации.

Выполнив действия, описанные в этом разделе, вы создадите приложение, в котором пользователи смогут просматривать, добавлять, удалять и обновлять контакты в приложениях, управляемых моделью, в Dynamics 365 (Dynamics 365 Sales, Dynamics 365 Customer Service, Dynamics 365, Dynamics 365 Marketing). и Dynamics 365 Project Service Automation. Пользователи могут запускать приложение [в браузере](../../../user/run-app-browser.md) или [на мобильном устройстве](../../../user/run-app-client.md), например на телефоне.

> [!NOTE]
> При подключении к приложениям, управляемым моделью, в Dynamics 365 рекомендуется использовать более надежный [соединитель Common Data Service](connection-common-data-service.md) .

## <a name="prerequisite"></a>Необходимое условие
Для выполнения инструкций из этого руководства потребуется учетная запись Microsoft Office 365, которая включает подписку Dynamics 365.

## <a name="create-a-connection"></a>Создание подключения
1. [Войдите в Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
2. На панели навигации слева щелкните **Подключения**.
   
    ![Параметр "Подключения" в меню "Файл"](./media/connection-dynamics-crmonline/file-connections.png)
3. В правом верхнем углу экрана щелкните **Создать подключение**.
   
    ![Создание подключения](./media/connection-dynamics-crmonline/new-connection.png)
4. В списке подключений выберите **Dynamics 365**.
   
    ![Параметр "Подключения" в меню "Файл"](./media/connection-dynamics-crmonline/connection-d365.png)
5. В диалоговом окне нажмите кнопку **Создать**.
   
    ![Создание подключения](./media/connection-dynamics-crmonline/create-connection.png)
6. В диалоговом окне **входа в учетную запись** введите учетные данные для клиента Dynamics 365 (Интернет).
   
    Будет создано подключение.

## <a name="generate-an-app-automatically"></a>Автоматическое создание приложения
1. [Войдите в Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), а затем щелкните **новое приложение** в левом нижнем углу.
   
    ![Создать приложение](./media/connection-dynamics-crmonline/new-app.png)
2. В разделе **Начать с данных** нажмите кнопку **Макет для телефона** на плитке **Dynamics 365**.
   
    ![Power Apps выберите Dynamics 365 Connector](./media/connection-dynamics-crmonline/phonelayout.png)
3. В разделе **Подключения** выберите нужное подключение, а затем набор данных, соответствующий экземпляру Dynamics 365, которым вы будете управлять в приложении.
4. В разделе **Выбор таблицы** щелкните **Контакты** и нажмите кнопку **Подключить**.
5. На панели навигации слева щелкните (коснитесь) значок, расположенный в правом верхнем углу, чтобы переключиться на представление эскиза.
   
    ![Переключение представлений](./media/connection-dynamics-crmonline/toggle-view.png)

Power Apps создает приложение с тремя экранами на основе записей контактов.

* **BrowseScreen1**. Этот экран появится по умолчанию при открытии приложения пользователями. На панели навигации слева появится эскиз для этого экрана — он отображается над двумя другими экранами.
* **DetailScreen1**. Этот экран отобразится, если щелкнуть элемент в **BrowseScreen1**.  На панели навигации слева появится эскиз для экрана **DetailScreen1** — он отображается между двумя другими экранами.
* **EditScreen1**. Этот экран появится, если щелкнуть значок "Изменить " для элемента на экране **DetailScreen1**. На панели навигации слева появится эскиз для экрана **EditScreen1** — он отображается под двумя другими экранами.

Приложение может работать и в исходном состоянии, но можно повысить его эффективность, уточнив информацию на каждом экране.

## <a name="customize-browsescreen1"></a>Настройка экрана BrowseScreen1
В рамках этой процедуры вы настроите экран **BrowseScreen1** для отображения имени и фамилии каждого контакта. Данные будут отображены в виде сетки из двух столбцов и отсортированы в алфавитном порядке по фамилии, а также будут содержать изображения.

1. На экране **BrowseScreen1** выберите коллекцию, щелкнув в ней любую запись, кроме первой.
   
    ![Выбор макета](./media/connection-dynamics-crmonline/select-gallery.png)
2. На панели справа откройте вкладку **Данные**.
3. В списке макетов выберите макет с изображением и текстом в сетке с двумя столбцами.
   
    Возможно, потребуется прокрутить экран вниз, чтобы отобразился этот параметр.
   
    ![Выбор макета](./media/connection-dynamics-crmonline/select-layout.png)
4. Скопируйте эту формулу, а затем, не отменяя выбор коллекции, вставьте формулу в строке формул (справа от кнопки **fx**):
   
    `SortByColumns(Search(Filter(Contacts;statuscode=1); TextSearchBox1.Text; "lastname"); "lastname"; If(SortDescending1; Descending; Ascending))`
5. На панели справа в верхнем раскрывающемся списке выберите пункт **firstname** (имя), а в среднем раскрывающемся списке — пункт **lastname** (фамилия).
   
    ![Выбор Body1](./media/connection-dynamics-crmonline/firstname-lastname.png)
6. (Необязательно.) В меню **Файл** выберите пункт **Сохранить как**, введите имя приложения и нажмите кнопку **Сохранить**.
   
    По умолчанию приложение сохраняется в облаке. Щелкните **Этот компьютер**, чтобы сохранить приложение локально.

## <a name="customize-detailsscreen1-and-editscreen1"></a>Настройка экранов DetailsScreen1 и EditScreen1
1. На панели навигации слева щелкните средний эскиз, чтобы перейти к экрану **DetailsScreen1**.
2. На экране **DetailScreen1**, щелкните в любом месте под строкой заголовка, чтобы отобразить параметры настройки на панели справа.
   
    ![Показать настройки формы](./media/connection-dynamics-crmonline/show-customization.png)
3. На панели справа щелкните значок с изображением глаза для каждого поля, которое нужно скрыть.
   
    ![Скрыть поля](./media/connection-dynamics-crmonline/hide-field.png)
4. Щелкните в любом месте под строкой заголовка, чтобы выбрать **Form1**.
   
    ![Выбор Form1](./media/connection-dynamics-crmonline/select-form1.png)
5. На панели справа щелкните значок глаза для каждого из этих полей, чтобы на экране отображалось изображение (если таковое содержится в таблице) и четыре других поля для каждого контакта:
   
   * **entityimage**
   * **firstname**
   * **lastname**
   * **mobilephone**
   * **emailaddress1**
     
     Панель справа должна выглядеть так, как показано ниже:
     
     ![Выбор Form1](./media/connection-dynamics-crmonline/show-fields.png)
6. Выберите экран **EditScreen1**, щелкнув нижний эскиз на панели навигации слева.
7. Повторите данную процедуру, чтобы настроить экран **EditScreen1** так же, как экран **DetailsScreen1**.
8. (Необязательно.) Сохраните приложение.

## <a name="next-steps"></a>Дальнейшие действия
* Протестируйте приложение в режиме предварительного просмотра, щелкнув экран **BrowseScreen1** на панели навигации слева и затем нажав клавишу F5 или выбрав ![режим предварительного просмотра](./media/connection-dynamics-crmonline/runpowerapp.png) в правом верхнем углу.
* [Предоставьте доступ к приложению другим пользователям](../share-app.md).
* [Добавьте второй источник данных](../add-data-connection.md).

