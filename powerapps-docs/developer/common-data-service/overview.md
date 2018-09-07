---
title: Introducción para desarrolladores de Common Data Service for Apps | Microsoft Docs
description: Obtenga información sobre cómo los desarrolladores pueden agregar valor mediante Common Data Service for Apps.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/19/2018
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3b0e2d70a9295bdf1a8a6d6a71cb6075677bb991
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42844063"
---
# <a name="common-data-service-for-apps-developer-overview"></a>Introducción para desarrolladores de Common Data Service for Apps

PowerApps ofrece a usuarios, empresas, proveedores de software independientes (ISV) e integradores de sistemas (SI) una plataforma eficaz para la creación de aplicaciones de línea de negocio. En esta versión, se ha agregado a PowerApps la ampliación de Common Data Service, que ahora se llama Common Data Service for Apps y contiene las principales funcionalidades de la plataforma Dynamics 365 que incorpora Dynamics 365 for Sales, Marketing y Customer Service.


## <a name="get-started"></a>Introducción

Si ya tiene experiencia con las aplicaciones de Dynamics 365 for Sales, Marketing o Customer Service, encontrará que podrá aplicarla para personalizar y ampliar Common Data Service for Apps.

Si no está familiarizado con las aplicaciones de Dynamics 365 for Sales, Marketing o Customer Service, en los temas siguientes se proporciona información general de los conceptos importantes para ayudarle a empezar a utilizar Common Data Service for Apps.

> [!NOTE]
> - Las aplicaciones controladas por modelos se conectan a Common Data Service for Apps. Para obtener información sobre cómo los desarrolladores pueden agregar valor en el nivel de aplicación, vea [Model-driven apps Developer Overview](../model-driven-apps/overview.md) (Introducción para desarrolladores de aplicaciones controladas por modelos). El contenido de esta sección hará referencia únicamente a lo que los desarrolladores de extensiones pueden hacer en el nivel de servicio. 
> - Ya que Common Data Service for Apps es la misma plataforma usada por las aplicaciones de Dynamics 365 for Sales, Marketing o Customer Service, encontrará información más completa para desarrolladores en la [Guía para desarrolladores de Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/developer-guide). En estos temas se proporciona una introducción con vínculos a la guía para desarrolladores y otras guías para obtener más información.


## <a name="tools-and-resources-for-developers"></a>Herramientas y recursos para desarrolladores

Los desarrolladores usarán las herramientas y recursos siguientes al trabajar con soluciones que usan Common Data Service for Apps.

### <a name="tools-available-for-download-from-nuget"></a>Herramientas disponibles para su descarga desde NuGet

Las herramientas siguientes se distribuyen en paquetes NuGet. En el tema [Guía para desarrolladores: descargar herramientas desde NuGet](/dynamics365/customer-engagement/developer/download-tools-nuget) se incluye un script de PowerShell que se puede usar para descargar y extraer las versiones más recientes de estas herramientas.

|Herramienta  |Descripción  |
|---------|---------|
|Herramienta de generación de código `CrmSvcUtil.exe`|Una herramienta de generación de código de línea de comandos que genera clases de .NET Framework enlazadas en tiempo de compilación que representan el modelo de datos de entidad que usa el servicio de organización. <br />Más información: <br />[Servicio de organización](use-web-services.md#organization-service)<br />[Crear clases de entidad con enlace en tiempo de compilación con la herramienta de generación de código (CrmSvcUtil.exe) (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/org-service/create-early-bound-entity-classes-code-generation-tool)|
|Herramienta Configuration Migration `DataMigrationUtility.exe`|Se usa para mover los datos de configuración entre entornos. Los datos de configuración se usan para definir funcionalidad personalizada y se suelen almacenar en entidades personalizadas. Esta herramienta no está diseñada para mover datos empresariales. <br /> Más información: [Mover datos de configuración entre instancias y organizaciones con la herramienta Configuration Migration (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/admin/manage-configuration-data)|
|Package Deployer `PackageDeployer.exe`|Se usa para implementar paquetes en instancias de Common Data Service for Apps. Un paquete es una unidad instalable que incluye soluciones. <br /> Más información: <br />[Implementar paquetes de solución](introduction-solutions.md#deploy-solution-packages)<br />[Crear paquetes para el Dynamics 365 Package Deployer (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/create-packages-package-deployer)|
|Herramienta de registro de complementos `PluginRegistration.exe`|Herramienta que se usa para suscribir clases de complemento de ensamblado .NET a eventos de servidor. <br />Más información: <br />[Crear un complemento](apply-business-logic-with-code.md#create-a-plug-in)<br />[Tutorial: Registrar un complemento mediante la herramienta de registro de complementos (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/walkthrough-register-plugin-using-plugin-registration-tool)|
|Herramienta SolutionPackager `SolutionPackager.exe`|Una herramienta que puede descomponer de manera reversible un archivo de solución comprimido de Common Data Service for Apps en varios archivos XML y otros archivos para que se puedan administrar con facilidad por un sistema de control de código fuente.<br /> Más información: <br />[Desarrollo en equipo de soluciones](introduction-solutions.md#team-development-of-solutions)<br />[Use la herramienta SolutionPackager para comprimir y extraer un archivo de solución (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/compress-extract-solution-file-solutionpackager)|

### <a name="net-sdk-assemblies"></a>Ensamblados del SDK de .NET

Los desarrolladores de .NET pueden usar los ensamblados siguientes. Las versiones más recientes están disponibles para descargar en los correspondientes paquetes NuGet.

#### <a name="work-with-data"></a>Trabajar con datos

Use estos ensamblados para interactuar con el servicio de organización y los servicios de detección.

Más información: [Usar el Servicio de la organización de Dynamics 365 (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-organization-service)

**Paquete NuGet**: [Microsoft.CrmSdk.CoreAssemblies](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreAssemblies/)

|Ensamblado  |Espacios de nombres  |
|---------|---------|
|Microsoft.Crm.Sdk.Proxy.dll|[Microsoft.Crm.Sdk](/dotnet/api/microsoft.crm.sdk)<br />[Microsoft.Crm.Sdk.Messages](/dotnet/api/microsoft.crm.sdk.messages)|
|Microsoft.Xrm.Sdk.dll|[Microsoft.Xrm.Sdk](/dotnet/api/microsoft.xrm.sdk)<br />[Microsoft.Xrm.Sdk.Client](/dotnet/api/microsoft.xrm.sdk.client)<br />[Microsoft.Xrm.Sdk.Discovery](/dotnet/api/microsoft.xrm.sdk.discovery)<br />[Microsoft.Xrm.Sdk.Messages](/dotnet/api/microsoft.xrm.sdk.messages)<br />[Microsoft.Xrm.Sdk.Metadata](/dotnet/api/microsoft.xrm.sdk.metadata)<br />[Microsoft.Xrm.Sdk.Metadata.Query](/dotnet/api/microsoft.xrm.sdk.metadata.query)<br />[Microsoft.Xrm.Sdk.Organization](/dotnet/api/microsoft.xrm.sdk.organization)<br />[Microsoft.Xrm.Sdk.Query](/dotnet/api/microsoft.xrm.sdk.query)<br />[Microsoft.Xrm.Sdk.WebServiceClient](/dotnet/api/microsoft.xrm.sdk.webserviceclient)|

#### <a name="create-process-designer-workflow-extensions"></a>Crear extensiones del Diseñador de procesos (flujo de trabajo)

Use este ensamblado para agregar actividades personalizadas al Diseñador de procesos. 

Más información: [Actividades de flujo de trabajo personalizadas (ensamblados de flujo de trabajo) (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/custom-workflow-activities-workflow-assemblies)

**Paquete NuGet**: [Microsoft.CrmSdk.Workflow](https://www.nuget.org/packages/Microsoft.CrmSdk.Workflow/) 

|Ensamblado|Espacios de nombres|
|---------|---------|
|Microsoft.Xrm.Sdk.Workflow.dll|[Microsoft.Xrm.Sdk.Workflow](/dotnet/api/microsoft.xrm.sdk.workflow)<br />[Microsoft.Xrm.Sdk.Workflow.Activities](/dotnet/api/microsoft.xrm.sdk.workflow.activities)<br />[Microsoft.Xrm.Sdk.Workflow.Designers](/dotnet/api/microsoft.xrm.sdk.workflow.designers)|

#### <a name="build-windows-client-applications"></a>Compilar aplicaciones cliente de Windows

Use estos ensamblados para facilitar la conexión con el servicio de organización y crear aplicaciones cliente de Windows. 

Más información: [Crear aplicaciones cliente de Windows mediante las herramientas XRM (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/build-windows-client-applications-xrm-tools)

**Paquetes NuGet**:
- [Microsoft.CrmSdk.XrmTooling.CoreAssembly](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.CoreAssembly/) (Microsoft.Xrm.Tooling.Connector.dll)
- [Microsoft.CrmSdk.XrmTooling.WpfControls](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.WpfControls/) 

|Ensamblado|Espacios de nombres  |
|---------|---------|
|Microsoft.Xrm.Tooling.Connector.dll|[Microsoft.Xrm.Tooling.Connector](/dotnet/api/microsoft.xrm.tooling.connector)<br />[Microsoft.Xrm.Tooling.Connector.Model](/dotnet/api/microsoft.xrm.tooling.connector.model)|
|Microsoft.Xrm.Tooling.CrmConnectControl.dll|[Microsoft.Xrm.Tooling.CrmConnectControl](/dotnet/api/microsoft.xrm.tooling.crmconnectcontrol)<br />[Microsoft.Xrm.Tooling.CrmConnectControl.Model](/dotnet/api/microsoft.xrm.tooling.crmconnectcontrol.model)<br />[Microsoft.Xrm.Tooling.CrmConnectControl.Properties](/dotnet/api/microsoft.xrm.tooling.crmconnectcontrol.properties)<br />[Microsoft.Xrm.Tooling.CrmConnectControl.Utility](/dotnet/api/microsoft.xrm.tooling.crmconnectcontrol.utility)|
|Microsoft.Xrm.Tooling.WebResourceUtility.dll|[Microsoft.Xrm.Tooling.WebResourceUtility](/dotnet/api/microsoft.xrm.tooling.webresourceutility)|

#### <a name="create-packages"></a>Crear paquetes

Use estos ensamblados para crear paquetes para Package Deployer.

Más información: [Crear paquetes para el Dynamics 365 Package Deployer (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/create-packages-package-deployer)

**Paquete NuGet**: [Microsoft.CrmSdk.XrmTooling.PackageDeployment](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PackageDeployment/)

|Ensamblado|Espacio de nombres  |
|---------|---------|
|Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.dll|[Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase](/dotnet/api/microsoft.xrm.tooling.packagedeployment.crmpackageextentionbase)|

#### <a name="create-custom-virtual-entity-data-providers"></a>Crear proveedores de datos de entidades virtuales personalizadas

Use este ensamblado para crear proveedores de datos de entidades virtuales personalizadas. 

Más información: [Introducción a las entidades virtuales (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve)

**Paquete NuGet**: [Microsoft.CrmSdk.Data](https://www.nuget.org/packages/Microsoft.CrmSdk.Data/)

|Ensamblado  |Espacios de nombres  |
|---------|---------|
|Microsoft.Xrm.Sdk.Data.dll|[Microsoft.Xrm.Sdk.Data](/dotnet/api/microsoft.xrm.sdk.data)<br />[Microsoft.Xrm.Sdk.Data.CodeGen](/api/microsoft.xrm.sdk.data.codegen)<br />[Microsoft.Xrm.Sdk.Data.Converters](/dotnet/api/microsoft.xrm.sdk.data.converters)<br />[Microsoft.Xrm.Sdk.Data.Exceptions](/dotnet/api/microsoft.xrm.sdk.data.exceptions)<br />[Microsoft.Xrm.Sdk.Data.Expressions](/dotnet/api/microsoft.xrm.sdk.data.expressions)<br />[Microsoft.Xrm.Sdk.Data.Infra](/dotnet/api/microsoft.xrm.sdk.data.infra)<br />[Microsoft.Xrm.Sdk.Data.Mappings](/dotnet/api/microsoft.xrm.sdk.data.mappings)|

#### <a name="extend-outlook-client"></a>Extender el cliente de Outlook

Use este ensamblado para interactuar con Microsoft Dynamics 365 para Outlook y Microsoft Dynamics 365 para Microsoft Office Outlook con acceso sin conexión. 

Más información: [Ampliar Dynamics 365 Customer Engagement para Outlook (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/extend-customer-engagement-outlook)

**Paquete NuGet**: [Microsoft.CrmSdk.Outlook](https://www.nuget.org/packages/Microsoft.CrmSdk.Outlook/)

|Ensamblado|Espacio de nombres|
|---------|---------|
|Microsoft.Crm.Outlook.Sdk.dll|[Microsoft.Crm.Outlook.Sdk](/dotnet/api/microsoft.crm.outlook.sdk)|



## <a name="community-tools-for-common-data-service-for-apps"></a>Herramientas de la comunidad para Common Data Service for Apps

La comunidad de Dynamics 365 crea herramientas. Muchas de las más populares se distribuyen en [XrmToolBox](https://www.xrmtoolbox.com/). XrmToolBox es una aplicación Windows que se conecta a Common Data Service for Apps, y proporciona herramientas para facilitar las tareas de personalización, configuración y funcionamiento. Incluye más de 30 complementos para realizar tareas de administración, personalización o configuración con más facilidad y en mucho menos tiempo.

La siguiente es una lista seleccionada de herramientas de la comunidad distribuidas a través de XrmToolBox que se pueden usar con Common Data Service for Apps.

|Herramienta  |Descripción  |
|---------|---------|
|[Administrador de atributos](https://www.xrmtoolbox.com/plugins/DLaB.Xrm.AttributeManager/)|Se usa para cambiar el nombre, eliminar o cambiar el tipo de un atributo.|
|[Early Bound Generator](https://www.xrmtoolbox.com/plugins/DLaB.Xrm.EarlyBoundGenerator/)|Genera entidades, conjuntos de opciones o acciones enlazadas en tiempo de compilación. Usa CrmSvcUtil del SDK y muestra la línea de comandos que se usa para crear las clases.|
|[Export to Excel](https://www.xrmtoolbox.com/plugins/Ryr.XrmToolBox.ExportToExcel/)|Exportar fácilmente los registros desde la vista o fetchxml seleccionado a Excel.|
|[FetchXML Builder](https://www.xrmtoolbox.com/plugins/Cinteros.Xrm.FetchXmlBuilder/)|Crear y probar consultas FetchXml|
|[Explorador de metadatos](https://www.xrmtoolbox.com/plugins/MsCrmTools.MetadataBrowser/)|Examinar los metadatos de la organización de Dynamics CRM|
|[Plugin Trace Viewer](https://www.xrmtoolbox.com/plugins/Cinteros.XrmToolBox.PluginTraceViewer/)|Investigar el registro de seguimiento de complementos con posibilidades sencillas de filtrado y visualización|
|[User Settings Utility](https://www.xrmtoolbox.com/plugins/MsCrmTools.UserSettingsUtility/)|Administrar la configuración personal de los usuarios en masa|

> [!NOTE]
> Microsoft no admite las herramientas creadas por la comunidad. Si tiene preguntas o problemas con las herramientas de la comunidad, póngase en contacto con el publicador de la herramienta.
