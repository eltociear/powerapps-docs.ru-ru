---
title: Объединение повторяющихся записей | Документация Майкрософт
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/31/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c0811645429c9f1e7570ceeaf316a5217e440ae4
ms.sourcegitcommit: bee698ca0d11524377b67813a65e1a022d08c05e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73609887"
---
# <a name="merge-duplicate-records"></a>Объединение повторяющихся записей 

Повторяющиеся записи могут появляться в данных, когда вы или другие пользователи вводите данные вручную или импортируете данные в виде пакета. Common Data Service помогает устранить потенциальные повторы, предоставляя обнаружение повторов для активных записей, таких как учетные записи и контакты. При объединении записи все связанные или дочерние записи также будут объединены. Администратор может также настроить правила обнаружения повторяющихся данных для других ситуаций.  
  
Например, вы вводите запись контакта "Джим Глинн", а также номер мобильного телефона.  Правило обнаружения повторяющихся данных определяет, что у вас уже есть аналогичная запись, и отображает это диалоговое окно.  
  
 > [!div class="mx-imgBorder"] 
 > ![Обнаружена повторяющаяся запись контакта](media/duplicates-detected.png "Обнаружена повторяющаяся запись контакта")  
  
 Вы не уверены, новая это запись (имя которой совпадает с именем существующего контакта) или дубликат, поэтому выберите **Пропустить и сохранить**.  
  
 Затем перейдите к списку **Все контакты**, и вы увидите, что теперь у вас есть две записи с одинаковым именем. После просмотра записей необходимо определить, что они являются дубликатами, которые необходимо объединить.  
 
 > [!div class="mx-imgBorder"] 
 > ![Обнаружена повторяющаяся запись контакта](media/duplicates-detected_1.png "Обнаружена повторяющаяся запись контакта")  
 
Common Data Service содержит правила обнаружения повторений для учетных записей и контактов. Эти правила включены автоматически, поэтому вам не нужно ничего делать, чтобы настроить обнаружение дубликатов для этих типов записей.  
  
> [!NOTE]
>  При наличии этой функции в системе можно также проверить наличие дубликатов других типов записей, не только контактов и учетных записей. Уточните у своего системного администратора. [Обращение к администратору или в службу поддержки](find-admin.md)  
  
## <a name="merge-duplicate-records"></a>Объединение повторяющихся записей  
  
1. Выберите повторяющиеся записи, а затем выберите **Объединить**.  
  
   > [!div class="mx-imgBorder"] 
   > ![Обнаружена повторяющаяся запись контакта](media/duplicates-detected_2.png "Обнаружена повторяющаяся запись контакта")  
  
2. В диалоговом окне **Объединить записи** выберите главную запись (ту, которую хотите сохранить), а затем выберите поля в новой записи, которые необходимо объединить с главной записью. Данные в этих полях могут переопределять существующие данные в главной записи. Выберите **ОК**.  
  
     
   > [!div class="mx-imgBorder"] 
   > ![Диалоговое окно для объединения записей](media/merge-records-dialog.png "Диалоговое окно для объединения записей")  
  
> [!NOTE]
>  Дубликаты обнаруживаются в нескольких ситуациях.  
> 
> - При создании или обновлении записи.  
>   - При использовании Dynamics 365 для Outlook и переходе из автономного режима в сеть.  
>   - При импорте данных с помощью мастера импорта данных.  
> 
>   Дубликаты не обнаруживаются при объединении записей, сохранении действия как завершенного или изменении состояния записи, например активации или повторной активации записи.  
