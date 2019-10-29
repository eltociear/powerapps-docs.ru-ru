---
title: Создание веб-страниц и управление ими | Документация Майкрософт
description: Инструкции по созданию веб-страниц и управлению ими на портале.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b62f6a811d2f2e6c5218ef601f18d69357d15ba9
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977020"
---
# <a name="create-and-manage-webpages"></a>Создание веб-страниц и управление ими

Веб-страница — это документ, определяемый уникальным URL-адресом на сайте. Это один из основных объектов веб-сайта, который создает иерархию веб-сайта через родительские и дочерние связи с другими веб-страницами.

> [!NOTE]
> При настройке портала с помощью PowerApps Portals Studio пользователи веб-сайта могут заметить влияние на производительность. Мы рекомендуем выполнить изменения в нерабочее время на активном портале.

## <a name="create-webpage"></a>Создать веб-страницу

1.  [Измените портал](manage-existing-portals.md#edit) , чтобы открыть его в PowerApps Portals Studio.  

2.  На панели команд выберите **создать страницу** и либо выберите страницу из **макетов** , либо **фиксированные макеты**.

    > [!div class=mx-imgBorder]
    > ![Создание новой веб-страницы](media/create-webpage.png "Создание новой веб-страницы")

    > [!NOTE]
    > - Создание страницы с помощью **макетов** позволяет вам гибко изменять всю страницу. **Фиксированные макеты** содержат шаблоны страниц, которые устанавливаются как часть подготовки портала, и пользовательские шаблоны страниц, созданные с помощью [приложения управления портала](configure/configure-portal.md).
    > - Для страниц, создаваемых с помощью параметра **Layouts** , устанавливается новый шаблон **стандартной страницы шаблона Studio** .

3.  На панели свойств в правой части экрана введите следующие сведения:

    - **Имя**: имя страницы. Это значение также используется в качестве заголовка страницы.

    - **Частичный URL-адрес**. сегмент URL-пути, используемый для создания URL-адреса портала этой страницы.

    - **Шаблон**: шаблон страницы, используемый для отображения этой страницы на портале. При необходимости можно выбрать другой шаблон из списка.

        > [!div class=mx-imgBorder]
        > (media/webpage-props.png "Свойства веб-страницы") ![свойств веб-страницы]

Создаваемые веб-страницы будут добавлены, а их иерархия отобразится на панели **страницы** . Чтобы открыть панель **страницы** , выберите **страницы** страницы ![значок](media/pages-icon.png "страницы значки из воле") в левой части экрана.  

Предположим, что вы создали несколько веб-страниц для портала. Иерархия страниц выглядит следующим образом:

> [!div class=mx-imgBorder]
> (media/pages-pane.png "область") страниц ![области страниц]  

Основное меню на веб-сайте создается автоматически на основе иерархии веб-страниц. Он называется меню **по умолчанию** . Можно также создать пользовательское меню, отображаемое на веб-сайте. Дополнительные сведения: [Добавление настраиваемого меню](compose-page.md#add-a-custom-menu)

> [!div class=mx-imgBorder]
> ![](media/website-navigation.png "Навигация") веб-сайта навигации веб-сайта

Если вы работаете с порталом, созданным с помощью среды Dynamics 365, и хотите, чтобы меню совпадало с иерархией страниц, необходимо выбрать **значение по умолчанию** в списке **меню навигации** .

> [!div class=mx-imgBorder]
> Меню(media/navigation-menu-default.png "перехода по") умолчанию в ![меню]навигации по умолчанию

## <a name="manage-webpage"></a>Управление веб-страницей

1.  [Измените портал](manage-existing-portals.md#edit) , чтобы открыть его в PowerApps Portals Studio.  

2.  В левой части **экрана выберите страницы** со ![значками страниц значок](media/pages-icon.png "страницы") .  

3.  Наведите указатель мыши на страницу, которой требуется управлять, и нажмите кнопку **с многоточием** (...) для веб-страницы, которой требуется управлять. Кроме того. можно щелкнуть правой кнопкой мыши страницу, которой требуется управлять.

4.  Выберите нужное действие в контекстном меню:

    - **Скрыть в меню по умолчанию**: Скрыть страницу от отображения на портале в меню по умолчанию.

    - **Показывать в меню по умолчанию**: отображать страницу на портале в меню по умолчанию.

    - **Добавление дочерней страницы**: Добавление дочерней страницы на выбранную страницу. Дочерняя страница наследует шаблон страницы родительской страницы.

    - **Задать в качестве домашней страницы**. Задайте страницу в качестве домашней страницы. Для URL-адреса новой домашней страницы задан корень веб-сайта и URL-адрес старой страницы соответствующим образом обновляется.

    - **Вверх: перемещение**страницы вверх в иерархии.

    - **Вниз: перемещение**страницы вниз по иерархии.

        > [!NOTE]
        > Перемещение страницы вверх или вниз поддерживается между страницами того же уровня.

    - Дочерняя **страница повышения**: Уменьшите отступ и сделайте дочернюю страницу на уровне предыдущей страницы в иерархии.

    - **Создать**вложенную страницу: увеличить отступ и сделать страницу дочерней страницей предыдущей страницы в иерархии.

    - **Удалить**. Удаляет страницу.

        > [!div class=mx-imgBorder]
        > параметры управления(media/webpage-manage-options.png "веб") -страницей параметров управления веб ![-страницей]  




