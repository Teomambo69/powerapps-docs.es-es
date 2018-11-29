---
title: 'Usar la biblioteca auxiliar de la API de Common Data Service para aplicaciones (C#) (Common Data Service para aplicaciones)| Microsoft Docs'
description: 'La biblioteca de código auxiliar de la API web de Common Data Service para aplicaciones ayuda a realizar tareas comunes, como la configuración de la aplicación, la autenticación con un servicio de Common Data Service para aplicaciones y la gestión de errores de respuesta HTTP'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: ba9d94fe-d189-4873-aef5-0010f3ccecba
caps.latest.revision: 7
author: brandonsimons
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-the-common-data-service-for-apps-web-api-helper-library-c"></a>Usar la biblioteca de código auxiliar de la API web de Common Data Service para aplicaciones (C#)

La mayor parte de los ejemplos de código C# de la API web de Common Data Service para aplicaciones que describe en este SDK utilizan la *biblioteca de código auxiliar de la API web de Common Data Service para aplicaciones* para ayudar a realizar tareas comunes, como configuración de aplicaciones, autenticación con un servicio de Common Data Service para aplicaciones y gestión de errores de respuesta HTTP. Puede que también encuentre este código de aplicación auxiliar útil en sus proyectos basados en .Net Framework.  
  
## <a name="obtain-and-use-the-helper-library"></a>Consiga y use biblioteca de código auxiliar

La biblioteca de código auxiliar de la API web de Common Data Service para aplicaciones se distribuye en forma de paquete NuGet [Microsoft.CrmSdk.WebApi.Samples.HelperCode](https://www.nuget.org/packages/Microsoft.CrmSdk.WebApi.Samples.HelperCode). Si no está familiarizado con la descarga e instalación de paquetes NuGet en proyectos de Visual Studio, consulte la sección [Agregar todos los recursos necesarios al proyecto](start-web-api-project-visual-studio-csharp.md#bkmk_addAllRequiredResources).  
  
> [!WARNING]
>  Este paquete Nuget es el origen autoritativo para la biblioteca de código auxiliar.  Para su comodidad, los temas de esta sección contienen una lista de código para cada clase en la biblioteca de código auxiliar. Sin embargo, no se garantiza que estas listas sean completas o actuales, por lo que no se deben usar en proyectos.  
  
## <a name="in-this-section"></a>En esta sección 
 
[Código auxiliar: clases de configuración](web-api-helper-code-configuration-classes.md)<br />
[Código auxiliar: clase de autenticación](web-api-helper-code-authentication-class.md)<br /> 
[Código auxiliar: clase CrmHttpResponseException](web-api-helper-code-crmhttpresponseexception-class.md)  
  
### <a name="see-also"></a>Vea también
 
[Introducción a la API web (C#)](get-started-dynamics-365-web-api-csharp.md)<br />
[Iniciar un proyecto de la API web en Visual Studio (C#)](start-web-api-project-visual-studio-csharp.md)<br />
[Realizar operaciones mediante la API web](perform-operations-web-api.md)
