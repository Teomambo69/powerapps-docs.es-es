---
title: Visualización o descarga de recursos para desarrolladores de Power Apps y Common Data Service | MicrosoftDocs
description: Buscar recursos para desarrolladores y direcciones URL del extremo de servicio para Power Apps y Common Data Service
keywords: ''
ms.date: 04/09/2020
ms.service: powerapps
ms.custom: ''
ms.topic: article
ms.assetid: e200d242-ff3f-48e5-af32-aed050e02441
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: pehecke
ms.suite: ''
ms.tgt_pltfrm: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bd3b907411d0e43b572908204aeff9c64069ed15
ms.sourcegitcommit: cbaf5ba8b6435796a538ece2da5cc172c0781fad
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2020
ms.locfileid: "3254402"
---
# <a name="view-or-download-developer-resources"></a>Visualización o descarga de recursos para programadores

Esta página ofrece recursos para desarrolladores e información acerca de la instancia específica en la que está trabajando. 

## <a name="view-the-developer-resources-page-for-your-environment"></a>Ver la página de Recursos para desarrolladores para su entorno

1. Inicie sesión en [Power Apps](https://make.powerapps.com) y luego seleccione su entorno en la esquina superior derecha.

1. Seleccione el botón **Configuración** en la esquina superior derecha y después seleccione **Configuración avanzada**.

    ![Personalizaciones avanzadas](media/advanced-customizations-menu.png)

1. En la página de **Configuración**, seleccione la flecha desplegable situada junto a **Configuración** y, a continuación, seleccione **Personalizaciones**.

    ![Seleccionar Personalizaciones](media/dev-customization.png)

1. En la página **Personalizaciones**, seleccione **Recursos de desarrolladores** para ver la página con recursos para desarrolladores.

    ![Página de recursos para desarrolladores](media/developer-resources-page.png)

Las siguientes secciones explican la información disponible en la página de recursos para desarrolladores.

## <a name="getting-started"></a>Introducción 

Esta sección proporciona los vínculos para que los desarrolladores busquen recursos. Están disponibles los siguientes recursos:


|Vínculo |Descripción|
|---------|---------|
|[Centro de desarrollo](https://go.microsoft.com/fwlink/?LinkId=551006)|El punto de entrada principal para la documentación para desarrolladores.|
|[Foros de desarrolladores](https://go.microsoft.com/fwlink/?LinkId=550993)|Formule preguntas y obtenga respuestas de otros desarrolladores.|
|[Paquetes NuGet SDK](https://go.microsoft.com/fwlink/?LinkId=550994)|Descubra los paquetes de NuGet para agregar ensamblados de SDK a sus proyectos.|
|Descarga de SDK|Ya no enviamos el paquete SDK como descarga en el Centro de descargas de Microsoft. En cambio, los ensamblajes y herramientas del SDK están disponibles como [paquetes NuGet](https://go.microsoft.com/fwlink/?LinkId=550994). Use el script de PowerShell en este artículo para obtener la última versión de las herramientas del SDK: [Descargar herramientas de NuGet](https://docs.microsoft.com/powerapps/developer/common-data-service/download-tools-nuget)|
|[Código de ejemplo](https://go.microsoft.com/fwlink/?LinkId=553007)|Una lista de ejemplos de código disponible.|
|[Información general para desarrolladores](https://go.microsoft.com/fwlink/?LinkId=550995)|Vincular a un tema que proporciona información general para desarrolladores.|


## <a name="connect-your-apps-to-this-instance-of-common-data-service"></a>Conectar las aplicaciones a esta instancia de Common Data Service

En esta sección se proporciona la información necesaria para conectarse a su instancia de Common Data Service.

### <a name="instance-web-api"></a>API web de la instancia

Es la dirección URL de la API web para su instancia. La API web es una API OData v4 RESTful. También puede descargar el documento de servicio que describe los metadatos y las operaciones disponible en su instancia. Más información: [Documentación para desarrolladores: Usar la API web de Common Data Service](/powerapps/developer/common-data-service/webapi/overview)

### <a name="organization-service"></a>Servicio de organización

Es la dirección URL del extremo de SOAP para el servicio de la organización para su instancia.
Puede descargar el WSDL para este servicio aquí, pero normalmente usará la herramienta de generación de código CrmSvcUtil.exe para crear clases de entidad para los proyectos de .NET. Más información: 
- [Documentación para desarrolladores: Crear clases de entidad con enlace en tiempo de compilación con la herramienta de generación de código (CrmSvcUtil.exe)](/powerapps/developer/common-data-service/org-service/generate-early-bound-classes)
- [Documentación para desarrolladores: Usar el servicio de organización](/powerapps/developer/common-data-service/org-service/overview)

### <a name="instance-reference-information"></a>Información de referencia de la instancia

Esta información describe de forma única la instancia. Hay un **Id.** de GUID y un **Nombre único**.
Esta información es necesaria cuando se usan extensiones de Azure con su instancia.
Más información: [Integración de Azure](/powerapps/developer/common-data-service/azure-integration)

## <a name="connect-your-apps-to-the-common-data-service-discovery-service"></a>Conectar las aplicaciones al Servicio de detección de Common Data Service

Puesto que los usuarios pueden acceder a varios entornos de Common Data Service, los servicios de detección permiten recuperar los entornos disponibles a los que puede acceder un usuario en función de sus credenciales.

### <a name="discovery-web-api"></a>API web de detección

Es la dirección del extremo para la versión v4 de RESTful OData del servicio de detección que se usará para su instancia. También puede descargar el documento de servicio aquí.
Más información: [Documentación para desarrolladores: Detectar la dirección URL de su organización con la API web](/powerapps/developer/common-data-service/webapi/discover-url-organization-web-api)


### <a name="discovery-service"></a>Servicio de detección

Es la dirección del extremo para la versión de SOAP del servicio de detección que se usará para su instancia. También puede descargar el documento de servicio aquí.
Más información: [Documentación para desarrolladores: Detectar la dirección URL de su organización con el servicio de organización](/powerapps/developer/common-data-service/org-service/discovery-service)
  
  

