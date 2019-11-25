---
title: 'Ejemplo: Pasar varios valores a un recurso web con el parámetro de datos (aplicaciones basadas en modelos) | Microsoft Docs'
description: Este ejemplo representa una técnica para transferir los valores adicionales con un solo parámetro y luego los procesa dentro del recurso web.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2a4b4a6bf2da6cc6588a0fcf8b7523bae1c7da5f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753588"
---
# <a name="sample-pass-multiple-values-to-a--web-resource-through-the-data-parameter"></a>Ejemplo: pasar varios valores a un recurso web mediante el parámetro de datos

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-pass-multiple-values-web-resource-through-data-parameter -->

Una página de recurso web (HTML) puede aceptar únicamente un solo parámetro personalizado denominado `data`. Para pasar más de un valor en el parámetro de datos, necesita codificar los parámetros y descodificar los parámetros de la página.  
  
 Esta página representa una técnica para transferir los valores adicionales con un solo parámetro y luego los procesa dentro del recurso web. 
  
## <a name="sample-html-web-resource"></a>Ejemplo del recurso web HTML  
 El código HTML que se muestra a continuación representa un recurso web de la página web (HTML) que incluye un script que define tres funciones:  
  
- **getDataParam**: Llamada desde el evento `body.onload`, esta característica recupera cualquier parámetro de cadena de consulta que pasa a la página y busca uno denominado `data`.  
  
- **parseDataValue**: Recibe el parámetro de datos de `getDataParam` y genera una tabla de DHTML para mostrar los valores en el parámetro de `data`.  
  
  > [!NOTE]
  >  Todos los caracteres incluidos en la cadena de consulta se codificarán mediante el [método encodeURIComponent](https://msdn.microsoft.com/library/xh9be5xc\(v=VS.85\).aspx). Esta funcionalidad usa el JavaScript [método decodeURIComponent](https://msdn.microsoft.com/library/91b80x6x\(VS.85\).aspx) para descodificar los valores transmitidos.  
  
- **noParams**: Muestra un mensaje cuando los parámetros no se transmiten a la página.  
  
```html  
<!DOCTYPE html >  
<html lang="en-us">  
<head>  
 <title>Show Data Parameters Page</title>  
 <style type="text/css">  
  body  
  {  
   font-family: Segoe UI, Tahoma, Arial;  
   background-color: #d6e8ff;  
  }  
  tbody  
  {  
   background-color: white;  
  }  
  th  
  {  
   background-color: black;  
   color: White;  
  }  
 </style>  
 <script type="text/javascript">  
  document.onreadystatechange = function () {  
   if (document.readyState == "complete") {  
    getDataParam();  
   }  
  }  
  
  function getDataParam() {  
   //Get the any query string parameters and load them  
   //into the vals array  
  
   var vals = new Array();  
   if (location.search != "") {  
    vals = location.search.substr(1).split("&");  
    for (var i in vals) {  
     vals[i] = vals[i].replace(/\+/g, " ").split("=");  
    }  
    //look for the parameter named 'data'  
    var found = false;  
    for (var i in vals) {  
     if (vals[i][0].toLowerCase() == "data") {  
      parseDataValue(vals[i][1]);  
      found = true;  
      break;  
     }  
    }  
    if (!found)  
    { noParams(); }  
   }  
   else {  
    noParams();  
   }  
  }  
  
  function parseDataValue(datavalue) {  
   if (datavalue != "") {  
    var vals = new Array();  
  
    var message = document.createElement("p");  
    setText(message, "These are the data parameters values that were passed to this page:");  
    document.body.appendChild(message);  
  
    vals = decodeURIComponent(datavalue).split("&");  
    for (var i in vals) {  
     vals[i] = vals[i].replace(/\+/g, " ").split("=");  
    }  
  
    //Create a table and header using the DOM  
    var oTable = document.createElement("table");  
    var oTHead = document.createElement("thead");  
    var oTHeadTR = document.createElement("tr");  
    var oTHeadTRTH1 = document.createElement("th");  
    setText(oTHeadTRTH1, "Parameter");  
    var oTHeadTRTH2 = document.createElement("th");  
    setText(oTHeadTRTH2, "Value");  
    oTHeadTR.appendChild(oTHeadTRTH1);  
    oTHeadTR.appendChild(oTHeadTRTH2);  
    oTHead.appendChild(oTHeadTR);  
    oTable.appendChild(oTHead);  
    var oTBody = document.createElement("tbody");  
    //Loop through vals and create rows for the table  
    for (var i in vals) {  
     var oTRow = document.createElement("tr");  
     var oTRowTD1 = document.createElement("td");  
     setText(oTRowTD1, vals[i][0]);  
     var oTRowTD2 = document.createElement("td");  
     setText(oTRowTD2, vals[i][1]);  
  
     oTRow.appendChild(oTRowTD1);  
     oTRow.appendChild(oTRowTD2);  
     oTBody.appendChild(oTRow);  
    }  
  
    oTable.appendChild(oTBody);  
    document.body.appendChild(oTable);  
   }  
   else {  
    noParams();  
   }  
  }  
  
  function noParams() {  
   var message = document.createElement("p");  
   setText(message, "No data parameter was passed to this page");  
  
   document.body.appendChild(message);  
  }  
  //Added for cross browser support.  
  function setText(element, text) {  
   if (typeof element.innerText != "undefined") {  
    element.innerText = text;  
   }  
   else {  
    element.textContent = text;  
   }  
  
  }  
 </script>  
</head>  
<body>  
</body>  
</html>  
  
```  
  
#### <a name="using-this-page"></a>Uso de esta página  
  
1.  Cree un recurso web de la página web denominado "new_/ShowDataParams.htm" con el código de ejemplo.  
  
     Los parámetros que desea pasar son: `first=First Value&second=Second Value&third=Third Value`  
  
    > [!NOTE]
    >  Si va a agregar parámetros estáticos mediante el cuadro de diálogo Propiedades de recurso web del editor de formularios, puede simplemente pegar los parámetros sin codificarlos en el campo **Custom Parameter(data)**. Estos valores se codificarán para usted, pero necesitará descodificarlos y extraerlos en su página.  
  
2.  Para valores dinámicos generados en el código, use el método de `encodeURIComponent` en los parámetros. Los valores codificados deben:  
  
     `first%3DFirst%20Value%26second%3DSecond%20Value%26third%3DThird%20Value`  
  
     Abrir la página al pasar los parámetros codificados como el valor del parámetro de datos:  
  
    ```  
    https://<server name>/WebResources/new_/ShowDataParams.htm?data=first%3DFirst%20Value%26second%3DSecond%20Value%26third%3DThird%20Value  
    ```  
  
    > [!NOTE]
    >  Si ha agregado el recurso web a un formulario y ha pegado los parámetros no codificados en el campo **Custom Parameters(data)** solo puede realizar una vista previa del formulario.  
  
3.  `new_/ShowDataParams.htm` mostrará una tabla dinámicamente generada:  
  
    |Parámetro|Valor|  
    |---------------|-----------|  
    |Primero|Primer valor|  
    |Segundo|Segundo valor|  
    |Tercero|Tercer valor|  
  
### <a name="how-it-works"></a>Cómo funciona  
 Para tener acceso a los valores incrustados dentro del valor del parámetro de la cadena de consulta de datos, en el recurso web de la página web puede extraer el valor del parámetro de datos y después usar el código para dividir la cadena en una matriz a fin de tener acceso a cada par de valor de nombre de forma individual.  
  
 Cuando la página se carga, se llama a la función `getDataParam`. Esta funcionalidad simplemente identifica el parámetro de datos y pasa el valor a la función `ParseDataValue` . Si no se encuentra el parámetro de datos, la característica de `noParams` agregará un mensaje a la página en el lugar de la tabla.  
  
 La función de `ParseDataValue` usa una lógica similar encontrada en `getDataParam` para ubicar los delimitadores de parámetros personalizados para crear una matriz de pares de valores de nombre. Después genera una tabla y la anexa a document.body que, de lo contrario, estaría vacío.  
  
### <a name="see-also"></a>Vea también  
 [Recursos web](web-resources.md)   
 [Ejemplo: importar archivos como recursos web](sample-import-files-web-resources.md)   
 [Recursos web de página web (HTML)](webpage-html-web-resources.md)   
