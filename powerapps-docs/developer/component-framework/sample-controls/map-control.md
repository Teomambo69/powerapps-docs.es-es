---
title: " Componente de mapa| Microsoft Docs"
description: Implementar el componente de mapa mediante Angular JS
ms.custom: ''
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: b5eeecdee0d16ed345549159a63f030cd9f11fff
ms.sourcegitcommit: 310dd3dc68ffebe6a416450836ac0ba988b84fb4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "3162049"
---
# <a name="implementing-map-component"></a>Implementar componente de mapa

Este componente de ejemplo cambia la experiencia de usuario de interactuar con campos de dirección del formulario. Además de los valores de texto de la dirección, este componente proporciona la capacidad de identificar visualmente una dirección específica en un mapa sin navegar a otra pestaña o pantalla. Puede descargar el componente de ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/component-framework/TS_MapControl).

> [!div class="mx-imgBorder"]
> ![Componente de asignación](../media/map-control.png "Componente de asignación")

## <a name="available-for"></a>Disponible para 

Aplicaciones basadas en modelos y aplicaciones de lienzo (vista previa pública) 

## <a name="manifest"></a>Manifiesto

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest>
    <control namespace="SampleNamespace" constructor="TSMapControl" version="1.0.0" display-name-key="TS_MapControl_Display_Key" description-key="TS_MapControl_Desc_Key" control-type="standard">
        <property name="controlValue" display-name-key="controlValue_Display_Key" description-key="controlValue_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" />
        <resources>
            <code path="index.ts" order="1" />
            <css path="css/TS_MapControl.css" order="1" />
        </resources>
    </control>
</manifest>
```

## <a name="code"></a>Código 

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
export class TSMapControl
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // HTML IFrame element that will be used to render the map
  private _iFrameElement: HTMLIFrameElement;
  // Power Apps component framework framework delegate which will be assigned to this object which would be called whenever an update happens.
  private _notifyOutputChanged: () => void;
  // reference to ComponentFramework Context object
  private _context: ComponentFramework.Context<IInputs>;
  // API Key used to activate and embed the maps automatically
  // NOTE: You can follow the documentation at https://developers.google.com/maps/documentation/embed/get-api-key to generate your own API Key
  private MAPS_API_KEY: string = "<Replace your Key here>";
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
    this._notifyOutputChanged = notifyOutputChanged;
    this._context = context;
    this._iFrameElement = document.createElement("iframe");
    this._iFrameElement.setAttribute("class", "mapHiddenStyle");
    this.renderMap(this.buildMapUrl(context.parameters.controlValue.formatted));
    container.appendChild(this._iFrameElement);
  }
  /**
   * Checks if the url is not null and sets the value to the iFrame source to be loaded inside it and then notifies the ComponentFramework that the output has changed
   * @param mapUrl : The url for the map that needs to be loaded inside the iFrame.
   */
  public renderMap(mapUrl: string) {
    if (mapUrl) {
      this._iFrameElement.setAttribute("src", mapUrl);
      this._iFrameElement.setAttribute("class", "mapVisibleStyle");
    } else {
      this._iFrameElement.setAttribute("class", "mapHiddenStyle");
    }
    this._notifyOutputChanged();
  }
  /**
   * Converts the string that is passed to a valid url that can be used to render the map for the location
   * @param addressString : any string that can be used to search for a location in maps
   * @returns the HTML encoded url that can be used to load the map if the addressString is non empty string
   */
  public buildMapUrl(addressString: string | undefined): string {
    if (addressString) {
      let url: string =
        "https://www.google.com/maps/embed/v1/place?key=" +
        this.MAPS_API_KEY +
        "&q=" +
        encodeURIComponent(addressString);
      return url;
    }
    return "";
  }
  /**
   * Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
   * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
   */
  public updateView(context: ComponentFramework.Context<IInputs>) {
    this._context = context;
    this.renderMap(this.buildMapUrl(context.parameters.controlValue.formatted));
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
  public destroy() {}
}
```

## <a name="resources"></a>Recursos

```css
.SampleNamespace\.TSMapControl .mapVisibleStyle {
  width: 640px;
  height: 420px;
  visibility: visible;
}
.SampleNamespace\.TSMapControl .mapHiddenStyle {
  visibility: hidden;
}
```

En el archivo de manifiesto, definimos la propiedad de tipo `Single line of Text`. La usamos para enlazarlo al campo de dirección del formulario.  

> [!NOTE]
> Puede usar cualquiera de las API de mapa que están disponibles en el mercado.En este ejemplo, vamos a mostrar cómo hacerlo con la API de Google Maps. Necesita crear una clave de API para que el componente tenga acceso a la API de Google Maps.Siga las instrucciones(https://developers.google.com/maps/documentation/embed/get-api-key para generar una).

Cree una `MAPS_API_KEY` de nombre de variable a la que se puede tener acceso en el contexto del componente.
La API de Google Maps permite generar solo los mapas en un `IFRAME`. Por lo tanto, debe crear un elemento `IFRAME` que vaya a generar el mapa mediante la dirección URL que generamos. De forma predeterminada, estamos configurando el mapa para que esté oculto y solo se muestre cuando el valor de dirección exista en el formulario.

`buildMapUrl` y `renderMap` (puede incluso combinarlos en uno) toma la cadena de la dirección y la inserta en la dirección URL del mapa codificando la cadena de dirección y después establece el elemento src del elemento IFRAME en la dirección URL respectivamente. Además, llame al método **notifyOutputChanged** para asegurarse de que notificamos al componente de que la representación ha cambiado. 
 
```TypeScript
 public renderMap(mapUrl: string) {
    if (mapUrl) {
      this._iFrameElement.setAttribute("src", mapUrl);
      this._iFrameElement.setAttribute("class", "mapVisibleStyle");
    } else {
      this._iFrameElement.setAttribute("class", "mapHiddenStyle");
    }
    this._notifyOutputChanged();
  }
```

Asegúrese de llamar a la función `renderMap` dentro de la función [updateView](../reference/control/updateview.md) para garantizar que el control se actualiza cada vez que se actualiza la vista. 

### <a name="related-topics"></a>Temas relacionados

[Descargar componentes de ejemplo](https://github.com/microsoft/PowerApps-Samples/tree/master/component-framework)<br/>
[¿Cómo usar los componentes de ejemplo?](../use-sample-components.md)<br/>
[Referencia de la API de Power Apps component framework](../reference/index.md)<br/>
[Referencia de esquema de manifiesto de Power Apps component framework](../manifest-schema-reference/index.md)