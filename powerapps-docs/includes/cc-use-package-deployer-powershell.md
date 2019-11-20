Los archivos de PowerShell para la herramienta Package Deployer están disponibles en forma de paquete [NuGet](https://go.microsoft.com/fwlink/?linkid=859211). Para usarlos, debe descargarlos y extraerlos en su equipo local mediante **nuget.exe**.<br/><br/>

Descargue **nuget.exe** de <https://www.nuget.org/downloads> y guárdelo en su equipo; por ejemplo, en **d:\\**. A continuación, ejecute el siguiente comando en el símbolo del sistema para extraer el contenido del paquete en una carpeta (por ejemplo, **PD-PowerShell**) del equipo:<br/>

`d:\nuget install Microsoft.CrmSdk.XrmTooling.PackageDeployment.PowerShell -Version [VERSION] -O d:\PD-PowerShell`<br/><br/>
    
Cuando haya extraído los archivos de PowerShell para la herramienta Package Deployer, vaya a la carpeta `[ExtractedLocation]\tools` para buscar los archivos necesarios. 
