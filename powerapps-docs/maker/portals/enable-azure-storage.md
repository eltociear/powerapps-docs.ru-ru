---
title: Включение хранилища Azure для порталов | MicrosoftDocs
description: Инструкции по включению службы хранилища Azure для порталов, чтобы воспользоваться преимуществами больших возможностей хранения файлов в Azure.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3da40cfdcb88726384218c4b1df370c301f8ac16
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759923"
---
# <a name="enable-azure-storage"></a>Включение хранилища Azure

Интеграция хранилища Azure для порталов позволяет воспользоваться большим объемом хранилища файлов Azure, используя тот же интерфейс и предоставляя то же взаимодействие с пользователем, что и для вложений файлов по умолчанию. Эта функция поддерживается для веб-файлов, форм сущностей и веб-форм.

Необходимо создать учетную запись хранилища, используя **Диспетчер ресурсов** в качестве модели развертывания. [!include[More information](../../includes/proc-more-information.md)] [Создание учетной записи хранилища Azure](https://docs.microsoft.com/azure/storage/storage-create-storage-account#create-a-storage-account).

После запуска учетной записи хранилища порталам требуются определенные глобальные параметры, которые будут указывать приложению, каким образом искать учетную запись хранилища. В приложении управления порталом перейдите в раздел **Параметры** > **Создать** и добавьте новый параметр с именем **FileStorage/CloudStorageAccount**.

> [!NOTE]
> Максимальный размер отправляемого файла: 125 МБ.

Чтобы найти значение для FileStorage/CloudStorageAccount, необходимо получить строку подключения от [!include[Azure portal](../../includes/pn-azure-portal.md)].

1. Выполните вход в [!include[Azure portal](../../includes/pn-azure-portal.md)].

2. Перейдите к учетной записи хранилища.

3. Выберите **Клавиши доступа**.

    ![Поиск значения для строки подключения от портала Azure](media/key-azure-storage.png "Поиск значения для строки подключения от портала Azure")

4. На полученной панели найдите поле с именем **Строка подключения**. Выберите значок **Копировать** рядом с полем, для которого необходимо скопировать значение, а затем вставьте это значение в новый параметр:

    ![Значение строки основного подключения](media/primary-connection-string-azure-storage.png "Значение строки основного подключения")

    ![Параметр портала для учетной записи облачного хранилища](media/portal-site-setting-cloud-storage-account.png "Параметр портала для учетной записи облачного хранилища")

## <a name="specify-the-storage-container"></a>Указание контейнера хранилища

Если у вас еще нет контейнера BLOB-объектов Azure в учетной записи хранилища, его необходимо добавить с помощью [!include[Azure portal](../../includes/pn-azure-portal.md)].

В [приложении управления порталом](configure/configure-portal.md) перейдите в раздел **Параметры** > **Создать** и добавьте новый параметр с именем **FileStorage/CloudStorageContainerName**, используя имя контейнера как значение.

![Параметр портала для контейнера облачного хранилища](media/portal-site-setting-cloud-storage-container.png "Параметр портала для контейнера облачного хранилища")

## <a name="add-cors-rule"></a>Добавление правила CORS

Необходимо добавить правило общего доступа к ресурсам независимо от источника (CORS) в учетной записи службы хранилища Azure, как указано ниже, в противном случае вы увидите обычный значок вложения, а не значок облака:

- **Допустимые источники**: укажите свой домен. Например, contoso.crm.dynamics.com.
- **Разрешенные команды**: GET, PUT, DELETE, HEAD, POST
- **Разрешенные заголовки**: укажите заголовки запросов, которые исходный домен может указывать в запросе CORS. Например, x-ms-meta-data\*, x-ms-meta-target\*. 
- **Предоставляемые заголовки**: укажите заголовки ответов, которые могут отправляться в ответ на запрос CORS браузером инициатору запроса. Например, x-ms-meta-\*.
- **Максимальный возраст (секунды)**: укажите максимальное время, в течение которого браузер должен кэшировать предварительный запрос OPTIONS. Например, 200.
 
[!include[More information:](../../includes/proc-more-information.md)] [Поддержка CORS для служб хранилища Azure](https://docs.microsoft.com/rest/api/storageservices/cross-origin-resource-sharing--cors--support-for-the-azure-storage-services)

## <a name="add-site-settings"></a>Добавление параметров сайта

Добавьте следующие параметры сайта из **Порталы** > **Параметры сайта**. [!include[More information:](../../includes/proc-more-information.md)] [Управление параметрами сайта портала](configure/configure-site-settings.md#manage-portal-site-settings)

|Имя|Значение|
|-----|-----|
|WebFiles/CloudStorageAccount|Предоставьте ту же строку подключения, что была предоставлена для параметра FileStorage/CloudStorageAccount.|
|WebFiles/StorageLocation|AzureBlobStorage|
|||

Теперь можно создать дочерний файл на портале и упомянуть полное имя (вместе с контейнером) в URL-адресе большого двоичного объекта Azure. Благодаря этим параметрам портала позволят отправлять и загружать файлы в хранилище Azure и из него. Однако вы не сможете воспользоваться всеми преимуществами этой функции, пока вы не [добавите веб-ресурс для включения отправки вложений в хранилище Azure](add-web-resource.md) и не настроите [формы сущностей](configure-notes.md#notes-configuration-for-entity-forms) или [веб-формы](configure-notes.md#notes-configuration-for-web-forms) для его использования.

### <a name="see-also"></a>См. также

[Добавление веб-ресурса](add-web-resource.md)

[Настройка примечаний](configure-notes.md)
