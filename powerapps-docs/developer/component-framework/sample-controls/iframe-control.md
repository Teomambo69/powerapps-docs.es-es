---
title: ' Componente IFRAME| Microsoft Docs'
description: Implementar componente IFRAME
ms.custom: ''
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.topic: article
ms.author: nabuthuk
---
# <a name="implementing-a-iframe-component"></a>Implementar un componente IFRAME

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

Este ejemplo describe cómo vincular un componente personalizado a distintos campos en el formulario y usar el valor de estos campos como propiedades de entrada al componente.  

> [!div class="mx-imgBorder"]
> ![Componente de IFRAME](../media/iframe-control.png "Componente de IFRAME")

## <a name="manifest"></a>Manifiesto

```xml
<?xml version="1.0" encoding="utf-8" ?>
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

## <a name="code"></a>Código

```TypeScript

import {IInputs, IOutputs} from "./generated/ManifestTypes";
export class TSIFrameControl implements ComponentFramework.StandardControl<IInputs, IOutputs> 
{
// Reference to Bing Map IFrame HTMLElement
private _bingMapIFrame: HTMLElement;
// Reference to the control container HTMLDivElement
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
public init(context: ComponentFramework.Context<IInputs>, notifyOutputChanged: () => void, state: ComponentFramework.Dictionary, container:HTMLDivElement)
{
    this._container = container;
    this._controlViewRendered = false;
}
/**
 * Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
 * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
 */
public updateView(context: ComponentFramework.Context<IInputs>)
{
    if (!this._controlViewRendered)
    {
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
private renderBingMapIFrame(): void
{
    this._bingMapIFrame = this.createIFrameElement();
    this._container.appendChild(this._bingMapIFrame);
}
/**
 * Updates the URL of the Bing Map IFrame to display the updated lat/long coordinates
 * @param latitude : latitude of center point of Bing map
 * @param longitude : longitude of center point of Bing map
 */
private updateBingMapURL(latitude:number, longitude:number): void
{
    // Bing Map API:
    // https://msdn.microsoft.com/library/dn217138.aspx
    // Provide bing map query string parameters to format and style map view
    let bingMapUrlPrefix = "https://www.bing.com/maps/embed?h=400&w=300&cp=";
    let bingMapUrlPostfix = "&lvl=12&typ=d&sty=o&src=SHELL&FORM=MBEDV8";
    // Build the entire URL with the user provided latitude and longitude
    let iFrameSrc:string = bingMapUrlPrefix + latitude + "~"+ longitude + bingMapUrlPostfix;
    // Update the IFrame to point to the updated URL
    this._bingMapIFrame.setAttribute("src", iFrameSrc);
}
/** 
 * Helper method to create an IFrame HTML Element
 */
private createIFrameElement(): HTMLElement
{
    let iFrameElement:HTMLElement = document.createElement("iframe")
    iFrameElement.setAttribute("class", "TS_SampleControl_IFrame");
    return iFrameElement
}
/** 
 * It is called by the framework prior to a control receiving new data. 
 * @returns an object based on nomenclature defined in manifest, expecting object[s] for property marked as “bound” or “output”
 */
public getOutputs(): IOutputs
{
    // no-op: method not leveraged by this example custom control
    return {};
}
/** 
 * Called when the control is to be removed from the DOM tree. Controls should use this call for cleanup.
 * i.e. canceling any pending remote calls, removing listeners, etc.
 */
public destroy()
{
    // no-op: method not leveraged by this example custom control
}
}
```

## <a name="resources"></a>Recursos

```css
.SampleNamespace\.TSIFrameControl .TS_SampleControl_IFrame
{
    width: 300px;
    height: 400px;
}
```

> [!NOTE]
> El marco de componentes de PowerApps aún no admite campos compuestos, por lo que no podrá vincular este componente a los campos de dirección de latitud y longitud predefinidos. Debe vincular el componente personalizado a otro campo de punto flotante.

Este componente de ejemplo genera un `IFRAME` que muestra `Bing Maps URL`. El componente está enlazado a dos campos de punto flotante en el formulario, que se pasan como parámetros al componente y se insertan en la `IFRAME URL` para actualizar el mapa de Bing a la latitud y la longitud de las entradas proporcionadas.  

Actualice el archivo de `Manifest` para incluir el enlace a dos campos adicionales en el formulario.  
Este cambio informa al marco de componentes de PowerApps de que estos campos enlazados deben pasarse al componente durante la inicialización y siempre que uno de los valores se actualice.
  
```xml

<property name="latitudeValue" display-name-key="Bing_Maps_Latitude_Value" description-key="latitude" of-type="FP" usage="bound" required="true" />  
<property name="longitudeValue" display-name-key="Bing_Maps_Longitude_Value" description-key="longitude" of-type="FP" usage="bound" required="true" />  
```

Las propiedades enlazadas adicionales pueden necesitarse o no. Esto se aplicará durante la configuración del componente cuando el componente se esté enlazado al formulario. Esto se puede configurar estableciendo el atributo `required` del nodo de la propiedad en el manifiesto del componente. Establezca el valor como falso si no desea exigir que la propiedad del componente esté enlazada a un campo. 
 
`ControlFramework.d.ts` debe actualizarse para agregar dos campos a la interfaz de `IInputs`. Este es el formato con el que el marco de componentes de PowerApps pasa los valores de campo. Agregar estos valores a la interfaz `IInputs` permite que el archivo TypeScript haga referencia a los valores y se compile correctamente.  

```TypeScript
    export interface IInputs 
    { latitudeValue: ControlFramework.PropertyTypes.NumberProperty;  
        longitudeValue: ControlFramework.PropertyTypes.NumberProperty;  
    }  
 ```

La representación inicial genera un elemento `IFRAME` y lo agrega al contenedor de controles. Este `IFRAME` se usa para mostrar el **Mapa de Bing**. La dirección URL del `IFRAME` se establece como la `Bing Map URL` e incluye los campos enlazados (latitudeValue y longitudeValue) en la dirección URL para centrar el mapa en la ubicación proporcionada. 

El método [updateView](../reference/control/updateview.md) se invoca siempre que uno de estos campos se actualiza en el formulario. Este método actualiza la dirección URL del IFRAME de **Mapa de Bing** para usar los nuevos valores de latitud y longitud pasados al componente. Para ver este componente en tiempo de ejecución, enlace el componente a un campo en el formulario como cualquier otro componente personalizado.

### <a name="related-topics"></a>Temas relacionados

[Descargar componentes de ejemplo](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[Referencia de esquema de manifiesto del marco de componentes de PowerApps](../manifest-schema-reference/index.md)<br />
[Referencia de la API de marco de componentes de PowerApps](../reference/index.md)<br />
[Descripción general de marco de componentes de PowerApps](../overview.md)
