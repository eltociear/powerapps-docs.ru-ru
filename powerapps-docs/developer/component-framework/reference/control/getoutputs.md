---
title: Выходные данные | MicrosoftDocs
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: reference
applies_to: ''
ms.assetid: c83c3a09-f04e-4dc6-8ddf-ccd0b4cc080e
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 408633e1fd87c3c9517ec0984251bbbce056cc50
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345389"
---
# <a name="getoutputs"></a>getOutputs

[!INCLUDE[./includes/getoutputs-description.md](./includes/getoutputs-description.md)]

## <a name="available-for"></a>Доступно для 

Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия)

## <a name="syntax"></a>Синтаксис

`getOutputs()`

## <a name="remarks"></a>Примечания

Выходные данные будут содержать значения для каждого свойства, помеченного как `input-output` или `bound` в манифесте.
Например, если манифест имеет свойство `value`, которое является `input-output`ом и необходимо задать его для локальной переменной `myvalue` необходимо вернуть:

```javascript
{
    value: myvalue
}
```

## <a name="example"></a>Пример

```javascript
MyControl.prototype.getOutputs = function () {
    var result = {
        value: this._value
    };
    return result;
};
```


### <a name="related-topics"></a>Связанные статьи

[Элемент управления](../control.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../../overview.md)