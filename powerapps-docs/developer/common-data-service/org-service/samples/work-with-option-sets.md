---
title: 'Ejemplo: trabajar con conjuntos de opciones (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo trabajar con un conjunto de opciones globales
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
ms.openlocfilehash: d9319235820f973a760784c140e445f0835b0356
ms.sourcegitcommit: 3bf59896a98e5f01289a2489e185f27518aeaec3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2020
ms.locfileid: "2956348"
---
# <a name="work-with-option-sets"></a>Trabajar con conjuntos de opciones

Este ejemplo muestra cómo trabajar con conjuntos de opciones. Normalmente, usa conjuntos de opciones globales para definir campos de manera que los campos diferentes puedan compartir el mismo conjunto de opciones, que se mantiene en una ubicación. A diferencia de conjuntos de opciones locales que se definen solo para un atributo específico, puede volver a usar conjuntos de opciones globales. También los verá usados en los parámetros de solicitudes de manera similar a una enumeración.

Cuando define un conjunto de opciones glogal mediante [Microsoft Docs](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.createoptionsetrequest?view=dynamics-general-ce-9), se recomienda dejar que el sistema asigne un valor. Realice esta acción al pasar un valor null al crear la nueva instancia de `OptionMetadata`. Al definir una opción, contendrá un determinada prefijo de valor de opción específico del contexto del editor establecido para la solución en la que se crea el conjunto de opciones. Este prefijo ayuda a reducir la oportunidad de crear conjuntos de opciones duplicados para una solución administrada, y en cualquier conjunto de opciones que están definidos en organizaciones donde está instalada la solución administrada. Para obtener más información, consulte [Combinar opciones del conjunto de opciones](https://docs.microsoft.com/powerapps/developer/common-data-service/understand-managed-solutions-merged#merge-option-set-options).

Use las siguientes clases de solicitud de mensajes para trabajar con conjuntos de opciones globales:

- [CreateOptionSetRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.createoptionsetrequest?view=dynamics-general-ce-9)
- [DeleteOptionSetRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.deleteoptionsetrequest?view=dynamics-general-ce-9)
- [RetrieveAllOptionSetsRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.retrievealloptionsetsrequest?view=dynamics-general-ce-9)
- [RetrieveOptionSetRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.retrieveoptionsetrequest?view=dynamics-general-ce-9)
- [UpdateOptionSetRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.updateoptionsetrequest?view=dynamics-general-ce-9)

Use las siguientes clases de solicitud de mensajes tanto con conjuntos de opciones globales como locales:

- [DeleteOptionValueRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.deleteoptionvaluerequest?view=dynamics-general-ce-9)
- [InsertOptionValueRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.insertoptionvaluerequest?view=dynamics-general-ce-9)
- [InsertStatusValueRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.insertstatusvaluerequest?view=dynamics-general-ce-9)
- [OrderOptionRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.orderoptionrequest?view=dynamics-general-ce-9)
- [UpdateOptionValueRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.updateoptionvaluerequest?view=dynamics-general-ce-9)
- [UpdateStateValueRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.updatestatevaluerequest?view=dynamics-general-ce-9)

Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/WorkWithOptionSets).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Los mensajes `CreateOptionSetRequest`, `DeleteOptionSetRequest`, `RetrieveOptionSetRequest` y `UpdateOptionSetRequest` están diseñados para usarse en un escenario donde contengan los datos necesarios para trabajar con conjuntos de opciones.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. El método `CreateOptionSetRequest` crea un conjunto de opciones globales. Necesita establecer el parámetro `IsGlobal=true`.  
2. El método `CreateAttributeRequest` crea una lista de selección vinculada a conjunto de opciones.
3. El método `UpdateOptionSetRequest` actualiza la información básica de un conjunto de opciones.
4. El método `PublishXmlRequest` publica el conjunto de opciones.
5. El método `InsertOptionValueRequest` inserta una nueva opción en un conjunto de opciones globales.
6. El método `RetrieveOptionSetRequest` recupera el conjunto de opciones global por su nombre.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en la [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
