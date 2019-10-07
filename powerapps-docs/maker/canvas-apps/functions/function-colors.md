---
title: Функция для обозначения цвета Color, а также функции ColorFade, ColorValue и RGBA | Документация Майкрософт
description: Справочные сведения о функции Color, а также функциях ColorFade, ColorValue и RGBA в PowerApps, в том числе описание синтаксиса и примеры.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/04/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4af851160ea8a2add22add9f79dcc181a734e715
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "71994860"
---
# <a name="color-enumeration-and-colorfade-colorvalue-and-rgba-functions-in-powerapps"></a>Функция для обозначения цвета Color, а также функции ColorFade, ColorValue и RGBA в PowerApps

Используйте встроенные значения цвета, определите пользовательские цвета и используйте альфа-канал.

## <a name="description"></a>Описание

Используя перечисление **цветов** , можно легко получить доступ к цветам, определенным в каскадные таблицы стилей HTML (CSS). Например, **Color. Red** возвращает чистый красный цвет. Список этих цветов можно найти в конце этого раздела.

Функция **колорвалуе** Возвращает цвет на основе строки цвета в CSS. Строка может принимать любую из следующих форм:

- **Имя цвета CSS:** Примерами являются **"роксибровн"** и **"ОливеДраб"** . Эти имена не содержат пробелов. Список поддерживаемых цветов представлен далее в этом разделе.
- **шестнадцатеричное значение из 6 цифр:** Например, **"#ffd700"** совпадает с **"золото"** . Строка имеет формат #*RRGGBB*, где *RR* — красная часть в двух шестнадцатеричных цифрах, *GG* — зеленым, а *BB* — синим.
- **8-значное шестнадцатеричное значение:** Например, **"#ff7f5080"** совпадает с **"кораллового"** и альфа-каналом 50%. Строка имеет формат "#*ррггббаа*", где *RR*, *GG*и *BB* идентичны форме из 6 цифр. Альфа-канал представлен *номером AA*: **00** представляет полностью прозрачный, а **FF** представляет полностью непрозрачный.

Функция **RGBA** Возвращает цвет на основе красного, зеленого и синего компонентов. Функция также включает альфа-канал для смешивания цветов элементов управления, которые расположены впереди друг друга. Альфа-канал варьируется от 0 до 0% (он полностью прозрачен и невидим) до 1 или 100% (который полностью непрозрачен и полностью блокирует все слои за элементом управления).

Функция **ColorFade** позволяет сделать цвет более светлым или темным. Величина затухания варьируется от-1 (что полностью затемняет цвет до черного) до 0 (что не влияет на цвет) на 1 (что приводит к полному изменению цвета на белый цвет).

## <a name="alpha-channel"></a>Альфа-канал

В приложении Canvas можно послойировать элементы управления впереди друг друга и указать прозрачность элемента управления для всех элементов управления, находящиеся за ним. В результате цвета будут смешиваться по слоям. Например, на этой схеме показано, как три основных цвета сочетаются с параметром альфа 50%:

> [!div class="mx-imgBorder"]
> @no__t 0Three основные цвета с параметром альфа-канала 50% ](media/function-colors/alpha-primary.png)

Кроме того, можно смешивать изображения в форматах файлов, поддерживающих альфа-каналы. Например, нельзя смешивать JPEG-файлы, но можно смешивать PNG-файлы. На следующем рисунке показаны те же цвета красного, зеленого и синего, что и в предыдущем примере, но красный цвет отображается в виде волнистой линии (а не окружности) в PNG-файле с 50% альфа-каналом:

> [!div class="mx-imgBorder"]
> ![Red волнистой линией с параметром альфа 50% перед синим и зеленым кружками @ no__t-1

Если указать значение перечисления **цветов** или создать формулу **колорвалуе** с именем цвета или шестнадцатеричным значением из 6 цифр, параметр Alpha имеет значение 100%, что является полностью непрозрачным.

## <a name="syntax"></a>Синтаксис

**Color**.*ColorName*

- *ColorName* — обязательный аргумент.  Имя цвета на языке CSS. Список возможных значений перечисления представлен в конце этого раздела.

**ColorValue**( *CSSColor* )

- *CSSColor* — обязательный аргумент.  Определение цвета на языке CSS. Можно указать либо имя, например **ОливеДраб**, либо шестнадцатеричное значение, например **#6b8e23** или **#7fffd420**. Шестнадцатеричные значения могут принимать форму либо #*RRGGBB* , либо #*ррггббаа*.

**RGBA**( *Red*, *Green*, *Blue*, *Alpha* )

- *Red*, *Green*, *Blue* — обязательны.  Цветовые компоненты — значения в диапазоне от 0 (без насыщенности) до 255 (полная насыщенность).
- *Alpha* — обязательный компонент.  Альфа-компонент, который в диапазоне от 0 (полностью прозрачный) до 1 (полностью непрозрачный). Вы также можете использовать проценты: от 0 % до 100 %.

**ColorFade**( *Color*, *FadeAmount* )

- *Color* — обязательный аргумент.  Значение цвета (например, **Color.Red**) или выходное значение **ColorValue** или **RGBA**.
- *FadeAmount* — обязательный аргумент.  Значение варьируется от -1 до 1. -1 полностью затемняет цвет до черного, 0 не влияет на цвет, а 1 полностью делает цвет белым. Можно также использовать значение в процентах от-100% до 100%.

## <a name="built-in-colors"></a>Встроенные цвета

| Обозначение цвета | ColorValue | RGBA | Палитры цветов |
| --- | --- | --- | --- |
| **Color.AliceBlue** |**Колорвалуе ("#f0f8ff" &nbsp;)**<br>**Колорвалуе ("AliceBlue" &nbsp;)** |**RGBA (&nbsp;240, &nbsp;248, &nbsp;255, &nbsp;1 @ NO__T-5)** |![Бледно-голубой](./media/function-colors/color-aliceblue.png) |
| **Color.AntiqueWhite** |**Колорвалуе ("#faebd7" &nbsp;)**<br>**Колорвалуе ("Антикуевхите" &nbsp;)** |**RGBA (&nbsp;250, &nbsp;235, &nbsp;215, &nbsp;1 @ NO__T-5)** |![Античный белый](./media/function-colors/color-antiquewhite.png) |
| **Color.Aqua** |**Колорвалуе ("#00ffff" &nbsp;)**<br>**Колорвалуе ("голубой" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;255, &nbsp;255, &nbsp;1 @ NO__T-5)** |![Бирюзовый](./media/function-colors/color-aqua.png) |
| **Color.Aquamarine** |**Колорвалуе ("#7fffd4" &nbsp;)**<br>**Колорвалуе ("Аквамариновый" &nbsp;)** |**RGBA (&nbsp;127, &nbsp;255, &nbsp;212, &nbsp;1 @ NO__T-5)** |![Аквамариновый](./media/function-colors/color-aquamarine.png) |
| **Color.Azure** |**Колорвалуе ("#f0ffff" &nbsp;)**<br>**Колорвалуе ("Azure" &nbsp;)** |**RGBA (&nbsp;240, &nbsp;255, &nbsp;255, &nbsp;1 @ NO__T-5)** |![Лазурный](./media/function-colors/color-azure.png) |
| **Color.Beige** |**Колорвалуе ("#f5f5dc" &nbsp;)**<br>**Колорвалуе ("бежевый" &nbsp;)** |**RGBA (&nbsp;245, &nbsp;245, &nbsp;220, &nbsp;1 @ NO__T-5)** |![Бежевый](./media/function-colors/color-beige.png) |
| **Color.Bisque** |**Колорвалуе ("#ffe4c4" &nbsp;)**<br>**Колорвалуе ("БИСКУЕ" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;228, &nbsp;196, &nbsp;1 @ NO__T-5)** |![Светло-коричневый](./media/function-colors/color-bisque.png) |
| **Color.Black** |**Колорвалуе ("#000000" &nbsp;)**<br>**Колорвалуе ("черный" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;0, &nbsp;0, &nbsp;1 @ NO__T-5)** |![Черный](./media/function-colors/color-black.png) |
| **Color.BlanchedAlmond** |**Колорвалуе ("#ffebcd" &nbsp;)**<br>**Колорвалуе ("бланчедалмонд" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;235, &nbsp;205, &nbsp;1 @ NO__T-5)** |![Миндальный](./media/function-colors/color-blanchedalmond.png) |
| **Color.Blue** |**Колорвалуе ("#0000ff" &nbsp;)**<br>**Колорвалуе ("синий" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;0, &nbsp;255, &nbsp;1 @ NO__T-5)** |![Синий](./media/function-colors/color-blue.png) |
| **Color.BlueViolet** |**Колорвалуе ("#8a2be2" &nbsp;)**<br>**Колорвалуе ("БЛУЕВИОЛЕТ" &nbsp;)** |**RGBA (&nbsp;138, &nbsp;43, &nbsp;226, &nbsp;1 @ NO__T-5)** |![Сине-фиолетовый](./media/function-colors/color-blueviolet.png) |
| **Color.Brown** |**Колорвалуе ("#a52a2a" &nbsp;)**<br>**Колорвалуе ("Иванов" &nbsp;)** |**RGBA (&nbsp;165, &nbsp;42, &nbsp;42, &nbsp;1 @ NO__T-5)** |![Коричневый](./media/function-colors/color-brown.png) |
| **Color.Burlywood** |**Колорвалуе ("#deb887" &nbsp;)**<br>**Колорвалуе ("бурливуд" &nbsp;)** |**RGBA (&nbsp;222, &nbsp;184, &nbsp;135, &nbsp;1 @ NO__T-5)** |![Крем-брюле](./media/function-colors/color-burlywood.png) |
| **Color.CadetBlue** |**Колорвалуе ("#5f9ea0" &nbsp;)**<br>**Колорвалуе ("Кадетблуе" &nbsp;)** |**RGBA (&nbsp;95, &nbsp;158, &nbsp;160, &nbsp;1 @ NO__T-5)** |![Светлый серо-голубой](./media/function-colors/color-cadetblue.png) |
| **Color.Chartreuse** |**Колорвалуе ("#7fff00" &nbsp;)**<br>**Колорвалуе ("ЧАРТРЕУСЕ" &nbsp;)** |**RGBA (&nbsp;127, &nbsp;255, &nbsp;0, &nbsp;1 @ NO__T-5)** |![Фисташковый](./media/function-colors/color-chartreuse.png) |
| **Color.Chocolate** |**Колорвалуе ("#d2691e" &nbsp;)**<br>**Колорвалуе ("шоколад" &nbsp;)** |**RGBA (&nbsp;210, &nbsp;105, &nbsp;30, &nbsp;1 @ NO__T-5)** |![Шоколад](./media/function-colors/color-chocolate.png) |
| **Color.Coral** |**Колорвалуе ("#ff7f50" &nbsp;)**<br>**Колорвалуе ("Коралловый" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;127, &nbsp;80, &nbsp;1 @ NO__T-5)** |![Коралловый](./media/function-colors/color-coral.png) |
| **Color.CornflowerBlue** |**Колорвалуе ("#6495ed" &nbsp;)**<br>**Колорвалуе ("CornflowerBlue" &nbsp;)** |**RGBA (&nbsp;100, &nbsp;149, &nbsp;237, &nbsp;1 @ NO__T-5)** |![Васильковый](./media/function-colors/color-cornflowerblue.png) |
| **Color.Cornsilk** |**Колорвалуе ("#fff8dc" &nbsp;)**<br>**Колорвалуе ("КОРНСИЛК" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;248, &nbsp;220, &nbsp;1 @ NO__T-5)** |![Кремово-лимонный](./media/function-colors/color-cornsilk.png) |
| **Color.Crimson** |**Колорвалуе ("#dc143c" &nbsp;)**<br>**Колорвалуе ("Crimson" &nbsp;)** |**RGBA (&nbsp;220, &nbsp;20, &nbsp;60, &nbsp;1 @ NO__T-5)** |![Алый](./media/function-colors/color-crimson.png) |
| **Color.Cyan** |**Колорвалуе ("#00ffff" &nbsp;)**<br>**Колорвалуе ("голубой" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;255, &nbsp;255, &nbsp;1 @ NO__T-5)** |![Зеленовато-голубой](./media/function-colors/color-cyan.png) |
| **Color.DarkBlue** |**Колорвалуе ("#00008b" &nbsp;)**<br>**Колорвалуе ("Даркблуе" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;0, &nbsp;139, &nbsp;1 @ NO__T-5)** |![Темно-синий](./media/function-colors/color-darkblue.png) |
| **Color.DarkCyan** |**Колорвалуе ("#008b8b" &nbsp;)**<br>**Колорвалуе ("ДАРКЦИАН" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;139, &nbsp;139, &nbsp;1 @ NO__T-5)** |![Темно-голубой](./media/function-colors/color-darkcyan.png) |
| **Color.DarkGoldenRod** |**Колорвалуе ("#b8860b" &nbsp;)**<br>**Колорвалуе ("Даркголденрод" &nbsp;)** |**RGBA (&nbsp;184, &nbsp;134, &nbsp;11, &nbsp;1 @ NO__T-5)** |![Темный желто-коричневый](./media/function-colors/color-darkgoldenrod.png) |
| **Color.DarkGray** |**Колорвалуе ("#a9a9a9" &nbsp;)**<br>**Колорвалуе ("даркграй" &nbsp;)** |**RGBA (&nbsp;169, &nbsp;169, &nbsp;169, &nbsp;1 @ NO__T-5)** |![Темно-серый](./media/function-colors/color-darkgray.png) |
| **Color.DarkGreen** |**Колорвалуе ("#006400" &nbsp;)**<br>**Колорвалуе ("Даркгрин" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;100, &nbsp;0, &nbsp;1 @ NO__T-5)** |![Темно-зеленый](./media/function-colors/color-darkgreen.png) |
| **Color.DarkGrey** |**Колорвалуе ("#a9a9a9" &nbsp;)**<br>**Колорвалуе ("ДАРКГРЭЙ" &nbsp;)** |**RGBA (&nbsp;169, &nbsp;169, &nbsp;169, &nbsp;1 @ NO__T-5)** |![Темно-серый](./media/function-colors/color-darkgrey.png) |
| **Color.DarkKhaki** |**Колорвалуе ("#bdb76b" &nbsp;)**<br>**Колорвалуе ("Дарккхаки" &nbsp;)** |**RGBA (&nbsp;189, &nbsp;183, &nbsp;107, &nbsp;1 @ NO__T-5)** |![Темный хаки](./media/function-colors/color-darkkhaki.png) |
| **Color.DarkMagenta** |**Колорвалуе ("#8b008b" &nbsp;)**<br>**Колорвалуе ("даркмажента" &nbsp;)** |**RGBA (&nbsp;139, &nbsp;0, &nbsp;139, &nbsp;1 @ NO__T-5)** |![Темно-пурпурный](./media/function-colors/color-darkmagenta.png) |
| **Color.DarkOliveGreen** |**Колорвалуе ("#556b2f" &nbsp;)**<br>**Колорвалуе ("Дарколивегрин" &nbsp;)** |**RGBA (&nbsp;85, &nbsp;107, &nbsp;47, &nbsp;1 @ NO__T-5)** |![Темный зеленовато-оливковый](./media/function-colors/color-darkolivegreen.png) |
| **Color.DarkOrange** |**Колорвалуе ("#ff8c00" &nbsp;)**<br>**Колорвалуе ("ДАРКОРАНЖЕ" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;140, &nbsp;0, &nbsp;1 @ NO__T-5)** |![Темно-оранжевый](./media/function-colors/color-darkorange.png) |
| **Color.DarkOrchid** |**Колорвалуе ("#9932cc" &nbsp;)**<br>**Колорвалуе ("Даркорчид" &nbsp;)** |**RGBA (&nbsp;153, &nbsp;50, &nbsp;204, &nbsp;1 @ NO__T-5)** |![Темно-лиловый](./media/function-colors/color-darkorchid.png) |
| **Color.DarkRed** |**Колорвалуе ("#8b0000" &nbsp;)**<br>**Колорвалуе ("даркред" &nbsp;)** |**RGBA (&nbsp;139, &nbsp;0, &nbsp;0, &nbsp;1 @ NO__T-5)** |![Темно-красный](./media/function-colors/color-darkred.png) |
| **Color.DarkSalmon** |**Колорвалуе ("#e9967a" &nbsp;)**<br>**Колорвалуе ("Дарксалмон" &nbsp;)** |**RGBA (&nbsp;233, &nbsp;150, &nbsp;122, &nbsp;1 @ NO__T-5)** |![Темный оранжево-розовый](./media/function-colors/color-darksalmon.png) |
| **Color.DarkSeaGreen** |**Колорвалуе ("#8fbc8f" &nbsp;)**<br>**Колорвалуе ("ДАРКСЕАГРИН" &nbsp;)** |**RGBA (&nbsp;143, &nbsp;188, &nbsp;143, &nbsp;1 @ NO__T-5)** |![Темно-зеленое море](./media/function-colors/color-darkseagreen.png) |
| **Color.DarkSlateBlue** |**Колорвалуе ("#483d8b" &nbsp;)**<br>**Колорвалуе ("Даркслатеблуе" &nbsp;)** |**RGBA (&nbsp;72, &nbsp;61, &nbsp;139, &nbsp;1 @ NO__T-5)** |![Темный синевато-серый](./media/function-colors/color-darkslateblue.png) |
| **Color.DarkSlateGray** |**Колорвалуе ("#2f4f4f" &nbsp;)**<br>**Колорвалуе ("даркслатеграй" &nbsp;)** |**RGBA (&nbsp;47, &nbsp;79, &nbsp;79, &nbsp;1 @ NO__T-5)** |![Темный серо-синий](./media/function-colors/color-darkslategray.png) |
| **Color.DarkSlateGrey** |**Колорвалуе ("#2f4f4f" &nbsp;)**<br>**Колорвалуе ("Даркслатегрэй" &nbsp;)** |**RGBA (&nbsp;47, &nbsp;79, &nbsp;79, &nbsp;1 @ NO__T-5)** |![Темный серый](./media/function-colors/color-darkslategrey.png) |
| **Color.DarkTurquoise** |**Колорвалуе ("#00ced1" &nbsp;)**<br>**Колорвалуе ("ДАРКТУРКУОИСЕ" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;206, &nbsp;209, &nbsp;1 @ NO__T-5)** |![Темно-бирюзовый](./media/function-colors/color-darkturquoise.png) |
| **Color.DarkViolet** |**Колорвалуе ("#9400d3" &nbsp;)**<br>**Колорвалуе ("Дарквиолет" &nbsp;)** |**RGBA (&nbsp;148, &nbsp;0, &nbsp;211, &nbsp;1 @ NO__T-5)** |![Темно-фиолетовый](./media/function-colors/color-darkviolet.png) |
| **Color.DeepPink** |**Колорвалуе ("#ff1493" &nbsp;)**<br>**Колорвалуе ("диппинк" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;20, &nbsp;147, &nbsp;1 @ NO__T-5)** |![Темно-розовый](./media/function-colors/color-deeppink.png) |
| **Color.DeepSkyBlue** |**Колорвалуе ("#00bfff" &nbsp;)**<br>**Колорвалуе ("Дипскиблуе" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;191, &nbsp;255, &nbsp;1 @ NO__T-5)** |![Темный небесно-синий](./media/function-colors/color-deepskyblue.png) |
| **Color.DimGray** |**Колорвалуе ("#696969" &nbsp;)**<br>**Колорвалуе ("ДИМГРАЙ" &nbsp;)** |**RGBA (&nbsp;105, &nbsp;105, &nbsp;105, &nbsp;1 @ NO__T-5)** |![Темно-серый](./media/function-colors/color-dimgray.png) |
| **Color.DimGrey** |**Колорвалуе ("#696969" &nbsp;)**<br>**Колорвалуе ("Димгрэй" &nbsp;)** |**RGBA (&nbsp;105, &nbsp;105, &nbsp;105, &nbsp;1 @ NO__T-5)** |![Темно-серый](./media/function-colors/color-dimgrey.png) |
| **Color.DodgerBlue** |**Колорвалуе ("#1e90ff" &nbsp;)**<br>**Колорвалуе ("доджерблуе" &nbsp;)** |**RGBA (&nbsp;30, &nbsp;144, &nbsp;255, &nbsp;1 @ NO__T-5)** |![Голубовато-синий](./media/function-colors/color-dodgerblue.png) |
| **Color.FireBrick** |**Колорвалуе ("#b22222" &nbsp;)**<br>**Колорвалуе ("Фиребрикк" &nbsp;)** |**RGBA (&nbsp;178, &nbsp;34, &nbsp;34, &nbsp;1 @ NO__T-5)** |![Красный кирпич](./media/function-colors/color-firebrick.png) |
| **Color.FloralWhite** |**Колорвалуе ("#fffaf0" &nbsp;)**<br>**Колорвалуе ("ФЛОРАЛВХИТЕ" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;250, &nbsp;240, &nbsp;1 @ NO__T-5)** |![Цветочно-белый](./media/function-colors/color-floralwhite.png) |
| **Color.ForestGreen** |**Колорвалуе ("#228b22" &nbsp;)**<br>**Колорвалуе ("Форестгрин" &nbsp;)** |**RGBA (&nbsp;34, &nbsp;139, &nbsp;34, &nbsp;1 @ NO__T-5)** |![Зеленый лес](./media/function-colors/color-forestgreen.png) |
| **Color.Fuchsia** |**Колорвалуе ("#ff00ff" &nbsp;)**<br>**Колорвалуе ("фучсиа" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;0, &nbsp;255, &nbsp;1 @ NO__T-5)** |![Фуксия](./media/function-colors/color-fuchsia.png) |
| **Color.Gainsboro** |**Колорвалуе ("#dcdcdc" &nbsp;)**<br>**Колорвалуе ("Гаинсборо" &nbsp;)** |**RGBA (&nbsp;220, &nbsp;220, &nbsp;220, &nbsp;1 @ NO__T-5)** |![Серо-фиолетовый, светлый](./media/function-colors/color-gainsboro.png) |
| **Color.GhostWhite** |**Колорвалуе ("#f8f8ff" &nbsp;)**<br>**Колорвалуе ("ГХОСТВХИТЕ" &nbsp;)** |**RGBA (&nbsp;248, &nbsp;248, &nbsp;255, &nbsp;1 @ NO__T-5)** |![Холодный белый](./media/function-colors/color-ghostwhite.png) |
| **Color.Gold** |**Колорвалуе ("#ffd700" &nbsp;)**<br>**Колорвалуе ("золото" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;215, &nbsp;0, &nbsp;1 @ NO__T-5)** |![Золотистый](./media/function-colors/color-gold.png) |
| **Color.GoldenRod** |**Колорвалуе ("#daa520" &nbsp;)**<br>**Колорвалуе ("-золотистый" &nbsp;)** |**RGBA (&nbsp;218, &nbsp;165, &nbsp;32, &nbsp;1 @ NO__T-5)** |![Светлый желто-коричневый](./media/function-colors/color-goldenrod.png) |
| **Color.Gray** |**Колорвалуе ("#808080" &nbsp;)**<br>**Колорвалуе ("серый" &nbsp;)** |**RGBA (&nbsp;128, &nbsp;128, &nbsp;128, &nbsp;1 @ NO__T-5)** |![Серый](./media/function-colors/color-gray.png) |
| **Color.Green** |**Колорвалуе ("#008000" &nbsp;)**<br>**Колорвалуе ("зеленый" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;128, &nbsp;0, &nbsp;1 @ NO__T-5)** |![Зеленый](./media/function-colors/color-green.png) |
| **Color.GreenYellow** |**Колорвалуе ("#adff2f" &nbsp;)**<br>**Колорвалуе ("Гринеллов" &nbsp;)** |**RGBA (&nbsp;173, &nbsp;255, &nbsp;47, &nbsp;1 @ NO__T-5)** |![Зеленовато-желтый](./media/function-colors/color-greenyellow.png) |
| **Color.Grey** |**Колорвалуе ("#808080" &nbsp;)**<br>**Колорвалуе ("серый" &nbsp;)** |**RGBA (&nbsp;128, &nbsp;128, &nbsp;128, &nbsp;1 @ NO__T-5)** |![Серый](./media/function-colors/color-grey.png) |
| **Color.Honeydew** |**Колорвалуе ("#f0fff0" &nbsp;)**<br>**Колорвалуе ("дыня" &nbsp;)** |**RGBA (&nbsp;240, &nbsp;255, &nbsp;240, &nbsp;1 @ NO__T-5)** |![Медовый](./media/function-colors/color-honeydew.png) |
| **Color.HotPink** |**Колорвалуе ("#ff69b4" &nbsp;)**<br>**Колорвалуе ("ХОТПИНК" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;105, &nbsp;180, &nbsp;1 @ NO__T-5)** |![Ярко-розовый](./media/function-colors/color-hotpink.png) |
| **Color.IndianRed** |**Колорвалуе ("#cd5c5c" &nbsp;)**<br>**Колорвалуе ("Индианред" &nbsp;)** |**RGBA (&nbsp;205, &nbsp;92, &nbsp;92, &nbsp;1 @ NO__T-5)** |![Светло-красный](./media/function-colors/color-indianred.png) |
| **Color.Indigo** |**Колорвалуе ("#4b0082" &nbsp;)**<br>**Колорвалуе ("Indigo" &nbsp;)** |**RGBA (&nbsp;75, &nbsp;0, &nbsp;130, &nbsp;1 @ NO__T-5)** |![Индиго](./media/function-colors/color-indigo.png) |
| **Color.Ivory** |**Колорвалуе ("#fffff0" &nbsp;)**<br>**Колорвалуе ("берег слоновой кости" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;255, &nbsp;240, &nbsp;1 @ NO__T-5)** |![Слоновая кость](./media/function-colors/color-ivory.png) |
| **Color.Khaki** |**Колорвалуе ("#f0e68c" &nbsp;)**<br>**Колорвалуе ("хаки" &nbsp;)** |**RGBA (&nbsp;240, &nbsp;230, &nbsp;140, &nbsp;1 @ NO__T-5)** |![Хаки](./media/function-colors/color-khaki.png) |
| **Color.Lavender** |**Колорвалуе ("#e6e6fa" &nbsp;)**<br>**Колорвалуе ("бледный" &nbsp;)** |**RGBA (&nbsp;230, &nbsp;230, &nbsp;250, &nbsp;1 @ NO__T-5)** |![Бледный розовато-лиловый](./media/function-colors/color-lavender.png) |
| **Color.LavenderBlush** |**Колорвалуе ("#fff0f5" &nbsp;)**<br>**Колорвалуе ("лавендерблуш" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;240, &nbsp;245, &nbsp;1 @ NO__T-5)** |![Розовато-лиловый](./media/function-colors/color-lavenderblush.png) |
| **Color.LawnGreen** |**Колорвалуе ("#7cfc00" &nbsp;)**<br>**Колорвалуе ("Лавнгрин" &nbsp;)** |**RGBA (&nbsp;124, &nbsp;252, &nbsp;0, &nbsp;1 @ NO__T-5)** |![Зеленая трава](./media/function-colors/color-lawngreen.png) |
| **Color.LemonChiffon** |**Колорвалуе ("#fffacd" &nbsp;)**<br>**Колорвалуе ("ЛЕМОНЧИФФОН" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;250, &nbsp;205, &nbsp;1 @ NO__T-5)** |![Лимонный](./media/function-colors/color-lemonchiffon.png) |
| **Color.LightBlue** |**Колорвалуе ("#add8e6" &nbsp;)**<br>**Колорвалуе ("LightBlue" &nbsp;)** |**RGBA (&nbsp;173, &nbsp;216, &nbsp;230, &nbsp;1 @ NO__T-5)** |![Светло-синий](./media/function-colors/color-lightblue.png) |
| **Color.LightCoral** |**Колорвалуе ("#f08080" &nbsp;)**<br>**Колорвалуе ("лигхткорал" &nbsp;)** |**RGBA (&nbsp;240, &nbsp;128, &nbsp;128, &nbsp;1 @ NO__T-5)** |![Светло-коралловый](./media/function-colors/color-lightcoral.png) |
| **Color.LightCyan** |**Колорвалуе ("#e0ffff" &nbsp;)**<br>**Колорвалуе ("Лигхтциан" &nbsp;)** |**RGBA (&nbsp;224, &nbsp;255, &nbsp;255, &nbsp;1 @ NO__T-5)** |![Светло-голубой](./media/function-colors/color-lightcyan.png) |
| **Color.LightGoldenRodYellow** |**Колорвалуе ("#fafad2" &nbsp;)**<br>**Колорвалуе ("лигхтголденроделлов" &nbsp;)** |**RGBA (&nbsp;250, &nbsp;250, &nbsp;210, &nbsp;1 @ NO__T-5)** |![Светло-лимонный](./media/function-colors/color-lightgoldenrodyellow.png) |
| **Color.LightGray** |**Колорвалуе ("#d3d3d3" &nbsp;)**<br>**Колорвалуе ("Лигхтграй" &nbsp;)** |**RGBA (&nbsp;211, &nbsp;211, &nbsp;211, &nbsp;1 @ NO__T-5)** |![Светло-серый](./media/function-colors/color-lightgray.png) |
| **Color.LightGreen** |**Колорвалуе ("#90ee90" &nbsp;)**<br>**Колорвалуе ("лигхтгрин" &nbsp;)** |**RGBA (&nbsp;144, &nbsp;238, &nbsp;144, &nbsp;1 @ NO__T-5)** |![Светло-зеленый](./media/function-colors/color-lightgreen.png) |
| **Color.LightGrey** |**Колорвалуе ("#d3d3d3" &nbsp;)**<br>**Колорвалуе ("Лигхтгрэй" &nbsp;)** |**RGBA (&nbsp;211, &nbsp;211, &nbsp;211, &nbsp;1 @ NO__T-5)** |![Светло-серый](./media/function-colors/color-lightgrey.png) |
| **Color.LightPink** |**Колорвалуе ("#ffb6c1" &nbsp;)**<br>**Колорвалуе ("ЛИГХТПИНК" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;182, &nbsp;193, &nbsp;1 @ NO__T-5)** |![Светло-розовый](./media/function-colors/color-lightpink.png) |
| **Color.LightSalmon** |**Колорвалуе ("#ffa07a" &nbsp;)**<br>**Колорвалуе ("Лигхтсалмон" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;160, &nbsp;122, &nbsp;1 @ NO__T-5)** |![Светлый оранжево-розовый](./media/function-colors/color-lightsalmon.png) |
| **Color.LightSeaGreen** |**Колорвалуе ("#20b2aa" &nbsp;)**<br>**Колорвалуе ("лигхтсеагрин" &nbsp;)** |**RGBA (&nbsp;32, &nbsp;178, &nbsp;170, &nbsp;1 @ NO__T-5)** |![Светло-зеленое море](./media/function-colors/color-lightseagreen.png) |
| **Color.LightSkyBlue** |**Колорвалуе ("#87cefa" &nbsp;)**<br>**Колорвалуе ("Лигхтскиблуе" &nbsp;)** |**RGBA (&nbsp;135, &nbsp;206, &nbsp;250, &nbsp;1 @ NO__T-5)** |![Светлый небесно-синий](./media/function-colors/color-lightskyblue.png) |
| **Color.LightSlateGray** |**Колорвалуе ("#778899" &nbsp;)**<br>**Колорвалуе ("ЛИГХТСЛАТЕГРАЙ" &nbsp;)** |**RGBA (&nbsp;119, &nbsp;136, &nbsp;153, &nbsp;1 @ NO__T-5)** |![Светлый серо-синий](./media/function-colors/color-lightslategray.png) |
| **Color.LightSlateGrey** |**Колорвалуе ("#778899" &nbsp;)**<br>**Колорвалуе ("Лигхтслатегрэй" &nbsp;)** |**RGBA (&nbsp;119, &nbsp;136, &nbsp;153, &nbsp;1 @ NO__T-5)** |![Светлый серо-синий](./media/function-colors/color-lightslategrey.png) |
| **Color.LightSteelBlue** |**Колорвалуе ("#b0c4de" &nbsp;)**<br>**Колорвалуе ("лигхтстилблуе" &nbsp;)** |**RGBA (&nbsp;176, &nbsp;196, &nbsp;222, &nbsp;1 @ NO__T-5)** |![Светлый синевато-стальной](./media/function-colors/color-lightsteelblue.png) |
| **Color.LightYellow** |**Колорвалуе ("#ffffe0" &nbsp;)**<br>**Колорвалуе ("Лигхтеллов" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;255, &nbsp;224, &nbsp;1 @ NO__T-5)** |![Светло-желтый](./media/function-colors/color-lightyellow.png) |
| **Color.Lime** |**Колорвалуе ("#00ff00" &nbsp;)**<br>**Колорвалуе ("ТРАВЯной" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;255, &nbsp;0, &nbsp;1 @ NO__T-5)** |![Травяной](./media/function-colors/color-lime.png) |
| **Color.LimeGreen** |**Колорвалуе ("#32cd32" &nbsp;)**<br>**Колорвалуе ("Лимегрин" &nbsp;)** |**RGBA (&nbsp;50, &nbsp;205, &nbsp;50, &nbsp;1 @ NO__T-5)** |![Лайм](./media/function-colors/color-limegreen.png) |
| **Color.Linen** |**Колорвалуе ("#faf0e6" &nbsp;)**<br>**Колорвалуе ("Линен" &nbsp;)** |**RGBA (&nbsp;250, &nbsp;240, &nbsp;230, &nbsp;1 @ NO__T-5)** |![Льняной](./media/function-colors/color-linen.png) |
| **Color.Magenta** |**Колорвалуе ("#ff00ff" &nbsp;)**<br>**Колорвалуе ("пурпурный" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;0, &nbsp;255, &nbsp;1 @ NO__T-5)** |![Пурпурный](./media/function-colors/color-magenta.png) |
| **Color.Maroon** |**Колорвалуе ("#800000" &nbsp;)**<br>**Колорвалуе ("КАШТАНОВЫЙ" &nbsp;)** |**RGBA (&nbsp;128, &nbsp;0, &nbsp;0, &nbsp;1 @ NO__T-5)** |![Малиновый](./media/function-colors/color-maroon.png) |
| **Color.MediumAquamarine** |**Колорвалуе ("#66cdaa" &nbsp;)**<br>**Колорвалуе ("Медиумакуамарине" &nbsp;)** |**RGBA (&nbsp;102, &nbsp;205, &nbsp;170, &nbsp;1 @ NO__T-5)** |![Умеренно-аквамариновый](./media/function-colors/color-mediumaquamarine.png) |
| **Color.MediumBlue** |**Колорвалуе ("#0000cd" &nbsp;)**<br>**Колорвалуе ("медиумблуе" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;0, &nbsp;205, &nbsp;1 @ NO__T-5)** |![Умеренно-синий](./media/function-colors/color-mediumblue.png) |
| **Color.MediumOrchid** |**Колорвалуе ("#ba55d3" &nbsp;)**<br>**Колорвалуе ("Медиуморчид" &nbsp;)** |**RGBA (&nbsp;186, &nbsp;85, &nbsp;211, &nbsp;1 @ NO__T-5)** |![Умеренно-лиловый](./media/function-colors/color-mediumorchid.png) |
| **Color.MediumPurple** |**Колорвалуе ("#9370db" &nbsp;)**<br>**Колорвалуе ("МЕДИУМПУРПЛЕ" &nbsp;)** |**RGBA (&nbsp;147, &nbsp;112, &nbsp;219, &nbsp;1 @ NO__T-5)** |![Умеренно-сиреневый](./media/function-colors/color-mediumpurple.png) |
| **Color.MediumSeaGreen** |**Колорвалуе ("#3cb371" &nbsp;)**<br>**Колорвалуе ("Медиумсеагрин" &nbsp;)** |**RGBA (&nbsp;60, &nbsp;179, &nbsp;113, &nbsp;1 @ NO__T-5)** |![Умеренно-зеленое море](./media/function-colors/color-mediumseagreen.png) |
| **Color.MediumSlateBlue** |**Колорвалуе ("#7b68ee" &nbsp;)**<br>**Колорвалуе ("медиумслатеблуе" &nbsp;)** |**RGBA (&nbsp;123, &nbsp;104, &nbsp;238, &nbsp;1 @ NO__T-5)** |![Умеренный синевато-серый](./media/function-colors/color-mediumslateblue.png) |
| **Color.MediumSpringGreen** |**Колорвалуе ("#00fa9a" &nbsp;)**<br>**Колорвалуе ("Медиумспринггрин" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;250, &nbsp;154, &nbsp;1 @ NO__T-5)** |![Умеренный весенне-зеленый](./media/function-colors/color-mediumspringgreen.png) |
| **Color.MediumTurquoise** |**Колорвалуе ("#48d1cc" &nbsp;)**<br>**Колорвалуе ("МЕДИУМТУРКУОИСЕ" &nbsp;)** |**RGBA (&nbsp;72, &nbsp;209, &nbsp;204, &nbsp;1 @ NO__T-5)** |![Умеренно-бирюзовый](./media/function-colors/color-mediumturquoise.png) |
| **Color.MediumVioletRed** |**Колорвалуе ("#c71585" &nbsp;)**<br>**Колорвалуе ("Медиумвиолетред" &nbsp;)** |**RGBA (&nbsp;199, &nbsp;21, &nbsp;133, &nbsp;1 @ NO__T-5)** |![Умеренный фиолетово-красный](./media/function-colors/color-mediumvioletred.png) |
| **Color.MidnightBlue** |**Колорвалуе ("#191970" &nbsp;)**<br>**Колорвалуе ("миднигхтблуе" &nbsp;)** |**RGBA (&nbsp;25, &nbsp;25, &nbsp;112, &nbsp;1 @ NO__T-5)** |![Сине-черный](./media/function-colors/color-midnightblue.png) |
| **Color.MintCream** |**Колорвалуе ("#f5fffa" &nbsp;)**<br>**Колорвалуе ("Минткреам" &nbsp;)** |**RGBA (&nbsp;245, &nbsp;255, &nbsp;250, &nbsp;1 @ NO__T-5)** |![Бледный фисташковый](./media/function-colors/color-mintcream.png) |
| **Color.MistyRose** |**Колорвалуе ("#ffe4e1" &nbsp;)**<br>**Колорвалуе ("МИСТИРОСЕ" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;228, &nbsp;225, &nbsp;1 @ NO__T-5)** |![Бледно-розовый](./media/function-colors/color-mistyrose.png) |
| **Color.Moccasin** |**Колорвалуе ("#ffe4b5" &nbsp;)**<br>**Колорвалуе ("Моккасин" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;228, &nbsp;181, &nbsp;1 @ NO__T-5)** |![Болотный](./media/function-colors/color-moccasin.png) |
| **Color.NavajoWhite** |**Колорвалуе ("#ffdead" &nbsp;)**<br>**Колорвалуе ("наважовхите" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;222, &nbsp;173, &nbsp;1 @ NO__T-5)** |![Папирус](./media/function-colors/color-navajowhite.png) |
| **Color.Navy** |**Колорвалуе ("#000080" &nbsp;)**<br>**Колорвалуе ("ВМФ" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;0, &nbsp;128, &nbsp;1 @ NO__T-5)** |![Глубокий темно-синий](./media/function-colors/color-navy.png) |
| **Color.OldLace** |**Колорвалуе ("#fdf5e6" &nbsp;)**<br>**Колорвалуе ("ОЛДЛАЦЕ" &nbsp;)** |**RGBA (&nbsp;253, &nbsp;245, &nbsp;230, &nbsp;1 @ NO__T-5)** |![Кремовый](./media/function-colors/color-oldlace.png) |
| **Color.Olive** |**Колорвалуе ("#808000" &nbsp;)**<br>**Колорвалуе ("Оливковый" &nbsp;)** |**RGBA (&nbsp;128, &nbsp;128, &nbsp;0, &nbsp;1 @ NO__T-5)** |![Оливковый](./media/function-colors/color-olive.png) |
| **Color.OliveDrab** |**Колорвалуе ("#6b8e23" &nbsp;)**<br>**Колорвалуе ("ОливеДраб" &nbsp;)** |**RGBA (&nbsp;107, &nbsp;142, &nbsp;35, &nbsp;1 @ NO__T-5)** |![Зеленовато-оливковый](./media/function-colors/color-olivedrab.png) |
| **Color.Orange** |**Колорвалуе ("#ffa500" &nbsp;)**<br>**Колорвалуе ("оранжевый" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;165, &nbsp;0, &nbsp;1 @ NO__T-5)** |![Оранжевый](./media/function-colors/color-orange.png) |
| **Color.OrangeRed** |**Колорвалуе ("#ff4500" &nbsp;)**<br>**Колорвалуе ("ОРАНЖЕРЕД" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;69, &nbsp;0, &nbsp;1 @ NO__T-5)** |![Оранжево-красный](./media/function-colors/color-orangered.png) |
| **Color.Orchid** |**Колорвалуе ("#da70d6" &nbsp;)**<br>**Колорвалуе ("лиловый умеренный" &nbsp;)** |**RGBA (&nbsp;218, &nbsp;112, &nbsp;214, &nbsp;1 @ NO__T-5)** |![Лиловый](./media/function-colors/color-orchid.png) |
| **Color.PaleGoldenRod** |**Колорвалуе ("#eee8aa" &nbsp;)**<br>**Колорвалуе ("палеголденрод" &nbsp;)** |**RGBA (&nbsp;238, &nbsp;232, &nbsp;170, &nbsp;1 @ NO__T-5)** |![Тусклый желто-зеленый](./media/function-colors/color-palegoldenrod.png) |
| **Color.PaleGreen** |**Колорвалуе ("#98fb98" &nbsp;)**<br>**Колорвалуе ("PaleGreen" &nbsp;)** |**RGBA (&nbsp;152, &nbsp;251, &nbsp;152, &nbsp;1 @ NO__T-5)** |![Бледно-зеленый](./media/function-colors/color-palegreen.png) |
| **Color.PaleTurquoise** |**Колорвалуе ("#afeeee" &nbsp;)**<br>**Колорвалуе ("ПАЛЕТУРКУОИСЕ" &nbsp;)** |**RGBA (&nbsp;175, &nbsp;238, &nbsp;238, &nbsp;1 @ NO__T-5)** |![Бледно-бирюзовый](./media/function-colors/color-paleturquoise.png) |
| **Color.PaleVioletRed** |**Колорвалуе ("#db7093" &nbsp;)**<br>**Колорвалуе ("Палевиолетред" &nbsp;)** |**RGBA (&nbsp;219, &nbsp;112, &nbsp;147, &nbsp;1 @ NO__T-5)** |![Бледный фиолетово-красный](./media/function-colors/color-palevioletred.png) |
| **Color.PapayaWhip** |**Колорвалуе ("#ffefd5" &nbsp;)**<br>**Колорвалуе ("папайавхип" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;239, &nbsp;213, &nbsp;1 @ NO__T-5)** |![Папайя](./media/function-colors/color-papayawhip.png) |
| **Color.PeachPuff** |**Колорвалуе ("#ffdab9" &nbsp;)**<br>**Колорвалуе ("Пеачпуфф" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;218, &nbsp;185, &nbsp;1 @ NO__T-5)** |![Персик](./media/function-colors/color-peachpuff.png) |
| **Color.Peru** |**Колорвалуе ("#cd853f" &nbsp;)**<br>**Колорвалуе ("Перу" &nbsp;)** |**RGBA (&nbsp;205, &nbsp;133, &nbsp;63, &nbsp;1 @ NO__T-5)** |![Рыжевато-коричневый](./media/function-colors/color-peru.png) |
| **Color.Pink** |**Колорвалуе ("#ffc0cb" &nbsp;)**<br>**Колорвалуе ("розовый" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;192, &nbsp;203, &nbsp;1 @ NO__T-5)** |![Розовый](./media/function-colors/color-pink.png) |
| **Color.Plum** |**Колорвалуе ("#dda0dd" &nbsp;)**<br>**Колорвалуе ("Плам" &nbsp;)** |**RGBA (&nbsp;221, &nbsp;160, &nbsp;221, &nbsp;1 @ NO__T-5)** |![Сливовый](./media/function-colors/color-plum.png) |
| **Color.PowderBlue** |**Колорвалуе ("#b0e0e6" &nbsp;)**<br>**Колорвалуе ("Повдерблуе" &nbsp;)** |**RGBA (&nbsp;176, &nbsp;224, &nbsp;230, &nbsp;1 @ NO__T-5)** |![Зеленовато-голубой](./media/function-colors/color-powderblue.png) |
| **Color.Purple** |**Колорвалуе ("#800080" &nbsp;)**<br>**Колорвалуе ("СИРЕНЕВЫй" &nbsp;)** |**RGBA (&nbsp;128, &nbsp;0, &nbsp;128, &nbsp;1 @ NO__T-5)** |![Сиреневый](./media/function-colors/color-purple.png) |
| **Color.Red** |**Колорвалуе ("#ff0000" &nbsp;)**<br>**Колорвалуе ("Red" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;0, &nbsp;0, &nbsp;1 @ NO__T-5)** |![Красный](./media/function-colors/color-red.png) |
| **Color.RosyBrown** |**Колорвалуе ("#bc8f8f" &nbsp;)**<br>**Колорвалуе ("росибровн" &nbsp;)** |**RGBA (&nbsp;188, &nbsp;143, &nbsp;143, &nbsp;1 @ NO__T-5)** |![Лилово-коричневый](./media/function-colors/color-rosybrown.png) |
| **Color.RoyalBlue** |**Колорвалуе ("#4169e1" &nbsp;)**<br>**Колорвалуе ("Ройалблуе" &nbsp;)** |**RGBA (&nbsp;65, &nbsp;105, &nbsp;225, &nbsp;1 @ NO__T-5)** |![Ярко-синий](./media/function-colors/color-royalblue.png) |
| **Color.SaddleBrown** |**Колорвалуе ("#8b4513" &nbsp;)**<br>**Колорвалуе ("САДДЛЕБРОВН" &nbsp;)** |**RGBA (&nbsp;139, &nbsp;69, &nbsp;19, &nbsp;1 @ NO__T-5)** |![Темно-коричневый](./media/function-colors/color-saddlebrown.png) |
| **Color.Salmon** |**Колорвалуе ("#fa8072" &nbsp;)**<br>**Колорвалуе ("оранжево" &nbsp;)** |**RGBA (&nbsp;250, &nbsp;128, &nbsp;114, &nbsp;1 @ NO__T-5)** |![Оранжево-розовый](./media/function-colors/color-salmon.png) |
| **Color.SandyBrown** |**Колорвалуе ("#f4a460" &nbsp;)**<br>**Колорвалуе ("сандибровн" &nbsp;)** |**RGBA (&nbsp;244, &nbsp;164, &nbsp;96, &nbsp;1 @ NO__T-5)** |![Песочно-коричневый](./media/function-colors/color-sandybrown.png) |
| **Color.SeaGreen** |**Колорвалуе ("#2e8b57" &nbsp;)**<br>**Колорвалуе ("Сеагрин" &nbsp;)** |**RGBA (&nbsp;46, &nbsp;139, &nbsp;87, &nbsp;1 @ NO__T-5)** |![Зеленое море](./media/function-colors/color-seagreen.png) |
| **Color.SeaShell** |**Колорвалуе ("#fff5ee" &nbsp;)**<br>**Колорвалуе ("ВЫБРОШЕННАЯ" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;245, &nbsp;238, &nbsp;1 @ NO__T-5)** |![Морская ракушка](./media/function-colors/color-seashell.png) |
| **Color.Sienna** |**Колорвалуе ("#a0522d" &nbsp;)**<br>**Колорвалуе ("Сиенна" &nbsp;)** |**RGBA (&nbsp;160, &nbsp;82, &nbsp;45, &nbsp;1 @ NO__T-5)** |![Охра](./media/function-colors/color-sienna.png) |
| **Color.Silver** |**Колорвалуе ("#c0c0c0" &nbsp;)**<br>**Колорвалуе ("серебро" &nbsp;)** |**RGBA (&nbsp;192, &nbsp;192, &nbsp;192, &nbsp;1 @ NO__T-5)** |![Светло-серый](./media/function-colors/color-silver.png) |
| **Color.SkyBlue** |**Колорвалуе ("#87ceeb" &nbsp;)**<br>**Колорвалуе ("Скиблуе" &nbsp;)** |**RGBA (&nbsp;135, &nbsp;206, &nbsp;235, &nbsp;1 @ NO__T-5)** |![Небесно-синий](./media/function-colors/color-skyblue.png) |
| **Color.SlateBlue** |**Колорвалуе ("#6a5acd" &nbsp;)**<br>**Колорвалуе ("СЛАТЕБЛУЕ" &nbsp;)** |**RGBA (&nbsp;106, &nbsp;90, &nbsp;205, &nbsp;1 @ NO__T-5)** |![Синевато-серый](./media/function-colors/color-slateblue.png) |
| **Color.SlateGray** |**Колорвалуе ("#708090" &nbsp;)**<br>**Колорвалуе ("Слатеграй" &nbsp;)** |**RGBA (&nbsp;112, &nbsp;128, &nbsp;144, &nbsp;1 @ NO__T-5)** |![Серо-синий](./media/function-colors/color-slategray.png) |
| **Color.SlateGrey** |**Колорвалуе ("#708090" &nbsp;)**<br>**Колорвалуе ("слатегрэй" &nbsp;)** |**RGBA (&nbsp;112, &nbsp;128, &nbsp;144, &nbsp;1 @ NO__T-5)** |![Темный серо-синий](./media/function-colors/color-slategrey.png) |
| **Color.Snow** |**Колорвалуе ("#fffafa" &nbsp;)**<br>**Колорвалуе ("снег" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;250, &nbsp;250, &nbsp;1 @ NO__T-5)** |![Снежно-белый](./media/function-colors/color-snow.png) |
| **Color.SpringGreen** |**Колорвалуе ("#00ff7f" &nbsp;)**<br>**Колорвалуе ("СПРИНГГРИН" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;255, &nbsp;127, &nbsp;1 @ NO__T-5)** |![Весенне-зеленый](./media/function-colors/color-springgreen.png) |
| **Color.SteelBlue** |**Колорвалуе ("#4682b4" &nbsp;)**<br>**Колорвалуе ("Стилблуе" &nbsp;)** |**RGBA (&nbsp;70, &nbsp;130, &nbsp;180, &nbsp;1 @ NO__T-5)** |![Синевато-стальной](./media/function-colors/color-steelblue.png) |
| **Color.Tan** |**Колорвалуе ("#d2b48c" &nbsp;)**<br>**Колорвалуе ("Tan" &nbsp;)** |**RGBA (&nbsp;210, &nbsp;180, &nbsp;140, &nbsp;1 @ NO__T-5)** |![Светло-коричневый](./media/function-colors/color-tan.png) |
| **Color.Teal** |**Колорвалуе ("#008080" &nbsp;)**<br>**Колорвалуе ("бирюзовый" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;128, &nbsp;128, &nbsp;1 @ NO__T-5)** |![Сине-зеленый](./media/function-colors/color-teal.png) |
| **Color.Thistle** |**Колорвалуе ("#d8bfd8" &nbsp;)**<br>**Колорвалуе ("СИСТЛЕ" &nbsp;)** |**RGBA (&nbsp;216, &nbsp;191, &nbsp;216, &nbsp;1 @ NO__T-5)** |![Чертополох](./media/function-colors/color-thistle.png) |
| **Color.Tomato** |**Колорвалуе ("#ff6347" &nbsp;)**<br>**Колорвалуе ("значение томатный" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;99, &nbsp;71, &nbsp;1 @ NO__T-5)** |![Томат](./media/function-colors/color-tomato.png) |
| **Цвет. прозрачный** |**Колорвалуе ("#00000000" &nbsp;)**<br>**Колорвалуе ("прозрачный" &nbsp;)** |**RGBA (&nbsp;0, &nbsp;0, &nbsp;0, &nbsp;0 @ NO__T-5)** |![прозрачное](./media/function-colors/color-transparent.png) |
| **Color.Turquoise** |**Колорвалуе ("#40e0d0" &nbsp;)**<br>**Колорвалуе ("бирюзовый" &nbsp;)** |**RGBA (&nbsp;64, &nbsp;224, &nbsp;208, &nbsp;1 @ NO__T-5)** |![Бирюзовый](./media/function-colors/color-turquoise.png) |
| **Color.Violet** |**Колорвалуе ("#ee82ee" &nbsp;)**<br>**Колорвалуе ("фиолетовый" &nbsp;)** |**RGBA (&nbsp;238, &nbsp;130, &nbsp;238, &nbsp;1 @ NO__T-5)** |![Фиолетовый](./media/function-colors/color-violet.png) |
| **Color.Wheat** |**Колорвалуе ("#f5deb3" &nbsp;)**<br>**Колорвалуе ("ВХЕАТ" &nbsp;)** |**RGBA (&nbsp;245, &nbsp;222, &nbsp;179, &nbsp;1 @ NO__T-5)** |![Пшеничный](./media/function-colors/color-wheat.png) |
| **Color.White** |**Колорвалуе ("#ffffff" &nbsp;)**<br>**Колорвалуе ("белый" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;255, &nbsp;255, &nbsp;1 @ NO__T-5)** |![Белый](./media/function-colors/color-white.png) |
| **Color.WhiteSmoke** |**Колорвалуе ("#f5f5f5" &nbsp;)**<br>**Колорвалуе ("вхитесмоке" &nbsp;)** |**RGBA (&nbsp;245, &nbsp;245, &nbsp;245, &nbsp;1 @ NO__T-5)** |![Дымчато-белый](./media/function-colors/color-whitesmoke.png) |
| **Color.Yellow** |**Колорвалуе ("#ffff00" &nbsp;)**<br>**Колорвалуе ("желтый" &nbsp;)** |**RGBA (&nbsp;255, &nbsp;255, &nbsp;0, &nbsp;1 @ NO__T-5)** |![Желтый](./media/function-colors/color-yellow.png) |
| **Color.YellowGreen** |**Колорвалуе ("#9acd32" &nbsp;)**<br>**Колорвалуе ("ЕЛЛОВГРИН" &nbsp;)** |**RGBA (&nbsp;154, &nbsp;205, &nbsp;50, &nbsp;1 @ NO__T-5)** |![Желто-зеленый](./media/function-colors/color-yellowgreen.png) |
