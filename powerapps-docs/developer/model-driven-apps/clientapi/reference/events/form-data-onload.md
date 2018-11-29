---
title: Evento OnLoad de datos de formulario (referencia API de cliente) en aplicaciones basadas en modelo| Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: fb13c0a1-0e00-4592-8e58-3c2412141fbd
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="form-data-onload-event-client-api-reference"></a>Evento de datos de formulario OnLoad (referencia de la API de cliente)



Este evento se produce cada vez que se cargan datos de formulario, específicamente:

- Durante la carga de páginas de inicio
- Cuando se actualizan los datos de páginas de forma explícita usando el método formContext.data.[refresh](../formContext-data/refresh.md).
- Cuando se actualizan los datos de una página al guardar un registro, si hay cambios.
 
Utilice los métodos formContext.data.[addOnLoad](../formContext-data/addOnLoad.md) y formContext.data.[removeOnLoad](../formContext-data/removeOnLoad.md) para administrar los controladores de eventos para este evento. 



