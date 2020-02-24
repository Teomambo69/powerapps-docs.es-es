---
title: Información general de auditoría (Common Data Service) | Microsoft Docs
description: Lea cómo la capacidad de auditoría de Common Data Service se puede usar para registrar cambios de datos de atributos y entidades con el tiempo para usarlos para fines de análisis e informes.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 71f39d432e551df456f3d339155d1f3105d6891b
ms.sourcegitcommit: 5bfd0448f1d5ca3d938e3bd928d1dd3d4042afff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/28/2020
ms.locfileid: "2992810"
---
# <a name="auditing-overview"></a>Información general de auditoría

Las organizaciones a menudo deben cumplir varias normativas para garantizar la disponibilidad del historial de la interacción con el cliente, registros de auditoría, informes de acceso e informes de seguimiento de incidentes de seguridad. Es posible que las organizaciones deseen realizar un seguimiento de los cambios en los datos de Common Data Service por motivos de seguridad y análisis.  
  
 Common Data Service admite una posibilidad de auditoría en la que los cambios en los datos de entidad y atributo en una organización se pueden registrar con el tiempo para usarlos para fines de análisis e informes. La auditoría se admite en todas las entidades y atributos personalizados y en la mayoría de entidades y atributos personalizables. La auditoría no se admite en los cambios en los metadatos, las operaciones de recuperación, las operaciones de exportación ni durante la autenticación. Para obtener información sobre cómo configurar la auditoría, vea [Configurar entidades y atributos para auditoría](configure-entities-attributes-auditing.md).  
  
## <a name="supported-for-auditing"></a>Se admite para auditoría  
 A continuación se muestran las capacidades de auditoría para Common Data Service:  
<!-- TODO: Jim, I don't think this is online only. Please correct the tokens here. -->
  
* Auditoría de entidades personalizables
* Auditoría de entidades personalizadas
* Configurar las entidades para auditoría
* Configurar los atributos para auditoría
* Visualización de traza de auditoría basada en privilegios
* Visualización resumen de traza de auditoría basada en privilegios
* Eliminación del registro de auditoría para una base de datos SQL particionada  
* Eliminación del registro de auditoría para una base de datos SQL no particionada 
* Auditoría de las operaciones de creación, actualización y eliminación de registros
* Auditoría de relaciones (1:N, N:N) 
* Auditoría de eventos de auditoría
* Auditoría de acceso de usuario
* Adherencia a normas reguladoras
* Las API de auditoría para desarrolladores
  
## <a name="not-supported-for-auditing"></a>Lo que no se admite para auditoría  
 A continuación se muestra lo que no se puede auditar de Common Data Service:  
  
* Auditoría de las operaciones de lectura
* Auditoría de cambios en los metadatos 
  
## <a name="key-concepts"></a>Conceptos clave  
 Las siguientes viñetas identifican algunos conceptos clave de auditoría:  
  
-   Puede habilitar o deshabilitar la auditoría entre organizaciones, entidades y atributos. Si la auditoría no está habilitada en el nivel de organización, la auditoría de entidades y atributos, incluso si está habilitada, no se produce. De forma predeterminada, está habilitada la auditoría en todos los atributos de entidad auditables, pero está deshabilitada en el nivel de entidad y de organización.  
  
-   La capacidad de recuperar y mostrar el historial de auditoría está limitada a los usuarios que poseen determinados privilegios de seguridad: Ver historial de auditoría y Ver resumen de auditoría. Existen también privilegios específicos de particiones: Ver particiones de auditoría y Eliminar particiones de auditoría. Vea la documentación de solicitud de mensajes específica para obtener información acerca de los privilegios necesarios para cada mensaje.  
  
-   Los cambios en los datos auditados se almacenan en registros de la entidad de **auditoría**.  
  
## <a name="data-that-can-be-audited"></a>Datos que se pueden auditar  
 La siguiente lista identifica los datos y las operaciones que se pueden auditar:  
  
-   Operaciones de creación, actualización y eliminación en registros.  
  
-   Cambios en los privilegios compartidos de un registro.  
  
-   Asociación o anulación de asociación N:N de registros.  
  
-   Cambios en los roles de seguridad.  
  
-   Cambios en la auditoría en el nivel de entidad, atributo y organización. Por ejemplo, habilitación de la auditoría en una entidad.  
  
-   Eliminación de los registros de auditoría  
  
-   Cuándo (fecha y hora) un usuario obtiene acceso a los datos de Common Data Service, durante cuánto tiempo y desde qué cliente.  
  
 La habilitación o deshabilitación de la seguridad a nivel de campo estableciendo el atributo <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.IsSecured> no se puede auditar.  
  
### <a name="see-also"></a>Vea también
   
 [Configurar entidades y atributos para auditoría](configure-entities-attributes-auditing.md) 
