---
title: getEventSource (referencia de API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
description: Obtenga información sobre el método getEventSource que devuelve una referencia al objeto en el que se produjo el evento.
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9f3b2fed-fde5-46e4-8c59-43aa51aa82df
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="geteventsource-client-api-reference"></a>getEventSource (referencia de la API de cliente)



Devuelve una referencia al objeto en que se produjo el evento.

## <a name="syntax"></a>Sintaxis

`ExecutionContextObj.getEventSource()`

## <a name="return-value"></a>Valor devuelto

**Tipo**: Objeto

**Descripción**: devuelve el objeto del modelo de objetos **Xrm** que es el origen del evento, no un objeto DOM HTML. Por ejemplo, en un evento [OnChange](../events/attribute-onchange.md), este método devuelve el objeto de atributo **formContext.data.entity** que representa el atributo cambiado.


### <a name="related-topics"></a>Temas relacionados
[Contexto de ejecución](../execution-context.md)





