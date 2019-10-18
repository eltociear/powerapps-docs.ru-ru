---
title: Создание и построение компонента кода | Документация Майкрософт
description: Начало создания компонента с помощью инструментария платформы компонентов PowerApps
keywords: Платформа компонентов PowerApps, компоненты кода, платформа компонентов
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
ms.openlocfilehash: 286458da2ed7b7b94f92b86355bf8785161ef778
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72347022"
---
# <a name="create-and-build-a-code-component"></a>Создание и построение компонента кода

В этом разделе объясняется, как создавать и развертывать компоненты кода с помощью командной строки PowerApps. Убедитесь, что установлен [Microsoft POWERAPPS CLI](https://aka.ms/PowerAppsCLI).

## <a name="create-a-new-component"></a>Создание нового компонента

Чтобы начать, откройте **Командная строка разработчика для VS 2017** после установки PowerApps CLI.

1. На Командная строка разработчика для VS 2017 создайте новую папку на локальном компьютере, например *К:\усерс\йоур name\Documents\My_PCF_Component* с помощью команды `mkdir <Specify the folder name>`.
2. Перейдите к созданной папке с помощью команды `cd <specify your new folder path>`.
3. Выполните следующую команду, чтобы создать новый проект компонента, передав некоторые основные параметры:

    `pac pcf init --namespace <specify your namespace here> --name <put component name here> --template <component type>`
 
   > [!NOTE]
   > В настоящее время в интерфейсе командной строки PowerApps поддерживаются два типа компонентов: **поле** и **набор данных**.  Для приложений Canvas поддерживается только тип **поля** в экспериментальном предварительном просмотре.

4. Чтобы получить все необходимые зависимости проекта, выполните команду `npm install`.
5. Откройте папку проекта `C:\Users\<your name>\Documents\<My_PCF_Component>` в любой среде разработчика по своему усмотрению и приступите к разработке компонентов кода. Самый быстрый способ начать работу — запустить `code .` из командной строки в `C:\Users\<your name>\Documents\<My_PCF_Component>` Directory. Эта команда открывает проект компонента в Visual Studio Code.

## <a name="build-your-component"></a>Создание компонента

Чтобы создать проект компонента, откройте папку проекта, содержащую `package.json` в Visual Studio Code и используйте команду (Ctrl-Shift-B), а затем выберите параметры сборки. Кроме того, можно быстро создать компонент, используя команду `npm run build` в окне Командная строка разработчика для VS 2017.

> [!TIP]
> Сведения об отладке компонента во время или после операции построения см. в разделе [Отладка компонента кода](debugging-custom-controls.md).

После завершения реализации логики компонента в TypeScript необходимо объединить все элементы компонента кода в файл решения, чтобы можно было импортировать решение в Common Data Service. Дополнительные сведения: [Упаковка компонента кода](import-custom-controls.md)

## <a name="known-configuration-issues-and-workarounds"></a>Известные проблемы конфигурации и способы их решения

**MSB4036 ошибки MSBuild:**

1. Имя задачи в файле проекта совпадает с именем класса задачи.
2. Класс Task является открытым и реализует интерфейс Microsoft. Build. Framework. ITask.
3. Задача правильно объявлена с *\<UsingTask >* в файле проекта или в файлах *. Tasks, расположенных в каталоге Path.

**Разрешением**

1. Откройте Visual Studio Installer. 
1. Для Visual Studio 2017 выберите **изменить**. 
1. Выберите **отдельные компоненты**.
1. В разделе средства кода проверьте **целевые объекты NuGet & задачах сборки**.

**Префикс издателя**

Если компонент создается с помощью инструментария командной строки PowerApps версии ниже 0.4.3, то при попытке повторного импорта файла решения в Common Data Service будет вычтено сообщение об ошибке. Возникает ошибка, так как имя вновь импортированного компонента теперь добавляется с префиксом издателя, чтобы гарантировать его уникальность и избежать конфликтов.

**Обходной путь**:

- Удалите решение, содержащее соответствующий компонент, из Common Data Service. Если компонент уже настроен в форме или сетке, необходимо сначала удалить его, так как решение компонента имело зависимость от конфигурации.  
- Импортируйте новое решение с обновлениями компонента, созданного с помощью последней версии CLI.
- Теперь в формах и сетках можно настроить только что импортированные компоненты.  


<!--2. When the components are created with the publisher prefix in mixed or upper case using the new CLI tooling version, it throws an error while importing the solution. This happens because the updated tooling version (0.4.3 and newer) now enforces the platform standard for lower case publisher prefix.

   **Workaround**:

    Update the solution and customizations to ensure that the associated prefix is modified to lower case and import the new solution into Common Data Service.-->


### <a name="see-also"></a>См. также

[Компоненты кода отладки](debugging-custom-controls.md)<br/>
[Упаковка компонента кода](import-custom-controls.md)<br/>
[Добавление компонентов кода в поле или сущность](add-custom-controls-to-a-field-or-entity.md)<br/>
[Обновление существующих компонентов кода](updating-existing-controls.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](overview.md)
