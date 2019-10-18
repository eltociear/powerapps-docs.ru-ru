---
title: DataSet | Документация Майкрософт
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0202d51f-e9a9-4a2e-b3e9-0bfd7f6afb86
ms.openlocfilehash: 5e9408c81fc9587b9dec30f18fc68c3112ba6125
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345320"
---
# <a name="dataset"></a>DataSet

[!INCLUDE [dataset-description](includes/dataset-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="properties"></a>Свойства

### <a name="addcolumn"></a>addColumn ()

Добавляет столбец в набор столбцов

### <a name="remarks"></a>Примечания

Этот метод принимает два параметра.

|Имя|Тип|Требуется|Description|
|------|-----|------|-----|
|Безымян|`string`|Да|Имя столбца, добавляемого в набор данных.|
|ентитялиас|`string`|Нет| Псевдоним сущности, для которого необходимо добавить имя столбца.|

### <a name="columns"></a>Столбце

Набор столбцов, доступных в этом наборе данных.

**Type**: [Column](column.md)[]

### <a name="error"></a>План

Указывает, произошла ли ошибка при извлечении данных.

**Тип**: `boolean`

### <a name="errormessage"></a>errorMessage

Сообщение об ошибке, связанное с последней возникшей ошибкой, если применимо.

**Тип**: `string`

### <a name="filtering"></a>записей

Фильтрация столбцов для текущего запроса.

**Тип**: [Фильтрация](filtering.md)

### <a name="linking"></a>связанных

Определяет сведения о связанной сущности.

**Тип**: [компоновка](linking.md)

### <a name="loading"></a>задержк

Указывает, загружается ли набор данных.

**Тип**: `boolean`

### <a name="paging"></a>просмотра

Состояние разбивки на страницы и действия.

**Тип**: [подкачка](paging.md)

### <a name="records"></a>PTR

Сопоставьте идентификаторы с полным объектом записи.

**Тип**: [ентитирекорд](entityrecord.md)

### <a name="sortedrecordids"></a>сортедрекордидс

Идентификаторы записей в наборе данных, упорядоченные по результатам ответа на запрос.

**Тип**: `string[]`

### <a name="sorting"></a>сортировок

Состояние сортировки для текущего запроса.

**Тип**: [сортстатус](sortstatus.md)

## <a name="methods"></a>Метод

|Method | Description | 
| ------------- |-------------|
|[клеарселектедрекордидс](dataset/clearselectedrecordids.md)|[!INCLUDE [clearselectedrecordids-description](dataset/includes/clearselectedrecordids-description.md)]| 
|[жетселектедрекордидс](dataset/getselectedrecordids.md)|[!INCLUDE [getselectedrecordids-description](dataset/includes/getselectedrecordids-description.md)]| 
|[жеттаржетентититипе](dataset/gettargetentitytype.md)|[!INCLUDE [gettargetentitytype-description](dataset/includes/gettargetentitytype-description.md)]| 
|[getTitle](dataset/gettitle.md)|[!INCLUDE [gettitle-description](dataset/includes/gettitle-description.md)]| 
|[жетвиевид](dataset/getviewid.md)|[!INCLUDE [getviewid-description](dataset/includes/getviewid-description.md)]| 
|[опендатасетитем](dataset/opendatasetitem.md)|[!INCLUDE [opendatasetitem-description](dataset/includes/opendatasetitem-description.md)]| 
|[обновляется](dataset/refresh.md)|[!INCLUDE [refresh-description](dataset/includes/refresh-description.md)]| 
|[сетселектедрекордидс](dataset/setselectedrecordids.md)|[!INCLUDE [setselectedrecordids-description](dataset/includes/setselectedrecordids-description.md)]| 

## <a name="example"></a>Пример

Дополнительные сведения о реализации методов набора данных см. в разделе [Компонент сетки набора данных](../sample-controls/data-set-grid-control.md) .

### <a name="related-topics"></a>Связанные статьи

[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)