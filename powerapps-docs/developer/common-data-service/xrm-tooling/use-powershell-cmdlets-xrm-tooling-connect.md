---
title: Usar cmdlets PowerShell para útiles de XRM para conectarse a Common Data Service (Common Data Service)| Microsoft Docs
description: 'Descubra cómo utilizar cmdlets de Powershell para que los útiles de XRM, como Get-CrmConnection y Get-CrmOrganizations, se conecten a Common Data Service y recuperen organizaciones a las que el usuario actual tiene acceso'
ms.custom: ''
ms.date: 03/27/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 81816457-c963-46ca-b350-615fa75f56a7
caps.latest.revision: 27
author: MattB-msft
ms.author: nabuthuk
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-powershell-cmdlets-for-xrm-tooling-to-connect-to-common-data-service"></a>Usar cmdlets PowerShell para útiles de XRM para conectarse a Common Data Service

Los útiles de XRM le proporcionan los siguientes cmdlets de **Windows PowerShell** que puede utilizar para conectarse a Common Data Service y recuperar las organizaciones a las que el usuario actual tiene acceso: `Get-CrmConnection` y `Get-CrmOrganizations`.  

> [!NOTE]
> [!INCLUDE[cc-d365ce-note-topic](../includes/cc-d365ce-note-topic.md)] [Usar cmdlets de PowerShell para útiles de XRM para conectarse a Customer Engagement](/dynamics365/customer-engagement/developer/xrm-tooling/use-powershell-cmdlets-xrm-tooling-connect)
  
<a name="Prereq"></a>   

## <a name="prerequisites"></a>Requisitos previos  
  
-  Para usar los cmdlets de los útiles de XRM, necesita la versión 3.0 de **PowerShell** o posterior. Para comprobar la versión, abra una ventana de **PowerShell** y ejecute el siguiente comando: `$Host`  
  
-  Establezca la directiva de ejecución para ejecutar los scripts de **PowerShell** firmados. Para ello, abra una ventana de **PowerShell** como **administrador** y ejecute el siguiente comando: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned`  
  
<a name="register"></a>   

## <a name="register-the-cmdlets"></a>Registro de los cmdlets  

 Antes de usar los cmdlets de **PowerShell** debe registrarlos. Los cmdlets de **PowerShell** de útiles de XRM están disponibles como paquete de NuGet [aquí:](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.CrmConnector.PowerShell). Para descargar y registrar los cmdlets
  
1. Abrir el bloc de notas y copiar el siguiente script

    ```powershell
    @PowerShell.exe -ExecutionPolicy RemoteSigned -Command "Invoke-Expression -Command ((Get-Content -Path '%~f0' | Select-Object -Skip 2) -join [environment]::NewLine)"
    @exit /b %Errorlevel%
    $currentFolder = Get-Location
    cd $currentFolder
    $sourceNugetExe = "https://dist.nuget.org/win-x86-commandline/latest/nuget.exe"
    $targetNugetExe = ".\nuget.exe"
    Remove-Item .\Tools -Force -Recurse -ErrorAction Ignore
    Invoke-WebRequest $sourceNugetExe -OutFile $targetNugetExe
    Set-Alias nuget $targetNugetExe -Scope Global -Verbose

    ##
    ##Specify the NuGet package source
    ##
    $nugetPackageSource = "https://api.nuget.org/v3/index.json"

    ##
    ##Download XRM Tooling PowerShell cmdlets
    ##
    ./nuget install -source $nugetPackageSource Microsoft.CrmSdk.XrmTooling.CrmConnector.PowerShell -O .\Tools
    md .\Tools\XRMToolingPowerShell
    $cmdletFolder = Get-ChildItem ./Tools | Where-Object {$_.Name -match 'Microsoft.CrmSdk.XrmTooling.CrmConnector.PowerShell.'}
    move .\Tools\$cmdletFolder\tools\*.* .\Tools\XRMToolingPowerShell
    Remove-Item .\Tools\$cmdletFolder -Force -Recurse

    ##
    ##Remove NuGet.exe
    ##
    Remove-Item nuget.exe
  
1. Save the notepad file as batch file on your computer: **GetTools.bat**.
1. Navigate to the folder where you saved the file, for example `C:\SDK`, and double-click the **GetTools.bat** file to run the script. This will create a `Tools\XRMToolingPowerShell` folder in the same location as your **GetTools.bat** file. The `Tools\XRMToolingPowerShell` folder contains the `RegisterXRMTooling.ps1` script to register the cmdlets, and other associated files.
1. Start **PowerShell** on your computer with elevated privileges (run as administrator).  
  
1. At the prompt, change your directory to the folder that contains the **PowerShell** script for registering the cmdlets. For example,  
  
    ```powershell  
    cd c:\SDK\Tools\XRMToolingPowerShell  
    ```  
  
1. Ejecutar el script `RegisterXRMTooling.ps1` para registrar los cmdlets de **PowerShell** de útiles de XRM. Escriba el siguiente comando y presione **ENTRAR**  
  
    ```powershell
    .\RegisterXRMTooling.ps1  
    ```
  
 Ahora está listo para usar estos cmdlets de **PowerShell**. Para mostrar los cmdlets que registró, ejecute el comando siguiente en la ventana de PowerShell  
  
```powershell
Get-Help “Crm”  
```  
  
<a name="RetrieveOrgs"></a>   

## <a name="use-the-cmdlet-to-retrieve-organizations-from-common-data-service"></a>Uso del cmdlet para recuperar organizaciones de Common Data Service  

Use el cmdlet `Get-CrmOrganizations` para recuperar las organizaciones a las que tiene acceso.  
  

1.  Especifique las credenciales para conectarse a la instancia de Common Data Service y haga clic en Iniciar sesión. Si ejecuta el siguiente comando se le pedirá que escriba su nombre de usuario y contraseña para conectarse a la instancia de Common Data Service y se almacenará en la variable `$Cred`.  

  
    ```powershell  
    $Cred = Get-Credential  
    ```  
2. Use el siguiente comando para recuperar sus organizaciones y almacenar la información en la variable `$CRMOrgs`

    - Si se va a conectar a una instancia de Common Data Service:  
  
        ```powershell  
        $CRMOrgs = Get-CrmOrganizations -Credential $Cred -DeploymentRegion NorthAmerica –OnlineType Office365  
        ```  
  
        > [!NOTE]
        > Los valores válidos del parámetro `DeploymentRegion` son: `NorthAmerica`, `EMEA`, `APAC`, `SouthAmerica`, `Oceania`, `JPN`, `CAN`, `IND` y `NorthAmerica2`. Para el parámetro `OnlineType`, especifique `Office365`.
  
  
3.  Sus credenciales suministradas se validan al ejecutar el comando en el paso 2. Tras la ejecución correcta del comando, escriba el siguiente comando, y presione ENTRAR para mostrar las organizaciones a las que tiene acceso:  
  
      ```powershell  
      $CRMOrgs  
      ```  
      > [!div class="mx-imgBorder"]
      > ![Información de la organización de Common Data Service](../media/xrmtooling-powershell-1.png "Common Data Service")
  

> [!TIP]
> Puede usar la variable que se usó para almacenar las organizaciones de Common Data Service recuperadas (en este caso, `$CRMOrgs`) con el cmdlet `Get-CrmConnection` para conectarse a Common Data Service. Para especificar el nombre de la organización, utilice el siguiente comando: `$CRMOrgs.UniqueName`.  
>   
> Si hay más de un valor de organización almacenado en la variable `$CRMOrgs`, puede referirse a la organización `nth` con el siguiente comando: `$CRMOrgs[n-1]`. Por ejemplo, para referirse al nombre único de la segunda organización de la variable `$CRMOrgs`, use el siguiente comando: `$CRMOrgs[1].UniqueName`.
  
<a name="ConnecttoCRM"></a>
   
## <a name="use-the-cmdlet-to-connect-to-common-data-service"></a>Uso del cmdlet para conectarse a Common Data Service  

Usar cmdlet `Get-CrmConnection` para conectarse a una instancia de Common Data Service El cmdlet le permite usar el control común de inicio de sesión de los útiles de XRM para especificar sus credenciales y conectarse a Common Data Service o especificar sus credenciales como parámetros en línea. Más información: [Usar el control de inicio de sesión común de los útiles de XRM](use-xrm-tooling-common-login-control-client-applications.md)

> [!IMPORTANT]
> Antes de usar el cmdlet `Get-CrmConnection`, asegúrese de que usa el siguiente comando de aplicar el uso de TLS 1.2 por PowerShell para conectarse a la instancia de Common Data Service<br/>
> `[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.SecurityProtocolType]::Tls12`<br/>
> Más información acerca de los requisitos de TLS 1.2 para conexión de Common Data Service [Entrada de blog: Próximas actualizaciones de seguridad de conexión de Common Data Service](https://blogs.msdn.microsoft.com/crm/2017/09/28/updates-coming-to-dynamics-365-customer-engagement-connection-security/)   
  
### <a name="connect-to-common-data-service-by-using-the-common-login-control"></a>Conexión a Common Data Service mediante el control de inicio de sesión común  
  
1.  Si desea usar el control de inicio de sesión común para proporcionar sus credenciales para conectarse a Common Data Service, use el siguiente comando. La información de conexión se almacena en la variable `$CRMConn` para poder usarla más adelante.  
  
    ```powershell  
    $CRMConn = Get-CrmConnection -InteractiveMode  
    ```  
  
2. Se abre el cuadro de diálogo **LoginControl**. Especifique las credenciales para conectarse a la instancia de Common Data Service y haga clic en **Iniciar sesión**.    
  
### <a name="connect-to-common-data-service-by-specifying-credentials-inline"></a>Conectarse a Common Data Service especificando credenciales en línea  
  
1.  Para conectarse a Common Data Service, utilice los comandos siguientes. Tenga en cuenta que estos comandos usan la variable `$Cred` que se creó anteriormente para almacenar las credenciales mientras se recuperaban las organizaciones. La información de conexión se guarda en la variable `$CRMConn`:

     - Si se va a conectar a una instancia de Common Data Service

        ```powershell  
        $CRMConn = Get-CrmConnection -Credential $Cred -DeploymentRegion <Deployment region name> –OnlineType Office365 –OrganizationName <OrgName>  
        ```
        > [!NOTE]
        > Los valores válidos para el parámetro `DeploymentRegion` son: `NorthAmerica`, `EMEA`, `APAC`, `SouthAmerica`, `Oceania`, `JPN`, `CAN`, `IND` y `NorthAmerica2`. Para el parámetro `OnlineType`, especifique `Office365`. 
  
        > [!NOTE]
        > Para el parámetro `OrganizationName` de todos los comandos anteriores, puede especificar el nombre único o el nombre descriptivo de la organización. También puede usar el nombre único o el nombre descriptivo de la organización que recuperó mediante el cmdlet `Get-CrmOrganizations` y que almacenó en la variable `$CRMOrgs`. Por ejemplo, puede usar `$CRMOrgs[x].UniqueName` o `$CRMOrgs[x].FriendlyName`.  
  
2.  Sus credenciales suministradas se validan al ejecutar el comando en el paso 1. Tras la ejecución correcta del cmdlet, escriba el siguiente comando, y presione ENTRAR para mostrar la información y el estado de conexión:  

      ```powershell  
       $CRMConn  
       ```  

       > [!div class="mx-imgBorder"]
       > ![Información y estado de conexión de Common Data Service](../media/xrm-tooling-powershell-2.png "Información y estado de conexión de Common Data Service") 

  
### <a name="see-also"></a>Vea también
  
[Uso de la API de útiles XRM para conectarse a Common Data Service](use-crmserviceclient-constructors-connect.md)<br />
[Crear aplicaciones cliente de Windows mediante las herramientas XRM](build-windows-client-applications-xrm-tools.md)<br />
[Blog: Módulo de PowerShell para realizar operaciones de datos y manipular la configuración de usuarios y del sistema en Common Data Service](http://blogs.msdn.com/b/crm/archive/2015/09/25/powershell-module-for-performing-data-operations-and-manipulating-user-and-system-settings-in-crm.aspx)
