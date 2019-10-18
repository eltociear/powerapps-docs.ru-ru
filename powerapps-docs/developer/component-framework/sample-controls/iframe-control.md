---
title: " Компонент IFRAME | Документация Майкрософт"
description: Реализация компонента IFRAME
ms.custom: ''
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: d10b03c478f238df02ee7e1309c0e39e758ce4c9
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340467"
---
# <a name="implementing-a-iframe-component"></a>Реализация компонента IFRAME

В этом примере описывается привязка компонента кода к различным полям в форме и использование значений этих полей в качестве входных свойств компонента.  

> [!div class="mx-imgBorder"]
> (../media/iframe-control.png "Компонент") IFRAME ![компонента IFRAME]

## <a name="available-for"></a>Доступно для 

Приложения на основе моделей и приложения Canvas (экспериментальная Предварительная версия) 

## <a name="manifest"></a>Явление

```XML
<?xml version="1.0" encoding="utf-8"?>
<manifest>
    <control namespace="SampleNamespace" constructor="TSIFrameControl" version="1.0.0" display-name-key="TS_IFrameControl_Display_Key" description-key="TS_IFrameControl_Desc_Key" control-type="standard">
        <property name="stringProperty" display-name-key="stringProperty_Display_Key" description-key="stringProperty_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" />
        <property name="latitudeValue" display-name-key="Bing_Maps_Latitude_Value" description-key="latitude" of-type="FP" usage="bound" required="true" />
        <property name="longitudeValue" display-name-key="Bing_Maps_Longitude_Value" description-key="longitude" of-type="FP" usage="bound" required="true" />
        <resources>
            <code path="index.ts" order="1" />
            <css path="css/TS_IFrameControl.css" order="2" />
        </resources>
    </control>
</manifest>
```

## <a name="code"></a>Код

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
export class TSIFrameControl
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // reference to Bing Map IFrame HTMLElement
  private _bingMapIFrame: HTMLElement;
  // reference to the control container HTMLDivElement
  // This element contains all elements of our custom control example
  private _container: HTMLDivElement;
  // Flag if control view has been rendered
  private _controlViewRendered: Boolean;
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
    this._container = container;
    this._controlViewRendered = false;
  }
  /**
   * Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
   * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
   */
  public updateView(context: ComponentFramework.Context<IInputs>) {
    if (!this._controlViewRendered) {
      this._controlViewRendered = true;
      this.renderBingMapIFrame();
    }
    let latitude: number = context.parameters.latitudeValue.raw;
    let longitude: number = context.parameters.longitudeValue.raw;
    this.updateBingMapURL(latitude, longitude);
  }
  /**
   * Render IFrame HTML Element that hosts the Bing Map and appends the IFrame to the control container
   */
  private renderBingMapIFrame(): void {
    this._bingMapIFrame = this.createIFrameElement();
    this._container.appendChild(this._bingMapIFrame);
  }
  /**
   * Updates the URL of the Bing Map IFrame to display the updated lat/long coordinates
   * @param latitude : latitude of center point of Bing map
   * @param longitude : longitude of center point of Bing map
   */
  private updateBingMapURL(latitude: number, longitude: number): void {
    // Bing Map API:
    // https://msdn.microsoft.com/library/dn217138.aspx
    // Provide bing map query string parameters to format and style map view
    let bingMapUrlPrefix = "https://www.bing.com/maps/embed?h=400&w=300&cp=";
    let bingMapUrlPostfix = "&lvl=12&typ=d&sty=o&src=SHELL&FORM=MBEDV8";
    // Build the entire URL with the user provided latitude and longitude
    let iFrameSrc: string =
      bingMapUrlPrefix + latitude + "~" + longitude + bingMapUrlPostfix;
    // Update the IFrame to point to the updated URL
    this._bingMapIFrame.setAttribute("src", iFrameSrc);
  }
  /**
   * Helper method to create an IFrame HTML Element
   */
  private createIFrameElement(): HTMLElement {
    let iFrameElement: HTMLElement = document.createElement("iframe");
    iFrameElement.setAttribute("class", "TS_SampleControl_IFrame");
    return iFrameElement;
  }
  /**
   * It is called by the framework prior to a control receiving new data.
   * @returns an object based on nomenclature defined in manifest, expecting object[s] for property marked as “bound” or “output”
   */
  public getOutputs(): IOutputs {
    // no-op: method not leveraged by this example custom control
    return {};
  }
  /**
   * Called when the control is to be removed from the DOM tree. Controls should use this call for cleanup.
   * i.e. canceling any pending remote calls, removing listeners, etc.
   */
  public destroy() {
    // no-op: method not leveraged by this example custom control
  }
}
```

## <a name="resources"></a>Ресурсы

```css
.SampleNamespace\.TSIFrameControl .TS_SampleControl_IFrame
{
    width: 300px;
    height: 400px;
}
```

> [!NOTE]
> Платформа компонентов PowerApps пока не поддерживает составные поля, поэтому вы не сможете привязать этот компонент к несущему полю адресов широты и долготы. Необходимо привязать компонент кода к другому полю с плавающей запятой.

Этот образец компонента отображает `IFRAME`, который отображает `Bing Maps URL`. Компонент привязан к двум полям с плавающей запятой, которые передаются в качестве параметров в компонент и вставляются в `IFRAME URL` для обновления карты Bing до широты и долготы предоставленных входных данных.  

Обновите файл `Manifest`, чтобы включить привязку к двум дополнительным полям в форме.  
Это изменение информирует платформу компонентов PowerApps о том, что эти привязанные поля должны быть переданы компоненту во время инициализации и при каждом обновлении одного из значений.
  
```xml

<property name="latitudeValue" display-name-key="Bing_Maps_Latitude_Value" description-key="latitude" of-type="FP" usage="bound" required="true" />  
<property name="longitudeValue" display-name-key="Bing_Maps_Longitude_Value" description-key="longitude" of-type="FP" usage="bound" required="true" />  
```

Могут быть необходимы дополнительные связанные свойства. Это будет применено во время настройки компонента при привязке компонента к форме. Это можно настроить, задав атрибут `required` узла свойств в манифесте компонента. Установите значение false, если не требуется, чтобы свойство Component было привязано к полю. 
 
`ControlFramework.d.ts` необходимо обновить, чтобы добавить два поля в интерфейс `IInputs`. Это формат, который платформа компонентов PowerApps передает значения полей. Добавление этих значений в интерфейс `IInputs` позволяет файлу TypeScript ссылаться на значения и компилироваться успешно.  

```TypeScript
    export interface IInputs 
    { latitudeValue: ControlFramework.PropertyTypes.NumberProperty;  
        longitudeValue: ControlFramework.PropertyTypes.NumberProperty;  
    }  
 ```

Начальная отрисовка создает элемент `IFRAME` и добавляет его в контейнер элементов управления. Этот `IFRAME` используется для отображения **карты Bing**. URL-адрес `IFRAME` задается как `Bing Map URL` и включает связанные поля (Латитудевалуе и Лонгитудевалуе) в URL-адресе, чтобы центрировать карту в указанном расположении. 

Метод [упдатевиев](../reference/control/updateview.md) вызывается всякий раз, когда одно из этих полей обновляется в форме. Этот метод обновляет URL-адрес IFRAME **карты Bing** , чтобы использовать новые значения широты и долготы, передаваемые компоненту. Чтобы просмотреть этот компонент во время выполнения, привяжите компонент к полю в форме, как и к любому другому компоненту кода.

### <a name="related-topics"></a>Связанные статьи

[Загрузка примеров компонентов](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[Справочник по схеме манифеста платформы компонентов PowerApps](../manifest-schema-reference/index.md)<br />
[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br />
[Обзор платформы компонентов PowerApps](../overview.md)
