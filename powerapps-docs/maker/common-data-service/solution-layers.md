---
title: Просмотр слоев решения | MicrosoftDocs
description: Сведения о способах использования слоев решения
keywords: ''
ms.date: 04/18/2019
ms.service: powerapps
ms.custom: ''
ms.topic: article
ms.assetid: ''
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
ms.openlocfilehash: a5b507384b3fdf157aa029ad98d4d4203f624d8f
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "2702118"
---
<!--note from editor: Best practice is that H1 title and title in metadata are different.    -->

# <a name="view-solution-layers"></a>Просмотр слоев решения
Слои решения позволяют просматривать все изменения компонентов, возникающих из-за изменения решения с ходом времени. В рамках слоя решения можно детализировать сведения для просмотра сведений об определенном измененном или неизменном свойстве для компонента. 

Слои решений: 
-   Позволяют увидеть порядок, в котором решение изменяло компонент. 
-   Позволяет просматривать все свойства компонента в рамках определенного решения, включая изменения компонента. 
-   Может использоваться для устранения неполадок зависимости или проблем слоев решения, отображая сведения об изменениях для компонента, который был введен при изменении решения.

## <a name="view-the-solution-layers-for-a-component"></a>Просмотр слоев решения для компонента
Можно получить доступ к слоям решения из списка **Компоненты** или из диалогового окна **Сведения о зависимости** в обозревателе решений. 

<!--note from editor: In step 2 below, does the page display a name at top? If so, use the same capitalization in text. -->

1. Для просмотра слоев решения из списка **Компоненты**, откройте [обозреватель решений](../model-driven-apps/advanced-navigation.md#solution-explorer). В списке **Компоненты** выберите компонент, например **Организация**, затем выберите **Слои решения** на панели инструментов. 

   > [!div class="mx-imgBorder"] 
   > ![Кнопка слоев решения](media/solution-layers-toolbar.png "Кнопка слоев решения")

2. Отобразится страница слоев решения. На не отображается каждый слой для компонента, например для показанной здесь сущности **Организация**, с самым недавним слоем сверху. Для просмотра сведений для слоя решения выберите его. 

   > [!div class="mx-imgBorder"] 
   > ![Список слоев решения](media/solution-layers-list.png "Список слоев решения")

3. В диалоговом окне **Слой решения** на вкладке **Измененные свойства** отображаются только те свойства, которые были изменены в рамках определенного слоя решения. 

   > [!div class="mx-imgBorder"] 
   > ![Измененные свойства слоя решения](media/solution-layers-change-prop.png "Измененные свойства слоя решения")

4. Выберите вкладку **Все свойства** для просмотра всех свойств, включая измененные и неизменные свойства, для слоя решения. 

   > [!div class="mx-imgBorder"] 
   > ![Все свойства слоя решения](media/solution-layers-all-prop.png "Все свойства слоя решения")

### <a name="see-also"></a>См. также
[Обзор решений](solutions-overview.md)
