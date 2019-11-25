---
title: Usar mensajes con el método ExecuteCrmOrganizationRequest (Common Data Service)| Microsoft Docs
description: Obtenga más información sobre cómo usar mensajes con el método ExecuteCrmOrganizationRequest. Los ejemplos muestran cómo ejecutar los mensajes CreateRequest y RetrieveMultipleRequest mediante el método CrmServiceClient.String).
ms.custom: ''
ms.date: 03/27/2019
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
ms.openlocfilehash: 02930412dfb6eb3825a9606befea3c24624914e2
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749643"
---
# <a name="use-messages-with-the-executecrmorganizationrequest-method"></a>Utilizar mensajes con el método ExecuteCrmOrganizationRequest
  
Las siguientes muestras de código muestran cómo se pueden ejecutar mensajes mediante el método de <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmOrganizationRequest*>.  
  
## <a name="example-1-createrequest-message"></a>Ejemplo: 1 Mensaje de CreateRequest  

 La siguiente muestra de código demuestra cómo ejecutar el mensaje de <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> mediante el método <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmOrganizationRequest*>. . En este ejemplo, cree una cuenta y, a continuación, muestre el identificador en el objeto de respuesta.  
  
```csharp 
CrmServiceClient svc = new CrmServiceClient(connectionstring);  
  
// Verify that you are connected.  
if (svc != null && svc.IsReady)  
{  
    var request = new CreateRequest();  
    var newAccount = new Entity("account");  
    newAccount.Attributes.Add("name", "Sample Test Account");  
    request.Target = newAccount;  
    var response = (CreateResponse)svc.ExecuteCrmOrganizationRequest(request);  
  
    // Display the ID of the newly created account record.  
    Console.WriteLine("Account record created with the following ID: {0}", response.id.ToString());  
}  
else  
{  
    // Display the last error.  
    Console.WriteLine("An error occurred: {0}", svc.LastCrmError);  
  
    // Display the last exception message if any.  
    Console.WriteLine(svc.LastCrmException.Message);  
    Console.WriteLine(svc.LastCrmException.Source);  
    Console.WriteLine(svc.LastCrmException.StackTrace);  
  
    return;  
}  
```  
  
## <a name="example-2-retrievemultiplerequest"></a>Ejemplo 2: RetrieveMultipleRequest  

 La siguiente muestra de código demuestra cómo ejecutar el mensaje de <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest> mediante el método <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmOrganizationRequest*>. . En este ejemplo, ejecuta una solicitud de varias recuperaciones para recuperar todos los contactos del sistema y mostrar su nombre completo.  
  
```csharp  
CrmServiceClient svc = new CrmServiceClient(connectionstring);  
  
// Verify that you are connected.  
if (svc != null && svc.IsReady)  
{  
  
    var userSettingsQuery = new QueryExpression("contact");  
    userSettingsQuery.ColumnSet.AllColumns = true;  
    var retrieveRequest = new RetrieveMultipleRequest()  
    {  
        Query = userSettingsQuery  
    };  
    EntityCollection EntCol = (svc.ExecuteCrmOrganizationRequest(retrieveRequest) as RetrieveMultipleResponse).EntityCollection;  
    foreach (var a in EntCol.Entities)  
    {  
        Console.WriteLine("Account name: {0} {1}", a.Attributes["firstname"], a.Attributes["lastname"]);  
    }  
}  
else  
{  
    // Display the last error.  
    Console.WriteLine("An error occurred: {0}", svc.LastCrmError);  
  
    // Display the last exception message if any.  
    Console.WriteLine(svc.LastCrmException.Message);  
    Console.WriteLine(svc.LastCrmException.Source);  
    Console.WriteLine(svc.LastCrmException.StackTrace);  
  
    return;  
}  
```  
  
### <a name="see-also"></a>Vea también  

[Usar útiles XRM para conectarse a Common Data Service](use-crmserviceclient-constructors-connect.md)<br />
[Usar la API de útiles XRM para ejecutar acciones en Common Data Service](use-xrm-tooling-execute-actions.md)
