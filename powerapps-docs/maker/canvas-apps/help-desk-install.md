---
title: Установка и настройка примера приложения PowerApps "Служба поддержки" | Документы Майкрософт
description: Пошаговые инструкции по установке и настройке примера приложения PowerApps "Служба поддержки".
services: ''
suite: powerapps
documentationcenter: na
author: caburk
manager: ''
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/20/2018
ms.author: caburk
ms.openlocfilehash: 97ff0c781933fa8d2896a35f0bd507bfb0b75ea9
ms.sourcegitcommit: eac8ad7b54a0b0eba6444a38a952dbfd17bc64b5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2018
---
# <a name="install-and-configure-the-help-desk-powerapps-sample"></a>Установка и настройка примера приложения PowerApps "Служба поддержки"

Пошаговые инструкции по установке и настройке примера приложения PowerApps "Служба поддержки".

Предполагаемое время выполнения этой процедуры: **10–15 минут**

Демонстрацию этой процедуры см. в следующем видео.

[![Установка приложения "Служба поддержки"](./media/help-desk-install/help-desk-install-video.png)](https://youtu.be/z4cdtD6hB_4 )

## <a name="help-desk-powerapps-sample-overview"></a>Обзор примера приложения PowerApps "Служба поддержки"
Приложение "Служба поддержки" оснащено удобным интерфейсом, с помощью которого пользователи могут обращаться к специалистам службы поддержки. Быстро находите ответы на самые важные вопросы, отслеживайте ход выполнения открытых запросов и просматривайте сведения о предыдущих запросах. Это приложение потребуется настроить в соответствии с вашими потребностями.

![Начальный экран приложения PowerApp "Служба поддержки"](./media/help-desk-install/Login-screen.png)

Просмотрите это видео, чтобы узнать, как использовать пример приложения PowerApps "Служба поддержки".

[![Демонстрация приложения "Служба поддержки"](./media/help-desk-install/help-desk-demo-video.png)](https://youtu.be/sl5fXwwnvzI)

## <a name="prerequisites"></a>Технические условия

- [Регистрация](https://web.powerapps.com/) в PowerApps.

## <a name="create-the-helpdesk-sharepoint-list"></a>Создание списка SharePoint HelpDesk (Служба поддержки)

В этом списке содержатся запросы в службу поддержки.

1. Откройте веб-браузер и перейдите к https://portal.office.com.
2. Войдите с учетной записью, которая имеет разрешение на создание списков.
3. Перейдите к семейству веб-сайтов, в котором будет размещаться список HelpDesk.
4. Щелкните **значок шестеренки** в верхней правой части веб-страницы.
5. Щелкните **Добавить приложение**.
6. В текстовом поле **Найти приложение** введите **Настраиваемый**.
7. Щелкните **значок поиска**.
8. Щелкните приложение **Настраиваемый список**.
9. В текстовом поле **Имя** введите **HelpDesk**.

    > [!IMPORTANT]
    > Если вы выбрали другое имя для списка, обязательно запишите его, так как вам потребуется использовать его вместо HelpDesk на всех этапах процесса установки и настройки.

10. Нажмите кнопку **Создать**.

### <a name="create-description-column"></a>Создание столбца Description (Описание)

1. Щелкните **Создать столбец**.
2. В текстовом поле **Имя столбца** введите **Description**.
3. В списке переключателей **Type of information in this column is** (Тип данных этого столбца) выберите **Несколько строк текста**.
4. В списке переключателей **Require that this column contains information** (Требовать, чтобы этот столбец содержал данные) выберите **Да**.
5. В списке переключателей **Specify the type of text to allow** (Укажите разрешенный тип текста) выберите **Обычный текст**.
6. Нажмите кнопку **ОК**.

### <a name="create-category-column"></a>Создание столбца Category (Категория)

1. Щелкните **Создать столбец**.
2. В текстовом поле **Имя столбца** введите **Category**.
3. В списке переключателей **Type of information in this column is** (Тип данных этого столбца) выберите **Выбор**.
4. В текстовом поле **Type each choice on a separate line** (Введите каждый вариант в отдельной строке) введите следующие значения, каждое в отдельной строке: 
    - Проблема с оборудованием ноутбука или ПК
    - Проблема с программным обеспечением ноутбука или ПК
5. В списке переключателей **Применять уникальные значения** выберите **Нет**.
6. В списке переключателей **Способ отображения вариантов** выберите **Раскрывающееся меню**.
7. В текстовом поле **Значение по умолчанию** введите **Проблема с оборудованием ноутбука или ПК**.
8. Нажмите кнопку **ОК**.

### <a name="create--complete-column"></a>Создание столбца "% Complete" (Процент выполнения)

1. Щелкните **Создать столбец**.
2. В текстовом поле **Имя столбца** введите **% Complete**.
3. В списке переключателей **Type of information in this column is** (Тип данных этого столбца) выберите **Число (1, 10, 100)**.
4. В списке переключателей **Require that this column contains information** (Требовать, чтобы этот столбец содержал данные) выберите **Нет**.
5. Нажмите кнопку **ОК**.

### <a name="create-priority-column"></a>Создание столбца Priority (Приоритет)

1. Щелкните **Создать столбец**.
2. В текстовом поле **Имя столбца** введите **Priority**.
3. В списке переключателей **Type of information in this column is** (Тип данных этого столбца) выберите **Выбор**.
4. В текстовом поле **Type each choice on a separate line** (Введите каждый вариант в отдельной строке) введите следующие значения, каждое в отдельной строке: 
    - ВЫСОКИЙ
    - СРЕДНЕСРОЧНЫЙ
    - НИЗКИЙ
5. В списке переключателей **Применять уникальные значения** выберите **Нет**.
6. В списке переключателей **Способ отображения вариантов** выберите **Раскрывающееся меню**.
7. В текстовом поле **Значение по умолчанию** введите **НИЗКИЙ**.
8. Нажмите кнопку **ОК**.

### <a name="create-taskstatus-column"></a>Создание столбца TaskStatus (Состояние задачи)

1. Щелкните **Создать столбец**.
2. В текстовом поле **Имя столбца** введите **TaskStatus**.
3. В списке переключателей **Type of information in this column is** (Тип данных этого столбца) выберите **Выбор**.
4. В текстовом поле **Type each choice on a separate line** (Введите каждый вариант в отдельной строке) введите следующие значения, каждое в отдельной строке: 
    - НЕ НАЧАТО
    - ВЫПОЛНЯЕТСЯ
    - ЗАВЕРШЕНО
    - ОТЛОЖЕНО
    - ОЖИДАНИЕ СПЕЦИАЛИСТА
5. В списке переключателей **Применять уникальные значения** выберите **Нет**.
6. В списке переключателей **Способ отображения вариантов** выберите **Раскрывающееся меню**.
7. В текстовом поле **Значение по умолчанию** введите **НЕ НАЧАТО**.
8. Нажмите кнопку **ОК**.

### <a name="create-assignedto-column"></a>Создание столбца AssignedTo (Кому назначено)

1. Щелкните **Создать столбец**.
2. В текстовом поле **Имя столбца** введите **AssignedTo**.
3. В списке переключателей **Type of information in this column is** (Тип данных этого столбца) выберите **Person or Group** (Пользователь или группа).
4. В списке переключателей **Require that this column contains information** (Требовать, чтобы этот столбец содержал данные) выберите **Нет**.
5. В списке переключателей **Разрешить выбор нескольких элементов** выберите **Нет**.
6. Нажмите кнопку **ОК**.

### <a name="edit-title-column"></a>Изменение столбца Title (Название)

1. Щелкните ссылку столбца **Title**.
2. В списке переключателей **Require that this column contains information** (Требовать, чтобы этот столбец содержал данные) выберите **Нет**.
3. Нажмите кнопку **ОК**.

## <a name="download-the-help-desk-powerapp"></a>Загрузка приложения PowerApps "Служба поддержки"

1.  В веб-браузере перейдите к http://pappsfeprodwestuscontent.blob.core.windows.net/sampleapps/helpdesk/docs/HelpDesk(SP_List).zip.
2.  Скачайте пакет PowerApps и сохраните его на компьютер.

## <a name="create-connections"></a>Создание подключений

1.  В веб-браузере перейдите к https://web.powerapps.com.
2.  Выполните вход, используя те же учетные данные, что и при регистрации.
3.  В меню слева выберите **Подключения**.
    
### <a name="create-office-365-outlook-connection"></a>Создание подключения к Office 365 Outlook

1.  Щелкните **+ Создать подключение**.
2.  В текстовом поле **Поиск** введите **Office 365 Outlook**.
3.  Выберите **Office 365 Outlook** в списке.
4.  Нажмите кнопку **Создать**.
5.  Во всплывающем окне выберите учетную запись, с которой вы вошли в систему.

### <a name="create-sharepoint-connection"></a>Создание подключения к SharePoint

1.  Щелкните **+ Создать подключение**.
2.  В текстовом поле **Поиск** введите **SharePoint**.
3.  Выберите **SharePoint** в списке.
4.  Нажмите кнопку **Создать**.
5.  Во всплывающем окне выберите учетную запись, с которой вы вошли в систему.

### <a name="create-office-365-users-connection"></a>Создание подключения "Пользователи Office 365"

1.  Щелкните **+ Создать подключение**.
2.  В текстовом поле **Поиск** введите **Пользователи Office 365**.
3.  Выберите **Пользователи Office 365** в списке.
4.  Нажмите кнопку **Создать**.
5.  Во всплывающем окне выберите учетную запись, с которой вы вошли в систему.

## <a name="import-the-help-desk-powerapp"></a>Импорт приложения PowerApps "Служба поддержки"

1.  В веб-браузере перейдите к https://web.powerapps.com.
2.  Выполните вход, используя те же учетные данные, что и при регистрации.
3.  В меню слева выберите **Приложения**. 
4.  Щелкните **Импорт пакета (предварительная версия)**.
    
    ![Экран "Импорт пакета"](./media/help-desk-install/import-package.png)

5.  Нажмите кнопку **Отправить** и выберите пакет PowerApps, загруженный в предыдущих шагах.
6.  Для типов ресурсов **Приложение** и **Поток** в поле **НАСТРОЙКА ИМПОРТА** выберите **Создать как новое**.
7.  Для подключений **SharePoint** и **Outlook** в поле **НАСТРОЙКА ИМПОРТА** выберите **Выбор во время импорта**.
    
    ![Экран параметров импорта](./media/help-desk-install/import-settings.png)

8.  Щелкните **красный значок** для **подключения к SharePoint**.
9.  В списке подключений щелкните элемент с вашим именем пользователя.

    ![Экран параметров импорта](./media/help-desk-install/import-settings-sharepoint.png)

10. Щелкните **Сохранить**.
11.  Щелкните **красный значок** для **подключения к Outlook Office 365**.
12.  В списке подключений щелкните элемент с вашим именем пользователя.

    ![Экран параметров импорта](./media/help-desk-install/import-settings-office365outlook.png)

13. Щелкните **Сохранить**.

    > [!TIP] 
    > После завершения он будет выглядеть следующим образом.

    ![Экран параметров импорта](./media/help-desk-install/import-settings-done.png)

14. Нажмите кнопку **Импорт** и подождите, пока процесс не завершится.

    ![Экран параметров импорта](./media/help-desk-install/import-done.png)

## <a name="configure-the-powerapp-to-use-the-sharepoint-list"></a>Настройка PowerApps для использования списка SharePoint

1. В веб-браузере щелкните **Приложения**.
2. Нажмите **кнопку с многоточием** рядом с приложением PowerApps "Служба поддержки".
3. Щелкните **Изменить в Интернете**.
4. Нажмите кнопку **Разрешить**.

### <a name="delete-connections"></a>Удаление подключений

1. Щелкните **Показать**.
2. Выберите **Источники данных**.
3. В области **Данные** нажмите **кнопку с многоточием** рядом с пунктом **HelpDesk**.
4. Щелкните **Удалить**.

### <a name="helpdesk-list"></a>Список HelpDesk

1. Щелкните **Показать**.
2. Выберите **Источники данных**.
3. В области **Данные** нажмите кнопку **+ Добавить источник данных**.
4. Выберите **SharePoint**.
5. Нажмите кнопку **Создать**.
6. В списке **Последние сайты** выберите сайт SharePoint, на котором вы создали список HelpDesk.

    > [!TIP] 
    > Если сайт не отображается в списке, введите URL-адрес сайта SharePoint в текстовом поле и нажмите кнопку **Перейти**.

7. В текстовом поле **Поиск** в верхней части списка введите **HelpDesk**.
8. Установите флажок рядом со списком **HelpDesk**.
9. Нажмите кнопку **Подключить**.

### <a name="update-admin-list"></a>Обновление списка администраторов

1. Выберите **LoginScreen** (Экран входа)
2. В раскрывающемся списке выберите **OnStart** (При запуске).
3. Разверните окно формул и найдите коллекцию **AdminList**.
4. Замените значения **user@microsoft.com** администраторами вашей службы поддержки.

    ![Обновление списка администраторов](./media/help-desk-install/Change-admin.png)
    
    > [!TIP] 
    > Если у вас несколько администраторов, используйте в качестве разделителя запятую.  Пример: "admin1@microsoft.com","admin2@microsoft.com".

5. Щелкните **Файл**.
6. Щелкните **Сохранить**.
7. Нажмите кнопку **Опубликовать**.
8. Щелкните **Опубликовать эту версию**.

## <a name="modify-the-flow"></a>Изменение потока

1.  В меню слева выберите **Потоки**.
2.  При необходимости выполните вход, используя те же учетные данные, что и при регистрации.
3.  Выберите **Мои потоки** в верхнем меню.
4.  Рядом с потоком **HelpDeskFlow** щелкните **значок карандаша**. 
 
    ![Экран изменения потока](./media/help-desk-install/edit-flow.png)

5.  Разверните действие **Get items** (Получить элементы). 
6.  Измените **адрес сайта** и **имя списка** в соответствии с созданным списком SharePoint HelpDesk.
    
    ![Экран изменения потока](./media/help-desk-install/edit-flow-getitems.png)

    > [!TIP] 
    > Нет необходимости вводить значения вручную, вы можете выбрать их в раскрывающихся списках.

7.  Разверните узел **Переключить**.
8.  Разверните обращение **НЕ НАЧАТО**.
9.  Разверните действие **Отправить сообщение электронной почты**.
10. Замените значение в поле **Кому** адресом электронной почты администратора службы поддержки.

    ![Экран изменения потока](./media/help-desk-install/edit-flow-condition-send-email.png) 

11. Щелкните **Обновить поток**.

## <a name="play-the-powerapp"></a>Запуск приложения PowerApps

1. В веб-браузере щелкните **Приложения**.
2. Нажмите **кнопку с многоточием** рядом с приложением PowerApps "Служба поддержки".
3. Щелкните **Открыть**. 

Просмотрите это видео, чтобы узнать, как использовать пример приложения PowerApps "Служба поддержки".

[![Демонстрация приложения "Служба поддержки"](./media/help-desk-install/help-desk-demo-video.png)](https://youtu.be/sl5fXwwnvzI)