---
title: 'Ejemplo: Eliminación en masa de registros exportados (Common Data Service para aplicaciones) | Microsoft Docs'
description: Este ejemplo muestra cómo realizar una eliminación en masa de registros
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-bulk-delete-exported-records"></a>Ejemplo: eliminación en masa de los registros exportados

Este ejemplo muestra cómo realizar una eliminación en masa de los registros que se exportaron anteriormente desde Common Data Service para aplicaciones mediante la opción **Exportar a Excel**. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/BulkDeleteExported).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `BulkDeleteRequest` está diseñado para usarse en un escenario donde contenga los datos necesarios para crear la solicitud de eliminación en masa.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. Consulta para que un usuario del sistema envíe un correo electrónico después de que la operación de solicitud de eliminación en masa se complete.
3. `BulkDeleteRequest` crea el proceso de eliminación en masa y establece las propiedades de la solicitud.
4. El método `CheckSuccess` consulta `BulkDeleteOperation` hasta que se ha completado o hasta que el tiempo asignado se agota. A continuación comprueba si se ha completado la operación.

### <a name="demonstrate"></a>Demostración

1. El método `PerformBulkDeleteBackup` realiza la operación de eliminación en masa en las actividades y oportunidades inactivas para quitarlas del sistema.

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup).

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
