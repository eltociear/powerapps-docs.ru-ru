---
title: Отображение или скрытие содержимого из вспомогательных технологий, в приложениях на основе холста | Документация Майкрософт
description: Методы для отображения содержимого, только к пользователям или только для чтения экрана пользователей только для приложений на основе холста
author: tahoon-ms
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.date: 10/22/2018
ms.author: tahoon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c680767bc6a56f0596eba03dd555c1c9a0205346
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61550095"
---
# <a name="show-or-hide-content-from-assistive-technologies-for-canvas-apps"></a>Отображение или скрытие содержимого из вспомогательных технологий для приложений на основе холста

В большинстве случаев все пользователи должны иметь возможность доступа к содержимому, но иногда может потребоваться Показать содержимое только к пользователям или только для чтения экрана пользователей. Например можно только чтения с экрана пользователей для доступа к описаниям диаграммы тенденций, очевидных к пользователям. Можно также скрыть значок от чтения экрана пользователей, если он описывается метку рядом. Другое описание, значок будет излишним.

## <a name="hide-content-from-all-users"></a>Скрыть содержимое всех пользователей

* Задайте **[Visible](controls/properties-core.md)** значение false.

## <a name="hide-content-from-sighted-users-and-show-it-to-screen-reader-users"></a>Скрыть содержимое пользователям и показать его для чтения экрана пользователей

Используйте любой из этих методов:

* Задайте **[размер](controls/properties-text.md)** 0.
* Задайте **[ширины](controls/properties-size-location.md)** и **[высота](controls/properties-size-location.md)** 1.
* Задайте  **[X](controls/properties-size-location.md)**,  **[Y](controls/properties-size-location.md)**, или оба свойства таким образом, что элемент управления находится за пределами экрана.
* Задайте **[цвет](controls/properties-color-border.md)** и свойства, связанные с прозрачным.
* Поместите прямоугольник **[фигуры](controls/control-shapes-icons.md)** выше содержимое и набор **[заполнения](controls/properties-color-border.md)** тот же цвет, как цвет фона экрана.

> [!NOTE]
> Пользователи могут продолжать использовать клавиатуру для доступа к интерактивные элементы управления, такие как  **[кнопку](controls/control-button.md)**, даже если скрыть его, используя один из методов в списке выше. Задайте **[TabIndex](controls/properties-accessibility.md)** значение -1, если вы хотите запретить пользователям доступ к элемент управления, нажав клавишу Tab.

## <a name="hide-content-from-screen-reader-users-and-show-it-to-sighted-users"></a>Скрыть содержимое от чтения экрана пользователей и показать его к пользователям

* Для  **[изображение](controls/control-image.md)**,  **[значок](controls/control-shapes-icons.md)**, и **[фигуры](controls/control-shapes-icons.md)** элементов управления **[AccessibleLabel](controls/properties-accessibility.md)** пустая строка «».

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о [свойства специальных возможностей](controls/properties-accessibility.md) элементов управления в приложениях на основе холста.
