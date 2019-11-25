---
title: " Componente Flip| Microsoft Docs"
description: Implementar el componente Flip mediante Angular JS
ms.custom: ''
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 90d74124e21fe74a96ca31830508f3bbb99e17b9
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749466"
---
# <a name="implementing-flip-component"></a>Implementar componente Flip

En este ejemplo se muestra cómo usar las bibliotecas de terceros para crear componentes en PowerApps component framework.  El componente de ejemplo Flip se implementa basándose en angular.js, angular-ui, angular-animate, angular-sanitize, bootstrap. El código puede no revelar las prácticas recomendadas para las bibliotecas de terceros mencioinadas.

> [!div class="mx-imgBorder"]
> ![Flip angular](../media/angular-flip.png "Flip angular")

## <a name="available-for"></a>Disponible para 

Aplicaciones basadas en modelo y aplicaciones de lienzo (vista previa piloto) 

## <a name="manifest"></a>Manifiesto

```XML
<?xml version="1.0" encoding="utf-8"?>
<manifest>
    <control namespace="SampleNamespace" constructor="JSAngularJSFlipControl" version="1.0.0" display-name-key="JS_AngularJSFlipControl_Display_Key" description-key="JS_AngularJSFlipControl_Desc_Key" control-type="standard">
        <property name="flipModel" display-name-key="flipModel_Display_Key" description-key="flipModel_Desc_Key" of-type="TwoOptions" usage="bound" required="true" />
        <resources>
            <code path="index.ts" order="5" />
            <css path="css/bootstrap-associated.css" order="1" />
        </resources>
    </control>
</manifest>
```

## <a name="overview"></a>información general

Este ejemplo proporciona ejemplos de cómo agregar dependencias para bibliotecas de terceros, mostrando cómo realizar de enlace de datos entre PowerApps component framework, el modelo de componentes y el modelo de datos internos a terceros de forma bidireccional.

El ejemplo de componente Flip consta de una etiqueta y un botón. Al hacer clic en el botón, cambia el texto de la etiqueta.

- Cuando el componente se carga, la etiqueta muestra el texto basado en el valor del atributo de vinculación. Los `context.parameters.[property_name].attributes` contienen los metadatos asociados.
- Para los campos TwoOptions, `context.parameters.[property_name].Options` incluirá la opción de valores Verdadero y Falso. 
- Al hacer clic en el botón Flip, la etiqueta actualizará el valor mediante el método **notifyOutputEvents**, el método [getOutputs](../reference/control/getoutputs.md) se llamará de forma asincrónica y pasará a PowerApps component framework,. 
- ClientAPI actualzia el valor del atributo de vínculo y el valor actualizado pasa a la etiqueta de componente. También puede usar `ClientAPI` para actualizar un valor de atributo para desencadenar el método [updateView](../reference/control/updateview.md) del control. El componente entronces actualiza el modelo de terceros y la etiqueta se actualiza.


## <a name="code"></a>Código

```TypeScript

import { IInputs, IOutputs } from "./generated/ManifestTypes";
import * as angular from "angular";
export class JSAngularJSFlipControl
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // Element id of the ng-app div. Type: string
  private _appDivId: string;
  // ng-app app id. Type: string
  private _appId: string;
  // ng-controller. Type: string
  private _controllerId: string;
  // PCF framework delegate which will be assigned to this object which would be called whenever an update happens. Type: function
  private _notifyOutputChanged: () => void;
  // Model of the bind field. Type: Boolean
  private _currentValue: boolean;
  // Option Label Text when Option is True. The Text is from attribute customization. Type: string
  private _optionTrueLabel: string;
  // Option Label Text when Option is False. The Text is from attribute customization. Type: string
  private _optionFalseLabel: string;
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
    // We need a random integer from 1-100, so that for a form of multiple fields bind to same attribute, we could differentiate
    let randomInt: number = Math.floor(Math.floor(100) * Math.random());
    let _this = this;
    this._appDivId = this.createUniqueId(
      context,
      "angularflip_controlid",
      randomInt
    );
    this._appId = this.createUniqueId(
      context,
      "JSAngularJSFlipControl",
      randomInt
    );
    this._controllerId = this.createUniqueId(
      context,
      "powerApps.angularui.demo",
      randomInt
    );
    this._notifyOutputChanged = notifyOutputChanged;
    // Assign Model the value of the bind attribute
    this._currentValue = context.parameters.flipModel.raw;
    // Initialize the True/False Label texts from the attribute metadata
    this.initializeOptionsLabel(context);
    // Create HTML structure for the control
    let appDiv: HTMLDivElement = document.createElement("div");
    appDiv.setAttribute("id", this._appDivId);
    appDiv.setAttribute("ng-controller", this._appId);
    appDiv.setAttribute("ng-app", this._controllerId);
    // Below sample html are from Angular-UI single toggle sample code
    // https://angular-ui.github.io/bootstrap/
    appDiv.innerHTML =
      "<pre>{{labelModel}}</pre><button type='button' class='btn btn-primary' ng-model='flipButtonModel' uib-btn-checkbox btn-checkbox-true='1' btn-checkbox-false='0'>Flip</button>";
    // Container appends the HTML structure
    container.appendChild(appDiv);
    // Angular code. Angular module/controller initialization.
    angular.module(this._controllerId, [
      "ngAnimate",
      "ngSanitize",
      "ui.bootstrap"
    ]);
    angular.module(this._controllerId).controller(this._appId, $scope => {
      // Intialize 'labelModel'. Assign initial option text to the Angular $scope labelModel. It will be revealed in '<pre>{{labelModel}}</pre>'
      $scope.labelModel = _this._currentValue
        ? _this._optionTrueLabel
        : _this._optionFalseLabel;
      // Intialize 'flipButtonModel'. Assign bind attribute value to Angular $scope flipButtonModel. The Flip button also bind to this 'flipButtonModel', so when we click, it will flip
      $scope.flipButtonModel = _this._currentValue ? 1 : 0;
      // Watch the click of the flip button
      $scope.$watchCollection("flipButtonModel", () => {
        // Update the label text when Flip Button clicks
        if ($scope.flipButtonModel) {
          $scope.labelModel = _this._optionTrueLabel;
        } else {
          $scope.labelModel = _this._optionFalseLabel;
        }
        // Call updateOutputIfNeeded and inform PCF framework that bind attribute value need update
        _this.updateOutputIfNeeded($scope.flipButtonModel);
      });
    });
    // Angular code. Create an App based on the new appDivId
    angular.element(document).ready(() => {
      angular.bootstrap(document.getElementById(_this._appDivId)!, [
        _this._controllerId
      ]);
    });
  }
  /**
   * Get UniqueId so as to avoid id conflict between multiple fields bind to same attribute
   * @param context The "Input Properties" containing the parameters, control metadata and interface functions.
   * @param passInString input string as suffix
   * @param randomInt random integer
   * @returns a string of uniqueId includes attribute logicalname + passIn specialized string + random Integer
   */
  private createUniqueId(
    context: ComponentFramework.Context<IInputs>,
    passInString: string,
    randomInt: number
  ): string {
    return (
      context.parameters!.flipModel.attributes!.LogicalName +
      "-" +
      passInString +
      randomInt
    );
  }
  /**
   * Initialize Options Label to use the attribute label from Metadata
   * @param context The "Input Properties" containing the parameters, control metadata and interface functions.
   */
  private initializeOptionsLabel(
    context: ComponentFramework.Context<IInputs>
  ): void {
    var _this = this;
    // Get option label texts from metadata
    var optionsMetadata = context.parameters.flipModel.attributes!.Options;
    optionsMetadata.forEach((option: any) => {
      if (option.Value) {
        _this._optionTrueLabel = option.Label;
      } else {
        _this._optionFalseLabel = option.Label;
      }
    });
  }
  /**
   * Update Angular 'flipButtonModel' if needed
   * @param newValue new value
   */
  private updateFlipButtonModelIfNeeded(newValue: boolean): void {
    if (
      (newValue && !this._currentValue) ||
      (!newValue && this._currentValue)
    ) {
      this._currentValue = newValue;
      // Angular Code. Update the 'flipButtonModel' value
      var $scope = angular
        .element(document.getElementById(this._appDivId)!)
        .scope();
      $scope.$apply(($scope: any) => {
        // 'flipButtonModel' value is either 1 or 0
        $scope.flipButtonModel = newValue ? 1 : 0;
      });
    }
  }
  /**
   * Update value in PowerApps component framework
   * @param newValue new value
   */
  private updateOutputIfNeeded(newValue: boolean): void {
    if (
      (newValue && !this._currentValue) ||
      (!newValue && this._currentValue)
    ) {
      this._currentValue = newValue ? true : false;
      this._notifyOutputChanged();
    }
  }
  /**
   * Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
   * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
   */
  public updateView(context: ComponentFramework.Context<IInputs>): void {
    // An attribute value from Control Framework could be updated even after init cycle, clientAPI, post Save response can update the attribute value and the Flip control should reveal the new value.
    this.updateFlipButtonModelIfNeeded(context.parameters.flipModel.raw);
  }
  /**
   * It is called by the framework prior to a control receiving new data.
   * @returns an object based on nomenclature defined in manifest, expecting object[s] for property marked as “bound” or “output”
   */
  public getOutputs(): IOutputs {
    var returnValue = this._currentValue;
    return { flipModel: returnValue };
  }
  /**
   * Called when the control is to be removed from the DOM tree. Controls should use this call for cleanup.
   * i.e. canceling any pending remote calls, removing listeners, etc.
   */
  public destroy(): void {
    // Add code to cleanup control if necessary
  }
}
```

### <a name="resources"></a>Recursos

```css
.SampleNamespace\.JSAngularJSFlipControl pre {
  display: block;
  padding: 9.5px;
  margin: 0 0 10px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #333;
  word-break: break-all;
  word-wrap: break-word;
  background-color: #f5f5f5;
  border: 1px solid #ccc;
  border-radius: 4px;
}
.SampleNamespace\.JSAngularJSFlipControl pre {
  font-family: Menlo, Monaco, Consolas, "Courier New", monospace;
}
.SampleNamespace\.JSAngularJSFlipControl pre {
  overflow: auto;
}
.SampleNamespace\.JSAngularJSFlipControl .btn-primary {
  color: #fff;
  background-color: #337ab7;
  border-color: #2e6da4;
}
.SampleNamespace\.JSAngularJSFlipControl .btn-primary.focus,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary:focus {
  color: #fff;
  background-color: #286090;
  border-color: #122b40;
}
.SampleNamespace\.JSAngularJSFlipControl .btn-primary:hover {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.SampleNamespace\.JSAngularJSFlipControl .btn-primary.active,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary:active,
.open > .dropdown-toggle.btn-primary {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.SampleNamespace\.JSAngularJSFlipControl .btn-primary.active.focus,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary.active:focus,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary.active:hover,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary:active.focus,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary:active:focus,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary:active:hover,
.open > .dropdown-toggle.btn-primary.focus,
.open > .dropdown-toggle.btn-primary:focus,
.open > .dropdown-toggle.btn-primary:hover {
  color: #fff;
  background-color: #204d74;
  border-color: #122b40;
}
.SampleNamespace\.JSAngularJSFlipControl .btn-primary.active,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary:active,
.open > .dropdown-toggle.btn-primary {
  background-image: none;
}
.SampleNamespace\.JSAngularJSFlipControl .btn-primary.disabled.focus,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary.disabled:focus,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary.disabled:hover,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary[disabled].focus,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary[disabled]:focus,
.SampleNamespace\.JSAngularJSFlipControl .btn-primary[disabled]:hover,
fieldset[disabled].btn-primary.focus,
fieldset[disabled].btn-primary:focus,
fieldset[disabled].btn-primary:hover {
  background-color: #337ab7;
  border-color: #2e6da4;
}
.SampleNamespace\.JSAngularJSFlipControl .btn-primary.badge {
  color: #337ab7;
  background-color: #fff;
}
.SampleNamespace\.JSAngularJSFlipControl .btn {
  display: inline-block;
  padding: 6px 12px;
  margin-bottom: 0;
  font-size: 14px;
  font-weight: 400;
  line-height: 1.42857143;
  text-align: center;
  white-space: nowrap;
  vertical-align: middle;
  -ms-touch-action: manipulation;
  touch-action: manipulation;
  cursor: pointer;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  background-image: none;
  border: 1px solid transparent;
  border-radius: 4px;
}

```

### <a name="related-topics"></a>Temas relacionados

[Referencia de esquema de manifiesto de PowerApps component framework](../manifest-schema-reference/index.md)<br />
[Referencia de la API de PowerApps component framework](../reference/index.md)<br />
[Información general sobre PowerApps component framework](../overview.md)
