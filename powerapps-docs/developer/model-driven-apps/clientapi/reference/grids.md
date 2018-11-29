---
title: Cuadrículas y subcuadrículas en aplicaciones basadas en modelos para Dynamics 365 | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9d35c036-637f-4580-8ba0-027a44c0fdee
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="grids-and-subgrids-in-model-driven-apps-client-api-reference"></a>Cuadrículas y subcuadrículas en aplicaciones basadas en modelos (referencia de API de cliente)



Las cuadrículas presentan datos en un formato de tabla en aplicaciones basadas en modelos. Las cuadrículas pueden abarcar todo el formulario o pueden ser uno de los elementos de un formulario; estos últimos se denominan *subcuadrículas*.

## <a name="types-of-grids"></a>Tipos de cuadrículas

Hay dos tipos de cuadrículas en aplicaciones basadas en modelos:
- **Cuadrículas de solo lectura**: muestran datos en un formato de tabla. Para editar los datos que se muestran en una cuadrícula de solo lectura, hay que hacer clic en el registro en la cuadrícula para abrir el formulario, editar los datos y guardarlo.
-  **Cuadrículas editables**: además de mostrar datos en formato de tabla, proporciona funciones de edición en línea enriquecidas en clientes web y móviles, lo que incluye la capacidad de agrupar, ordenar y filtrar los datos dentro de la misma cuadrícula de manera que no tenga que cambiar de registro o de vista. La cuadrícula editable es un control personalizado y se admite en la cuadrícula principal y en las subcuadrículas de un formulario del cliente web y de paneles, y en las cuadrículas de formulario de los clientes móviles. Aunque el control de cuadrícula editable proporcione la función de edición, respeta la configuración de metadatos de la cuadrícula de solo lectura y de seguridad a nivel de campo.

<a name="bkmk_gridcontext"></a>
## <a name="getting-the-grid-context"></a>Obtener el contexto de la cuadrícula

El contexto de la cuadrícula es la instancia de cuadrícula o subcuadrícula en un formulario con el que desea ejecutar el código. Para obtener más información sobre cómo obtener el contexto de cuadrícula para ejecutar el código de JavaScript, vea [contexto de cuadrícula de la API del cliente](../clientapi-grid-context.md)

## <a name="events"></a>Eventos

|Nombre|Descripción|Aplicable a|
|--|--|--|
|[Evento OnLoad de subcuadrícula](events/subgrid-onload.md)|Se produce cada vez que se actualiza la subcuadrícula. Esto incluye cuando los usuarios ordenan los valores de la subcuadrícula haciendo clic en los encabezados de columna.|Cuadrícula de solo lectura|
|[Cuadrícula OnChange](events/grid-onchange.md)|Se produce cuando un valor se modifica en una celda en la cuadrícula editable y la celda pierde el foco.|Cuadrícula editable|
|[Cuadrícula OnRecordSelect](events/grid-onrecordselect.md)|Se produce cuando una sola fila (registro) se selecciona en la cuadrícula editable.|Cuadrícula editable|
|[Cuadrícula OnSave](events/grid-onsave.md)|Se produce antes de enviar la información actualizada al servidor y cuando se produce alguno de los siguientes hechos: hay un cambio en la selección de registros, el usuario activa explícitamente una operación de guardado mediante el botón Guardar de la cuadrícula o el usuario aplica una operación de ordenación, filtrado, agrupación, paginación o navegación desde la cuadrícula editable mientras hay cambios pendientes.|Cuadrícula editable|

>[!NOTE]
>Puede registrar los eventos **OnChange**, **OnRecordSelect** y **OnSave** mediante la pestaña **Eventos** de la página de aplicaciones basadas en modelos que se usa para habilitar las cuadrículas editables para una entidad en una cuadrícula de solo lectura.

## <a name="methods"></a>Métodos

|Nombre|Descripción|Disponible para|
|--|--|--|
|[GridControl](grids/gridcontrol.md)|Proporciona métodos para trabajar con el control de cuadrícula o subcuadrícula.|Cuadrículas editables y de solo lectura|
|[Cuadrícula](grids/grid.md)|Proporciona los métodos para tener acceso a la información acerca de los datos de la cuadrícula.|Cuadrículas editables y de solo lectura|
|[GridRow](grids/gridrow.md)|Proporciona métodos para trabajar con filas o filas seleccionadas en la cuadrícula.|Cuadrículas editables y de solo lectura|
|[GridRowData](grids/gridrowdata.md)|Proporciona métodos para trabajar con filas o filas seleccionadas en la cuadrícula.|Cuadrículas editables y de solo lectura|
|[GridEntity](grids/gridentity.md)|Proporciona los métodos para tener acceso a datos acerca de registros específicos en las filas.|Cuadrículas editables y de solo lectura|
|[GridAttribute](grids/gridattribute.md)|Proporciona métodos para obtener acceso a los datos en la celda de una cuadrícula editable.|Cuadrícula editable|
|[GridCell](grids/gridcell.md)|Proporciona métodos para obtener acceso a los datos relacionados con el control en un formulario que está vinculado a un atributo en una cuadrícula editable.|Cuadrícula editable|
|[ViewSelector](grids/viewselector.md)|Proporciona métodos para obtener o para establecer la información sobre el selector de vistas del control de subcuadrícula.|Cuadrícula de solo lectura|


### <a name="related-topics"></a>Temas relacionados

[Contexto de cuadrícula de la API del cliente](../clientapi-grid-context.md)

[Usar cuadrículas editables](../../use-editable-grids.md)

[Referencia API de cliente para aplicaciones basadas en modelos](../reference.md)

[Resumen de las aplicaciones orientadas a modelos de desarrollador](../../overview.md)

