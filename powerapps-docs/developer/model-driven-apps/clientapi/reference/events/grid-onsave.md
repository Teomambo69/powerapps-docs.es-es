---
title: Evento OnStage de cuadrícula (referencia de API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 89123cde-7c66-4c7d-94e4-e287285019f8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="grid-onsave-event-client-api-reference"></a>Evento OnSave de cuadrícula (referencia de la API de cliente)



El evento `OnSave` aparece antes de enviar la información actualizada al servidor, y cuando se produce algo de lo siguiente: 
- Hay un cambio en la selección de registro.
- El usuario explícitamente desencadena una operación de guardar con el botón de guardar de la cuadrícula editable.
- El usuario aplica una operación de ordenación, filtro, grupo, paginación, o navegación desde la cuadrícula editable mientras hay cambios pendientes.

Algunos puntos importantes a tener en cuenta para el evento `OnSave`: 
- Si un usuario edita varias columnas del mismo registro en secuencia, el evento OnSave se desencadenará solo una vez para garantizar el rendimiento óptimo y la compatibilidad de comportamiento de formularios.
- La cuadrícula editable y el formulario primario tienen botones Guardar independientes. Al hacer clic en el botón Guardar en uno no guardará cambios en el otro.
- La cuadrícula editables no guarda cambios pendientes cuando las operaciones de navegación se realizan fuera de su contexto. Si el control tiene datos sin guardar, pueden perderse. Por lo tanto, el evento `OnSave` puede no desencadenarse. Por ejemplo, esto podría ocurrir al navegar a otro registro utilizando un campo de búsqueda de formulario o a través de la cinta de opciones.
- Si presiona el botón Actualizar en la cuadrícula editable se descartará cualquier cambio pendiente, y el evento `OnSave` no se desencadenará.
- El control de cuadrícula editable no implementa un temporizador de autoguardado.
La cuadrícula editable suprime reglas de detección de duplicados.

### <a name="related-topic"></a>Tema relacionado
[Evento OnSave de formulario](form-onsave.md)



