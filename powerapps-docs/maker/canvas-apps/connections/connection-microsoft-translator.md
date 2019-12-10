---
title: Общие сведения о подключении к Microsoft Translator | Документация Майкрософт
description: Узнайте, как подключиться к Microsoft Translator, ознакомьтесь с доступными функциями и некоторыми примерами
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 07/12/2017
ms.author: lanced
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 772f74b13d254746b75253012940efd8bda6e9d3
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74723813"
ms.PowerAppsDecimalTransform: true
---
# <a name="connect-to-microsoft-translator-from-power-apps"></a>Подключение к Microsoft Translator из Power Apps
![Microsoft Translator](./media/connection-microsoft-translator/translatoricon.png)

Добавьте в приложение соединитель Microsoft Translator для отображения переведенного текста в элементе управления **Метка**. Например, вы можете создать одно текстовое поле для ввода текста, который нужно перевести, и вторую метку для вывода переведенного текста.

В этой статье рассказано о том, как создать и использовать в приложении подключение к Microsoft Translator, и перечислены доступные функции.

> [!NOTE]
> Этот соединитель ограничен 150 вызовами на пользователя в день.

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

## <a name="connect-to-microsoft-translator"></a>Подключение к Microsoft Translator
1. Откройте Power Apps, выберите **создать**, а затем создайте **пустое приложение**. Выберите макет для телефона или планшета. Макет для планшета обеспечивает больше рабочего пространства:  

   ![Пустое приложение](./media/connection-microsoft-translator/blank-app.png)
2. На панели справа откройте вкладку **Данные**, а затем нажмите кнопку **Добавить источник данных**.
3. Выберите команду **Создать подключение**, а затем — **Microsoft Translator**:  

    ![Подключение к Microsoft Translator](./media/connection-microsoft-translator/addconnection.png)

    ![Подключение к Microsoft Translator](./media/connection-microsoft-translator/add-translator.png)
4. Выберите команду **Создать**. В разделе **Источники данных** появится подключение:  

    ![Подключение к Microsoft Translator](./media/connection-microsoft-translator/translatordatasource.png)

## <a name="use-the-microsoft-translator-connection-in-your-app"></a>Использование подключения к Microsoft Translator в приложении
### <a name="translate-text"></a>Перевод текста
1. В меню **Вставка** выберите **Текст**, а затем — **Ввод текста**. Назначьте элементу управления для ввода текста имя **Source**.  

    ![Переименовать](./media/connection-microsoft-translator/renametosource.png)
2. Добавьте элемент управления **Раскрывающийся список** (**Вставка** > **Элементы управления**), назначьте ему имя **TargetLang**, и расположите его ниже элемента **Source**.
3. Назначьте свойству **[Items](../controls/properties-core.md)** элемента **TargetLang** следующую формулу:  

    `MicrosoftTranslator.Languages()`
4. Добавьте метку, расположите ее ниже элемента управления **TargetLang** и назначьте ее свойству **[Text](../controls/properties-core.md)** следующую формулу:  

    `MicrosoftTranslator.Translate(Source.Text; TargetLang.Selected.Value)`
5. Введите какой-либо текст в поле **Source** и выберите язык в списке **TargetLang**. В метке будет выведен текст, переведенный на выбранный вами язык.  

    ![Перевод текста с английского на испанский язык](./media/connection-microsoft-translator/translate-text.png)

### <a name="speak-translated-text"></a>Озвучивание переведенного текста
Если вы еще этого не сделали, переведите какой-либо текст, следуя инструкциям из предыдущего раздела. Далее используются те же элементы управления.

1. Назначьте свойству **[Items](../controls/properties-core.md)** раскрывающегося списка **TargetLang** следующую формулу:  

    `MicrosoftTranslator.SpeechLanguages()`
2. Переименуйте вторую метку (не **Source**), назначив ей имя **Target**.
3. Добавьте элемент управления **Звук** (**Вставка** > **Мультимедиа**) и назначьте его свойству **Media** следующую формулу:  

    `MicrosoftTranslator.TextToSpeech(Target.Text; TargetLang.Selected.Value)`
4. Нажмите клавишу F5 или кнопку предварительного просмотра (![](./media/connection-microsoft-translator/preview.png)). Введите какой-либо текст в поле **Source**, выберите язык в списке **TargetLang**, а затем нажмите кнопку воспроизведения в элементе управления "Звук".

    Приложение озвучит введенный текст на выбранном вами языке.
5. Нажмите клавишу ESC, чтобы вернуться в рабочую область по умолчанию.

### <a name="detect-the-source-language"></a>Определение исходного языка
В этом разделе используются те же текстовые элементы управления **Source** и **Target**. При желании вы можете создать новые элементы управления, но следите за тем, чтобы в формулах использовались правильные имена.

1. Выберите элемент управления **Target** и назначьте его свойству **[Text](../controls/properties-core.md)** следующую формулу:  

    `MicrosoftTranslator.Detect(Source.Text).Name`
2. Введите какой-либо текст в элемент **Source**.

    В метке будет отображен язык введенного вами текста. Например, при вводе **bonjour** в метке появится значение **Французский**, а при вводе **ciao** — **Итальянский**.

## <a name="view-the-available-functions"></a>Просмотр доступных функций
Это подключение включает следующие функции:

| Имя функции | Description |
| --- | --- |
| [Languages](connection-microsoft-translator.md#languages) |Возвращает все языки, поддерживаемые службой Microsoft Translator. |
| [Translate](connection-microsoft-translator.md#translate) |Переводит текст на указанный язык с помощью службы Microsoft Translator. |
| [Detect](connection-microsoft-translator.md#detect) |Определяет исходный язык текста. |
| [SpeechLanguages](connection-microsoft-translator.md#speechlanguages) |Возвращает языки, доступные для синтеза речи. |
| [TextToSpeech](connection-microsoft-translator.md#texttospeech) |Преобразует указанный текст в речь в виде звукового потока в формате звукозаписи. |

### <a name="languages"></a>Языки
Эта функция возвращает все языки, поддерживаемые службой Microsoft Translator.

#### <a name="input-properties"></a>Входные свойства
Нет.

#### <a name="output-properties"></a>Выходные свойства

| Имя свойства | Тип данных | Требуется | Description |
| --- | --- | --- | --- |
| Код |строка |Нет | |
| Имя |строка |Нет | |

### <a name="translate"></a>Translate
Эта функция переводит текст на указанный язык с помощью службы Microsoft Translator.

#### <a name="input-properties"></a>Входные свойства

| Имя | Тип данных | Требуется | Description |
| --- | --- | --- | --- |
| query |строка |да |Текст, который нужно перевести. |
| languageTo |строка |да |Код целевого языка (например, 'fr'). |
| languageFrom |строка |нет |Исходный язык (если он не указан, Microsoft Translator попытается автоматически распознать язык). Пример: en. |
| category |строка |нет |Категория перевода (по умолчанию 'general'). |

#### <a name="output-properties"></a>Выходные свойства
Нет.

### <a name="detect"></a>Detect
Эта функция распознает исходный язык указанного текста.

#### <a name="input-properties"></a>Входные свойства

| Имя | Тип данных | Требуется | Description |
| --- | --- | --- | --- |
| query |строка |да |Текст, язык которого нужно распознать. |

#### <a name="output-properties"></a>Выходные свойства

| Имя свойства | Тип данных | Требуется | Description |
| --- | --- | --- | --- |
| Код |строка |Нет | |
| Имя |строка |Нет | |

### <a name="speechlanguages"></a>SpeechLanguages
Эта функция возвращает языки, доступные для синтеза речи.

#### <a name="input-properties"></a>Входные свойства
Нет.

#### <a name="output-properties"></a>Выходные свойства

| Имя свойства | Тип данных | Требуется | Description |
| --- | --- | --- | --- |
| Код |строка |Нет | |
| Имя |строка |Нет | |

### <a name="texttospeech"></a>TextToSpeech
Эта функция преобразует заданный текст в речь в виде звукового потока в формате звукозаписи.

#### <a name="input-properties"></a>Входные свойства

| Имя | Тип данных | Требуется | Description |
| --- | --- | --- | --- |
| query |строка |да |Текст, который нужно преобразовать. |
| language |строка |да |Код языка для синтеза речи (например, 'en-us'). |

#### <a name="output-properties"></a>Выходные свойства
Нет.

## <a name="helpful-links"></a>Полезные ссылки
Сведения о всех доступных подключениях см. [здесь](../connections-list.md).  
Узнайте, как [добавлять подключения](../add-manage-connections.md) в приложения.

