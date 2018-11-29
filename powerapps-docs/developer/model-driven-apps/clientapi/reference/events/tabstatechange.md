---
title: Evento TabStateChange (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
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
# <a name="tabstatechange-event-client-api-reference"></a>Evento TabStateChange (referencia de la API de cliente)



Este evento se produce cuando **DisplayState** de la pestaña cambia debido a la interacción del usuario o cuando el método [setDisplayState](../formContext-ui-tabs/setDisplayState.md) se aplica en código. 

Utilice este evento cuando desee cambiar la propiedad **src** de un IFRAME en la pestaña. Si establece la propiedad .**src** de IFrame en el evento OnLoad para IFRAME en una ficha contraído, el valor se sobrescribirá cuando se ha ampliado la ficha.

Utilice el método [addTabStateChange](../formContext-ui-tabs/addTabStateChange.md) para agregar controladores de eventos para este evento y el método [removeTabStateChange](../formContext-ui-tabs/removeTabStateChange.md) para quitarlos.



