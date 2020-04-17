---
title: Автоматизация тестов с помощью конвейера Azure с использованием классического редактора | Документация Майкрософт
description: Описание автоматизации наборов тестов и вариантов с помощью классического редактора из конвейера Azure.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/16/2020
ms.author: aheaney
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ecfeeb1f62032008d7ada618afb56e6da8589f40
ms.sourcegitcommit: 223c3d19ec4fbe43fcc7a16b76423c00f8602ecd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81490897"
---
# <a name="automate-tests-with-azure-pipeline-using-classic-editor"></a>Автоматизация тестов с помощью конвейера Azure с использованием классического редактора

В этой статье вы узнаете, как настроить и запустить тесты приложения Canvas, созданные в Test Studio, с помощью [Azure pipelines классического редактора](https://docs.microsoft.com/azure/devops/pipelines/get-started/pipelines-get-started?view=azure-devops#define-pipelines-using-the-classic-interface) в [Azure DevOps Services](https://docs.microsoft.com/azure/devops/user-guide/what-is-azure-devops?view=azure-devops).

Вы можете использовать общедоступный проект на сайте GitHub- [Microsoft/повераппстестаутоматион](https://github.com/microsoft/PowerAppsTestAutomation) , чтобы:

- Автоматизируйте операции входа в приложение.
- Откройте браузер на агенте сборки и выполните набор тестовых случаев и наборов.
- Просмотрите состояние выполнения теста в конвейере Azure DevOps.

## <a name="prerequisites"></a>Предварительные требования

Перед началом работы необходимо выполнить следующие действия.

- [Разветвление](#step-1---fork-the-powerappstestautomation-project) проекта [Microsoft/повераппстестаутоматион](https://github.com/microsoft/PowerAppsTestAutomation) на GitHub.

    > [!NOTE]
    > Общедоступные вилки нельзя сделать частными. Если вы хотите создать частный репозиторий, скопируйте [его](https://help.github.com/github/creating-cloning-and-archiving-repositories/duplicating-a-repository).

- Создайте в репозитории новый [*файл Test URL. JSON*](#step-2---create-test-url-json-file) с тестовыми URL-адресами приложения, которые нужно запустить из конвейера.

### <a name="step-1---fork-the-powerappstestautomation-project"></a>Шаг 1. ветвление проекта Повераппстестаутоматион

[Вилка](https://help.github.com/github/getting-started-with-github/fork-a-repo) — это копия репозитория. Разветвление репозитория позволяет вносить изменения без влияния на исходный проект.

1. Войдите в [GitHub](https://github.com/).

1. Перейдите в репозиторий [Microsoft/повераппстестаутоматион](https://github.com/microsoft/PowerAppsTestAutomation) . Вместо этого можно выполнить поиск по запросу **Microsoft/повераппстестаутоматион** , а затем выбрать репозиторий:

    ![Поиск в GitHub](media/test-studio-classic-pipeline-editor/search-github.png)

1. Выберите **вилку**:

    ![Файла](media/test-studio-classic-pipeline-editor/fork.png)

1. Выберите место, где нужно создать вилку:

    ![Учетная запись ветвления](media/test-studio-classic-pipeline-editor/fork-account.png)

Теперь разветвленный репозиторий будет доступен.

### <a name="step-2---create-test-url-json-file"></a>Шаг 2. Создание файла Test URL. JSON

Файл Test URL. JSON будет содержать URL-адреса набора тестов и тестовых случаев для проверки приложения. Чтобы получить URL-адреса набора тестов приложений и тестовых случаев, выберите [ссылку воспроизвести](working-with-test-studio.md#playing-tests-in-a-browser) в Test Studio.

Пример файла можно найти ```Samples/TestAutomationURLs.json``` в репозитории, который вы создали ранее.

1. Создайте новый файл ```TestURLs.json``` в репозитории или используйте любое другое имя файла. <br> Имя файла и расположение будут сопоставлены в переменных конвейера позже в документе.

1. Скопируйте формат из файла ```Samples/TestAutomationURLs.json```.

1. Обновите раздел тестовые URL-адреса, используя тесты, которые необходимо проверить в приложении.

1. Зафиксируйте изменения в репозитории:

    ![Обновление JSON](media/test-studio-classic-pipeline-editor/json-update.png)

## <a name="create-a-pipeline"></a>Создание конвейера

1. Войдите в экземпляр Azure DevOps.

1. Выберите существующий проект или создайте новый проект.

1. В меню слева выберите **конвейеры** .

1. Выберите **создать конвейер**:

    ![Создание конвейера](media/test-studio-classic-pipeline-editor/create-pipeline.png)

1. Выберите **использовать классический редактор**:

    ![Классический редактор](media/test-studio-classic-pipeline-editor/use-classic-editor.png)

1. Выберите GitHub в качестве источника.

1. При необходимости Авторизуйте подключение GitHub с помощью OAuth или личного маркера доступа:

    ![Конвейер — GitHub](media/test-studio-classic-pipeline-editor/pipeline-github.png)

1. При необходимости измените имя соединения.

1. В правой части входного **репозитория** выберите **...** (многоточие).

1. Введите имя проекта в GitHub, а затем **выберите** его:

    ![Выбор репозитория](media/test-studio-classic-pipeline-editor/select-repo.png)

1. Выберите **Продолжить**.

1. На экране Выбор шаблона выберите **пустое задание**:

    ![Пустое задание](media/test-studio-classic-pipeline-editor/empty-job.png)

1. **Сохраните** конвейер.

## <a name="add-tasks-to-the-pipeline"></a>Добавление задач в конвейер

Теперь вы добавите новые задачи задания и настроите задачи для выполнения тестов из конвейера в этой последовательности:

1. [Настройка разрешения экрана с помощью PowerShell.](#step-1---configure-screen-resolution-using-powershell)

1. [Восстановление пакетов NuGet для решения Повераппстестаутоматион.](#step-2---restore-nuget-packages)

1. [Создайте решение Повераппстестаутоматион.](#step-3---build-the-powerappstestautomation-solution)

1. [Добавьте тесты Visual Studio для Google Chrome.](#step-4---add-visual-studio-tests-for-google-chrome)

1. [Добавление тестов Visual Studio для Mozilla Firefox.](#step-5---add-visual-studio-tests-for-mozilla-firefox)

### <a name="step-1---configure-screen-resolution-using-powershell"></a>Шаг 1. Настройка разрешения экрана с помощью PowerShell

1. Выберите **+** рядом с *заданием агента 1*.

1. Выполните поиск по запросу **PowerShell**.

1. Нажмите кнопку **Добавить** , чтобы добавить задачу PowerShell в задание.

    ![PowerShell](media/test-studio-classic-pipeline-editor/powershell.png)

1. Выберите задачу. <br>
    Можно также обновить отображаемое имя, чтобы *задать для разрешения экрана агента значение 1920 x 1080* или аналогичное.

1. Выберите **встроенный** тип скрипта и введите в окне скрипта следующее:

    ```powershell
    # Set agent screen resolution to 1920x1080 to avoid sizing issues with Portal  
    Set-DisplayResolution -Width 1920 -Height 1080 -Force
    # Wait 10 seconds  
    Start-Sleep -s 10
    # Verify Screen Resolution is set to 1920x1080  
    Get-DisplayResolution
    ```

    ![Скрипт](media/test-studio-classic-pipeline-editor/script.png)

### <a name="step-2---restore-nuget-packages"></a>Шаг 2. восстановление пакетов NuGet

1. Выберите **+** рядом с заданием агента 1.

1. Найдите **NuGet**.

1. Нажмите кнопку Добавить, чтобы добавить задачу NuGet в задание.

1. Выберите задачу.
    <br> Вы также можете обновить отображаемое имя, чтобы **восстановить пакеты NuGet** или аналогичные.

1. Выберите **...** (многоточие) в поле **путь к файлу решения, Packages. config или Project. JSON** .

1. Выберите файл решения Повераппстестаутоматион. sln.

1. Нажмите кнопку **ОК**:

    ![Пакет NuGet](media/test-studio-classic-pipeline-editor/nuget.png)

### <a name="step-3---build-the-powerappstestautomation-solution"></a>Шаг 3. Создание решения Повераппстестаутоматион

1. Выберите **+** рядом с заданием агента 1.

1. Выполните поиск по запросу **сборки Visual Studio**.

1. Нажмите кнопку **Добавить** , чтобы добавить в задание задачу сборки Visual Studio.

1. Выберите задачу.
    <br> Вы также можете обновить отображаемое имя, чтобы **создать решение для автоматизации тестирования Power Apps** или аналогичное.

1. Выберите **...** (многоточие) в поле Конфигурация **решения** .

1. Выберите файл решения Повераппстестаутоматион. sln.

1. Нажмите кнопку **ОК**.

### <a name="step-4---add-visual-studio-tests-for-google-chrome"></a>Шаг 4. Добавление тестов Visual Studio для Google Chrome

1. Выберите **+** рядом с заданием агента 1.

1. Выполните поиск по запросу **Visual Studio Test**.

1. Нажмите кнопку Добавить, чтобы добавить задачу теста Visual Studio в задание.

1. Выберите задачу.
    <br> Вы также можете обновить отображаемое имя, чтобы *запустить тесты автоматизации тестирования Power Apps с помощью \$(бровсертипечроме)* или аналогичного.

1. Удалите записи по умолчанию в текстовом поле тестовые файлы и добавьте следующее:

    ```**\Microsoft.PowerApps.TestAutomation.Tests\bin\\Debug\Microsoft.PowerApps.TestAutomation.Tests.dll```

1. Введите ```TestCategory=PowerAppsTestAutomation``` в **поле Критерий тестового фильтра**.

1. Выберите **тестовый набор содержит тесты пользовательского интерфейса**.

    ![Chrome](media/test-studio-classic-pipeline-editor/chrome.png)

1. Выберите **...** (многоточие) в поле **файл параметров** .

1. Разверните узел **Microsoft. PowerApps. тестаутоматион. Tests**, выберите файл **патестаутоматион. runsettings** и нажмите кнопку **ОК**.

    ![Параметры запуска](media/test-studio-classic-pipeline-editor/runsettings.png)

1. Скопируйте следующие параметры в поле **Переопределение параметров тестового запуска** .

    ```
    -OnlineUsername $(OnlineUsername) -OnlinePassword $(OnlinePassword) -BrowserType $(BrowserTypeChrome) -OnlineUrl $(OnlineUrl) -UsePrivateMode $(UsePrivateMode) -TestAutomationURLFilePath $(TestAutomationURLFilePath) -DriversPath $(ChromeWebDriver)
    ```

    > [!NOTE]
    > Здесь настраиваются переменные в конвейере, представленные выше в виде \$(VariableName).

1. Введите **Запуск тестов автоматизации тестирования в Power Apps с помощью \$(бровсертипечроме)** или аналогичного поля в поле название тестового запуска.

    ![Тестовый запуск](media/test-studio-classic-pipeline-editor/test-run.png)

### <a name="step-5---add-visual-studio-tests-for-mozilla-firefox"></a>Шаг 5. Добавление тестов Visual Studio для Mozilla Firefox

1. Щелкните правой кнопкой мыши задачу **Добавить Visual Studio Tests для Chrome** и выберите команду **клонировать задачи**.

1. Выберите задачу и обновите следующие области.

    1. **Title**: запуск тестов автоматизации тестов в Power Apps с помощью копирования \$(бровсертипефирефокс)

    1.  **Переопределить параметры тестового запуска**

        ```
        -OnlineUsername $(OnlineUsername) -OnlinePassword $(OnlinePassword) -BrowserType $(BrowserTypeFirefox) -OnlineUrl $(OnlineUrl) -UsePrivateMode $(UsePrivateMode) -TestAutomationURLFilePath $(TestAutomationURLFilePath) -DriversPath $(GeckoWebDriver)
        ```

    1.  **Название тестового запуска**: запуск тестов автоматизации тестирования в Power Apps с помощью \$(бровсертипефирефокс)

## <a name="configure-pipeline-variables"></a>Настройка переменных конвейера

Теперь вы настроите переменные конвейера, определенные в добавленных [ранее](#add-tasks-to-the-pipeline)задачах.

1. Перейдите на вкладку **переменные** .

2. Выберите **Добавить** и повторите этот шаг, чтобы настроить следующие переменные:

| Имя переменной             | Значение переменной                                                                                                                 |
|---------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| бровсертипечроме         | Chrome                                                                                                                         |
| бровсертипефирефокс        | Firefox.                                                                                                                        |
| онлинеурл                 | <https://make.powerapps.com>                                                                                                   |
| тестаутоматионурлфилепас | ```$(Build.SourcesDirectory)\<test URL file>.json``` <br>**Примечание.** Это файл файла [*Test URLs. JSON*](#step-2---create-test-url-json-file) , созданный ранее.                      |
| усеприватемоде            | true                                                                                                                           |
| онлинеусернаме            | Введите Azure Active Directory адрес электронной почты контекста пользователя, который будет входить в приложение. Тесты будут выполняться в контексте этой учетной записи пользователя.\> |

1. Выберите Добавить и введите **онлинепассворд** в поле имя переменной.

1. Проверьте изображение блокировки, чтобы сделать эту переменную секретной.

    ![Переменные](media/test-studio-classic-pipeline-editor/variables.png)

1. **Сохраните** конфигурации конвейера.

## <a name="run-and-analyze-tests"></a>Выполнение и анализ тестов

Чтобы проверить успешное выполнение тестов, выберите **очередь** и щелкните **выполнить**. Задание будет запущено.

![Запустить задание](media/test-studio-classic-pipeline-editor/run-job.png)

При выполнении задания выберите задание, чтобы просмотреть подробные сведения о состоянии каждой из задач, которые выполняются:

![Сведения о задании](media/test-studio-classic-pipeline-editor/job-details.png)

После завершения задания можно просмотреть общие сведения о задании высокого уровня и все ошибки или предупреждения. Выбрав вкладку тест, можно просмотреть конкретные сведения о выполненных тестовых случаях.

В следующем примере показано, что при выполнении тестов с помощью браузера Chrome произошел сбой по крайней мере одного из наших тестовых случаев:

![Chrome — сбой](media/test-studio-classic-pipeline-editor/chrome-failed.png)

Выберите тест **рунтестаутоматион** , чтобы просмотреть подробные сведения о том, что тестовый случай завершился ошибкой. На *вкладке вложения*можно просмотреть сводку выполнения теста и тестовые случаи, которые завершились сбоем или были переданы в наборе тестов.

![Вкладка "вложения"](media/test-studio-classic-pipeline-editor/attachments-tab.png)

> [!NOTE]
> При выполнении набора тестов вы увидите сводку о пройденных и неудачных тестовых случаях. При выполнении тестового случая вы увидите конкретные сведения об ошибке для всех данных трассировки, если они доступны.

## <a name="known-limitations"></a>Известные ограничения

- Многофакторная идентификация не поддерживается.

- Internet Explorer 11 и Microsoft ребр не поддерживают браузеры.

- Сводка теста будет сообщать о результатах одного теста в браузере. Результат теста будет содержать 1 или несколько тестовых случаев или результатов набора тестов.   

- Любой процесс проверки подлинности, кроме Azure Active Directory последовательности входа, требует настройки процесса входа в решении **повераппстестаутоматион** .

### <a name="see-also"></a>См. также:

- [Обзор Test Studio](test-studio.md)
- [Использование Test Studio](working-with-test-studio.md)