---
title: Добавление подключений из приложений на основе холста и управление ими | Документы Майкрософт
description: Добавление, удаление и обновление подключений из приложений на основе холста к таким источникам данных, как SharePoint, SQL Server и OneDrive для бизнеса
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/05/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9b25eef7460098139c32fba5606b682baae2ada9
ms.sourcegitcommit: dc379bede57da58b5787eda5437eb94b662e21ed
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2020
ms.locfileid: "77037503"
---
# <a name="manage-canvas-app-connections-in-power-apps"></a>Управление холстами. подключения приложений в Power Apps
На сайте [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) можно создать или удалить подключение к одному или нескольким источникам данных, а также обновить для него учетные данные.

Приложение на основе холста может подключаться к SharePoint, SQL Server, Office 365, OneDrive для бизнеса, Salesforce, Excel и многим другим [источникам данных](connections-list.md).

Следующий этап после выполнения действий, описанных в этой статье, это вывод данных из источника в приложении и управление ими, как в следующих примерах:

* подключение к OneDrive для бизнеса и управление данными в книге Excel в приложении;
* обновление списка на веб-сайте SharePoint;
* подключение к серверу SQL Server и обновление таблицы из приложения.
* отправка сообщений электронной почты в Office 365;
* отправка твитов.
* Подключение к Twilio и отправка SMS-сообщений из приложения;

## <a name="prerequisites"></a>Предварительные требования
1. [Зарегистрируйтесь](../signup-for-powerapps.md) в Power Apps.
2. Войдите в [make.powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) , используя те же учетные данные, которые использовались для регистрации.

## <a name="background-on-data-connections"></a>Основные сведения о подключениях к данным
Большинство приложений Power Apps используют внешние сведения, называемые **источниками данных** , которые хранятся в облачных службах. Типичный пример — это таблица в файле Excel, который хранится в службе OneDrive для бизнеса. Приложения получают доступ к источникам данных с помощью **подключений**.

Самый распространенный вид источников данных — это таблица, которую можно использовать для получения и хранения информации. Подключения к источникам можно использовать для чтения и записи данных в книгах Microsoft Excel, списках SharePoint, таблицах SQL и во многих ресурсах других форматов, которые могут храниться в облачных службах, таких как OneDrive для бизнеса, DropBox, SQL Server и другие.

Существуют и другие типы источников данных, не являющиеся таблицами, например электронная почта, календари, Twitter и уведомления.

С помощью элементов управления **[Коллекция](controls/control-gallery.md)** , **[Форма отображения](controls/control-form-detail.md)** и **[Форма редактирования](controls/control-form-detail.md)** можно крайне просто создать приложение, которое считывает и записывает данные из источника данных. Чтобы начать работу, ознакомьтесь со статьей о [формах данных](working-with-forms.md).

Помимо создания подключений и управления ими на сайте [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), создать подключение также можно перечисленными ниже способами.

* Создайте [приложение на основе данных](app-from-sharepoint.md) автоматически, например пользовательский список SharePoint.
* Обновите существующее приложение или создайте новое, как описано в статье о [добавлении подключения](add-data-connection.md).
* Откройте приложение, которое создал и к которому [предоставил вам доступ](share-app.md) другой пользователь.

> [!NOTE]
> Если вместо этого вы хотите использовать Power Apps Studio, откройте меню **файл** , а затем выберите **подключения**. [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) откроется, чтобы можно было создавать подключения и управлять ими.

## <a name="create-a-new-connection"></a>Создание подключения
1. Войдите в [make.powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), если вы еще этого не сделали.
2. В левой области навигации разверните **данные** и выберите **подключения**.
   
    ![Управление подключениями](./media/add-manage-connections/open-connections.png)
3. Выберите **создать соединение**.
   
    ![Добавление подключений](./media/add-manage-connections/add-connection.png)
4. Выберите соединитель в появившемся списке и следуйте инструкциям на экране.
   
   ![Добавление подключений](./media/add-manage-connections/choose-connection.png)
5. Нажмите кнопку **создать** .
   
   ![Добавление подключений](./media/add-manage-connections/create-connection.png)
6. Следуйте инструкциям. Некоторые соединители предлагают ввести учетные данные, указать определенный набор данных или выполнить другие действия. Другие, например **Microsoft Translator**, не делают этого.
   
   Например, для этих соединителей потребуется указать дополнительные сведения, прежде чем вы сможете их использовать.
   
   * [SharePoint](connections/connection-sharepoint-online.md)
   * [SQL Server](connections/connection-azure-sqldatabase.md)

Новый соединитель отобразится в разделе **Connections** (Подключения), и вы сможете [добавить его в приложение](add-data-connection.md).

## <a name="update-or-delete-a-connection"></a>Обновление или удаление подключения
В списке подключений Найдите подключение, которое необходимо обновить или удалить, а затем нажмите кнопку с многоточием (...) справа от подключения.

![Обновление подключения](./media/add-manage-connections/auth-or-delete.png)

* Чтобы обновить учетные данные для подключения, щелкните значок ключа, а затем укажите учетные данные для этого подключения.
* Чтобы удалить подключение, выберите Удалить.
* Щелкните значок сведений, чтобы просмотреть сведения о подключении.

