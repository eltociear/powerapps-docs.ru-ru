---
title: Изменение размера и ориентации экрана в приложении на основе холста | Документы Майкрософт
description: Пошаговые инструкции по изменению таких параметров, как размер экрана и ориентация приложения Canvas в Power Apps
author: evchaki
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2018
ms.author: evchaki
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b6ec2006266a15b7552d1a83b2d7d67c14560470
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79211441"
ms.PowerAppsDecimalTransform: true
---
# <a name="change-screen-size-and-orientation-of-a-canvas-app-in-power-apps"></a>Изменение размера экрана и ориентации приложения Canvas в Power Apps
Настройте приложение на основе холста, изменив размер и ориентацию его экрана.

## <a name="prerequisites"></a>Предварительные требования

Создайте приложение или откройте его для редактирования, а затем выберите **Параметры приложения** в меню **файл** .

## <a name="change-screen-size-and-orientation"></a>Изменение размера и ориентации экрана
1. В разделе **App settings** (Параметры приложения) выберите пункт **Screen size + orientation** (Размер и ориентация экрана).

    ![Параметр изменения размера и ориентации экрана приложения](./media/set-aspect-ratio-portrait-landscape/size-orientation.png)

1. В списке **ориентация** выберите **Книжная** или **Альбомная**.

1. (Только для планшетных приложений) В **разделе пропорции выполните**одно из следующих действий.

    - Выберите отношение, соответствующее целевому устройству для этого приложения.
    - Выберите **Пользовательский** , чтобы задать собственный размер, а затем укажите ширину в диапазоне от 50 до 3840 и высоту в диапазоне от 50 до 2160.

    ![Изменение пропорций для планшетного приложения](./media/set-aspect-ratio-portrait-landscape/aspect-tablet.png)
    
1. В поле **масштабировать по размеру**укажите значение **включено** или **выключено**.

    Этот параметр включен по умолчанию, поэтому размеры экранов приложения изменяются в соответствии с объемом доступного пространства на устройстве. Если этот параметр включен, свойство **Width** приложения соответствует его **Десигнвидс**, а **Высота** приложения соответствует его **десигнхеигхту**.

    Если отключить этот параметр, приложение изменится на пропорции устройства, на котором оно выполняется, и займет все доступное пространство. Приложение не масштабируется, и в результате экраны могут отображать дополнительные сведения.

    При отключении этого параметра пропорции **блокировки** автоматически отключаются и отключаются. Кроме того, свойство **Width** для всех экранов имеет значение `Max(App.Width; App.DesignWidth)`, а свойство **Height** имеет значение `Max(App.Height; App.DesignHeight)`, чтобы они могли контролировать размеры окна, в котором выполняется приложение. Это изменение позволяет создавать приложения, реагирующие на различные устройства и размеры окон. Дополнительные сведения: [Создание макета с откликом](create-responsive-layout.md)

1. Для параметра **Lock aspect ratio** (Заблокировать пропорции) укажите значение **On** (Вкл.) или **Off** (Выкл.).

    Если этот параметр включен, приложение будет сохранять ориентацию экрана и пропорции, указанные в шагах 2 и 3, независимо от устройства. Например, приложение для телефона, которое работает в веб-браузере, оставляет соотношение для телефона, отображая темную полоску на каждой стороне, а не заполнять окно.

    Если этот параметр отключен, приложение корректирует пропорции устройства, на котором оно работает (и при необходимости искажает пользовательский интерфейс).

1. Для параметра **Lock orientation** (Заблокировать ориентацию) укажите значение **On** (Вкл.) или **Off** (Выкл.).

    Если вы блокируете ориентацию приложения, приложение будет хранить указанную ориентацию. Если приложение выполняется на устройстве, для которого задана другая ориентация экрана, приложение отображается неправильно и может показать нежелательные результаты. Если вы разблокируете ориентацию приложения, оно корректируется на ориентацию экрана устройства, на котором оно работает.

    Можно также изменить ориентацию приложения, включив параметр **включить взаимодействие с пользователем** в **дополнительных параметрах**. Эта функция сверху вниз выстраивает приложение при его внедрении и изменяет цвет фона полотна на белый.

1. Нажмите кнопку **Apply** (Применить), чтобы сохранить изменения.

## <a name="next-step"></a>Дальнейшие действия
В меню **Файл** выберите пункт **Сохранить**, чтобы повторно опубликовать приложение с новыми параметрами.