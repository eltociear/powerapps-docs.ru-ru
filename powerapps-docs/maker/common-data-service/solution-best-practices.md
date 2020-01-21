---
title: Рекомендации по решениям в Power Apps | MicrosoftDocs
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
ms.openlocfilehash: 40c59ccdebe8ee5192510b5d8ac7e825c6b68c58
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2019
ms.locfileid: "2909431"
---
# <a name="best-practices-when-working-with-solutions"></a>Рекомендации по работе с решениями 
В этом разделе описываются рекомендации при работе с решениями. 


## <a name="use-a-single-managed-solution-to-manage-a-model-driven-app"></a>Используйте одно управляемое решение для управления приложением на основе модели 
Чтобы обновить приложение, которое было включено в управляемое решение, используйте решения обновления или исправления. Не устанавливайте различные управляемые решения в среду, которые имеют одинаковое управляемое моделью приложение. Дополнительные сведения: [Обновление решений](update-solutions.md) и [Использование сегментированных решений и исправлений для экспорта выбранных ресурсов сущности](use-segmented-solutions-patches-simplify-updates.md) 


## <a name="use-security-roles-to-manage-app-access"></a>Использование ролей безопасности для управления доступом приложения
Управляемые моделью приложения должны иметь роли безопасности, назначенные для управления доступом пользователей. Дополнительные сведения: [Добавление ролей безопасности в приложение](../model-driven-apps/share-model-driven-app.md#add-security-roles-to-the-app) 

## <a name="delete-the-managed-solution-to-delete-a-model-driven-app"></a>Удаление управляемого решения для удаления управляемого моделью приложения 
Для удаления управляемого моделью приложения, которое было установлено в решение по умолчанию как часть управляемого решения, удалите управляемое решение. 

Не следует напрямую удалять приложение или карту сайта приложения из среды по умолчанию, которое было установлено как часть управляемого решения. Это может привести к сбою обновления решения или обновлений решений для решения, использованного для установки приложения. Примером прямого удаления управляемого моделью приложения могло быть открытие решения по умолчанию в обозревателе решений и переход в раздел **Приложения на основе модели**, выбор приложения и выбор пункта **Удалить**.

### <a name="see-also"></a>См. также
[Обзор решений](solutions-overview.md)
