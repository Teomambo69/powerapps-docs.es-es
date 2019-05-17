---
title: Implementación de controles personalizados mediante TypeScript | MicrosoftDocs
description: Cómo implementar un control personalizado mediante TypeScript
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.author: nabuthuk
---

# <a name="implement-controls-using-typescript"></a>Implemente controles mediante TypeScript

En este tutorial le guiará por crear un nuevo control personalizado en Typescript. El control de ejemplo es un control de entrada lineal. El control de entrada lineal permite a los usuarios especificar valores numéricos mediante un control deslizante visual en lugar de escribir directamente los valores.


## <a name="implementing-manifest"></a>Implementar el manifiesto

Un control personalizado es por la información en el archivo de manifiesto `Manifest.xml`. Para el control de entrada lineal, una propiedad se define para almacenar el valor numérico de la entrada del control deslizante.

1. Abra el archivo `Manifest.xml` en el editor de código (Visual Studio Code). El archivo `Manifest.xml` define una propiedad de control inicial llamada `sampleProperty`.

    ```XML
    <property name="sampleProperty" display-name-key="Property_Display_Key" description-key="Property_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" /> 
    ```

2. Cambie el nombre de `sampleProperty` y cambie el tipo de propiedad

    ```XML
    <property name="sliderValue" display-name-key=" sliderValue _Display_Key" description-key=" sliderValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" /> 
    ```

3. El atributo of-type-group hace referencia a un grupo de números permitidos. Agregue el siguiente elemento type-group como elemento del mismo nivel que el elemento <property> del manifiesto. El type-group especifica el valor de control y puede contener valores enteros, de divisa, punto flotante, o decimales.

    ```XML
    <type-group name="numbers"> 
      <type>Whole.None</type> 
      <type>Currency</type> 
      <type>FP</type> 
      <type>Decimal</type> 
     </type-group> 
    ```


4. Guarde los cambios en el archivo `ControlManifest.Input.xml`.
5. Cree el proyecto de control usando el comando `npm run build`.
6. La generación crea un archivo de declaración Typescript actualizado en `TSLinearInputControl/generated folder`.  El archivo `ManifestTypes.d.ts` define las propiedades a las que el control obtendrá acceso al código de origen Typescript.

## <a name="implementing-control-logic"></a>Implementar lógica de control

El origen del control personalizado se implementa en el archivo `index.ts`. El archivo `index.ts` incluye el andamio para métodos de interfaz requeridos por el marco de trabajo de componentes de PowerApps. 

1. Abra el archivo `index.ts` en el editor de código que prefiera.
2. Actualice la clase `TSLinearInputControl` con lo siguiente

```TypeScript
export class TSLinearInputControl implements ComponentFramework.StandardControl<IInputs, IOutputs> {
// Value of the field is stored and used inside the control 
private _value: number;
// PowerApps component framework framework delegate which will be assigned to this object which would be called whenever any update happens. 
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
    
public init(context: ComponentFramework.Context<IInputs>, notifyOutputChanged: () => void, state: ComponentFramework.Dictionary, container:HTMLDivElement)
  {
     this._context = context;
     this._container = document.createElement("div");
     this._notifyOutputChanged = notifyOutputChanged;
     this._refreshData = this.refreshData.bind(this);
     // creating HTML elements for the input type range and binding it to the function which refreshes the control data
     this.inputElement = document.createElement("input");
     this.inputElement.setAttribute("type","range");
     this.inputElement.addEventListener("input",this._refreshData);
     //setting the max and min values for the control.
     this.inputElement.setAttribute("min","1");
     this.inputElement.setAttribute("max","1000");
     this.inputElement.setAttribute("class","linearslider");
     this.inputElement.setAttribute("id","linearrangeinput");
     // creating a HTML label element that shows the value that is set on the linear range control
     this.labelElement = document.createElement("label");
     this.labelElement.setAttribute("class", "TS_LinearRangeLabel");
     this.labelElement.setAttribute("id","lrclabel");
     // retrieving the latest value from the control and setting it to the HTMl elements.
     this._value = context.parameters.sliderValue.raw;
     this.inputElement.setAttribute("value",context.parameters.sliderValue.formatted ? context.parameters.sliderValue.formatted : "0");
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

public refreshData(evt: Event) : void
  {
      this._value = (this.inputElement.value as any)as number;
      this.labelElement.innerHTML = this.inputElement.value;
      this._notifyOutputChanged();
    }
        
public updateView(context: ComponentFramework.Context<IInputs>): void
 {
      // storing the latest context from the control.
    this._value = context.parameters.sliderValue.raw;
    this._context = context;
    this.inputElement.setAttribute("value",context.parameters.sliderValue.formatted ? context.parameters.sliderValue.formatted : "");
    this.labelElement.innerHTML = context.parameters.sliderValue.formatted ? context.parameters.sliderValue.formatted : "";
        }
    
public getOutputs(): IOutputs
  {
     return {
            sliderValue : this._value
            };
        }
        
public destroy()
   {
     this.inputElement.removeEventListener("input", this._refreshData);
        }
    }
```

3. Vuelva a generar el proyecto usando el comando `npm run build` 
 
4. El control se compila en la carpeta `/out/controls/TSLinearInputControl`. Los artefactos de compilación incluyen:

   - bundle.js – Código origen del control agrupado 
   - ControlManifest.xml – Archivo de manifiesto del control real que se cargará en la organización de Common Data Service.

## <a name="adding-style-to-the-custom-control"></a>Agregar estilo al control personalizado

El método `init` del control de entrada lineal crea un elemento de entrada y establece el atributo de clase en `linearslider`. El estilo para la clase `linearslider` se define en un archivo `css` aparte. Recursos de control adicionales como `css` se pueden incluir con el control personalizado para admitir otras personalizaciones.

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
    background:transparent; 
   -webkit-appearance:none; 
    width:100%;padding:0; 
    height:24px; 
   -webkit-tap-highlight-color:transparent 
    } 
    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider:focus { 
     outline: none; 
     } 
    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-webkit-slider-runnable-track {    
     background: #666; 
     height:2px; 
     cursor:pointer 
     }    
     .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-webkit-slider-thumb {    
     background: #666;    
     border:0 solid #f00; 
     height:24px; 
     width:10px; 
     border-radius:48px; 
     cursor:pointer; 
     opacity:1; 
    -webkit-appearance:none; 
     margin-top:-12px 
     }     
    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-moz-range-track {    
     background: #666;    
     height:2px; 
     cursor:pointer   
     }    
     .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-moz-range-thumb {    
     background: #666;    
     border:0 solid #f00; 
     height:24px; 
     width:10px; 
     border-radius:48px; 
    cursor:pointer; 
    opacity:1; 
   -webkit-appearance:none; 
   margin-top:-12px 
   }    
   .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-ms-track {    
    background: #666;    
    height:2px; 
    cursor:pointer   
     }     
    .SampleNamespace\.TSLinearInputControl input[type=range].linearslider::-ms-thumb {    
    background: #666;    
    border:0 solid #f00; 
    height:24px; 
    width:10px; 
    border-radius:48px; 
   cursor:pointer; 
   opacity:1; 
   -webkit-appearance:none; 
    } 
   ```

5. Guarde el `TS_LinearInputControl.css` 
6. Vuelva a generar el proyecto usando el comando `npm run build `.
7. Inspeccione la salida de compilación en `./out/controls/TSLinearInputControl` y observe que el archivo `TS_LinearInputControl.css` ahora está incluido con los artefactos de generación compilados. 


### <a name="see-also"></a>Vea también

[Actualizar controles existentes del marco de componentes de PowerApps](updating-existing-controls.md)
