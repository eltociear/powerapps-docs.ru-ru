---
title: 'Предварительная версия: использование переменных среды в решениях | MicrosoftDocs'
description: Используйте переменные среды для переноса данных конфигурации приложений в решениях.
Keywords: переменные среды, переменные, приложение на основе модели, данные конфигурации
author: caburk
ms.author: caburk
manager: kvivek
ms.date: 10/22/2019
ms.service: powerapps
ms.topic: article
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f0c3189fceebb785a022d04c58ff6cf71fd388bc
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "2758295"
---
# <a name="preview-environment-variables-overview"></a>Предварительная версия: обзор переменных среды 

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Приложения и потоки часто требуют различных параметров конфигурации в средах. Переменные среды как настраиваемые входные параметры позволяют управлять данными отдельно по сравнению с жестким кодированием значений в настройке или с помощью дополнительных средств. Поскольку это компоненты решений, производительность намного лучше, чем при импорте данных конфигурации как данных записи.

Преимущества использования переменных среды:
- Не нужно вручную изменять конфигурируемые значения в производственной среде.
- Установите одну или несколько переменных в одном месте и ссылайтесь как на параметр в нескольких компонентах решений.
- Обновление значений без изменения кода.
- Безопасность на детальных уровнях, управляемая [Common Data Service](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-intro).
- Неограниченное число переменных (максимальный размер решения 29 МБ).
- Обслуживание определений и значений независимо или вместе.
- Поддерживается средствами [SolutionPackager](/powerapps/developer/common-data-service/compress-extract-solution-file-solutionpackager) и [DevOps](/powerapps/developer/common-data-service/build-tools-overview) и обеспечивает непрерывную интеграцию и непрерывную доставку (CI/CD).
- Поддержка локализации.
- Может использоваться для управления флагами функций и другими параметрами приложения.

> [!IMPORTANT]
> - Это функция для предварительного ознакомления.
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)] 

## <a name="how-they-work"></a>Как они работают?
Переменные среды могут создаваться и управляться через интерфейс современного решения или [с помощью кода](https://docs.microsoft.com/powerapps/developer/common-data-service/work-with-data-cds). Отдельный файл JSON создается в пакете решения для значений, которыми можно также управлять в элементе управления источника и изменены в конвейере сборки. Экспорт в Excel и импорт из него поддерживаются. После создания переменных среды можно использовать их в качестве входных данных в подключаемых модулях, потоках и других компонентах.

## <a name="default-value"></a>Значение по умолчанию
Это поле является частью сущности определения переменной среды и не является обязательным. Задайте значение по умолчанию для производственных сред или если значения не требуется изменять для разных сред.

## <a name="value"></a>Значение
Также известно как текущее значение или значение переопределения, этом поле необязательно и является частью сущности значения переменной среды. Задайте значение, если нужно переопределить значение по умолчанию в текущей среде. Удалите значение из своего решения, если не хотите использовать его в следующей среде. Значения также разделены в отдельный файл JSON в файле solution.zip, который экспортируется. 

>[!NOTE]
> Значение не может существовать без определения. Интерфейс позволяет только создавать одно значение на определение. 

Разделение значения по умолчанию и текущего значения позволяет обслуживать определение и значение по умолчанию отдельно от текущей значения. Оно также позволяет нам расширить функциональность в будущем, чтобы поддерживать несколько значений, ограниченных определенным контекстом времени выполнения.

## <a name="notifications"></a>Уведомления
Уведомление отображается, когда переменные среды не имеются никаких значений. Это напоминание установить значения, так чтобы компоненты, зависимые от переменных, не давали сбой. Оно также позволяет партнерам поставлять переменные без значений, и клиенту предлагается ввести значения.

>[!NOTE]
> Рекомендуется партнерам создавать собственные интерфейсы, требующие, чтобы клиенты ввели значения. Уведомления позволяют избежать сбоев, если этот шаг пропущен. 

## <a name="security"></a>Безопасность
Обе сущности environmentvariabledefinition и environmentvariablevalue [принадлежат пользователю или рабочей группе](https://docs.microsoft.com/powerapps/maker/common-data-service/types-of-entities). При создании приложения, которое использует переменные среды, следует назначить пользователям соответствующий уровень прав. Дополнительные сведения: [Безопасность в Common Data Service](https://docs.microsoft.com/power-platform/admin/wp-security). 

## <a name="current-limitations"></a>Текущие ограничения
- Кэширование. Подключаемым модулям потребуется выполнить запрос для извлечения значений. 
- Приложения холста и потоки могут использовать переменные среды как данные записи сущности. В будущем мы планируем создать другие действия в конструкторах приложений холста и потоков. Это упростит создание и обеспечит лучшую видимость переменных среды, используемых определенным приложением или потоком.
- Интеграция Azure Key Vault для управления секретами. В настоящее время переменные среды не должны использоваться для хранения безопасных данных, таких как пароли и ключи.
- Типы данных проверяются только в современном интерфейсе решений, но не на сервере в ходе предварительного просмотра. 
- Зависимости не накладываются принудительно для некоторых типов компонентов.
- При использовании Excel для импорта переменных среды необходимо заранее добавить префикс издателя в SchemaName.

### <a name="see-also"></a>См. также
[Использование подключаемых модулей для расширения бизнес-процессов](https://docs.microsoft.com/powerapps/developer/common-data-service/plug-ins) </BR>
[Примеры веб-API](https://docs.microsoft.com/powerapps/developer/common-data-service/webapi/web-api-samples) </BR>
[Создание приложений холста с нуля с помощью Common Data Service.](https://docs.microsoft.com/powerapps/maker/canvas-apps/data-platform-create-app-scratch) </BR>
[Создание потока с Common Data Service](https://docs.microsoft.com/flow/connection-cds)