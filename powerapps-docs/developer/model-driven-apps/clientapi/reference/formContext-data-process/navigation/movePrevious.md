---
title: movePrevious (referencia de API de cliente) en aplicaciones basadas en modelos | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 649fe7b0-016d-409f-ba3c-b14e0f1953e0
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="moveprevious-client-api-reference"></a>movePrevious (referencia de la API de cliente)



[!INCLUDE[./includes/movePrevious-description.md](./includes/movePrevious-description.md)]

Puede moverse también a una fase previa en otra entidad.

## <a name="syntax"></a>Sintaxis

`formContext.data.process.movePrevious(callbackFunction);`

## <a name="parameters"></a>Parámetros

<table style="width:100%">
<tr>
<th>Nombre</th>
<th>Tipo</th>
<th>Obligatoria</th>
<th>Descripción</th>
</tr>
<tr>
<td>callbackFunction</td>
<td>Función</td>
<td>No</td>
<td>Una función para llamar una vez terminada la operación. A esta función de devolución de llamada se le pasa uno de los siguientes valores de cadena para indicar el estado de la operación:
<table>
<tr>
<th>Value</th>
<th>Razón</th>
</tr>
<tr>
<td>correcto</td>
<td>La operación se ha realizado correctamente.</td>
</tr>
<tr>
<td>crossEntity</td>
<td>La fase anterior es para otra entidad.</td>
</tr>
<tr>
<td>inicial</td>
<td>La fase activa es la primera fase de la ruta activa.</td>
</tr>
<tr>
<td>no válido</td>
<td>La operación ha producido error porque la fase seleccionada no es la misma que la fase activa.</td>
</tr>
<tr>
<td>dirtyForm</td>
<td>Esta valor se devolverá si los datos en la página no se guardan.</td>
</tr>
</table>
</td>
</tr>
</table>

>[!IMPORTANT]
>Este método se puede usar únicamente cuando la fase seleccionada y la fase activa son iguales. Cuando el código se inicia desde el evento [OnStageChange](../../events/onstagechange.md), la fase actual se seleccionará. Cuando se inicia el código desde el evento [OnStageSelected](../../events/onstageselected.md), debe usar el método [getActiveStage](../activestage/getActiveStage.md) para comprobar que la fase seleccionada también es la fase activa. Para cualquier otro evento de formulario, no es posible determinar qué fase está seleccionada actualmente. Para obtener los mejores resultados, este método se debe usar solo en código al que se llame en funciones iniciadas por los eventos [OnStageChange](../../events/onstagechange.md) y [OnStageSelected](../../events/onstageselected.md).

## <a name="remarks"></a>Comentarios

Este método hará que se produzca el evento [OnStageChange](../../events/onstagechange.md).

### <a name="related-topics"></a>Temas relacionados

[moveNext](moveNext.md)

[formContext.data.process](../../formContext-data-process.md)
 


