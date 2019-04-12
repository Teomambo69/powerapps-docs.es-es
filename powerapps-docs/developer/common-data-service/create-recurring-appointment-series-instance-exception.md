---
title: 'Cree una serie, una instancia, o una excepción de citas periódicas (Common Data Service) | Microsoft Docs'
description: 'Crear mediante programación una cita periódica maestra (serie), instancias de cita periódica individuales, excepciones a dichas instancias o convertir una cita en periódica.'
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
# <a name="create-a-recurring-appointment-series-instance-or-exception"></a>Crear una instancia, excepción o serie de cita periódica.

Al crear una cita periódica maestra (serie), Common Data Service crea instancias individuales de la cita en función de la información periódica especificada. También puede crear instancias individuales de citas periódicas y las excepciones a dichas instancias, y puede convertir una cita en una cita periódica.  
  
<a name="bkmk_createseries"></a>   

## <a name="create-a-recurring-appointment-series"></a>Crear una serie de citas periódicas  

 Para crear una serie de citas periódicas (un registro de `RecurringAppointmentMaster`), puede usar el mensaje <xref:Microsoft.Crm.Sdk.Messages.BookRequest>, el mensaje <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> o el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*> .  
  
 Cuando crea una serie de citas periódicas, ocurre lo siguiente:  
  
1. Se crea un registro de `RecurringAppointmentMaster` (serie de citas periódicas) que contiene información básica y la frecuencia sobre la serie de citas periódicas. Cada registro se puede identificar de forma única mediante la propiedad `RecurringAppointmentMaster.ActivityId`. Además, esta serie de citas periódicas también se crea y se almacena como un registro de actividad (`ActivityPointer`). El registro de actividad se puede identificar de forma única mediante la propiedad `ActivityPointer.ActivityId`.  
  
2. Se crean instancias individuales de citas periódicas basándose en la información de la frecuencia y se almacenan como registros de `Appointment` . Estos objetos de cita se asocian a la serie primaria de citas periódicas mediante la propiedad `Appointment.SeriesId` y tienen el mismo valor que el Id. primario de la serie de citas periódicas (`ActivityPointer.SeriesId`).  
  
    El valor de la propiedad de `Appointment.InstanceTypeCode` se establece en **Instancia periódica** (valor de lista desplegable 2) para estos objetos de cita.  
  
   > [!NOTE]
   >  Las instancias de citas periódicas se crean basándose en el modelo de la expansión y los parámetros que se definen. Más información: [Modelo de expansión parcial de citas periódicas](recurring-appointment-partial-expansion-model.md)  
  
   Para ver el código de muestra para crear una serie de citas periódica, consulte [Ejemplo: Crear una cita periódica](/dynamics365/customer-engagement/developer/sample-create-retrieve-update-delete-recurring-appointment).  
  
<a name="bkmk_createinstance"></a>   

## <a name="create-a-recurring-appointment-instance"></a>Crear una instancia de citas periódicas  
 Para crear una instancia de citas periódicas (un registro de `RecurringAppointmentMaster` ), puede usar <xref:Microsoft.Crm.Sdk.Messages.CreateInstanceRequest>. Para este mensaje se necesitan dos parámetros: el número de instancias que se van a crear y la serie de citas periódicas para las que se tienen que crear instancias.  
  
 Las instancias se crean después de la última instancia de la serie de citas periódicas. Además, solo se crean instancias hasta la fecha de finalización futura de la instancia, independientemente del número de instancias que se haya especificado para la creación.  
  
<a name="bkmk_createexception"></a>   

## <a name="create-a-recurring-appointment-exception"></a>Crear una excepción a la cita periódica  
 Se crea una excepción al actualizar o eliminar una instancia de la cita periódica. Las instancias de citas periódicas se almacenan como un registro de cita junto a otras citas, y puede identificar una instancia de citas periódicas mediante el atributo `Appointment.InstanceTypeCode` de un registro de cita, que tendrá un valor de **Instancia periódica** (valor de lista desplegable 2).  
  
 Puede crear excepciones de las siguientes formas:  
  
-   Use la clase <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> en la entidad `Appointment` para actualizar una instancia de citas periódicas y establezca el valor del atributo `Appointment.InstanceTypeCode` en **Excepción periódica** (valor de lista desplegable 3).  
  
-   Use el tipo de clase <xref:Microsoft.Xrm.Sdk.Messages.DeleteRequest> de la entidad `Appointment` para eliminar una instancia de cita periódica. Al eliminar una instancia de cita, se señala como una excepción creando una entrada para la instancia en el atributo `RecurringAppointmentMaster.DeletedExceptionsList` del objeto primario de la serie de citas.  
  
-   Use la clase <xref:Microsoft.Crm.Sdk.Messages.CreateExceptionRequest> en la entidad `Appointment` .  
  
<a name="bkmk_convert"></a>   

## <a name="convert-an-appointment-to-a-recurring-appointment"></a>Convertir una cita en una cita periódica  
 Una cita periódica es una cita con información de la frecuencia. Puede convertir una cita existente en Common Data Service en una cita periódica mediante <xref:Microsoft.Crm.Sdk.Messages.AddRecurrenceRequest>. Cuando se convierte una cita existente en una cita periódica, los datos de la cita existente se copian en una nueva instancia de cita periódica maestra y se elimina la cita existente.  
  
### <a name="see-also"></a>Vea también  
 [Entidades de cita periódica](/dynamics365/customer-engagement/developer/recurring-appointment-entities)   
 [Actualizar una cita periódica](update-recurring-appointment.md)   
 [Ejemplo: Crear una cita periódica](/dynamics365/customer-engagement/developer/sample-create-retrieve-update-delete-recurring-appointment)   
 [Ejemplo: Convertir una cita en periódica](/dynamics365/customer-engagement/developer/sample-convert-appointment-recurring-appointment)
