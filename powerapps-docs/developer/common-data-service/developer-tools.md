---
title: Herramientas y recursos de desarrollo (Common Data Service para aplicaciones) | Microsoft Docs
description: Información sobre las herramientas y recursos disponibles para trabajar con soluciones.
ms.custom: ''
ms.date: 1/31/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="developer-tools-and-resources"></a>Herramientas y recursos de desarrollo

Los programadores utilizarán las herramientas y los recursos siguientes al trabajar con soluciones que usan Common Data Service para aplicaciones.

## <a name="tools-available-for-download-from-nuget"></a>Herramientas disponibles para descargar desde NuGet

Las siguientes herramientas se distribuyen en paquetes de NuGet. El tema [Guía para desarrolladores: Descargar herramientas de NuGet](/dynamics365/customer-engagement/developer/download-tools-nuget) incluye un script de PowerShell que puede usar para descargar y extraer las últimas versiones de estas herramientas.

|Herramienta  |Descripción  |
|---------|---------|
|Herramienta de generación de código `CrmSvcUtil.exe`|Herramienta de generación de código de la línea de comandos que genera clases de .NET Framework enlazadas en tiempo que representan el modelo de datos de la entidad que usa el servicio de la organización. <br />Más información: <br />[Servicio de organización](work-with-data-cds.md#organization-service)<br />[Crear las clases de entidad con enlace en tiempo de compilación con la herramienta de generación de código ](/dynamics365/customer-engagement/developer/org-service/create-early-bound-entity-classes-code-generation-tool)|
|Herramienta Configuration Migration `DataMigrationUtility.exe`|Usado para mover datos de configuración en los entornos. Los datos de configuración se usan para definir funciones personalizadas y normalmente se almacenan en entidades personalizadas. Esta herramienta no está diseñada para mover datos profesionales. <br /> Más información: [Guía del administrador de Common Data Service para aplicaciones: Mover datos de configuración entre instancias y organizaciones con la herramienta de migración de configuración](/dynamics365/customer-engagement/admin/manage-configuration-data)|
|Package Deployer `PackageDeployer.exe`|Se usa para implementar paquetes en las instancias de Common Data Service para aplicaciones. El paquete es una unidad instalable que incluye soluciones. <br /> Más información: <br />[Implementar paquetes de soluciones](introduction-solutions.md#deploy-solution-packages)<br />[Crear paquetes para Package Deployer de CDS for Apps](/dynamics365/customer-engagement/developer/create-packages-package-deployer)|
|Herramienta de registro de complementos `PluginRegistration.exe`|Herramienta usada para suscribir tipos de complementos ensamblados de .NET a eventos del servidor. <br />Más información: <br />[Crear un complemento](apply-business-logic-with-code.md#create-a-plug-in)<br />[Registro de un complemento](register-plug-in.md)|
|Herramienta SolutionPackager `SolutionPackager.exe`|Herramienta que puede descomponer de forma reversible un archivo comprimido de solución de Common Data Service para aplicaciones en varios archivos XML y otros archivos de forma que el sistema de control de código fuente pueda administrarlos fácilmente.<br /> Más información: <br />[Desarrollo del equipo de soluciones](introduction-solutions.md#team-development-of-solutions)<br />[Use la herramienta SolutionPackager para comprimir para extraer un archivo de solución](/dynamics365/customer-engagement/developer/compress-extract-solution-file-solutionpackager)|

## <a name="net-sdk-assemblies"></a>Ensamblados .NET SDK 

A continuación se describen ensamblados que los desarrolladores de .NET pueden usar. Las últimas versiones están disponibles para descargarlas en los paquetes correspondientes de NuGet.

### <a name="work-with-data"></a>Trabajar con datos

Use estos ensamblados para interactuar con el servicio de organización y los servicios de detección.

Más información: [Usar el servicio de organización de CSD for Apps](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-organization-service)

**Paquete de NuGet**: [Microsoft.CrmSdk.CoreAssemblies](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreAssemblies/)

|Ensamblado  |Espacios de nombres  |
|---------|---------|
|Microsoft.Crm.Sdk.Proxy.dll|[Microsoft.Crm.Sdk](/dotnet/api/microsoft.crm.sdk)<br />[Microsoft.Crm.Sdk.Messages](/dotnet/api/microsoft.crm.sdk.messages)|
|Microsoft.Xrm.Sdk.dll|[Microsoft.Xrm.Sdk](/dotnet/api/microsoft.xrm.sdk)<br />[Microsoft.Xrm.Sdk.Client](/dotnet/api/microsoft.xrm.sdk.client)<br />[Microsoft.Xrm.Sdk.Discovery](/dotnet/api/microsoft.xrm.sdk.discovery)<br />[Microsoft.Xrm.Sdk.Messages](/dotnet/api/microsoft.xrm.sdk.messages)<br />[Microsoft.Xrm.Sdk.Metadata](/dotnet/api/microsoft.xrm.sdk.metadata)<br />[Microsoft.Xrm.Sdk.Metadata.Query](/dotnet/api/microsoft.xrm.sdk.metadata.query)<br />[Microsoft.Xrm.Sdk.Organization](/dotnet/api/microsoft.xrm.sdk.organization)<br />[Microsoft.Xrm.Sdk.Query](/dotnet/api/microsoft.xrm.sdk.query)<br />[Microsoft.Xrm.Sdk.WebServiceClient](/dotnet/api/microsoft.xrm.sdk.webserviceclient)|

### <a name="create-process-designer-workflow-extensions"></a>Crear extensiones del diseñador de procesos (Flujo de trabajo)

Use este ensamblado para agregar actividades personalizadas al diseñador del proceso. 

Más información [Actividades de flujo de trabajo personalizadas (ensamblados de flujo de trabajo)](/dynamics365/customer-engagement/developer/custom-workflow-activities-workflow-assemblies)

**Paquete de NuGet**: [Microsoft.CrmSdk.Workflow](https://www.nuget.org/packages/Microsoft.CrmSdk.Workflow/) 

|Ensamblado|Espacios de nombres|
|---------|---------|
|Microsoft.Xrm.Sdk.Workflow.dll|[Microsoft.Xrm.Sdk.Workflow](/dotnet/api/microsoft.xrm.sdk.workflow)<br />[Microsoft.Xrm.Sdk.Workflow.Activities](/dotnet/api/microsoft.xrm.sdk.workflow.activities)<br />[Microsoft.Xrm.Sdk.Workflow.Designers](/dotnet/api/microsoft.xrm.sdk.workflow.designers)|

### <a name="build-windows-client-applications"></a>Crear aplicaciones cliente de Windows

Use estos ensamblados para facilitar el conectarse con el servicio de organización y crear aplicaciones cliente de Windows. 

Más información [Crear aplicaciones cliente de Windows mediante las herramientas XRM](/dynamics365/customer-engagement/developer/build-windows-client-applications-xrm-tools)

**Paquetes NuGet**:
- [Microsoft.CrmSdk.XrmTooling.CoreAssembly](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.CoreAssembly/) (Microsoft.Xrm.Tooling.Connector.dll)
- [Microsoft.CrmSdk.XrmTooling.WpfControls](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.WpfControls/) 

|Ensamblado|Espacios de nombres  |
|---------|---------|
|Microsoft.Xrm.Tooling.Connector.dll|[Microsoft.Xrm.Tooling.Connector](/dotnet/api/microsoft.xrm.tooling.connector)<br />[Microsoft.Xrm.Tooling.Connector.Model](/dotnet/api/microsoft.xrm.tooling.connector.model)|
|Microsoft.Xrm.Tooling.CrmConnectControl.dll|[Microsoft.Xrm.Tooling.CrmConnectControl](/dotnet/api/microsoft.xrm.tooling.crmconnectcontrol)<br />[Microsoft.Xrm.Tooling.CrmConnectControl.Model](/dotnet/api/microsoft.xrm.tooling.crmconnectcontrol.model)<br />[Microsoft.Xrm.Tooling.CrmConnectControl.Properties](/dotnet/api/microsoft.xrm.tooling.crmconnectcontrol.properties)<br />[Microsoft.Xrm.Tooling.CrmConnectControl.Utility](/dotnet/api/microsoft.xrm.tooling.crmconnectcontrol.utility)|
|Microsoft.Xrm.Tooling.WebResourceUtility.dll|[Microsoft.Xrm.Tooling.WebResourceUtility](/dotnet/api/microsoft.xrm.tooling.webresourceutility)|

### <a name="create-packages"></a>Crear paquetes

Use estos ensamblados para crear paquetes para Package Deployer.

Más información: [Crear paquetes para CDS for Apps Package Deployer](/dynamics365/customer-engagement/developer/create-packages-package-deployer)

**Paquete de NuGet**: [Microsoft.CrmSdk.XrmTooling.PackageDeployment](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PackageDeployment/)

|Ensamblado|Espacio de nombres  |
|---------|---------|
|Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.dll|[Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase](/dotnet/api/microsoft.xrm.tooling.packagedeployment.crmpackageextentionbase)|

### <a name="create-custom-virtual-entity-data-providers"></a>Crear proveedores de datos de entidad virtuales personalizados

Use este ensamblado para crear los proveedores de datos visuales personalizados de la entidad. 

Más información: [Introducción a las entidades virtuales](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve)

**Paquete de NuGet**: [Microsoft.CrmSdk.Data](https://www.nuget.org/packages/Microsoft.CrmSdk.Data/)

|Ensamblado  |Espacios de nombres  |
|---------|---------|
|Microsoft.Xrm.Sdk.Data.dll|[Microsoft.Xrm.Sdk.Data](/dotnet/api/microsoft.xrm.sdk.data)<br />[Microsoft.Xrm.Sdk.Data.CodeGen](/api/microsoft.xrm.sdk.data.codegen)<br />[Microsoft.Xrm.Sdk.Data.Converters](/dotnet/api/microsoft.xrm.sdk.data.converters)<br />[Microsoft.Xrm.Sdk.Data.Exceptions](/dotnet/api/microsoft.xrm.sdk.data.exceptions)<br />[Microsoft.Xrm.Sdk.Data.Expressions](/dotnet/api/microsoft.xrm.sdk.data.expressions)<br />[Microsoft.Xrm.Sdk.Data.Infra](/dotnet/api/microsoft.xrm.sdk.data.infra)<br />[Microsoft.Xrm.Sdk.Data.Mappings](/dotnet/api/microsoft.xrm.sdk.data.mappings)|

### <a name="extend-outlook-client"></a>Extender cliente de Outlook

Use este ensamblado para interactuar con Microsoft Dynamics 365 for Outlook y Microsoft CDS for Apps para Microsoft Office Outlook con acceso sin conexión. 

Más información: [Ampliar Dynamics 365 for Outlook](/dynamics365/customer-engagement/developer/extend-customer-engagement-outlook)

**Paquete de NuGet**: [Microsoft.CrmSdk.Outlook](https://www.nuget.org/packages/Microsoft.CrmSdk.Outlook/)

|Ensamblado|Espacio de nombres|
|---------|---------|
|Microsoft.Crm.Outlook.Sdk.dll|[Microsoft.Crm.Outlook.Sdk](/dotnet/api/microsoft.crm.outlook.sdk)|

