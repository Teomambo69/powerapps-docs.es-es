---
title: Crear paquetes para Package Deployer (Common Data Service) | Microsoft Docs
description: Cree paquetes que los administradores pueden implementar en las instancias de Common Data Service.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
ms.openlocfilehash: d713bee10d98006e8310d614175cdaf6898631e2
ms.sourcegitcommit: 3b68c4e29be4e8f68c0bfb88abdd1bbdf0187c57
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2020
ms.locfileid: "3080850"
---
# <a name="create-packages-for-the-package-deployer"></a>Crear paquetes para el Package Deployer

Package Deployer permite a los administradores implementar paquetes en instancias de Common Data Service. Un *paquete* puede estar compuesto por cualquiera de estos elementos o por todos ellos:  

- Uno o varios archivos de solución de Common Data Service.  
- Archivos sin formato o archivo de datos de configuración exportado desde la herramienta Configuration Migration. Para obtener más información sobre la herramienta, consulte [Mover datos de configuración entre instancias y organizaciones con la herramienta de migración de configuración](/dynamics365/customer-engagement/admin/manage-configuration-data).  
- El código personalizado que puede ejecutarse antes, durante o después del paquete se implementa en la instancia de Common Data Service.  
- Contenido HTML específico del paquete que mostrarse al principio y al final del proceso de implementación. Puede resultar útil para proporcionar una descripción de las soluciones y los archivos que se implementan en el paquete.  

Common Data Service proporciona una plantilla de Visual Studio para crear estos paquetes que se pueden usar con la herramienta Package Deployer para implementarlos en una instancia de Common Data Service.

<a name="Prereq"></a>
 
## <a name="prerequisites"></a>Requisitos previos  

- Asegúrese de que tiene todas las soluciones y archivos listos que desea incluir en el paquete.  
- Microsoft .NET Framework 4.6.2
- Visual Studio 2015 o Visual Studio 2017
- Administrador de paquetes de NuGet para [Visual Studio 2015](https://visualstudiogallery.msdn.microsoft.com/5d345edc-2e2d-4a9c-b73b-d53956dc458d)
    - En Visual Studio 2017, NuGet y el Administrador de paquetes de NuGet automáticamente se instalan cuando se selecciona cualquier carga de trabajo relacionada con .NET.
- Plantillas del SDK de Microsoft Dynamics CRM para Visual Studio que contienen la plantilla del paquete. Puede obtenerla descargando las [plantillas del SDK de Microsoft Dynamics CRM](https://go.microsoft.com/fwlink/p/?LinkId=400925) y haciendo doble clic en el archivo `CRMSDKTemplates.vsix` para instalar la plantilla en Visual Studio.  



<a name="HowTo"></a>
   
## <a name="create-a-package"></a>Crear un paquete  

 Siga estos cinco pasos para crear un paquete:  

- [Paso 1: Cree un proyecto usando la plantilla](create-packages-package-deployer.md#Step1)  
- [Paso 2: Agregue los archivos al proyecto](create-packages-package-deployer.md#Step2)  
- [Paso 3: Actualizar los archivos HTML](create-packages-package-deployer.md#Step3)  
- [Paso 4: Especifique los valores de configuración para el paquete](create-packages-package-deployer.md#Step4)  
- [Paso 5: Defina código personalizado para el paquete](create-packages-package-deployer.md#Step5)  

<a name="Step1"></a>  
 
#### <a name="step-1-create-a-project-using-the-template"></a>Paso 1: Cree un proyecto usando la plantilla  

1. Inicie Visual Studio y cree un nuevo proyecto.  
2. En el cuadro de diálogo **Nuevo proyecto**: 

   1. En la lista de plantillas instaladas, expanda **Visual c#**, y seleccione **Plantillas de SDK de Dynamics 365**.  
   2. Asegúrese de que **.NET Framework 4.6.2** está seleccionado.  
   3. Seleccione **Paquete de Dynamics 365**.  
   4. Especifique el nombre y la ubicación del proyecto, y haga clic en **Aceptar**.  

    ![Nuevo proyecto para crear un paquete personalizado](../media/crm-sdkv6-packagedeployer-01.png)

<a name="Step2"></a>   

#### <a name="step-2-add-your-files-to-the-project"></a>Paso 2: Agregue los archivos al proyecto  

1.  En el panel **Explorador de soluciones**, agregue sus soluciones y archivos en la carpeta **PkgFolder**.  
2.  Para cada archivo que agrega en la carpeta **PkgFolder**, en el panel **Propiedades**, establezca el valor **Copiar en el directorio de resultados** como **Copiar siempre**.  Esto garantiza que el archivo está disponible en el paquete generado.  

<a name="Step3"></a>  
 
#### <a name="step-3-update-the-html-files-english-and-other-languages"></a>Paso 3: Actualice los archivos HTML: Inglés y otros idiomas  

1.  En el panel del Explorador de soluciones, expanda **PkgFolder** > **Content** > **en-us**. Encontrará dos carpetas llamadas `EndHTML` y `WelcomeHTML`. Estas carpetas contienen el HTML y los archivos asociados que le permiten mostrar información al final y al principio del proceso de implementación del paquete. Edite los archivos de la carpeta HTML de estas carpetas para agregar información para el paquete.  

2.  También puede agregar los archivos HTML en el paquete en otros idiomas para que el contenido en HTML se muestre en el idioma en función de la configuración regional del equipo del usuario. Para ello:  

    1.  Cree una copia de la carpeta **en-us** bajo **PkgFolder** > **Content**.  
    2.  Cambie el nombre de la carpeta copiada al idioma correspondiente. Por ejemplo, en el idioma español, cambie el nombre a **es-ES**.  
    3.  Modifique el contenido de los archivos HTML para agregar contenido en español.  

<a name="Step4"></a>   

#### <a name="step-4-specify-the-configuration-values-for-the-package"></a>Paso 4: Especifique los valores de configuración para el paquete  

1. Defina la configuración del paquete agregando información sobre el paquete en el archivo **ImportConfig.xml** disponible en **PkgFolder**. Haga doble clic en el archivo para abrirlo y editarlo. La siguiente lista proporciona información acerca de cada parámetro y nodo en el archivo de configuración.  

    `installsampledata`  
    `True` o `false`. Si `true` instala datos de ejemplo en instancias de Common Data Service. Estos son los mismos datos de ejemplo que puede instalar desde el área **Configuración** > **Administración de datos** en Common Data Service.  

    `waitforsampledatatoinstall`  
   **True** o **false**. Si **true** y si **installsampledata** también se establece en **true**, espere los datos de ejemplo para instalar antes de implementar el paquete.  

   > [!NOTE]
   >  Asegúrese de establece **installsampledata** como **verdadero** si está configurando `waitforsampledatatoinstall` como **verdadero**.  

    `agentdesktopzipfile`  
    Nombre del archivo zip para desempaquetar. Si especifica un nombre de archivo .zip aquí, este agrega una pantalla durante el proceso de implementación del paquete que le solicita que seleccione una ubicación donde desea desempaquetar el contenido del archivo.  

    Esto es de uso general para crear los paquetes para Unified Service Desk for Dynamics 365. Para obtener más información sobre Unified Service Desk, consulte la [Guía de administración de Unified Service Desk 3.0.](/dynamics365/customer-engagement/unified-service-desk/administration-guide-unified-service-desk-3).  

    `agentdesktopexename`  
    Nombre del archivo .exe o .msi del archivo zip o una dirección URL que se invocará al final del proceso de implementación.  

    Esto es de uso general para crear los paquetes para Unified Service Desk.  

    `crmmigdataimportfile`  
    Nombre del archivo de datos de configuración predeterminada (.zip) exportado usando la herramienta Configuration Migration.  

   - También puede importar una versión localizada de los archivos de datos de configuración basada en el identificador de configuración regional (LCID) especificado mediante nuevos valores de tiempo de ejecución mientras ejecuta el implementador de paquetes. Use el nodo `<cmtdatafile>` (explicado posteriormente) para especificar las versiones localizadas del archivo de datos de configuración en un paquete y luego use el método `OverrideConfigurationDataFileLanguage` (explicado posteriormente) para especificar la lógica para importar el archivo de datos de configuración basado en el identificador de configuración regional especificado mediante los valores de tiempo de ejecución. No puede importar más de un archivo de datos de configuración con un paquete a la vez.  

   - Para Common Data Service (local), si el archivo de datos de configuración contiene información acerca del usuario, y las instancias de Common Data Service de origen y destino se encuentran en el mismo dominio de Active Directory, la información del usuario se importará a la instancia de Common Data Service de destino. Para importar la información de usuario a una instancia de Common Data Service (local) en otro dominio, debe incluir el archivo de asignación de usuarios (.xml) generado mediante la herramienta Configuration Migration en el proyecto, y especificarlo junto con el archivo de datos de configuración mediante el atributo `usermapfilename` en el nodo `<cmtdatafile>` explicado más adelante. La información de los usuarios no se puede importar a instancias de Common Data Service.  
     Nodo de `<solutions>`  
     Contiene una matriz de los nodos de `<configsolutionfile>` que describen las soluciones para importar. El orden de las soluciones en este nodo indica el orden en que las soluciones se importarán en la instancia de Common Data Service de destino.  

     Nodo de `<configsolutionfile>`  
     Use este nodo bajo el nodo `<solutions>` para especificar las soluciones individuales y la información siguiente para cada solución que desea importar:  

   - `solutionpackagefilename`: Especifique el nombre del archivo .zip de la solución. Requerido.  

   - `overwriteunmanagedcustomizations`: Especifique si desea sobrescribir personalizaciones no administradas cuando importa una solución que ya existe en la instancia de Dynamics 365 de destino. Esto es opcional, y si no especifica este atributo, de forma predeterminada las personalizaciones nos administradas de la solución existente se mantienen en la instancia de Dynamics 365 de destino.  

   - `publishworkflowsandactivateplugins`: Especifique si publicar flujos de trabajo y activar complementos en la instancia de Dynamics 365 de destino después de importar la solución. Esto es opcional, y si no especifica este atributo, de forma predeterminada los flujos de trabajo se publican y los complementos se activan después de que la solución se importe en la instancia de Dynamics 365 de destino.  

     Puede agregar varios nombres de archivo de solución en un paquete agregando tantos nodos de `<configsolutionfile>`. Por ejemplo, si desea importar tres archivos de solución, agréguelos así:  

   ```xml  

   <solutions>  
   <configsolutionfile solutionpackagefilename="SampleSolutionOne_1_0_managed.zip"  
   overwriteunmanagedcustomizations="false"  
   publishworkflowsandactivateplugins="true"/>  
   <configsolutionfile solutionpackagefilename="SampleSolutionTwo_1_0_managed.zip"  
   overwriteunmanagedcustomizations="false"  
   publishworkflowsandactivateplugins="true"/>  
   <configsolutionfile solutionpackagefilename="SampleSolutionThree_1_0_managed.zip" />  
   </solutions>  

   ```  

    Nodo de `<filestoimport>`  
    Contiene una matriz de los nodos de `<configimportfile>` y de `<zipimportdetails>` que se usan para describir los archivos individuales y los archivos zip respectivamente que se importarán.  

    Nodo de `<configimportfile>`  
    Use este nodo bajo el nodo de `<configimportfile>` para describir un archivo que se importará a Common Data Service. Puede agregar varios archivos en un paquete agregando tantos nodos de `<configimportfile>`.  

   ```xml  

   <filestoimport>  
   <configimportfile filename="File.csv"  
   filetype="CSV"  
   associatedmap="FileMap"  
   importtoentity="FileEntity"  
   datadelimiter=""  
   fielddelimiter="comma"  
   enableduplicatedetection="true"  
   isfirstrowheader="true"  
   isrecordownerateam="false"  
   owneruser=""  
   waitforimporttocomplete="true" />  
   <configimportfile filename="File.zip"  
   filetype="ZIP"  
   associatedmap="FileMapName"  
   importtoentity="FileEntity"  
   datadelimiter=""  
   fielddelimiter="comma"  
   enableduplicatedetection="true"  
   isfirstrowheader="true"  
   isrecordownerateam="false"  
   owneruser=""  
   waitforimporttocomplete="true"/>  

   </filestoimport>  

   ```  

    Este tiene los siguientes atributos:  

   |Atributo|Descripción|
   |--|-|
   |`filename`| Nombre del archivo que contiene los datos de importación. Si el archivo es un archivo .zip, un nodo de `<zipimportdetails>` debe estar presente con un nodo de `<zipimportdetail>` para cada archivo del archivo .zip. |
   |`filetype`|Puede ser csv, xml o zip.          |
   |`associatedmap`|Nombre de la asignación de datos de importación de Common Data Service a usar con este archivo. Si se deja en blanco, trata de usar el nombre de la asignación de datos de importación determinado por el sistema para este archivo.|
   |`importtoentity`| Puede ser el nombre del exe en el archivo zip, una dirección URL o un archivo .msi para proporcionar un vínculo para invocar al final del proceso.|
   |`datadelimiter`| Nombre del delimitador de datos usado en el archivo de importación. Los valores válidos son comillas simples o comillas dobles.|
   |`fielddelimiter`|Nombre del delimitador de campos usado en el archivo de importación. Los valores válidos son coma, dos puntos o comillas simples.|
   |`enableduplicatedetection`|Indica si desea habilitar reglas de detección de duplicados en la importación de datos. Los valores válidos son **true** o **false**.|
   |`isfirstrowheader`|Usado para denotar que la primera fila del archivo de importación contiene los nombres de campos. Los valores válidos son `true` o `false`. |
   |`isrecordownerateam`|Indica si el propietario del registro de importación debe ser un equipo. Los valores válidos son `true` o `false`.|
   |`owneruser`|Indica el Id. de usuario que debe ser el propietario de los registros. El valor predeterminado es el usuario que ha iniciado sesión actualmente.  |
   |`waitforimporttocomplete`|Si es `true`, el sistema espera que la importación termine antes de continuar. Si `false`, pone los trabajos en cola y continúa.|

    Nodo de `<zipimportdetails>`  
    Este nodo contiene una matriz de los nodos de `<zipimportdetail>` que describen los archivos incluidos en un archivo zip que se usa para importar a Dynamics 365.  

    Nodo de `<zipimportdetail>`  
    Use este nodo bajo el nodo de `<zipimportdetails>` para proporcionar información acerca de un archivo individual en un archivo .zip que se especifica en el nodo de `<configimportfile>`.  

   ```xml  
   <filestoimport>  
   ...  
   ...  
   <zipimportdetails>  
   <zipimportdetail filename="subfile1.csv" filetype="csv" importtoentity="account" />  
   <zipimportdetail filename="subfile2.csv" filetype="csv" importtoentity="contact" />  
   </zipimportdetails>  
   </filestoimport>  

   ```  

    Este tiene los siguientes atributos:  

   |Atributo|Descripción|  
   |---------------|-----------------|  
   |`filename`|Nombre del archivo que contiene los datos de importación.|  
   |`filetype`|Puede ser csv o xml.|  
   |`importtoentity`|Puede ser el nombre del exe en el archivo zip, una dirección URL o un archivo .msi para proporcionar un vínculo para invocar al final del proceso.|  

    Nodo de `<filesmapstoimport>`  
    Este nodo contiene una matriz de los nodos de `<configmapimportfile>` para importar. El orden de los archivos de asignación de este nodo indica el orden en que se importan. Para obtener información acerca de los mapas de datos, consulte [Crear asignaciones de datos para la importación](../create-data-maps-for-import.md).  

    Nodo de `<configimportmapfile>`  
    Use este nodo bajo el nodo de `<filesmapstoimport>` para proporcionar información acerca de un archivo de asignación individual para importar en Common Data Service.  

   ```xml  
   <filesmapstoimport>  
   <configimportmapfile filename="FileMap.xml" />  
   </filesmapstoimport>  
   ```  

    Nodo de `<cmtdatafiles>`  
    Este nodo contiene una matriz de nodos `<cmtdatafile>` que contiene la versión localizada del archivo de datos de configuración que se importará.  

    Nodo de `<cmtdatafile>`  
    Use este nodo en el nodo `<cmtdatafiles>` para especificar los archivos de datos de configuración localizados junto con el identificador de configuración regional (obligatorio) y el archivo de asignación de la información del usuario (opcional). Por ejemplo:  

   ```xml  
   <cmtdatafiles>  
   <cmtdatafile filename="data_1033.zip" lcid="1033" usermapfilename="UserMap.xml" />  
   <cmtdatafile filename="data_1041.zip" lcid="1041" usermapfilename="" />  
   </cmtdatafiles>  
   ```  

    Puede definir la lógica personalizada en el método `OverrideConfigurationDataFileLanguage` (explicado posteriormente) para importar un archivo de datos de configuración localizado en lugar del predeterminado (especificado en crmmigdataimportfile) basado en el valor del identificador de configuración regional (LCID) especificado mediante los valores de tiempo de ejecución (explicados posteriormente).  

2. Haga clic en **Guardar todo**.  

    Lo siguiente representa el contenido de un archivo de `ImportConfig.xml` de ejemplo.  

   ```xml  
   <?xml version="1.0" encoding="utf-16"?>  
   <configdatastorage xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"  
   xmlns:xsd="https://www.w3.org/2001/XMLSchema"  
   installsampledata="true"  
   waitforsampledatatoinstall="true"  
   agentdesktopzipfile=""  
   agentdesktopexename=""  
   crmmigdataimportfile="data_1033.zip">  
   <solutions>  
   <configsolutionfile solutionpackagefilename="SampleSolutionOne_1_0_managed.zip"  
   overwriteunmanagedcustomizations="false"  
   publishworkflowsandactivateplugins="true"/>  
   <configsolutionfile solutionpackagefilename="SampleSolutionTwo_1_0_managed.zip"  
   overwriteunmanagedcustomizations="false"  
   publishworkflowsandactivateplugins="true"/>  
   <configsolutionfile solutionpackagefilename="SampleSolutionThree_1_0_managed.zip" />  
   </solutions>  
   <filestoimport>  
   <configimportfile filename="SampleOption.csv"  
   filetype="CSV"  
   associatedmap="SampleOption"  
   importtoentity="sample_option"  
   datadelimiter=""  
   fielddelimiter="comma"  
   enableduplicatedetection="true"  
   isfirstrowheader="true"  
   isrecordownerateam="false"  
   owneruser=""  
   waitforimporttocomplete="false"/>  
   <configimportfile filename="File.zip"  
   filetype="ZIP"  
   associatedmap="FileMapName"  
   importtoentity="FileEntity"  
   datadelimiter=""  
   fielddelimiter="comma"  
   enableduplicatedetection="true"  
   isfirstrowheader="true"  
   isrecordownerateam="false"  
   owneruser=""  
   waitforimporttocomplete="true"/>  
   <zipimportdetails>  
   <zipimportdetail filename="subfile1.csv"  
   filetype="csv"  
   importtoentity="account" />  
   <zipimportdetail filename="subfile2.csv"  
   filetype="csv"  
   importtoentity="contact" />  
   </zipimportdetails>  
   </filestoimport>  
   <filesmapstoimport>  
   <configimportmapfile filename="SampleOption.xml" />  
   </filesmapstoimport>  
   <cmtdatafiles>  
   <cmtdatafile filename="data_1033.zip"  
   lcid="1033"  
   usermapfilename="UserMap.xml" />  
   <cmtdatafile filename="data_1041.zip"  
   lcid="1041"  
   usermapfilename="" />  
   </cmtdatafiles>  
   </configdatastorage>  

   ```  

<a name="Step5"></a>  
 
#### <a name="step-5-define-custom-code-for-your-package"></a>Paso 5: Defina código personalizado para el paquete  

1. En el panel del Explorador de soluciones, haga doble clic en el archivo **PackageTemplate.cs** en la raíz para editarlo.  

2. En el archivo PackageTemplate.cs, puede:  

   1. Escriba código personalizado para ejecutar cuando el paquete se inicie en la definición del método de sustitución de `InitializeCustomExtension`.  

       Este método se puede usar para permitir a los usuarios usar los parámetros de tiempo de ejecución mientras ejecutan un paquete. Como programador, puede agregar compatibilidad para cualquier parámetro de tiempo de ejecución al paquete mediante la propiedad <xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.IImportExtensions2.RuntimeSettings> siempre que haga que el código lo procese basándose en la entrada del usuario.  

       Por ejemplo, el siguiente código de ejemplo habilita un parámetro de tiempo de ejecución llamado `SkipChecks` para el paquete que tiene dos valores posibles: true o false. El código de ejemplo comprueba si el usuario ha especificado cualquier parámetro de tiempo de ejecución al ejecutar Package Deployer (usando la línea de comandos o PowerShell) y, a continuación procesa convenientemente la información. Si el usuario no especifica ningún parámetro en tiempo de ejecución al ejecutar el paquete, el valor de la propiedad <xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.IImportExtensions2.RuntimeSettings> será cero.  

      ```csharp  
      public override void InitializeCustomExtension()  
      {  
      // Do nothing.  

      // Validate the state of the runtime settings object.  
      if (RuntimeSettings != null)  
      {  
      PackageLog.Log(string.Format("Runtime Settings populated.  Count = {0}", RuntimeSettings.Count));  
      foreach (var setting in RuntimeSettings)  
      {  
      PackageLog.Log(string.Format("Key={0} | Value={1}", setting.Key, setting.Value.ToString()));  
      }  

      // Check to see if skip checks is present.  
      if ( RuntimeSettings.ContainsKey("SkipChecks") )  
      {  
      bool bSkipChecks = false;  
      if (bool.TryParse((string)RuntimeSettings["SkipChecks"], out bSkipChecks))  
      OverrideDataImportSafetyChecks = bSkipChecks;  
      }  
      }  
      else  
      PackageLog.Log("Runtime Settings not populated");  
      }  
      ```  

       Esto permite al administrador usar la línea de comandos o el cmdlet [Import-CrmPackage](/powershell/module/microsoft.xrm.tooling.packagedeployment/import-crmpackage) para especificar si se omiten las pruebas de seguridad al ejecutar la herramienta Package Deployer para importar el paquete. Más información: [Implementar paquetes mediante Package Deployer de Dynamics 365 y Windows PowerShell](/dynamics365/customer-engagement/admin/deploy-packages-using-package-deployer-windows-powershell)  

   2. Introduzca código personalizado antes de importar las soluciones en la definición del método de reemplazo de `PreSolutionImport` para especificar si mantener o sobrescribir personalizaciones mientras actualiza la solución especificada en una instancia de Common Data Service de destino y si se activan automáticamente complementos y flujos de trabajo.  

   3. Utilice la definición del método de sustitución de `RunSolutionUpgradeMigrationStep` para realizar la transformación de datos o actualizar entre dos versiones de una solución. Este método se llama solo si la solución que va a importar ya está presente en la instancia de Common Data Service de destino.  

        Esta característica espera los siguientes parámetros:  

        |    Parámetro    |            Descripción             |
        |-----------------|------------------------------------|
        | `solutionName`  |        Nombre de la solución        |
        |  `oldVersion`   | Número de versión de la solución antigua |
        |  `newVersion`   | Número de versión de la solución nueva |
        | `oldSolutionId` |     GUID de la solución antigua.      |
        | `newSolutionId` |     GUID de la solución nueva.      |


   4. Escriba código personalizado para ejecutar antes de que la importación de la solución se complete en la definición de reemplazo del método `BeforeImportStage`. Los datos de ejemplo y algunos archivos sin formato para soluciones especificadas en el archivo `ImportConfig.xml` se importan antes de que la importación de la solución se complete.  

   5. Reemplace el idioma seleccionado actualmente para la importación de datos de configuración mediante la definición del método de reemplazo de `OverrideConfigurationDataFileLanguage`. Si el Id. de configuración regional (LCID) especificado del idioma especificado no se encuentra en la lista de idiomas disponibles en el paquete, se importa el archivo de datos predeterminado.  

       Especifique los idiomas disponibles para los datos de configuración en el nodo `<cmtdatafiles>` del archivo `ImportConfig.xml`. El archivo de importación de datos de configuración predeterminado se especifica en el atributo `crmmigdataimportfile` en el archivo `ImportConfig.xml`.  

       Omitir las verificaciones de datos (<xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.IImportExtensions2.OverrideDataImportSafetyChecks> = true) puede ser efectivo aquí si está seguro de que la instancia de Common Data Service de destino no contiene ningún dato.  

   6. Escriba código personalizado para ejecutar después de que la importación de la solución se complete en la definición de reemplazo del método `AfterPrimaryImport`. Los archivos sin formato restantes que no se importaron anteriormente, antes de que la importación de la solución se iniciara, ahora se importan.  

   7. Cambie el nombre predeterminado de la carpeta del paquete de PkgFolder al nombre del paquete que desee. Para ello, cambie el nombre de la carpeta `PkgFolder` > en el panel **Explorador de soluciones** y luego edite el valor de devolución en la propiedad `GetImportPackageDataFolderName`.  

      ```csharp  
      public override string GetImportPackageDataFolderName  
      {  
      get  
      {  
      // WARNING this value directly correlates to the folder name in the Solution Explorer where the ImportConfig.xml and sub content is located.  
      // Changing this name requires that you also change the correlating name in the Solution Explorer  
      return "PkgFolder";  
      }  
      }  
      ```  

   8. Cambie el nombre del paquete editando el valor de devolución en la propiedad de `GetNameOfImport`.  

      ```csharp  
      public override string GetNameOfImport(bool plural)  
      {  
      return "Package Short Name";  
      }  
      ```  

       Éste es el nombre del paquete que aparecerá en la página de selección del paquete en el asistente para el Package Deployer de Dynamics 365.  

   9. Cambie la descripción del paquete editando el valor de devolución en la propiedad de `GetImportPackageDescriptionText`.  

       ```csharp  

       public override string GetImportPackageDescriptionText  
       {  
       get { return "Package Description"; }  
       }  

       ```  

        Ésta es la descripción del paquete que aparecerá junto al nombre del paquete en la página de selección del paquete del asistente de Package Deployer.  

   10. Cambie el nombre largo del paquete editando el valor de devolución en la propiedad de `GetLongNameOfImport`.  

       ```csharp  

       public override string GetLongNameOfImport  
       {  
       get { return "Package Long Name"; }  
       }  

       ```  

        El nombre largo del paquete aparecerá en la página siguiente después de seleccionar el paquete para instalar.  

3. Además, la función y variables siguientes están disponibles para el paquete:  


   |Nombre|Tipo|Descripción|
   |--|--|--|
   |<xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.ImportExtension.CreateProgressItem(System.String)> |Función|Usado para crear un nuevo artículo del progreso en la interfaz de usuario. |
   |<xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.ImportExtension.RaiseUpdateEvent(System.String,Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.ProgressPanelItemStatus)> |Función| Usado para actualizar el progreso creado por la llamada a <xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.ImportExtension.CreateProgressItem(System.String)>.<br /><br /> <xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.ProgressPanelItemStatus> es una enumeración con los siguientes valores:<br /><br /> En curso = 0<br />Finalizado = 1<br />Error = 2<br />Advertencia = 3<br />Desconocido = 4 |
   |<xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.ImportExtension.RaiseFailEvent(System.String,System.Exception)>|Función|Usado para generar error en la importación de estado actual con un mensaje de la excepción.|
   |<xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.ImportExtension.IsRoleAssoicatedWithTeam(System.Guid,System.Guid)>|Función|Usado para determinar si un rol está asociado con un equipo especificado.|
   |<xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.ImportExtension.IsWorkflowActive(System.Guid)>|Función|Usado para determinar si un flujo de trabajo especificado está activo. |
   |<xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.ImportExtension.PackageLog>| Puntero de clases|Es un puntero a la interfaz de registro inicializada para el paquete. Esta interfaz la usa un paquete para registrar mensajes y excepciones al archivo de registro del paquete.|
   |<xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.ImportExtension.RootControlDispatcher>|Propiedad|Es una interfaz de distribuidor usada para permitirle que el control genere su propia interfaz de usuario durante la implementación del paquete. Use esta interfaz para envolver los elementos o comando de la interfaz de usuario. Es importante comprobar si en esta variable hay valores nulos antes de usarla, ya que podría o no establecerse como un valor.  |
   |<xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.ImportExtension.CrmSvc>|Propiedad |Esto es un puntero a la clase <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> que permite que un paquete direccione Dynamics 365 desde el paquete. Use esto para ejecutar métodos de SDK y otras acciones en los métodos sustituidos.|
   |<xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.IImportExtensions2.DataImportBypass> |Propiedad|Use esta opción para especificar si el Package Deployer de Dynamics 365 omite todas las operaciones de importación de datos, como importar datos de ejemplo de Common Data Service, datos de archivos sin formato y datos exportados desde la herramienta Migración de configuración. Especifique verdadero o falso. El valor predeterminado es `false`.|
   | <xref:Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.IImportExtensions2.OverrideDataImportSafetyChecks> |Propiedad|Use esta opción para especificar si el Package Deployer de Dynamics 365 omitirá algunas de las pruebas de seguridad, lo que ayuda a mejorar el rendimiento de la importación. Especifique `true` o `false`. El valor predeterminado es `false`.<br /><br /> Debe configurar esto como `true` solo si la instancia de Common Data Service de destino no contiene ningún dato.|


4. Guarde el proyecto, y luego genérelo (**Generar** > **Generar solución**) para crear el paquete. El paquete contiene los siguientes archivos en la carpeta *\<Proyecto>* \Bin\Debug  

   - **carpeta \<PackageName>**: el nombre de la carpeta es el mismo que cambió para el nombre de carpeta del paquete en el paso 2.g de esta sección (paso 5: Definir código personalizado para el paquete.) Esta carpeta contiene todas las soluciones, datos de configuración, archivos sin formato y contenido para el paquete.  

   - **\<PackageName>.dll**: el ensamblado contiene el código personalizado para el paquete. De forma predeterminada, el nombre del ensamblado es el mismo que el nombre del proyecto de Visual Studio.  

     El siguiente paso es implementar el paquete.  

<a name="UsethePackage"></a> 
  
## <a name="deploy-a-package"></a>Implementar un paquete  

 Después de crear un paquete, puede implementarlo en la instancia de Common Data Service mediante la herramienta Package Deployer o Windows PowerShell. 

 La herramienta Package Deployer se distribuye 3 como parte del paquete NuGet [Microsoft.CrmSdk.XrmTooling.PackageDeployment.WPF](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PackageDeployment). Para descargar la herramienta Package Deployer, vea [Descargar herramientas de NuGet](../download-tools-nuget.md).

 Para obtener información detallada, consulte [Implementar paquetes mediante el Package Deployer de Dynamics 365 o Windows PowerShell](/dynamics365/customer-engagement/admin/deploy-packages-using-package-deployer-windows-powershell).  

<a name="BestPractices"></a>   

## <a name="best-practices-for-creating-and-deploying-packages"></a>Prácticas recomendadas para crear e implementar paquetes  

Cuando crean los paquetes, los programadores deben asegurarse de que los ensamblados del paquete están firmados.  

Mientras se implementan los paquetes, los administradores de Common Data Service deben:  

- Insistir en un ensamblado de paquete firmado de modo que se pueda realizar el seguimiento de un ensamblado hasta su origen.  
- Comprobar el paquete en una instancia de preproducción (preferiblemente una imagen reflejada de la instancia de producción) antes de ejecutarlo en una instancia de producción.  
- Realizar una copia de seguridad de la instancia de producción antes de implementar el paquete.  



