---
title: getGlobalContext (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: d87e0614-f365-4ed1-992a-741575bb2b7e
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getglobalcontext-client-api-reference"></a>getGlobalContext (referencia de la API de cliente)



[!INCLUDE[./includes/getGlobalContext-description.md](./includes/getGlobalContext-description.md)]
 El método permite el acceso al contexto global sin pasar por el contexto del formulario. Contiene un equivalente a todos los métodos disponibles para el objeto **Xrm.Page.context** (ahora desusado) para recuperar la información específica de un cliente, una organización o un usuario.

> [!IMPORTANT]
> Para acceder a la información de contexto global en recursos HTML Web independientes, debe incluir una referencia a **ClientGlobalContext.js.aspx** en el recurso web y a continuación, utilizar la función **GetGlobalContext**. Más información: [función GetGlobalContext y ClientGlobalContext.js.aspx](../GetGlobalContext-ClientGlobalContext.js.aspx.md) 

## <a name="properties-of-global-context-getglobalcontext"></a>Propiedades de contexto global (getGlobalContext)

Use las siguientes propiedades de contexto global para obtener información sobre el cliente, la configuración de la organización o la configuración de usuario:

|Propiedad |Descripción | 
|---|---|
|[client](getGlobalContext/client.md) | Devuelve información acerca del cliente.|
|[organizationSettings](getGlobalContext/organizationSettings.md) | Devuelve la información sobre la configuración de la organización actual.|
|[userSettings](getGlobalContext/userSettings.md) | Devuelve la información sobre la configuración del usuario actual.|


## <a name="methods-of-global-context-getglobalcontext"></a>Métodos de contexto global (getGlobalContext)

|Método |Descripción |
|---|---|
|[getAdvancedConfigSetting](getGlobalContext/getAdvancedConfigSetting.md) |Devuelve información sobre las opciones de configuración avanzadas de la organización.|
|[getClientUrl](getGlobalContext/getClientUrl.md) |Devuelve la dirección URL base que se usó para acceder a la aplicación.|
|[getCurrentAppName](getGlobalContext/getCurrentAppName.md) |Devuelve el nombre de la aplicación de negocio actual de las aplicaciones basadas en modelos.|
|[getCurrentAppProperties](getGlobalContext/getCurrentAppProperties.md) |Devuelve las propiedades de la aplicación de negocio actual de las aplicaciones basadas en modelos.|
|[getCurrentAppUrl](getGlobalContext/getCurrentAppUrl.md) |Devuelve la dirección URL de la aplicación de negocio actual de las aplicaciones basadas en modelos.|
|[getVersion](getGlobalContext/getVersion.md) |Devuelve el número de versión de la instancia de las aplicaciones basadas en modelos.|
|[isOnPremises](getGlobalContext/isOnPremises.md) |Devuelve un valor booleano que indica si la instancia de las aplicaciones basadas en modelos se hospeda en localmente o en línea.|
|[prependOrgName](getGlobalContext/prependOrgName.md) |Agrega el nombre único de la organización actual como prefijo a una cadena, normalmente una dirección URL.|




 



