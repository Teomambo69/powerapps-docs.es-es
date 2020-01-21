---
title: " Volcar relaciones de entidad a un archivo (Common Data Service) | Microsoft Docs"
description: Este ejemplo muestra cómo volcar relaciones de entidad a un archivo.
ms.custom: ''
ms.date: 12/20/2019
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
ms.openlocfilehash: 542abdd52320d866ff2bcd0ff65167bf8f3fc071
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934320"
---
# <a name="dump-entity-relationships-information-to-a-file"></a>Volcar la información de privilegios de entidad a un archivo

Este ejemplo muestra cómo escribir todos los metadatos de atributo en un archivo `XML`. Utiliza el mensaje [RetrieveAllEntitiesRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.retrieveallentitiesrequest?view=dynamics-general-ce-9). Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/DumpEntityRelationShips).

El siguiente ejemplo crea un nuevo archivo en `\DumpEntityRelationShips\bin\Debug\RelationshipInfo.xml`. Puede abrir este archivo en **Office Excel** para ver un informe tabular. 

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `RetrieveAllEntitiesRequest` está diseñado para usarse en un escenario con los datos necesarios para recuperar la información de metadatos sobre todas las entidades.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. El método `RetrieveAllEntitiesRequest` recupera los metadatos. 
1. `StreamWriter` crea una instancia de StreamWriter para escribir el texto en un archivo.

### <a name="clean-up"></a>Limpiar

En este ejemplo no crea ningún registro. No es necesario ninguna limpieza.
