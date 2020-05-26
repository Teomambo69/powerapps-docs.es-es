---
title: Exportación de definiciones de cinta de opciones (aplicaciones basadas en modelos) | Microsoft Docs
description: Obtenga información sobre cómo exportar definiciones de cinta de opciones.
ms.custom: ''
ms.date: 04/30/2020
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: nkrb
ms.author: nabuthuk
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2b0ca0fb153813a0ed5b48e9df8344d3b6741057
ms.sourcegitcommit: c6906775005aec98973b1f5c3dbe5924aff6d26e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "3341365"
---
# <a name="export-ribbon-definitions"></a>Exportar definiciones de cinta de opciones

Para definir cambios de un modo eficaz en el RibbonXml predeterminado, debe poder hacer referencia a los datos de RibbonXml que definen esas cintas de opciones.  
  
## <a name="access-the-ribbon-definitions-for-your-organization"></a>Tener acceso a las definiciones de la cinta de opciones de la organización  

Si la cinta de opciones de la organización se ha modificado, debe exportar las definiciones actuales si trata de trabajar con los elementos de cinta de opciones personalizados. Para ello, use el ejemplo de [Exportar cinta de opciones xml](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ExportRibbonDefinitions).  
  
## <a name="access-the-default-ribbon-data"></a>Tener acceso a los datos predeterminados de la cinta de opciones  

 Las definiciones de cintas de opciones predeterminadas para aplicaciones basadas en modelos pueden descargarse desde [Descargas de Microsoft: ExportedRibbonXml.zip](https://download.microsoft.com/download/C/2/A/C2A79C47-DD2D-4938-A595-092CAFF32D6B/ExportedRibbonXml.zip). 
  
 El archivo applicationRibbon.xml contiene la definición de las cintas de opciones de la aplicación principal.  
  
 Los archivos que quedan contienen las definiciones que usan las entidades que tienen definiciones de la cinta de opciones que difieren de la plantilla de entidad. Cada archivo se denomina de acuerdo con el nombre de la entidad: nombre lógico de la entidad + Ribbon.xml.  
  
 Estos archivos representan el resultado de dos mensajes mediante [Ejemplo: Exportar definiciones de cinta de opciones](sample-export-ribbon-definitions.md):  
  
 <xref:Microsoft.Crm.Sdk.Messages.RetrieveApplicationRibbonRequest>  
 Este mensaje recupera las cintas de opciones de la aplicación principal incluida la plantilla de entidad.  
  
 <xref:Microsoft.Crm.Sdk.Messages.RetrieveEntityRibbonRequest>  
 Este mensaje recupera la definición de cinta de opciones usada para una entidad específica.  
  
### <a name="decompress-the-ribbon-data"></a>Descomprimir datos de la cinta de opciones  

 Los datos de la cinta de opciones se exporta como un archivo comprimido. Para descomprimir el archivo en XML tiene que usar la clase [System.IO.Packaging.ZipPackage](https://msdn.microsoft.com/library/system.io.packaging.zippackage.aspx). El siguiente ejemplo es un método auxiliar usado en el ejemplo del SDK para descomprimir el archivo.  

 ``` C# 
/// <summary>
/// A helper method that decompresses the Ribbon data returned
/// </summary>
/// <param name="data">The compressed ribbon data</param>
/// <returns></returns>
public byte[] unzipRibbon(byte[] data)
{
 System.IO.Packaging.ZipPackage package = null;
 MemoryStream memStream = null;

 memStream = new MemoryStream();
 memStream.Write(data, 0, data.Length);
 package = (ZipPackage)ZipPackage.Open(memStream, FileMode.Open);

 ZipPackagePart part = (ZipPackagePart)package.GetPart(new Uri("/RibbonXml.xml", UriKind.Relative));
 using (Stream strm = part.GetStream())
 {
  long len = strm.Length;
  byte[] buff = new byte[len];
  strm.Read(buff, 0, (int)len);
  return buff;
 }
}

```

### <a name="retrieve-the-application-ribbon-data"></a>Recuperar datos de la cinta de opciones de la aplicación  

 La cinta de opciones de la aplicación se puede recuperar mediante <xref:Microsoft.Crm.Sdk.Messages.RetrieveApplicationRibbonRequest>, tal como se muestra en el siguiente ejemplo.  

 ```C# 
 //Retrieve the Application Ribbon
var appribReq = new RetrieveApplicationRibbonRequest();
var appribResp = (RetrieveApplicationRibbonResponse)service.Execute(appribReq);

System.String applicationRibbonPath = Path.GetFullPath(exportFolder + "\\applicationRibbon.xml");
File.WriteAllBytes(applicationRibbonPath, unzipRibbon(appribResp.CompressedApplicationRibbonXml)); 
```
  
### <a name="retrieve-entity-ribbons"></a>Recuperar cintas de opciones de la entidad  

 Para recuperar la definición de cinta de opciones para entidades, puede incluir el nombre de la entidad como un parámetro de <xref:Microsoft.Crm.Sdk.Messages.RetrieveEntityRibbonRequest>.  
  
 Para recuperar las definiciones de la cinta de opciones para todas las entidades que admiten la cinta de opciones, necesita una lista de las entidades del sistema que tienen definiciones de la cinta de opciones que puedan variar de la plantilla de cinta de opciones de entidad. En el siguiente ejemplo se muestra una matriz de todas las entidades del sistema que tienen definiciones de la cinta de opciones.  

 ```C# 
 //This array contains all of the system entities that use the ribbon.
public System.String[] entitiesWithRibbons = {"account",
"activitymimeattachment",
"activitypointer",
"appointment",
"bulkoperation",
"calendar",
"campaign",
"campaignactivity",
"campaignresponse",
"competitor",
"connection",
"contact",
"contract",
"contractdetail",
"convertrule",
"convertruleitem",
"customeraddress",
"discount",
"discounttype",
"email",
"emailserverprofile",
"entitlement",
"entitlementchannel",
"entitlementtemplate",
"entitlementtemplatechannel",
"fax",
"goal",
"goalrollupquery",
"importfile",
"incident",
"invoice",
"invoicedetail",
"kbarticle",
"kbarticlecomment",
"lead",
"letter",
"list",
"listmember",
"mailbox",
"metric",
"opportunity",
"opportunityproduct",
"partnerapplication",
"phonecall",
"postfollow",
"pricelevel",
"product",
"productpricelevel",
"queue",
"queueitem",
"quote",
"quotedetail",
"recurringappointmentmaster",
"report",
"rollupfield",
"routingrule",
"routingruleitem",
"salesliterature",
"salesliteratureitem",
"salesorder",
"salesorderdetail",
"service",
"serviceappointment",
"sharepointdocument",
"sharepointdocumentlocation",
"sharepointsite",
"site",
"sla",
"slaitem",
"socialactivity",
"socialprofile",
"systemuser",
"task",
"team",
"teamtemplate",
"territory",
"uom",
"uomschedule",
"userquery"};
 ```
  
En el siguiente ejemplo se muestra cómo recuperar las definiciones de la cinta de opciones de un conjunto de entidades. 

```csharp
//Retrieve system Entity Ribbons
var entRibReq = new RetrieveEntityRibbonRequest() { RibbonLocationFilter = RibbonLocationFilters.All };
foreach (System.String entityName in entitiesWithRibbons)
{
 entRibReq.EntityName = entityName;
 var entRibResp = (RetrieveEntityRibbonResponse)service.Execute(entRibReq);

 System.String entityRibbonPath = Path.GetFullPath(exportFolder + "\\" + entityName + "Ribbon.xml");
 File.WriteAllBytes(entityRibbonPath, unzipRibbon(entRibResp.CompressedEntityXml));
 //Write the path where the file has been saved.
 Console.WriteLine(entityRibbonPath);
} 
``` 
Cualquier entidad personalizada también admite personalizaciones de la cinta de opciones. Para obtener una lista de entidades personalizadas, use <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAllEntitiesRequest> y recupere los nombres de las entidades personalizadas. En el siguiente ejemplo se muestra cómo recuperar las definiciones de cintas de opciones de todas las entidades personalizadas.  

```csharp 
//Check for custom entities
 var raer = new RetrieveAllEntitiesRequest() { EntityFilters = EntityFilters.Entity };
 var resp = (RetrieveAllEntitiesResponse)service.Execute(raer);
 foreach (EntityMetadata em in resp.EntityMetadata)
 {
  if (em.IsCustomEntity == true && em.IsIntersect == false)
  {
   entRibReq.EntityName = em.LogicalName;
   var entRibResp = (RetrieveEntityRibbonResponse)service.Execute(entRibReq);
   System.String entityRibbonPath = Path.GetFullPath(exportFolder + "\\" + em.LogicalName + "Ribbon.xml");
   File.WriteAllBytes(entityRibbonPath, unzipRibbon(entRibResp.CompressedEntityXml));
   //Write the path where the file has been saved.
   Console.WriteLine(entityRibbonPath);
  }
 } 
``` 

## <a name="troubleshoot-ribbon-issues"></a>Solución de problemas de cinta

Si tiene un problema con un botón de la barra de comandos de la cinta, use esta [guía de solución de problemas](https://support.microsoft.com/help/4552163) para encontrar y resolver el problema.

### <a name="see-also"></a>Vea también  
 [Personalizar la cinta de opciones](customize-commands-ribbon.md)   
 [Presentación de la barra de comandos o la cinta de opciones](command-bar-ribbon-presentation.md)   
 [Exportar, preparar para modificar e importar la cinta de opciones](export-prepare-edit-import-ribbon.md)
