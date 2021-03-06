---
title: Добавление или настройка компонента экспресс-формы в форме | Документация Майкрософт
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.service: powerapps
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
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 758a7d2ce925526e5c0e7062f1e5134ac519e9eb
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2019
ms.locfileid: "2868262"
---
# <a name="add-and-configure-a-quick-view-component-on-a-form"></a>Добавление или настройка компонента экспресс-формы в форме  
Основная форма в которой отображаются сведения записи может использовать быстрые компонент экспресс-формы для отображения доступных только для чтения сведений связанной записи (поиск). Данные, отображаемые компонентом экспресс-формы, определяются экспресс-формой связанной сущности. Когда нет связанной записи, такой как поиск, компонент экспресс-формы автоматически скрывается.

## <a name="add-a-quick-view-component"></a>Добавление компонента экспресс-формы
Добавление компонента экспресс-формы так же, как вы добавляете любой другой компонент. Дополнительные сведения: [Добавление, настройка, перемещение или удаление компонентов в форме](add-move-configure-or-delete-components-on-form.md)

## <a name="configure-a-quick-view-component"></a>Настройка компонента экспресс-формы
Это свойства, доступные для настройки при использовании компонента экспресс-формы в форме с помощью конструктора форм.


<!--note from editor: "Drop-down" should be used only as an adjective. In the following table, is it a list? A menu? (It's used three times in line 44.) --> 


|Диаграмма с областями   |Имя  |Описание  |
|---------|---------|---------|
|**Параметры отображения** | **Подпись** | Локализуемая подпись для экспресс-формы, видимая для пользователей. <br /><br /> Это обязательное свойство. |
| **Параметры отображения** | **Название** |  Уникальное имя экспресс-формы, используемое при ссылке на нее в скриптах. Оно может содержать только алфавитно-цифровые знаки и символы подчеркивания. <br /> <br />Это обязательное свойство. |
| **Параметры отображения**  | **Скрыть подпись** |  Если установлено, подпись экспресс-формы скрыта. |
| **Параметры отображения**  | **Экспресс-формы для просмотра** |  Список экспресс-форм отображаемых для пользователей приложения. <br /><br />Настроить список экспресс-форм <br /><br /> Выберите **Выбрать формы ...**, а затем в раскрывающемся списке выберите поле **Поиск** в разделе выберите поле поиска в которых требуется экспресс-форму показывать. <br /><br />В зависимости от поля поиска, выбранного в раскрывающемся списке **Поиск**, вы увидите раскрывающиеся списки, которые позволят вам выбрать экспресс-формы для одной или нескольких сущностей. |

## <a name="see-also"></a>См. также
[Обзор конструктора управляемых моделью форм](form-designer-overview.md)  
[Создание, изменение или настройка форм с помощью конструктора форм](create-and-edit-forms.md)  
[Добавление, настройка, перемещение или удаление полей в форме](add-move-or-delete-fields-on-form.md)  
[Добавление, настройка, перемещение или удаление компонентов в форме](add-move-configure-or-delete-components-on-form.md)  
[Добавление, настройка, перемещение или удаление разделов в форме](add-move-or-delete-sections-on-form.md)  
[Добавление, настройка, перемещение или удаление вкладок в форме](add-move-or-delete-tabs-on-form.md)  
[Настройка свойств верхнего колонтитула в конструкторе форм](form-designer-header-properties.md)  
[Добавление или настройка компонента вложенной сетки в форме](form-designer-add-configure-subgrid.md)  
[Настройка компонента поиска в форме](form-designer-add-configure-lookup.md)  
[Использование представления дерева в конструкторе форм](using-tree-view-on-form.md)  
[Создание и изменение полей](../common-data-service/create-edit-field-portal.md)  
