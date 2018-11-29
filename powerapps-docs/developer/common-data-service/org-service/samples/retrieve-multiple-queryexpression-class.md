---
title: 'Ejemplo: Recuperar varios con la clase QueryExpression (Common Data Service para aplicaciones) | Microsoft Docs'
description: En este ejemplo se muestra cómo crear una tarea para un fax mediante usando QueryExpression.
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
# <a name="sample-retrieve-multiple-with-the-queryexpression-class"></a>Ejemplo: Recuperación múltiple con la clase de QueryExpression

<!-- Re-title? This is really about retrieving  related records 
https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/org-service/sample-retrieve-multiple-queryexpression-class
-->
Este ejemplo muestra cómo recuperar múltiples entidades utilizando el método [IOrganizationService.RetrieveMultiple(QueryBase)](https://docs.microsoft.com/en-us/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrievemultiple?view=dynamics-general-ce-9#Microsoft_Xrm_Sdk_IOrganizationService_RetrieveMultiple_Microsoft_Xrm_Sdk_Query_QueryBase_)con [QueryExpression](https://docs.microsoft.com/en-us/dotnet/api/microsoft.xrm.sdk.query.queryexpression?view=dynamics-general-ce-9) junto con sus columnas de entidades relacionadas. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveMultipleByQueryExpression).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]


## <a name="what-this-sample-does"></a>Qué hace este ejemplo

La clase `QueryExpression` está diseñada para usarse en un escenario donde contiene una consulta compleja que se expresa en una jerarquía de expresiones.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración
1. Crea varias cuentas con contactos principales.
1. La clase `QueryExpression` crea una expresión de consulta que especifica el alias de la entidad de vínculo y las columnas de entidad de vínculo que desea devolver.
### <a name="clean-up"></a>Limpiar

1. No es necesaria ninguna limpieza.
