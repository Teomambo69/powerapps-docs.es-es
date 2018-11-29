---
title: 'Ejemplo: consultar las horas laborables de un usuario (Common Data Service para aplicaciones) | Microsoft Docs'
description: Este ejemplo muestra cómo recuperar las horas laborables de un usuario
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
# <a name="sample-query-the-working-hours-of-a-user"></a>Ejemplo: consultar las horas laborables de un usuario

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/sample-query-working-hours-user -->

Este ejemplo muestra cómo recuperar las horas laborables de un usuario que usa el mensaje [QueryScheduleRequest](https://docs.microsoft.com/en-us/dotnet/api/microsoft.crm.sdk.messages.queryschedulerequest?view=dynamics-general-ce-9). Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/QueryWorkingHours
).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `QueryScheduleRequest` está diseñado para usarse en un escenario donde contiene los datos necesarios para buscar el recurso especificado durante un bloque de tiempo disponible que coincida con los parámetros específicos.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. El mensaje `WhoAMIRequest` recopila información del usuario actual.
2. El mensaje `QueryScheduleRequest` recupera el horas laborables del usuario actual.

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup).
    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
