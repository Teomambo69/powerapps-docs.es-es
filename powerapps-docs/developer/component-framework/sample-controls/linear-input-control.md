---
title: " Componente de entrada lineal| Microsoft Docs"
description: Implementar componente de entrada lineal
ms.custom: ''
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 8c252b8b5baff22400aa510d0d71a3546c6361c4
ms.sourcegitcommit: 59f0b3adc56279b5673cbf04b4a55bd7678e1ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2020
ms.locfileid: "3091207"
---
# <a name="implementing-linear-input-component"></a>Implementar componente de entrada lineal

Este componente de ejemplo cambia la experiencia de usuario de interactuar con tipos numéricos del formulario. En vez de escribir los números, el componente de entrada lineal proporciona un control deslizante lineal con el que el valor del atributo se puede establecer en el formulario.  

Para implementar este componente, lo primero que necesita es definir el archivo de [Manifiesto](../manifest-schema-reference/manifest.md) y, a continuación, implementar la lógica personalizada en TypeScript. Puede descargar el componente de ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/component-framework/TS_LinearInputControl).

> [!div class="mx-imgBorder"]
> ![Componente de entrada lineal](../media/linear-input-control.png "Componente de entrada lineal")

## <a name="available-for"></a>Disponible para 

Aplicaciones basadas en modelos y aplicaciones de lienzo (vista previa pública) 

## <a name="manifest"></a>Manifiesto

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

## <a name="code"></a>Código

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
export class TSLinearInputControl
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // Value of the field is stored and used inside the control
  private _value: number;
  // Power Apps component framework framework delegate which will be assigned to this object which would be called whenever an update happens.
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

## <a name="resources"></a>Recursos

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

En este ejemplo, un [type -group](../manifest-schema-reference/type-group.md) se define y se llama como `numbers` que incluye tipos de valores decimales, enteros, flotantes y divisa en ese grupo del manifiesto. Este grupo se usa para enlazar la propiedad del componente.

Se crea un elemento de la entrada de tipo `range` con valores `min` y `max` establecidos en 1 y a 1000, respectivamente. Se crea un elemento de etiqueta que muestra el valor que es relativo a la posición del control deslizante. Adjunte una función `refreshData` al `eventlistener` en la entrada del componente.

Cree una variable local para guardar el [contexto](../reference/context.md) y `notifyOutputChanged`. Asigne el contexto y notifyOutputChanged desde los parámetros que se pasan como parte de la función init.

Implemente la lógica para la función `refreshData`. Como puede ver en el ejemplo, tomamos el valor del `inputElement` y establecemos el valor del componente, propiedad `innerHTML` del `labelElement` y luego llamamos a `notifyOutputChanged` para disponer en cascada los cambios sobre la capa del marco.

```TypeScript
public refreshData(context: ComponentFramework.IPropBag<InputsOutputs.IInputBag>) 
{ 
   this._value = (this.inputElement.value as any)as number; 
   this.labelElement.innerHTML = this.inputElement.value; 
   this._notifyOutputChanged(); 
} 
```

En el método `updateView`, obtenemos el valor del atributo desde los parámetros de contexto y lo establecemos con la variable de valor que almacena el valor del componente y también los elementos de entrada en el componente. 

```TypeScript

public updateView(context: ComponentFramework.IPropBag<InputsOutputs.IInputBag>): void 
 { 
    this._value = context.parameters.controlValue.raw; 
    this._context = context; 
    this.inputElement.setAttribute("value",context.parameters.controlValue.formatted ? context.parameters.controlValue.formatted : ""); 
    this.labelElement.innerHTML = context.parameters.controlValue.formatted ? context.parameters.controlValue.formatted : ""; 
   } 
 ```

### <a name="related-topics"></a>Temas relacionados

[Descargar componentes de ejemplo](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[¿Cómo usar los componentes de ejemplo?](../use-sample-components.md)<br/>
[Referencia de la API de Power Apps component framework](../reference/index.md)<br/>
[Referencia de esquema de manifiesto de Power Apps component framework](../manifest-schema-reference/index.md)
