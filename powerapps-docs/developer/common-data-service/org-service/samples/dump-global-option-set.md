---
title: " Volcar la información del conjunto de opciones globales en un archivo (Common Data Service) | Microsoft Docs"
description: Este ejemplo muestra cómo volcar el conjunto de opciones globales en un archivo.
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
ms.openlocfilehash: 17940374791955a43cc27a030bc14c9d9abc2e73
ms.sourcegitcommit: 3bf59896a98e5f01289a2489e185f27518aeaec3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2020
ms.locfileid: "2956356"
---
# <a name="dump-global-option-information-to-a-file"></a>Volcar la información de las opciones globales a un archivo

Este ejemplo muestra cómo escribir todos los metadatos globales de OptionSet en un archivo `XML`. Utiliza el mensaje [RetrieveAllOptionSetsRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.retrievealloptionsetsrequest?view=dynamics-general-ce-9). Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/DumpGlobalOptionSetInfo).

El siguiente ejemplo crea un nuevo archivo en `\DumpGlobalOptionSetInfo\bin\Debug\AllOptionSetValues.xml`. Puede abrir este archivo en **Office Excel** para ver un informe tabular. 

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `RetrieveAllOptionSetsRequest` está diseñado para usarse en un escenario con los datos necesarios para recuperar la información de metadatos sobre todos los metadatos del conjunto de opciones globales.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. El método `RetrieveAllOptionSetsRequest` recupera los metadatos. 
1. `StreamWriter` crea una instancia de StreamWriter para escribir el texto en un archivo.

### <a name="clean-up"></a>Limpiar

En este ejemplo no crea ningún registro. No es necesario ninguna limpieza.