---
title: Implementación de componentes personalizados mediante TypeScript | MicrosoftDocs
description: Cómo implementar un componente personalizado mediante TypeScript
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
author: Nkrb
---

# <a name="implement-components-using-typescript"></a>Implementar componentes con TypeScript

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

En este tutorial le guiará por el proceso de crear un nuevo componente personalizado en Typescript. El componente de ejemplo es un componente de entrada lineal. El componente de entrada lineal permite a los usuarios especificar valores numéricos mediante un control deslizante visual en lugar de escribir directamente los valores. 

## <a name="creating-a-new-component-project"></a>Crear un nuevo proyecto de componente

Para crear un nuevo proyecto, siga los pasos indicados abajo:

1. Abra una ventana de Developer Command Prompt for VS 2017.
2. Cree una nueva carpeta para el proyecto usando el comando `mkdir LinearComponent`.
3. `cd` en el nuevo directorios y ejecute el comando `cd LinearComponent` 
4. Cree el proyecto de componente usando el comando `pac pcf init --namespace SampleNamespace --name TSLinearInputControl --template field` 
5. Instale las herramientas de generación del proyecto usando el comando `npm install` 
6. Abra el proyecto cualquier entorno de desarrollo de su elección y empiece a implementar el componente personalizado.

## <a name="implementing-manifest"></a>Implementar el manifiesto

Un componente personalizado es por la información en el archivo de manifiesto `ControlManifest.Input.xml`. En este tutorial, este archivo se crea en la subcarpeta `<Your component Name>`. Para el componente de entrada lineal, una propiedad se define para almacenar el valor numérico de la entrada del control deslizante.

1. Abra el archivo `ControlManifest.Input.xml` en el editor de código (Visual Studio Code). El archivo `ControlManifest.Input.xml` define una propiedad de componente inicial llamada `sampleProperty`.

    ```XML
    <property name="sampleProperty" display-name-key="Property_Display_Key" description-key="Property_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" /> 
    ```

2. Cambie el nombre de `sampleProperty` y cambie el tipo de propiedad

    ```XML
    <property name="sliderValue" display-name-key="sliderValue_Display_Key" description-key="sliderValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" /> 
    ```

3. El atributo of-type-group hace referencia a un grupo de números permitidos. Agregue el siguiente elemento type-group como elemento del mismo nivel que el elemento de propiedad del manifiesto. El type-group especifica el valor de componente y puede contener valores enteros, de divisa, punto flotante, o decimales.

    ```XML
    <type-group name="numbers"> 
      <type>Whole.None</type> 
      <type>Currency</type> 
      <type>FP</type> 
      <type>Decimal</type> 
     </type-group> 
    ```

4. Guarde los cambios en el archivo `ControlManifest.Input.xml`.
5. Ahora, cree una nueva carpeta dentro de la carpeta `TSLinearInputControl` y llámela **css**.
6. Cree un archivo CSS para [agregar estilos al componente personalizado](#adding-style-to-the-custom-component)
7. Cree el proyecto de componente usando el comando `npm run build`.
8. La generación crea un archivo de declaración Typescript actualizado en `TSLinearInputControl/generated folder`.

## <a name="implementing-component-logic"></a>Implementar lógica del componente

El origen del componente personalizado se implementa en el archivo `index.ts`. El archivo `index.ts` incluye el andamio para métodos de interfaz requeridos por el marco de trabajo de componentes de PowerApps. 

1. Abra el archivo `index.ts` en el editor de código que prefiera.
2. Actualice la clase `TSLinearInputControl` con lo siguiente

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
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
   - ControlManifest.xml – Archivo de manifiesto del componente real que se carga en la organización de Common Data Service.

## <a name="adding-style-to-the-custom-component"></a>Agregar estilo al componente personalizado

El método `init` del componente de entrada lineal crea un elemento de entrada y establece el atributo de clase en `linearslider`. El estilo para la clase `linearslider` se define en un archivo `CSS` aparte. Recursos de componente adicionales como `CSS` se pueden incluir con el componente personalizado para admitir otras personalizaciones.

1. Cree una nueva subcarpeta `css` en la carpeta `TSLinearInputControl`. 
2. Cree un nuevo archivo `TS_LinearInputControl.css` en la subcarpeta `css`. 
3. Agregue el siguiente contenido de estilo al archivo `TS_LinearInputControl.css`

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

5. Guarde el archivo `TS_LinearInputControl.css`.
6. Edite el archivo `ControlManifest.Input.xml` para incluir el archivo de recurso `CSS` en el elemento de recursos
 
    ```XML
    <resources> 
      <code path="index.ts" order="1"/> 
      <css path="css/TS_LinearInputControl.css" order="1"/> 
    </resources> 
     ```
7. Vuelva a generar el proyecto usando el comando  
   ```CLI
   npm run build
   ```
8. Inspeccione la salida de compilación en **./out/controls/TSLinearInputControl** y observe que el archivo **TS_LinearInputControl.css** ahora está incluido con los artefactos de generación compilados. 

## <a name="debugging-your-custom-component"></a>Depurar el componente personalizado

Una vez que termine de implementar la lógica del componente personalizado, ejecute el siguiente comando de iniciar el proceso de depuración. Más información: [Depurar componentes personalizados](debugging-custom-controls.md)

```CLI
npm start
```

## <a name="packaging-your-custom-components"></a>Empaquetar componentes personalizados

Siga los pasos indicados a continuación para crear e importar un archivo de [solución](https://docs.microsoft.com/dynamics365/customer-engagement/customize/solutions-overview):

1. Cree una nueva carpeta **Solutions** dentro de la carpeta **LinearComponent** y vaya a la carpeta. 
2. Cree un nuevo proyecto de solución en la carpeta **LinearComponent** usando el comando 
 
    ```CLI
     pac solution init --publisher-name developer --publisher-prefix dev 
    ```

   > [!NOTE]
   > Los valores [publisher-name](https://docs.microsoft.com/powerapps/developer/common-data-service/reference/entities/publisher) y [publisher-prefix](https://docs.microsoft.com/powerapps/maker/common-data-service/change-solution-publisher-prefix) deben ser únicos a su entorno.
 
3. Cuando se crea el nuevo proyecto de solución, debe hacer referencia a la ubicación donde se ubica el componente creado. Puede agregar la referencia usando el comando 

    ```CLI
     pac solution add-reference --path c:\users\LinearComponent
    ```

4. Para generar un archivo zip del proyecto de la solución, deberá `cd` en el directorio del proyecto de la solución y compilar el proyecto usando el comando 

    ```CLI
     msbuild /t:restore
    ```

5. Ejecute de nuevo el siguiente comando msbuild
    ```CLI
     msbuild
    ```

    > [!NOTE]
    > Asegúrese de que está activado **Destinos de NuGet y tareas de compilación**. Para habilitarlo
    > - Abra **Instalador de Visual Studio**
    > - Para VS 2017, haga clic en **Modificar**
    > - Haga clic en **Componentes individuales**
    > - En **Herramientas de código**, active **Destinos de NuGet y tareas de compilación**

6. El archivo zip generado de la solución se encuentra en `Solution\\bin\debug\`.
7. Debe [importar la solución](https://docs.microsoft.com/dynamics365/customer-engagement/customize/import-update-export-solutions) manualmente mediante el portal web una vez que el archivo zip esté listo.

## <a name="adding-custom-components-to-a-field-or-an-entity"></a>Agregar componentes personalizados a un campo o una entidad

Para agregar un componente personalizado como un componente del conjunto de datos o un componente de una tabla sencilla a una cuadrícula o vista, siga los pasos a los que se hace referencia en el tema [Agregar componentes a campos y entidades](add-custom-controls-to-a-field-or-entity.md).

### <a name="see-also"></a>Vea también

[Descargar componentes de ejemplo](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[Actualizar controles existentes del marco de componentes de PowerApps](updating-existing-controls.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](overview.md)
