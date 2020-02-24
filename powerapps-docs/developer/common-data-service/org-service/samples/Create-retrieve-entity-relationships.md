---
title: 'Ejemplo: Crear y recuperar las relaciones entre entidades (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo crear y recuperar relaciones entre entidades.
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
ms.openlocfilehash: 9542b7b9b76530cdfc40318fbd237657d7dc6134
ms.sourcegitcommit: 3bf59896a98e5f01289a2489e185f27518aeaec3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2020
ms.locfileid: "2956346"
---
# <a name="create-and-retrieve-entity-relationships"></a>Crear y recuperar relaciones entre entidades

Este ejemplo muestra cómo crear y recuperar relaciones entre entidades. Los siguientes métodos se utilizan para crear y recuperar Relaciones:

- [CreateOneToManyRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.createonetomanyrequest?view=dynamics-general-ce-9)
- [CreateManyToManyRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.createmanytomanyrequest?view=dynamics-general-ce-9)
- [CanBeReferencedRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.canbereferencedrequest?view=dynamics-general-ce-9)
- [CanBeReferencingRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.canbereferencingrequest?view=dynamics-general-ce-9)
- [CanManyToManyRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.canmanytomanyrequest?view=dynamics-general-ce-9)
- [RetrieveRelationshipRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.retrieverelationshiprequest?view=dynamics-general-ce-9)

Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/CreateRetrieveEntityRelationships).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Los mensajes `CreateOneToManyRequest`, `CreateManyToManyRequest`, `CanManyToManyRequest`, `CreateOneToManyRequest`, `CanBeReferencedRequest`, `CanBeReferencingRequest` y `RetrieveRelationshipRequest` están diseñados para usarse en un escenario donde contengan los datos necesarios para crear y recuperar relaciones de entidades.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. El método `CreateOneToManyRequest` crea una nueva relación 1:N (uno a varios). 
2. El método `CreateManyToManyRequest` crea una nueva relación N:N (varios a varios).
3. El método `EligibleCreateManyToManyRelationship` verifica si las entidades pueden participar en la relación N:N.
4. El método `RetrieveRelationshipRequest` recupera las dos relaciones entre entidades creadas anteriormente.


### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en la [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
