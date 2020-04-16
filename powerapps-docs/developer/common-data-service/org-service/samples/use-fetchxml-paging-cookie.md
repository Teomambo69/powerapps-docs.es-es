---
title: 'Ejemplo: Usar FetchXML con una cookie de paginación (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo usar la cookie de paginación en una FetchXML
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 97fef0ab9a697653a9c00d2b9e78ce38144b7291
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155532"
---
# <a name="sample-use-fetchxml-with-a-paging-cookie"></a>Ejemplo: usar FetchXML con una cookie de paginación

<!-- This could be greatly simplified IMHO 
https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/sample-use-fetchxml-paging-cookie
-->
Este ejemplo muestra cómo usar la cookie de paginación en una consulta de FetchXML para recuperar páginas sucesivas de resultados de la consulta. Usa el método [IOrganizationService. RetrieveMultiple](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrievemultiple?view=dynamics-general-ce-9). Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/UseFetchXMLWithPaging).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El método `IOrganizationService.Retrieve` está diseñado para usarse en un escenario donde contiene datos que recuperan todos los registros.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
1. El método `Account` crea un registro de cuenta primaria y también 10 registros de cuentas secundarias.

### <a name="demonstrate"></a>Demostración

La `fetchXml` crea la cadena FetchXML para recuperar todas las cuentas secundarias a una cuenta primaria. Esta consulta de Fetch usa 1 marcador para especificar el Id. de cuenta principal para filtrar las cuentas necesarias.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar todos los datos creados en el ejemplo. La eliminación es opcional en caso de que desee examinar los datos creados por el ejemplo. Puede eliminar manualmente los datos para obtener los mismos resultados.

