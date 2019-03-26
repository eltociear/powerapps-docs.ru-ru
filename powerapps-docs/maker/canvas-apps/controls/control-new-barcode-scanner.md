---
title: 'Элемент управления сканера штрих-кодов: ссылка | Документация Майкрософт'
description: Сведения, свойств и примерами, об элементе управления сканер штрихкодов
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 11/25/2018
ms.author: fikaradz
ms.reviewer: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 961f8908014ef9cd85eadacb97a7c1dfc7e52b25
ms.sourcegitcommit: eef2d6d9a9c7f5c8a44b9734817f59dc0eac3ecf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2019
ms.locfileid: "57801004"
---
# <a name="barcode-scanner-control-for-canvas-apps"></a>Элемент управления сканера штрих-кодов для приложений на основе холста

Сканирует штрихкоды, QR-коды и коды матрицы данных на устройстве Android или iOS. Не поддерживается в веб-браузере.

## <a name="description"></a>Описание

Элемент управления откроется собственного сканер на устройстве Android или iOS. Средство проверки автоматически обнаруживает штрихкода, QR-кода или кода матрицы данных, когда в представлении. Элемент управления не поддерживает проверку в веб-браузере.

Элемент управления поддерживает QR кодов, кодов матрицы данных и такого рода штрих-кодов:

- UPC A
- UPC E
- EAN 8
- EAN 13
- КОД 39
- КОД 128
- ITF
- PDF 417

## <a name="key-properties"></a>Основные свойства

**Значение** — свойство, содержащее текстовое значение код наиболее недавно просмотренного вывода.

**Текст** -текст, отображаемый для кнопки, который активирует сканер.

**OnScan** — поведение приложения при штрих-код успешно проверены.

## <a name="additional-properties"></a>Дополнительные свойства

**[BorderColor](properties-color-border.md)**  — цвет границы элемента управления.

**[BorderStyle](properties-color-border.md)**  — стиль границы элемента управления: **Сплошная**, **Штриховая**, **Пунктирная** или **Отсутствует**.

**[BorderThickness](properties-color-border.md)**  — толщина границы элемента управления.

**[DisplayMode](properties-core.md)** — в зависимости от значения этого режима элемент управления разрешает пользователю вводить данные (**Изменение**), только отображает данные (**Просмотр**) или элемент вообще отключен (**Отключено**).

**FlashlightEnabled** - ли фонариком включается автоматически при открытии средства проверки.

**[Высота](properties-size-location.md)**  — Высота кнопки, который активирует сканер.

**[Tooltip](properties-core.md)** — пояснительный текст, отображаемый при наведении указателя мыши на элемент управления.

**Тип** -тип кода, обнаруженного во время проверки, последнего успешного.

**[Visible](properties-core.md)** определяет, отображается ли элемент управления или он скрыт.

**[Ширина](properties-size-location.md)**  — Ширина кнопки, который активирует сканер.

**[X](properties-size-location.md)**  — расстояние между левым краем элемента управления и левым краем его родительского контейнера (или экрана, если родительского контейнера нет).

**[Y](properties-size-location.md)**  — расстояние между верхним краем элемента управления и верхним краем его родительского контейнера (или экрана, если родительского контейнера нет).