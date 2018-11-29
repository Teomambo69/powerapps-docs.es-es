---
title: Recuperar y eliminar el historial de los cambios de datos auditados (Common Data Service para aplicaciones) | Microsoft Docs
description: Recuperar mediante programación el historial de cambios de auditoría o eliminar registros de auditoría.
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
---
# <a name="retrieve-and-delete-the-history-of-audited-data-changes"></a>Recuperar y eliminar el historial de cambios de datos auditados

Una vez habilitada la auditoría y los cambios de los datos en esas entidades y los atributos auditados, puede continuar con la obtención del historial de cambio de datos. De manera opcional, puede eliminar registros de auditoría después de revisar el historial de cambios. Siga el vínculo del código de ejemplo al final de este tema para obtener más información.  
  
## <a name="retrieve-the-change-history"></a>Recuperan el historial de cambios 
 
 Existen varias solicitudes de mensajes que se pueden usar para recuperar el historial de cambios de la auditoría. Estas solicitudes están diferenciadas por la naturaleza de lo que recuperan. 
<!-- Bug 696490 should make the Audit entity public again: Refer to the topic  [Audit Entity](entities/audit.md) for a list of message requests related to auditing. -->
Consulte el vínculo de ejemplo al final de este tema para el código de ejemplo que muestran algunas de estas solicitudes de mensajes del historial de cambios.

## <a name="delete-the-change-history-for-a-record"></a>Eliminar el historial de cambios para un registro
 
 Utilice el mensaje <xref:Microsoft.Crm.Sdk.Messages.DeleteRecordChangeHistoryRequest> para eliminar todos los registros del historial de cambios de auditoría para un registro determinado. Esto le permite eliminar el historial de cambios de auditoría de un registro en lugar de eliminar todos los registros de auditoría para un intervalo de fechas, que se cubre en la siguiente sección. Para eliminar el historial de cambios de auditoría de un registro, debe tener un rol de seguridad con el privilegio **prvDeleteRecordChangeHistory** o ser administrador del sistema.

## <a name="delete-the-change-history-for-a-date-range"></a>Eliminar el historial de cambios para un intervalo de fechas

 Puede eliminar registros de `audit` para un intervalo de fechas mediante el uso de la solicitud de <xref:Microsoft.Crm.Sdk.Messages.DeleteAuditDataRequest>. Los registros de datos de auditoría se eliminan de forma secuencial, del más antiguo al más nuevo. La funcionalidad de esta solicitud es un poco diferente en función de la edición de Microsoft SQL Server que usa su servidor de CDS para aplicaciones. CDS para aplicaciones usa una edición Enterprise de SQL Server.

 Si el servidor de CDS para aplicaciones usa la edición estándar de SQL Server que no admite la función de partición de la base de datos, la solicitud de <xref:Microsoft.Crm.Sdk.Messages.DeleteAuditDataRequest> elimina todos los registros de auditoría creados hasta la fecha de finalización especificada en la propiedad de <xref:Microsoft.Crm.Sdk.Messages.DeleteAuditDataRequest.EndDate>.

 Si el servidor de CDS para aplicaciones usa una edición Enterprise de SQL Server que admite la partición, la solicitud de <xref:Microsoft.Crm.Sdk.Messages.DeleteAuditDataRequest> eliminará todos los datos de auditoría en las particiones donde la fecha de finalización es anterior a la fecha especificada en la propiedad de <xref:Microsoft.Crm.Sdk.Messages.DeleteAuditDataRequest.EndDate>. Ninguna de las particiones vacías puede eliminarse. Sin embargo, ni la partición actual (activa) ni los registros de `audit` en esa partición activa pueden eliminarse mediante esta solicitud o cualquier otra solicitud.

 La plataforma de CDS para aplicaciones automáticamente crea nuevas particiones trimestralmente cada año. Esta funcionalidad no es configurable y no se puede cambiar. Puede obtener una lista de particiones mediante el uso de la solicitud de <xref:Microsoft.Crm.Sdk.Messages.RetrieveAuditPartitionListRequest> . Si la fecha de finalización de cualquier partición es posterior a la fecha actual, no podrá eliminar esa partición o los registros de `audit` que contenga.  

### <a name="see-also"></a>Vea también

 [Administración de datos en Dynamics 365](/dynamics365/customer-engagement/developer/manage-data)<br />
 [Cambios de los datos de la entidad de auditoría](/dynamics365/customer-engagement/developer/audit-entity-data-changes)<br />
 [Auditoría de acceso de usuario](audit-user-access.md) <br />
 [Ejemplo: Auditar cambios de datos de entidad](org-service/samples/audit-entity-data-changes.md)