---
title: Создание веб-страниц и управление ими | Документация Майкрософт
description: Инструкции по созданию веб-страниц на портале и управлению ими.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 542622e814c2d650cbf3d6a4d3354bb363174e12
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980716"
---
# <a name="create-and-manage-webpages"></a>Создание веб-страниц и управление ими

Веб-страница — это документ, который идентифицируется уникальным URL-адресом на веб-сайте. Это один из основных объектов веб-сайта, который выстраивает иерархию веб-сайта на основе родительских и дочерних отношений с другими веб-страницами.

> [!NOTE]
> Если вы настроите портал с помощью студии порталов Power Apps, пользователи веб-сайта заметят снижение производительности. Мы порекомендовали. чтобы внести изменения в непиковые часы на эксплуатационном портале.

## <a name="create-webpage"></a>Создать веб-страницу

1.  [Изменить портал](manage-existing-portals.md#edit), чтобы открыть его в студии порталов Power Apps.  

2.  На панели команд выберите **Новая страница** и выберите страницу из пункта **Макеты** или **Фиксированные макеты**.

    > [!div class=mx-imgBorder]
    > ![создать новую веб-страницу](media/create-webpage.png "Создать новую веб-страницу")

    > [!NOTE]
    > - Создание страницы с помощью пункта **Макеты** предоставляет гибкость изменения всей страницы. **Фиксированные макеты** содержат шаблоны страниц, которые установлены в процессе портальной подготовки и настраиваемые шаблоны страниц, созданные с помощью [Приложения управления порталом](configure/configure-portal.md).
    > - Для страниц, которые необходимо создать с помощью параметра **Макеты**, установлен новый шаблон страницы **Шаблон студии по умолчанию**.

3.  В области свойств в правой части экрана введите следующие сведения:

    - **Имя**: имя страницы. Это значение также используется как заголовок страницы.

    - **Частичный URL-адрес**: Сегмент пути URL-адреса, используемый для построения URL-адреса портала для этой страницы.

    - **Шаблон**: шаблон страницы, используемый для отображения этой страницы на портале. При необходимости вы можете выбрать другой шаблон из списка.

        > [!div class=mx-imgBorder]
        > ![свойства веб-страницы](media/webpage-props.png "Свойства веб-страницы")

Созданные веб-страницы добавляются, и их иерархия отображается на панели **Страницы**. Чтобы просмотреть панель **Страницы**, выберите **Страницы** ![значок страницы](media/pages-icon.png "Значок страницы") в панели инструментов в левой части экрана.  

Допустим, вы создали несколько веб-страниц для своего портала. Иерархия страниц выглядит следующим образом:

> [!div class=mx-imgBorder]
> ![панель страницы](media/pages-pane.png "Панель страниц")  

Основное меню на веб-сайте создается автоматически на основе иерархии веб-страниц. Это называется меню **По умолчанию**. Можно также создать настраиваемое меню для отображения на веб-сайте. Дополнительные сведения: [Добавление настраиваемое меню](compose-page.md#add-a-custom-menu)

> [!div class=mx-imgBorder]
> ![навигация по веб-сайту](media/website-navigation.png "Навигация по веб-сайту")

Если вы работаете с порталом, созданным в среде, содержащей приложения на основе модели в Dynamics 365, и хотите, чтобы меню было таким же, как иерархия страниц, вы должны выбрать **По умолчанию** в списке **Меню навигации**.

> [!div class=mx-imgBorder]
> ![Меню навигации по умолчанию](media/navigation-menu-default.png "Меню навигации по умолчанию")

## <a name="manage-webpage"></a>Управление веб-страницей

1.  [Изменить портал](manage-existing-portals.md#edit), чтобы открыть его в студии порталов Power Apps.  

2.  Выберите **Страницы** ![значок страницы](media/pages-icon.png "Значок страницы") в панели инструментов в левой части экрана.  

3.  Наведите указатель мыши на страницу, которой хотите управлять, и нажмите кнопку **с многоточием** (...) для веб-страницы, которой вы хотите управлять. Вместо этого. можно щелкнуть правой кнопкой мыши на странице, которой вы хотите управлять.

4.  Выберите необходимые действия из контекстного меню:

    - **Скрыть в меню по умолчанию**: скрыть страницу от отображения на карте сайта через меню по умолчанию.

    - **Показать в меню по умолчанию**: отобразить страницу на карте сайта через меню по умолчанию.

    - **Добавить дочернюю страницу**: Добавьте дочернюю страницу к выбранной странице. Дочерняя страница наследует шаблон своей родительской страницы.

    - **Установить в качестве домашней страницы**: установить страницу в качестве домашней страницы. URL-адрес новой домашней страницы устанавливается в корневой каталог веб-сайта, а URL-адрес старой страницы обновляется соответствующим образом.

    - **Вверх**. Переместить страницу вверх в иерархии.

    - **Вниз**. Переместить страницу вниз в иерархии.

        > [!NOTE]
        > Перемещение страницы вверх или вниз поддерживается среди страниц на одном уровне.

    - **Повысить уровень вложенной страницы**: понизить уровень и сделать дочернюю страницу на уровне предыдущей страницы в иерархии.

    - **Сделать вложенной страницей**: повысить уровень и сделать страницу дочерней страницей предыдущей страницы в иерархии.

    - **Удаление**: Удаление страницу.

        > [!div class=mx-imgBorder]
        > ![параметры управления веб-страницей](media/webpage-manage-options.png "Параметры управления веб-страницей")  





