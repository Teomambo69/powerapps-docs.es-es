---
title: Utilizar útiles de XRM para crear datos (Common Data Service para aplicaciones)| Microsoft Docs
description: Utilizar la clase CrmServiceClient para crear datos en CDS para aplicaciones
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: f6a03552-1f07-4d4b-b7ae-fa246a0d7c29
caps.latest.revision: 14
author: MattB-msft
ms.author: kvivek
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-xrm-tooling-to-create-data"></a>Usar útiles de XRM para crear los datos

Existen siete métodos disponibles en la clase <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> para crear nuevos datos y asociaciones. Una acción de creación que usa la API de los útiles de XRM requiere una carga de datos. La carga útil de datos toma la forma de un objeto `Dictionary<string, CrmDataTypeWrapper>`. <xref:Microsoft.Xrm.Tooling.Connector.CrmDataTypeWrapper> se usa para informes a la interfaz del tipo de control debe ser aplicado al punto de datos al que está haciendo referencia. Algunos de los métodos para crear datos se enumeran en este tema.  
  
## <a name="createnewrecord"></a>CreateNewRecord  

Este método se usa para crear un tipo de datos de la entidad en CDS para aplicaciones. Para utilizarlo, es necesario conocer el nombre de esquema de la entidad en la que desea crear un registro y se debe crear una carga de datos para pasar al método. En este ejemplo se crea un registro de cuenta.  
  
```csharp 
CrmServiceClient crmSvc = new CrmServiceClient(new System.Net.NetworkCredential("<UserName>", "<Password>",“<Domain>”),"<Server>", "<Port>", "<OrgName>");  
  
// Verify that you are connected  
if (crmSvc != null && crmSvc.IsReady)  
{  
    //Display the CRM version number and org name that you’re connected to.  
    Console.WriteLine("Connected to CRM! (Version: {0}; Org: {1}",   
    crmSvc.ConnectedOrgVersion, crmSvc.ConnectedOrgUniqueName);  
  
    // Create an account record  
    Dictionary<string, CrmDataTypeWrapper> inData = new Dictionary<string, CrmDataTypeWrapper>();  
    inData.Add("name", new CrmDataTypeWrapper("Sample Account Name", CrmFieldType.String));  
    inData.Add("address1_city", new CrmDataTypeWrapper("Redmond", CrmFieldType.String));  
    inData.Add("telephone1", new CrmDataTypeWrapper("555-0160", CrmFieldType.String));  
    accountId = ctrl.CrmConnectionMgr.CrmSvc.CreateNewRecord("account", inData);  
  
    // Verify if the account is created.  
    if (accountId != Guid.Empty)  
    {  
        Console.WriteLine(“Account created.”);  
    }  
}  
else  
{  
    // Display the last error.  
    Console.WriteLine("An error occurred: {0}", crmSvc.LastCrmError);  
  
    // Display the last exception message if any.  
    Console.WriteLine(crmSvc.LastCrmException.Message);  
    Console.WriteLine(crmSvc.LastCrmException.Source);  
    Console.WriteLine(crmSvc.LastCrmException.StackTrace);  
  
    return;  
}  
```  
  
En este ejemplo se creó un objeto de carga de datos llamado `indata`. A continuación, se rellenó mediante la sintaxis general: `crmFieldName , new CrmDataTypeWrapper(data,CrmFieldType)`. Después de configurar el objeto `indata` para obtener los valores para crear, se denominó al método `CreateNewRecord` proporcionando el nombre lógico de la entidad para la cuenta y la carga de datos (`indata`).  
  
> [!NOTE]
>  También puede crear un registro de entidad usando los útiles de XRM al ejecutar el mensaje <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> con el método <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmOrganizationRequest*>. Más información: [Utilizar mensajes con el método ExecuteCrmOrganizationRequest](use-messages-executecrmorganizationrequest-method.md)  
  
## <a name="createannotation"></a>CreateAnnotation
  
Este método se usa para crear y adjuntar un objeto de nota a cualquier registro de entidad. Aunque puede rellenar todas las variables de la nota en el primer paso, solo debe proporcionar los campos de texto para el asunto y la nota. En la práctica, esto normalmente se usa para adjuntar notas generadas por el sistema a una entidad, o para adjuntar los archivos almacenados en CDS para aplicaciones a una entidad. Además, si proporciona su propia interfaz de usuario para crear notas para su usuario, así es cómo normalmente adjuntaría la nota a la entidad del titular en CDS para aplicaciones. Este ejemplo es la continuación del ejemplo anterior para crear una nota en la cuenta recién creada.  
  
```csharp
CrmServiceClient crmSvc = new CrmServiceClient(new System.Net.NetworkCredential("<UserName>", "<Password>", “<Domain>”),"<Server>", "<Port>", "<OrgName>");  
  
// Verify that you are connected.  
if (crmSvc != null && crmSvc.IsReady)  
{  
    //Display the CRM version number and org name that you are connected to.  
    Console.WriteLine("Connected to CRM! (Version: {0}; Org: {1}",   
    crmSvc.ConnectedOrgVersion, crmSvc.ConnectedOrgUniqueName);  
  
    // Create and attach a note.  
    inData.Clear();   
    inData.Add("subject", new CrmDataTypeWrapper("This is a NOTE from the API" , CrmFieldType.String));   
    inData.Add("notetext", new CrmDataTypeWrapper("This is text that will go in the body of the note" , CrmFieldType.String));  
    Guid noteID = crmSvc.CreateAnnotation("account", accountId, inData);  
}  
else  
{  
    // Display the last error.  
    Console.WriteLine("An error occurred: {0}", crmSvc.LastCrmError);  
  
    // Display the last exception message if any.  
    Console.WriteLine(crmSvc.LastCrmException.Message);  
    Console.WriteLine(crmSvc.LastCrmException.Source);  
    Console.WriteLine(crmSvc.LastCrmException.StackTrace);  
  
    return;  
}  
```  
  
### <a name="see-also"></a>Vea también  

[Ejemplo: inicio rápido para la API de útiles de XMR](sample-quick-start-xrm-tooling-api.md)<br />
[Usar API de útiles de XRM para ejecutar acciones en CDS para aplicaciones](use-xrm-tooling-execute-actions.md)