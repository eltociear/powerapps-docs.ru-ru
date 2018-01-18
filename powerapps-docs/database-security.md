---
title: "Настройка безопасности базы данных | Документация Майкрософт"
description: "В этой статье описана настройка безопасности базы данных."
services: powerapps
documentationcenter: na
author: maertenm
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/08/2017
ms.author: kfend
ms.openlocfilehash: a8c13158ab2c3f152aa99357684c818f48e637ae
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2018
---
# <a name="configure-database-security"></a>Настройка безопасности базы данных
Служба Common Data Service использует модель безопасности на основе ролей для обеспечения безопасного доступа к базе данных. В этой статье вы узнаете, как создавать артефакты безопасности, которые необходимы для защиты приложения. Роли пользователя позволяют контролировать доступ к данным во время выполнения. Они отделены от ролей среды, регулируемых разработчиками среды и ее администраторами. Общие сведения о средах см. в [этой статье](environments-overview.md).

Важно понимать, какой уровень доступа к этим сущностям должен быть у пользователей приложения. Служба Common Data Service поддерживает разрешения на создание, чтение, обновление и удаление сущностей.

* **Создание** — позволяет пользователю создавать записи в сущности.
* **Чтение** — позволяет пользователю просматривать имеющиеся записи и выполнять их поиск в сущности.
* **Обновление** — позволяет пользователю обновлять или изменять имеющуюся запись в сущности.
* **Удаление** — позволяет пользователю удалять или перемещать имеющуюся запись в сущности.

Чаще всего используются два уровня разрешений: разрешения на доступ только для чтения и полный доступ. Служба Common Data Service включает наборы разрешений на этих двух уровнях разрешений для всех сущностей. Наборы разрешений для просмотра предоставляют доступ на чтение к сущности. Наборы разрешений на управление предоставляют полный доступ к сущности.

Модель безопасности позволяет назначить роли пользователя любое сочетание этих разрешений. Роли могут сочетать разрешения всех добавленных к ним наборов. Таким образом, участники роли могут получить доступ ко всем данным в соответствии с наборами разрешений, включенными в роль. Дополнительные сведения о модели безопасности Common Data Service см. [здесь](https://docs.microsoft.com/en-us/common-data-service/entity-reference/security-model).

## <a name="identify-the-entities"></a>Определение сущностей
Чтобы настроить соответствующие элементы управления доступом для приложения, необходимо знать, какие сущности использует это приложение. Чтобы просмотреть список сущностей, которые использует приложение, сделайте следующее:

1. Откройте приложение в Microsoft PowerApps Studio.
2. Перейдите на вкладку **Содержимое** и щелкните или коснитесь **Источники данных**. В области справа отобразится список источников данных.

## <a name="configure-security"></a>Настройка безопасности
При создании сущности вам также необходимо создать набор разрешений или изменить имеющийся, чтобы предоставить доступ к ее данным. Если вы создаете приложение, мы советуем также создать набор разрешений, предоставляющих доступ ко всем сущностям, требуемым для выполнения этого приложения. Безопасностью можно управлять в центре администрирования.

1. Откройте [центр администрирования](https://admin.powerapps.com).
2. Выберите среду, которая содержит вашу базу данных.
3. Щелкните **Безопасность**. Для настройки безопасности базы данных используются вкладки **Наборы разрешений** и **Роли пользователей**.

## <a name="create-a-permission-set"></a>Создание набора разрешений
Чтобы предоставить доступ к новому приложению, вам сначала необходимо создать набор разрешений.

1. Выберите вкладку **Наборы разрешений**.
2. Щелкните **Новый набор разрешений**, чтобы создать набор разрешений.
3. Укажите для набора разрешений имя и описание, а затем выберите **Создать**. Созданный набор разрешений появится в соответствующем списке.
4. Выберите набор разрешений, который вы создали.
5. Выберите вкладку **Сущности**. Вкладка **Сущности** содержит список всех сущностей в базе данных. Для каждой сущности, использующейся в приложении, выберите разрешение, которое вы хотите назначить.
6. Нажмите кнопку **Save** (Сохранить).

## <a name="create-a-policy-technical-preview"></a>Создание политики (ознакомительная техническая версия)
Чтобы разрешить или ограничить доступ к записям сущности, вам сначала необходимо создать политику.

1. Выберите **Политики**.
2. Щелкните или коснитесь **Создать политику**.
3. Укажите для политики имя и описание.
4. Выберите нужный тип политики. Если вы создаете политику списка выбора, укажите нужный список выбора.
5. Выберите оператор, который будет использоваться.
6. Выберите значение для проверки политики.
7. Щелкните или коснитесь **Создать**.

## <a name="assign-a-policy-technical-preview"></a>Назначение политики (ознакомительная техническая версия)
Чтобы применить политику, ее необходимо назначить сущности данных в наборе разрешений.

1. Перейдите на вкладку **Наборы разрешений**.
2. Выберите набор разрешений для назначения политики.
3. Нажмите кнопку **Изменить** для сущности, которой назначается политика.
4. Разверните раздел **Назначение политики**.
5. Выберите операции с данными для применения к ним политики (**создание**, **чтение**, **обновление** или **удаление**).
6. Выберите поле сущности, на котором будет основана политика.
7. Выберите политику для назначения.
8. Щелкните или коснитесь **Назначить**.
9. Нажмите кнопку **Save** (Сохранить).

## <a name="create-and-assign-a-role"></a>Создание роли и ее назначение
После включения соответствующих разрешений в набор разрешений вы можете создать роль, которую можно назначить пользователям.

1. Перейдите на вкладку **Роли пользователя**.
2. Выберите **Новая роль**.
3. Присвойте роли имя и описание, а затем выберите **Создать**. Созданная роль появится в списке ролей **пользователя**.
4. Выберите роль, которую вы создали.
5. Перейдите на вкладку **Наборы разрешений**.
6. Введите имя набора разрешений, который вы создали ранее. В раскрывающемся списке, который появится при вводе, выберите набор разрешений, чтобы добавить его в роль. Добавьте другие наборы разрешений, которые вы хотите включить в роль.
7. Выберите для роли вкладку **Пользователи**.
8. Введите имена или адреса электронной почты пользователей (групп), чтобы добавить их в роль. В раскрывающемся списке, который появится при вводе, выберите пользователя. В список будут добавлены пользователи или группы, которым будет назначена роль.
9. Нажмите кнопку **Save** (Сохранить).

Теперь пользователи или группы в этой роли могут получить доступ к данным, предоставляемым любым набором разрешений, связанным с этой ролью. Чтобы использовать данные в базе данных, у пользователя должна быть роль безопасности и доступ к приложению PowerApps, которое эти данные использует.

## <a name="edit-permission-sets-and-roles"></a>Изменение наборов разрешений и ролей
Созданные роли и наборы разрешений можно изменить. Для этого нажмите кнопку **Изменить**.

Чтобы удалить роль или набор разрешений, нажмите кнопку **Удалить**.

## <a name="out-of-box-security-roles"></a>Встроенные роли безопасности
Две роли безопасности являются встроенными:

* **Владелец базы данных** — эта роль предназначена для пользователей, выполняющих административную функцию. Разработчик среды назначается этой роли автоматически. У пользователей, включенных в эту роль, всегда есть полный доступ ко всем сущностям в базе данных и даже к новым добавленным сущностям. Пользователи с ролью владельца базы данных также могут создавать и изменять схемы сущности в базе данных. Вам не нужно добавлять наборы разрешений для этой роли, достаточно просто назначать ее пользователям.
* **Пользователь в организации** — это роль по умолчанию, которая присваивается всем пользователям. Пользователи с этой ролью имеют доступ ко всем сущностям, содержащим общедоступные данные. Сущности, используемые приложениями с ограниченным режимом доступа, должны быть включены в эту роль. Эту роль присваивать не нужно, она назначается изначально для каждого пользователя в организации. Вам только нужно добавить наборы разрешений, которые вы хотите предоставить для всех сотрудников организации.
