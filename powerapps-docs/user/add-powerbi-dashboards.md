---
title: Добавление или изменение визуализаций Power BI на панели мониторинга | MicrosoftDocs
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
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75203934"
---
# <a name="add-or-edit-power-bi-visualizations-on-your-dashboard"></a>Добавление или изменение визуализаций Power BI на панели мониторинга

Создавайте полнофункциональные интерактивные отчеты и визуализации в режиме реального времени с помощью [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)] панелей мониторинга и плиток, добавляемых на персональные панели мониторинга.  
  
> [!NOTE]
> Чтобы добавить [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)] визуализации в персональные панели мониторинга в приложении, управляемом моделью, необходимо:  
> 
> - Включите визуализации [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)] для своей организации в окне **параметры** > **Администрирование** > **системные параметры** > вкладке **отчеты** > **разрешить внедрение визуализации**.  
> - Иметь учетную запись [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)] и иметь доступ хотя бы к одной панели мониторинга [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)].  
> - Избегайте добавления [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)] визуализаций к системным панелям мониторинга. Он не поддерживается.
  

## <a name="create-a-personal-power-bi-dashboard"></a>Создание личной панели мониторинга Power BI
  Выполните следующие действия, чтобы добавить панель мониторинга [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)] в приложение, управляемое моделью. Если вы подключаетесь к службе [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)], вам потребуется учетная запись и выбранный экземпляр Common Data Service в качестве источника данных. Дополнительные сведения о регистрации и подключении источников данных см. в разделе [Microsoft Power BI](https://powerbi.microsoft.com/).  

1. Откройте приложение и перейдите на **панели мониторинга**.
  
2. Щелкните **создать** , а затем выберите **Power BI панель мониторинга**.  

   
    > [!div class="mx-imgBorder"] 
    > ![Добавить новую панель мониторинга Power BI](media/pbi_1.png "Добавить новую панель мониторинга Power BI") 

3. В диалоговом окне **Свойства панели мониторинга Power BI** выберите рабочую область, а затем выберите панель мониторинга [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)], которую необходимо внедрить на панель мониторинга. Выберите **включить для мобильных устройств** , если вы хотите сделать панель мониторинга доступной для [!INCLUDE[pn_moca_full](../includes/pn-moca-full.md)] и [!INCLUDE[pn_Microsoft_Dynamics_CRM_Mobile](../includes/pn-dyn-365-phones.md)].

    
    > [!div class="mx-imgBorder"] 
    > ![Добавление плитки Power BI на личную панель мониторинга](media/workspace-add-power-bi-dashboard.png "Добавление плитки Power BI на личную панель мониторинга") 

4. Нажмите кнопку **сохранить** , чтобы сохранить панель мониторинга.
 
## <a name="embed--power-bi-tiles-on-your-personal-dashboard"></a>Внедрение Power BI плиток на личной панели мониторинга  
 Выполните следующие действия, чтобы добавить один или несколько плиток [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)] на личную панель мониторинга. Если вы подключаетесь к службе [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)], вам потребуется учетная запись и выбранный экземпляр Common Data Service в качестве источника данных. Дополнительные сведения о регистрации и подключении источников данных см. в разделе [Microsoft Power BI](https://powerbi.microsoft.com/).  
  
1. Откройте приложение и перейдите на **панели мониторинга**. 
  
2. Выберите существующую личную панель мониторинга или щелкните **создать** , чтобы создать ее.  
  
3. На панели мониторинга выберите область, в которой должна отображаться плитка, а затем выберите **Power BI плитку** на панели инструментов.  

   > [!div class="mx-imgBorder"] 
   > ![Добавить новую плитку Power BI](media/pbi_2.png "Добавить новую плитку Power BI") 
  
4. В диалоговом окне **Power BI плитке** выберите рабочую область и щелкните плитку [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)], которую требуется отобразить на панели мониторинга. Выберите **включить для мобильных устройств** , если хотите сделать плитку доступной для [!INCLUDE[pn_moca_full](../includes/pn-moca-full.md)] и [!INCLUDE[pn_Microsoft_Dynamics_CRM_Mobile](../includes/pn-dyn-365-phones.md)].  
  
     Выберите другую область панели мониторинга и повторите этот шаг, чтобы добавить еще одну плитку [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)] или другой компонент, например диаграмму или список, на панель мониторинга.  
  
5. Нажмите кнопку **сохранить** , чтобы сохранить панель мониторинга.  
  
  
### <a name="things-you-can-do-with-power-bi-embedded-tiles-in-personal-dashboards"></a>Действия, которые можно выполнить с помощью Power BI внедренных плиток на персональных панелях мониторинга 

Чтобы показать функции, доступные с помощью визуализации [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)], наведите указатель мыши на верхний правый элемент визуализации, чтобы увидеть следующие возможности.  
  
   > [!div class="mx-imgBorder"] 
   >![Внедрение Power BI мозаичных элементов](media/embed-powerbi-tile-features.png "Внедрение Power BI мозаичных элементов")  
  
1. Нажмите кнопку **Обновить** кнопка ![Обновить, чтобы обновить](media/embed-pbi-tile-refresh-button.png "Кнопка "Обновить"") базовые данные отчета плитки.  
  
2. Нажмите кнопку **Открыть в Power BI** ![Открыть в Power BI](media/open-in-power-bi.png "Кнопка "открыть в Power BI"") , чтобы открыть панель мониторинга [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)], содержащую визуализацию, на новой вкладке браузера.  
  
3. Нажмите кнопку **увеличить** рядом с элементом увеличить ![плитку](media/embed-pbi-tile-enlarge-button.png "Увеличить плитку") , чтобы развернуть визуализацию и увеличить область просмотра для визуализации, например плитку конвейера продаж, показанную здесь.  
  
    > [!div class="mx-imgBorder"] 
    >![Увеличенная плитка внедренного Power BI](media/embed-power-bi-tile-features.png "Увеличенная плитка внедренного Power BI")  
  
 
## <a name="share-a-personal-dashboard-that-contains-power-bi-visualizations"></a>Предоставление общего доступа к личной панели мониторинга, содержащей визуализации Power BI  
 Чтобы предоставить общий доступ к личной панели мониторинга, содержащей [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)] визуализации, необходимо настроить совместное использование в Common Data Service и [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)], а у пользователя или группы должны быть одинаковые учетные данные и соответствующий уровень доступа в обеих службах. Чтобы поделиться личной панелью мониторинга в приложении, перейдите на **панель мониторинга**. В списке панелей мониторинга выберите нужную личную панель мониторинга, а затем выберите **общий доступ к панели мониторинга**. Дополнительные сведения о совместном использовании панели мониторинга в [!INCLUDE[pn_power_bi_for_office_365_short](../includes/pn-power-bi-for-office-365-short.md)]см. в разделе [Power BI: предоставление общего доступа к панели мониторинга коллегам и другим пользователям](https://powerbi.microsoft.com/documentation/powerbi-service-share-unshare-dashboard/).  
  
<a name="privacy"></a>   
## <a name="privacy-notice"></a>Уведомление о конфиденциальности  
[!INCLUDE[cc_privacy_powerbi_tiles_dashboards](../includes/cc-privacy-powerbi-tiles-dashboards.md)]
  

