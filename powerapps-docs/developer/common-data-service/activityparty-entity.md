---
title: Entidad ActivityParty (Common Data Service) | Microsoft Docs
description: Un grupo de actividad representa a una persona o grupo asociado a una actividad. Una actividad puede tener varios grupos de actividad.
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
ms.openlocfilehash: fa10c95e2b5345f70399d1b19c5e0df0bf1f8527
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749416"
---
# <a name="activityparty-entity"></a>Entidad ActivityParty

Un grupo de actividad representa a una persona o grupo asociado a una actividad. Una actividad puede tener varios grupos de actividad.  
  
<a name="ActivityPartyTypes"></a>   

## <a name="activity-party-types"></a>Tipos de grupo de actividad  

 Hay 11 tipos de grupo de actividad en Common Data Service. El tipo de grupo de actividad se guarda como valor entero en el atributo `ActivityParty.ParticipationTypeMask`. La siguiente tabla muestra los diferentes tipos de grupo de actividad, el valor entero correspondiente para el atributo `ActivityParty.ParticipationTypeMask` y la descripción.  
  
|Tipo de grupo de actividad|Value|Descripción|  
|-------------------------|-----------|-----------------|  
|Remitente|1|Especifica el remitente.|  
|ToRecipient|2|Especifica el destinatario en el campo Para.|  
|CCRecipient|3|Especifica el destinatario en el campo CC.|  
|BccRecipient|4|Especifica el destinatario en el campo CCO.|  
|RequiredAttendee|5|Especifica un asistente necesario.|  
|OptionalAttendee|6|Especifica un asistente opcional.|  
|Organizador|7|Especifica el organizador de la actividad.|  
|Referente a|8|Especifica el elemento Referente a.|  
|Propietario|9|Especifica el propietario de la actividad.|  
|Recurso|10|Especifica un recurso.|  
|Cliente|11|Especifica un cliente.|  
  
<a name="SupportedActivityPartyTypes"></a>   
## <a name="activity-party-types-available-for-each-activity"></a>Tipos de grupo de actividad disponibles para cada actividad  
 No todos los tipos del grupo de actividad están disponibles para cada actividad en Common Data Service, salvo en el caso de una actividad personalizada. Una actividad personalizada admite todos los tipos de grupo de actividad. Puede asociar un tipo de grupo de actividad para una actividad mediante el atributo respectivo de una actividad. Por ejemplo, para asociar un tipo de grupo de actividad de `Organizer` a una actividad de cita, debe especificar un valor o una matriz de valores del `ActivityParty` tipo en el atributo `Appointment.Organizer`.  
  
 Para controlar qué dirección de correo electrónico debe usarse para enviar correos electrónicos al grupo de actividad, o para responder a mensajes de correo electrónico del grupo de actividad, establezca el atributo `ActivityParty.AddressUsed`.  
  
 La siguiente tabla muestra los tipos de grupo de actividad que se admiten para cada actividad, así como las propiedades de actividad correspondientes para especificar estos tipos de grupo de actividad.  
  
|Nombre de entidad de actividad|Tipo de grupo de actividad admitida|Atributo de actividad|  
|--------------------------|-----------------------------------|------------------------|  
|Cita|OptionalAttendee<br />Organizador<br />RequiredAttendee|Appointment.OptionalAttendees<br />Appointment.Organizer<br />Appointment.RequiredAttendees|  
|CampaignActivity|Remitente|CampaignActivity.Partners<br />CampaignActivity.From|  
|CampaignResponse|Cliente|CampaignResponse.Customer<br />CampaignResponse.Partner<br />CampaignResponse.From|  
|Enviar por correo electrónico|BccRecipient<br />CcRecipient<br />Remitente<br />ToRecipient|Email.Bcc<br />Email.Cc<br />Email.From<br />Email.To|  
|Fax|Remitente<br />ToRecipient|Fax.From<br />Fax.To|  
|Carta|BccRecipient<br />Remitente<br />ToRecipient|Letter.Bcc<br />Letter.From<br />Letter.To|  
|PhoneCall|Remitente<br />ToRecipient|PhoneCall.From<br />PhoneCall.To|  
|RecurringAppointmentMaster|OptionalAttendee<br />Organizador<br />RequiredAttendee|RecurringAppointmentMaster.OptionalAttendees<br />RecurringAppointmentMaster.Organizer<br />RecurringAppointmentMaster.RequiredAttendees|  
|ServiceAppointment|Cliente<br />Recurso|ServiceAppointment.Customers<br />ServiceAppointment.Resources|  
  
### <a name="see-also"></a>Vea también  
 [Entidades de actividad](activity-entities.md)   
 [Entidades de actividad de tarea, fax, llamada telefónica y carta](task-fax-phone-call-letter-activity-entities.md)   
 [Entidad ActivityParty](reference/entities/activityparty.md)   
 [Ejemplo: Reservar una cita](/dynamics365/customer-engagement/developer/sample-book-appointment)<br>
 [Ejemplo: Convertir un fax en una tarea](/dynamics365/customer-engagement/developer/sample-convert-fax-task)   
 [Ejemplo: Reemplazar el recuento total de objetivos y cerrar el objetivo](/dynamics365/customer-engagement/developer/sample-override-goal-total-count-close-goal)   
 [Ejemplo: Resumir datos de objetivos para un período fiscal en comparación con el recuento objetivo ajustado](/dynamics365/customer-engagement/developer/sample-rollup-goal-data-fiscal-period-stretch-target-count)   
 [Ejemplo: Enviar un mensaje de correo electrónico usando una plantilla](/dynamics365/customer-engagement/developer/sample-send-email-template)   
 [Ejemplo: Validar una cita](/dynamics365/customer-engagement/developer/sample-validate-appointment)
