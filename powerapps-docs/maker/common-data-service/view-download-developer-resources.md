---
title: Visualización o descarga de recursos para programadores | Microsoft Docs
description: Búsqueda de recursos para programadores y direcciones URL de punto de conexión de servicio
keywords: ''
ms.date: 06/06/2018
ms.service: crm-online
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: e200d242-ff3f-48e5-af32-aed050e02441
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.openlocfilehash: ae93b57d9ead3a62fb538ae986eb524367259545
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39711015"
---
<!-- TODO: The Developer Resources page have to be updated to match this page -->

# <a name="view-or-download-developer-resources"></a>Visualización o descarga de recursos para programadores

Esta página proporciona recursos para desarrolladores e información de la instancia específica en la que está trabajando. 

## <a name="view-the-developer-resources-page-for-your-environment"></a>Visualización de la página de recursos para desarrolladores de su entorno

1. En el portal de PowerApps, seleccione el ![botón Configuración](../../administrator/media/settings-button-nav-bar.png) botón Configuración y seleccione **Personalizaciones avanzadas**.

    ![Personalizaciones avanzadas](media/advanced-customizations-menu.png)

1. En el panel **Personalizaciones avanzadas**, elija el vínculo **Recursos de desarrollador**:<br />![Recursos para el desarrollador](media/developer-resources-link.png)

## <a name="getting-started"></a>Introducción 

Esta sección proporciona vínculos para que los desarrolladores encuentren recursos. Están disponibles los siguientes recursos:


|Vínculo |Descripción|
|---------|---------|
|[Centro para desarrolladores](https://go.microsoft.com/fwlink/?LinkId=551006)|El punto de entrada principal de documentación de los desarrolladores.|
|[Foros para desarrolladores](https://go.microsoft.com/fwlink/?LinkId=550993)|Intercambie preguntas y respuestas con otros desarrolladores.|
|[Paquetes NuGet](https://go.microsoft.com/fwlink/?LinkId=550994)|Descubra paquetes NuGet para agregar ensamblados de SDK a los proyectos.|
|[Herramientas de descarga](https://go.microsoft.com/fwlink/?LinkID=512122)|Las herramientas que necesita están disponibles para su descarga desde NuGet. Use el script de PowerShell de esta página para obtener las versiones más recientes.|
|[Código de ejemplo](https://go.microsoft.com/fwlink/?LinkId=553007)|Una lista de ejemplos disponibles.|
|[Información general para desarrolladores](https://go.microsoft.com/fwlink/?LinkId=550995)|Vínculo a un tema que proporciona una introducción para desarrolladores.|

<!-- TODO update 512122 to go to https://docs.microsoft.com/dynamics365/customer-engagement/developer/download-tools-nuget -->


## <a name="connect-your-apps-to-this-instance-of-common-data-service-for-apps"></a>Conexión de sus aplicaciones a esta instancia de Common Data Service for Apps

Esta sección proporciona la información que necesita para conectarse a la instancia de Common Data Service for Apps.

### <a name="instance-web-api"></a>API web de la instancia

Se trata de la URL de la API web de la instancia. La API web es una API RESTful de OData v4. También puede descargar el documento de servicio que se describe los metadatos y las operaciones disponibles en la instancia. Más información: [Documentación para desarrolladores: Uso de la API web de Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-web-api)

### <a name="organization-service"></a>Servicio de organización

Se trata de la URL del punto de conexión SOAP del servicio de organización de la instancia.
Puede descargar el archivo WSDL de este servicio aquí, pero normalmente usará la herramienta de generación de código CrmSvcUtil.exe con el fin de generar clases de entidad para proyectos de. NET. Más información: 
- [Documentación para desarrolladores: Creación de las clases de entidad con enlace en tiempo de compilación con la herramienta de generación de código (CrmSvcUtil.exe)](/dynamics365/customer-engagement/developer/org-service/create-early-bound-entity-classes-code-generation-tool)
- [Documentación para desarrolladores: Uso del servicio de organización para leer y escribir datos o metadatos](/dynamics365/customer-engagement/developer/org-service/use-organization-service-read-write-data-metadata)

### <a name="instance-reference-information"></a>Información de referencia de la instancia

Esta información describe de forma única la instancia. Hay un **identificador** de GUID y un **nombre único**.
Esta información es necesaria cuando se usa las extensiones de Azure con la instancia.
Más información: [Documentación para desarrolladores: Extensiones de Azure para Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/azure-extensions)

## <a name="connect-your-apps-to-the-common-data-service-for-apps-discovery-service"></a>Conexión de aplicaciones al servicio de detección de Common Data Service for Apps

Puesto que los usuarios pueden acceder a varios entornos de CDS for Apps, los servicios de detección permiten recuperar los entornos disponibles a los que puede acceder un usuario en función de sus credenciales.

### <a name="discovery-web-api"></a>API web de detección

Es la dirección del punto de conexión de la versión v4 de RESTful OData del servicio de detección que se usará para su instancia. También puede descargar el documento de servicio aquí.
Más información: [Documentación para desarrolladores: Detección de la dirección URL de su organización con la API web](/dynamics365/customer-engagement/developer/webapi/discover-url-organization-web-api)


### <a name="discovery-service"></a>Servicio de detección

Es la dirección del punto de conexión de la versión de SOAP del servicio de detección que se usará para su instancia. También puede descargar el documento de servicio aquí.
Más información: [Documentación para desarrolladores: Detección de la dirección URL de su organización mediante la utilización del servicio de detección](/dynamics365/customer-engagement/developer/org-service/discover-url-organization-organization-service)
  
### <a name="more-information"></a>Más información

[Documentación para desarrolladores: Página de recursos para desarrolladores](/dynamics365/customer-engagement/developer/developer-resources-page)<br />
[Documentación para desarrolladores: Uso de la API web de Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-web-api)<br />
[Documentación para desarrolladores: Uso del servicio de organización para leer y escribir datos o metadatos](/dynamics365/customer-engagement/developer/org-service/use-organization-service-read-write-data-metadata)<br />
[Documentación para desarrolladores: Extensiones de Azure para Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/azure-extensions)<br />
[Documentación para desarrolladores: Detección de la dirección URL de su organización con la API web](/dynamics365/customer-engagement/developer/webapi/discover-url-organization-web-api)<br />
[Documentación para desarrolladores: Detección de la dirección URL de su organización mediante la utilización del servicio de detección](/dynamics365/customer-engagement/developer/org-service/discover-url-organization-organization-service)
  

