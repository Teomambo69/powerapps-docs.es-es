---
title: Detección de datos duplicados con el servicio de organización (Common Data Service) | Microsoft Docs
description: El servicio de la organización le permite detectar registros duplicados en Common Data Service para mantener la integridad de los datos.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: cb2ecce70adaf47ea55117831d2ced866bce10f1
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "3109079"
---
# <a name="detect-duplicate-data-using-the-organization-service"></a>Detección de datos duplicados con el servicio de organización

El servicio de la organización de Common Data Service le permite detectar registros duplicados para mantener la integridad de los datos. Para obtener información detallada sobre Detección de datos duplicados usando código, consulte [Detectar datos duplicados con código](../detect-duplicate-data-with-code.md). 

> [!NOTE]
> Asegúrese de que existen reglas de detección de duplicados adecuadas. Common Data Service incluye reglas de detección de duplicados predeterminadas para cuentas, contactos y clientes potenciales, pero no para otros tipos de registros. Si desea que el sistema detecte duplicados para otros tipos de registro, deberá crear una nueva regla. <br/>- Para obtener información sobre cómo crear una regla de detección de duplicados usando la interfaz de usuario, consulte [Configurar reglas de detección de duplicados para mantener limpios los datos](/dynamics365/customer-engagement/admin/set-up-duplicate-detection-rules-keep-data-clean).<br/>- Para obtener información sobre cómo crear reglas de detección de duplicados usando código, consulte [Entidades de regla de duplicados](../duplicaterule-entities.md).


## <a name="use-retrieveduplicatesrequest-message-to-detect-duplicates-before-you-create-or-update-record"></a>Use el mensaje RetrieveDuplicatesRequest para detectar duplicados antes de crear o actualizar un registro

Puede mediante programación comprobar si una entidad es un duplicado o será un duplicado antes de crearla o actualizarla con la clase <xref:Microsoft.Crm.Sdk.Messages.RetrieveDuplicatesRequest>.

```csharp
var account = new Account();
account.Name = "Sample Account";

var request = new RetrieveDuplicatesRequest()
{
    BusinessEntity = account,
    MatchingEntityName = account.LogicalName,
    PagingInfo = new PagingInfo() { PageNumber = 1, Count = 50 }
};

var response = (RetrieveDuplicatesResponse)svc.Execute(request);

if (response.DuplicateCollection.Entities.Count >= 1)
{
    Console.WriteLine("{0} Duplicate records found.", response.DuplicateCollection.Entities.Count);
}
```

## <a name="use-suppressduplicatedetection-parameter-to-throw-errors-when-you-create-or-update-record"></a>Use el parámetro SuppressDuplicateDetection para devolver errores cuando se crea o se actualiza el registro

Si desea que la plataforma genere un error cuando un nuevo registro que cree resulta ser un registro duplicado, o actualiza un registro existente para evaluar las reglas de detección de duplicados, debe usar las clases <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> o <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> con el método <xref:Microsoft.Xrm.Sdk.IOrganizationService> .<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> y aplicar el parámetro `SuppressDuplicateDetection` establecido en `false`.

El siguiente código lanzará una excepción `InvalidOperationException` con el mensaje `A record was not created or updated because a duplicate of the current record already exists.` cuando las siguientes condiciones se cumplan:

- La detección de duplicados está activada para el entorno cuando se crea o se actualiza un registro.
- La entidad Cuenta tiene habilitada la detección de duplicados
- Se publica una regla de detección de duplicados que comprueba si el valor del nombre de la cuenta es un exacta coincidencia de un registro existente
- Hay una cuenta existente con el nombre `Sample Account`

```csharp
var account = new Account();
account.Name = "Sample Account";

var request = new CreateRequest();
request.Target = account;
request.Parameters.Add("SuppressDuplicateDetection", false);

try
{
    svc.Execute(request);
}
catch (FaultException<OrganizationServiceFault> ex)
{
    switch (ex.Detail.ErrorCode)
    {
        case -2147220685:
            throw new InvalidOperationException(ex.Detail.Message);
        default:
            throw ex;
    }
}
```

### <a name="see-also"></a>Vea también
[Detección de datos duplicados con la API web](../webapi/manage-duplicate-detection-create-update.md)

