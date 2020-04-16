---
title: 'Ejemplo: Inicio rápido la API de útiles de XRM (Common Data Service)| Microsoft Docs'
description: ''
ms.custom: ''
ms.date: 03/27/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: samples
applies_to:
- Dynamics 365 (online)
ms.assetid: 060d45bb-b7fd-48bd-ab8f-629c1b8bc1dc
caps.latest.revision: 20
author: MattB-msft
ms.author: nabuthuk
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 12c1b55605c9d85ee1cb840c54908085d7a57cac
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154880"
---
# <a name="sample-quick-start-for-xrm-tooling-api"></a>Ejemplo: inicio rápido para la API de útiles de XMR

El ejemplo de QuickStart es un ejemplo de código administrado .NET Framework que indica cómo conectar una instancia de Common Data Service mediante las API de útiles de XMR y realizar operaciones de creación, actualización, recuperación y eliminación básicas en una entidad. Para obtener más información acerca de los útiles de XMR, consulte [Crear aplicaciones cliente de Windows mediante los útiles XRM](build-windows-client-applications-xrm-tools.md).

Descargue el ejemplo: [Trabajar con API de útiles de XRM](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/Xrm%20Tooling/Quick%20start%20for%20XRM%20Tooling%20API).

## <a name="how-to-run-the-sample"></a>Cómo ejecutar el ejemplo

1. Descargar y extraer la muestra para que tenga una copia local.  
2. Abra el archivo `Quick start for XRM Tooling\C#\QuickStartXRMToolingWPFClient.sln` en Visual Studio.  
3. Presione **F5** para compilar y ejecutar el programa.  


## <a name="demonstrates"></a>Demostraciones

- El código de ejemplo se genera a través de la plantilla **Aplicación WPF para CRM** SDK que proporciona un control de inicio de sesión común integrado para autenticación y almacenamiento en caché y reutilización de credenciales. Para obtener más información sobre el control de inicio de sesión común y cómo usar la plantilla de SDK en Visual Studio, consulte [Usar el control de inicio de sesión común de los útiles de XRM](use-xrm-tooling-common-login-control-client-applications.md).  
- No se usó un código auxiliar para definir una conexión con Common Data Service.  
- Luego de conectarse a Common Data Service, el ejemplo realiza operaciones de creación, actualización, recuperación y eliminación en una entidad de cuenta.  
- Almacena las credenciales de usuario en un archivo de configuración (`Default_QuickStartXRMToolingWPFClient.exe.config`) en la carpeta `c:\Users\`*`<username>`*`\AppData\Roaming\Microsoft\QuickStartXRMToolingWPFClient` cuando el ejemplo se ejecuta por primera vez y, posteriormente pregunta al usuario si desea almacenar o especificar las nuevas credenciales en el tiempo de ejecución para iniciar sesión en Common Data Service.  
- Genera los siguientes archivos de registro, si se produce algún problema, para ayudar en la solución de problemas:  
- Login_ErrorLog.log: Para informar errores de inicio de sesión. Este archivo está disponible en `C:\Users\`*`<username>`*`\AppData\Roaming\Microsoft\QuickStartXRMToolingWPFClient`.  
- QuickStartXRMToolingWPFClient.log: Para informar sobre errores de funcionamiento. Este archivo está disponible en la misma ubicación que la aplicación ejecutable, que se encuentra en la carpeta de depuración del proyecto de Visual Studio.  

### <a name="see-also"></a>Vea también

[Usar el control de inicio de sesión común de los útiles de XRM](use-xrm-tooling-common-login-control-client-applications.md)<br />
[Crear aplicaciones cliente de Windows mediante las herramientas XRM](build-windows-client-applications-xrm-tools.md)<br />

