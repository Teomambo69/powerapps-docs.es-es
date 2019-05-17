---
title: Implementación de componentes personalizados mediante TypeScript | MicrosoftDocs
description: Cómo implementar un componente personalizado mediante TypeScript
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
---

# <a name="implement-controls-using-typescript"></a>Implemente controles mediante TypeScript

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

En este tutorial le guiará por crear un nuevo componente personalizado en Typescript. El componente de ejemplo es un componente de entrada lineal.  El componente de entrada lineal permite a los usuarios especificar valores numéricos mediante un control deslizante visual en lugar de escribir directamente los valores. 

> [!IMPORTANT]
> - Las herramientas de Microsoft PowerApps CLI son una versión preliminar y pueden ser diferentes de la versión lanzada comercialmente.
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)] 
> - Si proporciona comentarios acerca del software a Microsoft, usted concede a Microsoft, sin cargo alguno, el derecho de usar, compartir y comercializar sus comentarios de cualquier modo y con cualquier objetivo. 
> - Microsoft no ofrece soporte técnico para esta versión preliminar de característica. El soporte técnico de Microsoft no podrá ayudarle con los problemas o las preguntas que pueda tener.

## <a name="creating-a-new-component-project"></a>Crear un nuevo proyecto de componente

Para crear un nuevo proyecto, siga los pasos indicados abajo:

1. Abra una ventana de Developer Command Prompt for VS 2017.
2. Cree una nueva carpeta para el proyecto usando el comando `mkdir LinearControl`.
3. `cd` en el nuevo directorios y ejecute el comando `cd LinearControl` 
4. Cree el proyecto de componente usando el comando `pac pcf init --namespace SampleNamespace --name TSLinearInputControl --template field` 
5. Instale las herramientas de generación del proyecto usando el comando `npm install` 

## <a name="implementing-manifest"></a>Implementar el manifiesto

Un componente personalizado es por la información en el archivo de manifiesto `ControlManifest.Input.xml`. En este tutorial, este archivo se crea en la subcarpeta `<Your component Name>`. Para el componente de entrada lineal, una propiedad se define para almacenar el valor numérico de la entrada del control deslizante.

1. Abra el archivo `ControlManifest.Input.xml` en el editor de código (Visual Studio Code). El archivo `ControlManifest.Input.xml` define una propiedad de componente inicial llamada `sampleProperty`.

    ```XML
    <property name="sampleProperty" display-name-key="Property_Display_Key" description-key="Property_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" /> 
    ```

2. Cambie el nombre de `sampleProperty` y cambie el tipo de propiedad

    ```XML
    <property name="sliderValue" display-name-key="sliderValue _Display_Key" description-key=" sliderValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" /> 
    ```

3. El atributo of-type-group hace referencia a un grupo de números permitidos. Agregue el siguiente elemento type-group como elemento del mismo nivel que el elemento <property> del manifiesto. El type-group especifica el valor de componente y puede contener valores enteros, de divisa, punto flotante, o decimales.

    ```XML
    <type-group name="numbers"> 
      <type>Whole.None</type> 
      <type>Currency</type> 
      <type>FP</type> 
      <type>Decimal</type> 
     </type-group> 
    ```

4. Guarde los cambios en el archivo `ControlManifest.Input.xml`.
5. Cree el proyecto de componente usando el comando `npm run build`.
6. La generación crea un archivo de declaración Typescript actualizado en `TSLinearInputControl/generated folder`.  El archivo `ManifestTypes.d.ts` define las propiedades a las que el componente obtendrá acceso al código de origen Typescript.

## <a name="implementing-component-logic"></a>Implementar lógica del componente

El origen del componente personalizado se implementa en el archivo `index.ts`. El archivo `index.ts` incluye el andamio para métodos de interfaz requeridos por el marco de trabajo de componentes de PowerApps. 

1. Abra el archivo `index.ts` en el editor de código que prefiera.
2. Actualice la clase `TSLinearInputControl` con lo siguiente

```TypeScript
export class TSLinearInputControl implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // Value of the field is stored and used inside the control 
  private _value: number;
  // PCF framework delegate which will be assigned to this object which would be called whenever any update happens. 
  private _notifyOutputChanged: () => void;
  // label element created as part of this control
  private labelElement: HTMLLabelElement;
  // input element that is used to create the range slider
  private inputElement: HTMLInputElement;
  // Reference to the control container HTMLDivElement
  // This element contains all elements of our custom control example
  private _container: HTMLDivElement;
  // Reference to ComponentFramework Context object
  private _context: ComponentFramework.Context<IInputs>;
  // Event Handler 'refreshData' reference
  private _refreshData: EventListenerOrEventListenerObject;

  constructor() {
  }

  public init(context: ComponentFramework.Context<IInputs>, notifyOutputChanged: () => void, state: ComponentFramework.Dictionary, container: HTMLDivElement) {
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
    this._value = context.parameters.sliderValue.raw;
    this.inputElement.setAttribute("value", context.parameters.sliderValue.formatted ? context.parameters.sliderValue.formatted : "0");
    this.labelElement.innerHTML = context.parameters.sliderValue.formatted ? context.parameters.sliderValue.formatted : "0";
    // appending the HTML elements to the control's HTML container element.
    this._container.appendChild(this.inputElement);
    this._container.appendChild(this.labelElement);
    container.appendChild(this._container);
  }

  /**
  * Updates the values to the internal value variable we are storing and also updates the html label that displays the value
  * @param context : The "Input Properties" containing the parameters, control metadata and interface functions
  */

  public refreshData(evt: Event): void {
    this._value = (this.inputElement.value as any) as number;
    this.labelElement.innerHTML = this.inputElement.value;
    this._notifyOutputChanged();
  }

  public updateView(context: ComponentFramework.Context<IInputs>): void {
    // storing the latest context from the control.
    this._value = context.parameters.sliderValue.raw;
    this._context = context;
    this.inputElement.setAttribute("value",context.parameters.sliderValue.formatted ? context.parameters.sliderValue.formatted : "");
    this.labelElement.innerHTML = context.parameters.sliderValue.formatted ? context.parameters.sliderValue.formatted : "";
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

3. Vuelva a generar el proyecto usando el comando `npm run build` 
 
4. El componente se compila en la carpeta `out/controls/TSLinearInputControl`. Los artefactos de compilación incluyen:

   - bundle.js – Código origen del componente agrupado 
   - ControlManifest.xml – Archivo de manifiesto del componente real que se cargará en la organización de Common Data Service.

## <a name="adding-style-to-the-custom-component"></a>Agregar estilo al componente personalizado

El método `init` del control de entrada lineal crea un elemento de entrada y establece el atributo de clase en `linearslider`. El estilo para la clase `linearslider` se define en un archivo `css` aparte. Recursos de componente adicionales como `css` se pueden incluir con el componente personalizado para admitir otras personalizaciones.

1. Edite el archivo `ControlManifest.Input.xml` para incluir un recurso `css` adicional en el elemento <resources>
 
    ```XML
    <resources> 
      <code path="index.ts" order="1"/> 
      <css path="css/TS_LinearInputControl.css" order="1"/> 
    </resources> 
     ```

2. Cree una nueva subcarpeta `css` en la carpeta `TSLinearInputControl`. 
3. Cree un nuevo archivo `TS_LinearInputControl.css` en la subcarpeta `css`. 
4. Agregue el siguiente contenido de estilo al archivo `TS_LinearInputControl.css`

    ```CSS
    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider {
      margin: 1px 0;
      background: transparent;
      -webkit-appearance: none;
      width: 100%;
      padding: 0;
      height: 24px;
      -webkit-tap-highlight-color: transparent
    }

    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider:focus {
      outline: none;
    }

    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-webkit-slider-runnable-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-webkit-slider-thumb {
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

    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-moz-range-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-moz-range-thumb {
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

    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-ms-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-ms-thumb {
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

5. Guarde el `TS_LinearInputControl.css` 
6. Vuelva a generar el proyecto usando el comando `npm run build `.
7. Inspeccione la salida de compilación en `./out/controls/TSLinearInputControl` y observe que el archivo `TS_LinearInputControl.css` ahora está incluido con los artefactos de generación compilados. 

### <a name="see-also"></a>Vea también

[Descargar componentes de ejemplo](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[Actualizar controles existentes del marco de componentes de PowerApps](updating-existing-controls.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](overview.md)
