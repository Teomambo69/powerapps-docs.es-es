---
title: 'Ejemplo: Usar métodos de Dynamics 365 for Outlook (Common Data Service)| Microsoft Docs'
description: Este ejemplo muestra cómo usar los métodos disponibles en el ensamblado `Microsoft.Crm.Outlook.Sdk.dll`.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: sriharibs
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-use-dynamics-365-for-outlook-methods"></a>Ejemplo: usar métodos de Dynamics 365 para Outlook

Este código de ejemplo es para Common Data Service. Para descargar el ejemplo, consulte [ejemplo: uso de Dynamics 365 para métodos de Outlook](https://msdn.microsoft.com/en-us/library/gg309513.aspx).

## <a name="prerequisites"></a>Requisitos previos

Se requiere una conexión a Internet para descargar el proyecto de ejemplo y para restablecer los paquetes NuGet que se usan en el proyecto de ejemplo.
  
## <a name="demonstrates"></a>Demostraciones  
 Este ejemplo muestra cómo usar los métodos disponibles en el ensamblado `Microsoft.Crm.Outlook.Sdk.dll`.  
  
## <a name="example"></a>Ejemplo  

```csharp
// Set up the CRM Service.  
CrmOutlookService outlookService = new CrmOutlookService();

// Determine if the Outlook client is running
if (outlookService.IsCrmClientLoaded)
{
    if (outlookService.IsCrmDesktopClient)
    {
        // The desktop client cannot go offline
        Console.WriteLine("CRM Client Desktop URL: " +
            outlookService.ServerUri.AbsoluteUri);
        Console.WriteLine("CRM Client state: " +
            outlookService.State.ToString());
    }
    else
    {
        // See if laptop client is offline
        if (outlookService.IsCrmClientOffline)
        {
            Console.WriteLine("CRM Client Offline URL: " +
                outlookService.ServerUri.AbsoluteUri);
            Console.WriteLine("CRM Client state: " +
                outlookService.State.ToString());

            // Take client online
            // NOTE: GoOnline() will automatically Sync up with CRM
            // database, no need to call Sync() manually
            Console.WriteLine("Going Online...");
            outlookService.GoOnline();

            Console.WriteLine("CRM Client state: " +
                outlookService.State.ToString());
        }
        else
        {
            Console.WriteLine("CRM Client Online URL: " +
                outlookService.ServerUri.AbsoluteUri);
            Console.WriteLine("CRM Client state: " +
                outlookService.State.ToString());

            // Take client offline 
            // NOTE: GoOffline triggers a synchronization of the
            // offline database with the online server.
            // If a sync is not required, you can use SetOffline().
            Console.WriteLine("Going Offline...");
            outlookService.GoOffline();

            Console.WriteLine("CRM Client state: " +
                outlookService.State.ToString());
        }
    }
}
```
  
### <a name="see-also"></a>Vea también  

[Ampliar Dynamics 365 para Outlook](extend-dynamics-365-outlook.md)<br />
<xref:Microsoft.Crm.Outlook.Sdk.CrmOutlookService><br />
<xref:Microsoft.Crm.Outlook.Sdk.CrmOutlookService.GoOnline><br />
<xref:Microsoft.Crm.Outlook.Sdk.CrmOutlookService.GoOffline>