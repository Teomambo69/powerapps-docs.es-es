---
title: Crear aplicaciones cliente de Windows mediante las herramientas de XRM (Common Data Service para aplicaciones)| Microsoft Docs
description: Los útiles de XRM son un conjunto de API que proporciona soporte para crear aplicaciones cliente de CDS for Apps.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
ms.assetid: e2f22576-1705-4854-a804-a1ca232c0cfc
caps.latest.revision: 33
author: MattB-msft
ms.author: kvivek
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="build-windows-client-applications-using-the-xrm-tools"></a>Crear aplicaciones cliente de Windows mediante las herramientas XRM

Los útiles de XRM son un conjunto de API creadas sobre las API del ensamblado Common Data Service para aplicaciones (servicio de organización y servicio de detección) que proporcionan soporte para crear las aplicaciones cliente de Windows para CDS for Apps. Ofrece las siguientes funciones:  
  
- Admiten todos los modos de autenticación que inicien sesión en CDS for Apps.  
- Ofrece soporte de PowerShell para la autenticación y la conexión a CDS for Apps.  
- Proporciona seguridad de subprocesos para las acciones realizadas en CDS for Apps en un entorno multiprocesos. Más información [Subprocesamiento múltiple en componentes](https://msdn.microsoft.com/library/vstudio/3es4b6yy.aspx), [Componentes con seguridad para subprocesos](https://msdn.microsoft.com/library/vstudio/a8544e2s.aspx)  
- Proporciona un control de inicio de sesión común de Windows Presentation Foundation para CDS for Apps para tener una experiencia de inicio de sesión coherente en CDS for Apps desde las aplicaciones cliente de Windows.  
- Es compatible con almacenamiento seguro de credenciales de inicio de sesión y reutiliza las credenciales almacenadas para iniciar sesión automáticamente en CDS for Apps después del inicio de sesión inicial.  
- Proporciona informes de errores de diagnóstico integrado de seguimiento y rendimiento de las acciones realizadas en CDS for Apps, que puede configurar según los requisitos de la organización.  
  
## <a name="components-of-xrm-tooling"></a>Componentes de útiles de XRM  

Los útiles de XRM tienen los siguientes tres componentes:  
  
- **Interfaz para desarrolladores**: esto proporciona los métodos de nivel bajo de interacción y de contenedor para las API de ensamblado del SDK de CDS for Apps. Es un API instrumentado que proporciona un entorno seguro para subprocesos para realizar llamadas a CDS for Apps con capacidades de diagnóstico integrado para ayudar a determinar el rendimiento de llamadas individuales. También proporciona un conjunto estándar de agentes de escucha para soporte de depuración. El espacio de nombres para este componente es <xref:Microsoft.Xrm.Tooling.Connector>.  
  
- **Control de inicio de sesión común**: es un control de usuario de WPF que proporciona una interfaz de usuario común para la experiencia de inicio de sesión en CDS for Apps. El control de inicio de sesión ofrece compatibilidad con todos los modos de autenticación compatibles con CDS for Apps. El control de inicio de sesión común tiene cifrado integrado para almacenar con seguridad las credenciales/perfil y, a continuación, reutilizarlas en tiempo de ejecución para iniciar sesión automáticamente en CDS for Apps. El espacio de nombres para este componente es <xref:Microsoft.Xrm.Tooling.CrmConnectControl>.  
  
- **Utilidad de recurso web**: esto proporciona soporte para acceder a la información desde los dos tipos siguientes de recursos web en CDS for Apps: Imagen y XML. Puede obtener acceso a una imagen desde un recurso web de CDS for Apps y devolverla como objetos de WPF BitmapImage. De forma similar, puede devolver un recurso web XML como cadena. El espacio de nombres para este componente es <xref:Microsoft.Xrm.Tooling.WebResourceUtility>.  
  
## <a name="client-applications-that-use-xrm-tooling"></a>Aplicaciones cliente que usan los útiles de XRM

Las siguientes aplicaciones de la versión actual de CDS for Apps usan el control de inicio de sesión común WPF para autenticar los usuarios mientras inician sesión en CDS for Apps desde la aplicación cliente:  
  
- Unified Service Desk. Más información: [Extender Unified Service Desk](/dynamics365/customer-engagement/unified-service-desk/extend-unified-service-desk)

<!-- TODO: fix links when files added to admin guide

- Package Deployer tool. More information: [Deploy packages using Dynamics 365 Package Deployer and Windows PowerShell](../../administrator/deploy-packages-using-package-deployer-windows-powershell.md)   

- Configuration Migration tool. More information [Manage your configuration data](../../administrator/manage-configuration-data.md)  

-->
  
### <a name="see-also"></a>Vea también

[Ejemplo: inicio rápido para la API de útiles de XMR](sample-quick-start-xrm-tooling-api.md)<br />
<!-- TODO:
[Use the CDS for Apps Organization service](use-microsoft-dynamics-365-organization-service.md)<br />
[Discover the URL for Your Organization With IDiscoveryService Web Service](org-service/discover-url-organization-organization-service.md)<br />
[Write Applications and Server Extensions](extend-dynamics-365-server.md)<br /> -->
[Blog: Módulo de PowerShell para realizar operaciones de datos y manipular la configuración de usuarios y del sistema en CRM](http://blogs.msdn.com/b/crm/archive/2015/09/25/powershell-module-for-performing-data-operations-and-manipulating-user-and-system-settings-in-crm.aspx)