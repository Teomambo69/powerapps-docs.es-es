---
title: Uso de scripting del lado cliente con aplicaciones controladas por modelos | Microsoft Docs
description: Obtenga información sobre cómo los desarrolladores pueden usar JavaScript en scripts del lado cliente y aplicaciones controladas por modelos.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/13/2018
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 38a1a5371cbaf5d10c59a291127c13a1d00a3056
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42829408"
---
# <a name="client-scripting-with-model-driven-apps"></a>Scripting del lado cliente con aplicaciones controladas por modelos

El scripting del lado cliente con JavaScript es uno de los métodos para aplicar lógica de procesos de negocio personalizada para mostrar datos en un formulario en una aplicación controlada por modelos, pero no debería ser la primera opción. *Las reglas de negocio* proporcionan una manera para que alguien que no conoce JavaScript y no sea desarrollador aplique lógica de procesos de negocio en un formulario. Más información: [Crear reglas de negocio y recomendaciones para aplicar lógica en un formulario (Guía de personalización de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/customize/create-business-rules-recommendations-apply-logic-form)

> [!TIP]
> Encontrará el diseñador de reglas de negocio dentro del área **Common Data Service** en [powerapps.com](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). Cuando examine una entidad, busque la pestaña **Reglas de negocio**.

Si no se pueden alcanzar los requisitos de negocio con una regla de negocio, encontrará que el scripting del lado cliente con el modelo de objetos de la API cliente proporciona una manera eficaz de extender el comportamiento de la aplicación y habilitar la automatización en el cliente.

## <a name="resources"></a>Recursos

Los recursos siguientes para scripting del lado cliente están disponibles en la Guía para desarrolladores de Dynamics 365 Customer Engagement.

- [Ejemplo de script en Customer Engagement mediante JavaScript](/dynamics365/customer-engagement/developer/clientapi/client-scripting)
- [Eventos de formularios y cuadrículas en Customer Engagement](/dynamics365/customer-engagement/developer/clientapi/events-forms-grids)
- [Comprender el modelo de objetos de la API del cliente](/dynamics365/customer-engagement/developer/clientapi/understand-clientapi-object-model)
- [Tutorial: Escribir el primer script de cliente](/dynamics365/customer-engagement/developer/clientapi/walkthrough-write-your-first-client-script)
- [Depurar el código JavaScript para Customer Engagement](/dynamics365/customer-engagement/developer/clientapi/debug-javascript-code)
- [Prácticas recomendadas: ejemplo de script en Customer Engagement](/dynamics365/customer-engagement/developer/clientapi/client-scripting-best-practices)
- [Referencia de la API de cliente de Customer Engagement](/dynamics365/customer-engagement/developer/clientapi/reference)

