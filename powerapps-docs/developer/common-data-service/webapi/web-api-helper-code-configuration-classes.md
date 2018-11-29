---
title: 'Código auxiliar de la API web: Clases de configuración (Common Data Service para aplicaciones)| Microsoft Docs'
description: La jerarquía de clases de configuración puede usarse para especificar los datos de conexión necesarios para acceder a servicios web de Common Data Service para aplicaciones desde la aplicación.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 3b86c11a-15e1-40a1-aca0-34a9bab2f04a
caps.latest.revision: 14
author: brandonsimons
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-api-helper-code-configuration-classes"></a>Código auxiliar de la API web: Clases de configuración

Utilice la jerarquía de clases de configuración para especificar los datos de conexión necesarios para acceder a servicios web de Common Data Service para aplicaciones desde la aplicación. Puede proporcionar estos datos de conexión estableciendo valores directamente en el código, posiblemente desde la entrada del usuario, con la clase base de `Configuration`. Normalmente, se suministra esta información en la configuración almacenada en el archivo de configuración de la aplicación, utilizando la clase derivada, `FileConfiguration`.  
  
El código de origen para la jerarquía de clases de configuración se encuentra en el archivo Configuration.cs en la [Biblioteca de código auxiliar de la API web del SDK de CRM](https://www.nuget.org/packages/Microsoft.CrmSdk.WebApi.Samples.HelperCode/). La jerarquía de clases de configuración está diseñado para funcionar conjuntamente con la clase `Authentication` para permitirle establecer una conexión segura al servicio de Common Data Service para aplicaciones. Para obtener más información, consulte             [Usar la biblioteca de código auxiliar de la API web de Common Data Service para aplicaciones (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md).  
  
<a name="bkmk_Connectiondata"></a>

## <a name="connection-data"></a>Datos de conexión

La clase `Configuration` lee y analiza el archivo de configuración de la aplicación para obtener los datos de conexión siguientes.  
  
|Datos de conexión|Implementaciones|Descripción|  
|---------------------|-----------------|-----------------|  
|URL del servicio|Todo|La dirección URL base al servicio de Common Data Service para aplicaciones|  
|Nombre de usuario|Todo|El nombre de usuario registrado en CDS para aplicaciones|  
|Contraseña:|Todo|La contraseña de ese usuario|  
|Dominio|Todo|El dominio del servicio de Common Data Service para aplicaciones para autenticación de Active Directory|  
|Id. de cliente|Solo Online e IFD|El identificador del cliente de la aplicación como fue registrado con Azure AD para Common Data Service para aplicaciones|  
|URL de redireccionamiento|Solo Online e IFD|URI de devolución de llamada para la aplicación actual.|  
  
<!-- TODO:
For more information on obtaining a client ID and a redirection URL for an application, see [Walkthrough: Register a Common Data Service for Apps app with Azure Active Directory](../walkthrough-register-app-azure-active-directory.md).  
   -->
<a name="bkmk_FileConfigconnectionsettings"></a>

### <a name="fileconfiguration-connection-settings"></a>Configuración de conexión de FileConfiguration

La mayoría de los ejemplos de API Web de Common Data Service para aplicaciones usan la clase derivada, `FileConfiguration`, para extraer los datos de conexión del archivo de configuración de la aplicación, App.config. Este archivo tiene varias opciones de la aplicación que se aplican a los distintos modos de implementación de Common Data Service para aplicaciones. El valor `connectionString` contiene la dirección URL y el nombre de usuario de servicio. Además, la configuración de `ClientId` y `RedirectUrl` es necesaria para implementaciones con conexión a Internet (IFD) u online. Las siguientes líneas, extraídas del archivo App.config predeterminado proporcionado con la mayoría de los ejemplos de la API web, contienen estos datos de conexión como valores de marcador de posición. Debe reemplazar estos marcadores de posición con los valores específicos del usuario actual, el servidor de Common Data Service para aplicaciones y la aplicación cliente.  
  
```xml  
<connectionStrings> 
    <add name="default" connectionString="Url=http://myserver/myorg/; Username=name; Password=password; Domain=domain" /> 
</connectionStrings> 
<appSettings> 
    <add key="ClientId" value="e5cf0024-a66a-4f16-85ce-99ba97a24bb2" /> 
    <add key="RedirectUrl" value="http://localhost/SdkSample" /> 
</appSettings>  
```  
  
El contenido completo del archivo de configuración predeterminado se proporciona en [Default configuration file listing](#bkmk_Defaultconfigurationfilelisting)..  
  
<a name="bkmk_Classhierarchyandmembers"></a>
 
## <a name="class-hierarchy-and-members"></a>Jerarquía de clases e integrantes

La siguiente tabla muestra los integrantes públicos de la jerarquía de clases de configuración.  
  
 <!-- TODO:
![Common Data Service for Apps Web API Helper Library&#45;Configuration Class Diagram](../media/web-api-helper-library-configuration-class-diagram.png "Common Data Service for Apps Web API Helper Library-Configuration Class Diagram")   -->
  
 **Clase de configuración**  
  
 *Propiedades:*  
  
 Todas las propiedades se asignan directamente a los datos de conexión correspondientes detallados en la sección anterior.  
  
 *Métodos*:  
  
 El constructor predeterminado deja todas las propiedades sin inicializar (nulo).  
  
 **Clase FileConfiguration**  
  
 *Propiedades:*  
  
 `Name` es el nombre de entrada del valor de cadena de conexión.  
  
 `PathToConfig` es la ruta de acceso completa o relativa al archivo de configuración de la aplicación.  
  
 *Métodos*:  
  
 El constructor predeterminado deja todas las propiedades sin inicializar (nulo).  
  
 El constructor no predeterminado toma un único parámetro de cadena que especifica la cadena de conexión con nombre. Un valor de cadena vacía o cadena nula genera la primera entrada de cadena de conexión que se usa.  
  
 El método `Load` abre, lee, y analiza el archivo de configuración especificado. Es utilizado por el constructor no predeterminado.  
  
<a name="bkmk_usage"></a>

## <a name="usage"></a>Uso

 Las clases `FileConfiguration` y `Authentication` se diseñan para usar en tándem para leer la información de conexión en App.config y a continuación establecer una conexión segura con el servicio de Common Data Service para aplicaciones de destino. Esto se puede implementar con las instrucciones siguientes.  
  
```csharp  
FileConfiguration config = new FileConfiguration(null); Authentication auth = new Authentication(config); httpClient = new HttpClient(auth.ClientHandler, true);  
```  
  
 El constructor no predeterminado en la clase `Configuration` permite el uso de una cadena de conexión con nombre, por ejemplo:  
  
```csharp  
Configuration config = new FileConfiguration(“TestServer”);  
```  
  
 Si un nombre de cadena de conexión nulo o vacío se pasa al constructor de la clase `FileConfiguration`, se usará la primera cadena de conexión desde la parte superior del archivo de configuración.  
  
 Además, los ejemplos del SDK admiten un parámetro de comando en tiempo de ejecución, representando el nombre de la cadena de conexión deseada, para pasar al constructor. Esta opción se implementará por el siguiente código:  
  
```csharp  
if (cmdargs.Length > 0) { config = new FileConfiguration(cmdargs[0]); } else { config = new FileConfiguration(null); }  
```  
  
<a name="bkmk_Configurationsearchorder"></a>

### <a name="configuration-search-order"></a>Orden de búsqueda de configuración

 Si usa el archivo de configuración de una aplicación predeterminada o personalizada, la configuración de la aplicación `AlternateConfig` se puede proporcionar en el archivo para especificar un archivo de configuración alternativo. Si existe este archivo, su configuración de conexión se usará en su lugar.  
  
```xml  
<add key="AlternateConfig" value="C:\Temp\crmsample.exe.config"/>  
```  
  
 Uno uso común de este valor es proporcionar un archivo de configuración global para compartir entre varias aplicaciones, en lugar de editar el archivo App.config de cada aplicación. Es especialmente útil para compartir la información de configuración y registro entre varias aplicaciones que pasan por las fases de desarrollo y de prueba. A continuación solo para producción se proporcionaría información de configuración y registro única para cada aplicación.  
  
<a name="bkmk_Defaultconfigurationfilelisting"></a>

## <a name="default-configuration-file-listing"></a>Lista de archivos de configuración predeterminados

 El archivo App.config, suministrado con la mayoría de los ejemplos de la API web de Common Data Service para aplicaciones, contiene valores de conexión con marcadores de posición que deben ser editados por el desarrollador o el administrador del sitio.  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5.2" />
   </startup>
   <connectionStrings>
      <clear />
      <!-- When providing a password, make  
                sure to set the app.config file's security so that only you can read it. -->
      <add name="default" connectionString="Url=http://myserver/myorg/; Username=name; Password=password; Domain=domain" />
      <add name="CrmOnline" connectionString="Url=https://mydomain.crm.dynamics.com/;                   Username=someone@mydomain.onmicrosoft.com; Password=password" />
   </connectionStrings>
   <appSettings>
      <!--For information on how to register an app and obtain the ClientId and RedirectUrl values see https://msdn.microsoft.com/dynamics/crm/mt149065  
                -->
      <!--Active Directory application registration. -->
      <!--These are dummy values and should be replaced with your actual app registration values.-->
      <add key="ClientId" value="e5cf0024-a66a-4f16-85ce-99ba97a24bb2" />
      <add key="RedirectUrl" value="http://localhost/SdkSample" />
      <!-- Use an alternate configuration file for connection string and setting values. This optional setting enables use of an app.config file shared among multiple applications. If the specified file does not exist,  
                this setting is ignored.-->
      <add key="AlternateConfig" value="C:\Temp\crmsample.exe.config" />
   </appSettings>
</configuration>  
```  
  
## <a name="class-listing"></a>Lista de clases

 El origen más actual para esta clase se encuentra en el paquete de NuGet de la [Biblioteca de código auxiliar de la API web del SDK de CRM](https://www.nuget.org/packages/Microsoft.CrmSdk.WebApi.Samples.HelperCode).  
  
```csharp  
using System;
using System.IO;
using System.Security;
using System.Configuration;

namespace Microsoft.Crm.Sdk.Samples.HelperCode
{
    /// <summary>
    /// An application configuration containing user logon, application, and web service information
    /// as required for CRM Web API authentication.
    /// </summary>
    public class Configuration
    {
        #region Properties
        /// <summary>
        /// The root address of the Dynamics CRM service.
        /// </summary>
        /// <example>https://myorg.crm.dynamics.com</example>
        public string ServiceUrl { get; set; }

        /// <summary>
        /// The redirect address provided when the application was registered in Microsoft Azure
        /// Active Directory or AD FS.
        /// </summary>
        /// <remarks>Required only with a web service configured for OAuth authentication.</remarks>
        /// <seealso cref="https://msdn.microsoft.com/library/dn531010.aspx#bkmk_redirect"/>
        public string RedirectUrl { get; set; }

        /// <summary>
        /// The client ID that was generated when the application was registered in Microsoft Azure
        /// Active Directory or AD FS.
        /// </summary>
        /// <remarks>Required only with a web service configured for OAuth authentication.</remarks>
        public string ClientId { get; set; }

        /// <summary>
        /// The user name of the logged on user or null.
        /// </summary>
        public string Username { get; set; }

        /// <summary>
        ///  The password of the logged on user or null.
        /// </summary>
        public SecureString Password { get; set; }

        /// <summary>
        ///  The domain of the logged on user account or null.
        /// </summary>
        /// <remarks>Required only with a web service configured for Active Directory authentication.</remarks>
        public string Domain { get; set; }

        #endregion Properties

        #region Constructors

        /// <summary>
        /// Constructs a configuration object.
        /// </summary>
        public Configuration() { }

        #endregion Constructors
    }

    /// <summary>
    /// A configuration that is persisted to file storage.
    /// </summary>
    /// <remarks>This implementation defaults to using an app.config file. However, you
    /// can derive a subclass and override the virtual methods to make use of other
    /// file formats.
    /// 
    /// One set of application registration settings and multiple named connection strings are supported.</remarks>
    public class FileConfiguration : Configuration
    {
        #region Properties
        /// <summary>
        /// The full or relative path to the application's configuration file.
        /// </summary>
        /// <remarks>The file name is in the format <appname>.exe.config.</appname></remarks>
        public string PathToConfig { get; set; }

        /// <summary>
        /// The name of the connection.
        /// </summary>
        public string Name { get; set; }

        #endregion Properties

        #region Constructors
        /// <summary>
        /// Constructs a file configuration.
        /// </summary>
        public FileConfiguration()
            : base()
        { }

        /// <summary>
        /// Loads a named connection string and application settings from persistent file storage.
        /// The configuration file must have the same name as the application and be located in the 
        /// run-time folder.
        /// </summary>
        /// <param name="name">The name of the target connection string. An empty or null string value 
        /// results in the first named configuration being used.</param>
        /// <remarks>The app.config file must exist in the run-time folder and have the name
        /// <appname>.exe.config. To specify an app.config file path, use the Load() method.</remarks>
        public FileConfiguration(string name)
            : base()
        {
            var path = System.IO.Path.Combine(Directory.GetCurrentDirectory(), Environment.GetCommandLineArgs()[0]);

            Load(name, String.Concat(path, ".config"));
        }

        #endregion Constructors

        #region Methods
        /// <summary>
        /// Loads server connection information and application settings from persistent file storage.
        /// </summary>
        /// <remarks>A setting named OverrideConfig can optionally be added. If a config file that this setting
        /// refers to exists, that config file is read instead of the config file specified in the path parameter.
        /// This allows for an alternate config file, for example a global config file shared by multiple applications.
        /// </summary>
        /// <param name="connectionName">The name of the connection string in the configuration file to use. 
        /// Each CRM organization can have its own connection string. A value of null or String.Empty results
        /// in the first (top most) connection string being used.</param>
        /// <param name="path">The full or relative pathname of the configuration file.</param>
        public virtual void Load(string connectionName, string path)
        {
            // Check passed parameters.
            if (string.IsNullOrEmpty(path) || !System.IO.File.Exists(path))
                throw new ArgumentException("The specified app.config file path is invalid.", this.ToString());
            else
                PathToConfig = path;

            try
            {
                // Read the app.config file and obtain the app settings.
                System.Configuration.Configuration config = null;
                ExeConfigurationFileMap configFileMap = new ExeConfigurationFileMap();
                configFileMap.ExeConfigFilename = PathToConfig;
                config = ConfigurationManager.OpenMappedExeConfiguration(configFileMap, ConfigurationUserLevel.None);

                var appSettings = config.AppSettings.Settings;

                // If an alternate config file exists, load that configuration instead. Note the test
                // for redirectTo.Equals(path) to avoid an infinite loop.
                if (appSettings["AlternateConfig"] != null)
                {
                    var redirectTo = appSettings["AlternateConfig"].Value;
                    if (redirectTo != null && !redirectTo.Equals(path) && System.IO.File.Exists(redirectTo))
                    {
                        Load(connectionName, redirectTo);
                        return;
                    }
                }

                // Get the connection string.
                ConnectionStringSettings connection;
                if (string.IsNullOrEmpty(connectionName))
                {
                    // No connection string name specified, so use the first one in the file.
                    connection = config.ConnectionStrings.ConnectionStrings[0];
                    Name = connection.Name;
                }
                else
                {
                    connection = config.ConnectionStrings.ConnectionStrings[connectionName];
                    Name = connectionName;
                }

                // Get the connection string parameter values.
                if (connection != null)
                {
                    var parameters = connection.ConnectionString.Split(';');
                    foreach (string parameter in parameters)
                    {
                        var trimmedParameter = parameter.Trim();
                        if (trimmedParameter.StartsWith("Url="))
                            ServiceUrl = parameter.Replace("Url=", String.Empty).TrimStart(' ');

                        if (trimmedParameter.StartsWith("Username="))
                            Username = parameters[1].Replace("Username=", String.Empty).TrimStart(' ');

                        if (trimmedParameter.StartsWith("Password="))
                        {
                            var password = parameters[2].Replace("Password=", String.Empty).TrimStart(' ');

                            Password = new SecureString();
                            foreach (char c in password) Password.AppendChar(c);
                        }
                        if (trimmedParameter.StartsWith("Domain="))
                            Domain = parameter.Replace("Domain=", String.Empty).TrimStart(' ');
                    }
                }
                else
                    throw new Exception("The specified connection string could not be found.");

                // Get the Azure Active Directory application registration settings.
                RedirectUrl = appSettings["RedirectUrl"]?.Value;
                ClientId = appSettings["ClientId"]?.Value;
            }
            catch (InvalidOperationException e)
            {
                throw new Exception("Required setting in app.config does not exist or is of the wrong type.", e);
            }
        }

        /// <summary>
        /// Save the current configuration to persistent file storage.
        /// </summary>
        /// <remarks>Any existing configuration is overwritten.</remarks>
        public virtual void Save()
        {
            throw new NotImplementedException();
        }

        /// <summary>
        /// Add a named connection string to persistent file storage.
        /// </summary>
        /// <remarks>A named connection string from the current configuration is added to an existing
        /// configuration file./remarks>
        public virtual void AddConnection()
        {
            throw new NotImplementedException();
        }

        #endregion Methods
    }
} 
```  
  
### <a name="see-also"></a>Vea también

[Introducción a la API web (C#)](get-started-dynamics-365-web-api-csharp.md)<br />
[Iniciar un proyecto de la API web en Visual Studio (C#)](start-web-api-project-visual-studio-csharp.md)<br />
[Usar la biblioteca de código auxiliar de la API web de Common Data Service para aplicaciones (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md).<br />
[Código auxiliar: clase de autenticación](web-api-helper-code-authentication-class.md)<br />
[Código auxiliar: clase CrmHttpResponseException](web-api-helper-code-crmhttpresponseexception-class.md)<br />
[Ejemplo de código auxiliar SDK para punto de conexión del servicio de organización](https://www.nuget.org/packages/Microsoft.CrmSdk.Samples.HelperCode-CS)  