---
title: Добавление подключений из приложений на основе холста и управление ими | Документы Майкрософт
description: Добавление, удаление и обновление подключений из приложений на основе холста к таким источникам данных, как SharePoint, SQL Server и OneDrive для бизнеса
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 03/09/2017
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d2a7da93835e5fbe588a8683bbdb0393d5b76ee5
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61564358"
---
# <a name="manage-canvas-app-connections-in-powerapps"></a>Управление подключениями из приложений на основе холста в PowerApps
На сайте [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) можно создать или удалить подключение к одному или нескольким источникам данных, а также обновить для него учетные данные.

Приложение на основе холста может подключаться к SharePoint, SQL Server, Office 365, OneDrive для бизнеса, Salesforce, Excel и многим другим [источникам данных](connections-list.md).

Следующий этап после выполнения действий, описанных в этой статье, это вывод данных из источника в приложении и управление ими, как в следующих примерах:

* подключение к OneDrive для бизнеса и управление данными в книге Excel в приложении;
* обновление списка на сайте SharePoint;
* подключение к серверу SQL Server и обновление таблицы из приложения.
* отправка сообщения электронной почты в Office 365;
* отправка твита.
* Подключение к Twilio и отправка SMS-сообщений из приложения;

## <a name="prerequisites"></a>Технические условия
1. [Зарегистрируйтесь](../signup-for-powerapps.md) в PowerApps.
2. Войдите в [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), используя те же учетные данные, которые вы ввели при регистрации.

## <a name="background-on-data-connections"></a>Основные сведения о подключениях к данным
Большинство приложений PowerApps используют внешние сведения (**источники данных**), хранящиеся в облачных службах. Типичный пример — это таблица в файле Excel, который хранится в службе OneDrive для бизнеса. Приложения получают доступ к источникам данных с помощью **подключений**.

Самый распространенный вид источников данных — это таблица, которую можно использовать для получения и хранения информации. Подключения к источникам можно использовать для чтения и записи данных в книгах Microsoft Excel, списках SharePoint, таблицах SQL и во многих ресурсах других форматов, которые могут храниться в облачных службах, таких как OneDrive для бизнеса, DropBox, SQL Server и другие.

Существуют и другие типы источников данных, которые не являются таблицами, например электронные сообщения, календари, Twitter и уведомления (ожидаются в ближайшее время),

С помощью элементов управления **[Gallery](controls/control-gallery.md)** (Коллекция), **[Display form](controls/control-form-detail.md)** (Форма отображения) и **[Edit form](controls/control-form-detail.md)** (Форма изменения) можно легко создать приложение, которое считывает и записывает данные из источника данных. Чтобы начать работу, ознакомьтесь со статьей о [формах данных](working-with-forms.md).

Помимо создания подключений и управления ими на сайте [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), создать подключение также можно перечисленными ниже способами.

* Создайте [приложение на основе данных](app-from-sharepoint.md) автоматически, например пользовательский список SharePoint.
* Обновите существующее приложение или создайте новое, как описано в статье о [добавлении подключения](add-data-connection.md).
* Откройте приложение, которое создал и к которому [предоставил вам доступ](share-app.md) другой пользователь.

> [!NOTE]
> В PowerApps Studio можно открыть меню **Файл** и выбрать пункт **Подключения**. Откроется сайт [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), на котором можно создавать подключения и управлять ими.

## <a name="create-a-new-connection"></a>Создание подключения
1. Если вы еще не сделали этого, войдите на сайт [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
2. На панели навигации слева щелкните или нажмите **Connections** (Подключения).
   
    ![Управление подключениями](./media/add-manage-connections/open-connections.png)
3. В правом верхнем углу экрана нажмите кнопку **New connection** (Создать подключение).
   
    ![Добавление подключений](./media/add-manage-connections/add-connection.png)
4. В открывшемся списке выберите соединитель, а затем следуйте указаниям.
   
   ![Добавление подключений](./media/add-manage-connections/choose-connection.png)
5. Нажмите кнопку **Create** (Создать).
   
   ![Добавление подключений](./media/add-manage-connections/create-connection.png)
6. Следуйте инструкциям. Некоторые соединители предлагают ввести учетные данные, указать определенный набор данных или выполнить другие действия. Другие, например **Microsoft Translator**, не делают этого.
   
   Например, для этих соединителей потребуется указать дополнительные сведения, прежде чем вы сможете их использовать.
   
   * [SharePoint](connections/connection-sharepoint-online.md)
   * [SQL Server](connections/connection-azure-sqldatabase.md)

Новый соединитель отобразится в разделе **Connections** (Подключения), и вы сможете [добавить его в приложение](add-data-connection.md).

## <a name="update-or-delete-a-connection"></a>Обновление или удаление подключения
В списке подключений выберите то, которое хотите удалить или обновить, а затем щелкните или нажмите на значок многоточия справа от него.

![Обновление подключения](./media/add-manage-connections/auth-or-delete.png)

* Чтобы обновить учетные данные для подключения, щелкните или нажмите на значок ключа и введите новые значения.
* Чтобы удалить подключение, выберите значок корзины.

