---
title: Добавление или изменение визуализаций Power BI на панели мониторинга | Документация Майкрософт
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/15/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c386e53569b942cbc539438f9cf30cabab15bb65
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75203934"
---
# <a name="add-or-edit-power-bi-visualizations-on-your-dashboard"></a>Добавление или изменение визуализаций Power BI на панели мониторинга

Создавайте полнофункциональные интерактивные отчеты и визуализации в режиме реального времени с помощью панелей мониторинга [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)] и элементов, добавляемых на персональные панели мониторинга.  
  
> [!NOTE]
> Чтобы добавить визуализации [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)] в персональные панели мониторинга в приложении на основе модели, выполните следующие действия.  
> 
> - Включите визуализации [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)] для вашей организации на вкладке **Параметры** > **Администрирование** > **Параметры системы** > **Создания отчетов** > **Разрешить внедрение визуализаций Power BI**.  
> - Вам понадобится учетная запись [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)] и доступ хотя бы к одной панели мониторинга [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)].  
> - Избегайте добавления визуализаций [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)] к системным панелям мониторинга. Они не поддерживаются.
  

## <a name="create-a-personal-power-bi-dashboard"></a>Создание персональной панели мониторинга Power BI
  Выполните следующие действия, чтобы добавить панель мониторинга [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)] в приложение на основе модели. Если вы подключаетесь к службе [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)], вам потребуется учетная запись и выбранный экземпляр Common Data Service в качестве источника данных. Дополнительные сведения о регистрации и подключении источников данных см. в разделе [Microsoft Power BI](https://powerbi.microsoft.com/).  

1. Откройте приложение и перейдите в раздел **Панели мониторинга**.
  
2. Выберите **Создать**, а затем выберите **Панель мониторинга Power BI**.  

   
    > [!div class="mx-imgBorder"] 
    > ![Добавление новой панели мониторинга Power BI](media/pbi_1.png "Добавление новой панели мониторинга Power BI") 

3. В диалоговом окне **Свойства панели мониторинга Power BI** выберите рабочую область, а затем выберите панель мониторинга [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)], которую необходимо внедрить на панель мониторинга. Выберите **Включить для мобильных устройств**, если вы хотите сделать панель мониторинга доступной для [!INCLUDE[pn_moca_full](../includes/pn-moca-full.md)] и [!INCLUDE[pn_Microsoft_Dynamics_CRM_Mobile](../includes/pn-dyn-365-phones.md)].

    
    > [!div class="mx-imgBorder"] 
    > ![Добавление элемента Power BI на личную панель мониторинга](media/workspace-add-power-bi-dashboard.png "Добавление элемента Power BI на личную панель мониторинга") 

4. Выберите **Сохранить**, чтобы сохранить панель мониторинга.
 
## <a name="embed--power-bi-tiles-on-your-personal-dashboard"></a>Внедрение элементов Power BI в личную панель мониторинга  
 Выполните следующие действия, чтобы добавить один или несколько элементов [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)] на личную панель мониторинга. Если вы подключаетесь к службе [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)], вам потребуется учетная запись и выбранный экземпляр Common Data Service в качестве источника данных. Дополнительные сведения о регистрации и подключении источников данных см. в разделе [Microsoft Power BI](https://powerbi.microsoft.com/).  
  
1. Откройте приложение и перейдите в раздел **Панели мониторинга**. 
  
2. Выберите существующую личную панель мониторинга или выберите **Создать**, чтобы создать ее.  
  
3. На панели мониторинга выберите область, в которой должен отображаться элемент, а затем на панели инструментов выберите **Элемент Power BI**.  

   > [!div class="mx-imgBorder"] 
   > ![Добавление нового элемента Power BI](media/pbi_2.png "Добавление нового элемента Power BI") 
  
4. В диалоговом окне **Элемент Power BI** выберите рабочую область, а затем выберите элемент [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)], который необходимо отображать на панели мониторинга. Выберите **Включить для мобильных устройств**, если вы хотите сделать элемент доступным для [!INCLUDE[pn_moca_full](../includes/pn-moca-full.md)] и [!INCLUDE[pn_Microsoft_Dynamics_CRM_Mobile](../includes/pn-dyn-365-phones.md)].  
  
     Выберите другую область панели мониторинга и повторите этот шаг, чтобы добавить еще один элемент [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)] или другой компонент, например диаграмму или список, на панель мониторинга.  
  
5. Выберите **Сохранить**, чтобы сохранить панель мониторинга.  
  
  
### <a name="things-you-can-do-with-power-bi-embedded-tiles-in-personal-dashboards"></a>Действия, которые можно выполнить с помощью внедренных элементов Power BI на личных панелях мониторинга 

Чтобы показать функции, доступные с помощью визуализации [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)], наведите указатель мыши на правый верхний угол визуализации, чтобы открыть следующие возможности.  
  
   > [!div class="mx-imgBorder"] 
   >![Функции внедрения элементов Power BI](media/embed-powerbi-tile-features.png "Функции внедрения элементов Power BI")  
  
1. Нажмите кнопку **Обновить** ![кнопка "Обновить"](media/embed-pbi-tile-refresh-button.png "Кнопка "Обновить""), чтобы обновить базовые данные отчета элемента.  
  
2. Нажмите кнопку **Открыть в Power BI** ![кнопка "Открыть в Power BI"](media/open-in-power-bi.png "Кнопка "Открыть в Power BI""), чтобы открыть панель мониторинга [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)], содержащую визуализацию, на новой вкладке браузера.  
  
3. Нажмите кнопку **Увеличить** ![Увеличить элемент](media/embed-pbi-tile-enlarge-button.png "Увеличить элемент"), чтобы развернуть визуализацию и увеличить область просмотра для визуализации, например элемент конвейера продаж, показанный здесь.  
  
    > [!div class="mx-imgBorder"] 
    >![Увеличенный внедренный элемент Power BI](media/embed-power-bi-tile-features.png "Увеличенный внедренный элемент Power BI")  
  
 
## <a name="share-a-personal-dashboard-that-contains-power-bi-visualizations"></a>Предоставление общего доступа к личной панели мониторинга, содержащей визуализации Power BI  
 Чтобы предоставить общий доступ к личной панели мониторинга, содержащей визуализации [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)], необходимо настроить совместное использование в Common Data Service и [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)], а у пользователя или группы должны быть одинаковые учетные данные и соответствующий уровень доступа в обеих службах. Чтобы предоставить общий доступ к личной панели мониторинга в приложении, перейдите в раздел **Панели мониторинга**. В списке панелей мониторинга выберите нужную личную панель мониторинга, а затем выберите **ОБЩИЙ ДОСТУП К ПАНЕЛИ МОНИТОРИНГА**. Дополнительные сведения о совместном использовании панели мониторинга в [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)] см. в разделе [Power BI. Предоставление общего доступа к панели мониторинга коллегам и другим пользователям](https://powerbi.microsoft.com/documentation/powerbi-service-share-unshare-dashboard/).  
  
<a name="privacy"></a>   
## <a name="privacy-notice"></a>Уведомление о конфиденциальности  
[!INCLUDE[cc_privacy_powerbi_tiles_dashboards](../includes/cc-privacy-powerbi-tiles-dashboards.md)]
  

