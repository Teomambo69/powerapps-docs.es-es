---
title: Usar útiles de XRM para recuperar datos (Common Data Service)| Microsoft Docs
description: Utilizar la clase CrmServiceClient para recuperar datos de Common Data Service
ms.custom: ''
ms.date: 03/27/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 2afc057e-8f70-4bea-bad4-d01e18ed92fd
caps.latest.revision: 14
author: MattB-msft
ms.author: nabuthuk
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8de9abf4a377e91ad936a21429902ac426a088ae
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154848"
---
# <a name="use-xrm-tooling-to-retrieve-data"></a>Utilizar los útiles de XRM para recuperar datos

Existen muchos métodos disponibles en la clase de <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> para recuperar datos en Common Data Service. Los siguientes ejemplos muestran cómo puede recuperar un registro por identificador o consulta FetchXML.  
  
## <a name="getentitydatabyid"></a>GetEntityDataById  

Este método busca una entidad por el identificador especificado. En este ejemplo, especificamos null para el valor de la lista de campo para recuperar todos los atributos del registro de entidad especificado (cuenta) y, a continuación, mostramos el nombre del registro de cuenta recuperado.  
  
```csharp  
CrmServiceClient svc = new CrmServiceClient(connectionstring);  
  
// Verify that you are connected.  
if (svc != null && svc.IsReady)  
{  
    Dictionary<string, object> data = svc.GetEntityDataById("account", <Account_ID>, null);  
    foreach (var pair in data)  
    {  
        if (pair.Key == "name")  
        {  
            Console.WriteLine("Name of the account is {0}", pair.Value);  
        }  
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
  
## <a name="getentitydatabyfetchsearchec"></a>GetEntityDataByFetchSearchEC  

Este método busca la entidad en función de la consulta `FetchXML` especificada. En este ejemplo, recuperamos y presentamos el recuento de todos los registros de cuenta del sistema.  
  
```csharp  
CrmServiceClient svc = new CrmServiceClient(connectionstring);  
  
// Verify that you are connected.  
if (svc != null && svc.IsReady)  
{   
    string fetchXML =   
        @"<fetch version='1.0' output-format='xml-platform' mapping='logical' distinct='false' returntotalrecordcount='true' >  
            <entity name='account'>  
              <attribute name='accountid' />  
            </entity>  
        </fetch>";  
    var queryResult = crmSvc.GetEntityDataByFetchSearchEC(fetchXML);  
    if (queryResult != null)  
    {  
        Console.WriteLine(String.Format("Account Records Count : {0}", queryResult.TotalRecordCount));  
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

[Ejemplo: inicio rápido para la API de útiles de XMR](sample-quick-start-xrm-tooling-api.md)<br />
[Usar útiles XRM para conectarse a Common Data Service](use-crmserviceclient-constructors-connect.md)<br />
[Usar la API de útiles XRM para ejecutar acciones en Common Data Service](use-xrm-tooling-execute-actions.md)
