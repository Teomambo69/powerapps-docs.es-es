---
title: Visualización o descarga de recursos para desarrolladores | MicrosoftDocs
description: Buscar recursos para desarrolladores y direcciones URL del extremo de servicio
keywords: ''
ms.date: 06/06/2018
ms.service: crm-online
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: e200d242-ff3f-48e5-af32-aed050e02441
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
<!-- TODO: The Developer Resources page have to be updated to match this page -->

# <a name="view-or-download-developer-resources"></a>Visualización o descarga de recursos para programadores

Esta página ofrece recursos para desarrolladores e información acerca de la instancia específica en la que está trabajando. 

## <a name="view-the-developer-resources-page-for-your-environment"></a>Ver la página de Recursos para desarrolladores para su entorno

1. En el portal de PowerApps seleccione el botón de configuración ![Botón Configuración](../../administrator/media/settings-button-nav-bar.png) y elija **Personalizaciones avanzadas**.

    ![Personalizaciones avanzadas](media/advanced-customizations-menu.png)

1. En el panel **Personalizaciones avanzadas**, elija el vínculo **Recursos para desarrolladores** :<br />![Vínculo Recursos para desarrolladores](media/developer-resources-link.png)

## <a name="getting-started"></a>Introducción 

Esta sección proporciona los vínculos para que los desarrolladores busquen recursos. Están disponibles los siguientes recursos:


|Vínculo |Descripción|
|---------|---------|
|[Centro de desarrollo](https://go.microsoft.com/fwlink/?LinkId=551006)|El punto de entrada principal para la documentación para desarrolladores.|
|[Foros de desarrolladores](https://go.microsoft.com/fwlink/?LinkId=550993)|Formule preguntas y obtenga respuestas de otros desarrolladores.|
|[Paquetes de NuGet](https://go.microsoft.com/fwlink/?LinkId=550994)|Descubra los paquetes de NuGet para agregar ensamblados de SDK a sus proyectos.|
|[Descargar herramientas](https://go.microsoft.com/fwlink/?LinkID=512122)|Las herramientas que necesita se pueden descargar desde NuGet. Use el script de PowerShell en esta página para obtener las últimas versiones.|
|[Código de ejemplo](https://go.microsoft.com/fwlink/?LinkId=553007)|Una lista de ejemplos disponible.|
|[Información general para desarrolladores](https://go.microsoft.com/fwlink/?LinkId=550995)|Vincular a un tema que proporciona información general para desarrolladores.|

<!-- TODO update 512122 to go to https://docs.microsoft.com/dynamics365/customer-engagement/developer/download-tools-nuget -->


## <a name="connect-your-apps-to-this-instance-of-common-data-service-for-apps"></a>Conectar sus aplicaciones a esta instancia de Common Data Service for Apps

En esta sección se proporciona la información necesaria para conectarse a su instancia de Common Data Service for Apps.

### <a name="instance-web-api"></a>API web de la instancia

Es la dirección URL de la API web para su instancia. La API web es una API OData v4 RESTful. También puede descargar el documento de servicio que describe los metadatos y las operaciones disponible en su instancia. Más información: [Documentación para desarrolladores: Uso de la API web de Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-web-api)

### <a name="organization-service"></a>Servicio de organización

Es la dirección URL del extremo de SOAP para el servicio de la organización para su instancia.
Puede descargar el WSDL para este servicio aquí, pero normalmente usará la herramienta de generación de código CrmSvcUtil.exe para crear clases de entidad para los proyectos de .NET. Más información: 
- [Documentación para desarrolladores: Crear clases de entidad con enlace en tiempo de compilación con la herramienta de generación de código (CrmSvcUtil.exe)](/dynamics365/customer-engagement/developer/org-service/create-early-bound-entity-classes-code-generation-tool)
- [Documentación para desarrolladores: Usar el servicio de organización para leer y escribir datos o metadatos](/dynamics365/customer-engagement/developer/org-service/use-organization-service-read-write-data-metadata)

### <a name="instance-reference-information"></a>Información de referencia de la instancia

Esta información describe de forma única la instancia. Hay un **Id.** de GUID y un **Nombre único**.
Esta información es necesaria cuando se usan extensiones de Azure con su instancia.
Más información: [Documentación para desarrolladores: Extensiones de Azure para Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/azure-extensions)

## <a name="connect-your-apps-to-the-common-data-service-for-apps-discovery-service"></a>Conectar sus aplicaciones al servicio de detección de Common Data Service for Apps

Puesto que los usuarios pueden acceder a varios entornos de CDS for Apps, los servicios de detección permiten recuperar los entornos disponibles a los que puede acceder un usuario en función de sus credenciales.

### <a name="discovery-web-api"></a>API web de detección

Es la dirección del extremo para la versión v4 de RESTful OData del servicio de detección que se usará para su instancia. También puede descargar el documento de servicio aquí.
Más información: [Documentación para desarrolladores: Detectar la dirección URL de su organización con la API web](/dynamics365/customer-engagement/developer/webapi/discover-url-organization-web-api)


### <a name="discovery-service"></a>Servicio de detección

Es la dirección del extremo para la versión de SOAP del servicio de detección que se usará para su instancia. También puede descargar el documento de servicio aquí.
Más información: [Documentación para desarrolladores: Detectar la dirección URL de su organización con el servicio de detección](/dynamics365/customer-engagement/developer/org-service/discover-url-organization-organization-service)
  
### <a name="more-information"></a>Más información

[Documentación para desarrolladores: Página de recursos para desarrolladores](/dynamics365/customer-engagement/developer/developer-resources-page)<br />
[Documentación para desarrolladores: Uso de la API web de Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-web-api)<br />
[Documentación para desarrolladores: Usar el servicio de organización para leer y escribir datos o metadatos](/dynamics365/customer-engagement/developer/org-service/use-organization-service-read-write-data-metadata)<br />
[Documentación para desarrolladores: Extensiones de Azure para Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/azure-extensions)<br />
[Documentación para desarrolladores: Detectar la dirección URL de su organización con la API web](/dynamics365/customer-engagement/developer/webapi/discover-url-organization-web-api)<br />
[Documentación para desarrolladores: Detectar la dirección URL de su organización con el servicio de detección](/dynamics365/customer-engagement/developer/org-service/discover-url-organization-organization-service)
  

