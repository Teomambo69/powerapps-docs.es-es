---
title: " Compartir una cola (Common Data Service) | Microsoft Docs"
description: Este ejemplo muestra cómo compartir una cola.
ms.custom: ''
ms.date: 12/20/2019
ms.reviewer: pehecke
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
ms.openlocfilehash: d2f569de501b89be1a535244864dac8ff6a7578d
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155572"
---
# <a name="share-a-queue"></a>Compartir una cola

Este ejemplo muestra cómo otorgar a un usuario o equipo acceso a una cola. [AddPrincipalToQueueRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.addprincipaltoqueuerequest?view=dynamics-general-ce-9) agrega el principal especificado a la lista de miembros de la cola. Si la entidad de seguridad pasada es un equipo, cada miembro del equipo se agrega a la cola.

Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ShareQueue).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

Consulte [Cómo ejecutar este ejemplo](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/README.md) para obtener información sobre cómo ejecutar este ejemplo.

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje [AddPrincipalToQueueRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.addprincipaltoqueuerequest?view=dynamics-general-ce-9) está diseñado para usarse en un escenario donde contenga los datos para agregar el principal especificado a la lista de miembros de la cola. Si el principal es un equipo, agregue cada miembro del equipo a la cola.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Programa de instalación

1. Comprobaciones para la versión actual de la organización. 
1. Crea los datos necesarios que requiere este ejemplo.

### <a name="demonstrate"></a>Demostración

El mensaje `AddPrincipalToQueueRequest` comparte una cola con un equipo.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar todos los datos creados en el ejemplo. La eliminación es opcional en caso de que desee examinar los datos creados por el ejemplo. Puede eliminar manualmente los datos para obtener los mismos resultados.