---
title: Tipos de entidades | Microsoft Docs
ms.custom: ''
ms.date: 05/30/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 2f3f6053-0b9e-41e7-bd94-2239351e9f4b
caps.latest.revision: 41
ms.author: matp
manager: kvivek
ms.openlocfilehash: 60e16ff8cb5c40a37cf0a5243b420f77c4a695bb
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39712791"
---
# <a name="types-of-entities"></a>Tipos de entidades

Antes de crear o editar entidades en Common Data Service for Apps, debe tener claro que hay distintos tipos de entidades. Una vez que se crea una entidad, estos tipos no se pueden cambiar. Las dos divisiones principales se basan en la propiedad de entidad y en si las entidades son entidades de actividad.  
  
<a name="BKMK_EntityOwnership"></a>

## <a name="entity-ownership"></a>Propiedad de entidad  

Hay cuatro tipos distintos de propiedad de entidad. Cuando crea o personaliza una entidad, las únicas opciones son **propiedad del usuario o del equipo** o **propiedad de la organización**, pero debería saber que otras entidades tienen tipos de propiedad distintos.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|**Business-owned**|Los datos de estas entidades pertenecen a la unidad de negocio. El acceso a los datos se puede controlar en el nivel de la unidad de negocio.|  
|**None**|Los datos no pertenecen a otra entidad.|  
|**Organization-owned**|Los datos pertenecen a la organización. El acceso a los datos se controla en el nivel de la organización.|  
|**User or Team Owned**|Los datos pertenecen a un usuario o un equipo. Las acciones que se pueden realizar en estos registros se pueden controlar en el nivel de un usuario.|  
  
  
> [!IMPORTANT]
>  Una vez que se crea la unidad, no puede cambiar la propiedad. Antes de crear una entidad, asegúrese de elegir correctamente el tipo de propiedad. Si más tarde determina que la entidad personalizada debe tener un tipo distinto, deberá eliminarla y crearla de nuevo.
  
<a name="BKMK_ActivityEntities"></a>

## <a name="activity-entities"></a>Entidades Activity

Una actividad se puede considerar como cualquier acción para la que se puede realizar una entrada en un calendario. Una actividad tiene las dimensiones de tiempo (hora de inicio, hora de detención, fecha de vencimiento y duración) que ayudan a determinar cuándo se produjo o producirá la acción. Las actividades también contienen datos que ayudan a determinar cuál es la acción que la actividad representa, por ejemplo, el asunto y la descripción. Es posible abrir, cancelar o completar una actividad. El estado completado de una actividad tendrá varios valores de subestado asociados para clarificar la manera en que se completó a actividad.  
  
Las entidades de actividad solo pueden ser propiedad de un usuario o un equipo, no pueden ser propiedad de una organización.  
  
En la tabla siguiente, se muestran entidades de actividad que están disponibles en un entorno de CDS for Apps predeterminado.
  
|Nombre|Descripción|Se muestra en los menús de actividad|Referencia|
|----------|-----------------|----------------|---------------|  
|**Appointment**|Compromiso que representa un intervalo de tiempo con horas de inicio y fin, y duración.|Sí|[Appointment](/powerapps/developer/common-data-service/reference/entities/appointment)|
|**Email**|Actividad que se suministra mediante protocolos de correo electrónico.|Sí|[Email ](/powerapps/developer/common-data-service/reference/entities/email)|
|**Fax**|Actividad que mantiene un seguimiento del resultado de llamadas y el número de páginas para un fax y que, opcionalmente, almacena una copia electrónica del documento.|Sí|[Fax](/powerapps/developer/common-data-service/reference/entities/fax)|
|**Letter**|Actividad que realiza el seguimiento de la entrega de una carta. La actividad puede contener la copia electrónica de la carta.|Sí|[Letter](/powerapps/developer/common-data-service/reference/entities/letter)|
|**Phone Call**|Actividad para realizar el seguimiento de una llamada telefónica.|Sí|[PhoneCall ](/powerapps/developer/common-data-service/reference/entities/phonecall)|
|**Recurring Appointment**|La cita principal de una serie de citas periódicas.|Sí|[RecurringAppointmentMaster](/powerapps/developer/common-data-service/reference/entities/recurringappointmentmaster)|
|**Task**|Actividad genérica que representa el trabajo que se debe realizar.|Sí|[Task](/powerapps/developer/common-data-service/reference/entities/task)|
  
Puede crear nuevas entidades de actividad personalizadas. Por ejemplo, podría crear una entidad de actividad personalizada para registrar comunicaciones por mensajes instantáneos. Crear una entidad de actividad es distinto de crear una entidad que no es de actividad, porque no se especifica un campo principal. Todas las entidades de actividad tiene un **campo principal** establecido en **Asunto** y otros campos comunes, definidos por la entidad de actividad. Esto permite que se muestren todos los tipos de actividades en una vista en la que solo aparecen los campos comunes.  

> [!NOTE]
> No puede usar el portal de PowerApps para crear una actividad personalizada. Debe abrir el Explorador de soluciones con el botón **Avanzadas**.
  
Para crear una entidad de actividad personalizada, seleccione **Definir como una entidad de actividad**. Después de seleccionar esto, verá está seleccionado **Se muestra en los menús de actividad**. Esta configuración permite que los usuarios creen este tipo de actividad en los menús de la actividad. Esta opción no está seleccionada para las actividades que habitualmente se asocian con eventos específicos y que se crean detrás mediante el código o un flujo de trabajo. Después de guardar la entidad, no puede cambiar esta configuración.  

### <a name="see-also"></a>Vea también
[Crear o editar entidades](create-edit-entities.md)
