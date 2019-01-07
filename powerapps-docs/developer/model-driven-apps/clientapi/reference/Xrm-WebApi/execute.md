---
title: Xrm.WebApi.online.execute (referencia de API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 11/21/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: d4e92999-3b79-4783-8cac-f656fc5f7fda
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="xrmwebapionlineexecute-client-api-reference"></a>Xrm.WebApi.online.execute (referencia de la API de cliente)



[!INCLUDE[./includes/execute-description.md](./includes/execute-description.md)]

> [!NOTE]
> Este método solo es compatible para el modo con conexión ([Xrm.WebApi.online](online.md)).

## <a name="syntax"></a>Sintaxis

`Xrm.WebApi.online.execute(request).then(successCallback, errorCallback);`

## <a name="parameters"></a>Parámetros

<table style="width:100%">
<tr>
<th>Nombre</th>
<th>Escriba</th>
<th>Requerido</th>
<th>Descripción</th>
</tr>
<tr>
<td>solicitud</td>
<td>Objeto</td>
<td>Sí</td>
<td><p>Objeto que se pasará al extremo de la API web para ejecutar una acción, función o solicitud CRUD. El objeto muestra un método <b>getMetadata</b> que le permite definir los metadatos de la acción, la función o la solicitud CRUD que desea ejecutar. El método <b>getMetadata</b> tiene los siguientes parámetros:</p>
<ul>
<li><b>boundParameter</b>: cadena (opcional). Nombre de los parámetros asociados para que se ejecute la acción o función.
<ul><li>Especifique <code>undefined</code> si se está ejecutando una solicitud CRUD.</li>
<li>Especifique <code>null</code> si la acción o función que se va a ejecutar no depende de ninguna entidad.</li>
<li>Especifique <code>entity</code> si la acción o función que se va a ejecutar depende de una entidad. </li></ul>
<li><b>operationName</b>: (opcional). Cadena. Nombre de la acción, de la función o de uno de los valores siguientes si se está ejecutando una solicitud CRUD: "Create", "Retrieve", "RetrieveMultiple", "Update" o "Delete".</li>
<li><b>operationType</b>: (opcional). Número. Indica el tipo de operación que se está ejecutando. Especifique uno de los siguientes valores:
<br/><code>0: Action</code>
<br/><code>1: Function</code>
<br/><code>2: CRUD</code></li>
<li><b>parameterTypes</b>: objeto. Metadatos de los tipos de parámetro. El objeto tiene los siguientes atributos:
<ul>
<li><b>enumProperties</b>: objeto (opcional). Metadatos de los tipos de enumeración. El objeto tiene dos atributos de cadena: <b>name</b> y <b>value</b></li>
<li><b>structuralProperty</b>: número. Categoría del tipo de parámetro. Especifique uno de los siguientes valores:
<br/><code>0: Unknown</code>
<br/><code>1: PrimitiveType</code>
<br/><code>2: ComplexType</code>
<br/><code>3: EnumerationType</code>
<br/><code>4: Collection</code>
<br/><code>5: EntityType</code></li>
<li><b>typeName</b>: cadena. Nombre completo del tipo de parámetro.
</ul>
</li>
</ul>
</td>
</tr>
<tr>
<td>successCallback</td>
<td>Función</td>
<td>No</td>
<td><p>Función para llamar cuando la operación se ejecuta correctamente. Un objeto de respuesta con los siguientes atributos se pasa a la función:</p>
<ul>
<li><b>body</b>: (opcional). Objeto. Cuerpo de la respuesta.</li>
<li><b>headers</b>: objeto. Encabezados de la respuesta.</li>
<li><b>ok</b>: booleano. Indica si la solicitud se ha realizado correctamente.</li>
<li><b>status</b>: número. Valor numérico en el código de estado de la respuesta. Por ejemplo: <b>200</b></li>
<li><b>statusText</b>: cadena. Descripción del código del estado de la respuesta. Por ejemplo, <b>OK</b></li>
<li><b>type</b>: cadena. Tipo de respuesta. Los valores son: la cadena vacía (predeterminada), "arraybuffer", "blob", "document", "json" y "text".</b></li>
<li><b>url</b>: cadena. Dirección URL de la solicitud de la acción, de la función o de la solicitud CRUD que se envió al extremo de la API web.</b></li>
</ul>
</td>
</tr>
<tr>
<td>errorCallback</td>
<td>Función</td>
<td>No</td>
<td>Una función para llamar cuando la operación tiene error.</td>
</tr>
</table>

## <a name="return-value"></a>Valor devuelto

En caso de éxito, devuelve un objeto promesa que contiene los atributos especificados anteriormente en la descripción de la función **successCallback**.

## <a name="examples"></a>Ejemplos

### <a name="execute-an-action"></a>Ejecutar una acción

El siguiente ejemplo muestra cómo ejecutar la acción <xref:Microsoft.Dynamics.CRM.WinOpportunity>. El objeto de la solicitud se crea con la definición de la acción siguiente: [Acciones sin enlazar](../../../../common-data-service/webapi/use-web-api-actions.md#unbound-actions)
```JavaScript
var Sdk = window.Sdk || {};
/**
 * Request to win an opportunity
 * @param {Object} opportunityClose - The opportunity close activity associated with this state change.
 * @param {number} status - Status of the opportunity.
 */
Sdk.WinOpportunityRequest = function (opportunityClose, status) {
    this.OpportunityClose = opportunityClose;
    this.Status = status;

    this.getMetadata = function () {
        return {
            boundParameter: null,
            parameterTypes: {
                "OpportunityClose": {
                    "typeName": "mscrm.opportunityclose",
                    "structuralProperty": 5 // Entity Type
                },
                "Status": {
                    "typeName": "Edm.Int32",
                    "structuralProperty": 1 // Primitive Type
                }
            },
            operationType: 0, // This is an action. Use '1' for functions and '2' for CRUD
            operationName: "WinOpportunity",
        };
    };
};


var opportunityClose = {
    "opportunityid@odata.bind": "/opportunities(c60e0283-5bf2-e311-945f-6c3be5a8dd64)",
    "description": "Product and maintainance for 2018",
    "subject": "Contract for 2018"
}

// Construct a request object from the metadata
var winOpportunityRequest = new Sdk.WinOpportunityRequest(opportunityClose, 3);

// Use the request object to execute the function
Xrm.WebApi.online.execute(winOpportunityRequest).then(
    function (result) {
        if (result.ok) {
            console.log("Status: %s %s", result.status, result.statusText);
            // perform other operations as required;
        }
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```


### <a name="execute-a-function"></a>Ejecutar una función

El siguiente ejemplo muestra cómo ejecutar la función <xref:Microsoft.Dynamics.CRM.WhoAmI>:

```JavaScript
var Sdk = window.Sdk || {};
/**
 * Request to execute WhoAmI function
 */
Sdk.WhoAmIRequest = function () { };
Sdk.WhoAmIRequest.prototype.getMetadata = function () {
    return {
        boundParameter: null,
        parameterTypes: {},
        operationType: 1, // This is a function. Use '0' for actions and '2' for CRUD
        operationName: "WhoAmI",
    };
};

// Construct a request object from the metadata
var whoAmIRequest = new Sdk.WhoAmIRequest();

// Use the request object to execute the function
Xrm.WebApi.online.execute(whoAmIRequest).then(
    function (result) {
        if (result.ok) {
            console.log("Status: %s %s", result.status, result.statusText);
            result.json().then(
                function (response) {
                    console.log("User Id: %s", response.UserId);
                    // perform other operations as required;
                });
        }
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```

 
### <a name="related-topics"></a>Temas relacionados


[Xrm.WebApi](../xrm-webapi.md)




