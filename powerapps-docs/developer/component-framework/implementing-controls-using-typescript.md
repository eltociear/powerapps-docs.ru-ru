---
title: Реализация компонентов кода с помощью TypeScript | MicrosoftDocs
description: Реализация компонентов кода с помощью TypeScript
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 669bf03d7869d6fd625288a65a305a3a458cfde4
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025764"
---
# <a name="implement-components-using-typescript"></a>Реализация компонентов с помощью TypeScript

В этом разделе описывается процесс создания нового компонента кода в TypeScript с помощью интерфейса командной строки PowerApps. В этом учебнике мы создадим пример компонента линейного кода, который позволяет пользователям изменять числовые значения с помощью визуального ползунка вместо ввода значений в поле. 

Ниже перечислены артефакты, необходимые для построения компонентов кода.

1. [Создание нового проекта компонента](#creating-a-new-component-project)
2. [Реализация манифеста](#implementing-manifest)
3. [Реализация логики компонента с помощью TypeScript](#implementing-component-logic)
4. [Добавление стиля в компоненты кода](#adding-style-to-the-code-component)
5. [Упаковка компонентов кода](#packaging-your-code-components)

## <a name="creating-a-new-component-project"></a>Создание нового проекта компонента

Чтобы создать новый проект, выполните следующие действия.

1. Откройте окно **Командная строка РАЗРАБОТЧИКА VS 2017** .
1. Создайте новую папку для проекта с помощью следующей команды: 
    ```CLI
    mkdir LinearComponent
    ```

1. Перейдите в папку Component с помощью команды `cd LinearComponent`. 
   
1. Создайте новый проект компонента, передав базовые параметры с помощью команды.

   ```CLI
    pac pcf init --namespace SampleNamespace --name TSLinearInputComponent --template field
    ``` 

1. Установите средства сборки проекта с помощью команды `npm install`. 
1. Откройте папку проекта `C:\Users\<your name>\Documents\<My_code_Component>` в среде разработчика по своему усмотрению и приступайте к разработке компонентов кода. Самый быстрый способ запустить это, запустив `code .` из командной строки в `C:\Users\<your name>\Documents\<My_code_Component>` Directory. Эта команда открывает проект компонента в Visual Studio Code.

## <a name="implementing-manifest"></a>Реализация манифеста

Manifest — это XML-файл, содержащий метаданные компонента кода. Он также определяет поведение компонента кода. В этом руководстве этот файл манифеста создается в подпапке `<Your component Name>`. При открытии файла `ControlManifest.Input.xml` в Visual Studio Code можно заметить, что файл манифеста предопределен с некоторыми свойствами. Дополнительные сведения: [manifest](manifest-schema-reference/manifest.md).

Внесите изменения в предопределенный файл манифеста, как показано ниже:

1. [Управляющий](manifest-schema-reference/control.md) узел определяет пространство имен, версию и отображаемое имя компонента кода. Теперь определите каждое свойство узла [элемента управления](manifest-schema-reference/control.md) , как показано ниже:

   - **пространство имен**: пространство имен компонента кода. 
   - **Конструктор**: конструктор компонента кода.
   - **Версия**: версия компонента. При каждом обновлении компонента необходимо обновить версию, чтобы увидеть последние изменения в среде выполнения.
   - **отобразить-Name-Key**: имя компонента кода, отображаемого в пользовательском интерфейсе.
   - **Description-Name-ключ**: описание компонента кода, отображаемого в пользовательском интерфейсе.
   - **тип элемента управления**: тип компонента кода. Поддерживаются только *стандартные* типы компонентов кода.

     ```XML
      <?xml version="1.0" encoding="utf-8" ?>
      <manifest>
      <control namespace="SampleNameSpace" constructor="TSLinearInputComponent" version="1.0.0" display-name-key="Linear Input Component" description-key="Allows you to enter the numeric values using the visual slider." control-type="standard">
     ```

2. Узел [свойств](manifest-schema-reference/property.md) определяет свойства компонента кода, например определение типа данных поля. Узел свойства указан как дочерний элемент в элементе `control`. Определите узел [Свойства](manifest-schema-reference/property.md) , как показано ниже:

   - **Name**: имя свойства.
   - **отобразить-Name-Key**: отображаемое имя свойства, отображаемого в пользовательском интерфейсе.
   - **Description-Name-ключ**: описание свойства, отображаемого в пользовательском интерфейсе. 
   - **of-Type-Group**. параметр [of-Type-Group](manifest-schema-reference/type-group.md) используется, если требуется более двух полей типа данных. Добавьте элемент [типа Group](manifest-schema-reference/type-group.md) в качестве одноуровневого элемента в элемент `property` в манифесте. `of-type-group` указывает значение компонента и может содержать значения целых чисел, валют, чисел с плавающей запятой или десятичных значений.
   - **Использование**: имеет два свойства, *связанные* и *входные данные*. Привязанные свойства привязываются только к значению поля. Входные свойства либо привязываются к полю, либо позволяют использовать статическое значение.
   - **обязательный**: определяет, является ли свойство обязательным.

     ```XML
      <property name="sliderValue" display-name-key="sliderValue_Display_Key" description-key="sliderValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" />
      ```
3. Узел [ресурсы](manifest-schema-reference/resources.md) определяет визуализацию компонента кода. Он содержит все ресурсы, которые создают визуализацию и стилизацию компонента кода. [Код](manifest-schema-reference/code.md) указывается как дочерний элемент в элементе Resources. Определите [ресурсы](manifest-schema-reference/resources.md) , как показано ниже:

   - **Code**: указывает путь, по которому расположены все файлы ресурсов.
 
      ```XML
      <resources>
        <code path="index.ts" order="1" />
        <css path="css/TS_LinearInputComponent.css" order="1" />
        </resources>
        ```
      Общий файл манифеста должен выглядеть примерно так: 

     ```XML
      <?xml version="1.0" encoding="utf-8" ?>
      <manifest>
      <control namespace="SampleNamespace" constructor="TSLinearInputComponent" version="1.0.0" display-name-key="Linear Input Component" description-key="Allows you to enter the numeric values using the visual slider." control-type="standard">
        <type-group name="numbers">
          <type>Whole.None</type>
          <type>Currency</type>
          <type>FP</type>
          <type>Decimal</type>
         </type-group>
        <property name="sliderValue" display-name-key="sliderValue_Display_Key" description-key="sliderValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" />
       <resources>
         <code path="index.ts" order="1" />
         <css path="css/TS_LinearInputComponent.css" order="1" />
       </resources>
      </control>
     </manifest>
     ```

4. Сохраните изменения в файле `ControlManifest.Input.xml`.
5. Теперь создайте новую папку в папке `TSLinearInputComponent` и назовите ее как **CSS**.
6. Создайте CSS-файл, чтобы [Добавить к компоненту кода стили](#adding-style-to-the-code-component).
7. Создайте проект компонента с помощью команды `npm run build`.
8. Сборка создает обновленный файл объявления типа TypeScript в папке `TSLinearInputComponent/generated`.

## <a name="implementing-component-logic"></a>Реализация логики компонента

Следующим шагом после реализации файла манифеста является реализация логики компонента с помощью TypeScript. Логика компонента должна быть реализована в файле `index.ts`. При открытии файла `index.ts` в Visual Studio Code можно заметить, что четыре базовых класса являются предопределенными. Теперь давайте реализуем логику для компонента кода. 

1. Откройте файл `index.ts` в любом редакторе кода.
2. Обновите класс `TSLinearInputComponent` следующим кодом:

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
export class TSLinearInputComponent
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // Value of the field is stored and used inside the component
  private _value: number;
  // PowerApps component framework delegate which will be assigned to this object which would be called whenever any update happens.
  private _notifyOutputChanged: () => void;
  // label element created as part of this component
  private labelElement: HTMLLabelElement;
  // input element that is used to create the range slider
  private inputElement: HTMLInputElement;
  // reference to the component container HTMLDivElement
  // This element contains all elements of our code component example
  private _container: HTMLDivElement;
  // reference to PowerApps component framework Context object
  private _context: ComponentFramework.Context<IInputs>;
  // Event Handler 'refreshData' reference
  private _refreshData: EventListenerOrEventListenerObject;

  constructor() {}

  public init(
    context: ComponentFramework.Context<IInputs>,
    notifyOutputChanged: () => void,
    state: ComponentFramework.Dictionary,
    container: HTMLDivElement
  ) {
    this._context = context;
    this._container = document.createElement("div");
    this._notifyOutputChanged = notifyOutputChanged;
    this._refreshData = this.refreshData.bind(this);
    // creating HTML elements for the input type range and binding it to the function which refreshes the component data
    this.inputElement = document.createElement("input");
    this.inputElement.setAttribute("type", "range");
    this.inputElement.addEventListener("input", this._refreshData);
    //setting the max and min values for the component.
    this.inputElement.setAttribute("min", "1");
    this.inputElement.setAttribute("max", "1000");
    this.inputElement.setAttribute("class", "linearslider");
    this.inputElement.setAttribute("id", "linearrangeinput");
    // creating a HTML label element that shows the value that is set on the linear range component
    this.labelElement = document.createElement("label");
    this.labelElement.setAttribute("class", "TS_LinearRangeLabel");
    this.labelElement.setAttribute("id", "lrclabel");
    // retrieving the latest value from the component and setting it to the HTML elements.
    this._value = context.parameters.sliderValue.raw
      ? context.parameters.sliderValue.raw
      : 0;
    this.inputElement.setAttribute(
      "value",
      context.parameters.sliderValue.formatted
        ? context.parameters.sliderValue.formatted
        : "0"
    );
    this.labelElement.innerHTML = context.parameters.sliderValue.formatted
      ? context.parameters.sliderValue.formatted
      : "0";
    // appending the HTML elements to the component's HTML container element.
    this._container.appendChild(this.inputElement);
    this._container.appendChild(this.labelElement);
    container.appendChild(this._container);
  }

  /**
   * Updates the values to the internal value variable we are storing and also updates the html label that displays the value
   * @param context : The "Input Properties" containing the parameters, component metadata and interface functions
   */

  public refreshData(evt: Event): void {
    this._value = (this.inputElement.value as any) as number;
    this.labelElement.innerHTML = this.inputElement.value;
    this._notifyOutputChanged();
  }

  public updateView(context: ComponentFramework.Context<IInputs>): void {
    // storing the latest context from the control.
    this._value = context.parameters.sliderValue.raw
      ? context.parameters.sliderValue.raw
      : 0;
    this._context = context;
    this.inputElement.setAttribute(
      "value",
      context.parameters.sliderValue.formatted
        ? context.parameters.sliderValue.formatted
        : ""
    );
    this.labelElement.innerHTML = context.parameters.sliderValue.formatted
      ? context.parameters.sliderValue.formatted
      : "";
  }

  public getOutputs(): IOutputs {
    return {
      sliderValue: this._value
    };
  }

  public destroy() {
    this.inputElement.removeEventListener("input", this._refreshData);
  }
}

```

3. Перестройте проект с помощью команды `npm run build`. 
 
4. Компонент компилируется в папку `out/controls/TSLinearInputComponent`. К артефактам сборки относятся:

   - пакет пакета. js — исходный код компонента. 
   - Контролманифест. XML — фактический файл манифеста компонента, который загружается в Common Data Serviceную организацию.

## <a name="adding-style-to-the-code-component"></a>Добавление стиля в компонент кода

Разработчики и руководители приложений могут определить их стили для визуального представления их компонентов кода с помощью CSS. CSS позволяет разработчикам описывать представление компонентов кода, включая стиль, цвета, макеты и шрифты. Метод [init](reference/control/init.md) линейного входного компонента создает элемент ввода и задает для атрибута класса значение `linearslider`. Стиль класса `linearslider` определяется в отдельном `CSS`ном файле. Дополнительные ресурсы компонентов, такие как файлы `CSS`, можно добавить в компонент кода для поддержки дальнейшей настройки.

1. Создайте новую подпапку `css` в папке `TSLinearInputComponent`. 
2. Создайте новый файл `TS_LinearInputComponent.css` во вложенной папке `css`. 
3. Добавьте следующее содержимое стиля в файл `TS_LinearInputComponent.css`:

    ```CSS
    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider {
      margin: 1px 0;
      background: transparent;
      -webkit-appearance: none;
      width: 100%;
      padding: 0;
      height: 24px;
      -webkit-tap-highlight-color: transparent
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider:focus {
      outline: none;
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-webkit-slider-runnable-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-webkit-slider-thumb {
      background: #666;
      border: 0 solid #f00;
      height: 24px;
      width: 10px;
      border-radius: 48px;
      cursor: pointer;
      opacity: 1;
      -webkit-appearance: none;
      margin-top: -12px
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-moz-range-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-moz-range-thumb {
      background: #666;
      border: 0 solid #f00;
      height: 24px;
      width: 10px;
      border-radius: 48px;
      cursor: pointer;
      opacity: 1;
      -webkit-appearance: none;
      margin-top: -12px
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-ms-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-ms-thumb {
      background: #666;
      border: 0 solid #f00;
      height: 24px;
      width: 10px;
      border-radius: 48px;
      cursor: pointer;
      opacity: 1;
      -webkit-appearance: none;
    }
    ```

5. Сохраните файл `TS_LinearInputComponent.css`.
6. Измените файл `ControlManifest.Input.xml`, чтобы включить файл ресурсов `CSS` в элемент Resources.
 
    ```XML
    <resources> 
      <code path="index.ts" order="1"/> 
      <css path="css/TS_LinearInputComponent.css" order="1"/> 
    </resources> 
     ```
7. Перестройте проект с помощью следующей команды: 
   ```CLI
   npm run build
   ```
8. Проверьте выходные данные сборки в файле **./аут/Контролс/тслинеаринпуткомпонент** и убедитесь, что теперь файл **TS_LinearInputComponent. CSS** включен в состав скомпилированных артефактов сборки. 

## <a name="debugging-your-code-component"></a>Отладка компонента кода

После завершения реализации логики компонента кода выполните следующую команду, чтобы начать процесс отладки. Дополнительные сведения: [Отладка компонентов кода](debugging-custom-controls.md)

```CLI
npm start
```

## <a name="packaging-your-code-components"></a>Упаковка компонентов кода

Чтобы создать и импортировать файл [решения](https://docs.microsoft.com/powerapps/maker/common-data-service/solutions-overview) , выполните следующие действия.

1. Создайте **решения** для папок в папке **линеаркомпонент** и перейдите в папку. 
2. Создайте новый проект решения в папке **линеаркомпонент** с помощью следующей команды:
 
    ```CLI
     pac solution init --publisher-name developer --publisher-prefix dev 
    ```

   > [!NOTE]
   > Значения [издателя-Name](https://docs.microsoft.com/powerapps/developer/common-data-service/reference/entities/publisher) и [Publisher-prefix](https://docs.microsoft.com/powerapps/maker/common-data-service/change-solution-publisher-prefix) должны быть уникальными для вашей среды.
 
3. После создания нового проекта решения необходимо обратиться к расположению, в котором находится созданный компонент. Ссылку можно добавить с помощью следующей команды:

    ```CLI
     pac solution add-reference --path c:\users\LinearComponent
    ```

4. Чтобы создать ZIP-файл из проекта решения, необходимо `cd` в каталог проекта решения и выполнить сборку проекта с помощью следующей команды: 

    ```CLI
     msbuild /t:restore
    ```

5. Снова выполните следующую команду MSBuild:
    ```CLI
     msbuild
    ```

    > [!NOTE]
    > Убедитесь, что выбраны **цели NuGet & задач сборки** . Чтобы включить его, сделайте следующее:
    > - Откройте **Visual Studio Installer**.
    > - Для Visual Studio 2017 выберите **изменить**.
    > - Выберите **отдельные компоненты**.
    > - В разделе **средства кода**проверьте **целевые объекты NuGet & задачах сборки**.

6. Созданный ZIP-файл решения находится в папке `Solution\bin\debug`.
7. Вручную [импортируйте решение в Common Data Service](https://docs.microsoft.com/powerapps/maker/common-data-service/import-update-export-solutions) с помощью веб-портала после того, как файл ZIP будет готов, или ознакомьтесь с разделом [Проверка подлинности в Организации](import-custom-controls.md#authenticating-to-your-organization) и [развертывания](import-custom-controls.md#deploying-code-components) для импорта с помощью команд интерфейса командной строки PowerApps.

## <a name="adding-code-components-in-model-driven-apps"></a>Добавление компонентов кода в приложения, управляемые моделями

Чтобы добавить компонент кода, например линейный компонент ввода, выполните действия, описанные в разделе [Добавление компонентов в поля и сущности](add-custom-controls-to-a-field-or-entity.md).

## <a name="adding-code-components-to-a-canvas-app"></a>Добавление компонентов кода в приложение Canvas

Чтобы добавить компоненты кода в приложение Canvas, выполните действия, описанные в разделе [Добавление компонентов кода в приложение Canvas](component-framework-for-canvas-apps.md#add-components-to-a-canvas-app).

### <a name="see-also"></a>См. также

[Загрузка примеров компонентов](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[Обновление существующих компонентов платформы компонентов PowerApps](updating-existing-controls.md)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](reference/index.md)<br/>
[Обзор платформы компонентов PowerApps](overview.md)
