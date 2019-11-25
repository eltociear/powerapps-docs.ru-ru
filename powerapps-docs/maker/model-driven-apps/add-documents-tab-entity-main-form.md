---
title: Добавить вкладку документов в основную форму для сущности | Документация Майкрософт
description: Узнайте, как добавить вкладку документов в основную форму для сущности
s.custom: ''
ms.date: 09/05/2019
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: Mattp123
ms.assetid: ''
caps.latest.revision: ''
ms.author: matp
manager: kvivek
search.audienceType:
- customizer
search.app:
- D365CE
ms.openlocfilehash: d8a81b531f43f3e252f2df348b8ae95551e068d4
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "2702822"
---
# <a name="add-the-sharepoint-documents-tab-to-the-main-form-for-an-entity"></a>Добавить вкладку документов SharePoint в основную форму для сущности
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Добавление вкладки в основную форму сущности для отображения документов SharePoint помогает пользователям находить и использовать функции интеграции с SharePoint, доступные в приложении на основе моделей. 

![Вкладка файлов документа](media/document-files-tab.png)

> [!IMPORTANT]
> Чтобы использовать эту функцию, необходимо включить управление документами. Дополнительные сведения: [Управление документами с помощью SharePoint](/dynamics365/customer-engagement/admin/manage-documents-using-sharepoint)

## <a name="add-the-documents-tab-in-the-formxml"></a>Добавить вкладку документов в FormXML 
1.  Создание нового решения. Выполните вход в PowerApps и перейдите к **Решения**, выберите **Новое решение** и введите необходимые и дополнительные сведения. Дополнительные сведения: [Создание решения](../common-data-service/create-solution.md)
2. Добавьте сущности в решение, где вы хотите добавить вкладку документов в главной форме. Стандартная и все пользовательские сущности поддерживаются. Дополнительные сведения: [Добавление существующего компонента в решение](/powerapps/maker/common-data-service/use-solution-explorer#add-an-existing-component-to-a-solution)
3. Включение формы для сущности в решении, такую как основная форма для сущности учетной записи. Рядом с объектом, выберите **...**, а затем выберите **Изменить**. Выберите вкладку **Формы**. Если нужная форма отсутствует, добавьте ее.   

4. Добавление вкладки из одного столбца в основную форму. Для этого в конструкторе формы выберите область на холсте формы, выберите **1Добавить компонент**, а затем выберите **Вкладка из одного столбца**.  
   ![Вставка вкладки из одного столбца](media/insert-one-column-tab.png)

5. В конструкторе формы выберите **Новая вкладка** на холсте конструктора формы, выберите **Добавить поле** и добавьте поле, например *Адрес 1: город* в левой панели. Можно использовать любое текстовое или числовое поле для вкладки. ![Добавить поле на вкладку](media/add-field-to-tab.png)
6. Переименование подписи вкладки. Для этого выберите **Новая вкладка**, а в правой области свойств замените **Новая вкладка** на что-либо более описательное, например *Файлы*.
7. Выберите **Сохранить**, выберите **Опубликовать**, а затем закройте конструктор форм. 
8. На домашней странице разработчика PowerApps выбирайте **Решения**, выберите решение, а затем **Экспорт**, чтобы экспортировать решения как неуправляемое решение. Дополнительные сведения: [Экспорт решений](../common-data-service/import-update-export-solutions.md#export-solutions) 
9. Извлеките решение и откройте файл customization.xml в текстовом редакторе или редакторе XML. 
10. В файле customization.xml введите в поиск **описание подписи="Файлы"** (или иное имя вкладки на предыдущем шаге).
11. Прокрутите страницу вниз до элемента идентификатор элемента управления="*имя поля*", например, **идентификатор элемента управления="address1_city"** и замените весь элемент [примером XML](#xml-sample-for-adding-the-documents-tab-to-a-form) в данном разделе. 

    > [!div class="mx-imgBorder"] 
    > ![](media/form-xml.png "XML sample insertion point")

12. Внесите эти изменения в пример XML. 
    
     a. Найдите элемент **RelationshipName** и замените его именем схемы, которое отображается как *entityLogicalName*_SharePointDocument. Например, для сущности учетных записей именем схемы для отношения является Account_SharePointDocument, которое является именем схемы для примера XML в этом разделе. Чтобы найти имя для другой сущности, перейдите к **Настройки** > **Настройки** > **Настройка системы** > **Сущности** > выберите сущность > выберите **Отношения N:1**. Найдите **Связанная сущность** типа **SharePointDocument**. 

      ![Документ SharePoint об отношениях с учетной записью](media/account-sharepointdocument.png)

     b. Создайте глобальный уникальный идентификатор (guid) и замените существующий guid **uniqueid**, расположенный в элементе **управления**, который вы вставили на предыдущем шаге, сохраняя при этом фигурные скобки {}.  
       ![Уникальный идентификатор элемента управления](media/control-unique-id.png) с. Сохраните ваши изменения в customizations.xml. 
13. Откройте файл solution.xml и увеличьте значение элемента **Версия**. Например, с *1.1.0.0* на *1.2.0.0*. 
14. Упакуйте все файлы решения в сжатую (заархивированную) папку и импортируйте ее в свою среду. Если вы получили сообщение об ошибке, что необходимо удалить предыдущее решение, сделайте это. Дополнительные сведения: [Импорт, изменение и обновление решения](../common-data-service/import-update-export-solutions.md) 

## <a name="xml-sample-for-adding-the-documents-tab-to-a-form"></a>Пример XML для добавления вкладки документов в форму
```xml
  <control id="DocumentSubGrid" classid="{E7A81278-8635-4d9e-8D4D-59480B391C5B}" indicationOfSubgrid="true" uniqueid="{9cd66b5c-8b7a-6433-c5a5-46a7245dd534}"> 
    <parameters> 
      <ViewId>{0016F9F3-41CC-4276-9D11-04308D15858D}</ViewId> 
      <IsUserView>false</IsUserView>         
      <RelationshipName>Account_SharepointDocument</RelationshipName>
      <TargetEntityType>sharepointdocument</TargetEntityType> 
      <AutoExpand>Fixed</AutoExpand> 
      <EnableQuickFind>false</EnableQuickFind> 
      <EnableViewPicker>true</EnableViewPicker> 
      <ViewIds /> 
      <EnableJumpBar>false</EnableJumpBar> 
      <ChartGridMode>Grid</ChartGridMode> 
      <VisualizationId /> 
      <IsUserChart>false</IsUserChart> 
      <EnableChartPicker>false</EnableChartPicker> 
      <RecordsPerPage>10</RecordsPerPage> 
      <HeaderColorCode>#F3F3F3</HeaderColorCode> 
    </parameters> 
  </control> 
```

### <a name="see-also"></a>См. также
[Управление документами с помощью SharePoint](/dynamics365/customer-engagement/admin/manage-documents-using-sharepoint)