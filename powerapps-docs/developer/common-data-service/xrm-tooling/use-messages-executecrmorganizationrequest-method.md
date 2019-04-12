---
title: Utilizar mensajes con el método ExecuteCrmOrganizationRequest (Common Data Service)| Microsoft Docs
description: Obtenga más información sobre cómo usar mensajes con el método ExecuteCrmOrganizationRequest. Los ejemplos muestran cómo ejecutar los mensajes CreateRequest y RetrieveMultipleRequest mediante el método CrmServiceClient.String).
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 1ba60f67-522d-4540-a6f9-0787d7074a79
caps.latest.revision: 17
author: MattB-msft
ms.author: kvivek
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-messages-with-the-executecrmorganizationrequest-method"></a>Utilizar mensajes con el método ExecuteCrmOrganizationRequest

<!-- TODO:
In addition to using the <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> method, you can now use the <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmOrganizationRequest*> method to execute the xRM and Common Data Service Customer Engagement messages. Similar to the <xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> method, the <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmOrganizationRequest*> method takes a message request class as a parameter and returns a message response class. For a list of messages that you can execute using the <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmOrganizationRequest*> method, see [xRM Messages in the Organization Service](../org-service/xrm-messages-organization-service.md) and [Common Data Service Messages in the Organization Service](../org-service/organization-service-messages.md).   -->
  
 Las siguientes muestras de código muestran cómo se pueden ejecutar mensajes mediante el método de <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmOrganizationRequest*>.  
  
## <a name="example-1-createrequest-message"></a>Ejemplo: 1 Mensaje de CreateRequest  

 La siguiente muestra de código demuestra cómo ejecutar el mensaje de <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> mediante el método <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmOrganizationRequest*>. . En este ejemplo, cree una cuenta y, a continuación, muestre el identificador en el objeto de respuesta.  
  
```csharp 
CrmServiceClient crmSvc = new CrmServiceClient(new System.Net.NetworkCredential("<UserName>", "<Password>", "<Domain>"),"<Server>", "<Port>", "<OrgName>");  
  
// Verify that you are connected.  
if (crmSvc != null && crmSvc.IsReady)  
{  
    //Display the CRM version number and org name that you are connected to.  
    Console.WriteLine("Connected to CRM! (Version: {0}; Org: {1}",   
    crmSvc.ConnectedOrgVersion, crmSvc.ConnectedOrgUniqueName);  
  
    CreateRequest request = new CreateRequest();  
    Entity newAccount = new Entity("account");  
    newAccount.Attributes.Add("name", "Sample Test Account");  
    request.Target = newAccount;  
    CreateResponse response = (CreateResponse)crmSvc.ExecuteCrmOrganizationRequest(request);  
  
    // Display the ID of the newly created account record.  
    Console.WriteLine("Account record created with the following ID: {0}", response.id.ToString());  
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
  
## <a name="example-2-retrievemultiplerequest"></a>Ejemplo 2: RetrieveMultipleRequest  

 La siguiente muestra de código demuestra cómo ejecutar el mensaje de <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest> mediante el método <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmOrganizationRequest*>. . En este ejemplo, ejecuta una solicitud de varias recuperaciones para recuperar todos los contactos del sistema y mostrar su nombre completo.  
  
```csharp  
CrmServiceClient crmSvc = new CrmServiceClient(new System.Net.NetworkCredential("<UserName>", "<Password>", "<Domain>"),"<Server>", "<Port>", "<OrgName>");  
  
// Verify that you are connected.  
if (crmSvc != null && crmSvc.IsReady)  
{  
    //Display the CRM version number and org name that you are connected to.  
    Console.WriteLine("Connected to CRM! (Version: {0}; Org: {1}",   
    crmSvc.ConnectedOrgVersion, crmSvc.ConnectedOrgUniqueName);  
  
    QueryExpression userSettingsQuery = new QueryExpression("contact");  
    userSettingsQuery.ColumnSet.AllColumns = true;  
    var retrieveRequest = new RetrieveMultipleRequest()  
    {  
        Query = userSettingsQuery  
    };  
    EntityCollection EntCol = (crmSvc.ExecuteCrmOrganizationRequest(retrieveRequest) as RetrieveMultipleResponse).EntityCollection;  
    foreach (var a in EntCol.Entities)  
    {  
        Console.WriteLine("Account name: {0} {1}", a.Attributes["firstname"], a.Attributes["lastname"]);  
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
  
### <a name="see-also"></a>Vea también  

<!-- TODO:
[Use Messages (Request and Response Classes) with the Execute Method](../org-service/use-messages-request-response-classes-execute-method.md)<br /> -->
[Uso de útiles XRM para conectarse a Common Data Service](use-crmserviceclient-constructors-connect.md)<br />
[Use la API de útiles XRM para ejecutar acciones en Common Data Service](use-xrm-tooling-execute-actions.md)
