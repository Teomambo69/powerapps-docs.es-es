---
title: 'Ejemplo: Sincronizar datos con sistemas externos usando el sistema de seguimiento de cambios (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo recuperar cambios de una entidad y sincronizar datos con sistemas externos.
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
# <a name="sample-synchronize-data-with-external-systems-using-change-tracking"></a>Ejemplo: Sincronizar datos con sistemas externos utilizando seguimiento de cambios

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-synchronize-data-external-systems-using-change-tracking -->

Este código de ejemplo muestra cómo recuperar cambios de una entidad y sincronizar datos con sistemas internos mediante el mensaje `RetrieveEntityChanges` con las clases [RetrieveEntityChangesRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.retrieveentitychangesrequest) y [RetrieveEntityChangesResponse](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.retrieveentitychangesresponse). Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/Changetracking).

Para obtener más información acerca de la característica que este ejemplo demuestra, consulte [Uso del seguimiento de cambios para sincronizar los datos con sistemas externos](https://docs.microsoft.com/powerapps/developer/common-data-service/use-change-tracking-synchronize-data-external-systems).
<!-- The link above won't work until the topic is published -->

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `RetrieveEntityChanges` está diseñada para usarse en un escenario donde los datos de un sistema externo se sincronizan y la capacidad de usar seguimiento de cambios se puede usar para detectar y conciliar cambios de datos.

Sin un sistema aparte necesario para replicar completamente este escenario, este ejemplo simula el escenario realizando dos solicitudes. Entre las solicitudes se cambian algunos datos para que la segunda solicitud devuelva datos sobre qué cambió a lo largo del tiempo.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Importación de una solución administrada (ChangeTrackingSample_1_0_0_0_managed.zip) que cree una entidad `sample_book` que tenga una clave alternativa denominada `sample_bookcode`. Compruebe que los índices para admitir la clave alternativa estén activos
1. Se crean 10 registros de entidad iniciales sample_book para que puedan seguirse los cambios en esas entidades.

### <a name="demonstrate"></a>Demostración

1. Realizar la solicitud inicial y almacenar en caché los resultados, incluido el `DataToken`
1. Actualizar los registros creados en [Configuración](#setup)
1. Realice una segunda solicitud, esta vez pasando la `DataVersion` con el valor de `DataToken` recuperado de la solicitud inicial.
1. Mostrar los cambios de entidad devueltos por la segunda solicitud

### <a name="clean-up"></a>Limpiar

1. Muestre una opción para eliminar la solución administrada importada en [Configuración](#setup), que quita la entidad `sample_book` y todos los datos creadas en el ejemplo.

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente el `ChangeTrackingSample` para obtener el mismo resultado.
