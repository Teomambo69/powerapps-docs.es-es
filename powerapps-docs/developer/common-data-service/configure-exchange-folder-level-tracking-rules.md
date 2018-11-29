---
title: Configurar las reglas de seguimiento de carpeta de Exchange (Common Data Service para aplicaciones) | Microsoft Docs
description: Aprenda a configurar reglas de seguimiento de nivel de carpeta de Exchange.
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
# <a name="configure-exchange-folder-level-tracking-rules"></a>Configurar reglas de seguimiento de nivel de carpeta de Exchange

Configure las reglas de seguimiento de nivel de carpeta para asignar una carpeta de buzón de Microsoft Exchange a un registro de Common Data Service para aplicaciones para que se realice automáticamente el seguimiento de todos los mensajes de correo electrónico de la carpeta de Microsoft Exchange en comparación con el registro asignado en CDS for Apps. El seguimiento de nivel de carpeta de correos electrónicos funcionará sólo si:  

- La característica de seguimiento de nivel de carpeta está habilitada para la instancia de CDS for Apps. Puede habilitar el seguimiento de nivel de carpeta utilizando el cliente web o Dynamics 365 for Outlook. Más información: [Configurar el seguimiento de nivel de carpeta](/dynamics365/customer-engagement/admin/configure-outlook-exchange-folder-level-tracking)  

- La carpeta cuyo seguimiento está realizando se encuentra en la carpeta **Bandeja de entrada** en Microsoft Exchange. No se realizará seguimiento de los correos electrónicos en las carpetas que no se encuentran en la carpeta **Bandeja de entrada**.  

<a name="Create"></a>   

## <a name="create-and-manage-folder-level-tracking-rules"></a>Creación y administración de reglas de seguimiento de nivel de carpeta 
 
 Use la entidad [MailboxTrackingFolder](/reference/entities/mailboxtrackingfolder.md) para configurar y administrar mediante programación las reglas de seguimiento de nivel de carpeta. Para configurar una regla de seguimiento, use los siguientes atributos.  


|                                   Atributo                                   |                                                                                                                                                                                                                Descripción                                                                                                                                                                                                                 |
|-------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  [ExchangeFolderId](/reference/entities/mailboxtrackingfolder.md#BKMK_ExchangeFolderId)  | Especifique el Id. de carpeta de Microsoft Exchange que desea asignar. Puede usar Exchange Web Services (EWS) para recuperar el Id. de una carpeta bajo su carpeta Bandeja de entrada. Para obtener más información, vea [MSDN: Cómo: Trabajar con carpetas utilizando EWS en Exchange](https://msdn.microsoft.com/library/office/dn535504.aspx). Este atributo es obligatorio. |
|         [MailboxId](/reference/entities/mailboxtrackingfolder.md#BKMK_MailboxId)         |                                                                                                                                         Especifique el Id. de buzón de CDS for Apps para el que desea crear la regla. Este atributo es obligatorio.                                                                                                                                          |
| [RegardingObjectId](/reference/entities/mailboxtrackingfolder.md#BKMK_RegardingObjectId) |                                                                                                       Establezca el objeto referente a en CDS for Apps al que desea que se asigne la carpeta de Microsoft Exchange especificada. Se trata de un atributo opcional.                                                                                                       |

 El siguiente código de ejemplo muestra cómo puede crear una regla de seguimiento de nivel de carpeta.  

```csharp  
// Create a folder-level tracking rule  
MailboxTrackingFolder newTrackingFolder = new MailboxTrackingFolder();  

// Set the required attributes  
newTrackingFolder.ExchangeFolderId = "123456"; // Sample value. Retrieve this value using Exchange Web Services (EWS)  
newTrackingFolder.MailboxId = new EntityReference(Mailbox.EntityLogicalName, _mailboxId);  

// Set the optional attributes  
newTrackingFolder.RegardingObjectId = new EntityReference(Account.EntityLogicalName, _accountId);  
newTrackingFolder.RegardingObjectId.Name = _accountName;  
newTrackingFolder.ExchangeFolderName = "Sample Exchange Folder";  

// Execute the request to create the rule   
_folderTrackingId = _serviceProxy.Create(newTrackingFolder);  
Console.WriteLine("Created folder-level tracking rule for '{0}'.\n", _mailboxName);  
```  

 Puede crear un máximo de 25 reglas de seguimiento de nivel de carpeta por buzón. El Id. de la carpeta de Microsoft Exchange no se puede validar en el momento de crear la asignación con el SDK. Sin embargo, en cuanto cree una regla de asignación, y si el Id. de carpeta no es válido, aparecerá en la interfaz de usuario en CDS for Apps para indicar que la asignación no es válida.  

 Cualquier cambio manual realizado en el objeto referente a en los registros de actividad con seguimiento, creado en CDS for Apps como resultado de la regla de seguimiento de nivel de carpeta, será reemplazado la próxima vez que se produzca la sincronización del lado del servidor. Por ejemplo, si ha configurado una asignación entre la carpeta `Adventure Works` y la cuenta de `Adventure Works`, se realizará el seguimiento de todos los correos electrónicos de la carpeta de Microsoft Exchange `Adventure Works` como si fueran actividades en CDS for Apps con el referente establecido en el registro de cuenta de `Adventure Works`. Si cambia el referente de algunas actividades a cualquier otro registro, se reemplazará automáticamente la próxima vez que se produzca la sincronización del lado del servidor.  

<a name="Retrieve"></a>   

## <a name="retrieve-folder-level-tracking-rules-for-a-mailbox"></a>Recuperar reglas de seguimiento de nivel de carpeta para un buzón  

 Puede recuperar todas las reglas de seguimiento de nivel de carpeta para un buzón de correo con el mensaje <xref:Microsoft.Crm.Sdk.Messages.RetrieveMailboxTrackingFoldersRequest>. Pase el Id. del buzón para el que desea recuperar las reglas en la propiedad <xref:Microsoft.Crm.Sdk.Messages.RetrieveMailboxTrackingFoldersRequest>.<xref:Microsoft.Crm.Sdk.Messages.RetrieveMailboxTrackingFoldersRequest.MailboxId> y ejecute el mensaje.  

 El siguiente código de ejemplo muestra cómo puede recuperar reglas de seguimiento de nivel de carpeta para un buzón.  

```csharp  
// Retrieve the folder mapping rules for a mailbox  
RetrieveMailboxTrackingFoldersRequest req = new RetrieveMailboxTrackingFoldersRequest  
{  
    MailboxId = _mailboxId.ToString()  
};  

RetrieveMailboxTrackingFoldersResponse resp = (RetrieveMailboxTrackingFoldersResponse_serviceProxy.Execute(req);  
Console.WriteLine("Retrieved folder-level tracking rules for {0}:", _mailboxName);  
int n = 1;  
foreach (var folderMapping in resp.MailboxTrackingFolderMappings)  
{  
    Console.WriteLine("\tRule {0}: '{1}' is mapped to '{2}'.",   
        n, folderMapping.ExchangeFolderName, folderMapping.RegardingObjectName);  
    n++;  
}  
```  

### <a name="see-also"></a>Vea también  
 <xref href="Microsoft.Dynamics.CRM.RetrieveMailboxTrackingFolders?text=RetrieveMailboxTrackingFolders Function" /><br />
 [Entidad MailboxTrackingFolder](/reference/entities/mailboxtrackingfolder.md)<br />
 [Entidad de buzón](/reference/entities/mailbox.md)<br />
 [Configurar seguimiento a nivel de carpetas](/dynamics365/customer-engagement/admin/configure-outlook-exchange-folder-level-tracking)<br />
 [Entidades de sincronización del lado del servidor](server-side-synchronization-entities.md)<br />
