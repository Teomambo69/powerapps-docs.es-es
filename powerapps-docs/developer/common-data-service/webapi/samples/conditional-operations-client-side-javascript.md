---
title: Ejemplo de operaciones condicionales de API web (JavaScript de lado de cliente) (Common Data Service) | Microsoft Docs
description: Este ejemplo muestra cómo realizar operaciones condicionales mediante la API web de Common Data Service y JavaScript de lado de cliente.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
author: brandonsimons
ms.assetid: 7f097d9f-8fe7-428a-9ef7-ca79ec501d81
caps.latest.revision: 23
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-api-conditional-operations-sample-client-side-javascript"></a>Ejemplo de operaciones condicionales de la API web (JavaScript del lado del cliente)

Este ejemplo muestra cómo realizar operaciones condicionales mediante la API web de Common Data Service utilizando JavaScript de lado de cliente.  
  
> [!NOTE]
>  Este ejemplo implementa las operaciones detalladas en el [ejemplo de operaciones condicionales de la API web](../web-api-conditional-operations-sample.md) y utiliza las construcciones comunes del lado cliente de JavaScript que se describen en [ejemplos de API web (JavaScript del lado cliente)](../web-api-samples-client-side-javascript.md).  

<a name="bkmk_prerequisites"></a>
 
## <a name="prerequisites"></a>Requisitos previos

 Para ejecutar este ejemplo, se requiere lo siguiente:  
  
-   Obtenga acceso a Common Data Service online versión 8.0 o superior.  
  
-   Una cuenta de usuario con privilegios para importar soluciones y realizar operaciones CRUD, normalmente un rol de seguridad de administrador o personalizador del sistema.  
  
<a name="bkmk_runsample"></a>
 
## <a name="run-this-sample"></a>Ejecute este ejemplo

Para ejecutar este ejemplo, vaya a [Microsoft CRM API web ejemplo de operaciones condicionales (JavaScript del lado cliente)](http://go.microsoft.com/fwlink/p/?LinkId=824046) y descargue el archivo de ejemplo Microsoft CRM ejemplo de operaciones condicionales de la API web (JavaScript del lado cliente).zip. Extraiga el contenido y busque la solución administrada WebAPIConditionalOperations_1_0_0_0_managed.zip. Importe la solución administrada en la organización de Common Data Service y vea la página de configuración de la solución para ejecutar el ejemplo. Para obtener instrucciones sobre cómo importar la solución de ejemplo, consulte [ejemplos de API Web (JavaScript del lado cliente)](../web-api-samples-client-side-javascript.md).  
  
<a name="bkmk_sampleCode"></a>

## <a name="code-sample"></a>Ejemplo de código

 Este ejemplo incluye dos recursos web:  
  
-   [WebAPIConditionalOperations.html](#bkmk_WebAPIConditionalOperations)  
  
-   [WebAPIConditionalOperations.js](#bkmk_WebAPIConditionalOperationsJS)  
  
<a name="bkmk_WebAPIConditionalOperations"></a>
 
### <a name="webapiconditionaloperationshtml"></a>WebAPIConditionalOperations.html

 El recurso web WebAPIConditionalOperations.html proporciona el contexto en el que el código JavaScript se ejecutará.  
  
```html  
<!DOCTYPE html>  
<html>  
<head>  
 <title>Microsoft CRM Web API Conditional Operations Example</title>  
 <meta charset="utf-8" />  
 <script src="../ClientGlobalContext.js.aspx" type="text/javascript"></script>  
 <script src="scripts/es6promise.js"></script>  
 <script src="scripts/WebAPIConditionalOperations.js"></script>  
  
 <style type="text/css">  
  body {  
   font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;  
  }  
 </style>  
</head>  
<body>  
 <h1>Microsoft CRM Web API  Conditional Operations Example</h1>  
 <p>This page demonstrates the CRM Web API's Conditional Operations using JavaScript.</p>  
  
 <h2>Instructions</h2>  
 <p>  
  Choose your preferences and run the JavaScript code.  
  Use your browser's developer tools to view the output written to the console (e.g.: in IE11 or Microsoft Edge,   
  press F12 to load the Developer Tools).  
 </p>  
 <form id="preferences">  
  <p>This sample deletes the single record it creates.</p>  
  <input type="button" name="start_samples" value="Start Sample" onclick="Sdk.startSample()" />  
 </form>  
</body>  
</html>  
  
```  
  
<a name="bkmk_WebAPIConditionalOperationsJS"></a>

### <a name="webapiconditionaloperationsjs"></a>WebAPIConditionalOperations.js

El recurso web WebAPIConditionalOperations.js es la biblioteca JavaScript que define las operaciones que este ejemplo realiza.  
  
```javascript  
"use strict";  
var Sdk = window.Sdk || {};  
/**  
 * @function getClientUrl   
 * @description Get the client URL.  
 * @return {string} The client URL.  
 */  
Sdk.getClientUrl = function () {  
 var context;  
 // GetGlobalContext defined by including reference to   
 // ClientGlobalContext.js.aspx in the HTML page.  
 if (typeof GetGlobalContext != "undefined")  
 { context = GetGlobalContext(); }  
 else  
 {  
  if (typeof Xrm != "undefined") {  
   // Xrm.Page.context defined within the Xrm.Page object model for form scripts.  
   context = Xrm.Page.context;  
  }  
  else { throw new Error("Context is not available."); }  
 }  
 return context.getClientUrl();  
}  
  
// Global variables.  
var clientUrl = Sdk.getClientUrl();     // e.g.: https://org.crm.dynamics.com  
var webAPIPath = "/api/data/v8.1";      // Path to the web API.  
var account1Uri;                        // e.g.: Contoso Ltd (sample)  
var initialAcctETagVal;                 // The initial ETag value of the account created     
var updatedAcctETagVal;                 // The ETag value of the account after it is updated   
  
// Entity properties to select in a request.  
var contactProperties = ["fullname", "jobtitle", "annualincome"];  
var accountProperties = ["name"];  
var taskProperties = ["subject", "description"];  
  
/**  
 * @function request  
 * @description Generic helper function to handle basic XMLHttpRequest calls.  
 * @param {string} action - The request action. String is case-sensitive.  
 * @param {string} uri - An absolute or relative URI. Relative URI starts with a "/".  
 * @param {object} data - An object representing an entity. Required for create and update actions.  
 * @param {object} addHeader - An object with header and value properties to add to the request  
 * @returns {Promise} - A Promise that returns either the request object or an error object.  
 */  
Sdk.request = function (action, uri, data, addHeader) {  
 if (!RegExp(action, "g").test("POST PATCH PUT GET DELETE")) { // Expected action verbs.  
  throw new Error("Sdk.request: action parameter must be one of the following: " +  
      "POST, PATCH, PUT, GET, or DELETE.");  
 }  
 if (!typeof uri === "string") {  
  throw new Error("Sdk.request: uri parameter must be a string.");  
 }  
 if ((RegExp(action, "g").test("POST PATCH PUT")) && (!data)) {  
  throw new Error("Sdk.request: data parameter must not be null for operations that create or modify data.");  
 }  
 if (addHeader) {  
  if (typeof addHeader.header != "string" || typeof addHeader.value != "string") {  
   throw new Error("Sdk.request: addHeader parameter must have header and value properties that are strings.");  
  }  
 }  
  
 // Construct a fully qualified URI if a relative URI is passed in.  
 if (uri.charAt(0) === "/") {  
  uri = clientUrl + webAPIPath + uri;  
 }  
  
 return new Promise(function (resolve, reject) {  
  var request = new XMLHttpRequest();  
  request.open(action, encodeURI(uri), true);  
  request.setRequestHeader("OData-MaxVersion", "4.0");  
  request.setRequestHeader("OData-Version", "4.0");  
  request.setRequestHeader("Accept", "application/json");  
  request.setRequestHeader("Content-Type", "application/json; charset=utf-8");  
  if (addHeader) {  
   request.setRequestHeader(addHeader.header, addHeader.value);  
  }  
  request.onreadystatechange = function () {  
   if (this.readyState === 4) {  
    request.onreadystatechange = null;  
    switch (this.status) {  
     case 200: // Success with content returned in response body.  
     case 204: // Success with no content returned in response body.  
     case 304: // Success with Not Modified.  
      resolve(this);  
      break;  
     default: // All other statuses are error cases.  
      var error;  
      try {  
       error = JSON.parse(request.response).error;  
      } catch (e) {  
       error = new Error("Unexpected Error");  
      }  
      reject(error);  
      break;  
    }  
   }  
  };  
  request.send(JSON.stringify(data));  
 });  
};  
  
/**  
 * @function startSample  
 * @description Runs the sample.   
 * This sample demonstrates conditional operations using CRM Web API.   
 * Results are sent to the debugger's console window.  
 */  
Sdk.startSample = function () {  
 // Initializing...  
 console.log("-- Sample started --");  
  
 // Create the CRM account instance.  
 var account = {  
  name: "Contoso, Ltd",  
  telephone1: "555-0000",// Phone number value will increment with each update attempt.  
  revenue: 5000000,  
  description: "Parent company of Contoso Pharmaceuticals, etc."  
 };  
  
 var uri = "/accounts"; // A relative URi to the account entity.  
 Sdk.request("POST", uri, account)   
 .then( function (request) {  
  console.log("Account entity created.");  
  // Assign the Uri to the created account to a global variable.  
  account1Uri = request.getResponseHeader("OData-EntityId");  
  
  // Retrieve the created account entity.  
  return Sdk.request("GET", account1Uri + "?$select=name,revenue,telephone1,description");  
 })  
 .then( function (request) {  
  // Show the current entity properties.  
  var account = JSON.parse(request.response);  
  console.log(JSON.stringify(account, null, 2));  
  
  initialAcctETagVal = account["@odata.etag"]; // Save the current ETag value.  
  
  // Conditional Get START.  
  // Attempt to retrieve using conditional GET with current ETag value.  
  // Expecting nothing in the response because entity was not modified.  
  console.log("-- Conditional GET section started --");  
  var ifNoneMatchETag = { header: "If-None-Match", value: initialAcctETagVal };  
  return Sdk.request("GET", account1Uri + "?$select=name,revenue,telephone1,description", null, ifNoneMatchETag);  
 })  
 .then( function (request) {  
  console.log("Instance retrieved using ETag: %s", initialAcctETagVal);  
  if (request.status == 304) {  
   //Expected:  
   console.log("\tEntity was not modified so nothing was returned.")  
   console.log(request.response); //Nothing  
  }  
  else {  
   //Not Expected:  
   console.log(JSON.stringify(JSON.parse(request.response), null, 2));  
  }  
  
  // Modify the account instance by updating telephone1.  
  // This request operation will also update the ETag value.  
  return Sdk.request("PUT", account1Uri + "/telephone1", { value: "555-0001" })  
 } )  
 .then(  function (request) {  
   console.log("Account telephone number updated.");  
  
   // Re-attempt conditional GET with original ETag value.  
   var ifNoneMatchETag = { header: "If-None-Match", value: initialAcctETagVal };  
   return Sdk.request("GET", account1Uri + "?$select=name,revenue,telephone1,description", null, ifNoneMatchETag);  
  }  )  
  .then(  function (request) {  
   if (request.status == 200) {  
    // Expected.  
    console.log("Instance retrieved using ETag: %s", initialAcctETagVal);  
    var account = JSON.parse(request.response);  
    updatedAcctETagVal = account["@odata.etag"]; //Capture updated ETag.  
    console.log(JSON.stringify(account, null, 2));  
   }  
   else {  
    // Not Expected.  
    console.log("Unexpected status: %s", request.status)  
   }  
   // Conditional Get END.  
  
   // Optimistic concurrency on delete and update START.  
   console.log("-- Optimistic concurrency section started --");  
   // Attempt to delete original account (only if matches original ETag value).  
   var ifMatchETag = { header: "If-Match", value: initialAcctETagVal };  
   return Sdk.request("DELETE", account1Uri, null, ifMatchETag);  
  }  )  
  .then( function (request) {  
   // Success not expected.  
   console.log("Unexpected status: %s", request.status)  
  },  
  // Catch error.  
  function (error) {  
   // DELETE: Precondition failed error expected.  
   console.log("Expected Error: %s", error.message);  
   console.log("\tAccount not deleted using ETag '%s', status code: '%s'.", initialAcctETagVal, 412)  
  
   // Attempt to update account (if matches original ETag value).  
   var accountUpdate = {  
    telephone1: "555-0002",  
    revenue: 6000000  
   };  
   var ifMatchETag = { header: "If-Match", value: initialAcctETagVal };  
   return Sdk.request("PATCH", account1Uri, accountUpdate, ifMatchETag);  
  })  
  .then( function (request) {  
   // Success not expected.  
   console.log("Unexpected status: %s", request.status);  
  },  
  // Catch error.  
  function (error) {  
   // UPDATE: Precondition failed error expected.  
   console.log("Expected Error: %s", error.message);  
   console.log("\tAccount not updated using ETag '%s', status code: '%s'.", initialAcctETagVal, 412)  
  
   // Re-attempt update if matches current ETag value.  
   var accountUpdate = {  
    telephone1: "555-0003",  
    revenue: 6000000  
   };  
   var ifMatchETag = { header: "If-Match", value: updatedAcctETagVal };  
   return Sdk.request("PATCH", account1Uri, accountUpdate, ifMatchETag);  
  }  )  
  .then( function (request) {  
   if (request.status == 204) //No Content  
   {  
    // Expected.  
    console.log("Account successfully updated using ETag '%s', status code: '%s'.",  
     updatedAcctETagVal,  
     request.status)  
   }  
   else {  
    // Not Expected.  
    console.log("Unexpected status: %s", request.status)  
   }  
   // Retrieve and output current account state.  
   return Sdk.request("GET", account1Uri + "?$select=name,revenue,telephone1,description");  
  }  )  
  .then( function (request) {  
   var account = JSON.parse(request.response);  
   updatedAcctETagVal = account["@odata.etag"]; // Capture updated ETag.  
   console.log(JSON.stringify(account, null, 2));  
   // Optimistic concurrency on delete and update END.  
  
   // Controlling upsert operations START.  
   console.log("-- Controlling upsert operations section started --");  
  
   // Attempt to insert (without update) some properties for this account.  
   var accountUpsert = {  
    telephone1: "555-0004",  
    revenue: 7500000  
   };  
   var ifNoneMatchResource = { header: "If-None-Match", value: "*" };  
   return Sdk.request("PATCH", account1Uri, accountUpsert, ifNoneMatchResource);  
  }  )  
  .then( function (request) {  
   // Success not expected.  
   console.log("Unexpected status: %s", request.status);  
  },  
  // Catch error.  
  function (error) {  
   // Precondition failed error expected.  
   console.log("Expected Error: %s", error.message);  
   console.log("\tAccount not updated using ETag '%s', status code: '%s'.", initialAcctETagVal, 412)  
  
   // Attempt to perform same update without creation.   
   var accountUpsert = {  
    telephone1: "555-0005",  
    revenue: 7500000  
   };  
   // Perform operation only if matching resource exists.   
   var ifMatchResource = { header: "If-Match", value: "*" };  
   return Sdk.request("PATCH", account1Uri, accountUpsert, ifMatchResource);  
  } )  
  .then( function (request) {  
   if (request.status == 204)  // No Content.  
   {  
    // Expected.  
    console.log("Account updated using If-Match '*'")  
   }  
   else {  
    // Not Expected.  
    console.log("Unexpected status: %s", request.status)  
   }  
  
   // Retrieve and output current account state.  
   return Sdk.request("GET", account1Uri + "?$select=name,revenue,telephone1,description");  
  })  
  .then(  function (request) {  
   var account = JSON.parse(request.response);  
   updatedAcctETagVal = account["@odata.etag"]; // Capture updated ETag.  
   console.log(JSON.stringify(account, null, 2));  
  
   // Controlling upsert operations END.  
  
   // Prevent update of deleted entity START.  
   // Delete the account.  
   return Sdk.request("DELETE", account1Uri);  
  }  
  )  
  .then(  
  function (request) {  
   if (request.status == 204) {  
    console.log("Account was deleted");  
  
    // Attempt to update it.  
    var accountUpsert = {  
     telephone1: "555-0005",  
     revenue: 7500000  
    };  
    // Perform operation only if matching resource exists.   
    var ifMatchResource = { header: "If-Match", value: "*" };  
    return Sdk.request("PATCH", account1Uri, accountUpsert, ifMatchResource);  
   }  
  } )  
  .then( function (request) {  
   // Success not expected.  
   // Without the If-Match header while using PATCH a new entity would have been created with the   
   // same ID as the deleted entity.  
   console.log("Unexpected status: %s", request.status);  
  
  },  
  // Catch error.  
  function (error) {  
   // Not found error expected.  
   console.log("Expected Error: %s", error.message);  
   console.log("\tAccount not updated because it doesn't exist.");  
  }  
  
  )  
 .catch(function (error) {  
  console.log(error.message);  
 });  
}  
  
```  
  
### <a name="see-also"></a>Vea también

[Utilizar API Web de Common Data Service](../overview.md)<br />
[Realizar operaciones condicionales mediante la API web](../perform-conditional-operations-using-web-api.md)<br />
[Ejemplos de la API web](../web-api-samples.md)<br />
[Ejemplo de operaciones condicionales de la API web](../web-api-conditional-operations-sample.md)<br />
[Ejemplo de operaciones condicionales de la API web (C#)](conditional-operations-csharp.md)<br />
[Ejemplos de la API web (JavaScript del lado del cliente)](../web-api-samples-client-side-javascript.md)<br />
[Ejemplo de operaciones básicas de la API web (JavaScript del lado del cliente)](basic-operations-client-side-javascript.md)<br />
[Ejemplo de datos de consulta de la API web (JavaScript del lado del cliente)](query-data-client-side-javascript.md)<br />
[Ejemplo de funciones y acciones de la API web (JavaScript del lado del cliente)](functions-actions-client-side-javascript.md)
