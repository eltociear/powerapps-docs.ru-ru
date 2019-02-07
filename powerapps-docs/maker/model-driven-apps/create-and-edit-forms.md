---
title: 'Создание и изменение форм с помощью конструктора форм, управляемых моделью | MicrosoftDocs'
ms.custom: ''
ms.date: 12/13/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
  - PowerApps maker portal impact
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="create-and-edit-forms-using-the-form-designer"></a>Создание и изменение форм с помощью конструктора форм 
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Используйте новый конструктор форм для создания и разработки форм для управляемых моделью приложений.

> [!IMPORTANT]
> Новый конструктор управляемых моделью форм в настоящее время поддерживает только создание и редактирование основных форм. Дополнительные сведения: [Типы форм](types-forms.md)

## <a name="create-a-form"></a>Создание формы 
1. Выполните вход в [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). 
2. В левой области навигации разверните **Данные**, затем выберите **Сущности**. 
3. Выберите сущность, например сущность организации, затем выберите вкладку **Формы**. 
4. Выберите **Добавить форму**, затем выберите **Основная форма (предварительный просмотр)**.     
    Содержимое новой формы заполняется с использованием существующего определения основной формы. Если существуют несколько основных форм, форма в верхней части списка в порядке форм используется для заполнения новой формы. 
5. Выберите **Сохранить** для сохранения формы, или выберите **Опубликовать**, если требуется сохранить изменения и сделать их видимыми пользователям приложения.  

## <a name="edit-a-form"></a>Редактирование формы 
1. Выполните вход в [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). 
2. В левой области навигации разверните и выберите **Данные**, затем выберите **Сущности**. 
3. Выберите сущность, например сущность организации, затем выберите вкладку **Формы**.
4. Выберите форму, которую нужно изменить, затем выберите **Изменить форму (предварительный просмотр)**.  
   Можно также выбрать значок **...** рядом с требуемой формой, затем выбрать **Изменить форму (предварительный просмотр)**. 
5. Выберите **Сохранить** для сохранения формы, или выберите **Опубликовать**, если требуется сохранить изменения и сделать их видимыми пользователям приложения. 

## <a name="add-and-remove-fields"></a>Добавление и удаление полей 
Для добавления поля в форму или удаления полей из нее используйте область полей. Область полей позволяет осуществлять поиск и фильтрацию, чтобы можно было быстро находить нужные поля. Она также включает параметр для отображения только неиспользуемых полей. 

### <a name="add-a-field"></a>Добавление поля
1. Откройте конструктор форм для создания или редактирования формы. Дополнительные сведения: [Создание формы](#create-a-form) и [Редактирование формы](#edit-a-form)
2. В режиме предварительного просмотра формы выберите другое существующее поле или раздел. 
    - При выборе существующего поля новое поле добавляется под существующим полем. 
    - При выборе раздела новое поле добавляется в доступное пространство, чтобы равномерно распределить поля по столбцам. 
3. Выберите **Добавить поле** или в левой панели выберите **Поля**.  
   Панель полей по умолчанию открывается при открытии конструктора форм. 
4. На панели **Поля** с помощью поиска, фильтрации или прокрутки можно найти поле, которое требуется добавить. 
   Если не удается найти поле, оно может уже находиться в форме. Снимите флажок **Показывать только неиспользуемые поля** для просмотра всех полей, включая уже добавленные в форму. 
5. В области **Поля** выберите поле для добавления в форму. <br />
   Можно также выбрать **...** рядом с требуемым полем, затем выберите **Добавить в выбранный раздел**. 
6. Выберите **Сохранить** для сохранения формы или выберите **Опубликовать**, если требуется сохранить изменения и сделать их видимыми конечным пользователям. 

### <a name="remove-a-field"></a>Удаление поля
1. Откройте конструктор форм для создания или редактирования формы. Дополнительные сведения: [Создание формы](#create-a-form) и [Редактирование формы](#edit-a-form)
2. В режиме предварительного просмотра формы выберите поле, которое нужно удалить из формы. 
3. Выберите **Удалить**. <br />
4. Нажмите кнопку **Сохранить**. 

    > [!NOTE]
    >   -  Если поле удалено по ошибке, выберите **Отменить** для отмены действия. 
    >   -  Нельзя удалить обязательное или заблокированное поле. 

## <a name="add-and-remove-tabs-and-sections"></a>Добавление и удаление вкладок и разделов 
Для добавления или удаления вкладки или раздела в форме воспользуйтесь панелью планировок. 

### <a name="add-a-tab"></a>Добавление вкладки
1. Откройте конструктор форм для создания или редактирования формы. Дополнительные сведения: [Создание формы](#create-a-form) и [Редактирование формы](#edit-a-form) 
2. В режиме предварительного просмотра формы выберите другую существующую вкладку или форму. 
    - Если вы выберите существующую вкладку, новая вкладка будет добавлена справа от существующей вкладки. 
    - Если вы выберите форму, новая вкладка будет добавлена как самая правая вкладка формы. 
3. Выберите **Добавить элемент управления** или в левой панели выберите **Планировки**.  
4. В области **Планировки** выберите элемент управления вкладок, например **Вкладка из 2 столбцов**, чтобы добавить его в форму. <br />
   Можно также выбрать **...** рядом с элементом управления вкладки, затем выбрать **Добавить в форму**.  
5. Нажмите кнопку **Сохранить**. 


### <a name="remove-a-tab"></a>Удаление вкладки
1. Откройте конструктор форм для создания или редактирования формы. Дополнительные сведения: [Создание формы](#create-a-form) и [Редактирование формы](#edit-a-form)
2. В предварительном просмотре формы выберите вкладку, которую необходимо удалить, затем выберите **Удалить**. 
3. Нажмите кнопку **Сохранить**. 
    > [!NOTE]
    >    - Если вкладка удалена по ошибке, выберите **Отменить** для отмены действия удаления. 
    >     - Форма должна содержать по крайней мере одну вкладку. Нельзя удалить вкладку, если это единственная вкладка формы. 
    >    - Невозможно удалить вкладку с заблокированными разделами. 
    >    - Невозможно удалить вкладку с разделами, содержащими обязательные или заблокированные поля. 

### <a name="add-a-section"></a>Добавление раздела 
1. Откройте конструктор форм для создания или редактирования формы. Дополнительные сведения: [Создание формы](#create-a-form) и [Редактирование формы](#edit-a-form)
2. В режиме предварительного просмотра формы выберите другой раздел или вкладку. 
    - Если выбран существующий раздел, новый раздел будет добавлен под существующим разделом. 
    - Если выбрана вкладка, новый раздел будет добавлен в нижней части первого столбца вкладки. 
3. Выберите **Добавить элемент управления** или в левой панели выберите **Планировки**.
4. В области **Планировки** выберите элемент управления раздела для добавления в форму. <br />
   Можно также выбрать **...** рядом с требуемым элементом управления раздела, затем выберите **Добавить в выбранную вкладку**.      
5. Нажмите кнопку **Сохранить**. 
 

### <a name="delete-a-section"></a>Удаление раздела 
1. Откройте конструктор форм для создания или редактирования формы. Дополнительные сведения: [Создание формы](#create-a-form) и [Редактирование формы](#edit-a-form) 
2. В предварительном просмотре формы выберите раздел, который необходимо удалить, затем выберите **Удалить**.  
3. Нажмите кнопку **Сохранить**. 
    > [!NOTE]
    >    - Если раздел удален по ошибке, выберите **Отменить** для отмены действия удаления. 
    >    - Вкладка должна иметь минимум один раздел в каждом столбце.  
    >    - Нельзя удалить раздел, если он единственный в столбце вкладки. 
    >    - Невозможно удалить заблокированный раздел. 
    >    - Невозможно удалить раздел, содержащий обязательные или заблокированные поля. 
 
## <a name="use-the-tree-view"></a>Использование представления дерева 
В области представления в виде дерева отображается визуальная иерархия элементов управления и полей в форме. Значки в представлении в виде дерева помогают быстро определить тип поля или элемента управления. 

Можно также использовать представление в виде дерева для выбора полей и элементов управления в форме. Представление в виде дерева полезно, когда требуется выбрать скрытые элементы, которые, соответственно, не видны в представлении предварительного просмотра формы. 

Можно развернуть или свернуть узлы в представлении в виде дерева, чтобы просмотреть или скрыть элементы внутри узла. Когда пользователь выбирает элемент в представлении в виде дерева, оно выделяется в представлении предварительного просмотра формы, а на панели свойств отображаются свойства этого элемента. 

   ![Представление в виде дерева](media/tree-view.png)

### <a name="open-the-tree-view"></a>Открытие представления в виде дерева 
1. Откройте конструктор форм для создания или редактирования формы. Дополнительные сведения: [Создание формы](#create-a-form) и [Редактирование формы](#edit-a-form)  
2. В левой панели выберите **Представление в виде дерева**.

## <a name="see-also"></a>См. также
[Обзор конструктора управляемых моделью форм](form-designer-overview.md) <br />
[Создание и изменение полей](../common-data-service/create-edit-field-portal.md)