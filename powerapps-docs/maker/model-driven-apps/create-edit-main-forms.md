---
title: Создание или изменение основных форм управляемого моделью приложения в Power Apps | MicrosoftDocs
description: Инструкции по созданию и изменению основной формы
ms.custom: ''
ms.date: 05/23/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: <needs new guid>
caps.latest.revision: 18
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1f2faa63b75a6842ee73f74ac1ebabd36b24d383
ms.sourcegitcommit: 551af7e0273862b28d9b2387671a4eeaf719eb37
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2020
ms.locfileid: "3116693"
---
# <a name="create-or-edit-a-model-driven-app-main-form-for-an-entity"></a>Создание или изменение основной формы управляемого моделью приложения для сущности 

В этом разделе вы узнаете, как создавать или изменять основную форму для сущности.

При создании новой формы для сущности типом формы будет "Основная". Когда открывается новая форма, она идентична форме "Сведения". Можно добавлять и изменять поля, разделы, вкладки, переходы и свойства, связанные с формой, а затем сохранить форму.

Каждая основная форма состоит из одной или нескольких вкладок. Каждая вкладка имеет один или несколько разделов. Каждый раздел содержит одно или несколько полей. Если нужно создать новую форму на основе существующей, можно клонировать форму. 

Убедитесь, что у вас есть роль безопасности "Системный администратор", "Настройщик системы" или эквивалентные разрешения для выполнения этой задачи.

## <a name="how-to-create-or-edit-a-main-form"></a>Создание или изменение основной формы
  
1.   Выполните вход в [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

2.  Разверните **Данные**, выберите **Сущности**, выберите требуемую сущность, затем выберите вкладку **Формы**. 

3. Чтобы создать новую основную форму, на панели инструментов выберите **Добавить форму** > **Основная форма**.  
    \-ИЛИ- Чтобы изменить существующую основную форму, выберите любую форму со значением **Основная** для параметра **Тип**.
  
3.  При необходимости измените внешний вид формы любым из следующих способов.
    - Добавление вкладки в форму
    - Добавление раздела в форму
    - Добавление поля в форму
    - Добавление или изменение вложенной сетки в форме
    - Изменение верхних и нижних колонтитулов формы
    - Удаление вкладки, раздела, поля
    
4.  Внесите нужные изменения в свойства частей формы:
    - Изменение свойств формы
    - Изменение свойств полей формы
    - Изменение свойств вкладки
    - Изменение свойств раздела

5.    Закончив изменение формы, выберите **Сохранить** > **Сохранить как**, введите имя формы и нажмите кнопку **OK**.

6.    Когда ваши настройки завершены, вы можете опубликовать их: выберите **опубликовать**.
 
### <a name="next-steps"></a>Дальнейшие шаги  
[Обзор конструктора управляемых моделью форм](form-designer-overview.md)

[Обзор пользовательского интерфейса редактора форм](form-editor-user-interface-legacy.md)
 
