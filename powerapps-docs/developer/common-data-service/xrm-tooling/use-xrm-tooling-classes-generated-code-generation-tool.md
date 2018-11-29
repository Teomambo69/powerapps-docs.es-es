---
title: Usar útiles de XRM con clases generadas con la herramienta de generación de código (Common Data Service para aplicaciones)| Microsoft Docs
description: La clase CrmServiceClient se puede usar para configurar sus clases de entidad y contexto de datos con la herramienta de generación de código. La muestra muestra cómo crear una conexión a CDS para aplicaciones mediante una instancia de esta clase y definir el valor del objeto OrganizationServiceProxy para la propiedad CrmServiceClient.OrganizationServiceProxy.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 7c81c1e5-2229-4a15-8374-6ee9456d18a9
caps.latest.revision: 19
author: MattB-msft
ms.author: kvivek
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-xrm-tooling-with-classes-generated-using-the-code-generation-tool"></a>Usar los útiles de XRM con las clases generadas por la herramienta de generación de código

<!-- TODO:
The <xref:Microsoft.Xrm.Tooling.Connector> assembly doesn’t directly provide interfaces for the entity and data context classes generated using the code-generation tool. However, you can use the CDS for Apps connection created by the <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> class to set up your entity and data context classes by using the code-generation tool. More information: [Create Early Bound Entity Classes with the Code Generation Tool (CrmSvcUtil.exe)](../org-service/create-early-bound-entity-classes-code-generation-tool.md) -->
  
 Para usar la conexión de CDS para aplicaciones creada por la clase de <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>, utilice una instancia de esta clase para crear una conexión a CDS para aplicaciones y, a continuación, establezca el valor del objeto <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy> en la propiedad <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.OrganizationServiceProxy> .  
  
```csharp  
CrmServiceClient crmSvc = new CrmServiceClient(new System.Net.NetworkCredential("<UserName>", "<Password>",“<Domain>”),"<Server>", "<Port>", "<OrgName>");  
  
// Verify that you are connected.  
if (crmSvc != null && crmSvc.IsReady)  
{  
    //Display the CRM version number and org name that you are connected to  
    Console.WriteLine("Connected to CRM! (Version: {0}; Org: {1}",   
    crmSvc.ConnectedOrgVersion, crmSvc.ConnectedOrgUniqueName);  
  
    Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy prox = crmSvc.OrganizationServiceProxy;   
}  
else  
{  
    // Display the last error.  
    Console.WriteLine("Error occurred: {0}", crmSvc.LastCrmError);  
  
    // Display the last exception message if any.  
    Console.WriteLine(crmSvc.LastCrmException.Message);  
    Console.WriteLine(crmSvc.LastCrmException.Source);  
    Console.WriteLine(crmSvc.LastCrmException.StackTrace);  
  
    return;  
}  
  
```  
  
> [!NOTE]
>  La clase de <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy> no es segura para el hilo. Mientras trabaja con las clases de entidad y contexto de datos generadas con la herramienta de generación de código o con LINQ para recuperar datos, podría contemplar la posibilidad de crear un esquema de bloqueo en el código si se ejecuta en un entorno con varios subprocesos.  
  
### <a name="see-also"></a>Vea también  

<!-- TODO:
[Use the IOrganizationService Web Service to Read and Write Data or Metadata](../org-service/use-organization-service-read-write-data-metadata.md)<br /> -->
[Crear aplicaciones cliente de Windows mediante las herramientas XRM](build-windows-client-applications-xrm-tools.md)
