---
title: Функции для предварительного ознакомления. Использование базы данных Azure Cosmos DB для поставщика данных API SQL с Common Data Service | MicrosoftDocs
description: Узнайте, как настраивать базу данных Azure Cosmos DB для поставщика данных API SQL для использования с виртуальными сущностями.
keywords: API SQL
ms.date: 02/15/2019
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: d0031ffc-8754-4a12-b8c1-e08edc49ff73
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: ''
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3e9594ada54fb89f77298a4077281dcedbb8c656
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "2705682"
---
# <a name="preview-feature-azure-cosmos-db-sql-api-data-provider-requirements"></a>Функция для предварительного ознакомления. Требования к базе данных Azure Cosmos DB для поставщика данных API SQL

В этом разделе описываются требования для базы данных Azure Cosmos DB для поставщика данных SQL API, а также порядок настройки и рекомендации при использовании базы данных Azure Cosmos DB для поставщика данных SQL API с виртуальными сущностями. 

> [!IMPORTANT]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-expect-changes.md)]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-no-ms-support.md)]


## <a name="what-is-azure-cosmos-db"></a>Что такое Azure Cosmos DB?

Azure Cosmos DB — это глобально распространяемый многомодельный сервис базы данных Microsoft для критически важных приложений. Он предоставляет широкие и привычные возможности запросов SQL с постоянными низкими задержками с данными JSON без схемы. Дополнительные сведения: [Введение в базу данных Azure Cosmos DB: API SQL](https://docs.microsoft.com/azure/cosmos-db/sql-api-introduction)

## <a name="requirements"></a>Требования

- Подписка Azure, которая включает Azure Cosmos DB.
- Коллекция Azure Cosmos DB SQL API.
- Тип базы данных Azure Cosmos DB должен быть SQL. 

## <a name="data-type-mapping"></a>Сопоставление типов данных

Предположим, что имеется документ Azure Cosmos DB в коллекции с именем *Заказы*, который имеет следующую структуру JSON.

![Пример JSON для документа API SQL.](media/documentdbexample.png)

В этой таблице указаны сопоставления типов данных для документа SQL API в коллекции *Заказы* с Common Data Service.

|Данные SQL API|Common Data Service|
|--|--|
|`id`|Первичный ключ|
|`name`|Строка текста|
|`quantity`|Целое число|
|`orderid`|Одна строка текста|
|`ordertype`|Набор параметров|
|`amount`|Десятичное число или валюта|
|`delivered`|Два параметра|
|`datetimeoffset`|Дата и время|

> [!NOTE]
> - Атрибуты с префиксом подчеркивания (_) создаются в SQL API.
> - Атрибуты, которые настроены как необязательные в документе SQL API и сопоставлены в Common Data Service как **Требуется для бизнеса**, вызывают ошибку среды выполнения.
> - Значения атрибута id должны иметь тип guid.
> - Дополнительные сведения об использовании дат в SQL API см. в разделе [Работа с данными в Azure Cosmos DB](https://azure.microsoft.com/blog/working-with-dates-in-azure-documentdb-4/).

## <a name="supported-sql-query-filtering"></a>Поддерживаемая фильтрация запросов SQL

Фильтрация запросов SQL поддерживает следующие операторы. 

- Операторы сравнения: `<`,`>`,`<=`, `>=`,`!=`
- Логические операторы: `and`, `or` 
- Логические операторы: `in`, `not in`
- Строковые операторы: `like`, `contains`, `begins with`, `ends with`

> [!NOTE]
> Использование оператора like переводится в соответствующие операторы `contains`/`begins with`/`ends with`. SQL API не поддерживает аргументы шаблонов, как описано в разделе [Like (Transact-SQL)](/sql/t-sql/language-elements/like-transact-sql). База данных Azure Cosmos DB для поставщика данных SQL API может переводить один особый случай `Like('[aA]%')` в `BeginsWith('a')` OR `BeginsWith('A')`. Обратите внимание, что сравнение строк в SQL API чувствительно к регистру символов.

## <a name="add-a-data-source-using-the-azure-cosmos-db-for-sql-api-data-provider"></a>Добавление источника данных с использованием базы данных Azure Cosmos DB для поставщика данных API SQL

1. Перейдите в [AppSource](https://appsource.microsoft.com/product/dynamics-365/mscrm.documentdb_data_provider?tab=Overview), выберите **ПОЛУЧИТЬ** и следуйте инструкциям для добавления приложения в вашу среду с использованием версии v9x или более поздней.
2. После установки решения выполните вход в среду и откройте **Параметры** > **Администрирование** > **Источники данных виртуальных сущностей**.
3. На панели инструментов действий выберите **СОЗДАТЬ**, затем в диалоговом окне **Выберите поставщика данных** выберите **Azure Cosmos DB для поставщика данных API SQL** и выберите **ОК**.
![Выберите Azure Cosmos DB для поставщика данных API SQL](media/createdatasource.png)
1. Введите следующую информацию и выберите **СОХРАНИТЬ И ЗАКРЫТЬ**.

    |Поле|Описание|
    |--|--|
    |**Название**|Введите имя, которое описывает источник данных.|
    |**Имя коллекции**|Имя *базы данных* Azure Cosmos DB, содержащей коллекцию, которую требуется выводить в виртуальной сущности.  |
    |**Ключ авторизации**|Первичный или вторичный ключи для учетной записи Azure Cosmos DB. Ключ можно найти на портале администрирования Azure в параметре **Ключи** в вашей учетной записи Azure Cosmos DB.|
    |**URI-адрес**|URI-адрес группы ресурсов, в которой расположена коллекция Azure Cosmos DB. URI формируется аналогично `https://contoso/documents.azure.com:443`. URI-адрес можно найти на портале администрирования Azure в параметре **Ключи** для учетной записи Azure Cosmos DB. |
    |**Время ожидания в секундах**|Введите число секунд ожидания ответа службы Azure Cosmos DB перед отменой запроса данных из-за истечения времени ожидания. Например, введите 30 для ожидания не более 30 секунд до истечения срока ожидания. Время ожидания по умолчанию составляет 120 секунд.|

    > [!div class="mx-imgBorder"] 
    > ![Создайте источник данных с использованием поставщика данных API SQL.](media/cosmosdb-datasource.png)

## <a name="best-practices-and-limitations"></a>Рекомендации и ограничения

- Обратите внимание на следующее при использовании Azure Cosmos DB в качестве источника данных:
   - Каждый источник данных Azure Cosmos DB может быть связан только с одной виртуальной сущностью.
   - Можно подключить несколько источников данных к одной коллекции в Azure Cosmos DB.
- Нельзя сегментировать данные в коллекции по сущностям.
- Базы данных Azure Cosmos DB не требуют схемы, тем не менее данные внутри Azure Cosmos DB должны быть структурированы с помощью предсказуемой схемы. 
- Хотя база данных Azure Cosmos DB для поставщика данных SQL API реализует трансляцию запроса операторов проецирования, фильтрации и сортировки, она не поддерживает операции объединения.
- Можно фильтровать только по одному столбцу с SQL API.

## <a name="see-also"></a>См. также

[Создание и изменение виртуальных сущностей, содержащих данные из внешнего источника данных](create-edit-virtual-entities.md)
