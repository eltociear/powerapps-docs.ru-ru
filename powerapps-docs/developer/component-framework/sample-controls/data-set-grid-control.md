---
title: Компонент сетки набора данных | Документация Майкрософт
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 356561d0-a36b-4b93-8b76-3e1abf9414e9
ms.openlocfilehash: ca13ef7758bb21853f9c1411c641bd1ae88115b6
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340513"
---
# <a name="implementing-data-set-component"></a>Реализация компонента набора данных

В этом примере компонента показано, как изменить взаимодействие с пользователем для взаимодействия с набором данных. Например, сетка домашней страницы отображается только на домашней странице сущности в виде таблицы. Можно создать компонент кода, который может отображать данные в зависимости от выбранного варианта. В этом примере записи отображаются в виде плиток вместо обычной табличной сетки.

> [!div class="mx-imgBorder"]
> ![](../media/data-set-grid.png "Компонент") сетки набора данных компонент сетки наборов данных

## <a name="available-for"></a>Доступно для 

Приложения на основе модели

## <a name="manifest"></a>Явление 

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest>
    <control namespace="SampleNamespace" constructor="TSDataSetGrid" version="1.0.0" display-name-key="TS_DataSetGrid_Display_Key" description-key="TSIncrementControl_Desc_Key" control-type="standard">
        <data-set name="dataSetGrid" display-name-key="DataSetGridProperty_Display_Key">
        </data-set>
        <resources>
            <code path="index.ts" order="1" />
            <css path="css/TS_DataSetGrid.css" order="1" />
            <resx path="strings/TSDataSetGrid.1033.resx" version="1.0.0" />
        </resources>
    </control>
</manifest>
```

## <a name="code"></a>Код 

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
import DataSetInterfaces = ComponentFramework.PropertyHelper.DataSetApi;
type DataSet = ComponentFramework.PropertyTypes.DataSet;
// Define const here
const RowRecordId: string = "rowRecId";
// Style name of Load More Button
const DataSetControl_LoadMoreButton_Hidden_Style =
  "DataSetControl_LoadMoreButton_Hidden_Style";
export class TSDataSetGrid
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // Cached context object for the latest updateView
  private contextObj: ComponentFramework.Context<IInputs>;
  // Div element created as part of this control's main container
  private mainContainer: HTMLDivElement;
  // Table element created as part of this control's table
  private gridContainer: HTMLDivElement;
  // Button element created as part of this control
  private loadPageButton: HTMLButtonElement;
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
   * @param container If a control is marked control-type='starndard', it will receive an empty div element within which it can render its content.
   */
  public init(
    context: ComponentFramework.Context<IInputs>,
    notifyOutputChanged: () => void,
    state: ComponentFramework.Dictionary,
    container: HTMLDivElement
  ) {
    // Need to track container resize so that control could get the available width. The available height won't be provided even this is true
    context.mode.trackContainerResize(true);
    // Create main table container div.
    this.mainContainer = document.createElement("div");
    // Create data table container div.
    this.gridContainer = document.createElement("div");
    this.gridContainer.classList.add("DataSetControl_grid-container");
    // Create data table container div.
    this.loadPageButton = document.createElement("button");
    this.loadPageButton.setAttribute("type", "button");
    this.loadPageButton.innerText = context.resources.getString(
      "PCF_DataSetControl_LoadMore_ButtonLabel"
    );
    this.loadPageButton.classList.add(
      DataSetControl_LoadMoreButton_Hidden_Style
    );
    this.loadPageButton.classList.add("DataSetControl_LoadMoreButton_Style");
    this.loadPageButton.addEventListener(
      "click",
      this.onLoadMoreButtonClick.bind(this)
    );
    // Adding the main table and loadNextPage button created to the container DIV.
    this.mainContainer.appendChild(this.gridContainer);
    this.mainContainer.appendChild(this.loadPageButton);
    this.mainContainer.classList.add("DataSetControl_main-container");
    container.appendChild(this.mainContainer);
  }
  /**
   * Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
   * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
   */
  public updateView(context: ComponentFramework.Context<IInputs>): void {
    this.contextObj = context;
    this.toggleLoadMoreButtonWhenNeeded(context.parameters.dataSetGrid);
    if (!context.parameters.dataSetGrid.loading) {
      // Get sorted columns on View
      let columnsOnView = this.getSortedColumnsOnView(context);
      if (!columnsOnView || columnsOnView.length === 0) {
        return;
      }
      while (this.gridContainer.firstChild) {
        this.gridContainer.removeChild(this.gridContainer.firstChild);
      }
      this.gridContainer.appendChild(
        this.createGridBody(columnsOnView, context.parameters.dataSetGrid)
      );
    }
    // this is needed to ensure the scroll bar appears automatically when the grid resize happens and all the tiles are not visible on the screen.
    this.mainContainer.style.maxHeight =
      window.innerHeight - this.gridContainer.offsetTop - 75 + "px";
  }
  /**
   * It is called by the framework prior to a control receiving new data.
   * @returns an object based on nomenclature defined in manifest, expecting object[s] for property marked as “bound” or “output”
   */
  public getOutputs(): IOutputs {
    return {};
  }
  /**
   * Called when the control is to be removed from the DOM tree. Controls should use this call for cleanup.
   * i.e. cancelling any pending remote calls, removing listeners, etc.
   */
  public destroy(): void {}
  /**
   * Get sorted columns on view
   * @param context
   * @return sorted columns object on View
   */
  private getSortedColumnsOnView(
    context: ComponentFramework.Context<IInputs>
  ): DataSetInterfaces.Column[] {
    if (!context.parameters.dataSetGrid.columns) {
      return [];
    }
    let columns = context.parameters.dataSetGrid.columns.filter(function(
      columnItem: DataSetInterfaces.Column
    ) {
      // some column are supplementary and their order is not > 0
      return columnItem.order >= 0;
    });
    // Sort those columns so that they will be rendered in order
    columns.sort(function(
      a: DataSetInterfaces.Column,
      b: DataSetInterfaces.Column
    ) {
      return a.order - b.order;
    });
    return columns;
  }
  /**
   * funtion that creates the body of the grid and embeds the content onto the tiles.
   * @param columnsOnView columns on the view whose value needs to be shown on the UI
   * @param gridParam data of the Grid
   */
  private createGridBody(
    columnsOnView: DataSetInterfaces.Column[],
    gridParam: DataSet
  ): HTMLDivElement {
    let gridBody: HTMLDivElement = document.createElement("div");
    if (gridParam.sortedRecordIds.length > 0) {
      for (let currentRecordId of gridParam.sortedRecordIds) {
        let gridRecord: HTMLDivElement = document.createElement("div");
        gridRecord.classList.add("DataSetControl_grid-item");
        gridRecord.addEventListener("click", this.onRowClick.bind(this));
        // Set the recordId on the row dom
        gridRecord.setAttribute(
          RowRecordId,
          gridParam.records[currentRecordId].getRecordId()
        );
        columnsOnView.forEach(function(columnItem, index) {
          let labelPara = document.createElement("p");
          labelPara.classList.add("DataSetControl_grid-text-label");
          let valuePara = document.createElement("p");
          valuePara.classList.add("DataSetControl_grid-text-value");
          labelPara.textContent = columnItem.displayName + " : ";
          gridRecord.appendChild(labelPara);
          if (
            gridParam.records[currentRecordId].getFormattedValue(
              columnItem.name
            ) != null &&
            gridParam.records[currentRecordId].getFormattedValue(
              columnItem.name
            ) != ""
          ) {
            valuePara.textContent = gridParam.records[
              currentRecordId
            ].getFormattedValue(columnItem.name);
            gridRecord.appendChild(valuePara);
          } else {
            valuePara.textContent = "-";
            gridRecord.appendChild(valuePara);
          }
        });
        gridBody.appendChild(gridRecord);
      }
    } else {
      let noRecordLabel: HTMLDivElement = document.createElement("div");
      noRecordLabel.classList.add("DataSetControl_grid-norecords");
      noRecordLabel.style.width =
        this.contextObj.mode.allocatedWidth - 25 + "px";
      noRecordLabel.innerHTML = this.contextObj.resources.getString(
        "PCF_DataSetControl_No_Record_Found"
      );
      gridBody.appendChild(noRecordLabel);
    }
    return gridBody;
  }
  /**
   * Row Click Event handler for the associated row when being clicked
   * @param event
   */
  private onRowClick(event: Event): void {
    let rowRecordId = (event.currentTarget as HTMLTableRowElement).getAttribute(
      RowRecordId
    );
    if (rowRecordId) {
      let entityreference = this.contextObj.parameters.dataSetGrid.records[
        rowRecordId
      ].getNamedreference();
      let entityFormOptions = {
        entityName: entityreference.name,
        entityId: entityreference.id
      };
      this.contextObj.navigation.openForm(entityFormOptions);
    }
  }
  /**
   * Toggle 'LoadMore' button when needed
   */
  private toggleLoadMoreButtonWhenNeeded(gridParam: DataSet): void {
    if (
      gridParam.paging.hasNextPage &&
      this.loadPageButton.classList.contains(
        DataSetControl_LoadMoreButton_Hidden_Style
      )
    ) {
      this.loadPageButton.classList.remove(
        DataSetControl_LoadMoreButton_Hidden_Style
      );
    } else if (
      !gridParam.paging.hasNextPage &&
      !this.loadPageButton.classList.contains(
        DataSetControl_LoadMoreButton_Hidden_Style
      )
    ) {
      this.loadPageButton.classList.add(
        DataSetControl_LoadMoreButton_Hidden_Style
      );
    }
  }
  /**
   * 'LoadMore' Button Event handler when load more button clicks
   * @param event
   */
  private onLoadMoreButtonClick(event: Event): void {
    this.contextObj.parameters.dataSetGrid.paging.loadNextPage();
    this.toggleLoadMoreButtonWhenNeeded(this.contextObj.parameters.dataSetGrid);
  }
}
```

## <a name="resources"></a>Ресурсы

```css
.SampleNamespace\.TSDataSetGrid .DataSetControl_main-container {
  overflow-y: auto;
}

.SampleNamespace\.TSDataSetGrid .DataSetControl_grid-container {
  background-color: transparent;
  border: solid thin lightgray;
  padding: 10px;
  display: inline-block;
  overflow: auto;
}

.SampleNamespace\.TSDataSetGrid .DataSetControl_grid-item {
  margin: 5px;
  width: 200px;
  height: 200px;
  background-color: rgb(59, 121, 183);
  color: white;
  border: solid thin black;
  padding: 5px;
  text-align: center;
  float: left;
}

.SampleNamespace\.TSDataSetGrid .DataSetControl_grid-text-label {
  font-size: 12px;
  white-space: normal;
  margin: 2px;
  display: block;
  color: lightgray;
}

.SampleNamespace\.TSDataSetGrid .DataSetControl_grid-text-value {
  font-size: 12px;
  white-space: normal;
  margin: 1px;
  display: block;
  color: white;
  font-weight: bold;
}

.SampleNamespace\.TSDataSetGrid button.DataSetControl_LoadMoreButton_Style {
  background-color: #e5e5e5;
  font-size: 1.5rem;
  font-weight: bold;
  height: 3.5rem;
  text-align: center;
  width: 100%;
  border: none;
}

.SampleNamespace\.TSDataSetGrid
  button.DataSetControl_LoadMoreButton_Hidden_Style {
  display: none;
}

.SampleNamespace\.TSDataSetGrid .DataSetControl_grid-norecords {
  display: flex;
  align-items: center;
  justify-content: center;
}
```

```XML
<?xml version="1.0" encoding="utf-8"?>
<root>
<xsd:schema id="root" xmlns="" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">
<xsd:import namespace="http://www.w3.org/XML/1998/namespace" />
<xsd:element name="root" msdata:IsDataSet="true">
  <xsd:complexType>
    <xsd:choice maxOccurs="unbounded">
      <xsd:element name="metadata">
        <xsd:complexType>
          <xsd:sequence>
            <xsd:element name="value" type="xsd:string" minOccurs="0" />
          </xsd:sequence>
          <xsd:attribute name="name" use="required" type="xsd:string" />
          <xsd:attribute name="type" type="xsd:string" />
          <xsd:attribute name="mimetype" type="xsd:string" />
          <xsd:attribute ref="xml:space" />
        </xsd:complexType>
      </xsd:element>
      <xsd:element name="assembly">
        <xsd:complexType>
          <xsd:attribute name="alias" type="xsd:string" />
          <xsd:attribute name="name" type="xsd:string" />
        </xsd:complexType>
      </xsd:element>
      <xsd:element name="data">
        <xsd:complexType>
          <xsd:sequence>
            <xsd:element name="value" type="xsd:string" minOccurs="0" msdata:Ordinal="1" />
            <xsd:element name="comment" type="xsd:string" minOccurs="0" msdata:Ordinal="2" />
          </xsd:sequence>
          <xsd:attribute name="name" type="xsd:string" use="required" msdata:Ordinal="1" />
          <xsd:attribute name="type" type="xsd:string" msdata:Ordinal="3" />
          <xsd:attribute name="mimetype" type="xsd:string" msdata:Ordinal="4" />
          <xsd:attribute ref="xml:space" />
        </xsd:complexType>
      </xsd:element>
      <xsd:element name="resheader">
        <xsd:complexType>
          <xsd:sequence>
            <xsd:element name="value" type="xsd:string" minOccurs="0" msdata:Ordinal="1" />
          </xsd:sequence>
          <xsd:attribute name="name" type="xsd:string" use="required" />
        </xsd:complexType>
      </xsd:element>
    </xsd:choice>
  </xsd:complexType>
</xsd:element>
</xsd:schema>
<resheader name="resmimetype">
<value>text/microsoft-resx</value>
</resheader>
<resheader name="version">
<value>2.0</value>
</resheader>
<resheader name="reader">
<value>System.Resources.ResXResourceReader, System.Windows.Forms, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</value>
</resheader>
<resheader name="writer">
<value>System.Resources.ResXResourceWriter, System.Windows.Forms, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</value>
</resheader>
<data name="PCF_DataSetControl_LoadMore_ButtonLabel" xml:space="preserve">
<value>Load More</value>
<comment>Label for TSTableGrid's Load More Paging Button</comment>
</data>
<data name="PCF_DataSetControl_No_Record_Found" xml:space="preserve">
<value>No records found.</value>
<comment>No records found if no records</comment>
</data>
</root>
```

В этом примере у нас есть входной параметр, определенный в файле манифеста компонента с тегом набора данных. Это свойство ввода, которое привязывается к компоненту.  
 
Этот компонент имеет два важных контейнера, которые добавляются в главный тег div, который добавляется в элемент div, который передается в компонент.  Первый контейнер содержит плитки, отображающие данные записи из представления, а второй контейнер — для `Load More button`, которые показывают, когда есть записи, для которых требуется больше областей, которые можно разместить на одной странице. 
 
Оба контейнера создаются и обновляются при каждом вызове метода [упдатевиев](../reference/control/updateview.md) . Для первого контейнера мы создадим плитки на основе информации в столбцах и числа записей. Это обеспечит отображение плитки для каждой записи вместе со сведениями о ней.  
 
Если для записей существует Следующая страница, появится кнопка Загрузить еще, т. е. второй контейнер является видимым и скрытым, если в результирующем наборе нет страниц.  
 
При нажатии кнопки "загрузить еще" мы загружаем следующую страницу записей и добавляем ее к существующему результирующему набору, а логика для скрытия или отображения кнопки остается той же самой предыдущей, как показано в коде. Для этого используется метод ***онлоадморебуттонкликк*** , привязанный к кнопке.
 
Функция ***тогглелоадморебуттонвхеннидед*** принимает входные данные в качестве набора данных и проверяет, имеет ли набор данных следующую страницу, и если кнопка скрыта или видима, и соответственно скрывает или отображает кнопку.  
 
Функция ***онровкликк*** присоединяет контекст записи, используя ее значение GUID, и вызывает метод [openForm](../reference/navigation/openform.md) `NavigationAPI`, чтобы открыть соответствующую запись. Этот метод привязан к каждой плитке, формируемой как часть метода ***креатегридбоди*** .
 
Метод ***жетсортедколумнсонвиев*** возвращает список столбцов на основе заданного порядка в представлении.

### <a name="related-topics"></a>Связанные статьи

[Загрузка примеров компонентов](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[Справочник по API инфраструктуры компонентов PowerApps](../reference/index.md)<br/>
[Справочник по схеме манифеста платформы компонентов PowerApps](../manifest-schema-reference/index.md)
