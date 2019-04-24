---
title: Создание приложения на основе холста из Excel | Документы Майкрософт
description: Использование PowerApps для автоматического создания приложения на основе холста из файла Excel, хранящегося в облачной учетной записи хранения
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/14/2019
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7ab85f09ebf88c30b35c963242895cd74ca6a966
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61555136"
---
# <a name="generate-a-canvas-app-from-excel-in-powerapps"></a>Создание приложения на основе холста из Excel в PowerApps

В этом разделе вы автоматически создадите свое первое приложение на основе холста в PowerApps с помощью данных из таблицы Excel. Вы выберете файл Excel, создадите приложение, а затем запустите его. Каждое создаваемое приложение имеет экраны для просмотра списка записей и подробных сведений об отдельных записях, а также для создания и изменения записей. Вы можете быстро создать приложение, использующее данные Excel, а затем настроить его так, как вам требуется. 

Файл Excel должен находиться в облачной учетной записи хранения, например OneDrive, Dropbox или Google Диск. В этой статье используется OneDrive для бизнеса.

Если у вас нет лицензии на PowerApps, вы можете [зарегистрироваться для получения бесплатной версии](../signup-for-powerapps.md).

## <a name="prerequisites"></a>Технические условия

Для точного выполнения инструкций в этой статье скачайте файл [FlooringEstimates](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx) в Excel и сохраните его в [облачной учетной записи хранения](connections/cloud-storage-blob-connections.md).

> [!IMPORTANT]
> Вы можете использовать собственный файл Excel, однако данные в нем должны быть отформатированы в виде таблицы. Дополнительные сведения см. в разделе [Форматирование таблицы](how-to-excel-tips.md). 

## <a name="generate-the-app"></a>Создание приложения

1. Войдите в [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

1. В области **Создавайте собственные приложения** наведите указатель на плитку **Начать с данных** и выберите команду **Создать это приложение**.

    ![Команда для создания приложения](./media/get-started-create-from-data/start-from-data.png)

1. В области **Создать на основе своих данных** выберите **Макет телефона** на плитке своей облачной учетной записи хранения.

    ![Команда для создания приложения](./media/get-started-create-from-data/odfb-tile.png)

1. Если появится запрос, нажмите **Подключиться** и предоставьте данные этой учетной записи.

1. В разделе **Choose an Excel file** (Выбор файла Excel) найдите файл **FlooringEstimates.xlsx** и выберите его. 

1. В разделе **Choose a table** (Выбор таблицы) щелкните **FlooringEstimates**, а затем нажмите кнопку **Подключить**.

    ![Команда для создания приложения](./media/get-started-create-from-data/choose-table.png)

## <a name="run-the-app"></a>Запуск приложения

1. Откройте режим предварительного просмотра, нажав клавишу F5 (либо нажав значок воспроизведения в правом верхнем углу).

    ![Открытие режима предварительного просмотра](./media/get-started-create-from-data/open-preview.png)

1. Измените порядок сортировки, нажав значок сортировки в правом верхнем углу.

    ![Значок сортировки](./media/get-started-create-from-data/sort-icon.png)

1. Отфильтруйте список, введя или вставив один или несколько символов в поле поиска.

    Например, введите или вставьте **колонии** чтобы отобразить только запись для которого, что строка отображается в имени продукта, категории или Обзор.

    ![Пример фильтра](./media/get-started-create-from-data/filter-example.png)

1. Добавление записи:

    1. Выберите значок «плюс».

        ![Значок плюса](./media/get-started-create-from-data/plus-icon.png)

    1. Добавьте любые данные, необходимо, а затем выберите значок галочки, чтобы сохранить изменения.

        ![Значок сохранения](./media/get-started-create-from-data/save-icon.png)

1. Изменение записи:

    1. Щелкните стрелку для записи, которую требуется изменить.

        ![Стрелка далее](./media/get-started-create-from-data/next-arrow.png)

    1. Щелкните значок карандаша.

        ![Значок карандаша](./media/get-started-create-from-data/pencil-icon.png)

    1. Обновить одно или несколько полей, а затем выберите значок галочки, чтобы сохранить изменения.

        ![Значок сохранения](./media/get-started-create-from-data/save-icon.png)

        Кроме того выберите значок "Отмена", чтобы отменить изменения.

1. Удаление записи:

    1. Выберите стрелку «Далее» для записи, которую требуется удалить.

        ![Стрелка далее](./media/get-started-create-from-data/next-arrow.png)

    1. Выберите значок корзины.

        ![Значок корзины](./media/get-started-create-from-data/trash-icon.png)

## <a name="next-steps"></a>Дальнейшие действия

Настройте экрана обзора по умолчанию в соответствии со своими потребностями. К примеру можно сортировать и фильтровать список по только название продукта, а не категории или Обзор.

> [!div class="nextstepaction"]
> [Настройка экрана обзора по умолчанию](customize-layout-sharepoint.md)
