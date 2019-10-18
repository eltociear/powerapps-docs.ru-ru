---
title: " Компонент линейного ввода | Документация Майкрософт"
description: Реализация линейного входного компонента
ms.custom: ''
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: f7dcc3fef22c354b1fed684a09fb091f2d2c6cb7
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72347137"
---
# <a name="implementing-linear-input-component"></a>Реализация линейного входного компонента

Этот пример компонента изменяет взаимодействие с пользователем при взаимодействии с числовыми типами в форме. Вместо ввода чисел линейный входной компонент предоставляет линейный ползунок, с помощью которого значение атрибута может быть задано в форме.  

Чтобы реализовать этот компонент, сначала необходимо определить файл [манифеста](../manifest-schema-reference/manifest.md) и реализовать пользовательскую логику в TypeScript.

> [!div class="mx-imgBorder"]
> Линейный(../media/linear-input-control.png "входной") компонент ![линейного ввода]

## <a name="available-for"></a>Доступно для 

Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия) 

## <a name="manifest"></a>Явление

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest>
    <control namespace="SampleNamespace" constructor="TSLinearInputControl" version="1.0.0" display-name-key="TSLinearInputControl_Display_Key" description-key="TSLinearInputControl_Desc_Key" control-type="standard">
        <type-group name="numbers">
            <type>Whole.None</type>
            <type>Currency</type>
            <type>FP</type>
            <type>Decimal</type>
        </type-group>
        <property name="controlValue" display-name-key="controlValue_Display_Key" description-key="controlValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" />
        <resources>
            <code path="index.ts" order="1" />
            <css path="css/TS_LinearInputControl.css" order="1" />
        </resources>
    </control>
</manifest>
```

## <a name="code"></a>Код

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
export class TSLinearInputControl
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // Value of the field is stored and used inside the control
  private _value: number;
  // PowerApps component framework framework delegate which will be assigned to this object which would be called whenever an update happens.
  private _notifyOutputChanged: () => void;
  // label element created as part of this control
  private labelElement: HTMLLabelElement;
  // input element that is used to create the range slider
  private inputElement: HTMLInputElement;
  // reference to the control container HTMLDivElement
  // This element contains all elements of our custom control example
  private _container: HTMLDivElement;
  // reference to ComponentFramework Context object
  private _context: ComponentFramework.Context<IInputs>;
  // Event Handler 'refreshData' reference
  private _refreshData: EventListenerOrEventListenerObject;
  /**
   * Empty constructor.
   */
  constructor() {}
  /**
   * Used to initialize the control instance. Controls can kick off remote server calls and other initialization actions here.
   * Data-set values are not initialized here, use updateView.
   * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to property names defined in the manifest, as well as utility functions.
   * @param notifyOutputChanged A callback method to alert the framework that the control has new outputs ready to be retrieved asynchronously.
   * @param state A piece of data that persists in one session for a single user. Can be set at any point in a controls life cycle by calling 'setControlState' in the Mode interface.
   * @param container If control is marked control-type='standard', it receives an empty div element within which it can render its content.
   */
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
    // creating HTML elements for the input type range and binding it to the function which refreshes the control data
    this.inputElement = document.createElement("input");
    this.inputElement.setAttribute("type", "range");
    this.inputElement.addEventListener("input", this._refreshData);
    //setting the max and min values for the control.
    this.inputElement.setAttribute("min", "1");
    this.inputElement.setAttribute("max", "1000");
    this.inputElement.setAttribute("class", "linearslider");
    this.inputElement.setAttribute("id", "linearrangeinput");
    // creating a HTML label element that shows the value that is set on the linear range control
    this.labelElement = document.createElement("label");
    this.labelElement.setAttribute("class", "TS_LinearRangeLabel");
    this.labelElement.setAttribute("id", "lrclabel");
    // retrieving the latest value from the control and setting it to the HTMl elements.
    this._value = context.parameters.controlValue.raw;
    this.inputElement.setAttribute(
      "value",
      context.parameters.controlValue.formatted
        ? context.parameters.controlValue.formatted
        : "0"
    );
    this.labelElement.innerHTML = context.parameters.controlValue.formatted
      ? context.parameters.controlValue.formatted
      : "0";
    // appending the HTML elements to the control's HTML container element.
    this._container.appendChild(this.inputElement);
    this._container.appendChild(this.labelElement);
    container.appendChild(this._container);
  }
  /**
   * Updates the values to the internal value variable we are storing and also updates the html label that displays the value
   * @param evt : The "Input Properties" containing the parameters, control metadata and interface functions
   */
  public refreshData(evt: Event): void {
    this._value = (this.inputElement.value as any) as number;
    this.labelElement.innerHTML = this.inputElement.value;
    this._notifyOutputChanged();
  }
  /**
   * Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
   * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
   */
  public updateView(context: ComponentFramework.Context<IInputs>): void {
    // storing the latest context from the control.
    this._value = context.parameters.controlValue.raw;
    this._context = context;
    this.inputElement.setAttribute(
      "value",
      context.parameters.controlValue.formatted
        ? context.parameters.controlValue.formatted
        : ""
    );
    this.labelElement.innerHTML = context.parameters.controlValue.formatted
      ? context.parameters.controlValue.formatted
      : "";
  }
  /**
   * It is called by the framework prior to a control receiving new data.
   * @returns an object based on nomenclature defined in manifest, expecting object[s] for property marked as “bound” or “output”
   */
  public getOutputs(): IOutputs {
    return {
      controlValue: this._value
    };
  }
  /**
   * Called when the control is to be removed from the DOM tree. Controls should use this call for cleanup.
   * i.e. canceling any pending remote calls, removing listeners, etc.
   */
  public destroy() {
    this.inputElement.removeEventListener("input", this._refreshData);
  }
}
```

## <a name="resources"></a>Ресурсы

```css
.SampleNamespace\.TSLinearInputControl input[type="range"].linearslider {
  margin: 1px 0;
  background: transparent;
  -webkit-appearance: none;
  width: 100%;
  padding: 0;
  height: 24px;
  -webkit-tap-highlight-color: transparent;
}
.SampleNamespace\.TSLinearInputControl input[type="range"].linearslider:focus {
  outline: none;
}
.SampleNamespace\.TSLinearInputControl
  input[type="range"].linearslider::-webkit-slider-runnable-track {
  background: #666;
  height: 2px;
  cursor: pointer;
}
.SampleNamespace\.TSLinearInputControl
  input[type="range"].linearslider::-webkit-slider-thumb {
  background: #666;
  border: 0 solid #f00;
  height: 24px;
  width: 10px;
  border-radius: 48px;
  cursor: pointer;
  opacity: 1;
  -webkit-appearance: none;
  margin-top: -12px;
}
.SampleNamespace\.TSLinearInputControl
  input[type="range"].linearslider::-moz-range-track {
  background: #666;
  height: 2px;
  cursor: pointer;
}
.SampleNamespace\.TSLinearInputControl
  input[type="range"].linearslider::-moz-range-thumb {
  background: #666;
  border: 0 solid #f00;
  height: 24px;
  width: 10px;
  border-radius: 48px;
  cursor: pointer;
  opacity: 1;
  -webkit-appearance: none;
  margin-top: -12px;
}
.SampleNamespace\.TSLinearInputControl
  input[type="range"].linearslider::-ms-track {
  background: #666;
  height: 2px;
  cursor: pointer;
}
.SampleNamespace\.TSLinearInputControl
  input[type="range"].linearslider::-ms-thumb {
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

В этом примере определяется [группа типов](../manifest-schema-reference/type-group.md) , которая называется `numbers`, которая включает в эту группу в манифесте типы значений Decimal, целых, float и Currency. Эта группа используется для привязки свойства компонента.

Элемент input типа `range` с `min` и `max` значение 1 и 1000, соответственно, создается. Создается элемент Label, который показывает значение относительно положения ползунка. Присоедините `refreshData` функции к `eventlistener` входных данных компонента.

Создайте локальную переменную для сохранения [контекста](../reference/context.md) и `notifyOutputChanged`. Назначьте контекст и Нотифйоутпутчанжед из параметров, передаваемых как часть функции init.

Реализуйте логику функции `refreshData`. Как можно увидеть в примере, мы принимаем значение из `inputElement` и устанавливаем значение компонента, `innerHTML` свойство `labelElement`, а затем вызываю `notifyOutputChanged`, чтобы изменения были каскадом выше уровня платформы.

```TypeScript
public refreshData(context: ControlFramework.IPropBag<InputsOutputs.IInputBag>) 
{ 
   this._value = (this.inputElement.value as any)as number; 
   this.labelElement.innerHTML = this.inputElement.value; 
   this._notifyOutputChanged(); 
} 
```

В методе `updateView` мы получаем значение атрибута из context. Parameters, а затем присвоить ему переменную значения, в которой хранится значение компонента, а также элементы ввода в компоненте. 

```TypeScript

public updateView(context: ControlFramework.IPropBag<InputsOutputs.IInputBag>): void 
 { 
    this._value = context.parameters.controlValue.raw; 
    this._context = context; 
    this.inputElement.setAttribute("value",context.parameters.controlValue.formatted ? context.parameters.controlValue.formatted : ""); 
    this.labelElement.innerHTML = context.parameters.controlValue.formatted ? context.parameters.controlValue.formatted : ""; 
   } 
 ```

### <a name="related-topics"></a>Связанные статьи

[Загрузка примеров компонентов](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Справочник по схеме манифеста платформы компонентов PowerApps](../manifest-schema-reference/index.md)
