---
title: Экспорт в сводную таблицу Excel в управляемой моделью PowerApp | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 90cf377f10a99dbcece1e5f556cb50e678099744
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2019
ms.locfileid: "61544989"
---
# <a name="export-to-an-excel-pivottable"></a>Экспорт в сводную таблицу Excel


Вы можете экспортировать данные приложений в сводную таблицу Office Excel, чтобы просмотреть закономерности и тенденции в данных. Сводная таблица Excel — это отличный способ суммирования, анализа, просмотра и представления данных приложения. В каждый момент времени можно экспортировать до 100 000 записей.  
  

## <a name="export-data-to-an-excel-pivottable"></a>Экспорт данных в сводную таблицу Excel  
Возможность экспорта данных в сводную таблицу Excel доступна не во всех типах записей. Если этот параметр не отображается, он недоступен для этой записи.  
  
1. Откройте список записей в приложении, щелкните стрелку справа от параметра **Экспорт в Excel**, а затем выберите пункт **Динамическая сводная таблица**.  
  
2. В диалоговом окне **Выбор столбцов для сводной таблицы Excel** выберите параметры столбца и щелкните **Экспорт**.  
  
   По умолчанию **список полей сводной таблицы** содержит только поля, отображаемые в списке **Выбор столбцов для сводной таблицы Excel** .  
  
3. Выберите **сохранить** , а затем сохраните XLSX файл. Запишите место, где был сохранен файл.  
  
   > [!NOTE]
   > Если вы собираетесь изменить файл данных позже, рекомендуется сохранить файл перед его открытием. В противном случае может появиться следующее сообщение об ошибке: **Excel не может открыть или сохранить больше документов из-за нехватки свободной памяти или места на диске.**  
   > 
   > Чтобы устранить эту проблему, выполните следующие действия.  
   > 
   > 1. Откройте Excel и выберите **файл** > **Параметры** > **центр управления безопасностью**.  
   > 2. Выберите **Параметры центра управления безопасностью** , а затем щелкните **защищенное представление**.  
   > 3. В разделе **защищенное представление**снимите флажки для всех трех элементов.  
   > 4. Нажмите кнопку **ОК** > **ОК**.  
   > 
   > Мы настоятельно рекомендуем сохранить и открыть файл данных, а не отключать защищенное представление, что может поставить под угрозу компьютер.  
  
4. Откройте Excel, а затем откройте XLSX файл, сохраненный на предыдущем шаге.  
  
5. Если отображается предупреждение безопасности подключения к **внешним данным отключены**, выберите **включить содержимое**.  
  
6. Чтобы обновить данные в файле, на вкладке **данные** выберите **Обновить из PowerApps**.  
  
7. Перетащите поля из списка полей сводной таблицы в сводную таблицу. Дополнительные сведения см. в справке Excel.  
  
## <a name="tips"></a>Советы  
  
- В PowerApps значения валют экспортируются в Excel как числа. После завершения экспорта обратитесь к разделу справки Excel "Отображение чисел как денежной единицы", чтобы отформатировать данные как валюту.
  
- Значения даты и времени, отображаемые в приложении, отображаются только как Дата при экспорте файла в Excel, но в ячейке фактически отображается дата и время.  
  
- Если вы собираетесь внести изменения и импортировать файл данных обратно в приложение, помните, что защищенные, вычисляемые и составные поля (такие как полное имя) доступны только для чтения и не могут быть импортированы в приложение. Вы сможете изменить эти поля в Excel, но при импорте данных обратно в приложение эти поля не будут обновлены. Если вы хотите обновить эти поля, например имя контакта, рекомендуется использовать это представление для экспорта данных, обновления в Excel и импорта их обратно в приложение для внесения изменений.  
  
 