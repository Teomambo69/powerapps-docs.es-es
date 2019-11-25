---
title: Entidades de actividad de correo electrónico (Common Data Service) | Microsoft Docs
description: La actividad de correo electrónico en Dynamics 365 permite realizar el seguimiento y administrar comunicaciones de correo electrónico con los clientes.
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
ms.openlocfilehash: 3cc31d8cc572eae36d42535160cffab287098ca5
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749371"
---
# <a name="email-activity-entities"></a>Entidades de actividad de correo electrónico

La actividad de correo electrónico permite realizar el seguimiento y administrar comunicaciones de correo electrónico con los clientes. Common Data Service incluye el software E-mail Router que administra el enrutamiento de correo electrónico hacia o desde Common Data Service. La actividad de correo electrónico se entrega con protocolos de correo electrónico. E-mail Router admite los siguientes protocolos de correo electrónico: servicios web de Exchange, POP3 y SMTP. Además del software E-mail Router, la actividad de correo electrónico también se puede ofrecer mediante Dynamics 365 for Outlook.  
  
<a name="Actions"></a>   

## <a name="actions-on-an-email-activity"></a>Acciones en una actividad de correo electrónico  
 Mediante web servicios de Common Data Service, puede realizar las siguientes acciones sobre una actividad de correo electrónico:  
  
- Crear, recuperar, actualizar y eliminar la actividad de correo electrónico.  
  
- Enviar mensajes de correo electrónico o enviar mensajes de correo electrónico mediante plantillas de correo electrónico (`Template`). Para obtener más información acerca de las plantillas de correo electrónico, consulte [Entidad de plantilla](/reference/entities/template.md).  
  
- Adjunte archivos como datos adjuntos mediante el atributo (`ActivityMimeAttachment`) en el mensaje de correo electrónico.  
  
- Enviar mensajes de correo electrónico en masa.  
  
- Configurar mensajes de correo electrónico entrantes para que se entreguen desde Microsoft Exchange Server a cualquier usuario o cola, o mensajes salientes para que se envíen desde cualquier usuario o cola a Microsoft Exchange Server. Para obtener información sobre cómo configurar los mensajes de correo electrónico entrantes para las colas, consulte [Configurar el correo electrónico para los mensajes entrantes](/dynamics365/customer-engagement/developer/configure-email-incoming-messages).  
  
   Si los atributos de organización `Organization.RequireApprovalForuserEmail` y `Organization.RequireApprovalForQueueEmail` (correos electrónicos de proceso solo para usuarios o colas aprobados) se establecen en **true** (1), se produce lo siguiente: los mensajes de correo electrónico se entregan o se envían solamente desde un usuario o una cola si la dirección de correo electrónico principal del usuario o cola está aprobada. Los atributos `SystemUser.EmailRouterAccessApproval` y `Queue.EmailRouterAccessApproval` indican el estado de la dirección de correo electrónico principal del usuario y la cola respetivamente, y el valor debe establecerse como 1. De lo contrario, los mensajes entrantes y salientes se bloquearán. Puede actualizar el registro de usuarios o de colas para cambiar el valor del atributo, si no está ya en estado aprobado, siempre que su cuenta de usuario disponga del privilegio **prvApproveRejectEmailAddress** asignado.
  
> [!NOTE]
>  En Common Data Service, el atributo `Email.StatusCode` no puede ser **null**.  
  
<a name="BulkE-Mail"></a>   

## <a name="bulk-email"></a>Correo en masa  
 Common Data Service admite el envío de correo electrónico a una lista importante de destinatarios a través de una solicitud de correo electrónico en masa. Cuando se envía una solicitud de correo electrónico en masa a Common Data Service, se crea una operación asincrónica en la cola de servicio asincrónica que envía los mensajes de correo electrónico mediante un proceso en segundo plano. Esto le proporciona un rendimiento del sistema mejorado.  
  
 Los mensajes <xref:Microsoft.Crm.Sdk.Messages.SendBulkMailRequest> y <xref:Microsoft.Crm.Sdk.Messages.BackgroundSendEmailRequest> se usan para enviar mensajes de correo electrónico en masa. A continuación se enumera la secuencia utilizada para enviar correo electrónico en masa:  
  
1. Ejecute la solicitud `SendBulkMail`. Esta solicitud contiene una consulta que selecciona los destinatarios de correo electrónico de destino y una plantilla de correo electrónico para redactar cada correo electrónico.  
  
2. El servicio asincrónico crea actividades de correo electrónico para cada destinatario.  
  
3. El servicio asincrónico envía cada mensaje de correo electrónico. Los mensajes de correo electrónico tienen estado de envío "pendiente".  
  
4. El enrutador de correo electrónico, Dynamics 365 for Outlook, o un componente de envío de correo electrónico de terceros sondea Common Data Service en busca de mensajes de correo electrónico pendientes y, si se encuentra uno, los descarga mediante la solicitud `BackgroundSendEmail`.  
  
5. La solicitud `BackgroundSendEmail` realiza las operaciones siguientes: comprueba si hay mensajes de correo electrónico pendientes, descarga el correo electrónico al llamador del mensaje <xref:Microsoft.Crm.Sdk.Messages.BackgroundSendEmailRequest> y sincroniza las descargas si hay varios llamadores.  
  
6. El llamador del mensaje <xref:Microsoft.Crm.Sdk.Messages.BackgroundSendEmailRequest> recibe el mensaje de correo electrónico descargado y, a continuación, lo envía.  
  
<a name="E-MailAttachments"></a>   
## <a name="email-attachments"></a>Datos adjuntos de correo electrónico  
 Los datos adjuntos de correo electrónico son archivos que pueden adjuntarse a mensajes de correo electrónico o a plantillas de correo electrónico. Un archivo adjunto puede estar en cualquier formato de archivo de equipo estándar como documentos Office Outlook, hojas de cálculo de Office Excel, archivos de CAD y archivos PDF. Puede adjuntar varios archivos como datos adjuntos de correo electrónico a un correo electrónico o a una plantilla de correo electrónico. El tamaño máximo de los archivos que se pueden cargar se determina mediante la propiedad **Organization.MaxUploadFileSize**. Esta propiedad se define en la pestaña **Correo electrónico** de **Configuración del sistema** en la aplicación Dynamics 365. Esta configuración limita el tamaño de los archivos que pueden adjuntarse a los mensajes de correo electrónico, notas y recursos web. La configuración predeterminada es 5 MB. 
  
 Para adjuntar datos adjuntos de correo electrónico con un mensaje o una plantilla de correo electrónico, utilice los atributos `ActivityMimeAttachment.ObjectId` y `ActivityMimeAttachment.ObjectTypeCode` mientras está creando o actualizando un registro de adjunto MIME de actividad.  
  
 La muestra de código siguiente muestra cómo adjuntar datos adjuntos de correo electrónico en un correo electrónico:  
  
```csharp  
ActivityMimeAttachment _sampleAttachment = new ActivityMimeAttachment{  
    ObjectId = new EntityReference(Email.EntityLogicalName, _emailId),  
    ObjectTypeCode = Email.EntityLogicalName,  
    Subject = "Sample Attachment”,  
    Body = System.Convert.ToBase64String(new ASCIIEncoding().GetBytes("Example Attachment")),  
    FileName = "ExampleAttachment.txt"};  
```  
  
 De forma similar, para adjuntar los datos adjuntos de correo electrónico a una plantilla en vez de a un correo electrónico, se reemplazarán los valores de los atributos `ActivityMimeAttachment.ObjectId` y `ActivityMimeAttachment.ObjectTypeCode` del modo siguiente en el código anterior:  
  
```csharp  
ObjectId = new EntityReference(Template.EntityLogicalName, _templateId), ObjectTypeCode = Template.EntityLogicalName,  
```  
  
 Para ver un ejemplo de código completo sobre cómo crear adjuntos de correo electrónico, vea [Ejemplo: Crear, recuperar, actualizar y eliminar un adjunto de correo electrónico](/dynamics365/customer-engagement/developer/sample-create-retrieve-update-delete-email-attachment).  
  
### <a name="reusing-email-attachments"></a>Reutilización de datos adjuntos de correo electrónico  
 Cuando se crea un registro de datos adjuntos de correo electrónico, el archivo adjunto se guarda como BLOB de archivo. El atributo `ActivityMimeAttachment.AttachmentId` del registro de datos adjuntos de correo electrónico identifica de forma exclusiva al BLOB de archivo. Esto se hace para facilitar la reutilización de los datos adjuntos del archivo con otros registros de correo electrónico y de plantilla de correo electrónico, sin crear y almacenar varias copias del mismo archivo en la base de datos.  
  
 Para volver a usar datos adjuntos de un archivo existente:  
  
1.  Recupere el registro de `ActivityMimeAttachment` que contiene el archivo adjunto que desea volver a usar tal y como se muestra en el siguiente ejemplo de código:  
  
    ```csharp  
    ActivityMimeAttachment retrievedAttachment = (ActivityMimeAttachment)_serviceProxy.Retrieve(ActivityMimeAttachment.EntityLogicalName, _emailAttachmentId, new ColumnSet(true));  
    ```  
  
2.  Cree un nuevo registro de datos adjuntos de correo electrónico, asócielo con el registro requerido de correo electrónico o de plantilla de correo electrónico y diríjalo al archivo adjunto del registro `ActivityMimeAttachment` recuperado, tal y como se muestra en el siguiente ejemplo de código:  
  
    ```csharp  
    ActivityMimeAttachment _reuseAttachment = new ActivityMimeAttachment{  
        ObjectId = new EntityReference(Email.EntityLogicalName, _emailId),  
        ObjectTypeCode = Email.EntityLogicalName,  
        Subject = "Sample Attachment”,  
        AttachmentId = retrievedAttachment.AttachmentId};  
    ```  
  
     Debido a que está reutilizando un archivo de datos adjuntos existente, no tiene que especificar los valores de atributo de `ActivityMimeAttachment.Body` y `ActivityMimeAttachment.FileName` mientras está creando y asociando registros de datos adjuntos de correo electrónico a correos electrónicos o a plantillas de correo electrónico.  
  
### <a name="see-also"></a>Vea también  
 [Entidades de actividad](activity-entities.md)   
 [Código de ejemplo para las entidades de actividad](/dynamics365/customer-engagement/developer/sample-code-activity-entities)   
 [Entidad Email](/reference/entities/email.md)   
 [Entidad ActivityMimeAttachment](/reference/entities/activitymimeattachment.md)
