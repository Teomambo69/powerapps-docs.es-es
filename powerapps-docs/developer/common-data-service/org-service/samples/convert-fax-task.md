---
title: 'Ejemplo: Convertir un fax en una tarea (Common Data Service) | Microsoft Docs'
description: 'Ejemplo que muestra cómo convertir un fax en una tarea '
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 407a5981033d90df15c0f6ba200afd3ad77d6c44
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749675"
---
# <a name="sample-convert-a-fax-to-a-task"></a>Ejemplo: convertir un fax en una tarea

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-convert-fax-task -->


Este ejemplo muestra cómo convertir un **Fax** en una **tarea**. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ConvertFaxToTask).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]


## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El método `CreateRequiredRecords` crea los datos de ejemplo necesarios para el ejemplo. El método `retrievedFax` recupera el fax. El método `DeleteRequiredRecords` le da la opción de eliminar todos los datos que el ejemplo ha creado.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
1. El método `WhoAmIRequest` obtiene los detalles del usuario actual.
1. El método `ActivityParty` crea la parte de actividad para enviar y recibir fax.
1. El método `Fax` crea el fax necesarios para el ejemplo.


### <a name="demonstrate"></a>Demostración

1. Recupera todo los Id. de fax que se crean en [Configuración](#setup).
2. Crea una tarea y compruebe si se ha creado la tarea. 

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar todos los datos creados en el ejemplo.
2. La eliminación es opcional en caso de que desee examinar los datos creados por el ejemplo. Puede eliminar manualmente los datos para obtener los mismos resultados.
