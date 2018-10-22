---
title: Изменение цветовой схемы или добавление логотипа в соответствии с брендом организации | MicrosoftDocs
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
author: Mattp123
ms.assetid: 21a166a0-d25e-4260-a1e4-2ddc528787c2
caps.latest.revision: 17
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-a-theme"></a>Создание темы

Можно создать пользовательское оформление (тему) приложения, внеся изменения в цвета и визуальные элементы по умолчанию, предоставленные в ненастроенной системе. Например, можно брендировать приложение, добавив логотип компании и настроив цвета для каждой сущности. Тема создается с помощью средств настройки в пользовательском интерфейсе без написания кода разработчиком. Вы можете создавать, изменять и удалять используемые в вашей организации темы. Настройка тем поддерживается в веб-формах в Dynamics 365 for Outlook. Можно определить несколько тем, но только одну из них можно настроить и опубликовать как тему по умолчанию.  
  
<a name="UseThemes"></a>   
## <a name="use-themes-to-enhance-the-user-interface-and-create-your-product-branding"></a>Использование тем для повышения наглядности пользовательского интерфейса и брендирования приложения  
 Темы используются для повышения наглядности пользовательского интерфейса приложения, но не позволяют изменять его никаким радикальным образом. Цвета темы применяются глобально, во всех компонентах приложения. Например, можно изменить следующие визуальные элементы в пользовательском интерфейсе:  
  
-   изменить логотипы продуктов и цвета элементов навигации для брендирования приложения;  
  
-   откорректировать контрастные цвета, такие как цвета при наведении или выборе;  
  
-   настроить цвета для каждой сущности.  
    
-   Логотип  
  
-   Подсказка логотипа  
  
-   Цвет панели навигации  
  
-   Цвет подпанели навигации

-   Цвет главной панели команд в едином интерфейсе
  
-   Цвет заголовка  
  
-   Цвет глобальных ссылок  
  
-   Эффект выбранных ссылок  
  
-   Эффект наведения указателя на ссылки  
  
-   Цвет элемента управления процесса  
  
-   Цвет сущности по умолчанию  
  
-   Цвет пользовательской сущности по умолчанию  
  
-   Тень элемента управления  
  
-   Рамка элемента управления  
  
<a name="Solution"></a>   
## <a name="solution-awareness"></a>Связь с решениями  
 Темы не связываются с решениями. Изменения, внесенные в тему организации, не включаются в решения, экспортируемые из организации. Данные сохраняются в сущности темы, которую можно экспортировать и импортировать в другую среду. Для вступления в силу импортированную тему нужно опубликовать.  
  
<a name="CloneAlter"></a>   
## <a name="copy-and-alter-the-existing-theme"></a>Копирование и изменение существующей темы  
 Самый простой и быстрый способ создать новую тему — клонировать и изменить существующую тему, а затем сохранить ее, просмотреть и опубликовать. 
 
1.  Выполните вход в [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

2.  Выберите **Управляемое моделью** (в левом нижнем углу). 

3.  Выберите ![Значок "Параметры"](../model-driven-apps/media/powerapps-gear.png) (справа сверху) > **Дополнительные настройки**. 

4. В разделе **Темы** выберите **Все темы**. 

5. Выберите **Тема CRM по умолчанию**. 

На следующем снимке экрана показана часть настройки темы по умолчанию.  

> [!div class="mx-imgBorder"] 
> ![Тема по умолчанию](media/default-theme.png) 
  
 Мы клонировали тему по умолчанию и изменили цвета. На следующих снимках экрана показаны новые цвета для навигации и выделения. Также можно выбрать новый логотип для продукта.  
  
 На следующем снимке экрана показан новый цвет для навигации.  
 
 > [!div class="mx-imgBorder"] 
 > ![Цвета темы Gentle green](media/theme-gentle-green.png "Цвета темы Gentle green")  
  
 На следующем снимке экрана показана сетка сущности "Организация" с новым цветом выделения.  
 
 > [!div class="mx-imgBorder"] 
 > ![Сетка организации с темой Gentle green](media/themes-gentle-green-account-grid.png "Сетка организации с темой Gentle green")  
  
<a name="Publish"></a>   
## <a name="preview-and-publish-a-theme"></a>Предварительный просмотр и публикации темы  
 Для предварительного просмотра и публикации темы следующие действия:  
  
-   Создайте новую тему с нуля или клонировать существующую.  
  
-   Просмотрите новую тему, выбрав **Предварительный просмотр** на панели команд. Для выхода из режима просмотра выберите **Закончить предварительный просмотр** на панели команд рядом с кнопкой **Предварительный просмотр**.  
  
-   Опубликуйте тему. Выберите **Опубликовать тему** на панели команд.  
  
 На следующем снимке экрана показаны кнопки на панели команд для предварительного просмотра и публикации.  
  
 ![Использование кнопок предварительного просмотра для входа в режим предварительного просмотра и выхода из него](media/themes-preview-buttons.PNG "Использование кнопок предварительного просмотра для входа в режим предварительного просмотра и выхода из него")  
  
<a name="BestPracticies"></a>   
## <a name="best-practices"></a>Лучшие методики  
 Ниже приведены рекомендации по разработке контрастных цветов темы и подбору цветов.  
  
### <a name="theme-contrast"></a>Контрасты в теме  
 Рекомендуем следующий подход к использованию контрастных цветов:  
  
-   Тщательно выбирайте контрастные цвета. В готовой теме по умолчанию Common Data Service для приложений доступны правильные соотношения контрастов, обеспечивающие оптимальное удобство использования. Используйте аналогичные соотношения в своих собственных темах.  
  
-   Для высококонтрастного режима используйте параметры цветов по умолчанию.  
  
### <a name="theme-colors"></a>Цвета в темах  
 Не рекомендуется использовать большое количество разных цветов. Хотя вы можете задать отдельный цвет для каждой сущности, рекомендуем использовать одну из следующих схем:  
  
-   Сделайте все сущности нейтральных цветов и выделите ключевые сущности.  
  
-   Используйте один и тот же цвет для схожих или связанных сущностей, таких как очередь и элемент очереди, или сущности каталога продуктов. Общее число таких групп должно быть небольшим.  
  
<a name="Considerations"></a>   
## <a name="custom-theme-considerations"></a>Соображения, связанные с пользовательскими темами  
 Если вы планируете использовать пользовательские темы, учитывайте следующие соображения:  
  
-   Большинство обновляемых областей интерфейса будут отображаться в цветах пользовательской темы.  
  
-   Несмотря на то, что цвета темы применяются глобально во всем приложении, некоторые старые области интерфейса, например градиентные кнопки, будут сохранять свои собственные предусмотренные по умолчанию цвета.  
  
-   В некоторых областях необходимо использовать темные или светлые цвета для создания контраста с цветами значков. Цвета значков не настраиваются.  
  
-   Сущность не может отображаться разными цветами в разных узлах карты сайта.  
  
-   Цвет узлов карты сайта не настраивается.  
  
## <a name="see-also"></a>См. также  
         
 [Видео: темы в Dynamics 365 Customer Engagement](http://go.microsoft.com/fwlink/p/?LinkId=529568) [Запрос и изменение темы организации](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/query-and-edit-an-organization-theme)
