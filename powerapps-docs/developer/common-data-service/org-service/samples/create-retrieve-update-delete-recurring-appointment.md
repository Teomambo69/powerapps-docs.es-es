---
title: 'Ejemplo: operaciones CRUD en una cita periódica (Common Data Service para aplicaciones) | Microsoft Docs'
description: Este ejemplo muestra cómo realizar operaciones CRUD en citas periódicas
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
# <a name="sample-create-retrieve-update-and-delete-a-recurring-appointment"></a>Ejemplo: crear, recuperar, actualizar y eliminar una cita periódica

Este ejemplo muestra cómo crear, recuperar, actualizar, eliminar una serie de citas periódicas. Este ejemplo usa los siguientes métodos habituales:

- [IOrganizationService.Create](https://docs.microsoft.com/en-us/dotnet/api/microsoft.xrm.sdk.iorganizationservice.create?view=dynamics-general-ce-9)
- [IOrganizationService.Retrieve](https://docs.microsoft.com/en-us/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrieve?view=dynamics-general-ce-9)
- [IOrganizationService.Update](https://docs.microsoft.com/en-us/dotnet/api/microsoft.xrm.sdk.iorganizationservice.update?view=dynamics-general-ce-9)
- [IOrganizationService.Delete](https://docs.microsoft.com/en-us/dotnet/api/microsoft.xrm.sdk.iorganizationservice.delete?view=dynamics-general-ce-9)

Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/CRUDRecurringAppointment).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `IOrganizationService` está diseñado para usarse en un escenario donde contiene datos que proporcionan acceso mediante programación a los metadatos y los datos de una organización.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. Define tipos anónimos para definir los posibles valores de patrón periódico, los valores posibles por días de la semana y los valores posibles para el tipo de finalización de patrón de reglas. 
1. El método `RecurringAppointmentMaster` crea una cita periódica.
1. El método `QueryExpression` recupera la cita periódica recién creada.
1. El método `Update` actualiza el tema, el número de apariciones a 5, el intervalo de Cita a 2 para la cita periódica recuperada.


### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los registros creados en la [Configuración](#setup).

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.


