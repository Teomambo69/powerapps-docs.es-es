---
title: Eliminar datos en masa (Common Data Service) | Microsoft Docs
description: Eliminar datos de forma masiva ayuda a mantener la calidad de los datos y a administrar el consumo de almacenamiento del sistema eliminando los datos que ya no son necesarios.
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
ms.openlocfilehash: 5eb692c38d7a8dac779c827c09d7b767e89bb6e2
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749565"
---
# <a name="delete-data-in-bulk"></a>Eliminar datos en masa

La característica *eliminación en masa* ayuda a mantener la calidad de los datos y a administrar el consumo de almacenamiento del sistema en Common Data Service mediante la eliminación de datos que ya no son necesarios. Por ejemplo, puede eliminar los siguientes datos en masa:  
  
- Datos obsoletos.  
  
- Datos irrelevantes para el negocio.  
  
- Datos de ejemplo o de prueba innecesarios.  
  
- Datos que se importan incorrectamente desde otros sistemas.  
  
Con la eliminación en masa puede realizar las operaciones siguientes:  
  
- Eliminar datos en varias entidades.  
  
- Eliminar registros para una entidad especificada.  
  
- Recibir notificaciones por correo electrónico cuando finaliza una eliminación en masa.  
  
- Eliminar datos periódicamente.  
  
- Programar la hora de inicio de una eliminación en masa periódica.  
  
- Recuperar la información acerca de los errores que se han producido durante una eliminación en masa.  
  
## <a name="run-bulk-delete"></a>Ejecutar eliminación en masa

Para eliminar datos en masa, tiene que enviar un trabajo de eliminación en masa mediante el mensaje de <xref:Microsoft.Crm.Sdk.Messages.BulkDeleteRequest>. El trabajo de eliminación en masa se ejecuta asincrónicamente en segundo plano sin bloquear otras actividades. Las expresiones de la consulta que describen los registros en los que ejecutar el trabajo de eliminación en masa se especifican en la propiedad de <xref:Microsoft.Crm.Sdk.Messages.BulkDeleteRequest.QuerySet> de la solicitud.  
  
 Un trabajo de eliminación en masa se representa por la entidad de operación de eliminación en masa. El nombre de esquema de esta entidad es `BulkDeleteOperation`. Un registro de operación de eliminación masiva incluye la siguiente información:  
  
- Número de registros eliminados por el trabajo de eliminación en masa.  
  
- Número de registros que el trabajo de eliminación en masa no ha podido eliminar.  
  
- Si el trabajo de eliminación en masa es un trabajo periódico o no.  
  
- Hora de inicio del trabajo de eliminación en masa.  
  
  Un trabajo de eliminación en masa solo elimina los registros que se han creado antes de que el trabajo inicie su ejecución.  
  
> [!NOTE]
>  Si un trabajo de eliminación en masa falla o finaliza antes de tiempo, los registros que se eliminaron antes del error o de la finalización del trabajo no se revierten y permanecen eliminados. Los errores de la `BulkDeleteOperation` se almacenan en los registros de `BulkDeleteFailure` y se pueden recuperar mediante el mensaje <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest> o el mensaje <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest>.  
  
 Un trabajo de eliminación en masa elimina los registros especificados según las reglas en cascada. Estas reglas se basan en el tipo de relación entre entidades. Para obtener más información, consulte [Comportamiento de las relaciones de entidad](/dynamics365/customer-engagement/developer/entity-relationship-behavior).  
  
 Para ejecutar un trabajo de eliminación en masa, un usuario debe tener privilegios `BulkDelete` y `Delete` para los tipos de entidad que se están eliminando. El usuario deberá tener también permisos de lectura en los registros de entidad que se especifiquen en el mensaje de <xref:Microsoft.Crm.Sdk.Messages.BulkDeleteRequest>. De forma predeterminada, los administradores del sistema tienen los permisos necesarios; sin embargo, a otros usuarios deben concedérseles estos permisos.  
  
 Puede realizar una eliminación en masa en todas las entidades que son compatibles con la acción de eliminación. Para obtener más información sobre acciones posibles en los registros de entidad, consulte [Acciones de registros de entidad](/dynamics365/customer-engagement/developer/introduction-entities#ActionsOnEntityRecords).  
  
 Si un complemento o un flujo de trabajo (proceso) se activa dentro de la acción de eliminación para un tipo específico de la entidad, se desencadena cada vez que un registro de la entidad de este tipo es eliminado por el trabajo de eliminación en masa.  
  
## <a name="samples"></a>Muestras

Busque en los siguientes ejemplos de servicio de organización la característica de cancelación en masa:

- [Ejemplo: Eliminación en masa de los registros exportados](org-service/samples/bulk-delete-exported-records.md)   
- [Ejemplo: Eliminar en masa registros que coincidan con criterios comunes](org-service/samples/bulk-delete-records-match-common-criteria.md)

### <a name="see-also"></a>Vea también

[Entidad BulkDeleteOperation](reference/entities/bulkdeleteoperation.md)