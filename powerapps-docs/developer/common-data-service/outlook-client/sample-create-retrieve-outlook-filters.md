---
title: 'Ejemplo: Crear y recuperar filtros de Outlook (Common Data Service)| Microsoft Docs'
description: Este ejemplo muestra cómo recuperar filtros para Microsoft Dynamics 365 for Outlook.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
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
ms.openlocfilehash: 22fb005832149316eb8c967b425f6058d7e1bcf9
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155388"
---
# <a name="sample-create-and-retrieve-outlook-filters"></a>Ejemplo: crear y recuperar filtros de Outlook

Este código de muestra es para Common Data Service. Para descargar el ejemplo, consulte [ejemplo: crear y recuperar filtros de Outlook](/dynamics365/customer-engagement/developer/outlook-client/sample-create-retrieve-outlook-filters).

## <a name="prerequisites"></a>Requisitos previos

Se requiere una conexión a Internet para descargar el proyecto de ejemplo y para restablecer los paquetes NuGet que se usan en el proyecto de ejemplo.

## <a name="demonstrates"></a>Demostraciones  

 Este ejemplo muestra cómo recuperar filtros para Microsoft Dynamics 365 for Outlook.  
  
## <a name="example"></a>Ejemplo  

```csharp
// Create and Retrieve Offline Filter
// In your Outlook client, this will appear in the System Filters tab
// under File | CRM | Synchronize | Outlook Filters.
Console.Write("Creating offline filter");
String contactName = String.Format("offlineFilteredContact {0}",
    DateTime.Now.ToLongTimeString());
String fetchXml = String.Format("<fetch version=\"1.0\" output-format=\"xml-platform\" mapping=\"logical\"><entity name=\"contact\"><attribute name=\"contactid\" /><filter type=\"and\">" +
    "<condition attribute=\"ownerid\" operator=\"eq-userid\" /><condition attribute=\"description\" operator=\"eq\" value=\"{0}\" />" +
    "<condition attribute=\"statecode\" operator=\"eq\" value=\"0\" /></filter></entity></fetch>", contactName);
SavedQuery filter = new SavedQuery();
filter.FetchXml = fetchXml;
filter.IsQuickFindQuery = false;
filter.QueryType = SavedQueryQueryType.OfflineFilters;
filter.ReturnedTypeCode = Contact.EntityLogicalName;
filter.Name = "ReadOnlyFilter_" + contactName;
filter.Description = "Sample offline filter for Contact entity";
_offlineFilter = _serviceProxy.Create(filter);

Console.WriteLine(" and retrieving offline filter");
SavedQuery result = (SavedQuery)_serviceProxy.Retrieve(
    SavedQuery.EntityLogicalName,
    _offlineFilter,
    new ColumnSet("name", "description"));
Console.WriteLine("Name: {0}", result.Name);
Console.WriteLine("Description: {0}", result.Description);
Console.WriteLine();

// Create and Retrieve Offline Template
// In your Outlook client, this will appear in the User Filters tab
// under File | CRM | Synchronize | Outlook Filters.
Console.Write("Creating offline template");
String accountName = String.Format("offlineFilteredAccount {0}",
    DateTime.Now.ToLongTimeString());
fetchXml = String.Format("<fetch version=\"1.0\" output-format=\"xml-platform\" mapping=\"logical\"><entity name=\"account\"><attribute name=\"accountid\" /><filter type=\"and\">" +
    "<condition attribute=\"ownerid\" operator=\"eq-userid\" /><condition attribute=\"name\" operator=\"eq\" value=\"{0}\" />" +
    "<condition attribute=\"statecode\" operator=\"eq\" value=\"0\" /></filter></entity></fetch>", accountName);
SavedQuery template = new SavedQuery();
template.FetchXml = fetchXml;
template.IsQuickFindQuery = false;
template.QueryType = SavedQueryQueryType.OfflineTemplate;
template.ReturnedTypeCode = Account.EntityLogicalName;
template.Name = "ReadOnlyFilter_" + accountName;
template.Description = "Sample offline template for Account entity";
_offlineTemplate = _serviceProxy.Create(template);

Console.WriteLine(" and retrieving offline template");
result = (SavedQuery)_serviceProxy.Retrieve(
    SavedQuery.EntityLogicalName,
    _offlineTemplate,
    new ColumnSet("name", "description"));
Console.WriteLine("Name: {0}", result.Name);
Console.WriteLine("Description: {0}", result.Description);
Console.WriteLine();
```
  
### <a name="see-also"></a>Vea también  

[Ampliar Dynamics 365 for Outlook](extend-dynamics-365-outlook.md)<br />
[Ejemplo: Usar métodos de Outlook](sample-outlook-methods.md)<br />
[Plantillas y filtros de Outlook y sin conexión](offline-outlook-filters-templates.md)<br />
[Referencia de la entidad SavedQuery](../reference/entities/savedquery.md) 
<xref:Microsoft.Xrm.Sdk.IOrganizationService>