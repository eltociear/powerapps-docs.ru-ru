---
title: init | MicrosoftDocs
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: reference
applies_to: ''
ms.assetid: 4485b7d4-c68f-4298-8676-1820eb33c1ad
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 57a5ce0d4e930184bf42502f1dc16b6a648f1292
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345504"
---
# <a name="init"></a>init

[!INCLUDE[./includes/init-description.md](./includes/init-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия)

## <a name="syntax"></a>Синтаксис

`init(context,notifyOutputChanged,state,container)`

## <a name="parameters"></a>Вход

| Имя параметра|Тип|Требуется|Description|
| ------------- |----|--------|-----------|
|локального|[Context](../context.md)|да|*Входные свойства* , содержащие параметры, метаданные компонента и функции интерфейса.|
|нотифйоутпутчанжед|`function`|нет|Метод уведомления платформы о новых выходных данных|
|С|`Dictionary`|нет|Состояние компонента, сохраненное из *сетконтролстате* в последнем сеансе|
|Контейнера|[хтмлдивелемент](https://developer.mozilla.org/docs/Web/API/HTMLDivElement)|нет|Отображаемый элемент div|

## <a name="example"></a>Пример

```JavaScript
MyNameSpace.JSHelloWorldControl.prototype.init = function (context, notifyOutputChanged, state, container) {
    this._labelElement = document.createElement("label");
    this._labelElement.setAttribute("class", "JS_HelloWorldColor");
    container.appendChild(this._labelElement);
};
```

### <a name="related-topics"></a>Связанные статьи

[Элемент управления](../control.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)
