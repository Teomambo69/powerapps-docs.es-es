---
title: Utilizar útiles de XRM para actualizar datos (Common Data Service para aplicaciones)| Microsoft Docs
description: Utilizar la clase CrmServiceClient para actualizar datos en CDS para aplicaciones
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 8ec3d4ca-d836-4e7e-b2bf-9d9f806bd145
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
# <a name="use-xrm-tooling-to-update-data"></a>Usar útiles de XRM para actualizar los datos

Existen dos métodos disponibles en la clase <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> para actualizar datos en CDS para aplicaciones: <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.UpdateEntity(System.String,System.String,System.Guid,System.Collections.Generic.Dictionary{System.String,Microsoft.Xrm.Tooling.Connector.CrmDataTypeWrapper},System.String,System.Boolean,System.Guid)> y <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.UpdateStateAndStatusForEntity(System.String,System.Guid,System.String,System.String,System.Guid)>.  
  
Una acción de actualización que usa la API de los útiles de XRM requiere una carga de datos. La carga útil de datos requiere la forma de un objeto Dictionary\<string, CrmDataTypeWrapper>. <xref:Microsoft.Xrm.Tooling.Connector.CrmDataTypeWrapper> se usa para informes a la interfaz del tipo de control debe ser aplicado al punto de datos al que está haciendo referencia.  
  
## <a name="updateentity"></a>UpdateEntity  

Este es el método de delimitador para actualizar cualquier registro de CDS para aplicaciones, con la excepción del establecimiento del estado o del estado de un registro. Para usarlo, debe conocer la siguiente información: nombre de esquema de la entidad que desea actualizar, el campo de clave principal de la entidad que desea actualizar, el GUID del registro que desea actualizar y, por último, la matriz de carga de datos con la que desea actualizar.  
  
```csharp  
CrmServiceClient crmSvc = new CrmServiceClient(new System.Net.NetworkCredential("<UserName>", "<Password>", “<Domain>”),"<Server>", "<Port>", "<OrgName>");  
  
// Verify that you are connected  
if (crmSvc != null && crmSvc.IsReady)  
{  
    //Display the CRM version number and org name that you are connected to  
    Console.WriteLine("Connected to CRM! (Version: {0}; Org: {1}",   
    crmSvc.ConnectedOrgVersion, crmSvc.ConnectedOrgUniqueName);  
  
    // Update the account record  
    Dictionary<string, CrmDataTypeWrapper> updateData = new Dictionary<string, CrmDataTypeWrapper>();  
    updateData.Add("name", new CrmDataTypeWrapper("Updated Sample Account Name", CrmFieldType.String));  
    updateData.Add("address1_city", new CrmDataTypeWrapper("Boston", CrmFieldType.String));  
    updateData.Add("telephone1", new CrmDataTypeWrapper("555-0161", CrmFieldType.String));   
    bool updateAccountStatus = crmSvc.UpdateEntity("account","accountid",_accountId,updateData);  
  
    // Validate if the account record was updated successfully, and then display the updated information  
    if (updateAccountStatus == true)  
    {  
        Console.WriteLine("Updated the account details as follows:");  
        Dictionary<string, object> data = crmSvc.GetEntityDataById("account", accountId, null);  
        foreach (var pair in data)  
        {  
            if ((pair.Key == "name") || (pair.Key == "address1_city") || (pair.Key == "telephone1"))  
            {  
                Console.WriteLine(pair.Key.ToUpper() + ": " + pair.Value);  
            }  
        }  
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
  
## <a name="updatestateandstatusforentity"></a>UpdateStateAndStatusForEntity 
 
Este método se usa para establecer el estado de un registro en CDS para aplicaciones. Por ejemplo, todos los registros comienzan normalmente en un estado "abierto". El nombre del estado cambia en función del tipo de registro o incluso de las decisiones de los desarrolladores. Una oferta, por ejemplo, tiene varios estados posibles, **Borrador**, **Activo**, **Cerrar**, **Perdido**, **Ganado**.  
  
<!-- TODO:
> [!TIP]
>  You can use the OptionSets.cs file in the SDK\SampleCode\CS\HelperCode folder of the SDK download package to view and use the global option sets available for various entities in CDS for Apps. For more information about global option sets, see [Customize Global Option Sets](../org-service/customize-global-option-sets.md).   -->
  
Actualizar el estado de una entidad requiere que sepa cuál es el estado y de destino, por nombres o id. Los nombres y los id. se pueden encontrar consultando los metadatos de la entidad y mirando los campos de estado. En este ejemplo se mostrará cómo establecer el estado de un registro de cuenta en **Inactivo**.  
  
```csharp  
CrmServiceClient crmSvc = new CrmServiceClient(new System.Net.NetworkCredential("<UserName>", "<Password>", “<Domain>”),"<Server>", "<Port>", "<OrgName>");  
  
// Verify that you are connected  
if (crmSvc != null && crmSvc.IsReady)  
{   
    //Display the CRM version number and org name that you are connected to  
    Console.WriteLine("Connected to CRM! (Version: {0}; Org: {1}",  
    crmSvc.ConnectedOrgVersion, crmSvc.ConnectedOrgUniqueName);  
  
    // Here are the state and status code values  
    // statecode = 1 ( Inactive )   
    // statuscode = 2 ( Inactive )   
  
    crmSvc.UpdateStateAndStatusForEntity("account" , accountId , 1 , 2 );  
  
    // the same command using the second form of the method  
    crmSvc.UpdateStateAndStatusForEntity("account" , accountId , "Inactive" , "Inactive");  
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
[Use útiles de XRM para conectarse a CDS para aplicaciones](use-crmserviceclient-constructors-connect.md)<br />
[Usar API de útiles de XRM para ejecutar acciones en CDS para aplicaciones](use-xrm-tooling-execute-actions.md)<br />
<!-- TODO:
[Work with attribute metadata](../org-service/work-attribute-metadata.md) -->
