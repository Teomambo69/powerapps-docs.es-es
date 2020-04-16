---
title: Simultaneidad optimista (Common Data Service) | Microsoft Docs
description: La simultaneidad optimista ofrece la capacidad de que las aplicaciones detecten si un registro de entidad ha cambiado en el servidor desde el momento en que la aplicación recuperó el registro y cuando intenta actualizar o eliminar ese registro.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: df56a86d2f7b111904bf35343f846431f13acc7d
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156116"
---
# <a name="optimistic-concurrency"></a>Simultaneidad optimista

En un sistema con varios subprocesos y usuarios como Power Apps, las cambios en operaciones y datos suceden a menudo paralelamente. Un problema surge cuando dos o más operaciones de actualización o de eliminación del mismo dato suceden al mismo tiempo. Esta situación podría producir la pérdida de datos. La característica de simultaneidad optimista ofrece la capacidad de que las aplicaciones detecten si un registro de entidad ha cambiado en el servidor desde el momento en que la aplicación recuperó el registro y cuando intenta actualizar o eliminar ese registro.  
  
 La simultaneidad optimista se admite en todas las entidades predefinidas habilitadas para sincronización sin conexión y todas las entidades personalizadas. Puede determinar si una entidad admite simultaneidad optimista recuperando metadatos de la entidad con una llamada de SDK, o viendo los metadatos mediante el [Explorador de metadatos](browse-your-metadata.md), y comprobar si el atributo **IsOptimisticConcurrencyEnabled** está establecido como `true`. Para las entidades personalizadas, esta propiedad se establece como `true` de forma predeterminada.  
  
<a name="bkmk_enable"></a>   
## <a name="enable-optimistic-concurrency"></a>Habilitar simultaneidad optimista  
 Puede habilitar el comportamiento de comprobación de simultaneidad optimista cuando ejecuta una <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> estableciendo la propiedad <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest.ConcurrencyBehavior> de la solicitud como <xref:Microsoft.Xrm.Sdk.ConcurrencyBehavior.IfRowVersionMatches>. De igual modo, para una <xref:Microsoft.Xrm.Sdk.Messages.DeleteRequest>, establecería la propiedad <xref:Microsoft.Xrm.Sdk.Messages.DeleteRequest.ConcurrencyBehavior>.  
  
 Cuando usa el contexto de servicio de la organización para realizar cambios de datos, establezca <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.ConcurrencyBehavior> en el objeto <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>. Este valor se pasará a todos los mensajes de **UpdateRequest** y **DeleteRequest** usados por el **OrganizationServiceContext** cuando se llama a <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges>.  
  
 El comportamiento de simultaneidad optimista puede configurarse únicamente con una llamada del SDK. Actualmente no existe un valor para él en un formulario de la aplicación web.  
  
## <a name="apply-optimistic-concurrency-using-web-api"></a>Aplicar simultaneidad optimista utilizando la API web

Para obtener más información sobre el uso de la API web para aplicar simultaneidad optimista, vea [Aplicar la simultaneidad optimista](webapi/perform-conditional-operations-using-web-api.md##apply-optimistic-concurrency)


## <a name="apply-optimistic-concurrency-using-organization-service"></a>Aplicar la simultaneidad optimista mediante el servicio de la organización

Para obtener más información sobre el uso del servicio de la organización para aplicar simultaneidad optimista, vea [Comportamiento de la simultaneidad optimista](org-service/entity-operations-update-delete.md##optimistic-concurrency-behavior)
  
<a name="bkmk_handle"></a>   
## <a name="handle-exceptions"></a>Administrar excepciones  
 Hay varias condiciones de error que se pueden devolver en [FaultException](https://msdn.microsoft.com/library/ms576199\(v=vs.110\).aspx)\<<xref:Microsoft.Xrm.Sdk.OrganizationServiceFault>> desde la llamada de servicio web cuando se usa simultaneidad optimista.  
  
- **ConcurrencyVersionMismatch** (código=-2147088254)  
  
     Cuando se proporciona una versión de fila y se indica el comportamiento de **IfVersionMatches**, si la versión del registro existente no coincide con la versión de fila proporcionada en la solicitud, se devuelve un error.  
  
- **ConcurrencyVersionNotProvided** (código= -2147088253)  
  
     Cuando se indica el comportamiento **IfVersionMatches** y no se proporciona un valor para la versión de fila, se devuelve un error.  
  
- **OptimisticConcurrencyNotEnabled** (código=-2147088243)  
  
     Cuando el comportamiento **IfVersionMatches** se indica en una actualización a una entidad, donde simultaneidad optimista no está habilitada, se devuelve un error.  
  
  Puede comprobar la propiedad [Code](https://msdn.microsoft.com/library/system.servicemodel.faultexception.code\(v=vs.110\).aspx) del error devuelto para determinar si el error se relaciona con la simultaneidad optimista. Los códigos de las condiciones de error que aparecieron anteriormente se obtuvieron del código auxiliar ErrorCodes.cs.  
  
