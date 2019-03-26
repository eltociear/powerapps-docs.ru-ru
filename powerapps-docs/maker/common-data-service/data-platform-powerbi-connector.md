---
title: Создание отчета PowerBI | Microsoft Docs
description: Подключение к вашим данным из PowerBI Desktop с помощью соединителя Common Data Service для приложений.
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: lanced
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-a-power-bi-report"></a>Создание отчета Power BI
Common Data Service для приложений позволяет подключаться напрямую с вашим данными с помощью Power BI Desktop для создания отчетов и публикации их в Power BI. Из Power BI отчеты можно использовать в панелях мониторинга, предоставлять к ним доступ другим пользователям и получать доступ с различных платформ в мобильных приложениях Power BI.

![Power BI Desktop](./media/data-platform-cds-powerbi-connector/PBIDesktop.png "Power BI Desktop")

## <a name="prerequisites"></a>Необходимые условия

Для использования Power BI с Common Data Service для приложений необходимо следующее:

* Загрузите и установите бесплатное приложение Power BI Desktop, которое выполняется на локальном компьютере. Вы можете скачать Power BI Desktop [здесь](https://powerbi.microsoft.com/desktop/).
* Среда Common Data Service для приложений с разрешениями создателя для доступа к порталу и разрешениям чтения для доступа к данным в сущностях.

## <a name="finding-your-common-data-service-for-apps-environment-url"></a>Поиск URL-адреса среды Common Data Service для приложений

1. Откройте [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) и выберите среду, к которой требуется подключиться, затем нажмите **шестеренку параметров** в правом верхнем углу и нажмите **Дополнительные настройки**

    ![Среда CDS для приложений](./media/data-platform-cds-powerbi-connector/CDSEnv1.png "Среда CDS для приложений")

2. Щелкните **Ресурсы** в разделе ресурсов для разработчиков, чтобы открыть новую вкладку.

    ![Среда CDS для приложений](./media/data-platform-cds-powerbi-connector/CDSEnv2.png "Среда CDS для приложений")

3. Скопируйте корень URL-адреса на новой вкладке, который является уникальным URL-адресом для вашей среды. URL-адрес будет в формате **https://yourenvironmentid.crm.dynamics.com/**, не копируйте остальную часть URL-адреса. Сохраните это где-то, чтобы можно было использовать его при создании отчета PowerBI.

    > [!div class="mx-imgBorder"] 
    > ![Среда CDS для приложений](./media/data-platform-cds-powerbi-connector/CDSEnv3.png "Среда CDS для приложений")

## <a name="connecting-to-common-data-service-for-apps-from-power-bi-desktop"></a>Подключение к Common Data Service для приложений из Power BI Desktop

1. Запустите **Power BI Desktop**; если это выполняется впервые, может открыться приветственный экран, или может сразу открыться пустой холст — в любом случае щелкните **Получить данные** и выберите **Дополнительно** для открытия полного списка источников данных, доступных в Power BI Desktop.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport1.png "Power BI Desktop")

2. Щелкните **Online Services** и **Common Data Service for Apps (Beta)** в списке соединителей. Щелкните **Подключить**.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport2.png "Power BI Desktop")

3. Вставьте ваш **URL-адрес среды Common Data Service для приложений** в поле **URL-адрес сервера** и нажмите **ОК**. Если это ваш первый раз, появится предложение выполнить вход, используя те же учетные данные, что вы используете для соединения с PowerApps и Common Data Service для приложений.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport3.png "Power BI Desktop")

4. Навигатор показывает все доступные сущности для среды, сгруппированные в три папки. Разверните папку **Common Data Model**.

    * Common Data Model — это стандартные сущности, которые часто используются и доступны во всех средах как часть Common Data Model.
    * Настраиваемые сущности — это сущности, созданные вами или импортированные в среду.
    * Система — содержит все сущности в вашей среде, в том числе сущности Common Data Model и настраиваемые сущности.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport4.png "Power BI Desktop")

5. Выберите сущность **Организация**, чтобы посмотреть свои данные в правой панели, и нажмите **Загрузить**.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport5.png "Power BI Desktop")

6. Ваша сущность теперь загружена в ваш отчет, и вы можете начать формировать отчеты или повторить это действия для добавления других сущностей.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport6.png "Power BI Desktop")

7. Щелкните поле **Имя** на панели поля, чтобы добавить новую визуализацию на холст отчета. Теперь можно повторить этот процесс и изменить визуализации для построения отчета.

    ![Power BI Desktop](./media/data-platform-cds-powerbi-connector/CreateReport7.png "Power BI Desktop")


## <a name="using-option-sets"></a>Использование наборов параметров

Наборы параметров используются в сущностях для предоставления раскрывающегося списка значений пользователю в приложениях и потоках. Если используется соединитель Power BI, поля наборов параметров будут представлены как два столбца для индикации как уникального значения, так и отображаемого значения.

В качестве примера, если у вас имелся набор параметров в сущности с именем ApprovalStatus, вы увидите два поля в Power BI:

* ApprovalStatus — здесь будет отображаться уникальное целое значение для каждого элемента в наборе параметров, что удобно при применении фильтров, чтобы на них не влияли возможные будущие изменения отображаемого имени.
* ApprovalStatus_display — здесь отображается дружелюбное отображаемое имя элемента, которое наиболее часто используется при представлении параметра в электронной таблице или диаграмме.

    |ApprovalStatus|ApprovalStatus_Display|
    |---------|---------|
    1|Отправлено
    2|На проверке
    3|Утвержденная
    4|Отклонен

## <a name="navigating-relationships"></a>Навигация по отношениям

Отношения в Common Data Service для приложений требуют создания отношения в PowerBI Desktop между двумя сущностями с помощью поля GUID, которое содержит генерируемый системой уникальный идентификатор, обеспечивающий создание отношений для записей создания, в которых возможны неоднозначности или дублирование с другими полями. Можно прочитать дополнительные сведения об управлении отношениями в Power BI Desktop [здесь](https://docs.microsoft.com/power-bi/desktop-create-and-manage-relationships).

Хотя некоторые отношения могут создаваться автоматически, можно просмотреть и обеспечить создание правильных отношений при создании отчета:

* Поле подстановки в сущности будет содержать GUID записи в связанной сущности.
* Связанная сущность будет иметь поле в формате "[EntityName]id", которое содержит GUID, например Accountid или MyCustomEntityid
* С помощью функции управления отношениями PowerBI Desktop можно создать новое отношение между полем подстановки и полем идентификатора в связанной сущности.


## <a name="next-steps"></a>Дальнейшие действия
* [Управление полями в сущности](data-platform-manage-fields.md)
* [Определение отношений между сущностями](data-platform-entity-lookup.md)


