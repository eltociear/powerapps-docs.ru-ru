---
title: Справочник по схеме манифеста платформы компонентов PowerApps | Документация Майкрософт
description: ''
keywords: ''
ms.author: nabuthuk
manager: ''
ms.date: 06/4/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 045a395b-4475-48dd-8f67-6bc2b33cd89c
ms.openlocfilehash: 88e9d35792d86e279b9af4a19eaff288643412ca
ms.sourcegitcommit: c52c1869510a9a37d9f7b127e06f07583529588b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2019
ms.locfileid: "64524305"
---
# <a name="manifest-schema-reference"></a>Справочник по схеме манифеста

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

Этот раздел содержит справочную документацию по схеме манифеста, создаваемой с помощью интерфейса командной строки PowerApps.

|Элемент|Описание|
|----|-----------|
|[code](code.md)|[!INCLUDE [code-description](includes/code-description.md)]|
|[control](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|
|[css](css.md)|[!INCLUDE [css-description](includes/css-description.md)]|
|[data-set](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|
|[html](html.md)|[!INCLUDE [html-description](includes/html-description.md)]|
|[img](img.md)|[!INCLUDE [img-description](includes/img-description.md)]|
|[manifest](manifest.md)|Манифест — это файл метаданных, определяющий компонент. Это XML-документ, описывающий следующее.<br/> – Пространство имен компонента.<br/> – Тип данных, которые можно для него настроить, т. е. поле или набор данных.<br/> – Любые свойства, которые могут быть настроены в приложении при добавлении компонента.<br/> – Список файлов ресурсов, необходимых для компонента.<br/> – Один из них должен быть веб-ресурсом JavaScript. Этот код JavaScript должен включить функцию, которая создает экземпляр объекта. Этот код реализует интерфейс, предоставляющий методы, которые требуются для работы компонента. Это называется библиотекой реализации компонентов.<br/> – Имя функции JavaScript в библиотеке реализации компонентов, которая будет возвращать объект, применяющий требуемый интерфейс.<br/> Когда пользователь настраивает компонент в приложении, данные в манифесте отфильтровывают доступные компоненты таким образом, чтобы можно было настраивать только допустимые компоненты для контекста. Свойства, определенные в манифесте компонента, отображаются как поля конфигурации, чтобы пользователь, выполняющий настройку элемента управления, мог указать значения. Значения этих свойств будут доступны для функции компонента во время выполнения.|
|[property](property.md)|[!INCLUDE [property-description](includes/property-description.md)]|
|[property-set](property-set.md)|[!INCLUDE [property-set-description](includes/property-set-description.md)]|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|
|[resx](resx.md)|[!INCLUDE [resx-description](includes/resx-description.md)]|
|[type-group](type-group.md)|[!INCLUDE [type-group-description](includes/type-group-description.md)]|


### <a name="related-topics"></a>Связанные статьи

[Справочник по схеме манифеста платформы компонентов PowerApps](index.md)<br/>
[Справочник по API платформы компонентов PowerApps](../reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](../overview.md)