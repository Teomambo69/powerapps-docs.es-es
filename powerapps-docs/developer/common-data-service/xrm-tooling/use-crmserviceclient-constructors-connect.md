---
title: Use constructores CrmServiceClient para conectarse a CDS para aplicaciones (Common Data Service para aplicaciones)| Microsoft Docs
description: 'Puede crear una instancia de la clase CrmServiceClient y, a continuación, utilizar uno de los constructores para conectar a Common Data Service para aplicaciones'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 74862506-a955-4846-a148-ac266f65592f
caps.latest.revision: 27
author: MattB-msft
ms.author: kvivek
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-crmserviceclient-constructors-to-connect-to-cds-for-apps"></a>Usar constructores CrmServiceClient para conectarse a CDS para aplicaciones

Para conectarse a CDS para aplicaciones, cree una instancia de la clase <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> y después use uno de los constructores para conectarse. Todas las llamadas a CDS para aplicaciones que usan la clase <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> son seguras para el hilo.  
  
Aparte de los constructores mencionados en este tema, también puede usar cadenas de conexión con <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> para conectarse CDS para aplicaciones. Más información: [Usar cadenas de conexión en útiles de XRM para conectarse a CDS para aplicaciones](use-connection-strings-xrm-tooling-connect.md).  
  
<a name="orgServiceproxy"></a>

## <a name="connect-to-cds-for-apps-using-organizationserviceproxy"></a>Conexión a CDS para aplicaciones mediante OrganizationServiceProxy

 Use el siguiente constructor para conectarse a CDS para aplicaciones mediante la instancia de <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy> proporcionada por el usuario.  
  
```csharp
CrmServiceClient crmSvc = new CrmServiceClient(<externalOrgServiceProxy>);  
```  
  
<a name="orgWebProxyClient"></a>

## <a name="connect-to-cds-for-apps-using-organizationwebproxyclient"></a>Conexión a CDS para aplicaciones mediante OrganizationWebProxyClient

 Use el siguiente constructor para conectarse a CDS para aplicaciones mediante la instancia de <xref:Microsoft.Xrm.Sdk.WebServiceClient.OrganizationWebProxyClient> proporcionada por el usuario.  
  
```csharp
CrmServiceClient crmSvc = new CrmServiceClient(<externalOrgWebProxyClient>);  
```  
  
<a name="Office365"></a>

## <a name="connect-to-cds-for-apps-office-365"></a>Conectar a CDS para aplicaciones (Office 365)

 Use el siguiente constructor para utilizar el protocolo CDS para aplicaciones para conectarse a la instancia de Office 365.  
  
```csharp  
CrmServiceClient crmSvc = new CrmServiceClient("<crmUserId>", CrmServiceClient.MakeSecureString("<crmPassword>"), "<crmRegion>", "<orgName>", useUniqueInstance:false, useSsl:false, <orgDetail>, isOffice365:false);  
```  
  
 Los valores válidos para el parámetro `<crmRegion>` son: `NorthAmerica`, `EMEA`, `APAC`, `SouthAmerica`,  `Oceania`, `JPN`, `CAN`, `IND` y `NorthAmerica2`. Si lo establece en `String.Empty`, buscará los servidores de todas las regiones de la organización de CDS para aplicaciones. Para el parámetro `<orgName>`, puede especificar el nombre único o el nombre descriptivo.  
  
 Los parámetros de los siguientes son opcionales:  `useUniqueInstance`, `useSsl`, y `orgDetail`.  
  
<a name="Office365oAuth"></a>

## <a name="connect-to-cds-for-apps-office-365-using-oauth"></a>Conexión a CDS para aplicaciones (Office 365) mediante OAuth
 
 Utilice el siguiente constructor para utilizar el protocolo OAuth y conectarse a su instancia de CDS para aplicaciones en Office 365. La compatibilidad con OAuth se introdujo en CDS para aplicaciones.  
  
> [!NOTE]
>  Detección global admite ahora todas las consultas de instancia, regionales y globales. Para el tipo de autenticación `OAuth`, el valor de parámetro `crmRegion` global se establece de manera predeterminada como `Online Region  = Don't Know`, excepto donde se requieran reglas especiales de la región. Alemania y Norteamérica 2 no se exploran cuando se selecciona `Online Region = Don't Know`.

```csharp  
CrmServiceClient crmSvc = new CrmServiceClient("<crmUserId>", CrmServiceClient.MakeSecureString("<crmPassword>"), "<crmRegion>", "<orgName>", useUniqueInstance:false, <orgDetail>,  
                  <user>, <clientId>, <redirectUri>, <tokenCachePath>, <externalOrgWebProxyClient>, PromptBehavior.Auto);  
```  
  
 Este constructor usa la [Biblioteca de autenticación de Active Directory de Microsoft Azure (ADAL)](/azure/active-directory/develop/active-directory-authentication-libraries) para autenticar usuarios. Si las credenciales de usuario (nombre de usuario y contraseña) no se especifican, ADAL le pide al usuario que proporcione las credenciales en función del parámetro `PromptBehavior` (opcional) especificado en este constructor. ADAL autentica las credenciales mediante el protocolo de OAuth, obtiene los tokens de acceso y actualización de Azure Active Directory, y después usa el token de acceso para hacer solicitudes a CDS para aplicaciones.  
  
 Los valores válidos para el parámetro `<crmRegion>` son: `NorthAmerica`, `EMEA`, `APAC`, `SouthAmerica`, `Oceania`, `JPN`, `CAN`, `IND` y `NorthAmerica2`. Si lo establece en **String.Empty**, buscará los servidores de todas las regiones de la organización de CDS para aplicaciones. Para el parámetro `<orgName>`, puede especificar el nombre único o el nombre descriptivo.  
  
<!-- No on-premises or IFD enabled for this version yet
<a name="ActiveDirectory"></a>

## Connect to CDS for Apps on-premises (Active Directory)

Use the following constructor to connect to an on-premises instance with Active Directory authentication.  
  
```csharp  
CrmServiceClient crmSvc = new CrmServiceClient(new System.Net.NetworkCredential("<credential>"), authType, "<hostName>", "<port>", "<orgName>", useUniqueInstance:false, useSsl:false, <orgDetail>);  
  
```  
  
 This will run an Active Directory authentication based on the specified domain. For the `<hostName>` parameter, specify the host name of your CDS for Apps server, for example: `cdstest`. For the `<orgName>` parameter, you can specify either the unique or friendly name.  
The following parameters are optional: `useUniqueInstance`, `useSsl`, and `orgDetail`.  
  
<a name="IFD"></a> 
  
## Connect to CDS for Apps Internet-facing deployment (IFD) 
 
 Use the following constructor to connect to a CDS for Apps IFD instance.  
  
```csharp
CrmServiceClient crmSvc = new CrmServiceClient(new System.Net.NetworkCredential("<credential>"), authType, "<hostName>", "<port>", "<orgName>", useUniqueInstance:false, useSsl:false, <orgDetail>);  
  
```  
  
 This will run a claims-based authentication based on the specified local domain. This is useful for customers that use AD FS, and have configured their CDS for Apps server as claims, where the user population lives in the same AD FS domain as the CDS for Apps server. For the `<hostName>` parameter, specify the host name of your CDS for Apps server, for example, `cdstest`. For the `<orgName>` parameter, you can specify either the unique or friendly name.  
  
 The following parameters are optional: `useUniqueInstance`,  `useSsl`, and `orgDetail`.  
  
<a name="OPoAuth"></a> 

## Connect to CDS for Apps Internet-facing deployment (IFD) using OAuth

 Use the following constructor to use the OAuth protocol in Active Directory Federation Services (AD FS) in Windows Server 2012 R2 to connect to a CDS for Apps IFD instance. For this constructor to work, the computer where CDS for Apps is installed must have been configured to use AD FS 2.2 as the security token service (STS).  
  
```csharp
CrmServiceClient crmSvc = new CrmServiceClient("<crmUserId>", CrmServiceClient.MakeSecureString("<crmPassword>"), "<domain>","<homeRealm>", "<hostName>", "<port>", "<orgName>", useSsl, useUniqueInstance,   
                        <orgDetail>, <user>, <clientId>, <redirectUri>, <tokenCachePath>, externalOrgWebProxyClient, PromptBehavior.Auto);  
  
```  
 The `clientId` and `redirectUri` values for the application supporting OAuth should be registered in the IFD server.  
  
 If the user credentials (user name and password) aren’t specified, ADAL prompts the user to provide the credentials depending on the `PromptBehavior` parameter (optional) specified in the constructor. ADAL authenticates the user using the security token from AD FS, and uses the token to perform actions in CDS for Apps.  
  
<a name="ClaimsBased"></a>
   
## Connect to CDS for Apps (claims-based)
  
 Use the following constructor to use claims-based authentication.  
  
```  
CrmServiceClient crmSvc = new CrmServiceClient(new System.Net.NetworkCredential("<UserId>", "<password>", “<domain>”, "<homeRealm>"),"<hostName>", "<port>", "<orgName>");    
```  
  
 This will run a claims-based authentication against the specified Home realm. This is useful for customers that use AD FS, and have configured their CDS for Apps server as claims, where the user population lives in the same AD FS domain as the CDS for Apps server. For the `<hostName>` parameter, specify the host name of your CDS for Apps server, for example, `cdstest`. For the `<orgName>` parameter, you can specify either the unique or friendly name.  
   -->
  
 ## <a name="connect-to-dynamics-365-online-using-certificate-based-authentication"></a>Conectar a Dynamics 365 (online) mediante autenticación basada en certificados
 Use el constructor siguiente para usar autenticación basada en certificados.
 
 ```csharp
 CrmServiceClient CrmSvc = new CrmServiceClient("<certificate>", "<certificateStoreName>", "<certificateThumbPrint>", "<instanceUrl>", <useUniqueInstance>, <orgDetail>, <clientId>, <redirectUri>, <tokenCachePath>);
 ```
 Esto ejecutará la autenticación basada en certificados. Los valores `clientId` y `redirectUri` para la aplicación se proporcionan cuando se registra una aplicación en **Azure Portal**. 
 
 Los parámetros de los siguientes son opcionales: `useUniqueInstance`, `useSsl`, y `orgDetail`.
 
<a name="Determine"></a>

## <a name="determine-your-connection-status"></a>Determinación del estado de la conexión
 
 Para determinar si la solicitud de conexión se realizó correctamente, compruebe el valor de la propiedad <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.IsReady> . Si es **true**, la conexión se realizó correctamente y está listo para trabajar. De lo contrario, compruebe los valores de las propiedades <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>. <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.LastCrmError> y <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.LastCrmException> para la causa del error de conexión.  
  
### <a name="see-also"></a>Vea también

[Usar cadenas de conexión en útiles de XRM para conectarse a CDS para aplicaciones](use-connection-strings-xrm-tooling-connect.md).<br />
[Utilizar Cmdlets de PowerShell de Windows de útiles de XRM para conectarse a CDS para aplicaciones](use-powershell-cmdlets-xrm-tooling-connect.md)<br />
[Usar API de herramientas XRM para ejecutar acciones en CDS para aplicaciones](use-xrm-tooling-execute-actions.md)
<xref:Microsoft.Xrm.Tooling.Connector.AuthenticationType><br />
[Crear aplicaciones cliente de Windows mediante las herramientas XRM](build-windows-client-applications-xrm-tools.md)
<!-- TODO:[Sample: Quick Start for CDS for Apps](../sample-quick-start.md)-->

