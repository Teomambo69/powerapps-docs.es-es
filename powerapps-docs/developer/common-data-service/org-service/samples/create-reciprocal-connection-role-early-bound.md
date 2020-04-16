---
title: 'Ejemplo: Crear un rol de conexión recíproca(Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo crear un rol de conexión recíproca.
ms.custom: ''
ms.date: 10/31/2018
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
ms.openlocfilehash: bf4c86bffee4d99a9b678f831e78323f8a4262b7
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155880"
---
# <a name="sample-create-a-reciprocal-connection-role"></a>Ejemplo: creación de un rol de conexión recíproca

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-create-reciprocal-connection-role-early-bound -->

Este ejemplo muestra cómo crear los roles de conexión recíproca. Crea un rol de conexión para una cuenta y un rol de conexión para un contacto y, a continuación, los asocia entre sí para hacerlos recíprocos. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ReciprocalConnection
).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Los mensajes `ConnectionRole` y `ConnectionRoleObjectTypeCode` se pueden usar en un escenario donde contiene los datos que se necesitan para crear un nuevo rol de conexión y un tipo de objeto de rol de conexión.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. El mensaje `ConnectionRole` crea roles de conexión necesarios para el ejemplo.
3. El mensaje `ConnectionRoleObjectTypeCode` crea el registro de código de tipo de objeto de rol de conexión para la cuenta.
4. El mensaje `AssociateRequest` asocia los roles de conexión entre sí.

### <a name="demonstrate"></a>Demostración

1. Realizar la solicitud inicial y almacenar en caché los resultados, incluido el `DataToken`
1. Actualizar los registros creados en [Configuración](#setup)
1. Realice una segunda solicitud, esta vez pasando la `DataVersion` con el valor de `DataToken` recuperado de la solicitud inicial.
1. Mostrar los cambios de entidad devueltos por la segunda solicitud

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
