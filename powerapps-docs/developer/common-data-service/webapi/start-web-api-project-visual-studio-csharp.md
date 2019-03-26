---
title: 'Iniciar un proyecto de API web de Common Data Service para aplicaciones en Visual Studio (C#) (Common Data Service para aplicaciones)| Microsoft Docs'
description: Crear un nuevo proyecto en Visual Studio para compilar una aplicación de consola que utilice la API web de Common Data Service para aplicaciones
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 08377156-32c7-492a-8e66-50a47a330dc6
caps.latest.revision: 14
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="start-a-common-data-service-for-apps-web-api-project-in-visual-studio-c"></a>Iniciar un proyecto de API web de Common Data Service para aplicaciones en Visual Studio (C#)

En este tema se muestra cómo crear un proyecto nuevo en Visual Studio que compile una aplicación de consola para usar la API web de Common Data Service para aplicaciones. Ilustra las referencias comunes y los recursos de proyecto que la mayoría de aplicaciones, incluidos los ejemplos de SDK C#, usan para implementar soluciones basadas en la API web.  
  
<a name="bkmk_prerequisites"></a> 
  
## <a name="prerequisites"></a>Requisitos previos  

 Los siguientes requisitos previos son necesarios para crear la aplicación de consola que se describe en esta sección.  
  
- Visual Studio 2015 instalado en el equipo de desarrollo. Cualquier edición, incluido [Visual Studio Express](https://www.visualstudio.com/products/visual-studio-express-vs.aspx), debería bastar para trabajar con la API web de Common Data Service para aplicaciones.
  
-   Un cliente NuGet debe instalarse: la utilidad de línea de comandos o la extensión de Visual Studio. Para obtener más información, consulte [Instalar NuGet](https://docs.nuget.org/consume/installing-nuget).  
  
-   Se requiere conexión con Internet para descargar el paquete NuGet que contiene la biblioteca de código auxiliar de la API web de Common Data Service para aplicaciones y otros paquetes dependientes.
  
<a name="bkmk_createProject"></a>
   
## <a name="create-a-project"></a>Crear un proyecto  

<!-- TODO: The following procedure demonstrates how to create a console application project in C# that uses the Microsoft .NET Framework. For more information on supported versions of the .NET Framework, see [Supported extensions](../supported-extensions.md).   -->
  
<a name="bkmk_newProject"></a>

### <a name="new-project"></a>Nuevo proyecto  
  
1.  En Visual Studio, haga clic en **Nuevo proyecto**. Se muestra el diálogo **Nuevo proyecto**.  
2.  En el panel de navegación de la izquierda, en **Plantillas**, seleccione **Visual C#**.  
3.  Encima de la lista de plantillas disponibles, seleccione **.NET Framework 4.6.2**.  
4.  En la lista de plantillas, seleccione **Aplicación de consola**. (Como alternativa seleccione el tipo de proyecto adecuado para la solución.) Todos los ejemplos en C# de la API web son aplicaciones de consola.  
  
 <!-- TODO:
 ![A new console app project dialog in CDS for Apps](../media/new-project.PNG "A new console app project dialog in CDS for Apps")   -->
  
5.  En los cuadros de texto que están cerca de la parte inferior del formulario, escriba el nombre y la ubicación del proyecto y, a continuación, seleccione Aceptar. (Para este tema, se usó el nombre de la solución `StartWebAPI-CS`.) Se generarán los archivos de solución iniciales y la solución se cargará en Visual Studio.  
  
6.  En el menú **Proyecto**, abra el formulario de propiedades del proyecto y compruebe que el marco de destino está establecido en **.NET Framework 4.6.2**.  
  
<a name="bkmk_addAllRequiredResources"></a>
   
### <a name="add-all-required-resources-to-your-project"></a>Agregar todos los recursos necesarios al proyecto  

Los siguientes procedimientos explican cómo agregar todas las referencias y paquetes administrados necesarios al proyecto. Considérelo como un conjunto de recursos básico que la mayoría de las aplicaciones de código administrado necesitarán para llamar a operaciones de la API web.  
  
#### <a name="add-the-helper-library-nuget-package"></a>Agregar el paquete NuGet de la biblioteca de código auxiliar

La biblioteca de código auxiliar de la API web de Common Data Service para aplicaciones contiene clases para facilitar operaciones complementarias, como configuración de aplicaciones, autenticación del servidor de Common Data Service para aplicaciones, control de excepciones, y comunicación web. Para obtener más información, consulte [Usar la biblioteca de código auxiliar de la API web de Common Data Service para aplicaciones (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md).  El uso de estas clases es opcional, aunque se usan extensamente en los ejemplos de la API web.  La biblioteca de código auxiliar de la API web de Common Data Service para aplicaciones se distribuye en forma de código origen como paquete NuGet.  Las actualizaciones futuras serán distribuidas como actualizaciones del paquete NuGet.  
  
 Si ha instalado la utilidad de línea de comandos de NuGet o usa la Consola de administrador de paquetes en Visual Studio:  
  
1.  Emita el siguiente comando para instalar el paquete de la biblioteca de código auxiliar.  
  
     `Install-Package Microsoft.CrmSdk.WebApi.Samples.HelperCode`  
  
2.  Se muestran varios mensajes sobre el procesamiento de paquetes de dependencia. Si se muestra el diálogo **Aceptación de licencia**, lea los términos de licencia y haga clic en **Acepto**.  
  
3.  Omita el paso 6 más abajo para confirmar la instalación del paquete de biblioteca de código auxiliar.  
  
 Si ha instalado la extensión del Administrador de paquetes de NuGet:  
  
1.  Del menú **Proyecto**, seleccione **Administrar paquetes de NuGet**.  Se muestra la pestaña **Administrador de paquetes de NuGet**.  
  
2.  En la esquina superior derecha, establezca el desplegable de origen **Paquete** como **Nuget.org**.  
  
3.  En la esquina superior izquierda, haga clic en **Examinar** y escriba "`CDS for Apps HelperCode`“ en el cuadro de búsqueda y presione Entrar.  
  
 <!-- TODO:
![NuGet Package Manager showing Common Data Service for Apps Helper Code Library &#40;C&#35;&#41;](../media/package-manifest-helper-code.png "NuGet Package Manager showing Common Data Service for Apps Helper Code Library (C#)")   -->
  
4.  Haga clic en **Instalar**.  Si se muestra el diálogo **Vista previa**, haga clic en **Aceptar**.  
  
5.  Se muestra el diálogo **Aceptación de licencia**. Consulte los términos de la licencia y haga clic en **Acepto**.  
  
6.  Navegue a la ventana **Explorador de soluciones**. Confirme que se agregó una nueva carpeta de la solución llamada **Web API Helper Code**.  
  
 <!-- TODO:
 ![VS Solution Explorer showing helper library files](../media/solution-explorer-helper-code.PNG "VS Solution Explorer showing helper library files")   -->
  
 El paquete de la biblioteca de código auxiliar de la API web del SDK de Common Data Service para aplicaciones, [Microsoft.CrmSdk.WebApi.Samples.HelperCode](https://www.nuget.org/packages/Microsoft.CrmSdk.WebApi.Samples.HelperCode), depende de los siguientes paquetes, que se descargan e instalan automáticamente junto al paquete de biblioteca de código auxiliar:  
  
-   [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json) – contiene [Json.NET](http://www.newtonsoft.com/json), un popular marco de trabajo JSON con licencia MIT para .NET.  
  
-   [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) – contiene los archivos binarios de la biblioteca de autenticación de Active Directory ([ADAL](https://msdn.microsoft.com/library/azure/mt417579.aspx)), que proporciona la funcionalidad de autenticación para clientes de .NET.  
  
> [!WARNING]
>  El paquete de la biblioteca de código auxiliar de la API web del SDK de Common Data Service para aplicaciones se creó con versiones específicas de estos otros dos paquetes de apoyo.  Por este motivo, solo debe actualizar directamente el paquete NuGet de biblioteca de código auxiliar.  Esta operación actualizará los paquetes de apoyo adecuados si es necesario.  Si actualiza por separado uno de estos paquetes de apoyo, una versión más reciente de ese paquete puede ser incompatible con la biblioteca de código auxiliar.  
  
#### <a name="verify-the-required-assembly-references"></a>Compruebe las referencias de ensamblado necesarias  
  
1.  En **Explorador de soluciones**, expanda el nodo **Referencias**.  
  
2.  Confirme que las referencias siguientes se han agregado al proyecto.  
  
 <!-- TODO:
![VS Solution Explorer showing references for the helper library](../media/solution-explorer-references-helper-code.png "VS Solution Explorer showing references for the helper library")   -->
  
3.  Si tiene funcionalidad adicional que usa rutinariamente en sus aplicaciones, ahora puede agregar las referencias asociadas a los ensamblados necesarios. Para obtener más información, consulte [Cómo: Agregar o eliminar referencias mediante el cuadro de diálogo Agregar referencia](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).  
  
 Puesto que la API web de Common Data Service para aplicaciones se basa en principios REST, no requiere ensamblados del lado del cliente para tener acceso. 
  
#### <a name="add-typical-using-statements"></a>Agregar instrucciones using típicas  
  
1.  En **Explorador de soluciones**, abra **Program.cs** para editar.  
  
2.  En la parte superior del archivo, agregue las siguientes instrucciones `using`, que hacen referencia a espacios de nombre de referencia de uso general en soluciones basadas en la API web de Common Data Service para aplicaciones.  
  
    ```csharp
    using Microsoft.Crm.Sdk.Samples.HelperCode;  
    using Newtonsoft.Json;  
    using Newtonsoft.Json.Linq;  
    using System.Net.Http;  
    using System.Net.Http.Headers;
    ```  
  
3.  Si ha agregado rutinariamente ensamblados o referencias en las secciones anteriores, es posible que también desee agregar las instrucciones `using` correspondientes para estos recursos.  
  
4.  Guarde el archivo.  
  
<a name="bkmk_addConnectionCode"></a>
 
### <a name="add-connection-code"></a>Agregar código de conexión

Esta sección explica cómo agregar un conjunto básico de valores y de instrucciones para realizar estas operaciones.  Para obtener más información sobre el código común usado, consulte [Usar la biblioteca de código auxiliar de la API web de Common Data Service para aplicaciones (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md).  
  
#### <a name="edit-the-application-configuration-file"></a>Editar el archivo de configuración de aplicación
  
1.  En **Explorador de soluciones**, abra el archivo **App.config** para editar.  Agréguele las dos secciones siguientes, después de la sección `<startup>` existente y luego guarde el archivo.  
  
    ```xml  
  
    <connectionStrings>  
        <clear />  
  
        <!-- When providing a password, make sure to set the app.config file's security so that only you can read it. -->  
        <add name="default"   connectionString="Url=http://myserver/myorg/; Username=name; Password=password; Domain=domain" />  
        <add name="CrmOnline" connectionString="Url=https://mydomain.crm.dynamics.com/; Username=someone@mydomain.onmicrosoft.com; Password=password" />  
      </connectionStrings>  
  
      <appSettings>  
        <!--For information on how to register an app and obtain the ClientId and RedirectUrl  
            values see https://msdn.microsoft.com/dynamics/crm/mt149065 -->  
        <!--Active Directory application registration. -->  
        <!--These are dummy values and should be replaced with your actual app registration values.-->  
        <add key="ClientId" value="e5cf0024-a66a-4f16-85ce-99ba97a24bb2" />  
        <add key="RedirectUrl" value="http://localhost/SdkSample" />  
  
        <!-- Use an alternate configuration file for connection string and setting values. This optional setting  
        enables use of an app.config file shared among multiple applications. If the specified file does  
        not exist, this setting is ignored.-->  
        <add key="AlternateConfig" value="C:\Temp\crmsample.exe.config"/>  
      </appSettings>  
  
    ```  
  
2.  Cuando desarrolle o implemente una solución, la conexión real y los valores de registro de la aplicación deben ser sustituidos para los valores de marcador de ejemplo.  Para obtener más información, consulte [Código auxiliar: clases de configuración](web-api-helper-code-configuration-classes.md).  
  
<a name="bkmk_addCodeToCallHelperLibrary"></a>

#### <a name="add-code-to-call-the-helper-library"></a>Agregue código para llamar a la biblioteca de código auxiliar
  
1.  Edite el archivo Program.cs.  
  
2.  Agregue la siguiente propiedad a la clase de programa.  Esta propiedad será inicializada después de una conexión correcta un servidor de Common Data Service para aplicaciones.  
  
     `private HttpClient httpClient;`  
  
3.  En el método `Main`, agregue las siguientes instrucciones.  
  
    ```csharp  
  
    Program app = new Program();  
    try  
    {  
        String[] arguments = Environment.GetCommandLineArgs();  
        app.ConnectToCRM(arguments);  
    }  
    catch (System.Exception ex)  
    { ; }  
    finally  
    {  
        if (app.httpClient != null)  
        { app.httpClient.Dispose(); }  
    }  
  
    ```  
  
4.  A continuación agregue el método `ConnectToCRM`, que usa las clases `Configuration` y `Authentication` de la biblioteca de código auxiliar.  El siguiente código muestra la asignación de valores a las propiedades [HttpClient](https://msdn.microsoft.com/library/system.net.http.httpclient\(v=vs.118\).aspx) de modo que puede tener acceso correctamente a la versión de la API web de Common Data Service para aplicaciones .  
  
    ```csharp  
  
    private void ConnectToCRM(String[] cmdargs)  
    {  
        Configuration config = null;  
        if (cmdargs.Length > 0)  
            config = new FileConfiguration(cmdargs[0]);  
        else  
            config = new FileConfiguration(null);  
        Authentication auth = new Authentication(config);  
        httpClient = new HttpClient(auth.ClientHandler, true);  
        httpClient.BaseAddress = new Uri(config.ServiceUrl + "api/data/v8.1/");  
        httpClient.Timeout = new TimeSpan(0, 2, 0);  
        httpClient.DefaultRequestHeaders.Add("OData-MaxVersion", "4.0");  
        httpClient.DefaultRequestHeaders.Add("OData-Version", "4.0");  
        httpClient.DefaultRequestHeaders.Accept.Add(  
            new MediaTypeWithQualityHeaderValue("application/json"));  
    }  
  
    ```  
  
<a name="bkmk_addErrorHandlingCode"></a>

### <a name="add-error-handling-code"></a>Agregar código de control de errores

 Los siguientes cambios agregan código para recoger e informar de excepciones, incluidos los errores de la API web, a la consola.  Si el objetivo es otro entorno, modifique el código de control de excepciones adecuadamente para ese entorno.  
  
1.  En `Main`, agregue la siguiente instrucción al bloque `catch`.  
  
     `DisplayException(ex);`  
  
2.  Agregue el método correspondiente a la clase `Program`.  
  
    ```csharp  
  
    private static void DisplayException(Exception ex)  
    {  
        Console.WriteLine("The application terminated with an error.");  
        Console.WriteLine(ex.Message);  
        while (ex.InnerException != null)  
        {  
            Console.WriteLine("\t* {0}", ex.InnerException.Message);  
            ex = ex.InnerException;  
        }  
    }  
  
    ```  
  
3.  Guarde todos los archivos en la solución.  
  
<a name="bkmk_nextSteps"></a>

### <a name="next-steps"></a>Pasos siguientes

 En este punto la solución se puede generar sin errores.  Si edita el archivo de configuración de aplicación para proporcionar valores para el Common Data Service para aplicaciones, el programa también debe conectarse correctamente a ese servidor.  La solución representa un armazón esquelético que está listo para aceptar código personalizado, incluidas llamadas a la API web de Common Data Service para aplicaciones.  
  
> [!TIP]
>  Antes de salir de este tema, considere guardar el proyecto como una plantilla del proyecto. A continuación, puede volver a usar esa plantilla para futuros proyectos de aprendizaje y ahorrarse tiempo y esfuerzos para configurar nuevos proyectos. Para ello, mientras el proyecto está abierto en Microsoft Visual Studio, en el menú **Archivo**, seleccione **Exportar plantilla**. Siga las instrucciones del [Asistente para exportar plantilla](https://msdn.microsoft.com/library/xkh1wxd8.aspx) para crear la plantilla.  
  
### <a name="see-also"></a>Vea también

[Introducción a la API web (C#)](get-started-dynamics-365-web-api-csharp.md)<br />
[Usar la biblioteca de código auxiliar de la API web de Common Data Service para aplicaciones (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md).<br />  
[Realizar operaciones mediante la API web](perform-operations-web-api.md)
