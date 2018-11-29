---
title: GridAttribute (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 8139c622-e4d9-478f-9510-414d140e5556
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="gridattribute-client-api-reference"></a>GridAttribute (referencia de la API de cliente)



GridAttribute se admite únicamente para cuadrículas editables.

GridAttribute () representa los datos en la celda de una cuadrícula editable y contiene una referencia a todas las celdas asociadas al atributo. Vea [Colecciones (referencia de la API de cliente)](../collections.md) para obtener información sobre los métodos disponibles para obtener acceso a los datos de una colección.

GridAttribute también admite la colección **Controles** para atributos de una fila de cuadrícula seleccionada, que proporciona métodos para trabajar con una colección de celdas asociadas al atributo. Cada celda ([GridCell](gridcell.md)) de una fila de cuadrícula seleccionada es análoga a un control en un formulario que está ligado a un atributo en una cuadrícula editable. Vea [Colecciones (referencia de la API de cliente)](../collections.md) para obtener información sobre los métodos disponibles para obtener acceso a los datos de una colección.

>[!TIP]
>Por motivos de rendimiento, una fila (registro) en una cuadrícula editable no es editable hasta que se seleccione el registro. Los usuarios deben seleccionar un solo registro en una cuadrícula para editarla. Una vez que un registro se selecciona en una cuadrícula editable, Dynamics 365 evalúa internamente un número de elementos incluidos el acceso del usuario al registro, si el registro está activo, y las validaciones de campo para asegurarse de que la seguridad y la validez de datos se mantienen cuando se editan los datos. Considere usar el evento [OnRecordSelect](../events/grid-onrecordselect.md) con el método [getFormContext](../executioncontext/getFormContext.md) para obtener acceso a los registros de la cuadrícula que se encuentren en estado editable.

## <a name="methods"></a>Métodos

GridAttribute admite los siguientes métodos para los atributos de una fila de cuadrícula seleccionada.

|Nombre|Descripción|
|--|--|
|[getName](../attributes/getName.md)|Devuelve el nombre lógico del atributo de una fila de cuadrícula seleccionada.|
|[getRequiredLevel](../attributes/getRequiredLevel.md)| Devuelve un valor de cadena que indica si un valor del atributo es necesario o recomendado.|
|[setRequiredLevel](../attributes/setRequiredLevel.md)| Establece si los datos son requeridos o recomendados para el atributo de una fila de cuadrícula seleccionada antes de que el registro se pueda guardar.|
|[getValue](../attributes/getValue.md)| Recupera el valor de los datos de un atributo.|
|[setValue](../attributes/setValue.md)| Establece el valor de los datos de un atributo.|

>[!NOTE]
>Para seleccionar una fila de una cuadrícula editable, utilice la [cuadrícula](grid.md).[getSelectedRows](grid/getSelectedRows.md)

### <a name="related-topics"></a>Temas relacionados

[GridCell](gridcell.md)

[Cuadrículas y subcuadrículas en aplicaciones basadas en modelos](../grids.md)

[Colección de controles](../attributes/controls-collection.md)


