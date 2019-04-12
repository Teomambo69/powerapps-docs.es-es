---
title: Actualizar una cita periódica (Common Data Service) | Microsoft Docs
description: Actualice una serie de citas recurrentes utilizando el método IOrganizationService.Entity o el mensaje UpdateRequest en la entidad RecurringAppointmentMaster.
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
# <a name="update-a-recurring-appointment"></a>Actualizar una cita periódica

Puede actualizar la serie entera o actualizar una instancia de una cita periódica.  
  
## <a name="update-a-recurring-appointment-series"></a>Actualizar una serie de citas periódicas  
 Puede actualizar una serie de citas recurrente mediante el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> o el mensaje <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> en la entidad `RecurringAppointmentMaster`. Puede actualizar la información *básica* o *periódica*.  
  
### <a name="update-basic-information"></a>Actualizar la información básica  
 Cuando se actualiza la información básica de una serie de citas periódicas, como el asunto, la ubicación o los asistentes, todas las instancias de la serie se actualizan excepto las que tienen excepciones en el mismo atributo.  
  
### <a name="update-recurrence-information"></a>Actualizar la información periódica  
 Cuando se actualiza la información periódica de una serie de citas periódicas, como el patrón y el intervalo, se produce lo siguiente:  
  
1. Se crea una nueva serie con un nuevo `RecurringAppointmentMaster.ActivityId` que tiene la misma información que la serie original, y la fecha del atributo `RecurringAppointmentMaster.EffectiveEndDate` de la nueva serie se establece en la instancia que ocurrió en último lugar de la serie original. Todas las instancias futuras de la serie original se eliminan. De esta manera, se finaliza la serie original y se conserva el historial de las últimas instancias en el sistema almacenado en una nueva serie.  
  
2. La nueva información se usa para crear las futuras instancias de la serie nueva desde la fecha de inicio efectiva (`RecurringAppointmentMaster.EffectiveStartDate`).  
  
   Además, el atributo `RecurringAppointmentMaster.GroupId` para la serie original y nueva se rellena con el mismo valor. Esto implica que siempre que actualice la información de la periodicidad de una serie de citas periódicas, todas las nuevas series que se crean tienen el mismo valor en el atributo `RecurringAppointmentMaster.GroupId` que la serie de citas periódicas que se actualiza, aunque cada serie tenga un identificador de serie único.  
  
> [!NOTE]
>  Cuando actualice la información de la periodicidad de una serie de citas periódicas que tiene todas las instancias programadas para que ocurran en el futuro, se eliminan todas las instancias y la nueva información de la frecuencia se usa para crear o ampliar las nuevas instancias.  
  
 Para ver el código de muestra para actualizar una serie de citas periódica, consulta [Ejemplo: actualizar una cita periódica](org-service/samples/reschedule-cancel-recurring-appointment.md).  
  
## <a name="update-a-recurring-appointment-instance"></a>Actualizar una instancia de citas periódicas  
 Puesto que los registros de citas periódicas se almacenan como objetos de cita, puede usar el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> en la entidad `Appointment` para actualizar una instancia de citas recurrente. Cuando se actualiza una instancia de cita periódica, la instancia se marca como una excepción en la serie de citas periódicas. Más información: [Crear una excepción a la cita periódica](create-recurring-appointment-series-instance-exception.md#bkmk_createexception)  
  
 También puede usar la clase <xref:Microsoft.Crm.Sdk.Messages.CreateExceptionRequest> de la entidad `Appointment` para actualizar una instancia de cita periódica.  
  
> [!TIP]
>  Las instancias de citas periódicas se pueden identificar mediante el atributo `Appointment.InstanceTypeCode`, que tendrá que un valor de "2 " (instancia periódica). Más información: [Entida de cita](reference/entities/appointment.md)  
  
### <a name="see-also"></a>Vea también  
 [Entidades de cita periódica](/dynamics365/customer-engagement/developer/recurring-appointment-entities)   
 [Eliminar o finalizar una instancia o serie de cita periódica](/dynamics365/customer-engagement/developer/delete-or-end-a-recurring-appointment-series-or-instance)   
 [Ejemplo: crear, recuperar, actualizar y eliminar una cita periódica](org-service/samples/create-retrieve-update-delete-recurring-appointment.md)   
 [Ejemplo: reprogramar y cancelar una cita periódica](org-service/samples/reschedule-cancel-recurring-appointment.md)
