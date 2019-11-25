---
title: 'Ejemplo: Importar archivos como recursos web (aplicaciones basadas en modelos) | Microsoft Docs'
description: El ejemplo proporciona un ejemplo simplificado de la importación de archivos como recursos web.
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
ms.openlocfilehash: 775ad0f50f65845f6e7fa437348b69c6730008a5
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749596"
---
# <a name="sample-import-files-as-web-resources"></a>Ejemplo: importar archivos como recursos web

Cuando desarrolle un gran número de archivos para usar como recursos web, puede ahorrarse el trabajo de agregarlos manualmente en toda la aplicación. Muchos recursos web pueden desarrollarse y probarse fuera de aplicaciones basadas en modelos y luego se importan.  
  
 Esta muestra ofrece un ejemplo simplificado de este proceso.  
 
 Descargue el ejemplo: [Importar archivos como recursos web](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ImportWebResources). 

## <a name="prerequisites"></a>Requisitos previos
[!INCLUDE[sdk-prerequisite](../../includes/sdk-prerequisite.md)]
  
## <a name="requirements"></a>Requisitos  


<!-- TODO: This should be written so that the connection helper code is not required. [!INCLUDE[sdk_SeeConnectionHelper](../../includes/sdk-seeconnectionhelper.md)] -->
  
 El código de muestra que se incluye en el paquete de descarga de SDK incluye los siguientes archivos necesarios para esta muestra:  
  
 **ImportJob.xml**  
 Este archivo proporciona datos de los registros de recursos web que se crearán. Contiene los siguientes datos para cada archivo:  
  
- **path:** la ruta de acceso a cada archivo desde la carpeta FilesToImport.  
  
- **displayName:** El nombre del recurso web.  
  
- **descripción:** Una descripción de lo que hace cada archivo.  
  
- **nombre:** El nombre que se usará para el recurso web.  
  
  > [!NOTE]
  > - Cada uno de estos nombres comienza con un carácter de subrayado. El prefijo de personalización del editor de soluciones se antepondrá al nombre cuando se cree el recurso web. En lugar de codificar rígidamente un prefijo de personalización específico, esta muestra detectará el prefijo de personalización actual para un registro de editor que ya existe en la organización.  
  >   - Dado que cada uno de estos archivos se desarrolló fuera de aplicaciones basadas en modelos y dependen de las rutas relativas para acceder a la otra ruta, los nombres incluyen los caracteres de barra diagonal inversa "/" para crear una estructura de carpeta virtual de modo que los vínculos relativos seguirán funcionando dentro de aplicaciones basadas en modelos.  
  
- **type:** especifica el tipo de recurso web que crear con los valores enteros encontrados en [Tipos de recursos web](web-resources.md#BKMK_WebResourceTypes).
  
  **FilesToImport/ShowData.htm**  
  Este recurso web HTML requiere que cada uno de los demás archivos muestre la tabla siguiente.  
  
|||  
|-|-|  
|**Nombre de pila**|**Apellidos**|  
|Apurva|Dalia|  
|Ofer|Daliot|  
|Jim|Daly|  
|Ryan|Danner|  
|Mike|Danseglio|  
|Alex|Darrow|  
  
 **FilesToImport/CSS/Styles.css**  
 Este archivo proporciona los estilos CSS que se usan en ShowData.htm.  
  
 **FilesToImport/Data/Data.xml**  
 Este archivo contiene la lista de nombres que se muestra en la tabla.  
  
 **FilesToImport/script/Script.js**  
 Este archivo contiene una biblioteca JScript que contiene información sobre la ubicación relativa del archivo Data.xml y del archivo Transform.xslt. También contiene la función de `showData` que transforma los datos y los agrega a la página de ShowData.htm.  
  
 **FilesToImport/XSL/Transform.xslt**  
 Este archivo contiene la definición de XSL sobre cómo transformar los datos en una tabla HTML.  
  
## <a name="demonstrates"></a>Demostraciones  
  
### <a name="creating-web-resources-in-the-context-of-a-solution"></a>Creación de recursos web en el contexto de una solución  
 Los recursos web son registros propiedad de la organización por lo que se pueden crear utilizando el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*> o utilizando el mensaje <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> y el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> . Este ejemplo muestra cómo usar el parámetro opcional de `SolutionUniqueName` para asociar un recurso web con una solución específica cuando se crea. Esto requiere el uso del mensaje <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest>.  
  
### <a name="uploading-files-from-disk"></a>Carga de archivos desde el disco  
 La propiedad WebResource.Content requiere una cadena de base 64 que representa los contenidos binarios del archivo. El siguiente ejemplo es el método usado para convertir el archivo en el tipo requerido.  
  
```C#
//Encodes the Web Resource File
static public string getEncodedFileContents(String pathToFile)
{
    FileStream fs = new FileStream(pathToFile, FileMode.Open, FileAccess.Read);
    byte[] binaryData = new byte[fs.Length];
    long bytesRead = fs.Read(binaryData, 0, (int)fs.Length);
    fs.Close();
    return System.Convert.ToBase64String(binaryData, 0, binaryData.Length);
}
```
  
### <a name="combining-web-resource-record-data-with-file-data"></a>Combinar datos de registro del recurso web con datos de archivo  
 El archivo ImportJob.xml demuestra cómo se combinan los datos de los archivos que se importarán y los datos del recurso web que se creará. En especial, para que vínculos relativos entre los archivos relacionados sigan funcionando, el nombre de los recursos web que cree debe conservar la información acerca la posición relativa de los archivos en el disco mediante directorios simulados en el nombre de archivo. Debido a los datos en el archivo ImportJob.xml, todos estos archivos de recursos web relacionados se crearán en una carpeta virtual común.  
  
> [!NOTE]
>  No es necesario publicar los recursos web cuando se crean. No obstante, es necesario publicarlos cuando se actualizan.  
  
## <a name="example"></a>Ejemplo  
 La siguiente parte del archivo ImportWebResources.cs espera las siguientes variables:  
  
- `_customizationPrefix`: El prefijo de personalización del editor de **Ejemplos del SDK de MDA**. Si este editor no existe, se creará con el prefijo de personalización "ejemplo".  
  
- `_ImportWebResourcesSolutionUniqueName`: El nombre único **Importar solución de muestra de recursos web** creado en este ejemplo. El valor es `ImportWebResourcesSample`.  
  
```C#
//Read the descriptive data from the XML file
XDocument xmlDoc = XDocument.Load("../../ImportJob.xml");

//Create a collection of anonymous type references to each of the Web Resources
var webResources = from webResource in xmlDoc.Descendants("webResource")
                   select new
                   {
                       path = webResource.Element("path").Value,
                       displayName = webResource.Element("displayName").Value,
                       description = webResource.Element("description").Value,
                       name = webResource.Element("name").Value,
                       type = webResource.Element("type").Value
                   };

// Loop through the collection creating Web Resources
int counter = 0;
foreach (var webResource in webResources)
{
    //Set the Web Resource properties
    WebResource wr = new WebResource
    {
        Content = getEncodedFileContents(@"../../" + webResource.path),
        DisplayName = webResource.displayName,
        Description = webResource.description,
        Name = _customizationPrefix + webResource.name,
        LogicalName = WebResource.EntityLogicalName,
        WebResourceType = new OptionSetValue(Int32.Parse(webResource.type))
    };

    // Using CreateRequest because we want to add an optional parameter
    CreateRequest cr = new CreateRequest
    {
        Target = wr
    };
    //Set the SolutionUniqueName optional parameter so the Web Resources will be
    // created in the context of a specific solution.
    cr.Parameters.Add("SolutionUniqueName", _ImportWebResourcesSolutionUniqueName);

    CreateResponse cresp = (CreateResponse)_serviceProxy.Execute(cr);
    // Capture the id values for the Web Resources so the sample can delete them.
    _webResourceIds[counter] = cresp.id;
    counter++;
    Console.WriteLine("Created Web Resource: {0}", webResource.displayName);
}
```
  
  No es necesario publicar los recursos web cuando se crean. No obstante, es necesario publicarlos cuando se actualizan.  
  
### <a name="see-also"></a>Vea también  
 [Referencia de la entidad WebResource](../common-data-service/reference/entities/webresource.md)<br/>
 [Recursos web](web-resources.md)
