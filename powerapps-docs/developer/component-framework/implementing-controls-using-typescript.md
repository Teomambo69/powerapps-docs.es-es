---
title: Implementar componentes de código mediante TypeScript | MicrosoftDocs
description: Cómo implementar componentes de código mediante TypeScript
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
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025756"
---
# <a name="implement-components-using-typescript"></a>Implementar componentes con TypeScript

Este tema le guía por el proceso de creación de un nuevo componente de código en TypeScript mediante la CLI de PowerApps. En este tutorial, se creará un componente de código lineal de ejemplo que permite a los usuarios cambiar los valores numéricos con un control deslizante visual en lugar de escribir los valores en el campo. 

Los artefactos necesarios para compilar componentes de código son:

1. [Crear un nuevo proyecto de componente](#creating-a-new-component-project)
2. [Implementación del manifiesto](#implementing-manifest)
3. [Implementación de la lógica de componentes con TypeScript](#implementing-component-logic)
4. [Agregar estilo a los componentes de código](#adding-style-to-the-code-component)
5. [Empaquetar componentes de código](#packaging-your-code-components)

## <a name="creating-a-new-component-project"></a>Crear un nuevo proyecto de componente

Para crear un nuevo proyecto:

1. Abra un **símbolo del sistema para desarrolladores para la ventana de VS 2017** .
1. Cree una nueva carpeta para el proyecto con el siguiente comando: 
    ```CLI
    mkdir LinearComponent
    ```

1. Vaya a la carpeta de componentes con la `cd LinearComponent`de comandos. 
   
1. Cree un nuevo proyecto de componente pasando los parámetros básicos con el comando.

   ```CLI
    pac pcf init --namespace SampleNamespace --name TSLinearInputComponent --template field
    ``` 

1. Instale las herramientas de compilación del proyecto mediante el `npm install` de comandos. 
1. Abra la carpeta del proyecto `C:\Users\<your name>\Documents\<My_code_Component>` en el entorno de desarrollador que prefiera y empiece a trabajar con el desarrollo de componentes de código. La forma más rápida de empezar es mediante la ejecución de `code .` desde el símbolo del sistema una vez que se encuentra en el directorio `C:\Users\<your name>\Documents\<My_code_Component>`. Este comando abre el proyecto de componente en Visual Studio Code.

## <a name="implementing-manifest"></a>Implementación del manifiesto

El manifiesto es un archivo XML que contiene los metadatos del componente de código. También define el comportamiento del componente de código. En este tutorial, este archivo de manifiesto se crea en la subcarpeta `<Your component Name>`. Al abrir el archivo de `ControlManifest.Input.xml` en Visual Studio Code, observará que el archivo de manifiesto está predefinido con algunas propiedades. Más información: [manifiesto](manifest-schema-reference/manifest.md).

Realice cambios en el archivo de manifiesto predefinido, como se muestra aquí:

1. El nodo de [control](manifest-schema-reference/control.md) define el espacio de nombres, la versión y el nombre para mostrar del componente de código. Ahora, defina cada propiedad del nodo de [control](manifest-schema-reference/control.md) como se muestra aquí:

   - **espacio de nombres**: espacio de nombres del componente de código. 
   - **Constructor**: constructor del componente de código.
   - **Versión**: versión del componente. Siempre que actualice el componente, deberá actualizar la versión para ver los cambios más recientes en el tiempo de ejecución.
   - **Display-Name-Key**: nombre del componente de código que se muestra en la interfaz de usuario.
   - **Descripción-nombre-clave**: Descripción del componente de código que se muestra en la interfaz de usuario.
   - **tipo de control**: tipo de componente de código. Solo se admite el tipo *estándar* de componentes de código.

     ```XML
      <?xml version="1.0" encoding="utf-8" ?>
      <manifest>
      <control namespace="SampleNameSpace" constructor="TSLinearInputComponent" version="1.0.0" display-name-key="Linear Input Component" description-key="Allows you to enter the numeric values using the visual slider." control-type="standard">
     ```

2. El nodo de [propiedades](manifest-schema-reference/property.md) define las propiedades del componente de código como la definición del tipo de datos del campo. El nodo de propiedad se especifica como el elemento secundario bajo el elemento `control`. Defina el nodo de [propiedad](manifest-schema-reference/property.md) como se muestra aquí:

   - **Name**: nombre de la propiedad.
   - **Display-Name-Key**: nombre para mostrar de la propiedad que se muestra en la interfaz de usuario.
   - **Descripción-nombre-clave**: Descripción de la propiedad que se muestra en la interfaz de usuario. 
   - **de-Type-Group**: se usa la [de-Type-Group](manifest-schema-reference/type-group.md) cuando desea tener más de dos campos de tipo de datos. Agregue el elemento [del tipo-type-Group](manifest-schema-reference/type-group.md) como elemento relacionado con el elemento `property` del manifiesto. El `of-type-group` especifica el valor del componente y puede contener valores enteros, de moneda, de punto flotante o decimales.
   - **uso**: tiene dos propiedades, *enlazadas* y de *entrada*. Las propiedades enlazadas solo se enlazan al valor del campo. Las propiedades de entrada están enlazadas a un campo o permiten un valor estático.
   - **requerido**: define si la propiedad es obligatoria.

     ```XML
      <property name="sliderValue" display-name-key="sliderValue_Display_Key" description-key="sliderValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" />
      ```
3. El nodo [recursos](manifest-schema-reference/resources.md) define la visualización del componente de código. Contiene todos los recursos que compilan la visualización y el estilo del componente de código. El [código](manifest-schema-reference/code.md) se especifica como un elemento secundario en el elemento Resources. Defina los [recursos](manifest-schema-reference/resources.md) como se muestra aquí:

   - **código**: hace referencia a la ruta de acceso donde se encuentran todos los archivos de recursos.
 
      ```XML
      <resources>
        <code path="index.ts" order="1" />
        <css path="css/TS_LinearInputComponent.css" order="1" />
        </resources>
        ```
      El archivo de manifiesto general debe tener un aspecto similar al siguiente: 

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

4. Guarde los cambios en el archivo de `ControlManifest.Input.xml`.
5. Ahora, cree una nueva carpeta dentro de la carpeta `TSLinearInputComponent` y asígnele el nombre **CSS**.
6. Cree un archivo CSS para [Agregar estilo al componente de código](#adding-style-to-the-code-component).
7. Compile el proyecto de componente con la `npm run build` de comandos.
8. La compilación genera un archivo de declaración de tipo TypeScript actualizado en la carpeta `TSLinearInputComponent/generated`.

## <a name="implementing-component-logic"></a>Implementar la lógica de componentes

El siguiente paso después de implementar el archivo de manifiesto es implementar la lógica del componente mediante TypeScript. La lógica del componente debe implementarse dentro del archivo de `index.ts`. Al abrir el archivo de `index.ts` en el Visual Studio Code, observará que las cuatro clases esenciales están predefinidas. Ahora, vamos a implementar la lógica para el componente de código. 

1. Abra el archivo `index.ts` en el editor de código de su elección.
2. Actualice la clase `TSLinearInputComponent` con el código siguiente:

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

3. Vuelva a generar el proyecto mediante el `npm run build` de comandos. 
 
4. El componente se compila en la carpeta `out/controls/TSLinearInputComponent`. Los artefactos de compilación incluyen:

   - bundle. js: código fuente del componente agrupado. 
   - ControlManifest. xml: archivo de manifiesto de componente real que se carga en la organización de Common Data Service.

## <a name="adding-style-to-the-code-component"></a>Agregar estilo al componente de código

Los desarrolladores y los programadores de aplicaciones pueden definir su estilo para representar visualmente los componentes de código mediante CSS. CSS permite a los desarrolladores describir la presentación de componentes de código, incluidos el estilo, los colores, los diseños y las fuentes. El método [init](reference/control/init.md) del componente de entrada lineal crea un elemento de entrada y establece el atributo de clase en `linearslider`. El estilo de la clase `linearslider` se define en un archivo de `CSS` independiente. Se pueden incluir recursos de componentes adicionales, como `CSS` archivos, con el componente de código para admitir más personalizaciones.

1. Cree una nueva subcarpeta `css` en la carpeta `TSLinearInputComponent`. 
2. Cree un nuevo archivo de `TS_LinearInputComponent.css` dentro de la subcarpeta `css`. 
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

5. Guarde el archivo de `TS_LinearInputComponent.css`.
6. Edite el archivo de `ControlManifest.Input.xml` para incluir el archivo de recursos `CSS` en el elemento Resources.
 
    ```XML
    <resources> 
      <code path="index.ts" order="1"/> 
      <css path="css/TS_LinearInputComponent.css" order="1"/> 
    </resources> 
     ```
7. Vuelva a generar el proyecto con el siguiente comando: 
   ```CLI
   npm run build
   ```
8. Inspeccione la salida de la compilación en el archivo **./out/Controls/TSLinearInputComponent** y observe que el archivo **TS_LinearInputComponent. CSS** se incluye ahora con los artefactos de compilación compilados. 

## <a name="debugging-your-code-component"></a>Depurar el componente de código

Una vez que haya terminado de implementar la lógica del componente de código, ejecute el siguiente comando para iniciar el proceso de depuración. Más información: [depurar componentes de código](debugging-custom-controls.md)

```CLI
npm start
```

## <a name="packaging-your-code-components"></a>Empaquetar los componentes de código

Siga estos pasos para crear e importar un archivo de [solución](https://docs.microsoft.com/powerapps/maker/common-data-service/solutions-overview) :

1. Cree una nueva carpeta **soluciones** dentro de la carpeta **LinearComponent** y navegue hasta la carpeta. 
2. Cree un nuevo proyecto de solución en la carpeta **LinearComponent** con el siguiente comando:
 
    ```CLI
     pac solution init --publisher-name developer --publisher-prefix dev 
    ```

   > [!NOTE]
   > Los valores de [nombre del publicador](https://docs.microsoft.com/powerapps/developer/common-data-service/reference/entities/publisher) y [prefijo del publicador](https://docs.microsoft.com/powerapps/maker/common-data-service/change-solution-publisher-prefix) deben ser únicos para su entorno.
 
3. Una vez creado el nuevo proyecto de solución, debe hacer referencia a la ubicación donde se encuentra el componente creado. Puede Agregar la referencia con el siguiente comando:

    ```CLI
     pac solution add-reference --path c:\users\LinearComponent
    ```

4. Para generar un archivo zip desde el proyecto de la solución, debe `cd` en el directorio del proyecto de la solución y compilar el proyecto con el siguiente comando: 

    ```CLI
     msbuild /t:restore
    ```

5. Vuelva a ejecutar el siguiente comando MSBuild:
    ```CLI
     msbuild
    ```

    > [!NOTE]
    > Asegúrese de que los **destinos de NuGet & compilar tareas** está activada. Para habilitarlo:
    > - Abra **instalador de Visual Studio**.
    > - Para Visual Studio 2017, seleccione **modificar**.
    > - Seleccione **componentes individuales**.
    > - En **herramientas de código**, compruebe los **destinos de NuGet & las tareas de compilación**.

6. El archivo zip de la solución generada se encuentra en la carpeta `Solution\bin\debug`.
7. [Importe manualmente la solución en Common Data Service](https://docs.microsoft.com/powerapps/maker/common-data-service/import-update-export-solutions) mediante el portal web una vez que el archivo zip esté listo o consulte las secciones sobre [autenticación en su organización](import-custom-controls.md#authenticating-to-your-organization) e [implementación](import-custom-controls.md#deploying-code-components) para importar mediante los comandos de la CLI de PowerApps.

## <a name="adding-code-components-in-model-driven-apps"></a>Agregar componentes de código en aplicaciones controladas por modelos

Para agregar un componente de código como un componente de entrada lineal, siga los pasos mencionados en el tema [agregar componentes a campos y entidades](add-custom-controls-to-a-field-or-entity.md).

## <a name="adding-code-components-to-a-canvas-app"></a>Agregar componentes de código a una aplicación de lienzo

Para agregar los componentes de código a una aplicación de lienzo, siga los pasos descritos en el tema [agregar componentes de código a una aplicación de lienzo](component-framework-for-canvas-apps.md#add-components-to-a-canvas-app).

### <a name="see-also"></a>Vea también

[Descargar componentes de ejemplo](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[Actualización de los componentes del marco de componentes de PowerApps existentes](updating-existing-controls.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](overview.md)
