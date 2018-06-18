---
title: Открытие данных сущности в Excel | Документация Майкрософт
description: Открытие данных сущности в Excel для интерактивного просмотра и редактирования.
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: clwesene
ms.openlocfilehash: 8dbf6088104270d9251b70eec9adf0642de2f879
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34445908"
---
# <a name="open-entity-data-in-excel"></a>Открытие данных сущности в Excel
Открыв данные сущности в Microsoft Excel, вы сможете быстро и легко просмотреть и изменить данные с помощью надстройки Microsoft PowerApps Excel. Для использования надстройки PowerApps для Excel требуется Microsoft Excel 2016.

![Надстройка Excel](./media/data-platform-cds-excel-addin/ExcelAddin.png "Надстройка PowerApps для Excel")

## <a name="open-entity-data-in-excel"></a>Открытие данных сущности в Excel
1. На сайте [powerapps.com](https://web.powerapps.com) разверните раздел **Данные** и выберите элемент **Сущности** в области навигации слева. Отобразятся все сущности.
2. Нажмите кнопку с многоточием (...) справа от сущности, которая вас интересует.
3. Щелкните действие **Открыть в Excel** и откройте созданную книгу. Эта книга содержит сведения о привязке для выбранной сущности, указатель на среду и указатель на надстройку PowerApps для Excel.  
4. В Excel нажмите кнопку **Разрешить редактирование**, чтобы разрешить запуск надстройки PowerApps для Excel. Надстройка Excel откроется на панели в правой части окна Excel.
5. Если надстройка PowerApps для Excel запущена впервые, щелкните **Доверять этой надстройке**, чтобы разрешить запуск надстройки в Excel.
6. Если вы увидите приглашение для входа, щелкните **Войти** и выполните вход с теми же учетными данными, которые вы использовали на сайте [powerapps.com](https://web.powerapps.com). Надстройка Excel автоматически выполнит вход, используя данные, использованные для предыдущего входа, если это возможно. Убедитесь, что в верхнем правом углу надстройки Excel указано правильное имя пользователя.

Надстройка Excel автоматически считывает данные для выбранной сущности. Обратите внимание, что данные появятся в книге только после того, как надстройка Excel их считает.

## <a name="view-and-refresh-data-in-excel"></a>Просмотр и обновление данных в Excel
Когда надстройка Excel закончит перенос данных в рабочую книгу, вы можете в любой момент обновить эти данные, щелкнув **Обновить** в надстройке Excel.

## <a name="edit-data-in-excel"></a>Изменение данных в Excel
Теперь вы можете изменить любые данные о сущности, а затем опубликовать их, щелкнув команду **Опубликовать** в надстройке Excel.

Чтобы изменить запись, выделите ячейку на листе и введите новое значение ячейки.

Чтобы добавить новую запись, выполните одно из следующих действий.

* Щелкните в любом месте листа и нажмите кнопку **Добавить** в надстройке Excel.
* Щелкните в последней строке листа и нажмите клавишу Tab несколько раз, чтобы курсор вышел за пределы последнего столбца в этой строке. Это действие создает новую строку.
* Щелкните строку непосредственно под листом и просто вводите данные в ячейке. Когда фокус ввода уйдет из этой ячейки, лист автоматически расширится и добавит новую строку.

Чтобы удалить запись, выполните одно из следующих действий.

* Щелкните правой кнопкой мыши номер строки рядом со строкой, которую следует удалить, и нажмите кнопку **Удалить**.
* Щелкните правой кнопкой мыши в строке листа, которую нужно удалить, а затем выберите действие **Удалить** > **Строки таблицы**.

## <a name="add-or-remove-columns"></a>Добавление или удаление столбцов
С помощью конструктора вы можете указать, какие столбцы и сущности должны автоматически добавиться на лист.

1. Включите конструктор источников данных, доступный в надстройке Excel. Для этого откройте меню **Параметры** (обозначено символом шестеренки) и установите флажок **Включить разработку**.
2. Щелкните **Разработка** в надстройке Excel, чтобы отобразить все источники данных.
3. Рядом с источником данных щелкните кнопку **Изменить** (обозначена символом карандаша).
4. Настройте список в поле **Выбранные поля**.
   * Чтобы добавить поле из поля **Доступные поля** в поле **Выбранные поля**, щелкните нужное поле и выберите действие **Добавить**. Также можно просто дважды щелкнуть это поле.
   * Чтобы удалить поле из поля **Выбранные поля**, щелкните поле для удаления и выберите действие **Удалить**. Также можно просто дважды щелкнуть это поле.
   * Чтобы изменить порядок полей, щелкните нужное поле в поле **Выбранные поля** и выберите действие **Вверх** или **Вниз**.
5. Чтобы применить изменения к источнику данных, щелкните **Обновить**, а затем нажмите **Готово** для выхода из конструктора. Если вы добавили новое поле (столбец), щелкните **Обновить** для получения обновленного набора данных.

> [!NOTE]
> В рабочую книгу следует всегда включать идентификатор и обязательные для заполнения поля, иначе могут возникать ошибки публикации.

> [!NOTE]
> При добавлении полей подстановки необходимо добавлять поля идентификатора и отображения.

## <a name="troubleshooting"></a>Устранение неполадок
Существует несколько известных проблем, которые можно решить простыми действиями.

* Редактирование и создание новых записей поддерживается только определенными сущностями. Эти сущности открывают Excel и позволяют просматривать данные, но без возможности публикации.
* Для указания правильной записи поля подстановки следует изменять с помощью надстройки. Обновление этих полей путем копирования и вставки или непосредственный ввод в поле не поддерживаются.


Если вы столкнетесь с проблемой, которая не описана здесь, свяжитесь с нами через [страницы поддержки](https://powerapps.microsoft.com/support/).

## <a name="next-steps"></a>Дальнейшие действия
* [Управление полями сущности](data-platform-manage-fields.md)
* [Определение связи между сущностями в модели общих данных](data-platform-entity-lookup.md)
* [Создание приложения с помощью службы Common Data Service для приложений](../canvas-apps/data-platform-create-app.md)
* [Создание приложения с нуля с помощью службы Common Data Service для приложений](../canvas-apps/data-platform-create-app-scratch.md)
