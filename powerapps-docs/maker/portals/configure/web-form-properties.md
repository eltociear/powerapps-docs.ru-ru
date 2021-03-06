---
title: Настройка свойств веб-формы для портала | MicrosoftDocs
description: Инструкции по настройке свойств веб-форм для портала.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 31e7dd819ba274a70a4c07bf7a21721a7cfa1f76
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "3125280"
---
# <a name="define-web-form-properties-for-portals"></a>Определение свойств веб-формы для порталов

Веб-форма содержит отношения с веб-страницами и начальный шаг для управления инициализацией формы на портале. Отношение с веб-страницей обеспечивает динамическое извлечение определения формы для указанного узла страницы на веб-сайте.  

Другие параметры записи в самой записи веб-формы управляют настройками верхнего уровня многоступенчатого процесса в целом, например, требуется ли отображать панель хода выполнения.

Для просмотра существующих веб-форм или для создания новых веб-форм откройте [приложение управление порталами](configure-portal.md) и перейдите к пункту **Порталы** > **Веб-формы**.

> [!Note]
> **Веб-форма** должна быть связана с веб-страницей для определенного веб-сайта, чтобы эта форма была видна на этом сайте.  

При создании или изменении веб-страницы из [приложения управления порталами](configure-portal.md) можно указать **Веб-форму** в поле поиска, предусмотренном на форме **Создать веб-страницу**.

## <a name="web-form-attributes"></a>Атрибуты веб-формы

Следующие атрибуты и отношения определяют возможности веб-формы.


|                Полное имя                 |                                                                                                                                                                                        Описание                                                                                                                                                                                         |
|-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                Полное имя                 |                                                                                                                                                                          Название формы, используемое для ссылки.                                                                                                                                                                           |
|             Начальный шаг              |                                                                                Первый шаг формы. Веб-форма содержит один или несколько шагов. Дополнительные сведения об этих шагах см. ниже в разделе "Шаг веб-формы". Первый шаг не может иметь тип "Условие".                                                                                |
|       Требуется проверка подлинности       |                                                                              Если этот флажок установлен, когда пользователь, не выполнивший вход, посещает страницу, содержащую форму, он перенаправляется на страницу входа в систему. При успешном входе пользователь будет перенаправлен обратно на страницу, содержащую форму.                                                                               |
|      Начать новый сеанс при загрузке      |              Выбор **Да** указывает, что если пользователь открывает форму в новом браузере или в новой вкладке, закрывает браузер или страницу, а затем возвращается, форма запускает полностью новый сеанс и начинается с первого шага. В противном случае сеанс сохраняется, и пользователь может закрыть браузер или страницу и возобновить сеанс позднее точно в том месте, в котором он вышел. По умолчанию: **Нет**.               |
| Несколько записей на пользователя разрешено |                                                                                                  Выбор значения **Да** означает, что пользователю разрешено отправлять несколько результатов заполнения. Это помогает форме определить, что следует делать, если пользователь снова заходит в форму. Значение по умолчанию: **Да**.                                                                                                   |
|       Изменить код состояния с истекшим сроком действия       |                                                                                                                    Целое значение кода состояния целевой сущности, которое, вместе с причиной состояния, указывает, когда дальнейшее редактирование существующей записи невозможно.                                                                                                                     |
|     Изменить причину состояния с истекшим сроком действия      |                                                                       Целое значение кода состояния целевой сущности, которое, совместно с кодом состояния, указывает, что когда существующая запись имеет эти значения, то запись больше не может редактироваться &mdash; например, когда запись обновляется как завершенная.                                                                       |
|        Изменить сообщение с истекшим сроком действия         | Сообщение, выводимое, когда код состояния существующей записи и причина состояния совпадают с указанными значениями. Для каждого установленного и включенного языкового пакета для организации будет доступно поле для ввода сообщения на соответствующем языке. Сообщение по умолчанию: Отправка уже выполнена. Спасибо! |
|                                     |                                                                                                                                                                                                                                                                                                                                                                                            |

## <a name="progress-indicator-settings"></a>Параметры индикатора хода выполнения

| Имя                              | Описание                                                                                          |
|-----------------------------------|------------------------------------------------------------------------------------------------------|
| Включено                           | Нажмите для отображения индикатора хода выполнения. Значение по умолчанию: **Отключено**.                                      |
| Тип                              | Одно из следующего: заголовок, число (шаг x из n) и индикатор хода выполнения. Значение по умолчанию: **Заголовок**                                                                                    |
| Положение                          | Одно из следующих значений: сверху, снизу, слева, справа. Положение по отношению к форме. Значение по умолчанию: **Сверху**.                                                   |
| Добавить номер шага перед заголовком шага | Установите для добавления номера шага в начало заголовка шага. По умолчанию не установлен. |
||

Пример различных типов индикаторов хода выполнения:

**Заголовок**

![Отслеживание хода выполнения с помощью заголовка](../media/track-progress-title.png "Отслеживание хода выполнения с помощью заголовка")  

**Заголовок с номером шага перед заголовком**

![Отслеживание хода выполнения с помощью номера шага](../media/track-progress-step-number.png "Отслеживание хода выполнения с помощью номера шага")  

**Числовое**

![Отслеживание хода выполнения с помощью числового значения](../media/track-progress-numeral.png "Отслеживание хода выполнения с помощью числового значения")  

**Индикатор выполнения**

![Отслеживание хода выполнения с помощью индикатора](../media/track-progress-bar.png "Отслеживание хода выполнения с помощью индикатора")  

## <a name="save-changes-warning"></a>Предупреждение "Сохранить изменения" 

|                 Имя                  |                                                                                                                                Описание                                                                                                                                |
|---------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Показать предупреждающее сообщение о сохранении изменений при закрытии |                         Выберите для отображения предупреждающего сообщения, если пользователь сделал изменения в полях и пытается перезагрузить страницу, закрывает браузер, выбирает кнопку "Назад" браузера или выбирает кнопку "Предыдущий" в многошаговой форме.                         |
|     Предупреждающее сообщение о сохранении изменений      | Для каждого установленного и включенного языкового пакета для организации будет доступно поле для ввода сообщения на соответствующем языке. Если сообщение не указано, используется предусмотренное в браузере сообщение по умолчанию. |
|                                       |                                                                                                                                                                                                                                                                           |

Пример:

![Предупреждение о сохранении изменений](../media/save-changes-warning.png "Сохранение предупреждения об изменениях")  

>[!Note]
> Firefox не предоставляет возможности указать пользовательское сообщение.

## <a name="geolocation-configuration-for-web-form"></a>Конфигурация географического положения для веб-формы

Управляемую форму можно настроить для отображения элемента управления картой для отображения существующего положения в виде булавки на карте или для предоставления пользователям возможности указывать положение. См. раздел [Добавление географического положения](add-geolocation.md).

Элемент управления картой формы требует дополнительной конфигурации для указания того, что идентификаторы различных полей находятся в порядке для назначения их значений или извлечения значений из них. Запись шага веб-формы имеет раздел, в котором определены эти сопоставления полей, которым необходимо назначить значения. Имена полей будут меняться в зависимости от созданной схемы.

![Данные географического положения в веб-форме](../media/geolocation-managed-form.png "Данные географического положения в веб-форме")

> [!Note]
> Раздел "Географическое положение" не будет отображаться в среде государственного облака в Германии. Если пользователь включил географическое положение, используя другую форму, оно не будет отображаться при отрисовке портала.

### <a name="see-also"></a>См. также

[Настройка портала](configure-portal.md)  
[Определение форм сущности](entity-forms.md)  
[Шаги веб-формы для порталов](web-form-steps.md)  
[Метаданные веб-форм для порталов](configure-web-form-metadata.md)  
[Конфигурация вложенной сетки веб-форм для порталов](configure-web-form-subgrid.md)  
[Конфигурация примечаний для веб-форм для порталов](../configure-notes.md)  
