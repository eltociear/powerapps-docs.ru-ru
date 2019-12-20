---
title: Изменение CSS на портале | Документация Майкрософт
description: Инструкции по изменению CSS на портале.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 7fde904421d7c1d5b7e3b66d8644b0f984dd504b
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2019
ms.locfileid: "2864713"
---
# <a name="edit-css"></a>ИзменитьCSS

Каскадные таблицы стилей (CSS) позволяют управлять форматом веб-сайта. По умолчанию доступны файлы bootstrap.min.css и theme.css. Можно изменить существующие файлы CSS или отправить новые файлы CSS. При отправлении нового файла CSS он будет доступен как веб-файл в приложении управления порталами.

> [!NOTE]
> Порталы Power Apps основаны на Bootstrap 3.3.x за исключением [Портал событий](https://docs.microsoft.com/dynamics365/marketing/developer/event-management-web-application). Разработчики портала не должны заменять Bootstrap 3 другими библиотеками CSS, так как некоторые из сценариев на порталах Power Apps зависят от Bootstrap 3.3.x.

Чтобы открыть CSS в редакторе кода:

1.  [Изменить портал](manage-existing-portals.md#edit), чтобы открыть его в студии порталов Power Apps.  

2.  Выберите **Тема** ![значок "Тема"](media/theme-icon.png "Значок темы") из панели инструментов в левой части экрана. На экране появятся доступные темы.  

    > [!div class=mx-imgBorder]
    > ![Область тем](media/theme-pane.png "Область тем")  

3.  Выберите нужный CSS, чтобы открыть его в редакторе кода.

4.  Отредактируйте код и сохраните изменения.

Чтобы отправить новый файл CSS:

1.  [Изменить портал](manage-existing-portals.md#edit), чтобы открыть его в студии порталов Power Apps.  

2.  Выберите **Тема** ![значок "Тема"](media/theme-icon.png "Значок темы") из панели инструментов в левой части экрана. На экране появятся доступные темы.  

3. Выберите **Отправить пользовательский CSS**.

    > [!div class=mx-imgBorder]
    > ![Область тем](media/upload-css.png "Область тем")  

4. Найдите и выберите файл CSS для отправки.


