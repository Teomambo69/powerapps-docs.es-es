---
title: Función Revert | Microsoft Docs
description: Información de referencia, incluida la sintaxis y un ejemplo, para la función Revert en Power apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/21/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: efaffeac79c104d517d8e7da5b2e324fcac3eecb
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730339"
ms.PowerAppsDecimalTransform: true
---
# <a name="revert-function-in-power-apps"></a>Reversión de la función en Power apps
Actualiza y borra errores para los [registros](../working-with-tables.md#records) de un [origen de datos](../working-with-data-sources.md).

## <a name="description"></a>Descripción
La función **Revert** actualiza un origen de datos completo o un único registro en ese origen de datos. Verá los cambios que realizaron otros usuarios.

Para los registros revertidos, **Revert** también borra todos los errores de la [tabla](../working-with-tables.md) que la función **[Errors](function-errors.md)** devuelve.

Si la función **[Errors](function-errors.md)** informa sobre un conflicto después de **[Patch](function-patch.md)** u otra operación de datos, use **Revert** en el registro para iniciar con la versión en conflicto y vuelva a aplicar el cambio.

**Revert** no tiene ningún valor devuelto. Se puede usar únicamente en una [fórmula de comportamiento](../working-with-formulas-in-depth.md).

## <a name="syntax"></a>Sintaxis
**Revert**( *DataSource* [; *Record* ] )

* *DataSource*: requerido. El origen de datos que desea revertir.
* *Registro*: opcional.  El registro que desea revertir.  Si no se especifica un registro, se revierte el origen de datos completo.

## <a name="example"></a>Ejemplo
En este ejemplo, revertirá el origen de datos denominado **IceCream**, que empieza con los datos en esta tabla:

![](media/function-revert/icecream.png)

Un usuario de otro dispositivo cambia la propiedad **Quantity** en el registro **Strawberry** a **400**.  Aproximadamente al mismo tiempo, usted cambia la misma propiedad del mismo registro a **500**, sin tener conocimiento sobre el otro cambio.

Usa la función **[Patch](function-patch.md)** para actualizar el registro:<br>
**Patch( IceCream; First( Filter( IceCream; Flavor = "Strawberry" ) ); { Quantity: 500 } )**

Compruebe la tabla **[Errors](function-errors.md)** y encuentre un error:

| Registro | [Columna](../working-with-tables.md#columns) | Mensaje | Error |
| --- | --- | --- | --- |
| **{ ID: 1; Flavor: "Strawberry"; Cantidad: 300 }** |*blank* |**"Otro usuario ha modificado el registro que está intentando modificar.  Revierta el registro e inténtelo de nuevo ".** |**ErrorKind.Conflict** |

Tomando como base la columna **Error**, tiene un botón **Volver a cargar** para que la propiedad **[OnSelect](../controls/properties-core.md)** para establecer esta fórmula:<br>
**Revert( IceCream; First( Filter( IceCream; Flavor = "Strawberry" ) ) )**

Después de seleccionar el botón **Recargar**, la tabla **[Errores](function-errors.md)** está [vacía](function-isblank-isempty.md)y el nuevo valor para **Strawberry** se ha cargado:

![](media/function-revert/icecream-after.png)

Ha aplicado el cambio encima del cambio anterior y se ha cambiado el cambio correctamente porque el conflicto se ha resuelto.

![](media/function-revert/icecream-success.png)

