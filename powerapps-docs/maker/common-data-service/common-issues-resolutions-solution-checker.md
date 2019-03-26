---
title: Общие проблемы и их разрешение для средства проверки решений | Microsoft Docs
description: ' Список общих проблем и их разрешения для средства проверки решений'
keywords: ''
ms.date: 02/11/2019
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: caa4e3f2-9700-49b8-87ed-8a68e8878b02
author: jowells1
ms.author: jowells
manager: austinj
ms.reviewer: null
robots: 'noindex,nofollow'
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# Общие проблемы и их разрешение для средства проверки решений

В данной статье перечислены некоторые общие проблемы, которые могут возникнуть при использовании средства проверки решений. Где применимо, представлены временные способы решения.

## Запуск средства проверки решений завершается сбоем из-за установленной версии средства проверки PowerApps
Средство проверки решений входит в состав решения "Средство проверки PowerApps".  Если установлена версия средства проверки PowerApps до 1.0.0.47, работа средства проверки решений не будет завершаться успешно. Необходимо выполнить обновление версии средства проверки PowerApps из [!INCLUDE [pn-dyn-365-admin-center](../../includes/pn-dyn-365-admin-center.md)]. 

Однако если установлена версия средства проверки PowerApps до 1.0.0.45, рекомендуется удалить решение и установить его снова. В связи с недавними изменения схем обновление средства проверки PowerApps с версий до 1.0.0.45 может закончиться неудачей.

Если требуется сохранить прошлые результаты из средства проверки решений, экспортируйте результаты из предыдущих выполнений или экспортируйте все данные средства проверки решений с помощью функции [Экспорт данных в Excel](../../user/export-data-excel.md), чтобы экспортировать данные из следующих сущностей:

- Компонент анализа
- Задание анализа
- Результат анализа
- Подробность результата анализа

### Удаление средства проверки PowerApps

Чтобы удалить решение средства проверки PowerApps:

1. Как системный администратор или настройщик системы, откройте портал PowerApps, перейдя по адресу https://web.powerapps.com/environments.
2. Выберите **Решения**.
3. Выберите **Средство проверки PowerApps**, затем на панели инструментов решений выберите **Удалить**.

### Добавление средства проверки PowerApps

Чтобы добавить средство проверки PowerApps обратно в вашу среду CDS для приложений:

1. Как системный администратор или настройщик системы, откройте портал PowerApps, перейдя по адресу https://web.powerapps.com/environments.
2. Выберите **Решения**.
3. На панели инструментов выберите **Средство проверки PowerApps**, затем выберите **Установить**.

## Запуски на крупных решениях приводят к сбоям

Средство проверки решений имеет 10-минутное время ожидание для экспорта решения из среды Common Data Service (CDS) для приложений. Большие решения, такие как решение по умолчанию, могут не успеть экспортироваться в течение этого времени, и проверка не завершится успешно. Средство проверки решений выполнит три попытки перед сбоем обработки задания, поэтому вы можете получить уведомление об ошибке только через 30 минут или более.

Чтобы решить эту проблему, проверяйте или создавайте для анализа решения меньшего размера. Чтобы свести к минимуму ложные срабатывания, обязательно добавляйте зависимые настройки. При создании решения и добавлении таких компонентов включайте следующее:

- При добавлении подключаемых модулей включите шаги обработки сообщения SDKдля подключаемого модуля.
- При добавлении форм сущностей включите веб-ресурсы JavaScript, прикрепленные к событиям формы.  
- При добавлении веб-ресурсов JavaScript включите все зависимые веб-ресурсы JavaScript.
- При добавлении веб-ресурсов HTML включить все зависимые сценарии, которые определены в веб-ресурсе HTML.
- При добавлении пользовательских бизнес-процессов включите сборку, используемую в бизнес-процессе.

## Работа средства проверки решений или скачивание результатов не завершается 
Вскоре после запуска средства проверки решений работа не завершается и отображается следующее сообщение:<br />
"Не удалось выполнить проверку для решения *ИМЯ_РЕШЕНИЯ*. Попробуйте запустить повторно". <br />
![![Не удалось выполнить](media/solution-checker-werent-able-to-run.png)](media/solution-checker-werent-able-to-run.png)

Эта проблема возникает, потому что организация находится в состоянии **административного режима**, и средство проверки решений не может проверить полномочия пользователя, выполняющего запрос. Чтобы устранить эту проблему, отключите режим администрирования. 

### Отключение режима администрирования для экземпляра
1. Откройте средство выбора экземпляра Dynamics 365 for Customer Engagement: https://port.crm.dynamics.com/G/Instances/InstancePicker.aspx.
2. Выберите экземпляр, имеющий проблемы выполнения средства проверки решений.
3. Выберите **ADMIN**.<br />
![![Администратор экземпляра](media/solution-checker-instance-admin.png)](media/solution-checker-instance-admin.png)

4. Снимите флажок **Включить режим администрирования**. <br />
![![Отключение режима администрирования](media/solution-checker-instance-disable-admin-mode.png)](media/solution-checker-instance-disable-admin-mode.png)

5. Снова запустите средство проверки решений.

## Средство проверки решений не обрабатывает исправленные решения

Если к решению было применено [исправление](https://docs.microsoft.com/powerapps/developer/common-data-service/create-patches-simplify-solution-updates), средство проверки решений не сможет экспортировать решение для анализа. Когда к решению было применено исправление, первоначальное решение будет заблокировано, и его нельзя изменить или экспортировать, если имеются зависимые исправления в организации, которые определяют это решение как родительское решение.

Для исправления этой проблемы клонируйте решение, чтобы все исправления, связанные с решением, были свернуты во вновь созданное решение. Это разблокирует решение и позволит экспортировать решение из системы. Дополнительные сведения: [Клонирование решения](use-segmented-solutions-patches-simplify-updates.md#clone-a-solution)

## Ссылки по номерам строк для проблем в ресурсах HTML с внедренным кодом JavaScript неправильные 

Когда веб-ресурсы HTML обрабатываются в средстве проверки решений, веб-ресурс HTML обрабатывается отдельно от кода JavaScript в веб-ресурсе HTML. В связи с этим номер строки нарушения, найденного внутри элемента `<script>` веб-ресурса HTML, будет неправильным.

## Проблема неподдерживаемого в интернете синтаксиса для веб-ресурсов

Версии ECMAScript 6 (2015) или более поздние в настоящее время не поддерживаются для средства проверки решений. Когда средство проверки решений анализируйте JavaScript с использованием ECMAScript 6 или выше, возникает сообщение об ошибке поддерживаемого в интернете синтаксиса для веб-ресурса.  

## См. также
[[Рекомендации и советы для Common Data Service для приложений](../../developer/common-data-service/best-practices/index.md)](../../developer/common-data-service/best-practices/index.md)<br />
[[Рекомендации и советы для управляемых моделью приложений](../../developer/model-driven-apps/best-practices/index.md)](../../developer/model-driven-apps/best-practices/index.md)<br />