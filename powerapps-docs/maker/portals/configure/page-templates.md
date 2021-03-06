---
title: Создание шаблонов страниц и управление ими на порталах Power Apps | MicrosoftDocs
description: Узнайте, как создавать шаблоны страниц и управлять ими на порталах Power Apps.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 26d9799425d561e4fb6a5f9f6c368fa6162ecb6d
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980628"
---
# <a name="create-and-manage-page-templates"></a>Создание шаблонов страниц и управление ими

В то время как веб-страницы являются узлами на карте сайтов портала, которая отражает содержимое, доступное пользователями портала, шаблоны страниц представляют фактические страницы .aspx, которые обеспечивают единообразие внешнего вида и восприятия на всем веб-сайте. Шаблоны страниц построены с помощью страниц ASP.NET, главных страниц, каскадных таблиц стилей (CSS), элементов управления пользователей и элементов управления сервера.

При создании новой веб-страницы для сайта как помощью клиентской публикации, так и с помощью интерфейса портала, необходимо выбрать шаблон страницы, представляющий содержимое страницы пользователям портала.

Различие между веб-страницами и шаблонами страниц, вероятно, проще всего понять как разницу меду точным URL-адресом и фактической страницей .aspx, которая работает как светокопия для отображения содержимого. Каждая веб-страница представляется определенным URL-адресом на сайте, к которому пользователи могут перейти. Когда пользователь переходит на URL-адрес, отображается содержимое, связанное с этим URL-адресом. Однако веб-страница не содержит никакой информации о том, как это содержимое отображается.  Это определяется шаблоном страницы, который является фактической страницей .aspx, которая создает HTML, отображаемый пользователю.

При создании новой веб-страницы необходимо выбрать шаблон страницы из списка существующих шаблонов. Несколько шаблонов страницы включаются с каждым из начальных порталов. При использовании этих порталов в качестве основы для собственного веб-узла эти шаблоны пригодятся как базовые средства демонстрации возможностей портала. Однако разработчику портала будет необходимо значительно изменить макета этих страниц. В большинстве случаев, шаблон страницы "Страница" будет шаблоном страницы общего назначения: для веб-страницы, использующей этот шаблон, будет отображаться ее содержимое, а также список дочерних страниц, представленный как элементы навигации.

## <a name="manage-page-templates"></a>Управление шаблонами страниц

Создание нового шаблона страницы требуется только при создании совершенно новой страницы .aspx для отображения содержимого на веб-сайте, и это задача для разработчика портала. На самом деле для простой настройки макета сайта разработчик портала может в основном просто изменять существующие страницы .aspx.

1. Откройте [Приложение управления порталом](configure-portal.md).

2. Откройте **Порталы** > **Шаблоны страниц**.

3. Чтобы создать новый шаблон страницы, выберите **Создать**.

4. Чтобы изменить существующий шаблон страницы, выберите имя шаблона страницы.

5. Введите соответствующие значения в поля.

6. Выберите **Сохранить и закрыть**.

### <a name="page-template-attributes"></a>Атрибуты шаблона страницы

|Имя |Описание |
|-----|--------|
|Имя    |Имя шаблона, используемое для ссылки.   |
|Веб-сайт   |Связанный веб-сайт.   |
|Тип   |Тип шаблона, который управляет там, как шаблон определяет, что требуется отрисовывать.<ul><li>**Перезаписать**: будет использовать поле «Перезаписать URL-адрес» для указанного шаблона ASP.NET.</li><li>**Веб-шаблон**: будет использовать поле "Веб-шаблон" для отрисовки указанного веб-шаблона.</li></ul>   |
|Перезаписать URL-адрес   |Путь физической страницы ASP.NET .aspx (или другого ресурса, например .ashx), который будет отрисовывать содержимое.<br> Это поле отображается только в том случае, если выбрано значение **Перезаписать URL-адрес** в списке **Тип**. |
|Веб-шаблон   |Ссылка на веб-шаблон, который будет использоваться для отрисовки этого шаблона.<br>Это поле отображается только в том случае, если выбрано значение **Веб-шаблон** в списке **Тип**.  |
|По умолчанию   |Если "Да", этот шаблон будет по умолчанию назначаться раскрывающемуся списку в клиентских средствах редактирования.   |
|Имя сущности   |Тип сущности страницы, которую, как ожидается, этот шаблон будет преобразовать для просмотра. Это будет использоваться клиентской системой редактирования для представления только соответствующего списка шаблонов авторам содержимого.<br>Обычно это будет веб-страница (adx_webpage), но может быть другая сущность портала, например форум, дискуссия форума, блог или запись блога.   |
|Описание  |Описание этого шаблона для пользователей клиентского редактирования. |
|||

