---
title: Импорт данных в приложения на основе модели | Документация Майкрософт
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
- D365CE
ms.openlocfilehash: 8f1105fc88fe87aabceaa10160b96e2d7299cbe0
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74733209"
---
# <a name="import-data"></a>Импорт данных

Вы можете импортировать свои данные, хранящиеся в разных расположениях: в таблице, на телефоне или в программе электронной почты. Например, иногда нужно импортировать список контактов клиента из электронной таблицы Excel в приложение, чтобы отслеживать все данные клиента в одном расположении.
  
## <a name="step-1-get-your-import-file-ready"></a>Шаг 1. Подготовка файла импорта  
Сначала экспортируйте данные в файл Excel. Поддерживаются следующие форматы файлов:
 - книги Excel (.xls);
 - значения с разделителями запятыми (.csv).
  
Максимальный допустимый размер ZIP-файлов — 32 МБ. Для других форматов максимальный допустимый размер файлов составляет 8 МБ.  
  
### <a name="export-data-from-an-email-program"></a>Экспорт данных из программы электронной почты  
  
1.  Экспортируйте данные в файл значений с разделителями запятыми (.csv).  
  
     Чтобы определить способ экспорта контактов из программы электронной почты, откройте в программе раздел справки и выполните поиск по слову "экспорт". Найдите разделы, в заголовках которых содержится словосочетание "экспорт контактов", "экспорт адресной книги" или "мастер экспорта".  
  
2.  Сохраните файл в расположение, где вы сможете легко его найти.  
  
### <a name="export-data-from-a-spreadsheet"></a>Экспорт данных из электронной таблицы  
  
1.  Откройте электронную таблицу.  
  
2.  При необходимости измените имена столбцов в электронной таблице таким образом, чтобы они совпадали с соответствующими именами, представленными ниже.  
  
    > [!WARNING]
    > В электронной таблице могут содержаться не все перечисленные имена столбцов, это нормально. Но если имя столбца есть в таблице, оно должно совпадать с соответствующим именем в списке. Иначе вы не сможете выполнить импорт. Пробелы являются обязательными. Обратите внимание, что слово Email не содержит дефис.  

    |**Имя столбца в таблице (написание должно быть строго аналогичным)**|
    |---------|
    |Имя|  
    |Middle Name|  
    |Фамилия|  
    |Business Phone|  
    |Mobile Phone|  
    |Должность|  
    |Business Street|  
    |Business City|  
    |Business State|  
    |Business Postal Code|  
    |Business Country/Region|  
    |Email Address|  
  
3.  Сохраните файл.  
  
### <a name="export-data-from-your-phone"></a>Экспорт данных из телефона  

Используйте USB-кабель или приложение для экспорта данных, таких как контакты, с телефона на компьютер.
  
Чтобы определить способ экспорта контактов для вашей марки телефона, выполните поиск по фразе "экспорт контактов из телефона" в поисковой системе (например, Bing).  
  
Чтобы найти приложение, перейдите в интернет-магазин, связанный с вашей маркой телефона.  
  
## <a name="step-2-import-the-file"></a>Шаг 2. Импорт файла 
  
1. На панели команд выберите **Импорт из Excel** или **Импорт из CSV**.

   > [!div class="mx-imgBorder"]
   > ![Главное меню в Power Apps](media/import.png "Главное меню в Power Apps")
  
2. Перейдите к папке с сохраненным файлом, содержащим экспортированные контакты. Выберите файл, щелкните **Открыть** и **Далее**.  
  
   > [!TIP]
   > Можно импортировать только один файл за раз. Чтобы добавить файлы, запустите мастер еще раз.
   
3. Просмотрите имя файла и проверьте разделители полей и данных, используя параметр **Проверить сопоставление**. Если все правильно, выберите **Завершить импорт**.  
 
## <a name="step-3-check-that-the-import-is-successful"></a>Шаг 3. Проверка успешного выполнения импорта

По окончании работы мастера проверьте данные (например, список контактов), чтобы убедиться в успешном выполнении импорта.  
  
1. В главном меню выберите **Контакты**.
  
2. Прокрутите список контактов. Просмотрите, все ли пользователи включены в список, и проверьте точность содержимого полей.

## <a name="import-double-byte-characters"></a>Импорт двухбайтовых символов 

При импорте данных, которые содержат двухбайтовые символы для восточноазиатских языков, убедитесь, что файл кодирован с использованием метки порядка байтов (UTF-8). Обычной кодировки UTF-8 может оказаться недостаточно.

1. Откройте CSV-файл с помощью Visual Studio Code.
2. На панели внизу щелкните метку **UTF-8** (откроется всплывающее окно). 
3. Выберите **Сохранить с кодировкой**. 

Теперь вы можете выбрать кодировку UTF-8 с меткой порядка байтов для этого файла.

