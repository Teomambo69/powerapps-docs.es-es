---
title: Usar herramientas XRM para ejecutar acciones en Common Data Service| MicrosoftDocs
description: El objeto de clase CrmServiceClient se puede usar para realizar, crear, recuperar, actualizar y eliminar operaciones de datos de Dynamics 365
ms.custom: ''
ms.date: 03/20/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 72e9238d-e0fb-453b-b1ab-3a15ffb19838
caps.latest.revision: 13
ms.author: nabuthuk
manager: kvivek
author: Nkrb
search.audienceType:
- developer
search.app:
- D365CE
ms.openlocfilehash: ff161483f631fbd1673f36465041c5e0dbc0ac8c
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749638"
---
# <a name="use-xrm-tooling-to-execute-a-web-request-against-web-api"></a>Utilizar útiles de XRM para ejecutar una solicitud web con la API web

El objeto de clase <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> se usa para realizar acciones en los datos de Dynamics 365, como crear, actualizar, recuperar o eliminar datos.

Ahora puede usar el <!--<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmWebRequest>--> método para ejecutar una solicitud web con la API web de XRM.

El siguiente código de ejemplo demuestra cómo puede ejecutar una solicitud web mediante <!--<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmWebRequest>--> . 

>[!NOTE]
> Este método solo es aplicable cuando se especifica el tipo de autenticación como `OAuth` o `Certificate`.

## <a name="create-a-record"></a>Crear un registro

El siguiente código de ejemplo demuestra cómo crear un registro mediante <!--<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmWebRequest>--> . En este ejemplo, creará una cuenta y, a continuación, muestre el identificador en el objeto de respuesta.  

```csharp
 Dictionary<string, List<string>> ODataHeaders = new Dictionary<string, List<string>>() {
        { "Accept", new List<string>() { "application/json" } },
        {"OData-MaxVersion", new List<string>(){"4.0"}},
        {"OData-Version", new List<string>(){"4.0"}}
      };

using (CrmServiceClient svc = new CrmServiceClient(conn))
 {
    if (svc.IsReady)
    {
      HttpResponseMessage response = svc.ExecuteCrmWebRequest(HttpMethod.Get, "accounts?$select=name", "{ \"name\":\"Test Account\"}", ODataHeaders, "application/json");

    if (response.IsSuccessStatusCode)
     {
        var accountUri = response.Headers.GetValues("OData-EntityId").FirstOrDefault();
        Console.WriteLine("Account URI: {0}", accountUri);
       }
    else
     {
       Console.WriteLine(response.ReasonPhrase);
        }

  }
    else
      {
        Console.WriteLine(svc.LastCrmError);
           }
}
```