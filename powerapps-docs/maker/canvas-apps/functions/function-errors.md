---
title: Función Errors | Microsoft Docs
description: Información de referencia para la función Errors en PowerApps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/11/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 114474696f85980da315b6dd225250dc1b197805
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992799"
ms.PowerAppsDecimalTransform: true
---
# <a name="errors-function-in-powerapps"></a>Función Errors en PowerApps
Proporciona información de error para los cambios anteriores en un [origen de datos](../working-with-data-sources.md).

## <a name="overview"></a>Información general
Pueden producirse errores cuando se cambia un [registro](../working-with-tables.md#records) de un origen de datos.  Esto puede deberse a numerosas causas, como interrupciones de red, permisos inadecuados y conflictos de edición.  

La función **[Patch](function-patch.md)** y otras funciones de datos no devuelven errores directamente. En su lugar, devuelven el resultado de la operación. Una vez que se haya ejecutado una función de datos, puede usar la función **Errors** para obtener los detalles de los errores.  Puede comprobar la existencia de errores con la función **[IsEmpty]** en la fórmula **IsEmpty( Errors ( ... ) )** .

Puede evitar que se produzcan algunos errores mediante las funciones **[Validate](function-validate.md)** y **[DataSourceInfo](function-datasourceinfo.md)** .  En el tema relativo al [trabajo con orígenes de datos](../working-with-data-sources.md), encontrará más sugerencias sobre cómo trabajar con los errores y evitarlos.

## <a name="description"></a>Descripción
La función **Errors** devuelve una [tabla](../working-with-tables.md) de errores que contiene las [columnas](../working-with-tables.md#columns) siguientes:

* **Registro**.  Registro del origen de datos que contenía el error.  Si el error se produjo durante la creación de un registro, esta columna será *blank*.
* **Columna**.  Columna que produjo el error, en caso de que el error pueda atribuirse a una sola columna. De lo contrario, será *blank*.
* **Mensaje**.  Descripción del error.  Esta cadena de error se puede mostrar para el usuario final.  Tenga en cuenta que este mensaje puede generarlo el origen de datos, por lo que podría ser largo y contener nombres de columna sin formato carentes de significado para el usuario.
* **Error**.  Código de error que se puede usar en las fórmulas para ayudar a resolver el error:

| ErrorKind | Descripción |
| --- | --- |
| ErrorKind.Conflict |Se ha realizado otro cambio en el mismo registro, lo que produce un conflicto de cambios.  Use la función **[Refresh](function-refresh.md)** para volver a cargar el registro e intente de nuevo el cambio. |
| ErrorKind.ConstraintViolation |Se han infringido una o más restricciones. |
| ErrorKind.CreatePermission |Se ha intentado crear un registro, pero el usuario actual no tiene permiso para crear registros. |
| ErrorKind.DeletePermission |Se ha intentado eliminar un registro, pero el usuario actual no tiene permiso para eliminar registros. |
| ErrorKind.EditPermission |Se ha intentado editar un registro, pero el usuario actual no tiene permiso para editar registros. |
| ErrorKind.GeneratedValue |Se ha intentado cambiar una columna que el origen de datos genera automáticamente. |
| ErrorKind.MissingRequired |El valor de una columna necesaria no está en el registro. |
| ErrorKind.None |No hay ningún error. |
| ErrorKind.NotFound |Se ha intentado editar o eliminar un registro, pero no se pudo encontrar.  Es posible que otro usuario haya cambiado el registro. |
| ErrorKind.ReadOnlyValue |Se ha intentado cambiar una columna que es de solo lectura. |
| ErrorKind.Sync |El origen de datos ha notificado un error.  Consulte la columna Mensaje para obtener más información. |
| ErrorKind.Unknown |Se ha producido un error, pero es de tipo desconocido. |
| ErrorKind.Validation |Se ha detectado un problema de validación general que no se corresponde con ninguno de los demás tipos. |

Los errores pueden devolverse para el origen de datos completo o para una sola fila seleccionada si se proporciona el argumento *Record* a la función.  

La función **[Patch](function-patch.md)** u otras funciones de datos pueden devolver un valor *blank* si, por ejemplo, no se pudo crear un registro. Si pasa un valor *blank* a **Errors**, le devolverá información de error adecuada en estos casos.  El uso posterior de funciones de datos en el mismo origen de datos borrará esta información de error.

Si no hay ningún error, la tabla que **Errors** devuelve estará [vacía](function-isblank-isempty.md) y se podrá probar con la función **[IsEmpty](function-isblank-isempty.md)** .

## <a name="syntax"></a>Sintaxis
**Errors**( *DataSource* [; *Record* ] )

* *DataSource*: requerido. Origen de datos para el que quiere devolver errores.
* *Record*: opcional.  Registro específico para el que quiere devolver errores. Si no especifica este argumento, la función devuelve errores para todo el origen de datos.

## <a name="examples"></a>Ejemplos
### <a name="step-by-step"></a>Paso a paso
En este ejemplo, vamos a trabajar con el origen de datos **IceCream**:

![](media/function-errors/icecream.png)

A través de la aplicación, un usuario carga el registro Chocolate en un formulario de entrada de datos y cambia el valor de **Quantity** a 90.  El registro con el que se va a trabajar se coloca en la [variable de contexto](../working-with-variables.md#use-a-context-variable) **EditRecord**:

* **UpdateContext ({EditarRegistro: First (Filter (IceCream; Flavor = "chocolate"))})**

Para realizar este cambio en el origen de datos, se usa la función **[Patch](function-patch.md)** :

* **Patch( IceCream; EditRecord; Gallery.Updates )**

donde **Gallery. updates** se evalúa como **{Quantity: 90}** , ya que solo se ha modificado la propiedad **Quantity** .

Por desgracia, justo antes de que se invoque la función **[Patch](function-patch.md)** , otra persona modifica la propiedad **Quantity** de Chocolate y la establece en 80.  PowerApps lo detecta y no permite que se produzca el cambio en conflicto.  Puede comprobar esta situación mediante la fórmula:

* **IsEmpty( Errors( IceCream; EditRecord ) )**

que devuelve **false**, ya que la función **Errors** ha devuelto la tabla siguiente:

| Registro | Columna | Mensaje | Error |
| --- | --- | --- | --- |
| Tipo "Chocolate", cantidad: 100} |*blank* |"Otro usuario ha modificado el registro que está intentando modificar. Vuelva a cargar el registro e inténtelo de nuevo." |ErrorKind.Conflict |

Puede colocar una etiqueta en el formulario para mostrar este error al usuario.

* Para mostrar el error, establezca la propiedad **[Text](../controls/properties-core.md)** de la etiqueta en esta fórmula:<br>
  **Label.Text = First(Errors( IceCream; EditRecord )).Message**

También puede agregar un botón **Recargar** en el formulario para que el usuario pueda resolver eficazmente el conflicto.

* Para mostrar el botón solo cuando se haya producido un conflicto, establezca la propiedad **[Visible](../controls/properties-core.md)** del botón en esta fórmula:<br>
    **!IsEmpty( Lookup( Errors( IceCream; EditRecord ); Error = ErrorKind.Conflict ) )**
* Para revertir el cambio cuando el usuario selecciona el botón, establezca su propiedad **[OnSelect](../controls/properties-core.md)** en esta fórmula:<br>
    **ReloadButton.OnSelect = Revert( IceCream; EditRecord )**

