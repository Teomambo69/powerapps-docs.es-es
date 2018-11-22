La herramienta Package Deployer está disponible en forma de [paquete NuGet](https://go.microsoft.com/fwlink/?linkid=859205). Para usarla, debe descargarla y extraerla en su equipo local usando **nuget.exe**.<br/><br/>

Descargue **nuget.exe** de <https://www.nuget.org/downloads> y guárdelo en su equipo; por ejemplo, en **d:\\**. A continuación, ejecute el siguiente comando en el símbolo del sistema para extraer el contenido del paquete en una carpeta (por ejemplo, **PD**) del equipo:<br/>

`d:\nuget install Microsoft.CrmSdk.XrmTooling.PackageDeployment.Wpf -Version [VERSION] -O d:\PD`<br/><br/>
    
Cuando haya extraído los archivos de la herramienta Package Deployer, vaya a la carpeta `[ExtractedLocation]\tools` para buscar el archivo **PackageDeployer.exe**. 
