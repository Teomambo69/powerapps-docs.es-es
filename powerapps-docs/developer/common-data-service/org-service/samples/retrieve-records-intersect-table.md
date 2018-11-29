---
title: 'Ejemplo: Recuperar registros de una tabla de intersección(Common Data Service para aplicaciones) | Microsoft Docs'
description: Este ejemplo muestra cómo recuperar registros de una tabla de intersección.
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
# <a name="sample-retrieve-records-from-an-intersect-table"></a>Ejemplo: recuperar registros de una tabla de intersección

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/org-service/sample-retrieve-records-intersect-table -->Este ejemplo muestra cómo recuperar los registros de una tabla de intersección. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveRecordsFromIntersectTable).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `QueryExpression` está diseñado para usarse en un escenario que contiene consultas compleja en una jerarquía de expresiones.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización. 
1. El método `CreateRequireRecords` crea registros de entidad usados por el ejemplo.
1. El mensaje `QueryExpression` sirve para recuperar la unidad de negocio predeterminada necesaria para crear el equipo.
1. La `WhoAmIRequest` obtiene el GUID del usuario actual.
1. El mensaje `Role` crea instancias de un registro de entidad de rol y establece sus valores de la propiedad.
1. La `AssociateRequest` asigna al usuario el rol Administrador. 

### <a name="demonstrate"></a>Demostración

1. La `QueryExpression` recupera los registros de una tabla de intersección.
1. La `RetrieveMultipleRequest` crea la solicitud Fetch y obtiene los resultados.
### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los registros creados en la [Configuración](#setup).

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
