---
title: getActivePath (referencia API de cliente) en aplicaciones basadas en modelo| Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4916df68-b2d4-4a0b-b341-eb9f7032bc20
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getactivepath-client-api-reference"></a>getActivePath (referencia de la API de cliente)



[!INCLUDE[./includes/getActivePath-description.md](./includes/getActivePath-description.md)]

La ruta activa representa fases generadas actualmente en el control de proceso según las reglas de bifurcación y datos actuales en el registro.

## <a name="syntax"></a>Sintaxis

`var stageCollection = formContext.data.process.getActivePath();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: colección. 

**Descripción**: Una colección de todas las fases completadas, la fase activa actualmente y el conjunto previsto de fases futuras basadas en condiciones satisfechas en la regla de bifurcación. Podría ser un subconjunto de las fases devueltas con **formContext.data.process**.[getActiveProcess](../activeprocess/getActiveProcess.md) porque solo incluirá las fases que representan una transición válida de la fase actual basada en bifurcación que se ha producido en el proceso.

## <a name="example"></a>Ejemplo

La función Sdk.formOnLoad utiliza el método **formContext.data.process.getActivePath** para recuperar una colección de fases. A continuación, el código de ejemplo usa el método [forEach](../../collections/forEach.md) de la colección para repetir cada fase. El código escribe a continuación propiedades clave de la fase en la consola mediante la función **Sdk.writeToConsole** definida en esta biblioteca. Seguidamente el código accede a una colección de pasos para cada fase mediante el método [getSteps](../stage/getSteps.md). Por último, el ejemplo usa el método [forEach](../../collections/forEach.md) de la colección de pasos para acceder a cada paso y escribe las propiedades clave del paso en la consola.

>[!NOTE]
>La función **Sdk.formOnLoad** de la biblioteca de JavaScript de ejemplo se debe establecer como el controlador de eventos **OnLoad** para un formulario y la casilla **pasar el contexto de ejecución como primer parámetro** debe estar seleccionada en el cuadro de diálogo **Propiedades del controlador**.<br/>Además, este ejemplo solamente muestra el uso de algunos de los métodos de la API **formContext.data.process**. No representa el uso de esta API para cumplir un requisito de negocio; solo se usa para demostrar cómo se puede acceder a los valores de propiedades clave en código.

```JavaScript
// A namespace defined for SDK sample code
// You should define a unique namespace for your libraries
var Sdk = window.Sdk || {};
(function () {

    // A function to log messages while debugging only
    this.writeToConsole = function (message) {
        if (typeof console != 'undefined')
        { console.log(message); }
    };

    // Code to run in the OnLoad event 
    this.formOnLoad = function (executionContext) {
        // Retrieve the formContext
        var formContext = executionContext.getFormContext();

        // Enumerate the stages and steps in the active path
        var activePathCollection = formContext.data.process.getActivePath();
        activePathCollection.forEach(function (stage, n) {
            Sdk.writeToConsole("Stage Index: " + n);
            Sdk.writeToConsole("Entity: " + stage.getEntityName());
            Sdk.writeToConsole("StageId: " + stage.getId());
            Sdk.writeToConsole("Status: " + stage.getStatus());
            var stageSteps = stage.getSteps();
            stageSteps.forEach(function (step, i) {
                Sdk.writeToConsole("    Step Name: " + step.getName());
                Sdk.writeToConsole("    Step Attribute: " + step.getAttribute());
                Sdk.writeToConsole("    Step Required: " + step.isRequired());
                Sdk.writeToConsole("    ---------------------------------------")
            })
            Sdk.writeToConsole("---------------------------------------")
        });
    };
}).call(Sdk);
```

Cuando el ejemplo se ejecuta en el explorador, puede usar las herramientas del desarrollador del explorador para ver el texto escrito en la consola. Por ejemplo, cuando este ejemplo se ejecuta en el formulario de entidad de oportunidad con el Proceso oportunidad de venta, se escribe lo siguiente en la consola:

```
Stage Index: 0
Entity: opportunity
StageId: 6b9ce798-221a-4260-90b2-2a95ed51a5bc
Status: active
    Step Name: Identify Contact
    Step Attribute: parentcontactid
    Step Required: false
    ---------------------------------------
    Step Name: Identify Account
    Step Attribute: parentaccountid
    Step Required: false
    ---------------------------------------
    Step Name: Purchase Timeframe
    Step Attribute: purchasetimeframe
    Step Required: false
    ---------------------------------------
    Step Name: Estimated Budget
    Step Attribute: budgetamount
    Step Required: false
    ---------------------------------------
    Step Name: Purchase Process
    Step Attribute: purchaseprocess
    Step Required: false
    ---------------------------------------
    Step Name: Identify Decision Maker
    Step Attribute: decisionmaker
    Step Required: false
    ---------------------------------------
    Step Name: Capture Summary
    Step Attribute: description
    Step Required: false
    ---------------------------------------
---------------------------------------
Stage Index: 1
Entity: opportunity
StageId: 650e06b4-789b-46c1-822b-0da76bedb1ed
Status: inactive
    Step Name: Customer Need
    Step Attribute: customerneed
    Step Required: false
    ---------------------------------------
    Step Name: Proposed Solution
    Step Attribute: proposedsolution
    Step Required: false
    ---------------------------------------
    Step Name: Identify Stakeholders
    Step Attribute: identifycustomercontacts
    Step Required: false
    ---------------------------------------
    Step Name: Identify Competitors
    Step Attribute: identifycompetitors
    Step Required: false
    ---------------------------------------
---------------------------------------
Stage Index: 2
Entity: opportunity
StageId: d3ca8878-8d7b-47b9-852d-fcd838790cfd
Status: inactive
    Step Name: Identify Sales Team
    Step Attribute: identifypursuitteam
    Step Required: false
    ---------------------------------------
    Step Name: Develop Proposal
    Step Attribute: developproposal
    Step Required: false
    ---------------------------------------
    Step Name: Complete Internal Review
    Step Attribute: completeinternalreview
    Step Required: false
    ---------------------------------------
    Step Name: Present Proposal
    Step Attribute: presentproposal
    Step Required: false
    ---------------------------------------
---------------------------------------
Stage Index: 3
Entity: opportunity
StageId: bb7e830a-61bd-441b-b1fd-6bb104ffa027
Status: inactive
    Step Name: Complete Final Proposal
    Step Attribute: completefinalproposal
    Step Required: false
    ---------------------------------------
    Step Name: Present Final Proposal
    Step Attribute: presentfinalproposal
    Step Required: false
    ---------------------------------------
    Step Name: Confirm Decision Date
    Step Attribute: finaldecisiondate
    Step Required: false
    ---------------------------------------
    Step Name: Send Thank You
    Step Attribute: sendthankyounote
    Step Required: false
    ---------------------------------------
    Step Name: File De-brief
    Step Attribute: filedebrief
    Step Required: false
    ---------------------------------------
---------------------------------------
```

### <a name="related-topics"></a>Temas relacionados

[formContext.data.process](../../formContext-data-process.md)
 


