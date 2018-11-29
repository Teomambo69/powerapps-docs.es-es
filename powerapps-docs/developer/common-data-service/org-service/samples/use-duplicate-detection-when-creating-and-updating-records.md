---
title: 'Ejemplo: Usar detección de duplicados al crear y actualizar registros (Common Data Service para aplicaciones) | Microsoft Docs'
description: Este ejemplo muestra cómo invocar la detección de duplicados para crear y actualizar registros de entidad.
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
# <a name="sample-use-duplicate-detection-when-creating-and-updating-records"></a>Ejemplo: Uso de detección de duplicados para crear y actualizar registros

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/org-service/sample-use-duplicate-detection-when-creating-and-updating-records --> Este ejemplo muestra cómo invocar la detección de duplicados para crear y actualizar registros de entidad. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/UseDuplicatedetectionforCRUD).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]


## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El método `DuplicateRule` está diseñado para usarse en un escenario donde contenga los datos necesarios para crear la regla de detección de duplicados.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
1. El método `Account` crea un registro de cuenta. 
1. El método `DuplicateRule` creación una regla de detección de duplicados.
1. El método `DuplicateRuleCondition` creación condiciones de regla de detección de duplicados.
1. El método `PublishDuplicateRuleRequest` publica la regla de detección de duplicados creada anteriormente. Debe esperar que termine la operación de publicación, por lo que seguimos sondeando el estado de la regla hasta convertirse en `Published`.

### <a name="demonstrate"></a>Demostración
1. El método `Account` crea un registro de cuenta. 
1. El método `CreateRequest` crea la operación suprimiendo la detección de duplicados.
1. El método `UpdateRequest` actualiza el registro de cuenta recuperado con el nuevo número de cuenta.

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar todos los datos creados en el ejemplo.

La eliminación es opcional en caso de que desee examinar los datos creados por el ejemplo. Puede eliminar manualmente los datps para obtener los mismos resultados.
