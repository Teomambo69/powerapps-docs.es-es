---
title: 'Ejemplo: Insertar o actualizar registro mediante Upsert (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo insertar o actualizar registros mediante el mensaje de Upsert.
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
# <a name="sample-insert-or-update-a-record-using-upsert"></a>Ejemplo: Insertar o actualizar un registro mediante Upsert

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-insert-update-record-upsert -->

Este código de ejemplo muestra cómo insertar o actualizar registros mediante el mensaje de [UpsertReques](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.upsertrequest?view=dynamics-general-ce-9). Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/InsertRecordUsingUpsert).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `UpsertRequest` está diseñado para usarse en un escenario donde contenga los datos necesarios para actualizar o insertar un registro.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprueba la versión actual de la organización.
1. Importación de una solución administrada (UpsertSample_1_0_0_0_managed.zip) que cree una entidad `sample_product` que tenga una clave alternativa denominada `sample_productcode`. Compruebe que los índices para admitir la clave alternativa estén activos.

### <a name="demonstrate"></a>Demostración

1. El método `ProcessUpsert` procesa datos en `newsampleproduct.xml` para representar nuevos productos y crea 13 nuevos registros.
1. La segunda vez que se llama al método `ProcessUpsert`, este procesa datos en el archivo `updatedsampleproduct.xml` para representar actualizaciones a productos creados anteriormente. 
1. El método `UpsertRequest` crea 6 registros actualizados. 

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar la solución administrada creada en [Configuración](#setup).

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
