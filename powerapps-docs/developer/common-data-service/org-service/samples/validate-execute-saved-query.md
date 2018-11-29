---
title: 'Ejemplo: Validar y ejecutar consulta guardada (Common Data Service para aplicaciones) | Microsoft Docs'
description: Este ejemplo muestra cómo validar y ejecutar una consulta guardada.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-validate-and-execute-a-saved-query"></a>Ejemplo: validar y ejecute una consulta guardada

<!-- Needs supporting conceptual topic 
https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/org-service/sample-validate-execute-saved-query
-->
Este ejemplo muestra cómo usar el mensaje [IOrganizationService.ValidateSavedQueryRequest](https://docs.microsoft.com/en-us/dotnet/api/microsoft.crm.sdk.messages.validatesavedqueryrequest?view=dynamics-general-ce-9) para validar una consulta FetchXML y, a continuación, usar el mensaje [IOrganizationService.ExecuteByIdSavedQueryRequest](https://docs.microsoft.com/en-us/dotnet/api/microsoft.crm.sdk.messages.executebyidsavedqueryrequest?view=dynamics-general-ce-9) para ejecutar la consulta. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ValidateandExecuteSavedQuery).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]


## <a name="what-this-sample-does"></a>Qué hace este ejemplo

La clase `ValidateSavedQueryRequest` está diseñado para usarse en un escenario donde contenga los datos necesarios para validar una consulta guardada (vista). 

La clase `ExecuteByIdSavedQueryRequest` está diseñado para usarse en un escenario donde contenga los datos necesarios para ejecutar una consulta guardada (vista) que tiene el ID especificado.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
1. El método `Account` crea 3 registros de cuenta.
1. El método `SavedQuery` crea una consulta guardada.
1. El método `UserQuery` crea una consulta de usuario.


### <a name="demonstrate"></a>Demostración
1. El método `ValidateSavedQueryRequest` crea la solicitud de validación.
1. El método `ExecuteByIdSavedQueryRequest` ejecuta la consulta guardada.

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar todos los datos creados en el ejemplo.

La eliminación es opcional en caso de que desee examinar los datos creados por el ejemplo. Puede eliminar manualmente los datps para obtener los mismos resultados.
