---
title: Objeto Xrm de API de cliente para aplicaciones basadas en modelos | MicrosoftDocs
description: El tema se proporciona la referencia de API de clientes para aplicaciones basadas en modelos.
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: conceptual
applies_to:
- Dynamics 365 (online)
ms.assetid: 15272ad9-25d7-499e-9361-a65f789daf20
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 6ee727043ba58c4facc387b7834728e1c30c7406
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115884"
---
# <a name="client-api-xrm-object"></a>Objeto Xrm de API de cliente



El objeto **Xrm** está disponible globalmente para utilizarlo en el código sin tener que usar el contexto de ejecución en la API del cliente.

## <a name="xrm-object-model"></a>Modelo de objetos Xrm 

En la siguiente ilustración se muestra el modelo de objetos Xrm:

![Modelo de objetos Xrm](../media/ClientAPI-XrmModel.png)

Esta es la información acerca de cada uno de los espacios de nombre en el objeto Xrm:

|Espacio de nombres  |Descripción  |
---------|---------------
|[Xrm.Device](reference/xrm-device.md)|Proporciona los métodos para usar las funciones nativas de los dispositivos móviles.|
|[Xrm.Encoding](reference/xrm-encoding.md)|Proporciona métodos para codificar cadenas.|
|[Xrm.Navigation](reference/xrm-navigation.md)|Proporciona métodos para navegar por los formularios y los elementos de aplicaciones basadas en modelos.|
|[Xrm.Panel](reference/xrm-panel.md)|Proporciona un método para mostrar una página web en el panel lateral del formulario de aplicaciones basadas en modelos.|
|[Xrm.Utility](reference/xrm-utility.md)|Proporciona un contenedor para métodos útiles.|
|[Xrm.WebApi](reference/xrm-webapi.md)|Proporciona métodos para usar las API web para crear y administrar registros y ejecutar las funciones y las acciones de las API web.<br/><br/>[Xrm.WebApi.offline](reference/xrm-webapi/offline.md): Proporciona métodos para crear y administrar registros en los clientes móviles de aplicaciones basadas en modelos mientras se trabaja en modo *sin conexión*.<br/><br/>[Xrm.WebApi.online](reference/xrm-webapi/online.md): Proporciona métodos para usar la API web para crear y administrar registros y ejecutar funciones y acciones de la API web en Customer Engagement cuando se establece conexión con el servidor de Customer Engagement (modo en línea).|

## <a name="client-api-global-context"></a>Contexto global de API del cliente

Utilice el método **Xrm.Utility**.[getGlobalContext](reference/xrm-utility/getGlobalContext.md) de los formularios para recuperar información específica de una organización, un usuario o del cliente donde se ejecuta el script sin pasar por el contexto de ejecución de formulario. Este es un cambio frente a las versiones anteriores donde había que usar el contexto de formulario para recuperar contexto global usando **Xrm.Page.context**.

> [!NOTE]
> **Xrm.Page.context** está [obsoleto](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming#some-client-apis-are-deprecated) en la versión actual y ahora debe usar el nuevo método **Xrm.Utility.**[getGlobalContext](reference/xrm-utility/getGlobalContext.md) para obtener el contexto global en su código versión 9.0 o posterior. 

Para acceder a la información de contexto global en recursos HTML Web independientes, debe incluir una referencia a **ClientGlobalContext.js.aspx** en el recurso web y a continuación, utilizar la función **GetGlobalContext**. Más información: [función GetGlobalContext y ClientGlobalContext.js.aspx](reference/GetGlobalContext-ClientGlobalContext.js.aspx.md)

### <a name="related-topics"></a>Temas relacionados

[Comprender el modelo de objetos de la API de cliente](understand-clientapi-object-model.md)<br/>
[API de cliente obsoletas](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming#some-client-apis-are-deprecated)
