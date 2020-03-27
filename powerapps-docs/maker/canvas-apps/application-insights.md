---
title: Анализ телеметрии приложения с помощью Application Insights | Документация Майкрософт
description: Анализ телеметрии приложения с помощью Application Insights
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/25/2020
ms.author: aheaney
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: cf7e65d395e8ad28e434cc957502a5bce52a3e6e
ms.sourcegitcommit: 77e00640a59a7db9d67d3ac52f74d264cbe3a494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2020
ms.locfileid: "80328923"
---
# <a name="analyze-app-telemetry-using-application-insights"></a>Анализ телеметрии приложения с помощью Application Insights

Вы можете подключить приложение с помощью [Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview), функции [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview). Application Insights включает мощные средства анализа, помогающие диагностировать проблемы и понять, что пользователи фактически делают с вашим приложением. 

Если приложение подключено к Application Insights, вы можете собраться со сведениями, помогающими решить более качественные бизнес-решения и улучшить качество приложений.

В этом кратком руководстве вы сможете инструментировать приложение Canvas под названием Kudos. Это поможет исследовать, обнаруживать концепции телеметрии и применять их к собственным приложениям Canvas. Пример приложения Kudos входит в набор приложений для работы с сотрудниками, доступных для скачивания из комплекта [Starter Kit для сотрудников](https://powerapps.microsoft.com/blog/powerapps-employee-experience-starter-kit).

## <a name="prerequisites"></a>Предварительные требования

- Необходимо иметь доступ к [портал Azure](https://portal.azure.com).
- У вас должны быть разрешения на [Создание ресурсов Azure](https://docs.microsoft.com/azure/role-based-access-control/quickstart-assign-role-user-portal).

### <a name="optional"></a>Необязательно

- Скачайте и установите приложение Kudos из [набора сотрудников для начала работы](https://powerapps.microsoft.com/blog/powerapps-employee-experience-starter-kit). Вместо этого можно использовать существующее приложение.

## <a name="create-an-application-insights-resource"></a>Создание ресурса Application Insights

Прежде чем можно будет отправить данные телеметрии для приложения, необходимо создать ресурс Azure Application Insights для хранения событий.

1. Войдите в [портал Azure](https://portal.azure.com/).

1. Поиск Application Insights:

    ![Azure Application Insights](./media/application-insights/azureappinsights.png)

1. Создайте ресурс Application Insights:

    ![Добавление ресурса Application Insights Azure](./media/application-insights/azureappinsights-add.png)

1. Введите соответствующие значения и выберите **проверить и создать**. Дополнительные сведения см. в статье [создание Application Insights ресурса](https://docs.microsoft.com/azure/azure-monitor/app/create-new-resource). 

    ![Создание ресурса](./media/application-insights/createresource.png)

1. После создания экземпляра Application Insights вы увидите общие сведения об экземпляре. Скопируйте **ключ инструментирования**. Этот ключ потребуется для настройки приложения.

    ![Копировать ключ инструментирования](./media/application-insights/instrumentation-key.png)

## <a name="connect-your-app-to-application-insights"></a>Подключение приложения к Application Insights

1. Выполните вход в [Power Apps](https://make.powerapps.com).

1. В области навигации слева выберите **приложения** . В списке приложений выберите приложение **Kudos** и щелкните **изменить**:

    ![Изменить приложение Kudos](./media/application-insights/edit-kudos-app.png)

    > [!NOTE]
    > Кроме того, можно [создать](open-and-run-a-sample-app.md) новое приложение или [изменить](edit-app.md) любое существующее.

1. Выберите объект **приложения** в представлении дерева навигации слева и вставьте **ключ инструментирования**:

    ![Добавить ключ инструментирования](./media/application-insights/add-instrumentation-key.png)

1. **Сохраните** & **опубликуйте** свое приложение.

1. **Воспроизведение** опубликованного приложения и просмотр различных экранов. 

При просмотре различных экранов события автоматически регистрируются в Application Insights включая следующие сведения об использовании:

- Откуда осуществляется доступ к приложению.
- Используемые устройства.
- Используемые типы браузеров.

> [!IMPORTANT]
> Чтобы отправить события в Application Insights, необходимо воспроизвести опубликованное приложение. События не отправляются в Application Insights при предварительном просмотре приложения в Power Apps Studio.

## <a name="view-events-in-application-insights"></a>Просмотр событий в Application Insights

1. Войдите в [портал Azure](https://portal.azure.com/) и откройте созданный [ранее](#create-an-application-insights-resource)ресурс Application Insights.

1. Прокрутите вниз в левой области навигации и выберите **Пользователи** в разделе **Использование** . 

    > [!NOTE]
    > В представлении " **Пользователи** " отображаются сведения об использовании приложения, например:
    > - Число пользователей, которые просматривали приложение.
    > - Число сеансов пользователей для приложения.
    > - Число событий, регистрируемых для приложения.
    > - Сведения о версиях операционных систем и браузеров для пользователей.
    > - Регион и расположение пользователей.
    > 
    > Дополнительные сведения см. [в статье анализ пользователей, сеансов и событий в Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/usage-segmentation).

1. Выберите один из пользовательских сеансов для детализации конкретных сведений. Вы увидите такие сведения, как длина сеанса и посещаемые экраны:

    ![Сведения об использовании для пользователей](./media/application-insights/appinsights-users.gif)

1. Выберите представление " **события** " в левой области навигации в разделе " **Использование** ". Вы увидите сводку по всем экранам, просматриваемым во всех сеансах приложений:

    ![Сведения о событии для приложения](./media/application-insights/appInsights-events.gif)

> [!TIP]
> Ниже перечислены некоторые дополнительные функции Application Insights, которые можно использовать.  
> - [**Воронки**](https://docs.microsoft.com/azure/azure-monitor/app/usage-funnels)
> - [**Когорты**](https://docs.microsoft.com/azure/azure-monitor/app/usage-cohorts)
> - [**Анализ влияния**](https://docs.microsoft.com/azure/azure-monitor/app/usage-impact)
> - [**Анализ хранения**](https://docs.microsoft.com/azure/azure-monitor/app/usage-retention)
> - [**Потоки использования**](https://docs.microsoft.com/azure/azure-monitor/app/usage-flows)

## <a name="create-custom-trace-events"></a>Создание пользовательских событий трассировки

Вы можете писать пользовательские трассировки непосредственно в Application Insights и начать анализировать сведения, относящиеся к конкретному сценарию. Функция [Trace](https://docs.microsoft.com/powerapps/maker/canvas-apps/functions/function-trace) позволяет осуществлять накопление:

- Подробные сведения об использовании элементов управления на экранах.
- Конкретные пользователи, обращающиеся к вашему приложению.
- Какие ошибки возникают.

Трассировка может также помочь в диагностике проблем, так как вы можете отправить конечные данные по мере того, как пользователи просматривают приложение и выполняют различные действия.

При отправке пользовательской информации трассировки в Application Insights из приложения есть три важности для сообщений трассировки:

- **Об**
- **!**
- **План**

В зависимости от сценария можно выбрать отправку сообщения трассировки с соответствующим уровнем серьезности. Вы можете запросить данные и выполнить определенные действия в зависимости от серьезности сообщения.

> [!NOTE]
> Если вы ведете запись в журнал любых данных о персонале, необходимо учитывать любые обязательства по обеспечению соответствия данных, например GDPR, которые также могут потребоваться для реализации.

Теперь вы можете обновить приложение и создать новый компонент для сбора отзывов на каждом экране приложения. События будут записаны в Application Insights.

1. Выполните вход в [Power Apps](https://make.powerapps.com).

1. В области навигации слева выберите **приложения** . В списке приложений выберите приложение **Kudos** и нажмите кнопку **изменить**.

    > [!NOTE]
    > Кроме того, можно [создать](open-and-run-a-sample-app.md) новое приложение или [изменить](edit-app.md) любое существующее.

1. Выберите параметр **компоненты** в представлении в **виде дерева**.

    ![Компоненты](./media/application-insights/new-component.png)

1. Выберите **новый компонент**, а затем измените ширину до 200, а высота — на 75:

    ![Высота и ширина](./media/application-insights/resize-component.png)

1. Выберите в меню пункт **Вставить** , а затем щелкните **значок** , чтобы добавить значки *эмодзи-нахмуренный смайлик* и *эмодзи-смайлик* :

    ![Добавление значков](./media/application-insights/add-icons.png)

1. Выберите **новое настраиваемое свойство** , чтобы создать пользовательское свойство:

    ![Создать пользовательское свойство](./media/application-insights/create-custom-property.png)

1. Введите *имя* свойства и *Отображаемое имя* , например *фидбакксцеен*.

1. Введите *Описание*свойства.

1. Выберите **тип свойства** **входные** **данные и тип данных** в качестве **экрана**:

    ![Пользовательское свойство](./media/application-insights/custom-input-property.png)

    > [!NOTE]
    > Свойство Input позволяет записать имя экрана и его компонент, чтобы можно было записать эти сведения в Application Insights.

1. Выберите компонент в представлении в **виде дерева**, затем выберите **Дополнительные действия** (**...**), а затем нажмите кнопку **Переименовать** , чтобы переименовать компонент с осмысленным именем, например *фидбакккомпонент*.

    ![Переименование компонента и недостатков](./media/application-insights/rename-component-icons.png)

1. Выберите значки, выберите **Дополнительные действия** (**...**), а затем щелкните **Переименовать** , чтобы переименовать значки с осмысленными именами, например *фровникон* и *смилеикон*.

1. Выберите *фровникон*, выберите свойство **OnSelect** и введите в строке формул следующее выражение:

    ```
    Trace(
       "App Feedback",
       TraceSeverity.Information,
           {
             UserName: User().FullName,
             UserEmail: User().Email,
             Screen: FeedbackComponent.FeedbackScreen.Name,
             FeedbackValue: "-1"
           }
         );
    Notify("Thanks for you feedback!");
    ```

    ![Формула значка нахмуренный смайлик](./media/application-insights/frownicon-formula.png)

    > [!NOTE]
    > Выражение формулы отправляет *имя пользователя*, *UserEmail*, *экран* и *отзыв* (со значением *-1*) для Application Insights.

1. Выберите *смилеикон*, выберите свойство **OnSelect** и введите в строке формул следующее выражение:
    
    ```
    Trace(
       "App Feedback",
       TraceSeverity.Information,
           {
             UserName: User().FullName,
             UserEmail: User().Email,
             Screen: FeedbackComponent.FeedbackScreen.Name,
             FeebackValue: "1"
           }
         );
    Notify("Thanks for you feedback!");
    ```

1. Добавьте компонент на один из экранов в приложении:

    ![Добавить компонент обратной связи](./media/application-insights/add-feedback-component.png)

1. Выберите **сохранить** , а затем **опубликовать** , чтобы сохранить & публикации приложения.

1. Воспроизводите опубликованное приложение, отправляйте смайлик и нахмуренный смайлик отзывы с экрана.

    > [!IMPORTANT]
    > Чтобы отправить события в Application Insights, необходимо воспроизвести опубликованное приложение. События не отправляются в Application Insights при предварительном просмотре приложения в Power Apps Studio.

    ![Воспроизвести опубликованное приложение](./media/application-insights/play-published-app.png)

## <a name="analyze-data-in-application-insights"></a>Анализ данных в Application Insights

Теперь вы можете начать анализировать отправленные данные с помощью функции [трассировки](#create-custom-trace-events) приложения в App Insights.

1. Войдите в [портал Azure](https://portal.azure.com/) и откройте созданный [ранее](#create-an-application-insights-resource)ресурс Application Insights.

    ![Выбор Application Insights](./media/application-insights/select-app-insights.png)

1. Выберите **журналы** в разделе **мониторинг** в левой области навигации:

    ![Выбор журналов](./media/application-insights/select-logs.png)

1. Введите следующий запрос и выберите **выполнить**. Отзыв, полученный от приложения, возвращает:

    ```powerappsfl
    traces
    | where message == "App Feedback"
    | order by timestamp
    ```

    ![Просмотр отзывов о приложении](./media/application-insights/view-app-feedback.png)

1. Выберите строку в результатах и разверните поле *Custom Dimensions (пользовательские измерения* ). 

    Были записаны значения для **экрана**, **username**, **UserEmail**и **фидбакквалуе** для события **OnSelect** значка "смайлик" или "нахмуренный смайлик" в компоненте. <br>
    Кроме того, для каждого события, отправленного в Application Insights, записываются дополнительные значения. например **AppID**, **AppName** и **аппсессионид**.

    ![Развернуть пользовательские измерения](./media/application-insights/expand-custom-dimensions.png)

1. В следующем примере запроса можно расширить свойства настраиваемых измерений JSON и проецировать столбцы в представлении результатов.

    ```powerappsfl
    traces
        | extend customdims = parse_json(customDimensions)
        | where message == "App Feedback"
        | project timestamp
            , message
            , AppName = customdims.['ms-appName']
            , AppId = customdims.['ms-appId']
            , FeedbackFrom = customdims.UserEmail
            , Screen = customdims.Screen
            , FeedbackValue = customdims.FeedbackValue
        | order by timestamp desc
    ```

    ![Расширение запроса customDimensions](./media/application-insights/custom-dimensions-extend-query.png)

    > [!TIP]
    > *Запросы журналов* являются чрезвычайно мощными. Их можно использовать для объединения нескольких таблиц, объединения больших объемов данных и выполнения сложных операций. Дополнительные сведения см. в статье [запросы журналов](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview).

## <a name="export-data-to-power-bi"></a>Экспорт данных в Power BI

Вы можете экспортировать данные Application Insights и результаты запросов в Power BI для анализа и представления данных.

1. Войдите в [портал Azure](https://portal.azure.com/) и откройте созданный [ранее](#create-an-application-insights-resource)ресурс Application Insights.

1. Выберите **журналы** в разделе **мониторинг** в левой области навигации:

1. В окне запроса log Analytics выберите пункт раскрывающееся меню **Экспорт** .

1. Выберите параметр **Экспорт в Power BI (M Query)** . Будет загружен файл Power BI запроса на компьютер:

    ![Экспорт запроса Power BI](./media/application-insights/export-powerbi-query.png)

1. Откройте скачанный файл в текстовом редакторе и скопируйте запрос в буфер обмена.

1. Откройте Power BI.

1. На вкладке **Главная** ленты выберите пункт **получить данные** и щелкните **пустой запрос**.

    ![Power BI пустой запрос](./media/application-insights/powerbi-blank-query.png)

1. В окне запроса выберите **Расширенный редактор**. Вставьте запрос из шага 5 в окно, выберите **Готово**, а затем нажмите кнопку **Закрыть & применить**:

    ![Power BI авансового запроса](./media/application-insights/powerbi-advance-query.png)

1. Вы также можете создавать диаграммы и визуализации в Power BI для представления отзывов, полученных в приложении. И принимать решения и действия на основе данных.

    ![Диаграммы и визуализации](./media/application-insights/powerbi-feedback.png)

## <a name="default-trace-event-context-and-dimensions"></a>Контекст и измерения для событий трассировки по умолчанию

Набор измерений по умолчанию также добавляется в свойство *customDimensions* для каждого события трассировки. Эти измерения можно использовать для обнаружения сеансов приложений и приложений, в которых возникли события. Если вы зарегистрируете дополнительные пользовательские данные с помощью функции трассировки, они также будут отображаться в пользовательских измерениях.

| Имя измерения  | Соответствующий                                            |
|-----------------|-------------------------------------------------------|
| Идентификатор приложения MS-appId        | Идентификатор приложения, отправившего событие     |
| MS-appName      | Имя приложения, отправившего событие   |
| MS-Аппсессионид | Идентификатор сеанса приложения.                           |

