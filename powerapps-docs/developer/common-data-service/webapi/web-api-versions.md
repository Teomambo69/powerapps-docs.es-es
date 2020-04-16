---
title: Versiones de la API web de Common Data Service (Common Data Service)| Microsoft Docs
description: Lea cómo funciona el control de versiones de API web de Common Data Service. Las versiones API web de Common Data Service admiten diferencias específicas de versión en el mismo entorno que es diferente del comportamiento en las versiones de v8.x, en las que se añadió nuevas capacidades
ms.custom: ''
ms.date: 07/25/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: d9bb79a5-2bfa-4ffe-8cb4-60f192359489
caps.latest.revision: 34
author: JimDaly
ms.author: jdaly
ms.reviewer: pehecke
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9f400988376ccfe1427df8dd6036fb61b85aa987
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154940"
---
# <a name="common-data-service-web-api-versions"></a>Common Data ServiceVersiones de la API web

A partir de la v9.0 de Dynamics 365, la API web admite diferencias específicas de versión en el mismo entorno.  
  
Esto es diferente del comportamiento para las versiones de v8.*x*. En las versiones anteriores nuevas funcionalidades estaban disponibles para cualquier versión del servicio según la actualización aplicada al entorno.  Después de la actualización a v8.2, los servicios de v8.0 y v8.1 eran idénticos. Esto fue posible porque todos los cambios eran adición. Nada se ha quitado ni se han introducido cambios importantes. Como consecuencia, la versión específica que se hace referencia en la dirección URL del servicio de la versión 8.*x* no era realmente importante.  
  
El futuro de las funcionalidades del servicio puede cambiar, incluidos cambios potencialmente importantes como quitar operaciones específicas. Esto le permitirá de las mejoras que se aplicarán a la forma en curso. En este tema se registra cualquier diferencia específica de la versión y las limitaciones en la API web aún no se ha igualado con el servicio de la organización.  
  
## <a name="web-api-version-specific-differences"></a>Diferencias específicas de las versiones de la API web

<a name="BKMK_fetchresponse"></a>

### <a name="encoding-for-special-characters-in-fetchxml-query-response"></a>Codificación para caracteres especiales en respuesta de la consulta FetchXML

Para las versiones v8.*x*, la respuesta de las consultas FetchXML que contengan entidades de vínculo y sus atributos contiene caracteres Unicode especiales, por ejemplo '.' se convierte en '_x002e_' y '@' se convierte en '_x0040_'. Esta codificación de caracteres especiales no está presente en la respuesta de las consultas FetchXML para la versión v9.*x* .

### <a name="same-name-for-entity-and-attribute"></a>Mismo nombre para entidad y atributo

Si el nombre de una entidad y uno de los atributos es el mismo, se anexa “1 "al nombre de atributo en instancias v8.x. Por ejemplo, si una entidad **new_zipcode** tiene un atributo con el nombre **new_zipcode**, el nombre del atributo cambiará a **new_zipcode1**.

Para instancias de v9.*x*, no se anexará nada al nombre del atributo.

## <a name="new-operations-added"></a>Nuevas operaciones agregadas  

Las operaciones siguientes se han agregado a la API web para la versión v9.x.  
  
||||  
|-|-|-|  
|<xref:Microsoft.Crm.Sdk.Messages.GrantAccessRequest>|<xref:Microsoft.Crm.Sdk.Messages.ModifyAccessRequest>|<xref:Microsoft.Crm.Sdk.Messages.RetrieveSharedPrincipalsAndAccessRequest>|  

## <a name="web-api-limitations"></a>Limitaciones de la API web de   

La API web de Common Data Service proporciona paridad completa con las capacidades de servicio de la organización. Para Common Data Service, este tema describe las limitaciones que proceden de Common Data Service versión v8.x. Para las versiones anteriores, consulte [Limitaciones de API Web de Dynamics CRM 2016](https://msdn.microsoft.com/library/mt628816\(CRM.8\).aspx).  
 
> [!NOTE] 
> Si ha definido una acción personalizada que incluya un valor de devolución complejo y un valor de devolución simple, una acción correspondiente no estaba disponible en la API web pero estaba disponible mediante el extremo de 2011 SOAP. Un valor de devolución complejo es una `EntityReference`, `Entity`, o `EntityCollection`. Puede tener cualquier combinación de valores de devolución simples o un solo valor de devolución complejo. Más información: [Crear sus propias acciones](/dynamics365/customer-engagement/developer/create-own-actions).

### <a name="see-also"></a>Vea también  

[Usar la API web de Common Data Service](overview.md)<br />
[Autenticarse en Common Data Service con la API web](authenticate-web-api.md)<br />
[Tipos y operaciones de API web](web-api-types-operations.md)<br />
[Realizar operaciones mediante la API web](perform-operations-web-api.md)