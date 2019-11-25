---
title: Entidades de cola (Common Data Service) | Microsoft Docs
description: Las colas en PowerApps son fundamentales para organizar, asignar prioridades y supervisar el progreso de su trabajo.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
ms.openlocfilehash: 6452dd50cb54e1c7c3aa5a57b9d7751ba9f13af7
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749811"
---
# <a name="queue-entities"></a>Entidades de cola

Las *colas* en son fundamentales para organizar, asignar prioridades y supervisar el progreso de su trabajo. Como ubicación central para la administración del trabajo, las colas le ayudarán a procesar casos, responder a las llamadas de servicio o enviar la información del producto a los posibles clientes. Desde el punto de vista de programación, una cola es una recopilación de elementos de cola. Un elemento de cola sirve como contenedor para un registro de entidad, como una tarea, un correo electrónico o un caso que necesita procesamiento. Ver [Entidad de cola](reference/entities/queue.md)

> [!NOTE]
> Para obtener información sobre cómo trabajar con colas en la interfaz de usuario, consulte [Información general de colas](/dynamics365/customer-engagement/customer-service/set-up-queues-manage-activities-cases).  
  
La siguiente información pertenece a las colas:  
  
-   Todas las entidades personalizables pueden habilitarse para colas.  
  
-   Las colas pueden ser públicas o privadas. Los elementos de cola privada solo son visibles para los integrantes de la cola.  
  
-   Una cola privada se crea automáticamente para cada nuevo usuario o equipo.  
  
-   Una cola puede contener varios tipos de entidades, como tareas, mensajes de correo electrónico o casos.  
  
-   Una cola contiene información del usuario que está trabajando en un elemento específico de la cola. Esto le ayuda a administrar los recursos más eficazmente y a evitar la duplicación de trabajo.  
  
-   Las colas se pueden habilitar para los flujos de trabajo y la auditoría. Esto ayuda a mejorar la productividad y a realizar el seguimiento de los datos de la entidad y el atributo para el análisis y la creación de informes futuros.  
  
<a name="BKMK_MemberCapabilities"></a>   
## <a name="members-capabilities"></a>Capacidades de los miembros  
 Las colas se clasifican en colas *públicas* o *privadas*. Las colas privadas tienen usuarios individuales como miembros para facilitar el control del acceso a las colas. Si agrega un equipo a una cola privada, todos los integrantes del equipo serán integrantes de la cola privada.  
  
<a name="BKMK_publicAndPrivateQueues"></a>   
## <a name="public-and-private-queues"></a>Colas públicas y privadas  
 El atributo [QueueViewType](reference/entities/queue.md#BKMK_QueueViewType) es una lista desplegable que define si una cola es pública o privada.  
  
-   Todas las colas del usuarios son colas privadas del usuario: Solo este podrá ver los elementos de sus colas privadas.  
  
-   Las colas del equipo se marcarán como privadas con los miembros: el propietario del equipo y todos los integrantes del equipo podrán ver la cola en la aplicación.  
  
-   El resto de las colas son públicas. Todos los usuarios con privilegios de lectura para la entidad de cola podrán ver estas colas.  
  
<a name="BKMK_QueueAttributes"></a>   
## <a name="attributes-used-to-manage-queues"></a>Atributos que se usan para administrar colas  
 Use los siguientes atributos para administrar colas.  
  
|SchemaName|DisplayName|Tipo|Descripción|  
|----------------|-----------------|----------|-----------------|  
|NumberOfItems|Elementos de cola|Entero|Número de elementos de cola asociados con la cola.|  
|NumberOfMembers|Núm. de Integrantes|Entero|Número de miembros asociados con la cola.|  
|QueueViewType|Tipo|Los atributos de lista desplegable|Seleccione si la cola es pública o privada. Una cola pública la pueden ver todos los usuarios. Una cola privada solo la pueden ver los miembros agregados a la cola.|  
  
<a name="BKMK_deletingQueues"></a>   
## <a name="restrictions-on-deleting-queues"></a>Restricciones sobre la eliminación de colas  
 Una cola no se puede eliminar si se cumple lo siguiente:  
  
-   Cuando la cola tiene elementos de cola.  
  
-   La utiliza una regla de enrutamiento.  
  
<a name="BKMK_Enabling"></a>   
## <a name="enable-entities-for-queues"></a>Habilitar entidades para las colas  
 Para habilitar una entidad personalizable, (`EntityMetadata.IsCustomizable = true`), para las colas, use el mensaje <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest> para establecer el atributo <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsValidForQueue> en `true`. La entidad de cola y la entidad de elemento de cola son entidades personalizables, pero no se pueden habilitar para la colas.  
  
 La siguiente lista contiene las entidades habilitadas para las colas predeterminadas de Common Data Service:  
  
-   Cita  
  
-   Campaignactivity  
  
-   CampaignResponse  
  
-   Enviar por correo electrónico  
  
-   Fax  
  
-   Incidente  
  
-   Carta  
  
-   PhoneCall  
  
-   RecurringAppointmentMaster  
  
-   ServiceAppointment  
  
-   Actividad social  
  
-   Tarea  
  
<a name="BKMK_Inheriting"></a>   
## <a name="inherit-privileges-and-provide-limited-access-to-a-queue"></a>Heredar privilegios y proporcionar acceso limitado a una cola  
 Una cola y un elemento de cola tienen una relación jerárquica en la que las operaciones en el registro de la cola primaria se propagan a los registros de elementos de la cola secundaria.  
  
> [!NOTE]
>  En esta relación jerárquica específica, solo la acción Eliminar se propaga en cascada de la entidad de la cola primaria a la entidad de elemento de la cola secundaria. Otras acciones, como la asignación, combinación o uso compartido no se propagan en cascada.  
  
 Los privilegios de un elemento de cola se heredan de los privilegios de una cola.  
  
- Si tiene el privilegio `prvReadQueue`, también tiene el privilegio de lectura en una entidad de elemento de cola.  
  
- Si tiene el privilegio `prvAppendToQueue`, también tiene los privilegios de creación, actualización y eliminación en una entidad de elemento de cola.  
  
  A menudo, debe limitar el acceso a la cola permitiendo el acceso a los elementos de la cola. Como propietario de la cola con acceso completo a esta, quizás desee compartir una cola con un equipo que tendrá acceso limitado a ella. Por ejemplo, si el equipo de soporte técnico dispone de privilegios de lectura y anexión en una cola, los integrantes del equipo no pueden realizar cambios en la cola, como cambiar el nombre o el propietario de la cola. Sin embargo, pueden crear, recuperar, actualizar y eliminar elementos de cola.  
  
<a name="BKMK_Actions"></a>   
## <a name="actions-on-queues-and-queue-items"></a>Acciones en colas y elementos de cola  
 Puede llevar a cabo diversas acciones en colas y elementos de cola, si tiene los privilegios apropiados en la entidad de cola y la entidad de elemento de cola.  
  
### <a name="actions-on-queues"></a>Acciones en colas  
 Puede realizar las siguientes acciones en las colas:  
  
-   Personalizar colas y elementos de cola agregando atributos personalizados.  
  
-   Agregar un registro de entidad a una cola.  
  
    > [!NOTE]
    >  Un registro de entidad no se puede agregar a varias colas. Una excepción es un registro de entidad correo electrónico con el estado "recibido".  
  
-   Agregar registros de entidad de distintos tipos de entidad en la misma cola.  
  
-   Cambiar la propiedad de una cola asignándola a otro usuario o equipo.  
  
-   Agregar entidades de seguridad a una cola privada mediante el mensaje <xref:Microsoft.Crm.Sdk.Messages.AddPrincipalToQueueRequest>.  
  
-   Limpiar el historial de una cola mediante la eliminación de elementos de cola inactivos en la cola, como llamadas telefónicas realizadas o canceladas.  
  
-   Recuperar todas las colas a las que un usuario tiene acceso usando el mensaje <xref:Microsoft.Crm.Sdk.Messages.RetrieveUserQueuesRequest>  
  
-   Convertir una cola en la cola predeterminada para un usuario estableciendo el atributo `SystemUser.QueueId` en el identificador de la cola. La misma cola se puede especificar como una cola predeterminada para distintos usuarios.  
  
-   Crear un flujo de trabajo que funciona en todas las colas privadas. Por ejemplo, siempre que un usuario crea una tarea, el flujo de trabajo agrega la tarea a la cola predeterminada del usuario. También puede crear un flujo de trabajo que funcione solo en una cola específica.  
  
-   Configurar un correo electrónico para los mensajes entrantes, si desea que los mensajes de correo electrónico entrantes se entreguen en una cola.  
  
### <a name="actions-on-queue-items"></a>Acciones en elementos de cola  
 Puede realizar las siguientes acciones en los elementos de cola:  
  
- Asignar un elemento de cola a un usuario mediante el mensaje <xref:Microsoft.Crm.Sdk.Messages.PickFromQueueRequest>.  
  
- Mover un elemento de cola de una cola de origen a una cola de destino mediante el mensaje <xref:Microsoft.Crm.Sdk.Messages.AddToQueueRequest>. Un elemento de cola se puede mover de una cola a otra hasta que se desactive mediante el mensaje <xref:Microsoft.Crm.Sdk.Messages.SetStateRequest>.  
  
  > [!NOTE]
  >  Un elemento de cola se desactiva automáticamente si el estado del registro del elemento de cola cambió de activo a inactivo. Esto se aplica a las entidades habilitadas para las colas que tengan los estados activo e inactivo. Para determinar si una entidad está habilitada para las colas y si un registro de entidad puede estar en un estado activo o inactivo, vea la información de los metadatos de la entidad.  
  
- Liberar de nuevo un elemento en la cola usando el mensaje <xref:Microsoft.Crm.Sdk.Messages.ReleaseToQueueRequest>.  
  
- Eliminar un elemento de cola de una cola mediante el mensaje <xref:Microsoft.Xrm.Sdk.Messages.DeleteRequest>. Cuando se elimina un elemento de cola, el registro de entidad al que se hace referencia no se elimina. Sin embargo, si elimina un registro de entidad, se eliminan todos los elementos de cola que hacen referencia a este registro.  
  
### <a name="see-also"></a>Vea también  
 <!--[Configure EMail for Incoming Messages](configure-email-incoming-messages.md)-->  
 
[Entidad Queue](reference/entities/queue.md)   
[Entidad QueueItem](reference/entities/queueitem.md)   
<xref:Microsoft.Crm.Sdk.Messages.AddToQueueRequest>   
 