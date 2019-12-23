---
title: Tipos de entidades | MicrosoftDocs
ms.custom: ''
ms.date: 05/30/2018
ms.reviewer: ''
ms.service: powerapps
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
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ebf5b794bcfc7ec01abf08315f1dbf59ce6e4808
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2869916"
---
# <a name="types-of-entities"></a>Tipos de entidades

Antes de crear o modificar entidades en Common Data Service, debe comprender que hay diferentes tipos de entidades. Una vez que se crea una entidad personalizada, estos tipos no se pueden cambiar. Las dos divisiones principales se basan en la propiedad de la entidad y en si las entidades son entidades de actividad.  
  
<a name="BKMK_EntityOwnership"></a>

## <a name="entity-ownership"></a>Propiedad de la entidad  

Existen cuatro tipos diferentes de propiedad de la entidad. Cuando cree una entidad personalizada las únicas opciones son **propiedad de un usuario o equipo** o **propiedad de la organización**, pero debe tener en cuenta que otras entidades tienen tipos de propiedad diferentes.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|**Propiedad del negocio**|Los datos de estas entidades pertenecen a la unidad de negocio. El acceso a los datos se puede controlar en el nivel de unidad de negocio.|  
|**Ninguno**|Los datos no son propiedad de otra entidad.|  
|**Propiedad de la organización**|Los datos pertenecen a la organización. El acceso a los datos se controla en el nivel de organización.|  
|**Propiedad del usuario o el equipo**|Los datos pertenecen a un usuario o un equipo. Las acciones que se pueden realizar en estos registros se pueden controlar en un nivel de usuario.|  
  
  
> [!IMPORTANT]
>  Cuando se crea una entidad, no puede cambiar la propiedad. Antes de crear una entidad, asegúrese de que elija el tipo adecuado de propiedad. Si determina posteriormente que la entidad personalizada debe ser de un tipo diferente, tendrá que eliminarla y crear una nueva.
  
<a name="BKMK_ActivityEntities"></a>

## <a name="activity-entities"></a>Entidades de actividad

Una actividad puede considerarse cualquier acción de la que se puede crear una entrada en un calendario. Una actividad puede tener dimensiones de tiempo (hora de inicio, hora de detención, fecha de vencimiento y duración) que ayudan a determinar cuándo se ha producido la acción o cuándo tendrá lugar. Las actividades también contienen datos que ayudan a determinar qué acción representa la actividad, por ejemplo, el tema y la descripción. Una actividad se puede abrir, cancelar o completar. El estado completado de una actividad tendrá varios valores de estado secundarios asociados para aclarar el modo en que la actividad se ha completado.  
  
Las entidades de actividad solo pueden pertenecer a un usuario o equipo, no pueden ser propiedad de una organización.  
  
En la tabla siguiente se muestran las entidades de actividad que están disponibles en un entorno predeterminado de Common Data Service.
  
|Nombre|Descripción|Mostrar en los menús de actividades|Referencia|
|----------|-----------------|----------------|---------------|  
|**Cita**|Compromiso que representa un intervalo de tiempo con las fechas de inicio y fin, y la duración.|Sí|[Cita](/powerapps/developer/common-data-service/reference/entities/appointment)|
|**Correo electrónico**|Actividad entregada con protocolos de correo electrónico.|Sí|[Correo electrónico](/powerapps/developer/common-data-service/reference/entities/email)|
|**Fax**|Actividad que mantiene un seguimiento del resultado de llamadas y el número de páginas para un fax y que, opcionalmente, almacena una copia electrónica del documento.|Sí|[Fax](/powerapps/developer/common-data-service/reference/entities/fax)|
|**Carta**|Actividad que realiza un seguimiento de la entrega de una carta. Actividad que puede contener la copia electrónica de la carta.|Sí|[Carta](/powerapps/developer/common-data-service/reference/entities/letter)|
|**Llamada de teléfono**|Actividad para mantener un seguimiento de una llamada de teléfono.|Sí|[PhoneCall](/powerapps/developer/common-data-service/reference/entities/phonecall)|
|**Cita periódica**|Cita principal de una serie de citas periódicas.|Sí|[Maestro recurrente de la cita](/powerapps/developer/common-data-service/reference/entities/recurringappointmentmaster)|
|**Tarea**|Actividad genérica que representa el trabajo que se debe realizar.|Sí|[Tarea](/powerapps/developer/common-data-service/reference/entities/task)|
  
Puede crear nuevas entidades de actividad personalizadas. Por ejemplo, puede crear una entidad de actividad personalizada para registrar comunicaciones de mensajes instantáneos. Crear una entidad de actividad es diferente de crear una entidad de no actividad porque no especifica un campo principal. Todas las entidades de actividad tienen **Campo principal** establecido en **Asunto** y otros campos comunes que se definen mediante la entidad Actividad. Esto permite que se incluyan todos los tipos de actividades en una vista que solo muestra los campos comunes.  

> [!NOTE]
> No puede crear una actividad personalizada mediante el portal de Power Apps. Debe abrir el explorador de soluciones con el botón **Avanzado**.
  
Para crear una entidad de actividad personalizada, seleccione **Definir como entidad de actividad**. Después de seleccionar esto, verá que la opción **Mostrar en los menús de actividades** está seleccionada. Esta opción permite a las personas crear este tipo de actividad en los menús de actividad. No está activada para las actividades que suelen asociarse con determinados eventos y que se crean detrás mediante código o por un flujo de trabajo. Después de guardar la entidad, no se puede cambiar la configuración.  

### <a name="see-also"></a>Vea también
[Crear o editar entidades](create-edit-entities.md)
