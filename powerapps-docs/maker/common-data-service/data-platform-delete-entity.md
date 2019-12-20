---
title: Удаление настраиваемой сущности | Microsoft Docs
description: Пошаговые инструкции по удалению настраиваемой сущности и очистки всех данных в Power Apps
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8925c11d202ce73a7690687762c8bc2282913050
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "2883675"
---
# <a name="delete-a-custom-entity"></a>Удаление настраиваемого объекта
Можно удалить настраиваемые сущности, но нельзя удалить стандартные сущности.

1. На сайте [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) разверните раздел **Данные** и щелкните или нажмите **Сущности** на левой панели навигации.

    ![Сведения о сущности](./media/data-platform-cds-create-entity/entitylist.png "Список сущностей")

2. В списке сущностей щелкните или нажмите сущность, которую требуется удалить, затем щелкните или нажмите пункт **Удалить сущность** на панели команд.

3. В открывшемся диалоговом окне щелкните или нажмите **Удалить**, чтобы удалить сущность.

>[!NOTE]
>При удалении сущности удаляется как определение сущности и все данные, которые содержит сущность. Сущности и данные в них невозможно восстановить, если они удалены.

>[!NOTE]
>Можно нарушить работу приложения или потока, если удалить сущность, которая используется в данном приложении.

>[!NOTE]
>Если сущность A содержит [поля подстановки](data-platform-entity-lookup.md) в сущность B, может потребоваться удалить сущность B, чтобы можно было удалить сущность A.

