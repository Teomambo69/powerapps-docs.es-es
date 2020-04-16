---
title: 'Ejemplo: Usar QueryExpresion con una cookie de paginación (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo usar la cookie de paginación en una QueryExpresion
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
ms.openlocfilehash: 4e130a5c03567771f38a201ada5ef4e7457bb724
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155524"
---
# <a name="sample-use-queryexpression-with-a-paging-cookie"></a>Ejemplo: usar QueryExpression con una cookie de paginación

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/sample-use-queryexpression-with-a-paging-cookie -->

Este ejemplo muestra cómo usar la cookie de paginación en una consulta de QueryExpression para recuperar páginas sucesivas de resultados de la consulta. Usa el método [IOrganizationService.RetrieveMultiple](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrievemultiple?view=dynamics-general-ce-9). Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/UseQueryExpressionwithPaging).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El método `IOrganizationService.RetreiveMultiple` está diseñada para usarse en un escenario donde recupera una colección de registros.
## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
1. El método `Account` crea un registro de cuenta primaria y 10 registros de cuentas secundarias.

### <a name="demonstrate"></a>Demostración

1. La `ConditionExpress` define expresión de condición para recuperar los registros.
1. El método `OrderExpression` define la expresión de orden para recuperar los registros.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar todos los datos creados en el ejemplo. La eliminación es opcional en caso de que desee examinar los datos creados por el ejemplo. Puede eliminar manualmente los datos para obtener los mismos resultados.
