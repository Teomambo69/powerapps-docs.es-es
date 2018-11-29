---
title: Evento OnStageChange de formulario (referencia de API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
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
# <a name="form-onsave-event-client-api-reference-in-model-driven-apps"></a>Evento OnStageChange de formulario (referencia de API de cliente) en aplicaciones basadas en modelos



El evento `OnSave` se produce cuando:
- El usuario hace clic en el icono **Guardar** situado en la esquina inferior derecha del formulario, incluso cuando no hay datos modificados para guardar.
- El código ejecuta el método [formContext.data.entity.save](../formContext-data-entity/save.md), incluso si no hay datos modificados para guardar.
- El usuario navega fuera del formulario y hay datos sin guardar en el formulario.
- La opción de autoguardado está habilitada, 30 segundos después de que los datos han cambiado y hay datos sin guardar en el formulario.
- El código ejecuta el método [formContext.data.save](../formContext-data/save.md) y hay datos sin guardar en el formulario.
- El código ejecuta el método [formContext.data.refresh](../formContext-data/refresh.md) que pasa un valor true al primer parámetro y hay datos sin guardar en el formulario.

Para determinar en qué botón se ha hecho clic para realizar la acción de guardar, use el método getSaveMode.

Puede cancelar la acción de guardar mediante el método preventDefault en el objeto de argumentos del evento. El método preventDefault que es accesible mediante el método getEventArgs que forma parte del contexto de ejecución. El contexto de ejecución se transfiere automáticamente al controlador de eventos del formulario.

### <a name="related-topic"></a>Tema relacionado
[Evento de cuadrícula OnSave](grid-onsave.md)  



