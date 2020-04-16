---
title: Extender Dynamics 365 for Outlook (Common Data Service) | Microsoft Docs
description: Dynamics 365 for Outlook permite a los usuarios interactuar con datos sin conexión y sin estar conectados a un servidor. Common Data Service incluye características que permiten extender las soluciones a escenarios sin conexión llamando a los servicios web sin conexión desde su código personalizado. Además, el ensamblado Sdk ofrece compatibilidad mediante programación para acciones básicas de Outlook, como sincronización, conexión y desconexión, y comprobación de estado de Dynamics 365 for Outlook. La programación sin conexión utiliza el servidor de desarrollo de ASP.NET.
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
ms.openlocfilehash: b73543ce9220db75269e9452b4e839fcd6d2cb1c
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155404"
---
<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/extend-customer-engagement-outlook 

This topic should be in powerapps-docs/developer/common-data-service/outlook-client/
-->

# <a name="extend-dynamics-365-for-outlook"></a>Extender Dynamics 365 for Outlook

> [!IMPORTANT]
> El 29/1/2018, de acuerdo con los innumerables comentarios recibidos y de nuestro deseo de seguir ayudando a nuestros clientes, hemos **decidido no dejar de usar Dynamics 365 for Outlook** (complemento de Outlook). Lea [esta entrada de blog](https://blogs.msdn.microsoft.com/crm/2018/01/29/continued-support-for-outlook-add-in-dynamics-365-for-outlook/) para obtener más detalles.

Microsoft Dynamics 365 for Outlook permite a los usuarios interactuar con datos sin conexión y sin estar conectados a un servidor. Common Data Service incluye características que permiten extender las soluciones a escenarios sin conexión llamando a los servicios web sin conexión desde su código personalizado. Además, el ensamblado <xref:Microsoft.Crm.Outlook.Sdk> ofrece compatibilidad mediante programación para acciones básicas de Outlook, como sincronización, conexión y desconexión, y comprobación de estado de Dynamics 365 for Outlook. La programación sin conexión utiliza el servidor de desarrollo de ASP.NET.  
  
 Dynamics 365 incluye características que permiten a los administradores personalizar y administrar filtros para los usuarios. Las plantillas de filtro proporcionan el punto de partida para la sincronización de entidades en Dynamics 365 for Outlook. Los filtros que determinan qué colecciones de la entidad se sincronizan con Outlook y SQL Server 2008 Express Edition para soluciones de Dynamics 365 Server habilitadas para su uso sin conexión.  
  
## <a name="in-this-section"></a>En esta sección

[Plantillas y filtros de Outlook y sin conexión](offline-outlook-filters-templates.md)<br />  
[Ejemplo: Recuperar filtros de Outlook](sample-create-retrieve-outlook-filters.md)<br />  
[Ejemplo: Usar métodos de Outlook](sample-outlook-methods.md)<br />
  
## <a name="related-sections"></a>Secciones relacionadas

<!-- TODO:
[Extend Dynamics 365](extend-dynamics-365-server.md)<br />
[Supported Extensions for Dynamics 365](supported-extensions.md)<br />
[The Metadata and Data Models in Dynamics 365](metadata-data-models.md)<br />
[Extend Dynamics 365 on the server](extend-dynamics-365-server.md)<br />
[Extend Dynamics 365 on the client](extend-client.md)<br />
[Customize Dynamics 365 applications](customize-dev/customize-applications.md)<br />
[Package and distribute extensions using solutions](package-distribute-extensions-use-solutions.md)<br />
[Integrate Dynamics 365 with SharePoint](integration-dev/integrate-sharepoint.md)<br />
 -->
<xref href="Microsoft.Dynamics.CRM.savedquery?text=savedquery EntityType" /><br />
[Entidad SavedQuery](../reference/entities/savedquery.md)<br />
  

