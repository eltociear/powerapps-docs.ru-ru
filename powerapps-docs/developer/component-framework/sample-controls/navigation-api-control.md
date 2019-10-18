---
title: " Компонент API навигации | Документация Майкрософт"
description: Реализация компонента API навигации
ms.custom: ''
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 85dd665f7a3dc92b5198cfd8429b59af0896d5cc
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340352"
---
# <a name="implementing-navigation-api-component"></a>Реализация компонента API навигации

В этом примере компонента рассматриваются различные методы, доступные в составе API навигации инфраструктуры компонентов PowerApps. В этом примере создается ряд входных элементов с кнопками типа, которые вызывают соответствующие методы API навигации, соответствующие отображаемому значению.  

> [!div class="mx-imgBorder"]
> (../media/navigation-api-control.png "Компонент API навигации") для ![компонента API навигации]

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="manifest"></a>Явление

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest>
    <control namespace="SampleNamespace" constructor="TSNavigationAPI" version="1.0.0" display-name-key="TS_NavigationAPI_Display_Key" description-key="TS_NavigationAPI_Desc_Key" control-type="standard">
        <type-group name="numbers">
            <type>Whole.None</type>
            <type>Currency</type>
            <type>FP</type>
            <type>Decimal</type>
        </type-group>
        <property name="controlValue" display-name-key="controlValue_Display_Key" description-key="controlValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" />
        <resources>
            <code path="index.ts" order="1" />
            <css path="css/TS_NavigationAPI.css" order="1" />
        </resources>
    </control>
</manifest>
```

## <a name="code"></a>Код

```TypeScript
import {IInputs, IOutputs} from "./generated/ManifestTypes";
export class TSNavigationAPI implements ComponentFramework.StandardControl<IInputs, IOutputs> {
// PowerApps component framework framework delegate which will be assigned to this object which would be called whenever an update happens. 
private _notifyOutputChanged: () => void;
// Reference to the div element that hold together all the HTML elements that we are creating as part of this control
private divElement: HTMLDivElement;
// Reference to the button that invokes the openAlertDialog command
private openAlertDialogButton: HTMLButtonElement;
// Reference to the button that invokes the openConfirmDialog command
private openConfirmDialogButton: HTMLButtonElement;
// Reference to the button that invokes the openFile command
private openFileButton: HTMLButtonElement;
// Reference to the button that invokes the openUrl command
private openUrlButton: HTMLButtonElement;
// Reference to the control container HTMLDivElement
// This element contains all elements of our custom control example
private _container: HTMLDivElement;
// Reference to ComponentFramework Context object
private _context : ComponentFramework.Context<IInputs>;
/**
* Empty constructor.
*/
constructor()
{
}
/**
* Used to initialize the control instance. Controls can kick off remote server calls and other initialization actions here.
* Data-set values are not initialized here, use updateView.
* @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to property names defined in the manifest, as well as utility functions.
* @param notifyOutputChanged A callback method to alert the framework that the control has new outputs ready to be retrieved asynchronously.
* @param state A piece of data that persists in one session for a single user. Can be set at any point in a controls life cycle by calling 'setControlState' in the Mode interface.
* @param container If control is marked control-type='standard', it receives an empty div element within which it can render its content.
*/
public init(context: ComponentFramework.Context<IInputs>, notifyOutputChanged: () => void, state: ComponentFramework.Dictionary, container:HTMLDivElement)
{
this._notifyOutputChanged = notifyOutputChanged;
this._context = context;
this._container = container;
this.divElement = document.createElement("div");
this.divElement.setAttribute("class","TSNavigationAPI");
// Create the HTML button elements for openAlertDialog button
this.openAlertDialogButton = document.createElement("button");
this.openAlertDialogButton.setAttribute("id","openAlertDialogButton");
this.openAlertDialogButton.innerHTML = "openAlertDialogButton";
// Create the HTML button elements for openConfirmDialog button
this.openConfirmDialogButton = document.createElement("button");
this.openConfirmDialogButton.setAttribute("id","openConfirmDialogButton");
this.openConfirmDialogButton.innerHTML = "openConfirmDialogButton";
// Create the HTML button elements for openFile button
this.openFileButton = document.createElement("button");
this.openFileButton.setAttribute("id","openFileButton");
this.openFileButton.innerHTML = "openFileButton";
// Create the HTML button elements for openUrl button
this.openUrlButton = document.createElement("button");
this.openUrlButton.setAttribute("id","openUrlButton");
this.openUrlButton.innerHTML = "openUrlButton";
// bind the function which invokes the respective API's to each of the buttons
this.openAlertDialogButton.addEventListener("click",this.raiseEvent.bind(this));
this.openConfirmDialogButton.addEventListener("click",this.raiseEvent.bind(this));
this.openFileButton.addEventListener("click",this.raiseEvent.bind(this));
this.openUrlButton.addEventListener("click",this.raiseEvent.bind(this));
// append all the button elements to the parent div element for control.
this.divElement.appendChild(this.openAlertDialogButton);
this.divElement.appendChild(this.openConfirmDialogButton);
this.divElement.appendChild(this.openFileButton);
this.divElement.appendChild(this.openUrlButton);
// append the parent div element in the control to the control's container
this._container.appendChild(this.divElement);
}
/**
* Handles the events raised by each of the buttons that are binded according to their id
* @param event : event object that contains all the properties regarding the raised event
*/
public raiseEvent(event: Event,)
{
var inputSource = (event.srcElement! as Element)!.id;
switch(inputSource)
{
    case "openAlertDialogButton": this._context.navigation.openAlertDialog({text:"This is an alert.", confirmButtonLabel : "Yes",}).then(
        function success()
        {
            document.getElementById("openAlertDialogButton")!.innerHTML = "Alert dialog closed";
        },
        function()
        {
            document.getElementById("openAlertDialogButton")!.innerHTML = "Error in Alert Dialog";
        }
    );
    break;
    case "openConfirmDialogButton": this._context.navigation.openConfirmDialog({title:"Confirmation Dialog", text:"This is a confirmation.",},{height:200, width:450}).then(
        function(success)
        {
            if(success.confirmed)
            {
                document.getElementById("openConfirmDialogButton")!.innerHTML = "Ok button clicked.";
            }
            else
            {
                document.getElementById("openConfirmDialogButton")!.innerHTML = "Cancel or X button clicked.";
            }
        }
    );
    break;
    case "openFileButton": 
        var file = {
                    fileContent: "U2FtcGxlIGNvbnRlbnQgZm9yIERlbW8=", //Contents of the file in base64 encoded format. 
                    fileName: "Sample.txt", //Name of the file.
                    fileSize: 29, //Size of the file in KB.
                    mimeType: "text/plain" //MIME type of the file.
                    };
        this._context.navigation.openFile(file,{openMode:2});
    break;
    case "openUrlButton": this._context.navigation.openUrl("https://www.microsoft.com");
    break;
};
//this._notifyOutputChanged();
}
/**
* Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
* @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
*/
public updateView(context: ComponentFramework.Context<IInputs>,): void
{
this._context = context;
}
/** 
* It is called by the framework prior to a control receiving new data. 
* @returns an object based on nomenclature defined in manifest, expecting object[s] for property marked as “bound” or “output”
*/
public getOutputs(): IOutputs
{
// no-op: method not leveraged by this example custom control
return { };
}
/** 
* Called when the control is to be removed from the DOM tree. Controls should use this call for cleanup.
* i.e. canceling any pending remote calls, removing listeners, etc.
*/
public destroy()
{
}
}
```

## <a name="resources"></a>Ресурсы

```css
.SampleNamespace\.TSNavigationAPI button {
  background-color: rgb(59, 121, 183);
  border: 1px solid black;
  color: white;
  padding: 10px 24px;
  cursor: pointer;
  width: 100%;
  display: block;
}
.SampleNamespace\.TSNavigationAPI button:not(:last-child) {
  border-bottom: none;
}
.SampleNamespace\.TSNavigationAPI button:hover {
  background-color: #c2c2c2;
}
```

Метод `openAlertDialog` предоставляет возможность отображать диалоговое окно предупреждения, содержащее сообщение и кнопку. Можно также реализовать методы обратного вызова, когда диалоговое окно предупреждения закрыто или при загрузке диалогового окна возникла ошибка.
  
В этом примере при щелчке `openAlertDialogButton` диалоговом окне предупреждения открывается и устанавливается значение `Alert dialog closed` при закрытии диалогового окна либо с помощью кнопки `OK`, либо с кнопкой `X`.

> [!NOTE]
> Это похоже на вызов метода [XRM. Navigation. опеналертдиалог](https://docs.microsoft.com/dynamics365/customer-engagement/developer/clientapi/reference/xrm-navigation/openalertdialog) в клиентапи.  

Метод `openConfirmDialog` предоставляет возможность отображать диалоговое окно предупреждения, содержащее сообщение и две кнопки. Этот метод можно использовать для реализации другой логики на основе нажатой кнопки. Можно реализовать обратный вызов успеха, который вызывается, когда диалоговое окно закрывается нажатием любой из кнопок.
  
В этом примере отображается диалоговое окно подтверждения, когда вы щелкнули `openConfirmDialogButton` и устанавливаете для него значение `Ok` или `Cancel` или `X` в зависимости от нажатой кнопки.

> [!NOTE]
> Это похоже на вызов метода [XRM. Navigation. опенконфирмдиалог](https://docs.microsoft.com/dynamics365/customer-engagement/developer/clientapi/reference/xrm-navigation/openconfirmdialog) в клиентапи.
  
Метод `openFile` предоставляет возможность открытия файла. Необходимо передать объект File, содержащий имя файла, содержимое, тип MIME и размер файла. Кроме того, можно передать необязательный параметр в режиме, в котором вы хотите открыть файл, как 1 или 2, а 1 — по умолчанию, который открывает файл в режиме чтения или открытия.
  
В этом примере открывается файл с именем `SampleDemo.txt` в режиме сохранения при щелчке `openFileButton`.

> [!NOTE]
> Это похоже на вызов метода [XRM. Navigation. OpenFile](https://docs.microsoft.com/dynamics365/customer-engagement/developer/clientapi/reference/xrm-navigation/openfile) в клиентапи.

Метод `openUrl` предоставляет возможность открытия URL-адреса. Необходимо передать URL-адрес как строку в метод, а также передать необязательные параметры Height, Width и Опенинневвиндов как true, если вы хотите, чтобы URL-адрес открывался в новом окне.
  
В этом примере открывается новое окно и загружается Домашняя страница microsoft.com при щелчке `openUrlButton`.

> [!NOTE]
> Это похоже на вызов метода [XRM. Navigation. openUrl](https://docs.microsoft.com/dynamics365/customer-engagement/developer/clientapi/reference/xrm-navigation/openurl) в клиентапи.

### <a name="related-topics"></a>Связанные статьи

[Загрузка примеров компонентов](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Справочник по схеме манифеста платформы компонентов PowerApps](../manifest-schema-reference/index.md)

