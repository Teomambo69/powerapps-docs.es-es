---
title: 'Ejemplo: Importe archivos como recursos web (Common Data Service) | Microsoft Docs'
description: En este ejemplo se muestra cómo importar archivos como recursos web
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
ms.openlocfilehash: d73d2d7fa70998ceedc2cf9f833201a92c32c7e4
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934581"
---
# <a name="sample-import-files-as-web-resources"></a>Ejemplo: importar archivos como recursos web 

En este ejemplo se muestra cómo importar archivos como recursos web. Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ImportWebResources).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Este ejemplo muestra cómo usar el parámetro opcional de `SolutionUniqueName` para asociar un recurso web con una solución específica cuando se crea.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. La clase `CreateRequiredRecords` crea un editor y una solución necesaria para la muestra al agregar los recursos web.


### <a name="demonstrate"></a>Demostración

1. El método `XDocument` lee los datos descriptivos de los archivos XML. 
1. El `WebResource` se utiliza para establecer las propiedades del recurso web.
1. El método `CreateRequest` se utiliza para agregar parámetros opcionales.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.

