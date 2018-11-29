---
title: setActiveStage (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9c40a770-f4cb-4230-8893-0527f8472825
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setactivestage-client-api-reference"></a>setActiveStage (referencia de la API de cliente)



[!INCLUDE[./includes/setActiveStage-description.md](./includes/setActiveStage-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.data.process.setActiveStage(stageId, callbackFunction);`

## <a name="parameters"></a>Parámetros

<table style="width:100%">
<tr>
<th>Nombre</th>
<th>Tipo</th>
<th>Obligatoria</th>
<th>Descripción</th>
</tr>
<tr>
<td>stageId</td>
<td>String</td>
<td>Sí</td>
<td>El Id. de la fase completada para la entidad para crear la fase activa. </td>
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
<td>no válido</td>
<td>Hay tres razones por las que este valor puede ser devuelto:
<ul>
<li>El parámetro *stageId* es un valor de Id. de fase inexistente.</li>
<li>La fase activa no es la fase seleccionada.</li>
<li>El registro aún no se ha guardado.</li>
</ul>
</td>
</tr>
<tr>
<td>Inaccesible</td>
<td>La fase existe en otra ruta.</td>
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
>Este método se puede usar únicamente cuando la fase seleccionada y la fase activa son iguales. Cuando el código se inicia desde el evento [OnStageChange](../../events/onstagechange.md), la fase actual se seleccionará. Cuando se inicia el código desde el evento [OnStageSelected](../../events/onstageselected.md), debe usar el método [getActiveStage](getActiveStage.md) para comprobar que la fase seleccionada también es la fase activa. Para cualquier otro evento de formulario, no es posible determinar qué fase está seleccionada actualmente. Para obtener los mejores resultados, este método se debe usar solo en código al que se llame en funciones iniciadas por los eventos [OnStageChange](../../events/onstagechange.md) y [OnStageSelected](../../events/onstageselected.md).

### <a name="related-topics"></a>Temas relacionados

[getActiveStage](getActiveStage.md)

[formContext.data.process](../../formContext-data-process.md)
 


