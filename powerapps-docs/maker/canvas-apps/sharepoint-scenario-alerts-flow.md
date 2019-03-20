---
title: Настройка предупреждений о данных для информационной панели Power BI | Документация Майкрософт
description: В этой задаче мы добавим в Power BI оповещение о проектах, для утверждения которых превышено время ожидания, и поток операций, выполняемых после этого оповещения.
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/12/2017
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 89c22bec8972c0d58c559a09d4e9f0a8a8e3b7f5
ms.sourcegitcommit: 90245baddce9d92c3ce85b0537c1ac1cf26bf55a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2019
ms.locfileid: "57799095"
---
# <a name="set-up-data-alerts-for-the-power-bi-dashboard"></a>Настройка оповещений о данных для панели мониторинга Power BI
> [!NOTE]
> Эта статья входит в серию руководств по использованию PowerApps, Microsoft Flow и Power BI совместно с SharePoint Online. Обязательно просмотрите [вводные сведения](sharepoint-scenario-intro.md), чтобы получить общее представление о процессе и скачать связанные файлы.

В этой задаче мы добавим в Power BI оповещение о проектах, для утверждения которых превышено время ожидания, и поток операций, выполняемых после этого оповещения. Дополнительные сведения об оповещениях см. в статье [Оповещения о данных в службе Power BI](https://docs.microsoft.com/power-bi/service-set-data-alerts).

## <a name="step-1-create-an-alert"></a>Шаг 1. Создать оповещение
1. В службе Power BI откройте панель мониторинга, созданную в предыдущей задаче.
2. На карте с числом нажмите кнопку с многоточием (**...**).
   
    ![Карта максимального числа дней в ожидании утверждения](./media/sharepoint-scenario-alerts-flow/07-01-01-tile-ellipsis.png)
3. Выберите стрелку ![Значок колокольчика](./media/sharepoint-scenario-alerts-flow/icon-bell.png).
   
    ![Меню с плитками](./media/sharepoint-scenario-alerts-flow/07-01-02-tile-bell.png)
4. В области справа нажмите кнопку **Добавить правило оповещения**.
   
    ![Добавление правила оповещения](./media/sharepoint-scenario-alerts-flow/07-01-03-add-alert.png)
5. Изучите доступные параметры, такие как частота оповещений. Присвойте параметру **Пороговое значение** значение 25, а затем нажмите кнопку **Сохранить и закрыть**.
   
    ![Настройка порогового значения для оповещения и сохранение](./media/sharepoint-scenario-alerts-flow/07-01-04-save-alert.png)

Сейчас оповещение не активируется, несмотря на то, что 56 превышает пороговое значение 25. Оповещение активируется во время обновления данных. Мы увидим это при [сквозном выполнении сценария](sharepoint-scenario-summary.md).

При активации оповещения его автору отправляется сообщение электронной почты из службы Power BI. На следующем этапе вы узнаете, как отправлять дополнительные сообщения с помощью Microsoft Flow.

## <a name="step-2-create-a-flow-that-responds-to-the-alert"></a>Шаг 2. Создание последовательности, выполняемых после оповещения
1. Войдите на веб-сайт flow.microsoft.com, выберите **Службы**, а затем — **Power BI**.
   
    ![Power BI в Microsoft Flow](./media/sharepoint-scenario-alerts-flow/07-01-05-power-bi.png)
2. Выберите шаблон **Отправка электронного письма кому угодно при активации оповещения о данных Power BI**.
   
    ![Отправка сообщение электронной почты при активации оповещения о данных Power BI](./media/sharepoint-scenario-alerts-flow/07-01-06-alert-flow.png)
3. Выберите **Использовать этот шаблон**.
4. Войдите в Outlook и Power BI, если вы еще не сделали это, а затем нажмите кнопку **Продолжить**.
   
    ![Вход в систему и продолжение работы](./media/sharepoint-scenario-alerts-flow/07-01-08-continue.png)
5. В раскрывающемся списке **Идентификатор оповещения** выберите **Оповещение для максимального количества дней в ожидании утверждения**.
   
    ![Определение оповещения в качестве триггера](./media/sharepoint-scenario-alerts-flow/07-01-09-choose-alert.png)
6. Введите действительный адрес электронной почты в поле **Кому**.
   
    ![Указание адресата](./media/sharepoint-scenario-alerts-flow/07-01-10-choose-email.png)
7. Выберите **Изменить**, чтобы просмотреть другие поля, которые можно обновлять.
   
    ![Изменение оповещения по электронной почте](./media/sharepoint-scenario-alerts-flow/07-01-11-email-full.png)
8. В верхней правой части экрана щелкните **Создать поток** и нажмите кнопку **Готово**.
   
    ![Кнопка "Готово"](./media/sharepoint-scenario-alerts-flow/07-01-12-done.png)

Мы увидим потоковое выполнение при [сквозном выполнении сценария](sharepoint-scenario-summary.md). Теперь перейдем к последней задаче в этом сценарии — внедрению отчета Power BI в SharePoint.

## <a name="next-steps"></a>Дальнейшие действия
Следующий шаг в этой серии руководств — [внедрение отчета о проекте Power BI в SharePoint Online](sharepoint-scenario-embed-report.md).

