---
title: Función Revertir | Microsoft Docs
description: Información de referencia de la función Revertir en PowerApps, con sintaxis y ejemplos
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 10/21/2015
ms.author: gregli
ms.openlocfilehash: 08cb0690904a4b63645828678232769b66a439a1
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="revert-function-in-powerapps"></a>Función Revertir en PowerApps
Actualiza y borra errores para los [registros](../working-with-tables.md#records) de un [origen de datos](../working-with-data-sources.md).

## <a name="description"></a>Descripción
La función **Revertir** actualiza un origen de datos completo o un único registro en ese origen de datos. Verá los cambios que realizaron otros usuarios.

Para los registros revertidos, **Revertir** también borra todos los errores de la [tabla](../working-with-tables.md) que la función **[Errores](function-errors.md)** devuelve.

Si la función **[Errores](function-errors.md)** informa sobre un conflicto después de una **[Revisión](function-patch.md)** u otra operación de datos, **Revierta** el registro para iniciar con la versión en conflicto y vuelva a aplicar el cambio.

**Revertir** no tiene ningún valor devuelto. Se puede usar únicamente en una [fórmula de comportamiento](../working-with-formulas-in-depth.md).

## <a name="syntax"></a>Sintaxis
**Revertir**( *DataSource* [, *Registro* ] )

* *DataSource*: requerido. El origen de datos que desea revertir.
* *Registro*: opcional.  El registro que desea revertir.  Si no se especifica un registro, se revierte el origen de datos completo.

## <a name="example"></a>Ejemplo
En este ejemplo, revertirá el origen de datos denominado **IceCream**, que empieza con los datos en esta tabla:

![](media/function-revert/icecream.png)

Un usuario de otro dispositivo cambia la propiedad **Quantity** en el registro **Strawberry** a **400**.  Aproximadamente al mismo tiempo, usted cambia la misma propiedad del mismo registro a **500**, sin tener conocimiento sobre el otro cambio.

Usa la función **[Revisión](function-patch.md)** para actualizar el registro:<br>
**Revisión( IceCream, Primero( Filtrar( IceCream, Flavor = "Strawberry" ) ), {Quantity: 500} )**

Compruebe la tabla **[Errores](function-errors.md)** y encuentre un error:

| Registro | [Columna](../working-with-tables.md#columns) | Mensaje | Error |
| --- | --- | --- | --- |
| **{ ID: 1, Flavor: "Strawberry", Cantidad: 300 }** |*blank* |**"Otro usuario ha modificado el registro que está intentando modificar.  Revierta el registro e inténtelo de nuevo".** |**ErrorKind.Conflict** |

Tomando como base la columna **Error**, tiene un botón **Volver a cargar** para que la propiedad **[AlSeleccionar](../controls/properties-core.md)** para establecer esta fórmula:<br>
**Revert( IceCream, First( Filter( IceCream, Flavor = "Strawberry" ) ) )**

Después de seleccionar el botón **Recargar**, la tabla **[Errores](function-errors.md)** está [vacía](function-isblank-isempty.md)y el nuevo valor para **Strawberry** se ha cargado:

![](media/function-revert/icecream-after.png)

Ha aplicado el cambio encima del cambio anterior y se ha cambiado el cambio correctamente porque el conflicto se ha resuelto.

![](media/function-revert/icecream-success.png)

