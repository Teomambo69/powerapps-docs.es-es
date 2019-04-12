---
title: Generar clases de enlace en tiempo de compilación con el servicio de la organización (Common Data Service) | Microsoft Docs
description: CrmSvcUtil.exe es una herramienta de generación de código de línea de comandos para su uso con Common Data Service. Esta herramienta genera clases de enlace en tiempo de compilación de .NET Framework que representan el modelo de datos de la entidad usado por Common Data Service.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="generate-early-bound-classes-for-the-organization-service"></a>Generar clases de enlace en tiempo de compilación para el servicio de la organización

**CrmSvcUtil.exe** es una herramienta de generación de código de línea de comandos para su uso con Common Data Service. Esta herramienta genera clases de enlace en tiempo de compilación de .NET Framework que representan el modelo de datos de la entidad usado por Common Data Service. La herramienta de generación de código (CrmSvcUtil.exe) se distribuye como parte del paquete de NuGet [Microsoft.CrmSdk.CoreTools](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreTools). 

> [!NOTE]
> Para obtener información sobre cómo descargar la herramienta de generación de código (CrmSvcUtil.exe), consulte [Descargar herramientas de NuGet](../download-tools-NuGet.md).

## <a name="generate-entity-classes"></a>Generar clases de entidad

La herramienta **CrmSvcUtil.exe** crea un archivo de salida de Microsoft Visual C# o Visual Basic .NET que contiene las clases con establecimiento inflexible de tipos para las entidades en su organización. Esto incluye las entidades y los atributos personalizados. Este archivo de salida contiene una clase para cada entidad, y brinda enlace en tiempo de compilación y soporte de IntelliSense en Visual Studio para ayudarlo a medida que escribe el código. Las clases generadas son las clases parciales que pueden ampliarse con lógica empresarial personalizada en archivos separados. También puede crear extensiones para esta herramienta. Para obtener más información, consulte [Crear extensiones para la herramienta de generación de código](extend-code-generation-tool.md).  

## <a name="generate-an-organizationservicecontext-class"></a>Generar una clase OrganizationServiceContext

La herramienta también se puede usar para generar una clase derivada de clases de <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext> que actúa como un contenedor de entidad en el modelo de datos de la entidad. Este contexto de servicio proporciona las instalaciones para realizar el seguimiento de los cambios y la administración de identidades, simultaneidad, y relaciones. Esta clase también expone un método de <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges> que permite escribir insertos, actualizar y eliminar registros en Common Data Service. Para obtener más información, consulte [Usar OrganizationServiceContext](organizationservicecontext.md).  

## <a name="use-generated-classes"></a>Use clases generadas

Las clases creadas por la herramienta de generación de códigos están diseñadas para integrarse a una biblioteca de clases referenciada por los proyectos que usan Common Data Service. Luego de haber generado el archivo de clase mediante la herramienta, debería agregar el archivo al proyecto de Visual Studio. También deberá agregar referencias a varios ensamblados de los que dependen las clases generadas.  

A continuación se enumeran los ensamblados a los que se debe hacer referencia en el proyecto cuando se usa el archivo de código generado.  

- `Microsoft.Crm.Sdk.Proxy.dll`  
- `Microsoft.Xrm.Sdk.dll ` 

Estos ensamblados forman parte de [Microsoft.CrmSdk.CoreAssemblies](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreAssemblies/). Use los paquetes de este Nuget para agregar estos ensamblados al proyecto de Visual Studio.

<a name="bkmk_RuntheCodeGenerationUtility"></a>

## <a name="run-the-code-generation-tool"></a>Ejecutar la herramienta de generación de código

La herramienta de generación de código toma varios parámetros que determinan los contenidos del archivo que se va a crear. Los parámetros se pueden efectuar desde la línea de comandos al ejecutar la herramienta o en un archivo de configuración de la aplicación conectado a .NET. 

Ejecute la herramienta `CrmSvcUtil.exe` desde la carpeta `Tools\CoreTools` creada cuando descargue las herramientas mediante el script descrito en [Herramientas de descargue de NuGet](../download-tools-NuGet.md). Si ejecuta la herramienta desde otra ubicación de la carpeta, asegúrese de que una copia del ensamblado `Microsoft.Xrm.Sdk.dll` se encuentre en la misma carpeta.  

El siguiente ejemplo muestra el formato para ejecutar la herramienta desde la línea de comandos con Common Data Service. Para usar el inicio de sesión interactivo, puede proporcionar simplemente estas opciones:

```ms-dos
CrmSvcUtil.exe /interactivelogin ^
/out:<outputFilename>.cs ^
/namespace:<outputNamespace> ^
/serviceContextName:<serviceContextName> ^
/generateActions
```

Al ejecutar la herramienta con la opción `interactivelogin` (de acceso directo `il`), se abrirá un cuadró de diálogo y podrá especificar sus credenciales de inicio de sesión y el servidor al que desea conectarse.

También puede especificar los parámetros que desea transmitir directamente a la línea de comandos o mediante un archivo por lotes (.bat) puede ejecutar para generar nuevas clases.

```ms-dos
CrmSvcUtil.exe ^
/url:https://<organizationUrlName>.api.crm.dynamics.com/XRMServices/2011/Organization.svc ^
/out:<outputFilename>.cs ^
/username:<username> ^
/password:<password> ^
/namespace:<outputNamespace> ^
/serviceContextName:<serviceContextName>
```
Por ejemplo:

```ms-dos
CrmSvcUtil.exe ^
/url:https://myorganization.api.crm.dynamics.com/XRMServices/2011/Organization.svc ^
/out:MyOrganizationSdkTypes.cs ^
/username:you@yourOrg.onmicrosoft.com ^
/password:myp455w0rd ^
/namespace:MyOrg ^
/serviceContextName:MyContext
```


> [!NOTE]
> Los ejemplos anteriores usan el carácter (`^`) para desglosar la lista de parámetros para mejorar la legibilidad. Puede crear los parámetros de comando con argumentos mediante el bloc de notas y después pegándolos en la línea de comandos.

- Para los parámetros `username` y `password`, escriba el nombre de usuario y la contraseña que se usan para iniciar sesión a Common Data Service. 
- Para el parámetro de `url`, puede buscar la dirección URL correcta en la aplicación web al seleccionar **Configuración**. A continuación, desplácese hasta **Personalizaciones** y luego seleccione **Recursos de desarrollador**. La URL se muestra en **Servicio de organización**.  

Para enumerar los parámetros de línea de comandos admitidos, use el siguiente comando.

```ms-dos
CrmSvcUtil.exe /?  
```

<a name="bkmk_parameters"></a>

## <a name="parameters"></a>Parámetros

La siguiente tabla muestra los parámetros de las herramientas de generación de código y proporciona una breve descripción de su uso.  
  
|Parámetro|Acceso directo|Descripción|Requerido|
|--|--|--|--|
|`deviceid`|`di`|Ya no se necesita|Falso|
|`devicepassword`|`dp`|Ya no se necesita|Falso|
|`domain`|`d`|El dominio en el que se autentica al conectarse al servidor local.|Falso|
|`url`||La URL para el servicio de la organización.|True a menos que use `interactivelogin`|
|`out`|`o`|El nombre de archivo para el código generado.|Verdadero|
|`language`|`l`|El idioma en el que generar el código. Puede ser ”CS” o ”VB”. El valor predeterminado es "CS".|Falso|
|`namespace`|`n`|El espacio de nombres para el código generado. El valor predeterminado es el espacio de nombre global.|Falso|  
|`username`|`u`|El nombre de usuario usado al conectar al servidor para la autenticación.|Falso|  
|`password`|`p`|La contraseña de usuario usada al conectar al servidor para la autenticación.|Falso|  
|`servicecontextname`||El nombre de la clase de contexto de servicio de la organización generada. Si no se proporciona un valor, no se crea ningún contexto del servicio.|Falso|
|`help`|`?`|Mostrar la información de uso.|Falso|
|`nologo`||Suprimir pancartas en tiempo de ejecución.|Falso|
|`generateActions`||Generar clases de solicitud y respuesta para acciones personalizadas.|Falso|
|`interactivelogin`|`il`|Cuando se use, se mostrará un diálogo para iniciar sesión en el servicio Common Data Service. Se omiten todos los demás parámetros relacionados con la conexión especificados en la línea de comandos.|Falso|  
|`connectionstring`|`connstr`|Contiene información, proporcionada como una sola cadena, para conectarse a una organización de Common Data Service. Se omiten todos los demás parámetros relacionados con la conexión especificados en la línea de comandos. Para obtener más información, consulte [Usar cadenas de conexión en útiles de XRM para conectarse a Common Data Service](../xrm-tooling/use-connection-strings-xrm-tooling-connect.md).|Falso|


<a name="bkmk_sampleconfig"></a>

## <a name="use-the-configuration-file"></a>Archivos el archivo de configuración

El archivo de configuración CrmSvcUtil.exe.config debe estar en la misma carpeta que la herramienta CrmSvcUtil.exe. El archivo de configuración usa los pares clave/valor estándar en la sección `appSettings`. Sin embargo, si ingresa un valor en la línea de comandos, ese valor se usará en lugar del que aparece en el archivo de configuración. Se ignorarán todos los pares clave/valor que se encuentran en el archivo de configuración de la aplicación que no coinciden con los parámetros esperados.  

En el archivo de configuración no se incluyen los parámetros `url` y `namespace`. Deben ingresarse desde la línea de comandos cuando se ejecuta la herramienta CrmSvcUtil.exe.  

El siguiente ejemplo muestra cómo configurar el archivo de salida y los parámetros del nombre de dominio del archivo de configuración de la aplicación mediante las teclas de método abreviado.  

```xml
<appSettings>    
    <add key="o" value="CrmProxy.cs"/>    
    <add key="d" value="mydomain"/>
</appSettings>  
```

<a name="bkmk_enabletrace"></a>

## <a name="enable-tracing"></a>Habilitar seguimiento
 Para habilitar el seguimiento luego de ejecutar la herramienta, agregue las siguientes líneas al archivo de configuración:  

```xml
<system.diagnostics>   
   <trace autoflush="false" indentsize="4">   
      <listeners>   
         <add name="configConsoleListener" type="System.Diagnostics.ConsoleTraceListener">   
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />   
         </add>   
      </listeners>   
   </trace>   
</system.diagnostics>  
```

Para obtener más información acerca de las opciones de seguimiento admitidas, consulte [Configurar el seguimiento de útiles de XRM](../xrm-tooling/configure-tracing-xrm-tooling.md).  

## <a name="community-tools"></a>Herramientas de la Comunidad

**Generador de enlace en tiempo de compilación** es una herramienta de la comunidad XrmToolbox. Consulte el tema [Herramientas y recursos para desarrolladores](../developer-tools.md) para obtener información sobre herramientas desarrolladas por la comunidad.

> [!NOTE]
> Las herramientas de la comunidad no son un producto de Microsoft y no se incluyen en el soporte técnico. Si tiene alguna duda relacionada con la herramienta, póngase en contacto con el Editor. Más información: [XrmToolBox](https://www.xrmtoolbox.com). 


### <a name="see-also"></a>Vea también

[Herramientas y recursos de desarrollo](../developer-tools.md)<br />
[Crear una extensión para la herramienta de generación de código](extend-code-generation-tool.md)<br />
[Descargar herramientas de NuGet](../download-tools-NuGet.md)