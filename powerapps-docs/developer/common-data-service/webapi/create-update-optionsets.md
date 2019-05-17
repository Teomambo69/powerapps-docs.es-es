---
title: Crear y actualizar conjuntos de opciones utilizando la API web (Common Data Service) | Microsoft Docs
description: Aprenda a crear y actualizar entidades. Common Data Service usa una arquitectura controlada por metadatos que proporciona flexibilidad para crear entidades personalizadas y atributos adicionales de las entidades del sistema.
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
caps.latest.revision: 15
author: brandonsimons
ms.author: jdaly
ms.reviewer: susikka
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="create-and-update-option-sets-using-the-web-api"></a>Crear y actualizar conjuntos de opciones mediante la API web

Normalmente, usa conjuntos de opciones *globales* para definir campos de manera que los campos diferentes puedan compartir el mismo conjunto de opciones, que se mantiene en una ubicación. A diferencia de conjuntos de opciones *locales* que se definen solo para un atributo específico, puede volver a usar conjuntos de opciones globales. También los verá usados en los parámetros de solicitudes de manera similar a una enumeración.  
  
Cuando define un conjunto de opciones global mediante una solicitud POST en *[URI de organización]*`/api/data/v9.0/GlobalOptionSetDefinitions`, se recomienda dejar que el sistema asigne un valor. Realice esta acción al pasar un valor **null** al crear la nueva instancia de `OptionMetadata`. Al definir una opción, contendrá un determinada prefijo de valor de opción específico del contexto del editor establecido para la solución en la que se crea el conjunto de opciones. Este prefijo ayuda a reducir la oportunidad de crear conjuntos de opciones duplicados para una solución administrada, y en cualquier conjunto de opciones que están definidos en organizaciones donde está instalada la solución administrada. Para obtener más información, consulte [Combinar opciones del conjunto de opciones](../understand-managed-solutions-merged.md#merge-option-set-options).

 ## <a name="messages"></a>Mensajes  
 La siguiente tabla enumera los mensajes que se pueden usar con los conjuntos de opciones globales.  
  
|Mensaje|Operación de API web|  
|--|--|
|CreateOptionSet|Use la solicitud `POST` para *[URI de organización]*`/api/data/v9.0/GlobalOptionSetDefinitions`.|
|DeleteOptionSet|Use la solicitud `DELETE` para *[URI de organización]*`/api/data/v9.0/GlobalOptionSetDefinitions(`*metadataid*`)`.|
|RetrieveAllOptionSets|Use la solicitud `GET` para *[URI de organización]*`/api/data/v9.0/GlobalOptionSetDefinitions`.| 
|RetrieveOptionSet|Use la solicitud `GET` para *[URI de organización]*`/api/data/v9.0/GlobalOptionSetDefinitions(`*metadataid*`)`.|   


La siguiente tabla enumera los mensajes que se pueden usar con los conjuntos de opciones globales y locales.

|Mensaje|Operación de API web|  
|--|--|
|DeleteOptionValue</br>Elimina uno de los valores de un conjunto de opciones globales.|<xref href="Microsoft.Dynamics.CRM.DeleteOptionValue?text=DeleteOptionValue Action" />  
|InsertOptionValue</br>Inserta una opción en un conjunto de opciones globales.|<xref href="Microsoft.Dynamics.CRM.InsertOptionValue?text=InsertOptionValue Action" />| 
|InsertStatusValue</br>Inserta una nueva opción en el conjunto de opciones globales usado en el atributo de `Status`.|<xref href="Microsoft.Dynamics.CRM.InsertStatusValue?text=InsertStatusValue Action" />|
|OrderOption</br>Cambia el orden relativo de las opciones de un conjunto de opciones.|<xref href="Microsoft.Dynamics.CRM.OrderOption?text=OrderOption Action" />|
|UpdateOptionSet|Use la solicitud `PUT` con un <xref href="Microsoft.Dynamics.CRM.OptionSetMetadata?text=OptionSetMetadata EntityType" /> para *[URI de organización]*`/api/data/v9.0/GlobalOptionSetDefinitions(`*metadataid*`)/Microsoft.Dynamics.CRM.OptionSetMetadata`.<br />Para un conjunto de opciones locales use *[URI de organización]*`/api/data/v9.0/EntityDefinitions(`*metadataid*`)/Attributes(`*metadataid*`)/Microsoft.Dynamics.CRM.PicklistAttributeMetadata/OptionSet`.|
|UpdateOptionValue</br>Actualiza una opción de un conjunto de opciones globales.|<xref href="Microsoft.Dynamics.CRM.UpdateOptionValue?text=UpdateOptionValue Action" />|
|UpdateStateValue</br>Inserta una nueva opción en el conjunto de opciones usado en el atributo de `Status`.|<xref href="Microsoft.Dynamics.CRM.UpdateStateValue?text=UpdateStateValue Action" />|

### <a name="see-also"></a>Vea también

[Conjunto de opciones personalizadas](../org-service/metadata-option-sets.md)