---
title: Versiones de la API web de Common Data Service (Common Data Service)| Microsoft Docs
description: 'Leer cómo funciona el control de versiones de la API web de Common Data Service. Las versiones API web de Common Data Service admiten diferencias específicas de versión en el mismo entorno que es diferente del comportamiento en las versiones de v8.x, en las que se añadió nuevas capacidades'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: d9bb79a5-2bfa-4ffe-8cb4-60f192359489
caps.latest.revision: 34
author: brandonsimons
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="common-data-service-web-api-versions"></a>Versiones de API Web de Common Data Service

A partir de la v9.0 de Dynamics 365, la API web admite diferencias específicas de versión en el mismo entorno.  
  
Esto es diferente del comportamiento para las versiones de v8.*x*. En las versiones anteriores nuevas funcionalidades estaban disponibles para cualquier versión del servicio según la actualización aplicada al entorno.  Después de la actualización a v8.2, los servicios de v8.0 y v8.1 eran idénticos. Esto fue posible porque todos los cambios eran adición. Nada se ha quitado ni se han introducido cambios importantes. Como consecuencia, la versión específica que se hace referencia en la dirección URL del servicio de la versión 8.*x* no era realmente importante.  
  
El futuro de las funcionalidades del servicio puede cambiar, incluidos cambios potencialmente importantes como quitar operaciones específicas. Esto le permitirá de las mejoras que se aplicarán a la forma en curso. En este tema se registra cualquier diferencia específica de la versión y las limitaciones en la API web aún no se ha igualado con el servicio de la organización.  
  
## <a name="web-api-limitations"></a>Limitaciones de la API web de   

La API web de Common Data Service proporciona paridad completa con las capacidades de servicio de la organización. Para Common Data Service, este tema describe las limitaciones que proceden la versión v8.X de Common Data Service. Para las versiones anteriores, vea [limitaciones de API Web de Dynamics CRM 2016](https://msdn.microsoft.com/library/mt628816\(CRM.8\).aspx).  
 
> [!NOTE] 
> Si ha definido una acción personalizada que incluya un valor de devolución complejo y un valor de devolución simple, una acción correspondiente no estaba disponible en la API web pero estaba disponible mediante el extremo de 2011 SOAP. Un valor de devolución complejo es una `EntityReference`, `Entity`, o `EntityCollection`. Puede tener cualquier combinación de valores de devolución simples o un solo valor de devolución complejo. Más información: [Crear sus propias acciones](/dynamics365/customer-engagement/developer/create-own-actions).
 
## <a name="new-operations-added"></a>Nuevas operaciones agregadas  
 Las operaciones siguientes se han agregado a la API web para la versión v9.x.  
  
||||  
|-|-|-|  
|<xref:Microsoft.Crm.Sdk.Messages.GrantAccessRequest>|<xref:Microsoft.Crm.Sdk.Messages.ModifyAccessRequest>|<xref:Microsoft.Crm.Sdk.Messages.RetrieveSharedPrincipalsAndAccessRequest>|  
  
### <a name="see-also"></a>Vea también  

[Utilizar API Web de Common Data Service](overview.md)<br />
[Autentique Common Data Service con la API web](authenticate-web-api.md)<br />
[Tipos y operaciones de API web](web-api-types-operations.md)<br />
[Realizar operaciones mediante la API web](perform-operations-web-api.md)
