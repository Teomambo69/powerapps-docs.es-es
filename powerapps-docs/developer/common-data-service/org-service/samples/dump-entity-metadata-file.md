---
title: 'Ejemplo: volcar metadatos de entidad en un archivo (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo escribir todos los metadatos de la entidad en un archivo XML.
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
ms.openlocfilehash: 007ac9701350f5b6ae86b411898f5190ad880816
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749901"
---
# <a name="sample-dump-entity-metadata-to-a-file"></a>Ejemplo: volcar metadatos de entidad en un archivo

Este ejemplo muestra cómo escribir todos los metadatos de la entidad en un archivo `XML`. Utiliza el mensaje [RetrieveAllEntitiesRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.retrieveallentitiesrequest?view=dynamics-general-ce-9).

El siguiente ejemplo crea un nuevo archivo en `\Entities\bin\Debug\EntityInfo.xml`. Puede abrir este archivo en Office Excel para ver un informe tabular. Es posible que necesite esta información para descubrir el código de tipo de entidad para una entidad personalizada para usar en los informes. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/DumpEntityMetadata).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `RetrieveAllEntitiesRequest` está diseñado para usarse en un escenario con los datos necesarios para recuperar la información de metadatos sobre todas las entidades.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.


### <a name="demonstrate"></a>Demostración

1. El método `RetrieveAllEntitiesRequest` recupera los metadatos. 
1. `StreamWriter` crea una instancia de StreamWriter para escribir el texto en un archivo.

### <a name="clean-up"></a>Limpiar

1. En este ejemplo no crea ningún registro. No es necesario ninguna limpieza.


