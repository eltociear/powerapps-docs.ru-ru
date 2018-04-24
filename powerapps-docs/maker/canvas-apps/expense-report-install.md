---
title: Установка и настройка примера приложения PowerApps "Отчет о расходах" | Документы Майкрософт
description: Пошаговые инструкции по установке и настройке примера приложения PowerApps "Отчет о расходах".
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
ms.openlocfilehash: 0a4c35fe756e6ba9baf899a302d739467e21b591
ms.sourcegitcommit: eac8ad7b54a0b0eba6444a38a952dbfd17bc64b5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2018
---
# <a name="install-and-configure-the-expense-report-powerapps-sample"></a>Установка и настройка примера приложения PowerApps "Отчет о расходах"

Пошаговые инструкции по установке и настройке примера приложения PowerApps "Отчет о расходах".

Предполагаемое время выполнения этой процедуры: **10–15 минут**

Демонстрацию этой процедуры см. в следующем видео.

[![Установка приложения "Отчет о расходах"](./media/expense-report-install/expense-report-install-video.png)](https://youtu.be/DOR28V5kCkw)

## <a name="expense-report-powerapps-sample-overview"></a>Обзор примера приложения PowerApps "Отчет о расходах"
Отслеживайте отчеты о затратах от их подачи до утверждения. Суммируйте отдельные позиции по мере увеличения отдельных затрат и подавайте их на утверждение по мере готовности. Это приложение потребуется настроить в соответствии с вашими потребностями.

![Начальный экран приложения PowerApps "Отчет о расходах"](./media/expense-report-install/expense-report-powerapp.png)

Просмотрите это видео, чтобы узнать, как использовать пример приложения PowerApps "Отчет о расходах".

[![Установка приложения "Отчет о расходах"](./media/expense-report-install/expense-report-demo-video.png)](https://youtu.be/h6E9cdrOvMU)

## <a name="prerequisites"></a>Технические условия

- [Регистрация](../signup-for-powerapps.md) в PowerApps.

## <a name="create-the-expenses-sharepoint-list"></a>Создание списка SharePoint Expenses (Расходы)

В этом списке хранятся отчеты о расходах.

1. Откройте веб-браузер и перейдите к https://portal.office.com.
2. Войдите с учетной записью, которая имеет разрешение на создание списков.
3. Перейдите к семейству веб-сайтов, в котором будет размещаться список Expenses.
4. Щелкните **значок шестеренки** в верхней правой части веб-страницы.
5. Щелкните **Добавить приложение**.
6. В текстовом поле **Найти приложение** введите **Настраиваемый**.
7. Щелкните **значок поиска**.
8. Щелкните приложение **Настраиваемый список**.
9. В текстовом поле **Имя** введите **Expenses**.

    > [!IMPORTANT]
    > Если вы выбрали другое имя для списка, обязательно запишите его, так как вам потребуется использовать его вместо Expenses на всех этапах процесса установки и настройки.

10. Нажмите кнопку **Создать**.

### <a name="create-costcenter-column"></a>Создание столбца CostCenter (Центр затрат)

1. Щелкните список **Expenses**.
2. Щелкните **значок шестеренки** в верхней правой части веб-страницы.
3. Выберите **Параметры списка**.
4. Щелкните **Создать столбец**.
5. В текстовом поле **Имя столбца** введите **CostCenter**.
6. В списке переключателей **Type of information in this column is** (Тип данных этого столбца) выберите **Выбор**.
7. В текстовом поле **Type each choice on a separate line** (Введите каждый вариант в отдельной строке) введите следующие значения, каждое в отдельной строке: 
    - Microsoft
    - Contoso
8. В текстовом поле **Значение по умолчанию** введите **Microsoft**.
9. Нажмите кнопку **ОК**.

### <a name="create-comments-column"></a>Создание столбца Comments (Комментарии)

1. Щелкните **Создать столбец**.
2. В текстовом поле **Имя столбца** введите **Comments**.
3. В списке переключателей **Type of information in this column is** (Тип данных этого столбца) выберите **Несколько строк текста**.
4. Нажмите кнопку **ОК**.

### <a name="create-status-column"></a>Создание столбца Status (Состояние)

1. Щелкните список **Expenses**.
2. Щелкните **значок шестеренки** в верхней правой части веб-страницы.
3. Выберите **Параметры списка**.
4. Щелкните **Создать столбец**.
5. В текстовом поле **Имя столбца** введите **Status**.
6. В списке переключателей **Type of information in this column is** (Тип данных этого столбца) выберите **Выбор**.
7. В текстовом поле **Type each choice on a separate line** (Введите каждый вариант в отдельной строке) введите следующие значения, каждое в отдельной строке: 
    - Открытость
    - Pending
    - Approved
8. В текстовом поле **Значение по умолчанию** введите **Open** (Открыто).
9. Нажмите кнопку **ОК**.

### <a name="create-approvername-column"></a>Создание столбца ApproverName (Имя утверждающего)

1. Щелкните **Создать столбец**.
2. В текстовом поле **Имя столбца** введите **ApproverName**.
3. В списке переключателей **Type of information in this column is** (Тип данных этого столбца) выберите **Person or Group** (Пользователь или группа).
4. В списке переключателей **Require that this column contains information** (Требовать, чтобы этот столбец содержал данные) выберите **Да**.
5. Нажмите кнопку **ОК**.

### <a name="create-datesubmitted-column"></a>Создание столбца DateSubmitted (Дата отправки)

1. Щелкните **Создать столбец**.
2. В текстовом поле **Имя столбца** введите **DateSubmitted**.
3. В списке переключателей **Type of information in this column is** (Тип данных этого столбца) выберите **Дата и время**.
4. В списке переключателей **Require that this column contains information** (Требовать, чтобы этот столбец содержал данные) выберите **Да**.
5. Нажмите кнопку **ОК**.

### <a name="create-startdate-column"></a>Создание столбца StartDate (Дата начала)

1. Щелкните **Создать столбец**.
2. В текстовом поле **Имя столбца** введите **StartDate**.
3. В списке переключателей **Type of information in this column is** (Тип данных этого столбца) выберите **Дата и время**.
4. В списке переключателей **Require that this column contains information** (Требовать, чтобы этот столбец содержал данные) выберите **Да**.
5. Нажмите кнопку **ОК**.

### <a name="create-enddate-column"></a>Создание столбца EndDate (Дата окончания)

1. Щелкните **Создать столбец**.
2. В текстовом поле **Имя столбца** введите **EndDate**.
3. В списке переключателей **Type of information in this column is** (Тип данных этого столбца) выберите **Дата и время**.
4. В списке переключателей **Require that this column contains information** (Требовать, чтобы этот столбец содержал данные) выберите **Да**.
5. Нажмите кнопку **ОК**.

## <a name="create-the-line-items-sharepoint-list"></a>Создание списка SharePoint LineItems

В этом списке хранятся позиции строк, связанных с отчетами о расходах.

1. Перейдите к семейству веб-сайтов, в котором будет размещаться список Expense.
2. Щелкните **значок шестеренки** в верхней правой части веб-страницы.
3. Щелкните **Добавить приложение**.
4. В текстовом поле **Найти приложение** введите **Настраиваемый**.
5. Щелкните **значок поиска**.
6. Щелкните приложение **Настраиваемый список**.
7. В текстовом поле **Имя** введите **LineItems**.

    > [!IMPORTANT] 
    > Если вы выбрали другое имя для списка, обязательно запишите его, так как вам потребуется использовать его вместо LineItems на всех этапах процесса установки и настройки.

8. Нажмите кнопку **Создать**.
 
### <a name="create-category-column"></a>Создание столбца Category (Категория)

1. Щелкните список **LineItems**.
2. Щелкните **значок шестеренки** в верхней правой части веб-страницы.
3. Выберите **Параметры списка**.
4. Щелкните **Создать столбец**.
5. В текстовом поле **Имя столбца** введите **Category**.
6. В списке переключателей **Type of information in this column is** (Тип данных этого столбца) выберите **Выбор**.
7. В текстовом поле **Type each choice on a separate line** (Введите каждый вариант в отдельной строке) введите следующие значения, каждое в отдельной строке: 
    - Еда и напитки
    - Транспорт
    - Деловые потребности
8. В текстовом поле **Значение по умолчанию** введите **Еда и напитки**.
9. Нажмите кнопку **ОК**.

### <a name="create-cost-column"></a>Создание столбца Cost (Затраты)

1. Щелкните **Создать столбец**.
2. В текстовом поле **Имя столбца** введите **Cost**.
3. В списке переключателей **Type of information in this column is** (Тип данных этого столбца) выберите **Число (1, 10, 100)**.
4. В списке переключателей **Require that this column contains information** (Требовать, чтобы этот столбец содержал данные) выберите **Да**.
5. Нажмите кнопку **ОК**.

### <a name="create-date-column"></a>Создание столбца Date (Дата)

1. Щелкните **Создать столбец**.
2. В текстовом поле **Имя столбца** введите **Date**.
3. В списке переключателей **Type of information in this column is** (Тип данных этого столбца) выберите **Дата и время**.
4. В списке переключателей **Require that this column contains information** (Требовать, чтобы этот столбец содержал данные) выберите **Да**.
5. Нажмите кнопку **ОК**.

### <a name="create-description-column"></a>Создание столбца Description (Описание)

1. Щелкните **Создать столбец**.
2. В текстовом поле **Имя столбца** введите **Description**.
3. В списке переключателей **Type of information in this column is** (Тип данных этого столбца) выберите **Несколько строк текста**.
4. В списке переключателей **Require that this column contains information** (Требовать, чтобы этот столбец содержал данные) выберите **Да**.
5. В списке переключателей **Specify the type of text to allow** (Укажите разрешенный тип текста) выберите **Обычный текст**.
6. Нажмите кнопку **ОК**.

### <a name="create-reportid-column"></a>Создание столбца ReportID (Код отчета)

1. Щелкните **Создать столбец**.
2. В текстовом поле **Имя столбца** введите **ReportID**.
3. В списке переключателей **Type of information in this column is** (Тип данных этого столбца) выберите **Поиск (данные уже на этом сайте)**.
4. В списке переключателей **Require that this column contains information** (Требовать, чтобы этот столбец содержал данные) выберите **Да**.
5. В раскрывающемся списке **Get information from** (Получать данные из) выберите созданный список **Expenses**.
6. В раскрывающемся списке **В этом столбце** выберите **Идентификатор**.
7. Нажмите кнопку **ОК**.

### <a name="edit-title-column"></a>Изменение столбца Title (Название)

1. Щелкните ссылку столбца **Title**.
2. В списке переключателей **Require that this column contains information** (Требовать, чтобы этот столбец содержал данные) выберите **Нет**.
3. Нажмите кнопку **ОК**.

## <a name="download-the-expense-report-powerapp"></a>Загрузка приложения PowerApps "Отчет о расходах"

1.  В веб-браузере перейдите по следующей ссылке:

    http://pappsfeprodwestuscontent.blob.core.windows.net/sampleapps/myexpenses/docs/MyExpenses(SP_List).zip.

2.  Скачайте пакет примера приложения PowerApps "Отчет о расходах" и сохраните его на компьютер.

## <a name="create-connections"></a>Создание подключений

1.  В веб-браузере перейдите к https://web.powerapps.com.
2.  Выполните вход, используя те же учетные данные, что и при регистрации.
3.  В меню слева выберите **Подключения**.

### <a name="create-approvals-connection"></a>Создание подключений для утверждений

1.  Щелкните **+ Создать подключение**.
2.  В текстовом поле **Поиск** введите **Approvals** (Утверждения).
3.  Выберите **Approvals** в списке.
4.  Нажмите кнопку **Создать**.
    
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

## <a name="import-the-expense-report-powerapp"></a>Импорт приложения PowerApps "Отчет о расходах"

1.  В веб-браузере перейдите к https://web.powerapps.com.
2.  Выполните вход, используя те же учетные данные, что и при регистрации.
3.  В меню слева выберите **Приложения**. 
4.  Щелкните **Импорт пакета (предварительная версия)**.
    
    ![Экран "Импорт пакета"](./media/expense-report-install/import-package.png)

5.  Нажмите кнопку **Отправить** и выберите пакет PowerApps, загруженный в предыдущих шагах.
6.  Для типов ресурсов **Приложение** и **Поток** в поле **НАСТРОЙКА ИМПОРТА** выберите **Создать как новое**.
7.  Для подключений **SharePoint** и **Outlook** в поле **НАСТРОЙКА ИМПОРТА** выберите **Выбор во время импорта**.
    
    ![Экран параметров импорта](./media/expense-report-install/import-settings.png)

8.  Щелкните **красный значок** для **подключения к SharePoint**.
9.  В списке подключений щелкните элемент с вашим именем пользователя.

    ![Экран параметров импорта](./media/expense-report-install/import-settings-sharepoint.png)

10. Щелкните **Сохранить**.
11. Щелкните **красный значок** для **подключения к SharePoint**.
12. В списке подключений щелкните элемент с вашим именем пользователя.

    ![Экран параметров импорта](./media/expense-report-install/import-settings-approvals.png)

13.  Щелкните **Сохранить**.
14.  Щелкните **красный значок** для **подключения к Outlook Office 365**.
15.  В списке подключений щелкните элемент с вашим именем пользователя.

    ![Экран параметров импорта](./media/expense-report-install/import-settings-office365outlook.png)

16. Щелкните **Сохранить**.

    > [!TIP] 
    > После завершения он будет выглядеть следующим образом:

    ![Экран параметров импорта](./media/expense-report-install/import-settings-done.png)

17. Нажмите кнопку **Импорт** и подождите, пока процесс не завершится.

    ![Экран параметров импорта](./media/expense-report-install/import-done.png)

## <a name="configure-the-powerapp-to-use-the-sharepoint-lists"></a>Настройка PowerApps для использования списков SharePoint

1. В веб-браузере щелкните **Приложения**.
2. Нажмите **кнопку с многоточием** рядом с приложением PowerApps "Отчет о расходах".
3. Щелкните **Изменить в Интернете**.
4. Нажмите кнопку **Разрешить**.

### <a name="delete-connections"></a>Удаление подключений
1. Щелкните **Показать**.
2. Выберите **Источники данных**.
3. В области **Данные** нажмите **кнопку с многоточием** рядом с пунктом **Expenses**.
4. Щелкните **Удалить**.
5. В области **Данные** нажмите **кнопку с многоточием** рядом с пунктом **LineItems**.
6. Щелкните **Удалить**.

### <a name="expenses-list"></a>Список Expenses

1. Щелкните **Показать**.
2. Выберите **Источники данных**.
3. В области **Данные** нажмите кнопку **+ Добавить источник данных**.
4. Щелкните **+ Создать подключение**.
5. Выберите **SharePoint**.
6. Нажмите кнопку **Создать**.
7. В списке **Последние сайты** выберите сайт SharePoint, на котором вы создали список Expenses.

    > [!TIP] 
    > Если сайт не отображается в списке, введите URL-адрес сайта SharePoint в текстовом поле и нажмите кнопку **Перейти**.

8. В текстовом поле **Поиск** в верхней части списка введите **Expenses**.
9. Установите флажок рядом со списком **Expenses**.
10. Нажмите кнопку **Подключить**.

### <a name="lineitems-list"></a>Список LineItems

1. Щелкните **Показать**.
2. Выберите **Источники данных**.
3. В области **Данные** нажмите кнопку **+ Добавить источник данных**.
4. Щелкните **+ Создать подключение**.
5. Выберите **SharePoint**.
6. Нажмите кнопку **Создать**.
7. В списке **Последние сайты** выберите сайт SharePoint, на котором вы создали список LineItems.

    > [!TIP] 
    > Если сайт не отображается в списке, введите URL-адрес сайта SharePoint в текстовом поле и нажмите кнопку **Перейти**.

8. В текстовом поле **Поиск** в верхней части списка введите **LineItems**.
9. Установите флажок рядом со списком **LineItems**.
10. Нажмите кнопку **Подключить**.
11. Щелкните **Файл**.
12. Щелкните **Сохранить**.
13. Нажмите кнопку **Опубликовать**.
14. Щелкните **Опубликовать эту версию**.

## <a name="modify-the-flow"></a>Изменение потока

1.  В меню слева выберите **Потоки**.
2.  При необходимости выполните вход, используя те же учетные данные, что и при регистрации.
3.  Выберите **Мои потоки** в верхнем меню.
4.  Рядом с потоком **ApproveExpense** щелкните **значок карандаша**.
 
    ![Экран изменения потока](./media/expense-report-install/edit-flow.png)

5.  Разверните действие **Get items** (Получить элементы). 
6.  Измените **адрес сайта** и **имя списка** в соответствии с созданным списком SharePoint Expenses.
    
    ![Экран изменения потока](./media/expense-report-install/edit-flow-getitems.png)

    > [!TIP] 
    > Нет необходимости вводить значения вручную, вы можете выбрать их в раскрывающихся списках.

7.  Разверните узел **Условие**.
8.  Разверните раздел **If yes** (Если да).
9.  Разверните действие **Change item status to Approved** (Изменить состояние элемента на "Утверждено").
10. Измените **адрес сайта** и **имя списка** в соответствии с созданным списком SharePoint Expenses.

    ![Экран изменения потока](./media/expense-report-install/edit-flow-condition-ifyes.png) 

    > [!TIP] 
    > Нет необходимости вводить значения вручную, вы можете выбрать их в раскрывающихся списках.

11. Разверните раздел **If no** (Если нет).
12. Разверните действие **Change item status to Open** (Изменить состояние элемента на "Открыто").
13. Измените **адрес сайта** и **имя списка** в соответствии с созданным списком SharePoint Expenses. 

    ![Экран изменения потока](./media/expense-report-install/edit-flow-condition-ifno.png)

    > [!TIP] 
    > Нет необходимости вводить значения вручную, вы можете выбрать их в раскрывающихся списках.

14. Щелкните **Обновить поток**.

## <a name="play-the-powerapp"></a>Запуск приложения PowerApps

1. В веб-браузере щелкните **Приложения**.
2. Нажмите **кнопку с многоточием** рядом с приложением PowerApps "Отчет о расходах".
3. Щелкните **Открыть**.

Просмотрите это видео, чтобы узнать, как использовать пример приложения PowerApps "Отчет о расходах".

[![Установка приложения "Отчет о расходах"](./media/expense-report-install/expense-report-demo-video.png)](https://youtu.be/h6E9cdrOvMU)




