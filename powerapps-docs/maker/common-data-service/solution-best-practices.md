---
title: Рекомендации по решениям в PowerApps | MicrosoftDocs
description: Сведения о рекомендациях при работе с решениями
ms.custom: ''
ms.date: 10/08/2019
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
ms.assetid: ''
caps.latest.revision: 55
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e10b9951ca70e497349620ae96308d6db49403fe
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "2702162"
---
# <a name="best-practices-when-working-with-solutions"></a>Рекомендации по работе с решениями 
В этом разделе описываются рекомендации при работе с решениями. 


## <a name="use-a-single-managed-solution-to-manage-a-model-driven-app"></a>Используйте одно управляемое решение для управления приложением на основе модели 
Чтобы обновить приложение, которое было включено в управляемое решение, используйте решения обновления или исправления. Не устанавливайте различные управляемые решения в среду, которые имеют одинаковое управляемое моделью приложение. Дополнительные сведения: [Обновление решений](import-update-export-solutions.md#update-solutions) и [Использование сегментированных решений и исправлений для экспорта выбранных ресурсов сущности](use-segmented-solutions-patches-simplify-updates.md) 


## <a name="use-security-roles-to-manage-app-access"></a>Использование ролей безопасности для управления доступом приложения
Управляемые моделью приложения должны иметь роли безопасности, назначенные для управления доступом пользователей. Дополнительные сведения: [Добавление ролей безопасности в приложение](../model-driven-apps/share-model-driven-app.md#add-security-roles-to-the-app) 

## <a name="delete-the-managed-solution-to-delete-a-model-driven-app"></a>Удаление управляемого решения для удаления управляемого моделью приложения 
Для удаления управляемого моделью приложения, которое было установлено в решение по умолчанию как часть управляемого решения, удалите управляемое решение. 

Не следует напрямую удалять приложение или карту сайта приложения из среды по умолчанию, которое было установлено как часть управляемого решения. Это может привести к сбою обновления решения или обновлений решений для решения, использованного для установки приложения. Примером прямого удаления управляемого моделью приложения могло быть открытие решения по умолчанию в обозревателе решений и переход в раздел **Приложения на основе модели**, выбор приложения и выбор пункта **Удалить**.

### <a name="see-also"></a>См. также
[Обзор решений](solutions-overview.md)
