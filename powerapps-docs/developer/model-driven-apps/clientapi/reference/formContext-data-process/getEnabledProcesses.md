---
title: getEnabledProcesses (referencia API de cliente) en aplicaciones basadas en modelo| Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 52f79803-2ce0-4ca7-8200-aec544545d62
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getenabledprocesses-client-api-reference"></a>getEnabledProcesses (referencia de la API de cliente)



[!INCLUDE[./includes/getEnabledProcesses-description.md](./includes/getEnabledProcesses-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.data.process.getEnabledProcesses(callbackFunction(enabledProcesses));`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|callbackFunction|Función|Sí|La característica de devolución de llamada debe aceptar un parámetro que contenga un objeto con las propiedades de diccionario donde el nombre de la propiedad sea el identificador del flujo de proceso de negocio y el valor de la propiedad sea el nombre del flujo de proceso de negocio.<br/><br/>Los procesos habilitados se filtran según los privilegios del usuario. La lista de procesos habilitados es la misma que un usuario puede ver en la interfaz de usuario si desea cambiar el proceso manualmente.|

## <a name="example"></a>Ejemplo

La función **Sdk.formOnLoad** en el ejemplo utiliza el método **formContext.data.process.getEnabledProcesses** para recuperar información asincrónicamente sobre los flujos de procesos de negocio que están habilitados para la entidad. El ejemplo pasa una función anónima como primer parámetro. Esta funcionalidad se ejecuta asincrónicamente cuando se devuelven los datos y los datos se pasan como parámetro a la función anónima.

La información del flujo de proceso de negocio habilitado se proporciona como un objeto de diccionario donde el identificador del proceso es el nombre de propiedad y el nombre del flujo de proceso de negocios es el valor de la propiedad. El código de ejemplo procesa esta información y establece los valores en una matriz de **Sdk.enabledProcesses** global a la que se puede acceder con lógica que se ejecute más adelante. El ejemplo también repite los valores que utiliza la matriz **Sdk.enabledProcesses** y usa la función **Sdk.writeToConsole** para escribir información sobre flujos de proceso de negocio recuperados en la consola.

>[!NOTE]
>La función **Sdk.formOnLoad** de la biblioteca de JavaScript de ejemplo se debe establecer como el controlador de eventos **OnLoad** para un formulario y la casilla **pasar el contexto de ejecución como primer parámetro** debe estar seleccionada en el cuadro de diálogo **Propiedades del controlador**.<br/>Además, este ejemplo solamente muestra el uso de algunos de los métodos de la API **formContext.data.process**. No representa el uso de esta API para cumplir un requisito de negocio; solo se usa para demostrar cómo se puede acceder a los valores de propiedades clave en código.

```JavaScript
//A namespace defined for SDK sample code
//You should define a unique namespace for your libraries
var Sdk = window.Sdk || {};
(function () {
    //A global variable to store information about enabled business processes after they are retrieved asynchronously
    this.enabledProcesses = [];

    // A function to log messages while debugging only
    this.writeToConsole = function (message) {
        if (typeof console != 'undefined')
        { console.log(message); }
    };

    // Code to run in the OnLoad event 
    this.formOnLoad = function (executionContext) {
        // Retrieve the formContext
        var formContext = executionContext.getFormContext();

        // Retrieve Enabled processes
        formContext.data.process.getEnabledProcesses(function (processes) {
            //Move processes to the global Sdk.enabledProcesses array;
            for (var processId in processes) {
                Sdk.enabledProcesses.push({ id: processId, name: processes[processId] })
            }
            Sdk.writeToConsole("Enabled business processes flows retrieved and added to Sdk.enabledProcesses array.");

            //Write the values of the Sdk.enabledProcesses array to the console
            if (Sdk.enabledProcesses.length < 0) {
                Sdk.writeToConsole("There are no enabled business process flows for this entity.");
            }
            else {
                Sdk.writeToConsole("These are the enabled business process flows for this entity:");
                for (var i = 0; i < Sdk.enabledProcesses.length; i++) {
                    var enabledProcess = Sdk.enabledProcesses[i];
                    Sdk.writeToConsole("id: " + enabledProcess.id + " name: " + enabledProcess.name)
                }
            }

            //Any code that depends on the Sdk.enabledProcesses array needs to be initiated here

        });
    };

}).call(Sdk);
```

Cuando ejecuta este ejemplo con las herramientas del desarrollador del explorador abiertas, lo siguiente es un ejemplo de salida escrita en la consola para una entidad con varios flujos de proceso de negocio habilitados.

```
Enabled business processes flows retrieved and added to Sdk.enabledProcesses array.
These are the enabled business process flows for this entity:
id: 7994be68-899e-4a40-8d18-f5c3b6940188 name: Sample Lead Process
id: 919e14d1-6489-4852-abd0-a63a6ecaac5d name: Lead to Opportunity Sales Process
```

### <a name="related-topics"></a>Temas relacionados

[setActiveProcessInstance](setActiveProcessInstance.md)

[formContext.data.process](../formContext-data-process.md)
 


