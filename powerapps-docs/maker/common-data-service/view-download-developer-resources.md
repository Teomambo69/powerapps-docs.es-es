---
title: Visualización o descarga de recursos para desarrolladores de PowerApps y Common Data Service | MicrosoftDocs
description: Buscar recursos para desarrolladores y direcciones URL del extremo de servicio PowerApps y Common Data Service
keywords: ''
ms.date: 09/25/2019
ms.service: powerapps
ms.custom: null
ms.topic: article
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

# <a name="view-or-download-developer-resources"></a>Visualización o descarga de recursos para programadores

Esta página ofrece recursos para desarrolladores e información acerca de la instancia específica en la que está trabajando. 

## <a name="view-the-developer-resources-page-for-your-environment"></a>Ver la página de Recursos para desarrolladores para su entorno

1. En el portal de PowerApps seleccione el ![Botón Configuración](../../administrator/media/settings-button-nav-bar.png) botón Configuración y elija **Personalizaciones avanzadas**.

    ![Personalizaciones avanzadas](media/advanced-customizations-menu.png)

1. En el panel **Personalizaciones avanzadas**, elija el vínculo **Recursos para desarrolladores** :<br />![Vínculo Recursos para desarrolladores](media/developer-resources-link.png)

## <a name="getting-started"></a>Introducción 

Esta sección proporciona los vínculos para que los desarrolladores busquen recursos. Están disponibles los siguientes recursos:


|Vínculo |Descripción|
|---------|---------|
|[Centro para desarrolladores](https://go.microsoft.com/fwlink/?LinkId=551006).|Empiece aquí para documentos de desarrollo en PowerApps y Common Data Service.|
|[Comunidad/Foro de PowerApps](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1)|Formule y responda preguntas de la comunidad de PowerApps.|
|[NuGetPaquetes](https://www.nuget.org/profiles/crmsdk)|Descubra los paquetes de NuGet para agregar ensamblados de SDK a sus proyectos.|
|[Descargar herramientas](/powerapps/developer/common-data-service/download-tools-nuget)|Las herramientas que necesita se pueden descargar desde NuGet. Use el script de PowerShell en esta página para obtener las últimas versiones.|
|[Código de ejemplo](https://go.microsoft.com/fwlink/?LinkId=553007)|Un repositorio de GitHub para ejemplos de PowerApps.|
|[Información general para desarrolladores](https://go.microsoft.com/fwlink/?LinkId=550995)|Vincular a un tema que proporciona información general para desarrolladores.|

## <a name="connect-your-apps-to-this-instance-of-common-data-service"></a>Conectar las aplicaciones a esta instancia de Common Data Service

En esta sección se proporciona la información necesaria para conectarse a su instancia de Common Data Service.

### <a name="instance-web-api"></a>API web de la instancia

Es la dirección URL de la API web para su instancia. La API web es una API OData v4 RESTful. También puede descargar el documento de servicio que describe los metadatos y las operaciones disponible en su instancia. Más información: [Documentación para desarrolladores: Usar la API web de Common Data Service](/powerapps/developer/common-data-service/webapi/overview)

### <a name="organization-service"></a>Servicio de organización

Es la dirección URL del extremo de SOAP para el servicio de la organización para su instancia.
Puede descargar el WSDL para este servicio aquí, pero normalmente usará la herramienta de generación de código CrmSvcUtil.exe para crear clases de entidad para los proyectos de .NET. Más información: 
- [Documentación para desarrolladores: Generar clases de entidad con enlace en tiempo de compilación con la herramienta de generación de código (CrmSvcUtil.exe)](/powerapps/developer/common-data-service/org-service/generate-early-bound-classes)
- [Documentación para desarrolladores: Usar el servicio de organización para leer y escribir datos o metadatos](/powerapps/developer/common-data-service/org-service/overview)

### <a name="instance-reference-information"></a>Información de referencia de la instancia

Esta información describe de forma única la instancia. Hay un **Id.** de GUID y un **Nombre único**.
Esta información es necesaria cuando se usan extensiones de Azure con su instancia.
Más información: [Documentación para desarrolladores: Extensiones de Azure para Dynamics 365](/dynamics365/customer-engagement/developer/azure-extensions)

## <a name="connect-your-apps-to-the-common-data-service-discovery-service"></a>Conectar las aplicaciones al Servicio de detección de Common Data Service

Puesto que los usuarios pueden acceder a varios entornos de Common Data Service, los servicios de detección permiten recuperar los entornos disponibles a los que puede acceder un usuario en función de sus credenciales.

### <a name="discovery-web-api"></a>API web de detección

Es la dirección del extremo para la versión v4 de RESTful OData del servicio de detección que se usará para su instancia. También puede descargar el documento de servicio aquí.
Más información: [Documentación para desarrolladores: Detectar la dirección URL de su organización con la API web](/powerapps/developer/common-data-service/webapi/discover-url-organization-web-api)


### <a name="discovery-service"></a>Servicio de detección

Es la dirección del extremo para la versión de SOAP del servicio de detección que se usará para su instancia. También puede descargar el documento de servicio aquí.
Más información: [Documentación para desarrolladores: Detectar la dirección URL de su organización con el servicio de detección](/dynamics365/customer-engagement/developer/org-service/discover-url-organization-organization-service)
  
