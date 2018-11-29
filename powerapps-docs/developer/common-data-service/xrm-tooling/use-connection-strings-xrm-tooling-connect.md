---
title: Usar cadenas de conexión en útiles de XRM para conectarse a Common Data Service para aplicaciones (Common Data Service para aplicaciones)| Microsoft Docs
description: Los útiles de XRM le permiten conectarse a su entorno de Common Data Service para aplicaciones mediante las cadenas de conexión
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: a98b2fce-df49-4b60-91f4-a4446aa61cd3
caps.latest.revision: 21
author: MattB-msft
ms.author: kvivek
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-connection-strings-in-xrm-tooling-to-connect-to-common-data-service-for-apps"></a>Usar cadenas de conexión en útiles de XRM para conectarse a Common Data Service para aplicaciones.

Con CDS para aplicaciones, los útiles de XRM le permiten conectarse a su entorno de CDS para aplicaciones mediante las cadenas de conexión. Esto es similar al concepto de cadenas de conexión que se utilizan con SQL Server. Las cadenas de conexión tienen compatibilidad nativa en archivos de configuración, incluida la capacidad de cifrar las secciones de configuración para máxima seguridad. Esto permite configurar las conexiones de CDS para aplicaciones en tiempo de implementación, y no codificar de forma rígida en su aplicación para conectarse al entorno de CDS para aplicaciones.  
  
<a name="Create"></a> 

## <a name="create-a-connection-string"></a>Crear una cadena de conexión

 La cadena de conexión se especifica en el archivo app.config o web.config para su proyecto, como se muestra en el siguiente ejemplo.  
  
```xml  
<connectionStrings>  
    <add name="MyCDSServer" connectionString="AuthType=AD;Url=http://contoso:8080/Test;" />  
</connectionStrings>  
```  
  
> [!IMPORTANT]
>  Si agrega cualquier información confidencial al archivo app.config o web.config, por ejemplo, una contraseña de cuenta, asegúrese de tomar las precauciones de seguridad apropiadas para proteger la información.  
  
 Después de crear la cadena de conexión, úsela para crear un objeto <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.  
  
```csharp  
//Use the connection string named "MyCDSServer"  
//from the configuration file  
CrmServiceClient crmSvc = new CrmServiceClient(ConfigurationManager.ConnectionStrings["MyCDSServer"].ConnectionString);  
```  
  
> [!NOTE]
>  Tendrá que usar la directiva `using` en siguiente el código para hacer referencia al espacio de nombres de `System.Configuration` para obtener acceso a la cadena de conexión en el código: `using System.Configuration;`  
  
 Después de crear un objeto <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>, puede usar el objeto para realizar acciones en CDS para aplicaciones. Más información: [Usar útiles de XRM para ejecutar acciones en CDS para aplicaciones](use-xrm-tooling-execute-actions.md)  
  
<a name="Parameters"></a>

## <a name="connection-string-parameters"></a>Parámetros de la cadena de conexión

 La cadena de conexión contiene una serie de pares de name=value separados por punto y coma. La siguiente tabla muestra los parámetros admitidos, que se pueden escribir en cualquier orden.  
  
|Nombre del parámetro|Descripción|  
|--------------------|-----------------|  
|ServiceUri, Uri de servicio, Url o Servidor|Especifica la dirección URL al entorno de CDS para aplicaciones. La URL puede utilizar el protocolo http o https, y el puerto es opcional. El puerto predeterminado es 80 para el protocolo http y 443 para el protocolo https. La dirección URL del servidor suele encontrarse en el formato `https://`*`<organization-name>`*`.crm.dynamics.com`<br /><br /> Se requiere el nombre de la organización.|  
|Dominio|Especifica el dominio que comprobará las credenciales de usuario.|  
|UserName, nombre de usuario, UserId o id de usuario|Especifica el nombre de identificación del usuario asociado con las credenciales.|  
|Contraseña:|Especifica la contraseña del nombre de usuario asociado con las credenciales.|  
|HomeRealmUri o Uri de dominio de inicio|Especifica el Uri de dominio de inicio|  
|AuthenticationType o AuthType|Especifica el tipo de autenticación para conectarse al entorno de CDS para aplicaciones. Los valores válidos son: `AD`, `IFD` (AD FS habilitado), `OAuth` o `Office365`.<br /><br /> -   `AD` y `IFD` se permiten para entornos locales de CDS para aplicaciones únicamente.<br />-   `OAuth` se permite para CDS para aplicaciones y entornos locales.<br />-   `Office365` se permite solo para entornos de CDS para aplicaciones.|  
|RequireNewenvironment|Indica si se debe volver a usar una conexión existente si se vuelve a hacer la llamada mientras la conexión sigue activa. El valor predeterminado es `false` que indica que la conexión existente se reutilizará. Si se establece en `true`, se obliga al sistema a crear una conexión única.|  
|ClientId, AppId o ApplicationId|Especifica el `ClientID` asignado cuando se registró su aplicación en Azure Active Directory o Servicios de federación de Active Directory (AD FS).<br /><br /> Este parámetro es aplicable solo cuando especifica el tipo de autenticación como `OAuth`.|  
|RedirectUri o ReplyUrl|Especifica el URI de redirección de la aplicación que registró en Azure Active Directory o Servicios de federación de Active Directory (AD FS).<br /><br /> Este parámetro es aplicable solo cuando especifica el tipo de autenticación como `OAuth`.|  
|TokenCacheStorePath|Especifica la ruta de acceso completa a la ubicación donde la memoria caché del símbolo de usuario debe ser almacenada. El proceso en ejecución debe tener acceso a la ruta especificada. Es responsabilidad de los procesos establecer y configurar esta ruta.<br /><br /> Este parámetro es aplicable solo cuando especifica el tipo de autenticación como `OAuth`.|  
|LoginPrompt|Especifica si se le piden al usuario credenciales si las credenciales no se proporcionan. Los valores válidos son:<br /><br /> -   `Always`: Pide siempre al usuario que especifique credenciales.<br />-   `Auto`: Permite que el usuario seleccione en la interfaz de control de inicio de sesión si se muestra un mensaje o no.<br />-   `Never`: No pide al usuario que especifique credenciales. Si usa un método de conexión que no tiene interfaz de usuario, debe usar este valor.<br /><br /> Este parámetro es aplicable solo cuando especifica el tipo de autenticación como `OAuth`.|  
|CertStoreName|Especifica el nombre de la ubicación en el equipo donde se encuentra el certificado con la huella digital pasada. Este parámetro es aplicable solo cuando especifica el tipo de autenticación como `Certificate`.|
|CertThumbPrint| Especifica la huella digital del certificado para usar. Este parámetro es aplicable solo cuando especifica el tipo de autenticación como `Certificate`.|
|SkipDiscovery|Si el parámetro está establecida en True, el Uri de servicio se debe usar directamente.| 
  
<a name="Examples"></a>

## <a name="connection-string-examples"></a>Ejemplos de cadena de conexión
 
Los ejemplos siguientes muestran cómo usar cadenas de conexión para conectar con distintas implementaciones y escenarios de autenticación.  

<!-- TODO: Get rid of on-premises examples & settings? or just comment them out? -->

<!-- ### Integrated on-premises authentication  
  
```xml
<add name="MyCRMServer" connectionString="AuthType=AD;Url=http://contoso:8080/Test;" />  
```  
  
### Named account using on-premises authentication  
  
```xml  
<add name="MyCRMServer" connectionString="AuthType=AD;Url=http://contoso:8080/Test; Domain=CONTOSO; Username=jsmith; Password=passcode" />  
```  
   -->
### <a name="named-account-using-office-365"></a>Cuenta con nombre utilizando Office 365  
  
```xml
<add name="MyCDSServer" 
 connectionString="
  AuthType=Office365;
  Username=jsmith@contoso.onmicrosoft.com; 
  Password=passcode;
  Url=https://contoso.crm.dynamics.com"/>  
```  
  
### <a name="oauth-using-named-account-in-office-365-with-ux-to-prompt-for-authentication"></a>OAuth utilizando cuenta con nombre en Office 365 con UX para solicitar autenticación  
  
```xml
<add name="MyCDSServer"
 connectionString="
  AuthType=OAuth;
  Username=jsmith@contoso.onmicrosoft.com;
  Password=passcode;
  Url=https://contosotest.crm.dynamics.com;
  AppId=<GUID>;
  RedirectUri =app://<GUID>;
  TokenCacheStorePath =c:\MyTokenCache;
  LoginPrompt=Auto"/>  
```  
  
<!-- ### OAuth using named account in CDS for Apps on-premises with UX to prompt for authentication  
  
```xml
<add name="MyCRMServer" connectionString="AuthType=OAuth;Username=jsmith@contoso.onmicrosoft.com; Password=passcode;Url=https://contoso:8080/Test;AppId=<GUID>;RedirectUri=app://<GUID>;TokenCacheStorePath =c:\MyTokenCache;LoginPrompt=Auto"/>  
```  
  
### IFD using a named account with delegation to a sub realm  
  
```xml
<add name="MyCRMServer" connectionString="AuthType=IFD;Url=http://contoso:8080/Test; HomeRealmUri=https://server-1.server.com/adfs/services/trust/mex/;Domain=CONTOSO; Username=jsmith; Password=passcode" />  
```   -->

### <a name="certificate-based-authentication"></a>Autenticación basada en certificados

```xml
<add name="MyCDSServer" 
  connectionString="
  AuthType=Certificate;
  SkipDiscovery=true;
  url={InstanceUri};
  thumbprint={CertThumbPrintId};
  ClientId={AppId};
  RequireNewInstance=true"
  />
```

  
<a name="ConnectionStatus"></a>

## <a name="determine-your-connection-status"></a>Determinación del estado de la conexión

 Para determinar si la solicitud de conexión se realizó correctamente, compruebe el valor de la propiedad <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.IsReady> . Si es **true**, la conexión se realizó correctamente y está listo para trabajar. De lo contrario, compruebe los valores de las propiedades <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.LastCrmError> y <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.LastCrmException>. para la causa del error de conexión.  
  
### <a name="see-also"></a>Vea también

[Crear aplicaciones cliente de Windows mediante las herramientas XRM](build-windows-client-applications-xrm-tools.md)<br />
[Usar constructores CrmServiceClient para conectarse a CDS para aplicaciones](use-crmserviceclient-constructors-connect.md)<br />
[Usar útiles de XRM para ejecutar acciones en CDS para aplicaciones](use-xrm-tooling-execute-actions.md)<br />
<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>
