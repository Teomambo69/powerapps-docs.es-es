---
title: 'Ejemplo: consulte las horas laborables de varios usuarios (Common Data Service para aplicaciones) | Microsoft Docs'
description: En este ejemplo se muestra cómo consultar las horas laborables de varias horas
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
# <a name="sample-query-the-working-hours-of-multiple-users"></a>Ejemplo: consultar las horas laborables de varios usuarios

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/sample-query-working-hours-multiple-users -->

Este ejemplo muestra cómo recuperar las horas de trabajo de varios usuarios utilizando el mensaje [QueryMultipleSchedulesRequest](https://docs.microsoft.com/en-us/dotnet/api/microsoft.crm.sdk.messages.querymultipleschedulesrequest?view=dynamics-general-ce-9). Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23).

Este ejemplo requiere usuarios adicionales que no están presentes en el sistema. Creación del usuario necesario manualmente **tal cual** se muestra en **Office 365** antes de ejecutar el ejemplo. Reemplace `yourorg` por el valor de `OrgName` de su organización.

**Nombre**: Kevin<br/>
**Apellidos**: Cook<br/>
**Rol de seguridad**: jefe de ventas<br/>
**Nombre de usuario**: kcook@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `QueryMultipleScheduleRequest` está diseñado para usarse en un escenario donde contiene los datos necesarios para buscar varios recursos durante el bloque de tiempo disponible que coincida con los parámetros específicos.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. Recupera la información de usuario actual y también el usuario, que ha creado manualmente en **Office 365**.

### <a name="demonstrate"></a>Demostración

1. El mensaje `QueryMultipleScheduleRequest` recupera las horas laborables del usuario actual y el usuario que ha creado manualmente.

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los registros creados en [Configuración](#setup).

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
