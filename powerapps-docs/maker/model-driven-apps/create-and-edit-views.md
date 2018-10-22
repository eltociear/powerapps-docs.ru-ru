---
title: Создание или изменение представления управляемого моделью приложения в PowerApps | MicrosoftDocs
description: 'Узнайте, как создать или изменить представление'
ms.custom: ''
ms.date: 06/11/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: bd1d393d-16ea-40ac-8136-26643c37dd2a
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-or-edit-a-model-driven-app-view"></a>Создание или изменение представления управляемого моделью приложения

<a name="BKMK_CreatingAndEditingViews"></a>   

 В этом разделе вы создадите новое настраиваемое общее представление. Вы также измените существующее представление.  
  
### <a name="create-a-new-view"></a>Создать новое представление  
  
1.  На сайте [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) выберите **Управляемые моделью** (в левой нижней части панели навигации).  

    ![Режим разработки, управляемый моделью](media/model-driven-switch.png)

    > [!IMPORTANT]
    > Если режим разработки **Управляемые моделью** недоступен, может потребоваться [создать среду](https://docs.microsoft.com/powerapps/administrator/create-environment). 

2.  Разверните **Данные**, выберите **Сущности**, выберите сущность **Организация** и перейдите на вкладку **Представления**. 

3.  На панели инструментов выберите **Добавить представление**.  

4.  В диалоговом окне **Просмотреть свойства** введите **Имя**, например **Организации с 25 или более сотрудниками**, при необходимости введите **Описание** для представления и нажмите кнопку **OK**.

    > [!div class="mx-imgBorder"] 
    > ![Просмотреть свойства](media/view-properties.png)
  
5.  На правой панели "Общие задачи" выберите **Добавить столбцы**, в диалоговом окне выберите **Добавить столбцы** выберите **Количество сотрудников** и нажмите кнопку **OK**.  

    > [!div class="mx-imgBorder"] 
    > ![Столбец "Количество сотрудников"](media/column-no-employees.png)
  
6. На правой панели "Общие задачи" выберите **Изменить условия фильтра**, в диалоговом окне "Изменить условия фильтра" выберите **Количество сотрудников**, выберите **Больше или равно** и введите **25**.  

    > [!div class="mx-imgBorder"] 
    > ![Изменение условий фильтра](media/edit-filter-criteria.png)

7.  Нажмите кнопку **OK**, чтобы закрыть диалоговое окно **Изменить условия фильтра**, затем нажмите **Сохранить и закрыть** в редакторе представлений.  
  
8.  Обратите внимание, что теперь представление доступно на вкладке **Представления** на сайте PowerApps, и его можно добавлять в приложение.
  
### <a name="edit-a-view"></a>Изменение представления  
  
1.  На вкладке **Представления** на сайте PowerApps выберите представление **Количество сотрудников**.
  
2.  Измените **Имя** представления на **Количество сотрудников с 25 или более сотрудниками в Аризоне** и нажмите кнопку **OK**.  

3.  На правой панели "Общие задачи" выберите **Добавить столбцы**, в диалоговом окне выберите **Добавить столбцы** выберите **Адрес 1: город** и нажмите кнопку **OK**.  

4. На правой панели "Общие задачи" выберите **Изменить условия фильтра** и в диалоговом окне "Изменить условия фильтра" добавьте второе предложение фильтра. Выберите **Адрес 2: область, республика, край, округ**, выберите **Равно** и введите **Аризона**. 

    > [!div class="mx-imgBorder"] 
    > ![Адрес 2: область, республика, край, округ](media/column-address-2-state.png)

5. Нажмите кнопку **OK**, чтобы закрыть диалоговое окно **Изменить условия фильтра**, затем нажмите **Сохранить и закрыть** в редакторе представлений.  
  

## <a name="create-a-new-view-from-an-existing-view"></a>Создание нового представления из существующего представления  
 Следуйте указаниям, чтобы изменить представление, но вместо выбора кнопки **Сохранить и закрыть** выберите **Сохранить как** и введите новые значения в полях **Имя** и **Описание** представления.  
 
### <a name="next-steps"></a>Дальнейшие действия
[Выбор и настройка столбцов](choose-and-configure-columns.md)  
  
[Изменение условий фильтра](edit-filter-criteria.md)  
  
[Настройка сортировки](configure-sorting.md)  