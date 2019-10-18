---
title: Библиотека реализации компонентов | Документация Майкрософт
description: Создание компонентов кода с помощью JavaScript или TypeScript
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d100dc3-bd82-4b45-964c-d90eaebc0735
ms.openlocfilehash: 31b7d2b30a1ef83ca4400011d50854713cb260f6
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72347252"
---
# <a name="component-implementation-library"></a>Библиотека реализации компонентов

Реализация библиотеки компонентов является одним из ключевых шагов при разработке компонентов кода с помощью платформы компонентов PowerApps. Разработчики могут реализовать библиотеку компонентов с помощью TypeScript. Каждый компонент кода должен иметь библиотеку, включающую в себя определение функции, которая возвращает объект, реализующий методы, описанные в интерфейсе компонента кода. 

Объект реализует следующие методы:

- [init](reference/control/init.md) (обязательно)
- [упдатевиев](reference/control/updateview.md) (обязательно)
- [выходные данные](reference/control/getoutputs.md) (необязательно)
- [уничтожить](reference/control/destroy.md) (обязательно)

Эти методы управляют жизненным циклом компонента кода.

