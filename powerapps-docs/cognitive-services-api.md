---
title: "Использование служб Cognitive Services с PowerApps | Документация Майкрософт"
description: "Создание простого приложения, использующего API-интерфейс Microsoft Cognitive Services для анализа текста."
services: 
suite: powerapps
documentationcenter: na
author: mgblythe
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 07/24/2017
ms.author: mblythe
ms.openlocfilehash: 2767ee72fcf62b626f0376e34f058e72bb3708e3
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2017
---
# <a name="use-cognitive-services-in-powerapps"></a>Использование служб Cognitive Services с PowerApps
Из этой статьи вы узнаете, как создать базовое приложение, использующее [API анализа текста Microsoft Cognitive Services](https://docs.microsoft.com/azure/cognitive-services/text-analytics/overview), чтобы анализировать текст. Мы объясним, как установить API анализа текста и подключиться к нему с помощью [соединителя для анализа текста](https://docs.microsoft.com/connectors/cognitiveservicestextanalytics/). Затем мы покажем, как создать приложение, которое вызывает API.

**Примечание.** Если вы не знакомы с созданием приложений в PowerApps, рекомендуем ознакомиться со статьей [Создание приложения с нуля](get-started-create-from-blank.md), прежде чем подробно изучить эту статью.

## <a name="introduction-to-microsoft-cognitive-services"></a>Общие сведения о Microsoft Cognitive Services
Microsoft Cognitive Services — это набор API-интерфейсов, пакетов SDK и служб, которые помогают сделать ваши приложения более интеллектуальными, привлекательными и доступными. Эти службы позволяют легко добавлять в приложения такие интеллектуальные функции, как обнаружение эмоций и видео, распознавание лиц, речи и визуальных образов, а также понимание речи и языка.

В этой статье мы сосредоточимся на распознавании речи с помощью API анализа текста. Этот API-интерфейс позволяет определять тональность, ключевые фразы, темы и язык текста. Давайте сначала протестируем демоверсию API, а затем зарегистрируемся для получения предварительной версии.

### <a name="try-out-the-text-analytics-api"></a>Тестирование API анализа текста
Для этого API-интерфейса представлена интерактивная демоверсия. Вы можете увидеть принцип его работы и просмотреть JSON-код, возвращаемый службой.

1. Перейдите на страницу [API анализа текста](https://azure.microsoft.com/services/cognitive-services/text-analytics/).
2. В разделе **Оцените работу решения в действии** используйте пример текста или введите собственный текст. Нажмите кнопку **Анализ**. 
   
    ![Демоверсия API анализа текста](./media/cognitive-services-api/text-analytics-demo.png)
3. Отформатированные результаты отобразятся на вкладке **Анализируемый текст**, а ответ в формате JSON — на вкладке **JSON** этой страницы. [JSON](http://json.org/) — это способ представления данных. В нашем случае это данные, возвращаемые API-интерфейсом анализа текста.

## <a name="sign-up-for-the-text-analytics-api"></a>Регистрация для работы с API анализа текста
Этот API-интерфейс доступен в качестве бесплатной предварительной версии и связан с подпиской Azure. Управление API выполняется с помощью портала Azure.

1. Если у вас еще нет подписки Azure, [зарегистрируйтесь, чтобы получить бесплатную подписку](https://azure.microsoft.com/free/).
2. Войдите в учетную запись Azure.
3. На портале Azure перейдите в колонку [Создание](https://go.microsoft.com/fwlink/?LinkId=761108) для Cognitive Services.
4. Введите информацию для API анализа текста, как показано ниже. Выберите ценовую категорию **F0** (бесплатно).
   
    ![Создание API анализа текста](./media/cognitive-services-api/azure-create.png)
5. В левом нижнем углу нажмите кнопку **Создать**.
6. На **панели мониторинга** выберите только что созданный API-интерфейс.
   
    ![Панель мониторинга Azure](./media/cognitive-services-api/azure-dashboard.png)
7. Выберите **Ключи**.
   
    ![Меню Azure](./media/cognitive-services-api/azure-menu-keys.png)
8. Скопируйте любой ключ в правой части экрана. Этот ключ понадобится позже при создании подключения к API.
   
    ![Ключи API](./media/cognitive-services-api/azure-keys.png)

## <a name="build-the-app"></a>Создание приложения
Теперь, когда API анализа текста готов, мы подключимся к нему через PowerApps и создадим приложение, которое вызывает API. У этого приложения будет один экран и такие же функциональные возможности, как у демоверсии на странице API анализа текста. Приступим к созданию.

### <a name="create-the-app-and-add-a-connection"></a>Создание приложения и добавление подключения
Сначала мы создадим пустое приложение для телефона, а затем добавим подключение с помощью соединителя для **анализа текста**. Дополнительные сведения об этих задачах см. в статьях [Создание приложения с нуля](get-started-create-from-blank.md) и [Управление подключениями в PowerApps](add-manage-connections.md).

1. В PowerApps Studio выберите **Файл** > **Создать**, а затем в разделе **Пустое приложение** щелкните **Макет для телефона**.
   
    ![Элементы управления "Пустое приложение" и "Макет для телефона"](./media/cognitive-services-api/blank-app.png)
2. В центральной области щелкните **Подключиться к данным**.
3. В области справа последовательно выберите **Создать подключение** > **Текстовая аналитика**.
   
    ![Источники данных в PowerApps](./media/cognitive-services-api/data-sources.png)
4. Вставьте ключ в поле **Ключ учетной записи**, а затем нажмите кнопку **Создать**.
   
    ![Соединитель для анализа текста](./media/cognitive-services-api/create-connection-ta.png)

### <a name="add-controls-to-the-app"></a>Добавление элементов управления в приложение
Следующий шаг при создании приложения — добавление всех элементов управления. Обычно, создавая приложения, я сразу добавляю формулы для элементов управления. Но в этом случае мы сначала сосредоточимся на элементах управления, а затем добавим некоторые формулы в следующем разделе. На следующем изображении показано приложение со всеми элементами управления.

![Готовое приложение](./media/cognitive-services-api/finished-app-no-data.png)

Выполните действия ниже, чтобы создать такой экран. Если для элемента управления задано имя, оно будет использоваться в формуле в следующем разделе.

1. На вкладке **Главная** щелкните **Новый экран** и выберите **Окно с прокруткой**. 
2. На экране **Screen2** выделите **[Название]** и введите **Анализ текста**.
3. Добавьте элемент управления **Метка** для вводного текста.
4. Добавьте элемент управления **Текстовое поле**, чтобы вводить текст для анализа. Присвойте этому элементу имя **tiTextToAnalyze**. Приложение должно выглядеть приблизительно так:
   
    ![Приложение с заголовком, подзаголовком и текстовым полем](./media/cognitive-services-api/partial-app-step1.png)
5. Добавьте три **флажка** для выбора операций API, которые будут выполняться. Присвойте флажкам имена **chkLanguage**, **chkPhrases** и **chkSentiment**.
6. Добавьте кнопку, чтобы вызывать API после выбора выполняемых операций. Приложение должно выглядеть приблизительно так:
   
    ![Приложение с флажками и кнопкой](./media/cognitive-services-api/partial-app-step2.png)
7. Добавьте три **метки**. В первых двух будут содержаться результаты вызовов API анализа тональности и языка. В третьей — просто общие сведения для коллекции в нижней части экрана.
8. Добавьте **пустую вертикальную коллекцию**, а затем добавьте в нее **метку**. В коллекции будут содержаться результаты вызова API анализа ключевых фраз. Приложение должно выглядеть приблизительно так:
   
    ![Приложение с метками и коллекцией](./media/cognitive-services-api/partial-app-step3.png)
9. В области слева последовательно выберите **Screen1** > **…** (многоточие) > **Удалить**. Этот экран не требуется для нашего приложения.

Мы оставим это приложение только для вызовов API анализа текста. Но вы сможете добавить такие элементы, как логика для отображения и скрытия элементов управления на основе установленных флажков, обработка ошибок, если пользователь не выбрал параметры, и т. д.

### <a name="add-logic-to-make-the-right-api-calls"></a>Добавление логики для корректного выполнения вызовов API
Итак, мы создали приложение с привлекательным интерфейсом, но оно пока не выполняет никаких действий. Мы исправим это чуть позже. Но прежде чем углубиться в детали, рассмотрим принцип работы этого приложения.

1. Приложение выполняет определенные вызовы API в зависимости от установленных флажков в приложении. Если нажать кнопку **Анализировать текст**, приложение выполнит 1, 2 или 3 вызова API.
2. Данные, возвращаемые API, хранятся в трех разных [коллекциях](working-with-variables.md#create-a-collection): **languageCollect**, **sentimentCollect** и **phrasesCollect**.
3. Свойство **Текст** для двух меток и свойство **Элементы** для коллекции обновляются с помощью данных из трех коллекций.

Учитывая все, написанное выше, добавим формулу для свойства **OnSelect** кнопки. И тут происходит все самое интересное.

```
If(chkLanguage.Value=true,

        ClearCollect(languageCollect, TextAnalytics.DetectLanguage({numberOfLanguagesToDetect:1, text:tiTextToAnalyze.Text}).detectedLanguages.name)

);

If(chkPhrases.Value=true,

        ClearCollect(phrasesCollect, TextAnalytics.KeyPhrases({language:"en", text:tiTextToAnalyze.Text}).keyPhrases)

);

If(chkSentiment.Value=true,

        ClearCollect(sentimentCollect, TextAnalytics.DetectSentiment({language:"en", text:tiTextToAnalyze.Text}).score)

)
```

На самом деле ничего сложного, так что давайте разберем каждый фрагмент кода:

* **If** — это простые инструкции. Установив определенный флажок, вызовите API, чтобы выполнить операцию.
* Для каждого вызова укажите соответствующие параметры:
  * Для трех вызовов указан параметр ввода текста **tiTextToAnalyze.Text**.
  * В методе **DetectLanguage()** для параметра **numberOfLanguagesToDetect** жестко задано значение 1. Но этот параметр можно передать на основе определенной логики в приложении.
  * В методах **KeyPhrases()** и **DetectSentiment()** для языка жестко задано значение "en". Но этот параметр можно передать на основе определенной логики в приложении. Например, можно сначала определить язык, а затем установить для этого параметра значение на основе результата, возвращенного методом **DetectLanguage()**.
* Для каждого выполняемого вызова добавьте результаты в соответствующую коллекцию:
  * В коллекцию **languageCollect** добавляется **название** языка, определенного в тексте.
  * В коллекцию **phrasesCollect** добавляются **ключевые фразы**, определенные в тексте.
  * В коллекцию **sentimentCollect** добавляется **балл** тональности текста, от 0 до 1, где 1 — полностью положительная тональность.

### <a name="display-the-results-of-the-api-calls"></a>Отображение результатов вызовов API
Чтобы отобразить результаты вызовов API, добавьте ссылку на соответствующую коллекцию для каждого элемента управления:

1. Для свойства **Текст** метки языка задайте следующее: `"The language detected is " & First(languageCollect).name`.
   
    Функция **First()** возвращает первую (и в нашем случае единственную) запись в коллекции **languageCollect**, и отображается значение поля **name** (единственное поле), связанное с этой записью.
2. Для свойства **Текст** метки тональности задайте следующее: `"The sentiment score is " & Round(First(sentimentCollect.Value).Value, 3)\*100 & "% positive."`.
   
    Эта формула также использует функцию **First()**, возвращает **значение** (0–1) из первой и единственной записи, а затем форматирует его в виде процентов.
3. Для свойства **Элементы** коллекции ключевых фраз задайте следующее: `phrasesCollect`.
   
    В этом случае задействована коллекция, поэтому не нужно, чтобы функция **First()** извлекала одиночное значение. Мы указываем ссылку на коллекцию, а ключевые фразы из коллекции выводятся в виде списка.

## <a name="run-the-app"></a>Запуск приложения
Теперь, когда приложение создано, запустим его, чтобы узнать, как оно работает. На следующем изображении выбраны все три параметра, а текст такой же, как и текст по умолчанию на странице API анализа текста.

![Готовое приложение с данными](./media/cognitive-services-api/finished-app.png)

Если сравнить выходные данные этого приложения с данными на странице API анализа текста в начале этой статьи, можно увидеть, что они совпадают.

Надеемся, что вы больше узнали об API анализа текста и с удовольствием интегрировали его в приложение. Если вам интересно прочесть статьи о других возможностях Cognitive Services (или других службах в целом), сообщите нам об этом. Как всегда, оставляйте отзывы и задавайте вопросы в комментариях.
