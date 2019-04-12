---
title: Entidades de actividad (Common Data Service) | Microsoft Docs
description: 'En Dynamics 365 (en línea), las actividades son las tareas que usted o sus equipos realizan cuando se ponen en contacto con los clientes, por ejemplo, enviar cartas o hacer llamadas de teléfono.'
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
---
# <a name="activity-entities"></a>Entidades de actividad

En Common Data Service, las actividades son las tareas que usted o sus equipos realizan cuando se ponen en contacto con los clientes, por ejemplo, enviar cartas o hacer llamadas de teléfono. Puede crear las actividades por usted mismo, asignarlas a otra persona o compartirlas con otros usuarios o equipos. Una actividad es cualquier acción que se pueda incluir en un calendario y tiene las dimensiones de tiempo (hora de inicio, hora de finalización, fecha de vencimiento y duración) que ayudan a determinar cuándo se ha producido la acción o va se va a producir. Las actividades tienen algunas propiedades básicas que ayudan a determinar qué acción representa la actividad, por ejemplo, el tema y la descripción. Un estado de la actividad puede ser abierto, cancelado o completado. El estado completado de una actividad tendrá varios valores de estado secundarios asociados para aclarar el modo en que la actividad se ha completado.  
  
 Las actividades conllevan uno o varios participantes, denominados usuarios de la actividad en Common Data Service. Para una actividad de reunión, los participantes son los contactos o usuarios que asisten a la reunión. Para una actividad de llamada de teléfono o fax, los usuarios son el autor de la llamada y la persona a la que se llama. El diagrama siguiente muestra las relaciones entre entidades para las actividades.  
  
 ![Diagrama de actividades](media/entity-model-activity.gif "Diagrama de actividades")  
  
 Para satisfacer las necesidades de comunicación de la empresa actual, como mensajería instantánea (IM) y SMS, puede crear actividades personalizadas en Common Data Service.  
  
 **Otras entidades de actividad**  
  
-   La programación de actividades le permite programar los servicios y los recursos, y de este modo definir los programas de trabajo. Las entidades de actividad de programación son `Appointment`, `ServiceAppointment` y `RecurringAppointmentMaster`. Para obtener más información, consulte [Entidades de programación y citas](/dynamics365/customer-engagement/developer/schedule-appointment-entities).  
  
-   La actividad de marketing, `CampaignResponse`, le permite capturar las respuestas de los clientes de una campaña de marketing, aunque la entidad `CampaignActivity` representa un paso de una campaña. Para obtener más información, consulte [Entidades de campaña](/dynamics365/customer-engagement/developer/campaign-entities).  
  
-   Las entidades de automatización de la fuerza de ventas `OpportunityClose`, `OrderClose` y `QuoteClose` capturan la información acerca de cada uno de los eventos. Para obtener más información, consulte [Entidades de ventas (cliente potencial, oportunidad, competidor, oferta, pedido, factura)](/dynamics365/customer-engagement/developer/sales-entities-lead-opportunity-competitor-quote-order-invoice)  
  
-   La actividad de entidad de servicio de atención al cliente `IncidentResolution` captura la información sobre la resolución de un caso. Para obtener más información, consulte [Entidades de incidentes (caso)](/dynamics365/customer-engagement/developer/incident-case-entities).  
  
## <a name="in-this-section"></a>En esta sección  
 [Actividades personalizadas en Dynamics 365](custom-activities.md)  
  
 [Entidad de puntero de actividad (actividad)](activitypointer-activity-entity.md)  
  
 [Entidad de grupo de actividad](activityparty-entity.md)  
  
 [Entidades de actividad de tarea, fax, llamada telefónica y carta](task-fax-phone-call-letter-activity-entities.md)  
  
 [Entidades de actividad de correo electrónico](email-activity-entities.md)  
  
 [Código de ejemplo para entidades de actividad](/dynamics365/customer-engagement/developer/sample-code-activity-entities)  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Modele sus datos profesionales con Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/model-business-data)  
  
 [Entidades de sincronización del lado del servidor](server-side-synchronization-entities.md)  
  
 [Personalizar metadatos de entidad](customize-entity-metadata.md)
