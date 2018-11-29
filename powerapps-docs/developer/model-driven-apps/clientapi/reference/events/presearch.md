---
title: Evento Presearch de control de búsqueda (referencia API de cliente) en aplicaciones basadas en modelos | MicrosoftDocs
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
# <a name="lookup-control-presearch-event-client-api-reference"></a>Evento PreSearch de control de búsqueda (referencia de la API de cliente)



Este evento se produce justo antes de que el control de búsqueda inicie un diálogo para buscar registros. No hay una interfaz de usuario para establecer controladores de eventos para este evento. Debe usar los métodos [addPreSearch](../controls/addpresearch.md) y [removePreSearch](../controls/removepresearch.md) en el control de búsqueda para agregar o quitar controladores de eventos para este evento.

Use este evento con otros métodos de control de búsqueda para cambiar los resultados que se muestran en una búsqueda basada en los datos de formulario actuales justo antes de que el control de búsqueda muestre los resultados de búsqueda para que el usuario los elija. 

## <a name="related-topics"></a>Temas relacionados

[addCustomFilter](../controls/addCustomFilter.md)



