---
title: Общие сведения о подключении к облачному хранилищу | Документация Майкрософт
description: Сведения о том, как подключиться к учетной записи облачного хранилища и отобразить в приложении данные Excel
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 07/12/2016
ms.author: lanced
ms.reviewer: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 10a6178c63495b929eb6e5885ded9394b31a11ef
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61546071"
---
# <a name="connect-to-cloud-storage-from-powerapps"></a>Подключение к облачному хранилищу из PowerApps
В PowerApps есть несколько вариантов подключения к облачным хранилищам. С помощью любого из них вы можете сохранить файл Excel и использовать информацию из него в своем приложении. Ниже перечислены доступные подключения.  

| **Azure Blob** | **Box** | **Dropbox** | **Google Диск** | **OneDrive** | **OneDrive<br>для бизнеса** |
| --- | --- | --- | --- | --- | --- |
| ![Значок](./media/cloud-storage-blob-connections/blobicon.png) |![Значок API][boxicon] |![Значок API][dropboxicon] |![Значок API][googledriveicon] |![Значок API][onedriveicon] |![Значок API][onedriveforbusinessicon] |

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

* Файл Excel с данными, [отформатированными в виде таблицы](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664):
  
  1. Откройте файл Excel и выберите любую ячейку с данными, которые вы хотите использовать.
  2. На вкладке **Insert** (Вставка) выберите **Table** (Таблица).
  3. В диалоговом окне **Save as Table** (Сохранение в виде таблицы) установите флажок **My table has headers** (Таблица с заголовками) и нажмите кнопку **ОК**.
  4. Сохраните изменения.

## <a name="connect-to-the-cloud-storage-connection"></a>Подключение к облачному хранилищу
1. На сайте [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) разверните раздел **Manage** (Управление) и выберите пункт **Connections** (Подключения):  
   
    ![Выбор подключений](./media/cloud-storage-blob-connections/connections.png)
2. Щелкните **New connection** (Создать подключение) и выберите подключение к облачному хранилищу. Например, вы можете выбрать службу **OneDrive**.
3. Вам будет предложено ввести имя пользователя и пароль к учетной записи облачного хранилища. Укажите их и нажмите **Sign in** (Войти):  
    ![Ввод имени пользователя и пароля](./media/cloud-storage-blob-connections/signin.png)
   
    После входа это подключение можно будет использовать в приложениях.
4. На ленте приложения откройте вкладку **Представление** и выберите пункт **Источники данных**. На панели справа выберите команду **Добавить источник данных**, щелкните подключение к облачному хранилищу, а затем выберите таблицу Excel.
5. Выберите команду **Создать**.
   
    Таблица указана как источник данных:
   
    ![Выбор таблицы Excel](./media/cloud-storage-blob-connections/selecttable.png)
   
    > [!NOTE]
   > Данные Excel должны быть в формате таблицы.

## <a name="using-the-excel-data-in-your-app"></a>Использование данных Excel в приложении
1. На вкладке **Insert** (Вставка) выберите **Gallery** (Коллекция), а затем — элемент управления **With text** (С текстом).
2. Укажите для свойства **[Items](../controls/properties-core.md)** (Элементы) коллекции свою таблицу Excel. Например, если она называется **Table1**, установите для этого свойства значение Table1:  
   
    ![Свойство Items](./media/cloud-storage-blob-connections/itemsproperty.png)  
   
    Коллекция автоматически обновится и будет заполнена значениями из таблицы Excel.
3. Выберите в коллекции вторую или третью **метки**. По умолчанию для свойства **Text** второй и третьей меток автоматически устанавливается значение `ThisItem.something`. Вы можете установить для этих меток любой столбец своей таблицы.
   
    В следующем примере для второй метки устанавливается значение `ThisItem.Name`, а для третьей — `ThisItem.Notes`:  
   
    ![Вторая метка](./media/cloud-storage-blob-connections/items-secondtextbox.png)  
   
    ![Третья метка](./media/cloud-storage-blob-connections/items-thirdtextbox.png)  
   
    Пример данных на экране:  
    ![Вторая и третья метки](./media/cloud-storage-blob-connections/secondthirdtextboxes.png)
   
> [!NOTE]
> Первое поле является элементом управления "Изображение". Если в вашей таблице Excel нет изображения, можно удалить элемент управления "Изображение" и добавить вместо него метку. В статье [Add and configure controls](../add-configure-controls.md) (Добавление и настройка элементов управления) представлено много полезных сведений.

В статье [Общие сведения о таблицах и записях](../working-with-tables.md) приведена более подробная информация и ряд примеров.  

## <a name="sharing-your-app"></a>Совместное использование приложения
Вы можете предоставить другим пользователям в организации общий доступ к своим [данным](../share-app-data.md), [приложению](../share-app.md) и [ресурсам](../share-app-resources.md), таким как соединители.

Чтобы предоставить общий доступ к папке в Dropbox, ее необходимо присоединить к учетной записи Dropbox.

Для соединителей, включающих файлы Excel, действуют [определенные ограничения](#sharing-excel-tables).

## <a name="known-limitations"></a>Известные ограничения
Если при попытке использовать подключение к Excel в приложении появляется сообщение **Data type unsupported** (Тип данных не поддерживается) или **Not formatted as a table** (Данные не отформатированы в виде таблицы), [отформатируйте свои данные как таблицу](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664).

Если данные Excel содержат вычисляемый столбец, вы не сможете использовать их для создания нового приложения или добавить их в существующее.

### <a name="sharing-excel-tables"></a>Совместное использование таблиц Excel
Чтобы предоставить общий доступ к данным в файле Excel:

* предоставьте общий доступ к файлу в OneDrive для бизнеса;
* в OneDrive предоставьте общий доступ к папке с файлом и укажите путь к файлу (не URL-адрес) для любого носителя;
* предоставьте общий доступ к файлу или папке в Dropbox или Google Drive.

## <a name="helpful-links"></a>Полезные ссылки
Сведения о всех доступных подключениях см. [здесь](../connections-list.md).  
Узнайте, как добавлять в приложения [подключения](../add-manage-connections.md) и [источники данных](../add-data-connection.md).  
Ознакомьтесь с [общими сведениями о таблицах и записях](../working-with-tables.md) с табличными источниками данных.  
Дополнительные ресурсы, посвященные коллекциям, включают статьи о том, как [показать список элементов](../add-gallery.md) и [показать изображения и текст в коллекции](../show-images-text-gallery-sort-filter.md).

<!--Icon references-->
[boxicon]: ./media/cloud-storage-blob-connections/boxicon.png
[dropboxicon]: ./media/cloud-storage-blob-connections/dropboxicon.png
[googledriveicon]: ./media/cloud-storage-blob-connections/googledriveicon.png
[onedriveicon]: ./media/cloud-storage-blob-connections/onedriveicon.png
[onedriveforbusinessicon]: ./media/cloud-storage-blob-connections/onedriveforbusinessicon.png
