---
title: Предоставление общего доступа к файлам Excel, используемым приложением | Документация Майкрософт
description: Совместное использование файлов Excel в Dropbox, OneDrive и Google Диске. Пользователи могут изменять и просматривать файлы и папки.
author: jamesol-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/16/2016
ms.author: jamesol
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b2eca27d418a762820bf0955edafff435a176efb
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2019
ms.locfileid: "74674930"
---
# <a name="share-excel-data-used-by-your-app"></a>Совместное использование данных Excel, используемых приложением
Пользователи приложения могут совместно использовать данные Excel в [облачной учетной записи](connections/cloud-storage-blob-connections.md), например OneDrive.

Например, можно создать приложение, которое показывает имена и номера телефонов группы технической поддержки вашей компании. Данные хранятся в электронной таблице Excel, которая помещена в папку в Dropbox. Можно предоставить общий доступ к этой папке пользователям приложения, чтобы они могли просматривать имена и номера телефонов.

Необходимо предоставить общий доступ к данным, чтобы пользователи могли запускать и даже изменять приложение. Пользователи, не получившие разрешения на общий доступ, не будут видеть данные в файле Excel.

В этом разделе показано, как совместно использовать данные в электронной таблице Excel, используя Dropbox, OneDrive и Google Диск. Чтобы создать приложение, которое отображает данные из файла Excel, изучите раздел [Создание приложения на основе данных Excel](get-started-create-from-data.md).

## <a name="share-data-in-dropbox"></a>Совместное использование данных в Dropbox
1. Войдите в Dropbox, используя ту же учетную запись, которая использовалась для создания подключения из Power apps к Dropbox.
2. Выберите папку, содержащую файл Excel, а затем выберите **Поделиться**.  
   
    ![Пункт "Совместный доступ"](./media/share-app-data/dropbox-share.png)
3. В диалоговом окне введите электронные адреса, с помощью которых пользователи приложения входят в Dropbox.  
   
    ![Общий доступ в Dropbox](./media/share-app-data/dropbox-perms.png)
4. Если пользователи приложения будет добавлять, изменять или удалять данные в приложении, выберите **Может изменять**. В противном случае выберите **Просмотр**.
5. Выберите **Поделиться**.

Дополнительные сведения см. в разделе [Общие папки: как предоставить доступ к файлам с возможностью редактирования](https://www.dropbox.com/en/help/19).

## <a name="share-data-in-onedrive"></a>Совместное использование данных в OneDrive
1. Войдите в OneDrive, используя ту же учетную запись, которая использовалась при создании подключения из Power apps к OneDrive.
2. Выберите папку, содержащую файл, а затем выберите **Общий доступ**.  
   
    ![Пункт "Совместный доступ"](./media/share-app-data/onedrive-share.png)
   
    > [!NOTE]
   > В OneDrive для бизнеса следует предоставлять общий доступ к самому файлу, а не папке, в которой он содержится.
3. В диалоговом окне выберите **Электронная почта**.
   
    ![Отправить по электронной почте](./media/share-app-data/onedrive-email.png)
4. Укажите электронные адреса, с помощью которых пользователи приложения входят в OneDrive, и выберите **Общий доступ**.  
   
    ![Указание пользователя](./media/share-app-data/onedrive-perms.png)

Дополнительные сведения см. в разделе [Общий доступ к файлам и папкам OneDrive](https://support.office.com/article/Share-OneDrive-files-and-folders-and-change-permissions-9fcc2f7d-de0c-4cec-93b0-a82024800c07).

## <a name="share-data-in-google-drive"></a>Совместное использование данных на Google Диске
1. Войдите на Google Drive, используя ту же учетную запись, с которой вы создали подключение из Power apps к Google Drive.
2. Щелкните правой кнопкой мыши папку, содержащую файл Excel, а затем выберите **Совместный доступ**.  
   
    ![Пункт "Совместный доступ"](./media/share-app-data/googledrive-share.png)
3. В диалоговом окне введите электронные адреса, с помощью которых пользователи приложения входят в Google Диск.  
   
    ![Указание пользователя](./media/share-app-data/googledrive-perms.png)
4. Если пользователи приложения будут добавлять, изменять или удалять данные в приложении, выберите **Перемещение и изменение** из списка разрешений. В противном случае выберите **Просмотр**.
5. Нажмите кнопку **Готово**.

Дополнительные сведения см. в разделе [Как предоставить доступ к файлам и папкам на Google Диске](https://support.google.com/drive/answer/2494822).

### <a name="known-limitations"></a>Известные ограничения
[Просмотрите эти ограничения](connections/cloud-storage-blob-connections.md#known-limitations) для совместного использовании данных Excel в организации.

