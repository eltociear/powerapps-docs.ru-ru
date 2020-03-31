---
title: Создание приложения Canvas из базы данных SQL Azure | Документация Майкрософт
description: Описание процесса создания приложения Canvas на основе данных в базе данных SQL Azure
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/30/2020
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c17fff957091a13e26e4bbbb3bc90f34fa5659f7
ms.sourcegitcommit: 204d73f30be2fd63e13e3c64cbfa62b8d667df33
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2020
ms.locfileid: "80406093"
---
# <a name="preview-create-a-canvas-app-from-azure-sql-database"></a>Предварительная версия: создание приложения Canvas из базы данных SQL Azure

[В этой статье содержится предварительная версия сведений, которые могут быть изменены в последующих выпусках.]

В этом разделе вы будете использовать данные в базе данных SQL Azure для создания приложения с Power Apps за считаные минуты. Вы получите полностью функциональное приложение с данными, которые можно настроить в соответствии с потребностями бизнеса и поделиться на любом устройстве.

> [!IMPORTANT]
> - Это ознакомительная версия функции.
> - Функция предварительной версии может иметь ограниченную доступность и функциональность. Доступ к этой предварительной версии функции предоставляется до официального выпуска, чтобы клиенты могли оценить их и отправить отзыв.

## <a name="prerequisites"></a>Предварительные требования

- В браузере должны быть включены всплывающие окна.
- Вам нужна подписка Azure. </br>Если у вас нет подписки Azure, [Создайте бесплатную учетную запись](https://azure.microsoft.com/free/).
- Необходим доступ к существующей базе данных SQL. </br> Если у вас нет существующей базы данных SQL, [Создайте новую базу данных](https://docs.microsoft.com/azure/sql-database/sql-database-single-database-get-started?tabs=azure-portal).
- Вам нужно разрешить [IP-адрес](#app-access-to-sql-database) региона Power Apps или доступ служб Azure к базе данных SQL в параметрах брандмауэра.
- В таблице базы данных SQL должен быть хотя бы один столбец с типом данных Text.

## <a name="create-an-app-from-azure-portal"></a>Создание приложения из портал Azure

> [!TIP]
> Вы также можете создать приложение, которое использует базу данных SQL Azure из [Power Apps](https://make.powerapps.com). Дополнительные сведения см. в статье [SQL Server Connector для Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/connections/connection-azure-sqldatabase).

1. Войдите в [портал Azure](https://portal.azure.com).
2. Перейдите к базе данных SQL.
3. Выберите Power Apps.
    
    ![Параметры Power Apps в параметрах базы данных SQL](./media/app-from-azure-sql-database/powerapps-link-azure-portal.png "Параметр Power Apps в базе данных SQL")

4. Введите имя приложения, например "Проверка сайта", "благотворительность" или "средство мониторинга бюджета".

5. Введите пароль проверки подлинности SQL и при необходимости измените имя пользователя.
    
    > [!NOTE]
    > Если вы хотите использовать встроенную проверку подлинности Azure AD вместо проверки подлинности SQL с базой данных SQL Azure, создайте приложение из [приложения Power Apps](https://make.powerapps.com) и используйте [соединитель SQL Server](https://docs.microsoft.com/powerapps/maker/canvas-apps/connections/connection-azure-sqldatabase).

6. Выберите таблицу из раскрывающегося списка, которую нужно использовать для создания приложения.

7. Выберите **Создать**.


    ![Укажите сведения о приложении](./media/app-from-azure-sql-database/powerapps-create-page-azure-portal.png "Укажите сведения о приложении")

    [Приложение Power Apps Studio](https://create.powerapps.com/studio/) откроется на новой вкладке. Если всплывающее окно заблокировано, обновите браузер, чтобы разрешить всплывающие окна, и повторите попытку. После создания вы получите 3-страничное приложение с данными из базы данных SQL.

## <a name="accessing-your-app"></a>Доступ к приложению

Чтобы снова получить доступ к созданному приложению, перейдите по адресу [make.powerapps.com](https://make.powerapps.com).

## <a name="app-environment-and-region"></a>Среда и регион приложения

Приложение, создаваемое с помощью этого метода, использует [среду по умолчанию](https://docs.microsoft.com/power-platform/admin/environments-overview#the-default-environment) для клиента и развертывается в регионе этого окружения. Регион развернутого приложения или среды по умолчанию вашего клиента можно найти в [центре администрирования](https://docs.microsoft.com/power-platform/admin/regions-overview#how-do-i-find-out-where-my-app-is-deployed). Чтобы проверить все приложения в определенной среде, перейдите по адресу [make.powerapps.com](https://make.powerapps.com), выберите **среду** на ленте, а затем выберите **приложения** слева.

## <a name="app-access-to-sql-database"></a>Доступ приложения к базе данных SQL

Вы можете настроить Power Apps для подключения к базе данных SQL с помощью IP-адресов или службы Azure.

### <a name="app-access-using-ip-address"></a>Доступ к приложению по IP-адресу

[Требования к системе для Power Apps](limits-and-config.md#ip-addresses) список IP-адресов, используемых приложениями Power Apps в зависимости от региона приложения.

Для настройки этого доступа можно использовать либо хранимую процедуру Transact-SQL, либо портал Azure.

- [Sp_set_firewall_rule](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database?view=azuresqldb-current) хранимых процедур для базы данных SQL или SQL Server правил брандмауэра
- [Портал Azure](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure) для SQL Server правил брандмауэра

### <a name="app-access-as-an-azure-service"></a>Доступ к приложениям как к службе Azure

Power Apps может подключаться к базе данных SQL, **разрешающей доступ к службе управления службами Azure** с помощью портал Azure. Чтобы настроить этот доступ, войдите в [портал Azure](https://portal.azure.com/) и перейдите на портале, чтобы **SQL Server**. Выберите **брандмауэры и виртуальные сети** и настройте элемент управления **Разрешить службам и ресурсам Azure доступ к этому серверу** **.** Нажмите кнопку **сохранить** , чтобы отправить изменения.

> [!IMPORTANT]
> Если оставить для элемента управления значение Вкл., сервер базы данных SQL Azure будет принимать данные из любой подсети в границах Azure, которая исходит от одного из IP-адресов, распознаваемых в диапазонах, определенных для центров обработки данных Azure. При включении элемента управления в значение ON может возникнуть чрезмерный доступ с точки зрения безопасности.

## <a name="limitations"></a>Ограничения

- Имя приложения может содержать только буквы, цифры, дефисы, круглые скобки и символы подчеркивания.
- Для создания приложения из портал Azure требуется проверка подлинности SQL.
- При создании приложения Canvas из портал Azure можно выбрать только одну таблицу. Настройте приложение после создания приложения, если требуется добавить дополнительные таблицы и другие источники данных, добавив дополнительные подключения к данным.
- Power Apps не удается подключиться к базе данных SQL с помощью конечных точек службы виртуальной сети. Дополнительные сведения см. в статье [разрешение доступа через конечные точки службы виртуальной сети](https://docs.microsoft.com/azure/sql-database/sql-database-vnet-service-endpoint-rule-overview).

## <a name="other-considerations"></a>Другие рекомендации

- Доступ приложения к базе данных SQL неявно предоставляется всем пользователям, которым вы предоставляете доступ к [этому приложению](share-app.md) . Убедитесь, что учетные данные проверки подлинности SQL имеют соответствующий доступ для чтения и записи данных. </br> Например, можно создать отдельное приложение, которое подключается к той же базе данных SQL с разными учетными данными для проверки подлинности SQL, чтобы разделить доступ на чтение и чтение и запись.
- Ознакомьтесь с ограничениями регулирования, делегированными функциями и операциями, известными проблемами и ограничениями соединителя [базы данных SQL](https://docs.microsoft.com/connectors/sql/) , которые эта функция использует для обеспечения производительности.
- Создайте приложение из [make.powerapps.com](https://make.powerapps.com) , когда необходимо создать приложение для среды, отличной от используемой по умолчанию, и другой регион для клиента, использующего данные из базы данных SQL.

## <a name="next-steps"></a>Следующие шаги

В качестве следующего шага используйте [Power Apps](https://make.powerapps.com) Studio для настройки приложения, добавив дополнительные элементы управления, образы и логику в соответствии с бизнес-потребностями.

> [!div class="nextstepaction"]
> [Проектирование интерфейса приложения Canvas в Power Apps](add-configure-controls.md)

## <a name="see-also"></a>См. также:

- [Совместное использование приложения Canvas в Power Apps](share-app.md) </br>
- [Добавление подключения к данным в приложение Canvas в Power Apps](add-data-connection.md#add-data-source)</br>
- [Microsoft Learn: Настройка приложения Canvas в Power Apps](https://docs.microsoft.com/learn/modules/customize-apps-in-powerapps/)
