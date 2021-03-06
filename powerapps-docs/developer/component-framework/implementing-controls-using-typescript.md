---
title: Cree su primer componente usando Power Apps component framework | MicrosoftDocs
description: Cómo implementar componentes de código mediante TypeScript
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: d60bbb70b4f716868aa5f7090750d8f334808444
ms.sourcegitcommit: 6fce86edacd9bfe49f8114a2a69bc18302cd01f9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "3260658"
---
# <a name="create-your-first-component"></a>Crear el primer componente 

 En este tutorial, demostramos cómo crear un componente de código de control deslizante lineal que permita a los usuarios cambiar los valores numéricos mediante un control deslizante visual en lugar de escribiendo los valores en el campo. 

Los siguientes pasos son necesarios para crear un componente de código deslizante lineal:

- [Crear un nuevo proyecto de componente](#creating-a-new-component-project)
- [Implementar el manifiesto](#implementing-manifest)
- [Implementar lógica de componentes con TypeScript](#implementing-component-logic)
- [Agregar estilo a los componentes de código](#adding-style-to-the-code-component)
- [Crear sus componentes de código](#build-your-code-components)
- [Empaquetar componentes de código](#packaging-your-code-components)
- [Agregar un componente a una aplicación basada en modelos](#adding-code-components-in-model-driven-apps)
- [Agregar un componente a una aplicación de lienzo](#adding-code-components-to-a-canvas-app)

## <a name="creating-a-new-component-project"></a>Crear un nuevo proyecto de componente

Para crear un nuevo proyecto:

1. Abra una ventana de **Developer Command Prompt for VS 2017**. Cree una nueva carpeta para el proyecto usando el comando siguiente: 
    ```CLI
     mkdir LinearComponent
    ```
                     
1. Vaya a la carpeta componente usando el comando `cd LinearComponent`. 
         
1. Cree un nuevo proyecto de componente pasando parámetros básicos utilizando el comando.

   ```CLI
    pac pcf init --namespace SampleNamespace --name TSLinearInputComponent --template field
    ``` 

1. Instale las herramientas de generación del proyecto usando el comando `npm install`. 
1. Abra la carpeta de proyecto en un entorno de desarrollo de su elección y empiece con el desarrollo del componente de código. La forma más rápida de comenzar es ejecutando `code .` desde el símbolo del sistema una vez que esté en el directorio del proyecto. Este comando abre el proyecto de componente en Código de Visual Studio.

## <a name="implementing-manifest"></a>Implementar el manifiesto

Manifest es un archivo XML que contiene los metadatos del componente de código. También define el comportamiento del componente de código. En este tutorial, este archivo de manifiesto se crea en la subcarpeta `<Your component Name>`. Cuando abra el archivo `ControlManifest.Input.xml` en código Visual Studio, observará que el archivo de manifiesto está predefinido con algunas propiedades. Más información: [Manifiesto](manifest-schema-reference/manifest.md).

Realice cambios en el archivo de manifiesto predefinido, como se muestra aquí:

1. El nodo [control](manifest-schema-reference/control.md) define el espacio de nombres, la versión y el nombre para mostrar del componente de código. Ahora, defina cada propiedad del nodo [control](manifest-schema-reference/control.md) como se muestra aquí:

   - **espacio de nombres**: Espacio de nombres del componente de código. 
   - **Constructor**: Constructor del componente de código.
   - **Versión**: Versión del componente. Cada vez que actualice el componente, deberá actualizar la versión para ver los últimos cambios en tiempo de ejecución.
   - **display-name-key**: Nombre del componente de código que se muestra en la interfaz de usuario.
   - **description-name-key**: Descripción del componente de código que se muestra en la interfaz de usuario.
   - **control-type**: tipo de componente de código. Solo se admiten tipos *estándar* de componentes de código.

     ```XML
      <?xml version="1.0" encoding="utf-8" ?>
      <manifest>
      <control namespace="SampleNameSpace" constructor="TSLinearInputComponent" version="1.0.0" display-name-key="TSLinearInputComponent_Display_Key" description-key="TSLinearInputComponent_Desc_Key" control-type="standard">
     ```

2. El nodo [propiedad](manifest-schema-reference/property.md) define las propiedades del componente de código como la definición del tipo de datos de campo. El nodo de la propiedad se especifica como elemento secundario bajo el elemento `control`. Defina el nodo [propiedad](manifest-schema-reference/property.md) como se muestra aquí:

   - **name**: Nombre de la propiedad.
   - **display-name-key**: Nombre para mostrar de la propiedad que se muestra en la interfaz de usuario.
   - **description-name-key**: Descripción de la propiedad que se muestra en la interfaz de usuario. 
   - **of-type-group**: [of-type-group](manifest-schema-reference/type-group.md) se usa cuando desea tener más de dos campos de tipo de datos. Agregue el elemento [of-type-group](manifest-schema-reference/type-group.md) como elemento del mismo nivel que el elemento `property` del manifiesto. El `of-type-group` especifica el valor de componente y puede contener valores enteros, de divisa, punto flotante, o decimales.
   - **uso**: Tiene dos propiedades, *bound* e *input*. Las propiedades enlazadas están enlazadas únicamente al valor del campo. Las propiedades de entrada están enlazadas a un campo o permiten un valor estático.
   - **requerida**: Define si la propiedad es requerida o no

     ```XML
      <property name="sliderValue" display-name-key="sliderValue_Display_Key" description-key="sliderValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" />
      ```

3. El nodo [resources](manifest-schema-reference/resources.md) define la visualización del componente de código. Contiene todos los recursos que crean la visualización y el diseño del componente de código. El [código](manifest-schema-reference/code.md) se especifica como elemento secundario bajo el elemento recursos. Defina los [recursos](manifest-schema-reference/resources.md) como se muestra aquí:

   - **code**: Hace referencia a la ruta de acceso donde se ubican todos los archivos de recursos.
 
      ```XML
      <resources>
        <code path="index.ts" order="1" />
        <css path="css/TS_LinearInputComponent.css" order="1" />
      </resources>
        ```
      El archivo de manifiesto general ser de este tipo: 

     ```XML
      <?xml version="1.0" encoding="utf-8" ?>
      <manifest>
      <control namespace="SampleNamespace" constructor="TSLinearInputComponent" version="1.0.0" display-name-key="TSLinearInputComponent_Display_Key" description-key="TSLinearInputComponent_Desc_Key" control-type="standard">
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

4. Guarde los cambios en el archivo `ControlManifest.Input.xml`.

## <a name="implementing-component-logic"></a>Implementar lógica del componente

El siguiente paso después de implementar el archivo de manifiesto es implementar la lógica de componente con TypeScript. La lógica de componente se debe implementar en el archivo `index.ts`. Cuando abra el archivo `index.ts` en el código de Visual Studio, observará que cuatro clases esenciales están predefinidas. Ahora, implementemos la lógica para el componente de código. 

1. Abra el archivo `index.ts` en el editor de código que prefiera.
2. Actualice la clase `TSLinearInputComponent` con el siguiente código:

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
export class TSLinearInputComponent
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // Value of the field is stored and used inside the component
  private _value: number;
  // Power Apps component framework delegate which will be assigned to this object which would be called whenever any update happens.
  private _notifyOutputChanged: () => void;
  // label element created as part of this component
  private labelElement: HTMLLabelElement;
  // input element that is used to create the range slider
  private inputElement: HTMLInputElement;
  // reference to the component container HTMLDivElement
  // This element contains all elements of our code component example
  private _container: HTMLDivElement;
  // reference to Power Apps component framework Context object
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
    this.inputElement.value =
      context.parameters.sliderValue.formatted
        ? context.parameters.sliderValue.formatted
        : "0";
    
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
    this.inputElement.value =
     
      context.parameters.sliderValue.formatted
        ? context.parameters.sliderValue.formatted
        : "";
    
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

3. Guarde los cambios en el archivo `index.ts`.

## <a name="adding-style-to-the-code-component"></a>Agregar estilo al componente de código

Los programadores y proveedores de aplicaciones pueden definir el diseño para representar sus componentes de código visualmente usando CSS. CSS permite que los desarrolladores describan la presentación de componentes de código, incluidos estilo, colores, diseños, y fuentes. El método [init](reference/control/init.md) del componente de entrada lineal crea un elemento de entrada y establece el atributo de clase en `linearslider`. El estilo para la clase `linearslider` se define en un archivo `CSS` aparte. Recursos de componente adicionales como `CSS` se pueden incluir con el componente de código para admitir otras personalizaciones.

> [!IMPORTANT]
> Cuando implemente estilos en sus componentes de código mediante CSS, asegúrese de que el ámbito de CSS es el control. Para ello, use las clases CSS generadas automáticamente y aplíqueselas al elemento `DIV` del contenedor para el componente. Si el código CSS tiene un ámbito global, es probable que rompa el estilo existente del formulario o la pantalla donde se representa el componente de código. Si usa un marco de trabajo CSS de terceros, debe usar una versión que ya tenga espacio de nombres o, de lo contrario, encapsular ese marco en un espacio de nombres, ya sea manualmente o mediante un preprocesador de CSS.

1. Cree una nueva subcarpeta `css` en la carpeta `TSLinearInputComponent`. 
2. Cree un nuevo archivo `TS_LinearInputComponent.css` en la subcarpeta `css`. 
3. Agregue el siguiente contenido de estilo al archivo `TS_LinearInputComponent.css`:

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

5. Guarde el archivo `TS_LinearInputComponent.css`.
6. Edite el archivo `ControlManifest.Input.xml` para incluir el archivo de recurso `CSS` en el elemento de recursos.
 
    ```XML
    <resources> 
      <code path="index.ts" order="1"/> 
      <css path="css/TS_LinearInputComponent.css" order="1"/> 
    </resources> 
     ```

## <a name="build-your-code-components"></a>Crear sus componentes de código

Después de terminar de agregar manifiesto, lógica de componentes y estilo, compile los componentes del código con el comando:
```
npm run build
```

De forma alternativa, para crear el componente del proyecto, abra la carpeta del proyecto que contiene `package.json` en Visual Studio Code y use el comando (Ctrl-Shift-B) y después las opciones de creación. La generación crea un archivo de declaración de tipo TypeScript actualizado en la carpeta `TSLinearInputComponent/generated`.
El componente se compila en la carpeta `out/controls/TSLinearInputComponent`. Los artefactos de compilación incluyen:

   - bundle.js – Código origen del componente agrupado. 
   - ControlManifest.xml – Archivo de manifiesto del componente real que se carga en la organización de Common Data Service.

## <a name="debugging-your-code-component"></a>Depurar el componente de código

Una vez que termine de implementar la lógica del componente de código, ejecute el siguiente comando de iniciar el proceso de depuración. Más información: [Depurar componentes de código](debugging-custom-controls.md)

```CLI
npm start
```

## <a name="packaging-your-code-components"></a>Empaquetar componentes de código

Siga estos pasos para crear e importar un archivo de [solución](https://docs.microsoft.com/powerapps/maker/common-data-service/solutions-overview):

1. Cree una nueva carpeta **Solutions** dentro de la carpeta **LinearComponent** y vaya a la carpeta. 
2. Cree un nuevo proyecto de solución en la carpeta **LinearComponent** usando el comando siguiente:
 
    ```CLI
     pac solution init --publisher-name developer --publisher-prefix dev 
    ```

   > [!NOTE]
   > Los valores [publisher-name](https://docs.microsoft.com/powerapps/developer/common-data-service/reference/entities/publisher) y [publisher-prefix](https://docs.microsoft.com/powerapps/maker/common-data-service/change-solution-publisher-prefix) deben ser únicos a su entorno.
 
3. Cuando se crea el nuevo proyecto de solución, debe hacer referencia a la ubicación donde se ubica el componente creado. Puede agregar la referencia usando el comando siguiente:

    ```CLI
     pac solution add-reference --path c:\users\LinearComponent
    ```

4. Para generar un archivo zip del proyecto de la solución, deberá `cd` en el directorio del proyecto de la solución y compilar el proyecto usando el comando siguiente: 

    ```CLI
     msbuild /t:restore
    ```

5. Ejecute de nuevo el siguiente comando:
    ```CLI
     msbuild
    ```
    > [!TIP]
    > Recibirá el error: *No use la función `eval` o sus equivalentes funcionales*, cuando cree el archivo de solución utilizando el comando `msbuild` y lo importe en Common Data Service y ejecuta el comprobador de soluciones.
    > Vuelva a compilar el archivo de solución con el comando `msbuild/property:configuration:Release` y reimporte la solución en Common Data Service y ejecute el comprobador de soluciones.
      
    > [!NOTE]
    > Asegúrese de que está activado **Destinos de NuGet y tareas de compilación**. Para habilitarla:
    > - Abra **Instalador de Visual Studio**.
    > - Para Visual Studio 2017, seleccione **Modificar**.
    > - Seleccione **Componentes individuales**.
    > - En **Herramientas de código**, active **Destinos de NuGet y tareas de compilación**.

6. El archivo zip generado de la solución se encuentra en la carpeta `Solution\bin\debug`.
7. [Importe manualmente la solución en Common Data Service](https://docs.microsoft.com/powerapps/maker/common-data-service/import-update-export-solutions) con el portal web una vez que el archivo zip esté listo o usando automáticamente la [herramienta de compilación de Power Apps](https://marketplace.visualstudio.com/items?itemName=microsoft-IsvExpTools.PowerApps-BuildTools).

## <a name="adding-code-components-in-model-driven-apps"></a>Agregar componentes código en aplicaciones basadas en modelo

Para agregar un componente de código como un componente de entrada lineal, siga los pasos mencionados en el artículo [Agregar componentes a campos y entidades](add-custom-controls-to-a-field-or-entity.md).

## <a name="adding-code-components-to-a-canvas-app"></a>Agregar componentes de código a una aplicación de lienzo

Para agregar los componentes del código a una aplicación de lienzo, siga los pasos del artículo [Agregar componentes de código a una aplicación de lienzo](component-framework-for-canvas-apps.md#add-components-to-a-canvas-app).

### <a name="see-also"></a>Vea también

[Descargar componentes de ejemplo](https://github.com/microsoft/PowerApps-Samples/tree/master/component-framework)<br/>
[Más información sobre Power Apps component framework](https://docs.microsoft.com/learn/paths/use-power-apps-component-framework)<br/>
[Actualizar componentes existentes de Power Apps component framework](updating-existing-controls.md)<br/>
[Power Apps build tools](https://docs.microsoft.com/powerapps/developer/common-data-service/build-tools-overview)<br/>
[Referencia de la API de Power Apps component framework](reference/index.md)<br/>
[Información general sobre Power Apps component framework](overview.md)
