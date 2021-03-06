---
title: Создание и настройка панелей мониторинга интерактивного взаимодействия приложений на основе модели в Power Apps | Документация Майкрософт
description: Узнайте, как создавать и настраивать панели мониторинга интерактивного взаимодействия в Power Apps
keywords: Интерактивные панели мониторинга; Customer Service; Microsoft Dynamics 365; Центр интерактивного обслуживания
author: Mattp123
ms.author: matp
manager: kvivek
ms.custom: ''
ms.date: 04/08/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: d1446a95-14bf-4b15-a905-72fce07f4c76
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 584aeae66230e94296b386023c00f95d07c51a13
ms.sourcegitcommit: 7d3caf698d367a56af9e16c43af8005adb9f87cd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2020
ms.locfileid: "3250072"
---
# <a name="create-and-configure-model-driven-app-interactive-experience-dashboards"></a>Создание и настройка панелей мониторинга интерактивного взаимодействия приложений на основе модели

Панели мониторинга интерактивного взаимодействия могут быть универсальной рабочей областью для пользователей приложений, например представителей по сервисному обслуживанию, для просмотра данных сведений о нагрузке и выполнения действия. Они являются полностью настраиваемыми, основаны на ролях безопасности и предоставляют данные о нагрузке по нескольким потокам в реальном времени. Пользователям интерактивной панели мониторинга не нужно проходить через страницы приложения в поисках определенной записи; они могут выполнить действие с ней непосредственно с панели мониторинга. 

 Панели мониторинга интерактивного взаимодействия бывают двух видов: многопотоковые и однопотоковые. Кроме того, многопотоковые панели мониторинга могут быть домашней страницей или панелями мониторинга конкретной сущности. Панели мониторинга конкретной сущности настраиваются в другой части пользовательского интерфейса и частично подгружаются со сведениями конфигурации конкретной сущности.  
  
 Многопотоковые панели мониторинга отображают данные в реальном времени в нескольких потоках данных. Ограничения на количество потоков, настраиваемых на панели мониторинга, нет. Данные в потоке могут быть основаны только на одной сущности, но каждый поток может быть основан на другой сущности. На панелях мониторинга конкретной сущности все потоки основаны на одной и той же сущности. Данные поступают из различных представлений или очередей, например **Мои действия**, **Мои обращения** или **Обращения в очереди банка**. 
 
> [!NOTE]
> В описанных здесь примерах используется сущность обращения, которая доступна в приложении Dynamics 365 Customer Service.
  
 Однопотоковые панели мониторинга отображают данные в реальном времени в одном потоке, основанном на представлении сущности или очереди. Плитки находятся с правой стороны панелей мониторинга и всегда отображаются. Однопотоковые панели мониторинга обычно полезны для руководителей или менеджеров облуживания уровня 2, которые контролируют более редкие, но более сложные обращения или обращения с эскалацией.  
  
 Многопотоковые и однопотоковые панели мониторинга содержат интерактивные диаграммы, в которых указано количество релевантных записей, таки как обращения по приоритету или по состоянию. Эти диаграммы применяются как визуальные фильтры. Визуальные фильтры (интерактивные диаграммы) основаны на нескольких сущностях и на однопотоковых панелях мониторинга сущность в потоке данных определяет сущность визуального фильтра.   
  
 Пользователи могут применять дополнительные фильтры с глобальным фильтром и временным фильтром. Глобальный фильтр работает на уровне полей на всех диаграммах, а также в потоках и на плитках, которые основаны на сущности фильтра (сущность фильтра указывается при настройке визуальных фильтров). 
  
> [!NOTE]
>  Интерактивные панели мониторинга зависят от решения и могут экспортироваться, а затем импортироваться в другую среду как решение. Однако очереди, на которых основаны потоки и плитки, не зависят от решения. Перед импортом решения панели мониторинга в целевую систему, очереди необходимо вручную создать в целевой системе в разделе **Параметры** > **Управление сервисом** > **Очереди**. После создания очередей импортируйте решение панели мониторинга в целевой системе, а затем измените потоки или плитки, которые основаны на очередях, чтобы правильно назначить заново созданные очереди.  
  
 На иллюстрациях в этом разделе показаны многопотоковые и однопотоковые панели мониторинга с панелью заголовка. Под заголовком показаны визуальные фильтры и потоки. На однопотоковой панели мониторинга также отображаются плитки. Для каждого типа панелей мониторинга можно выбирать несколько разных макетов, которые также отображаются. Заголовок панели мониторинга содержит следующие элементы управления и выбираемые значки, слева направо: средство выбора панели мониторинга, обновление, значок визуального фильтра, значок глобального фильтра и временного фильтра.  
  
### <a name="multi-stream-dashboard-standard-view"></a>Стандартное представление многопотоковой панели мониторинга  
 На многопотоковой панели мониторинга имеется ряд визуальных фильтров в верхней части и потоки данных — в нижней.  
 
![Многопотоковая интерактивная панель мониторинга](media/interactive-dashboards-multi-stream.png) 
   
### <a name="multi-stream-dashboard-tile-view"></a>Представление плиток многопотоковой панели мониторинга  
 Аналогичная панель мониторинга только представлении плиток.  
  
 ![Представление плиток многопотоковой панели мониторинга](media/interactive-dashboards-multi-stream-tiles.png "Представление плиток многопотоковой панели мониторинга")  
  
### <a name="multi-stream-dashboard-layouts"></a>Макеты многопотоковых панелей мониторинга  
 Для многопотоковых панелей мониторинга можно выбрать различные макеты.  

 > [!div class="mx-imgBorder"] 
 > ![Макеты многопотоковых панелей мониторинга](media/interactive-dashboards-multi-stream-layout.png "Макеты многопотоковых панелей мониторинга")  
  
### <a name="multi-stream-entity-specific-dashboard"></a>Многопотоковая панель мониторинга конкретной сущности  
 Здесь показана панель мониторинга конкретный сущности для сущности обращения.  
  
 ![Панель мониторинга открытых обращений](media/interactive-dashboard-cases-entity-specific.png "Панель мониторинга открытых обращений")  
  
### <a name="single-stream-dashboard"></a>Однопотоковая панель мониторинга  
 Однопотоковая панель мониторинга содержит поток данных слева и визуальные фильтры и плитки справа.  
  
 ![Панель мониторинга интерактивного центра обслуживания с одним потоком](media/interactive-dashboards-single-stream.png "Панель мониторинга интерактивного центра обслуживания с одним потоком")  
  
### <a name="single-stream-dashboard-layouts"></a>Макеты однопотоковых панелей мониторинга  
 Для однопотоковых панелей мониторинга можно выбрать различные макеты.  
 
 > [!div class="mx-imgBorder"] 
 > ![Макеты однопотоковых панелей мониторинга.](media/interactive-dashboards-single-stream-layout.png "Макеты однопотоковых панелей мониторинга.")  
  
<a name="BKMK_Enable"></a>   
## <a name="configure-filter-fields-and-security-roles-for-the-interactive-dashboards"></a>Настройка полей фильтра и ролей безопасности для интерактивных панелей мониторинга  
 При настройке интерактивных панелей мониторинга сначала следует включить поля фильтра и роли безопасности, чтобы можно было настроить для них панели мониторинга. Обратите внимание, этот интерактивные панели мониторинга доступны для всех сущностей и настраиваемых сущностей по умолчанию. 
  
### <a name="configure-filter-fields"></a>Настройка полей фильтра  
 Чтобы поле появилось в глобальном фильтре и было включено в сортировку потока данных, следует установить два флага:

- Присутствует в глобальном фильтре при интерактивном взаимодействии
- Поддерживает сортировку на панели мониторинга интерактивного взаимодействия

В этом примере доступны два параметра интерактивной панели мониторинга в сущности "Обращение" для поля **IsEscalated**.  

 > [!div class="mx-imgBorder"] 
 > ![Включить поле для глобального фильтра и сортировки](media/enable-filter-sort.png "Включить поле для глобального фильтра и сортировки")  
  
### <a name="configure-the-appears-in-global-filter-in-interactive-experience-option"></a>Настройка параметра "Присутствует в глобальном фильтре при интерактивном взаимодействии"

1.  Выполните вход в [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). 
2.  Выберите **Решения**, откройте нужное решение, а затем на панели инструментов выберите **Перейти в классический режим**. 
3. В разделе **Компоненты** раскройте узел **Сущности**, затем раскройте требуемую сущность.
4. На панели навигации выберите **Поля** и в таблице дважды щелкните поле, которое следует включить.
5. На вкладке **Общие** установите флажок **Присутствует в глобальном фильтре при интерактивном взаимодействии**. Выберите **Сохранить и закрыть**.
6. Выберите **Опубликовать все настройки**, чтобы изменения вступили в силу.
  
 Поля, включенные для параметра **Присутствует в глобальном фильтре при интерактивном взаимодействии**, отображаются в всплывающем меню глобального фильтра, если значок глобального фильтра нажат в заголовке панели мониторинга. В окне всплывающего меню представитель обслуживания может выбрать поля, на основе которых должна осуществляться глобальная фильтрация, в диаграммах, а также в потоках и на плитках, основанных на сущности фильтра.   
  
 Здесь показано окно всплывающего меню глобального фильтра:  
  
 ![Добавить два поля глобального фильтра](media/global-filter-escalated.png "Поля глобального фильтра")  
  
> [!TIP]
>  При настройке визуального фильтра, основанного на таких полях, как состояние или приоритет, рекомендуется также включить отображение этих полей (приоритет, состояние) в глобальном фильтре.  
  
### <a name="configure-the-sortable-in-interactive-experience-dashboard-option"></a>Настройка параметра "Поддерживает сортировку на панели мониторинга интерактивного взаимодействия"
  
1.  Выполните вход в [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). 
2.  Выберите **Решения**, откройте нужное решение, а затем на панели инструментов выберите **Перейти в классический режим**. 
3. В разделе **Компоненты** раскройте узел **Сущности**, затем раскройте требуемую сущность.
4. На панели навигации выберите **Поля** и в таблице дважды щелкните поле, которое следует включить.
5. На вкладке **Общие** установите флажок **Поддерживает сортировку на панели интерактивного взаимодействия**. Выберите **Сохранить и закрыть**.
6. Выберите **Опубликовать все настройки**, чтобы изменения вступили в силу.
  
Поля, настроенные для сортировки, отображаются в заголовке потока раскрывающегося списка. 

На следующем рисунке показано диалоговое окно всплывающего меню со списком доступных полей для сортировки в раскрывающемся списке. Сортировка по умолчанию всегда задается в поле **Дата и время изменения**.  
  
 ![Раскрывающийся список "Сортировать по"](media/sort-field.png "Раскрывающийся список "Сортировать по"")    
    
### <a name="enable-security-roles"></a>Включение ролей безопасности  
 Выберите и включите роли безопасности, которые позволят просматривать интерактивные панели мониторинга.  
  
#### <a name="enable-security-roles-for-interactive-dashboards"></a>Включить роли безопасности для интерактивных панелей мониторинга

1.  Выполните вход в [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). 
  
2.  Выберите **Решения**, а затем откройте нужное решение. 

3.  Выберите нужную панель мониторинга и затем на панели инструментов выберите **Включить роли безопасности**. 
  
    > [!div class="mx-imgBorder"] 
    > ![Включение ролей безопасности](media/dashboard-enable-security-roles.png)

4.  В диалоге **Назначение ролей безопасности** выберите **Отображать только для выбранных ролей безопасности** и выберите роли, которые требуется включить. Нажмите **ОК**.  

     ![Включение ролей безопасности](media/security-roles.png "Включение ролей безопасности")    
  
5.  Выберите **Опубликовать**, чтобы изменения вступили в силу.    
  
  
<a name="BKMK_Configure"></a>   
## <a name="create-interactive-experience-dashboards"></a>Создание панелей мониторинга интерактивного взаимодействия  
Следующие разделы описывают способы создания и последующей настройки различных типов интерактивного панелей мониторинга.  
  
### <a name="configure-a-multi-stream-interactive-dashboard-using-the-4-column-layout"></a>Настройка многопотоковой интерактивной панели мониторинга с помощью макета из 4 столбцов  
 
1.  Выполните вход в [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). 
  
2.  Выберите **Решения**, откройте нужное решение, а затем на панели инструментов выберите **Перейти в классический режим**. 

3.  В левой области навигации выберите **Панели мониторинга**, на панели инструментов выберите **Создать**, а затем выберите **Панель мониторинга интерактивного взаимодействия**. 

    ![Создать панель мониторинга интерактивного взаимодействия](media/interactive-exp-dash-sol-explorer.png)
  
4.  Выберите макет шириной 2, 3 или 4 столбца.  
  
5.  При открытии формы панели мониторинга укажите сведения о фильтрации в верхней части формы, как показано ниже.  
 
    > [!div class="mx-imgBorder"] 
    > ![Добавление визуальных фильтров](media/interactive-dashboards-add-visual-filters.png "Добавление визуальных фильтров")  
  
   - **Фильтровать сущность**: визуальные фильтры и атрибуты глобального фильтра основаны на данной сущности.  
      
   - **Представление сущностей**: визуальные фильтры основаны на этом представлении.  
      
   - **Отфильтровать по:**: поле, к которому применяется временной фильтр.  
      
   - **Интервал времени**: значение временного фильтра по умолчанию для поля **Отфильтровать по:**.  
      
 После указания сведений о фильтрации начните добавлять компоненты для диаграмм и потоков данных. Для добавления компонента просто выберите на элемент в центре диаграммы или потока и при появлении диалогового окна выберите обязательные сведения из раскрывающегося списка, как показано на следующих иллюстрациях.  
  
 Добавьте кольцевую диаграмму **Обращения по приоритету**.
  
 > [!div class="mx-imgBorder"] 
 > ![Добавление компонента кольцевой диаграммы.](media/interactive-dashboards-add-chart-circle.png "Добавление компонента кольцевой диаграммы.")  
  
 Некоторые диаграммы, такие как линейчатые диаграммы или круговые диаграммы, представляют данные, хранящиеся в системе. Кольцевые диаграммы и теговые диаграммы загружаются как статические изображения и не обеспечивают предварительный просмотр фактических данных.  
  
> [!NOTE]
>  Диаграммы, настроенные для визуальных фильтров, могут использовать поля для сущности **Фильтр**, а также связанные сущности. При использовании диаграмм, основанных на полях сущности представители отдела обслуживания клиентов могут фильтровать диаграммы, используя эти связанные поля сущности. Поля, которые основаны на связанной сущности, обычно имеют следующий формат в окне конфигурации диаграмм: "имя поля (имя сущности)", например **Изменено (представитель)**. Для создания диаграммы из нескольких сущностей необходимо добавить поля связанной сущности в любое представление, а затем использовать эти поля при создании диаграмм.  
 
 > [!div class="mx-imgBorder"] 
 > ![Создание диаграмм для визуальных фильтров](media/interactive-dashboard-visual-charts-x-y-axes.PNG "Создание диаграмм для визуальных фильтров")  
  
 Далее настройте потоки. Как и при добавлении компонентов в диаграммы, выберите элемент внутри панели потока. Когда появляется диалог, выберите **Представление** или **Очередь** в зависимости от элемента, который должен использовать поток. Введите необходимые сведения, как показано на следующем рисунке.  
  
 Настройте поток для **Доступные для работы элементы**, как показано ниже:  
  
 ![Добавление потока моих активных обращений.](media/add-stream-dashboard.png "Добавление потока моих активных обращений.")  

> [!NOTE]
>  Параметр **Очередь** доступен только в диалоговом окне для сущностей с включенными очередями. Для панелей мониторинга сущности, если сущность без включенной очереди, вы не увидите параметр **Очередь** в диалоговом окне. Можно только использовать параметр **Представление** в потоке панелей мониторинга для сущностей без включенной очереди.    
 
На следующем рисунке показан пример полностью настроенной области диаграммы и панели потоков:  
 
 > [!div class="mx-imgBorder"] 
 > ![Полностью настроенная панель мониторинга](media/example-stream-visual.png "Полностью настроенная панель мониторинга")  
  
 После завершения настройки панели мониторинга сохраните ее и опубликуйте настройки, чтобы изменения вступили в силу.   
  
#### <a name="edit-or-delete-individual-streams-of-an-existing-dashboard"></a>Изменение или удаление отдельных потоков существующей панели мониторинга  
  
1. Выполните вход в [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).   
  
2. Выберите **Решения**, откройте нужное решение и затем откройте панель мониторинга интерактивного взаимодействия.  
  
3.  Выберите поток, который нужно изменить, чтобы выбрать его, затем выберите **Изменить компонент**.  
  
4.  В зависимости от того, следует ли добавить представление или очередь в поток, выберите сведения представления или очереди для потока, а затем выберите **Задать**.  
  
5.  Нажмите кнопку **Сохранить**.  
  
 Также можно удалить отдельный поток с панели мониторинга. Для этого выберите поток, а затем на панели инструментов выберите **Удалить**.  
  
### <a name="create-an-entity-specific-dashboard"></a>Создание панели мониторинга конкретной сущности  
 Панель мониторинга конкретной сущности является многопотоковой панелью мониторинга. Настройка данной панели мониторинга аналогична настройке многопотоковой панели мониторинга главной страницы, но выполняется в другом месте в пользовательском интерфейсе, также есть ряд других отличий. 

Например, вместо выбора сущности некоторые поля на панели мониторинга конкретной сущности-уже предварительно настроены для сущности, для которой создается панель мониторинга.  
  
1.  Выполните вход в [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

2.  Выберите **Данные** > **Сущности** > выберите требуемую сущность. 

3.  Выберите вкладку **Панели мониторинга**, затем на панели инструментов выберите **Добавить панель мониторинга**.  
4.  Выберите макет шириной 2, 3 или 4 столбца.    
  
5.  Когда форма панели мониторинга откроется, для пункта **Фильтровать сущность** уже задано значение с учетом сущности, для которой создается панель мониторинга. В раскрывающемся списке **Представление сущности** содержатся доступные представления сущности. Выберите представление и укажите остальные сведения на странице.  
  
 Окончание настройки очень похоже на настройку многопотоковой панели мониторинга главной страницы, описанную в предыдущем разделе.  
  
### <a name="configure-a-single-stream-dashboard"></a>Настройка однопотоковой панели мониторинга  
 Настройка однопотоковой панели мониторинга аналогична настройке многопотоковой панели мониторинга. Все действия в пользовательском интерфейсе такие же, что и для многопотоковой панели мониторинга. Можно выбрать макет, содержащий плитки или макет, не включающий плитки. Если включены плитки, они всегда отображаются на панели мониторинга. Чтобы настроить плитку, выберите значок в центре плитки. Когда откроется окно **Добавить плитку**, введите все обязательные данные. На следующей иллюстрация показан пример настройки плитки.  
  
 ![Добавление плитки к однопотоковой панели мониторинга](media/add-tile.png "Добавление плитки к однопотоковой панели мониторинга")  
  
<a name="BKMK_ConfigureColors"></a>   
## <a name="configure-dashboard-colors"></a>Настройка цветов панели мониторинга  
Для всех типов полей **Набор параметров** и **Два параметра** (например, **Тип обращения**, **IsEscalated** или **Приоритет** сущности **Обращение**) можно настроить определенный цвет, который отображается в диаграммах и потоках для конкретных значений полей. Например, самые важные обращения в интерактивных диаграммах могут отображаться красным, средней важности — синим, малой важности — зеленым. В потоках рядом с описанием рабочего элемента будет цветная тонкая вертикальная линия.  
  
> [!NOTE]
>  Цветовая кодировка недоступна для теговых диаграмм и кольцевых диаграмм. Эти диаграммы отображаются на панели мониторинга в белыми, серыми черными оттенками.  
  
1.  Откройте [обозреватель решений](advanced-navigation.md#solution-explorer).  
2.  В разделе **Компоненты** раскройте узел **Сущности**, затем раскройте требуемую сущность. Если требуемая сущность не отображается, выберите **Добавить существующий**, чтобы добавить его.  
  
3.  На панели навигации выберите **Поля**. В таблице дважды щелкните поле, для которого необходимо настроить цвет.  
  
4.  На вкладке **Общие** в области **Тип** выберите **Да**, затем выберите **Изменить**.  
  
5.  Когда появится диалоговое окно **Изменить значение в списке**, задайте новое значение в текстовом поле **Цвет**. Нажмите **ОК**.  
  
6.  Выберите **Сохранить и закрыть**.  
  
7.  Выберите **Опубликовать**, чтобы изменения вступили в силу.  
  
В следующем примере показано изменение цвета для поля **IsEscalated**. Используйте кнопку **Изменить** для открытия диалогового окна **Изменить значение в списке**:  
 
 > [!div class="mx-imgBorder"] 
 > ![Изменение цвета на панели мониторинга](media/edit-color.png "Изменение цвета на панели мониторинга")  
  
При появлении диалогового окна **Изменить значение в списке** введите шестнадцатеричный код цвета, как показанный здесь #800000:  
  
 ![Изменение цвета панели мониторинга](media/modify-color.png "Изменение цвета панели мониторинга")  

Аналогично, если перейти в поле **Приоритет** для изменения цветов параметров приоритета обращения, выберите цвет в подразделе **Параметры** вкладки **Общее**, как показано ниже:

 ![Изменение цвета панели мониторинга](media/priority-color-modify.png "Изменение цвета панели мониторинга для приоритета обращения")  
  
### <a name="see-also"></a>См. также  
 
[Создание и изменение панелей мониторинга](create-edit-dashboards.md)
 

