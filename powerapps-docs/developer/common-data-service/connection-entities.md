---
title: Usar conexiones para vincular registros entre sí (Common Data Service) | Microsoft Docs
description: Las entidades de conexión le permiten habilitar, crear y consultar conexiones.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7ad1b1874f71c958204119a35440922361746252
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749578"
---
# <a name="use-connections-to-link-records-to-each-other"></a>Usar conexiones para vincular registros entre sí

Las *conexiones* proporcionan una forma flexible de conectar y describir las relaciones entre los dos registros de entidad de Common Data Service. Ayudan a promover el trabajo en equipo, la colaboración y la administración eficaz de los procesos de negocio y de ventas. Las conexiones le permiten establecer fácilmente asociaciones entre usuarios, contactos, ofertas, pedidos de ventas y muchos otros registros de entidad. A los registros de la asociación se les pueden asignar roles determinados que ayudan a definir el objetivo de la relación.  
  
 Las conexiones proporcionan las capacidades siguientes:  
  
- Una forma fácil y flexible de crear una conexión entre dos registros de la mayoría de los tipos de entidades de Common Data Service. Todas las entidades personalizadas y de negocio que pueden personalizarse se pueden habilitar para establecer conexiones.  
  
- Una opción para agregar información útil, como una descripción de la conexión y su duración.  
  
- La capacidad de crear roles de conexión que describen la relación entre dos registros, como la relación entre un doctor y un paciente o entre un jefe y un empleado.  
  
- Una forma rápida de crear varias conexiones y roles para un registro determinado. Por ejemplo, un contacto puede tener varias relaciones con otros contactos, cuentas o contratos. En cada relación, un contacto puede desempeñar un rol distinto.  
  
- Información para generar consultas y crear gráficos. Puede buscar todas las conexiones y los roles de conexión de un registro específico y crear gráficos para representar visualmente las conexiones.  
  
- Compatibilidad con flujos de trabajo y auditorías para mejorar y automatizar procesos de negocio.  
  
## <a name="enabling-and-creating-connections"></a>Habilitación y creación de conexiones  
 Puede habilitar cualquier entidad personalizada o personalizable para las conexiones actualizando los metadatos de la entidad. Use el mensaje <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest> para establecer la propiedad <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsConnectionsEnabled> en `true`.  
  
 Para crear una conexión entre dos registros, use la entidad `Connection`. Debe especificar un registro desde el que va a crear una conexión (el origen) y un registro al que va a conectar (el destino). Use el atributo `Connection.Record1Id` para especificar el registro de entidad de origen y el atributo `Connection.Record2Id` para especificar el registro de entidad de destino. También puede especificar la duración y la descripción de la conexión. Para describir la relación entre los participantes de la conexión, use los roles de conexión. Para especificar los roles de conexión, use el atributo `Connection.Record1RoleId` y el atributo `Connection.Record2RoleId`.  
  
## <a name="querying-connections"></a>Consulta de conexiones  
 La consulta de conexiones proporciona los datos valiosos que puede usar para crear informes o gráficos. Puede consultar conexiones por un registro de entidad, un tipo de entidad (código de tipo de entidad), para un rol determinado u otros criterios. Los siguientes son ejemplos de cómo puede consultar conexiones:  
  
 Por un registro de entidad:  
  
- Mostrar todas las conexiones de la cuenta A.  
  
- Mostrar todos los roles de la cuenta A.  
  
  Para un tipo de entidad (mediante los códigos de tipo de entidad):  
  
- Mostrar todos los roles de la entidad Competidor.  
  
- Encontrar el número total de roles de la entidad Cuenta.  
  
  Por un rol:  
  
- Encontrar todas las conexiones cuya cuenta A es “Proveedor”.  
  
- Encontrar todas las oportunidades abiertas de más de 20.000 USD cuyo contacto B sea “Comercial”.  
  
- Encontrar todos los roles coincidentes para un rol de “Doctor”, como “Paciente”, “Enfermera” o “Auxiliar de clínica”.  
  
- Encontrar todos los contactos cuyo rol sea “Amigo”.  
  
> [!IMPORTANT]
>  Cuando se crea un registro de entidad conexión, se crean dos registros en la base de datos. El primer registro representa un origen para la conexión de destino y el segundo registro representa un destino para la conexión de origen. Esto garantiza que una consulta encontrará todas las conexiones en las que participa el registro, independientemente de si es un registro de origen o un registro de destino en la conexión.  
  
### <a name="see-also"></a>Vea también  
 [Describir una relación entre entidades con roles de conexión](describe-relationship-entities-connection-roles.md)   
 [Entidad de conexión](/reference/entities/connection.md)   
 [Entidad ConnectionRole](/reference/entities/connectionrole.md)   
 [Código de ejemplo para entidades de conexión](/dynamics365/customer-engagement/developer/sample-code-connection-entities)   
 [Entidades de administración de empresas](/dynamics365/customer-engagement/developer/business-management-entities)   
 [Ver y analizar datos con visualizaciones y paneles en Dynamics 365](/dynamics365/customer-engagement/developer/customize-dev/customize-visualizations-dashboards)   
 [Calendario fiscal y entidades de territorio](/dynamics365/customer-engagement/developer/fiscal-calendar-and-territory-entities)