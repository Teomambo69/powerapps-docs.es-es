---
title: GridCell (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
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
# <a name="gridcell-client-api-reference"></a>GridCell (referencia de la API de cliente)



GridCell se admite únicamente para cuadrículas editables.

GridCell de una fila de cuadrícula seleccionada es análoga a un control en un formulario que está ligado a un atributo en una cuadrícula editable. Vea [Colecciones (referencia de la API de cliente)](../collections.md) para obtener información sobre los métodos disponibles para obtener acceso a los datos de una colección.

## <a name="methods"></a>Métodos

GridCell admite los siguientes métodos.

|Nombre |Descripción |
|--|--|
|[clearNotification](../controls/clearNotification.md)| Desactiva la notificación de una celda.|
|[getDisabled](../controls/getDisabled.md)| Devuelve si la celda está deshabilitada (solo lectura).|
|[setDisabled](../controls/setDisabled.md)| Establece si la celda está deshabilitada.<br/><br/>**NOTA**: Habilitar a una celda de sólo lectura para editar puede producir un error cuando se guarda el registro. Si el campo es considerado de sólo lectura por el servidor, un error puede producirse si se modifica el valor. Eso puede ocurrir en los escenarios donde el usuario no tiene privilegios de escritura en el registro, el registro está deshabilitado, o el usuario no tiene los privilegios de seguridad de nivel de campo necesarios.| 
|[setNotification](../controls/setNotification.md)|Muestra un mensaje de error de una celda para indicar que los datos no son válidos.|
|[getLabel](../controls/getLabel.md)|Devuelve la etiqueta de la columna que contiene la celda.|


### <a name="related-topics"></a>Temas relacionados

[Cuadrículas y subcuadrículas en aplicaciones basadas en modelos](../grids.md)

[Controles](../controls.md)


