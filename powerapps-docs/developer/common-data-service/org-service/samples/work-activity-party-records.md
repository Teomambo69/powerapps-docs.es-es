---
title: 'Ejemplo: Trabajar con registros de grupos de actividad (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo trabajar con registros del grupo de actividad.
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
# <a name="sample-work-with-activity-party-records"></a>Ejemplo: trabajar con registros de grupo de actividad

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-work-activity-party-records -->

Este código de ejemplo muestra cómo trabajar con registros del grupo de actividad. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ActivityPartyRecords).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Este ejemplo crea algunos datos de ejemplo, para trabajar con registros de grupos de actividad. 

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
1. Crea tres registros de contactos que se necesitan para este ejemplo.


### <a name="demonstrate"></a>Demostración

1. Recupera los registros de contacto que se crean en la [Configuración](#setup). 
2. Crea los registros de grupos de actividad para cada contacto.
3. También crea actividad Carta y establece los campos **De** y **Para** con las entidades de grupo de actividad respectivas.

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los registros creados durante la [Configuración](#setup).

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
