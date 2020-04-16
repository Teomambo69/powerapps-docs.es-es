---
title: Ejemplo de operaciones de datos de la API web (JavaScript del lado del cliente) (Common Data Service)| Microsoft Docs
description: En este tema se proporciona una descripción de distintos ejemplos de API Web que están implementados mediante JavaScript del lado cliente
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: a32e9a04-7bc1-41dd-b9af-bb4f21a613c6
caps.latest.revision: 15
author: JimDaly
ms.author: jdaly
ms.reviewer: pehecke
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 18393e9416de7430c794831a7f6cf5fdb74d46b4
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154948"
---
# <a name="web-api-data-operations-samples-client-side-javascript"></a>Ejemplo de operaciones de datos de la API web (JavaScript del lado del cliente)


En este tema se proporciona un entendimiento común sobre los ejemplos de la API web mediante JavaScript del lado del cliente. Si bien cada ejemplo se centra en un aspecto distinto de la API web de Common Data Service, todos ellos siguen un proceso y una estructura similares descritos en este tema.  

<a name="bkmk_listOfSamples"></a>   
## <a name="web-api-samples-using-client-side-javascript"></a>Ejemplos de la API web mediante JavaScript del lado del cliente  
 Los siguientes ejemplos utilizan los patrones descritos aquí:  
  
|Muestra|Grupo de ejemplo|Descripción|  
|------------|------------------|-----------------|  
|[Ejemplo de operaciones básicas de la API web (JavaScript del lado del cliente)](samples/basic-operations-client-side-javascript.md)|[Ejemplo de operaciones básicas de la API web](web-api-basic-operations-sample.md)|Demuestra cómo crear, recuperar, actualizar, eliminar, asocie y anular la asociación de registros de entidad de Common Data Service.|  
|[Ejemplo de datos de consulta de la API web (JavaScript del lado del cliente)](samples/query-data-client-side-javascript.md)|[Ejemplo de datos de consulta de la API web](web-api-query-data-sample.md)|Demuestra cómo usar sintaxis y funciones de consulta de OData v4 así como funciones de consulta de Common Data Service. Incluye demostración de trabajo con consultas predefinidas y uso de FetchXML para realizar consultas.|  
|[Ejemplo de operaciones condicionales de la API web (JavaScript del lado del cliente)](samples/conditional-operations-client-side-javascript.md)|[Ejemplo de operaciones condicionales de la API web](web-api-conditional-operations-sample.md)|Demuestra cómo realizar operaciones condicionales. El comportamiento de estas operaciones depende de los criterios que especifique.|  
|[Ejemplo de funciones y acciones de la API web (JavaScript del lado del cliente)](samples/functions-actions-client-side-javascript.md)|[Ejemplo de funciones y acciones de la API web](web-api-functions-actions-sample.md)|Demuestra cómo usar funciones y acciones enlazadas y sin enlazar, incluidas acciones personalizadas.|  
  
<a name="bkmk_howToDownload"></a>   
## <a name="how-to-download-the-source-code-for-the-sample"></a>Cómo descargar el código de origen del ejemplo.  
 El código de origen para cada ejemplo está disponible en [Galería de código de MSDN](https://code.msdn.microsoft.com/site/search?f%5b0%5d.type=user&f%5b0%5d.value=microsoft%20dynamics%20crm%20sdk%20documentation%20team). El vínculo para descargar cada ejemplo se incluye en la página individual de ese ejemplo.  
  
 Después de descargar el ejemplo, extraiga el archivo comprimido. Busque la solución Microsoft Visual Studio 2015 para cada ejemplo dentro de la carpeta C# porque el proyecto es un proyecto de aplicación web ASP.NET vacío. Una solución Common Data Service también se proporciona en la descarga que puede importar y ejecutar.  
  
> [!NOTE]
>  No se requiere Visual Studio ni ASP.NET para desarrollar JavaScript del lado del cliente para Common Data Service, aunque el sitio de la Galería de códigos de MSDN requiere que se incluyan archivos en Visual Studio como contenedor.  Sin embargo, Visual Studio proporciona una buena experiencia para escribir JavaScript.  
  
<a name="bkmk_HowToImport"></a>   
## <a name="how-to-import-the-common-data-service-solution-that-contains-the-sample"></a>Cómo importar la solución de Common Data Service que contiene el ejemplo.  
 Dentro de cada proyecto encontrará un archivo de solución administrada de Common Data Service. El nombre de este archivo dependerá del nombre del proyecto de ejemplo, pero el nombre de archivo terminará con `_managed.zip`.  
  
 Para importar la solución de Common Data Service en el servidor de Common Data Service, siga estos pasos:  
  
1.  Extraiga el contenido del archivo zip descargado y busque el archivo de la solución de Common Data Service, que también será un archivo zip. Por ejemplo, si ha descargado el ejemplo `Basic Operations`, busque el archivo zip de la solución de Common Data Service con el nombre `WebAPIBasicOperations\WebAPIBasicOperations_1_0_0_0_managed.zip`.  
  
2.  En la UI de Common Data Service, vaya a **Configuración > Soluciones**. Esta página enumera todas las soluciones del servidor de Common Data Service. Después de acabar de importar esta solución, el nombre de la solución para ese ejemplo aparecerá en esta lista (por ejemplo, **Web API Basics Operations**).  
  
3.  Haga clic en **Importar** y siga las instrucciones del diálogo de importación para terminar esta acción.  
  
<a name="bkmk_howToRunSample"></a>   
## <a name="how-to-run-the-sample-to-see-the-script-in-action"></a>Cómo ejecutar el ejemplo para ver el script en acción  
 El programa de ejemplo se ejecuta como recurso web en Common Data Service. La solución importada proporciona una página de configuración que le da una opción de mantener o de eliminar datos de ejemplo y un botón para iniciar el programa de ejemplo.
  
 Para ejecutar el ejemplo, lleva a cabo lo siguiente:  
  
1.  En la página **Todas las soluciones** en Common Data Service, haga clic en el nombre de la solución (por ejemplo, vínculo **Web API Basics Operations**). Se abrirán las propiedades de la solución en una nueva ventana.  
  
2.  En el menú de navegación izquierdo, haga clic en **Configuración**.  
  
3.  Haga clic en el botón **Iniciar ejemplo** para ejecutar el código de ejemplo.  
  
<a name="bkmk_commonElements"></a>   
## <a name="common-elements-found-in-each-sample"></a>Elementos comunes que se encuentran en cada ejemplo  
 En la siguiente lista se resaltan algunos elementos comunes que se encuentran en cada uno de estos ejemplos.  
  
-   Se llama a la función `Sdk.startSample` cuando un usuario hace clic en el botón **Iniciar ejemplo** desde la página HTML. La función `Sdk.startSample` inicializa variables globales y pone en marcha la primera operación de la cadena.  
  
-   La salida del programa y mensajes de error se envían a la consola de depurador del explorador. Para ver esta salida, abra la ventana de la consola primero antes de ejecutar el ejemplo.  Pulse F12 para tener acceso a las herramientas de desarrollo, incluida la ventana de la consola, en exploradores Internet Explorer y Microsoft Edge.  
  
-   Estos ejemplos usan la implementación nativa [ES6-Promise](https://msdn.microsoft.com/library/dn802826\(v=vs.94\).aspx) del explorador para exploradores modernos que la admiten. Para Internet Explorer, este ejemplo usar [ES6-Promise polyfill](https://github.com/stefanpenner/es6-promise) porque Internet Explorer es el único explorador admitido por Common Data Service que no tiene compatibilidad nativa para esta característica.  
  
     No se requieren promesas. Pueden realizarse interacciones similares con funciones de devolución de llamada.  
  
-   La función `Sdk.request` controla la solicitud en función de la información pasada en como parámetros. En función de la necesidad de cada ejemplo, los parámetros pasados pueden ser diferentes. Consulte el código de origen del ejemplo para obtener más detalles.  
  
    ```javascript  
    /**  
     * @function request  
     * @description Generic helper function to handle basic XMLHttpRequest calls.  
     * @param {string} action - The request action. String is case-sensitive.  
     * @param {string} uri - An absolute or relative URI. Relative URI starts with a "/".  
     * @param {object} data - An object representing an entity. Required for create and update actions.  
     * @returns {Promise} - A Promise that returns either the request object or an error object.  
     */  
    Sdk.request = function (action, uri, data) {  
        if (!RegExp(action, "g").test("POST PATCH PUT GET DELETE")) { // Expected action verbs.  
            throw new Error("Sdk.request: action parameter must be one of the following: " +  
                "POST, PATCH, PUT, GET, or DELETE.");  
        }  
        if (!typeof uri === "string") {  
            throw new Error("Sdk.request: uri parameter must be a string.");  
        }  
        if ((RegExp(action, "g").test("POST PATCH PUT")) && (data === null || data === undefined)) {  
            throw new Error("Sdk.request: data parameter must not be null for operations that create or modify data.");  
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
            request.onreadystatechange = function () {  
                if (this.readyState === 4) {  
                    request.onreadystatechange = null;  
                    switch (this.status) {  
                        case 200: // Success with content returned in response body.  
                        case 204: // Success with no content returned in response body.  
                            resolve(this);  
                            break;  
                        default: // All other statuses are unexpected so are treated like errors.  
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
    ```  
  
     La función `Sdk.request` devuelve una promesa. Cuando la solicitud envuelta por la promesa está completa, se resuelve o se rechaza la promesa. Si se resuelve, se llamará a la función en el método `then` siguiente. Si se rechaza, se llamará a la función en el método `catch` siguiente. Si la función en el método `then` propiamente dicho devuelve una promesa, la cadena de operaciones en los métodos `then` consecutivos puede continuar. Devolver una promesa nos permite encadenar estas operaciones de ejemplo juntas de forma que sea preferida por muchos programadores a las funciones de devolución de llamada tradicionales. Para obtener más información sobre promesa, consulte [Promesa de JavaScript](https://msdn.microsoft.com/library/dn802826\(v=vs.94\).aspx).  
  
### <a name="see-also"></a>Vea también

[Usar la API web de Common Data Service](overview.md)<br />
[Ejemplos de la API web](web-api-samples.md)<br />
[Ejemplos de la API web (C#)](web-api-samples-csharp.md)   
 
