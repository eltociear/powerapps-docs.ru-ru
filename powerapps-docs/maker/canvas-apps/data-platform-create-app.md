---
title: Создание приложения Canvas из Common Data Service | Документация Майкрософт
description: В PowerApps автоматически создает приложение Canvas для управления данными в Common Data Service
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: quickstart
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/06/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f9dedc515ee130a950c1dc12793751d43aa3804f
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "71993085"
---
# <a name="generate-a-canvas-app-from-common-data-service-in-powerapps"></a>Создание приложения Canvas на основе Common Data Service в PowerApps

В PowerApps автоматически создает приложение Canvas на основе списка примеров учетных записей в [Common Data Service](../common-data-service/data-platform-intro.md). В этом приложении можно просматривать все учетные записи, отображать подробные сведения о отдельной записи, а также создавать, изменять и удалять учетные записи.

Если вы не зарегистрированы в PowerApps, перед началом работы [пройдите бесплатную регистрацию](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

## <a name="prerequisites"></a>Технические условия

Для выполнения этого краткого руководства необходимо назначить роль безопасности " [создатель среды](https://docs.microsoft.com/power-platform/admin/database-security#predefined-security-roles) ", и необходимо [переключиться на среду](working-with-environments.md) , в которой создана база данных Common Data Service, содержит данные и допускает обновления. Если такая среда отсутствует и у вас есть права администратора, вы можете [создать среду](https://docs.microsoft.com/power-platform/admin/environments-administration#create-an-environment), отвечающую этим требованиям.

## <a name="generate-an-app"></a>Создание приложения

1. Войдите в [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) и переключитесь на среду, соответствующую указанным выше требованиям.

1. В области **Создавайте собственные приложения** наведите указатель на плитку **Начать с данных** и выберите команду **Создать это приложение**.

    ![Команда для создания приложения](./media/data-platform-create-app/start-from-data.png)

1. На плитке **Common Data Service** выберите **Макет телефона**.

    ![Плитка подключения](./media/data-platform-create-app/connection-tile.png)

1. В поле **Выберите таблицу** выберите **Учетные записи**, а затем щелкните **Подключиться**.

1. Если отобразится диалоговое окно **Вас приветствует PowerApps Studio**, выберите в нем **Пропустить**.

Откроется приложение с окном обзора, в котором приведен список учетных записей в элементе управления, называемом коллекцией. В верхней части экрана в строке заголовка отображаются значки для обновления данных в коллекции, сортировки данных в коллекции в алфавитном порядке и добавления данных в коллекцию. Под заголовком есть поле поиска, с помощью которого можно отфильтровать данные в коллекции по введенному или вставленному тексту. 

По умолчанию в коллекции отображаются адрес электронной почты, город и имя учетной записи. Как вы увидите в разделе [Дальнейшие действия](data-platform-create-app.md#next-steps), будет доступна возможность настройки отображения данных и даже вывода других типов данных в коллекции.

![Экран обзора](./media/data-platform-create-app/browse-screen.png)

## <a name="save-the-app"></a>Сохранение приложения
Прежде чем использовать это приложение или представлять доступ к нему другим пользователям, вам, возможно, потребуется внести в него и другие изменения. Прежде чем продолжить, рекомендуем сохранить результаты работы.

1. В левом верхнем углу экрана выберите вкладку **Файл**.

1. На странице **Параметры приложения** задайте имя приложения **AppGen**, а затем измените цвета фона на темно-красный, а значок — на галочку.

    ![Страница "Параметры приложения"](./media/data-platform-create-app/app-settings.png)

1. Рядом с левым краем экрана выберите **Сохранить**, а затем щелкните **Сохранить** в нижнем левом углу.

## <a name="next-steps"></a>Дальнейшие действия
В этом кратком руководстве вы создали приложение для управления демонстрационными данными об учетных записях в Common Data Service. На следующем шаге мы настроим коллекцию и еще несколько элементов на стандартном экране просмотра в соответствии со своими потребностями.

> [!div class="nextstepaction"]
> [Настройка коллекции](customize-layout-sharepoint.md).
