---
title: Предоставление клиентам тестовых выпусков приложения на основе холста в AppSource | Документы Майкрософт
description: Использование AppSource для предоставления клиентам доступа к приложению на основе холста и привлечения потенциальных клиентов для своего бизнеса.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/08/2017
ms.author: litran
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 324c7880643a6e06bc147d1bbafb1b9638b8f2ec
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731596"
ms.PowerAppsDecimalTransform: true
---
# <a name="let-customers-test-drive-your-canvas-app-on-appsource"></a>Предоставление клиентам тестовых выпусков приложения на основе холста в AppSource

Вы не собираетесь создавать приложения Canvas в Power Apps? Хотите предоставить свое приложение на основе холста для доступа клиентам? [AppSource.com](https://appsource.microsoft.com) поддерживает решения для тестирования устройств Power Apps в качестве способа совместного использования приложений с клиентами и создания интересов для вашего бизнеса.

## <a name="what-is-a-test-drive-solution"></a>Что такое решение для тестирования?

Решение для тестирования позволяет вашим клиентам опробовать реальное приложение без регистрации в плане приложений для Power Apps или установки каких-либо приложений. Клиентам необходимо лишь войти на сайт AppSource.com, используя учетную запись Azure Active Directory (AAD), и запустить приложение в веб-браузере. Если приложение не имеет тестового выпуска, клиенты могут только просматривать сведения и видео о нем. С помощью тестового выпуска клиенты могут лучше понять, что представляет собой ваше решение и какие возможности предоставляет ваше приложение, а также оценить его работу на практике. Пользователи не смогут узнать принцип сборки вашего приложения, поэтому ваша интеллектуальная собственность в безопасности. Мы собираем для вас информацию о потенциальных клиентах, которые используют тестовый выпуск приложения, чтобы помочь развитию вашей компании.

Далее приведен пример [описания приложения](https://go.microsoft.com/fwlink/?linkid=848867) на AppSource.com:

![Пример описания AppSource ](./media/dev-appsource-test-drive/sample-app-source-listing.png)

Перейдя по ссылке на **бесплатную пробную версию** из приведенного выше приложения, вы запустите соответствующее приложение тестового диска Power Apps непосредственно в браузере пользователя:

![Образец веб-проигрывателя](./media/dev-appsource-test-drive/sample-app-web-player.png)

## <a name="how-do-i-build-a-test-drive-solution"></a>Как создать решение для тестирования?
Создание приложения для решения тестового диска аналогично созданию любого приложения в Power Apps, но вместо внешних подключений к данным используются внедренные данные. Использование внедренных данных сокращает барьер развертывания приложения на клиенте, поэтому для их пробного использования не требуется никаких препятствий. Полное решение, которое вы в итоге распространяете клиентам, обычно включает подключения к данным, но внедренные данные хорошо подходят для решения тестового диска.

Power Apps изначально поддерживает создание приложений с внедренными данными, поэтому для использования в приложении нужны только образцы данных. Данные должны содержаться в одной или нескольких таблицах в файле Excel. В Power Apps вы затем извлекаете данные из таблиц Excel в приложение и работаете с ним, а не через внешнее подключение. Ознакомьтесь с трехэтапной процедурой ниже, чтобы переместить данные и использовать их в приложении.

### <a name="step-1-import-data-into-the-app"></a>Шаг 1. Импорт данных в приложение
Предположим, что у вас есть две таблицы в файле Excel: **SiteInspector** и **SitePhotos**.

![Таблицы Excel, которые необходимо импортировать](./media/dev-appsource-test-drive/excel-file.png)

Импортируйте эти две таблицы в Power Apps с помощью параметра **добавить статические данные в приложение**.

![Добавление статических данных в приложение](./media/dev-appsource-test-drive/static-data.png)

Теперь таблицы добавлены в приложение в качестве источников данных.

![Таблицы Excel как импортированные источники данных](./media/dev-appsource-test-drive/data-sources.png)

### <a name="step-2-handling-read-only-and-read-write-scenarios"></a>Шаг 2. Обработка сценариев только для чтения и сценариев для чтения и записи
Импортированные данные являются *статическими* и доступны только для чтения. Если приложение доступно только для чтения (т. е. оно только отображает данные для пользователя), запрашивайте таблицы непосредственно в приложении. Например, если требуется получить доступ к полю **Заголовок** в таблице **SiteInspector**, используйте **SiteInspector.Title** в формуле.

Если приложение доступно для чтения и записи, сначала извлекаются данные из каждой таблицы в *коллекцию*, которая представляет собой табличную структуру данных в Power Apps. Затем вместо таблицы используйте коллекцию. Чтобы переместить данные из таблиц **SiteInspector** и **SitePhotos** в коллекции **SiteInspectorCollect** и **SitePhotosCollect**, используйте следующую формулу:

```powerapps-comma
ClearCollect( SiteInspectorCollect; SiteInspector );; 
ClearCollect( SitePhotosCollect; SitePhotos )
```

С помощью этой формулы можно очистить обе коллекции, а затем переместить данные из каждой таблицы в соответствующую коллекцию.

* Вызовите эту формулу где-нибудь в приложении, чтобы загрузить данные.
* Просмотрите все коллекции в приложении, выбрав **Файл** > **Коллекции**.
* Дополнительные сведения см. в статье [Создание и обновление коллекции в приложении](../canvas-apps/create-update-collection.md).

Теперь, чтобы получить доступ к полю **Заголовок**, используйте в формуле **SiteInspectorCollect.Title**.

### <a name="step-3-add-update-and-delete-data-in-your-app"></a>Шаг 3. Добавление, обновление и удаление данных в приложении
Вы научились считывать данные напрямую и из коллекции. Теперь мы покажем, как добавить, обновить и удалить данные в коллекции.

**Чтобы добавить строку в коллекцию**, используйте [Collect( DataSource, Item, ... )](../canvas-apps/functions/function-clear-collect-clearcollect.md):

```powerapps-comma
Collect( SiteInspectorCollect;
    {
        ID: Value( Max( SiteInspectorCollect; ID ) + 1 );
        Title: TitleText.Text;
        SubTitle: SubTitleText.Text;
        Description: DescriptionText.Text
    }
)
```

**Чтобы обновить строку в коллекции**, используйте [UpdateIf( DataSource, Condition1, ChangeRecord1 [, Condition2, ChangeRecord2, ...] )](../canvas-apps/functions/function-update-updateif.md):

```powerapps-comma
UpdateIf( SiteInspectorCollect;
    ID = record.ID;
    {
        Title: TitleEditText.Text;
        SubTitle: SubTitleEditText.Text;
        Description: DescriptionEditText.Text
    }
)
```

**Чтобы удалить строку из коллекции**, используйте [RemoveIf( DataSource, Condition [, ...] )](../canvas-apps/functions/function-remove-removeif.md):

```powerapps-comma
RemoveIf( SiteInspectorCollect; ID = record.ID )
```

> [!NOTE]
> Коллекции хранят данные только во время выполнения приложения. При закрытии приложения все изменения будут утеряны.

Таким образом, вы можете создать версию приложения с внедренными данными, что имитирует работу приложения при подключении к внешним данным. После внедрения данных вы сможете опубликовать это приложение как решение для тестирования на сайте AppSource.com.

## <a name="how-do-i-list-my-test-drive-solution-on-appsourcecom"></a>Как добавить решение для тестирования на сайте AppSource.com?
Теперь, когда приложение готово, его можно опубликовать на сайте AppSource.com. Чтобы начать этот процесс, заполните [форму приложения](https://powerapps.microsoft.com/partners/get-listed/) в Power Apps.com.

После подачи заявки вы получите электронное письмо с инструкциями о том, как отправить приложение для публикации на сайте AppSource.com. Документацию по подключению, в которой полностью описывается этот процесс, можно скачать [отсюда](https://go.microsoft.com/fwlink/?linkid=851031).

