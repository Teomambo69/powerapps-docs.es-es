---
title: 'Iniciar un proyecto de la API web de Common Data Service en Visual Studio (C#) (Common Data Service)| MicrosoftDocs'
description: Crear un nuevo proyecto en Visual Studio para crear una aplicación de consola que use la API web de Common Data Service
ms.custom: null
ms.date: 04/22/2019
ms.reviewer: null
ms.service: powerapps
ms.suite: null
ms.tgt_pltfrm: null
ms.topic: get-started-article
ms.assetid: F96B384D-EF70-490D-BE3D-2E3883278B99
caps.latest.revision: 14
author: JimDaly
ms.author: jdaly
manager: annbe
search.audienceType:
  - developer
search.app:
  - D365CE
---
# <a name="start-a-common-data-service-web-api-project-in-visual-studio-c"></a>Iniciar un proyecto de la API web de Common Data Service en Visual Studio (C#)

En este tema se muestra cómo crear un proyecto nuevo en Visual Studio 2017 que crea una aplicación de consola que usa la API web de Common Data Service. Ilustra las referencias comunes y los recursos de proyecto que la mayoría de aplicaciones, incluidos los ejemplos de SDK C#, usan para implementar soluciones basadas en la API web.  
  
<a name="bkmk_prerequisites"></a>   
## <a name="prerequisites"></a>Requisitos previos  
 Los siguientes requisitos previos son necesarios para crear la aplicación de consola que se describe en esta sección.  
  
- Visual Studio 2017 instalado en el equipo de desarrollo. Cualquier edición, incluido [Visual Studio Express](https://www.visualstudio.com/products/visual-studio-express-vs.aspx), debería bastar para trabajar con la API web de Common Data Service.
  
- Un cliente de NuGet debe instalarse: la utilidad de línea de comandos o la extensión de Visual Studio. Para obtener más información, vea el tema [Instalar NuGet](https://docs.nuget.org/consume/installing-nuget).  
  
<a name="bkmk_createProject"></a>   

## <a name="create-a-project"></a>Crear un proyecto  
En el siguiente procedimiento se muestra cómo crear un proyecto de aplicación de consola en C# que usa Microsoft .NET Framework.
  
<a name="bkmk_newProject"></a> 

### <a name="new-project"></a>Nuevo proyecto  
  
1. En Visual Studio, haga clic en **Nuevo proyecto**. Se muestra el diálogo **Nuevo proyecto**.  
  
2. En el panel de navegación de la izquierda, en **Plantillas**, seleccione **Visual C#**.  
  
3. Encima de la lista de plantillas disponibles, seleccione **.NET Framework 4.6.2**.  
  
4. En la lista de plantillas, seleccione **Aplicación de consola (.NET Framework)**. (Como alternativa seleccione el tipo de proyecto adecuado para la solución.) Todos los ejemplos en C# de la API web son aplicaciones de consola.  
  
   ![Un nuevo diálogo de proyecto de aplicación de consola en Common Data Service](media/new-project.PNG "Un nuevo diálogo de proyecto de aplicación de consola en Common Data Service")  
  
5. En los cuadros de texto que están cerca de la parte inferior del formulario, escriba el nombre y la ubicación del proyecto y, a continuación, seleccione Aceptar. (Para este tema, se usó el nombre de la solución “StartWebAPI-CS”.) Se generarán los archivos de solución iniciales y la solución se cargará en Visual Studio.  
  
6. En el menú **Proyecto**, abra el formulario de propiedades del proyecto y compruebe que el marco de destino está establecido en **.NET Framework 4.6.2**.  
  
#### <a name="install-and-verify-the-required-assembly-references"></a>Instale y compruebe las referencias de ensamblado necesarias  

1. Cuando se abra el proyecto, haga clic en **Herramientas** en la barra de control en la parte superior del proyecto. Seleccione **Administrador de paquetes de NuGet** > **Consola del administrador de paquetes** e instale los siguientes paquetes de NuGet.

```
install-package Newtonsoft.Json
install-package System.Net.Http
```
2. En **Explorador de soluciones**, expanda el nodo **Referencias**.  
  
3. Confirme que todas las referencias requeridas se han agregado al proyecto.  
  
4. Si tiene funcionalidad adicional que usa rutinariamente en sus aplicaciones, ahora puede agregar las referencias asociadas a los ensamblados necesarios. Para obtener más información, consulte [Cómo: Agregar o eliminar referencias mediante el cuadro de diálogo Agregar referencia](https://msdn.microsoft.com/library/wkze6zky.aspx).  
  
   Puesto que la API web de Common Data Service se basa en principios REST, no requiere ensamblados del lado del cliente para tener acceso.  Sin embargo, otras API compatibles con aplicaciones de Common Data Service los requieren.
  
#### <a name="add-typical-using-statements"></a>Agregar instrucciones using típicas  
  
1.  En **Explorador de soluciones**, abra **Program.cs** para editar.  
  
2.  En la parte superior del archivo, agregue las siguientes instrucciones `using`, que hacen referencia a espacios de nombre de referencia de uso general en soluciones basadas en la API web de Common Data Service.  
  
    ```csharp
    using Newtonsoft.Json;  
    using Newtonsoft.Json.Linq;  
    using System.Net.Http;  
    using System.Net.Http.Headers;
    ```  
  
3.  Si ha agregado rutinariamente ensamblados o referencias en las secciones anteriores, es posible que también desee agregar las instrucciones `using` correspondientes para estos recursos.  
  
4.  Guarde el archivo.  
  
<a name="bkmk_addConnectionCode"></a>
 
### <a name="add-connection-code"></a>Agregar código de conexión

Esta sección explica cómo agregar un conjunto básico de valores y de instrucciones para realizar estas operaciones.  
  
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
  
2.  Cuando desarrolle o implemente una solución, la conexión real y los valores de registro de la aplicación deben ser sustituidos para los valores de marcador de ejemplo.  
  
### <a name="next-steps"></a>Pasos siguientes

 En este punto la solución se puede generar sin errores. Si edita el archivo de configuración de aplicación para proporcionar valores para el Dynamics 365 Server, el programa también debe conectarse correctamente a ese servidor. La solución representa un armazón esquelético que está listo para aceptar código personalizado, incluidas llamadas a la API web de Common Data Service.  
  
> [!TIP]
>  Antes de salir de este tema, considere guardar el proyecto como una plantilla del proyecto. A continuación, puede volver a usar esa plantilla para futuros proyectos de aprendizaje y ahorrarse tiempo y esfuerzos para configurar nuevos proyectos. Para ello, mientras el proyecto está abierto en Microsoft Visual Studio, en el menú **Archivo**, seleccione **Exportar plantilla**. Siga las instrucciones del [Asistente para exportar plantilla](https://msdn.microsoft.com/library/xkh1wxd8.aspx) para crear la plantilla.  
  
### <a name="see-also"></a>Vea también

 [Introducción a la API web de (C#)](get-started-dynamics-365-web-api-csharp.md)   
 [Use la biblioteca de código auxiliar de la API web (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md)   
 [Realizar operaciones mediante la API web](perform-operations-web-api.md)