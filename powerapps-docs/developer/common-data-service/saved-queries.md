---
title: Consultas guardadas (Common Data Service) | Microsoft Docs
description: Conozca cómo las consultas guardadas aumentan el entorno de búsqueda en Common Data Service.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="saved-queries"></a>Consultas guardadas

Las consultas guardadas son las entidades de negocio que definen los parámetros y los criterios de una búsqueda del entorno de Common Data Service. Las consultas guardadas admiten búsquedas de entidades cruzadas. Hay dos entidades disponibles para consultas en relación con el entorno de Common Data Service.  
  
- Una *consulta de usuario*, llamada una vista guardada en la aplicación, es propiedad de un usuario individual, se puede asignar y compartir con otros usuarios, y pueden verla otros usuarios en función de sus privilegios de acceso. Esto es adecuado para consultas usadas frecuentemente que abarcan tipos de entidad y consultas que realizan agregación. Más información: [Editar UserQuery](reference/entities/userquery.md) 

- Una *consulta guardada*, denominada una vista en la aplicación, es propiedad de una organización que la hace visible para todos los usuarios de la organización. Las consultas guardadas (vistas) se usan para las vistas definidas para una entidad y para los filtros y plantillas de Dynamics 365 for Outlook. Más información: [Editar SavedQuery](reference/entities/savedquery.md) 
  
 Se genera una consulta en forma de una instrucción FetchXML y a continuación se asigna al atributo `UserQuery.FetchXml`. Esta consulta se puede ejecutar mediante el mensaje <xref:Microsoft.Crm.Sdk.Messages.ExecuteByIdUserQueryRequest>.  
  
 Puede ver la consulta de usuario en la sección **Búsqueda avanzada** de la aplicación basada en modelos, así como en la lista desplegable **Ver** de una entidad.  Puede exportar el valor del atributo `UserQuery.FetchXml` con el botón **Descargar FetchXML** en el cuadro de diálogo **Búsqueda avanzada**.  
  
## <a name="use-web-api-to-execute-saved-queries"></a>Uso de la API web para ejecutar consultas guardadas

Para conocer sobre la ejecución de una consulta de usuario y consulta guardada con API web, consulte [Recuperar y ejecutar consultas predefinidas](webapi/retrieve-and-execute-predefined-queries.md)

## <a name="use-organization-service-to-execute-saved-queries"></a>Uso del servicio de la organización para ejecutar consultas guardadas

Puede usar los mensajes <xref:Microsoft.Crm.Sdk.Messages.ExecuteByIdUserQueryRequest> y <xref:Microsoft.Crm.Sdk.Messages.ExecuteByIdSavedQueryRequest> para ejecutar consulta de usuario y consulta guardada respectivamente.
