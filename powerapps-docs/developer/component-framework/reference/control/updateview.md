---
title: Упдатевиев | MicrosoftDocs
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 899d6eb3-62b4-4c1f-947c-aed1f8643caa
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: d7ac81ef617aa4e9e3564ade01bc469b0d7f5bc8
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345343"
---
# <a name="updateview"></a>updateView

[!INCLUDE[./includes/updateview-description.md](./includes/updateview-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия)

## <a name="syntax"></a>Синтаксис

`updateView(context)`

## <a name="parameters"></a>Вход

| Имя параметра|Тип|Требуется|Description|
| ------------- |----|--------|-----------|
|локального|`context`|да|Содержит значения, настроенные средством настройки, сопоставленные с именем, определенным в манифесте, а также в служебных функциях.|

## <a name="example"></a>Пример

```JavaScript
MyNameSpace.JSHelloWorldControl.prototype.updateView = function (context) {
    this._labelElement.innerText = "Hello World! (JS)";
};
```

## <a name="remarks"></a>Примечания

Установить в качестве значения компонента поля необработанное значение из настроенного поля


### <a name="related-topics"></a>Связанные статьи

[Элемент управления](../control.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)