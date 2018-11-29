---
title: Servicio de exportación de datos (Common Data Service para aplicaciones) | Microsoft Docs
description: 'Capacidades, requisitos previos, API y programación del servicio de exportación de datos.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: sabinn-msft
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="data-export-service"></a>Servicio de exportación de datos

La exportación de datos es un servicio complementario habilitado como solución de Common Data Service para aplicaciones que agrega la capacidad de replicar los datos de Common Data Service para aplicaciones en un almacén de base de datos de Microsoft Azure SQL en una suscripción de Microsoft Azure propiedad del cliente. Los objetivos de destino admitidos son la base de datos de Microsoft Azure SQL y Microsoft Azure SQL Server en las máquinas virtuales de Microsoft Azure. La exportación de datos sincroniza inteligentemente los esquemas y datos completos de Dynamics 365 inicialmente y después sincroniza de manera continua cuando se producen cambios (cambios delta) en el sistema Dynamics 365 (en línea).  
  
 El servicio Exportación de datos proporciona una interfaz para administrar la configuración y la administración continua de este servicio desde CDS for Apps.  Para obtener más información, vea [Exportación de datos](https://technet.microsoft.com/library/a70feedc-12b9-4a2d-baf0-f489cdcc177d). En este tema se explican la interfaz programática y los problemas correspondientes para este servicio.  
  
## <a name="prerequisites-for-using-the-data-export-service"></a>Los requisitos previos para utilizar el servicio Exportación de datos  
 Puesto que este servicio necesita acceso a una base de datos de Microsoft Azure SQL externa desde CDS for Apps, deben cumplirse varios requisitos previos para poder tener acceso correctamente a este servicio. Los siguientes requisitos previos se describen más detalladamente desde el punto de vista de un administrador en la sección [Requisitos previos para usar el servicio de exportación de datos](https://technet.microsoft.com/library/mt744592.aspx).  
  
 El servicio CDS for Apps debe configurarse para que:  
  
- Las entidades que se exportarán están habilitadas con seguimiento de cambios. Para obtener más información, consulte [Usar el seguimiento de cambios para sincronizar los datos con sistemas externos](use-change-tracking-synchronize-data-external-systems.md).  
  
- El código se ejecuta en el contexto de un usuario con el rol de seguridad Administrador del sistema.  
  
> [!NOTE]
>  Tenga en cuenta que el acceso mediante programación a este servicio *no* requiere la instalación de la solución administrada Exportar datos asociada.  
  
 La base de datos de Azure SQL de destino debe estar configurada de modo que:  
  
- La suscripción debe admitir el volumen de datos que se replican desde la instancia de CDS for Apps.  
  
- Las configuraciones de firewall deben permitir el acceso desde la dirección IP del servicio Exportación de datos. Para obtener más información, consulte [Configurar una regla de firewall a nivel de servidor de base de datos de Azure SQL mediante Azure Portal](https://azure.microsoft.com/en-us/documentation/articles/sql-database-configure-firewall-settings/).  
  
- Se recomienda que la opción “Permitir acceso a servicios de Azure” esté habilitada.  
  
- El usuario de la base de datos, especificado en la cadena de conexión de Exportación de datos, debe tener los permisos adecuados para crear y modificar en la base de datos de destino.  Como mínimo incluyen: `CRTB`, `CRTY`, `CRVW`, `CRPR`, y `ALUS`. Para obtener más información, consulte [Permisos (motor de base de datos)](https://msdn.microsoft.com/en-us/library/ms191291.aspx).  
  
- Al menos un usuario tiene permisos extensos en el esquema. El siguiente script crea nuevo usuario de ese tipo.  
  
```sql  
  
USE MASTER;  
CREATE LOGIN NewUser WITH PASSWORD='newpassword';  
  
USE DESTINATIONDATABASE;  
CREATE USER NewUser FOR LOGIN NewUser  
GRANT CREATE TABLE, CREATE TYPE, CREATE VIEW, CREATE PROCEDURE, ALTER ANY USER to NewUser  
GRANT ALTER, REFERENCES, INSERT, DELETE, UPDATE, SELECT, EXECUTE ON SCHEMA::dbo TO NewUser  
  
```  
  
Para soluciones y servicios en línea, Azure proporciona un servicio de [Key Vault](https://azure.microsoft.com/en-us/services/key-vault/) para salvaguardar claves criptográficas, contraseñas y otros secretos.  Para usar Almacén de claves de Azure, este servicio propiedad del cliente se debe configurar para conceder permiso a "Servicio de exportación de datos de Dynamics 365”, que se usará para almacenar con seguridad la cadena de conexión de SQL Azure. Para realizar esta configuración con un script de PowerShell, consulte [Cómo configurar Azure Key Vault](https://technet.microsoft.com/library/mt744592.aspx). Como alternativa, este servicio se puede administrar con su API de REST; consulte [Administración de Key Vault](https://msdn.microsoft.com/library/azure/mt620024.aspx).  
  
También se aconseja que agregue el dominio https://discovery.crmreplication.azure.net/ a la lista de sitios de confianza en el explorador y habilite ventanas emergentes para este sitio.  
  
## <a name="programming-for-the-data-export-service"></a>Programación para el servicio Exportación de datos  
 El servicio de exportación de datos expone una API basada en REST que se divide en dos grupos: un conjunto de operaciones de `Metadata` para explorar la estructura organizativa, las relaciones y la información de conexión de CDS for Apps, y un conjunto de operaciones de `Profiles` para configurar y administrar cada replicación de datos.  Esta API se define y se documenta completamente en las direcciones URL [Swagger](http://swagger.io/) siguientes:  
  
|Extremo de Swagger|Descripción|  
|----------------------|-----------------|  
|[https://discovery.crmreplication.azure.net/swagger/docs/2016-01-01](https://discovery.crmreplication.azure.net/swagger/docs/2016-01-01)|Definición de JSON de la API del Servicio de exportación de datos para uso por las herramientas de desarrollo y procesos dinámicos|  
|[https://discovery.crmreplication.azure.net/swagger/ui/index#](https://discovery.crmreplication.azure.net/swagger/ui/index)|La versión de fácil uso de esta API para referencia del desarrollador|  
  
<a name="bk_ApiQuickReference"></a>   
### <a name="api-quick-reference"></a>Referencia rápida de la API  
 Para comodidad del lector, estas interfaces se resumen en las siguientes tablas.  
  
 **Operaciones de metadatos** (`https://discovery.crmreplication.azure.net/crm/exporter/metadata/`)  
  
|Recurso|Métodos|Descripción|  
|--------------|-------------|-----------------|  
|organizations|[GET](https://discovery.crmreplication.azure.net/swagger/ui/index#/Metadata/Metadata_GetOrganizations)|Obtener detalles organizativos de todas las organizaciones a las que el usuario actual pertenece|  
|discover|[GET](https://discovery.crmreplication.azure.net/swagger/ui/index#/Metadata/Metadata_GetOrgDetails)|Obtener los detalles organizativos de la organización especificada|  
|connector|[GET](https://discovery.crmreplication.azure.net/swagger/ui/index#/Metadata/Metadata_GetConnectorDetails)|Obtener los detalles de conector de la organización especificada|  
|entities|[GET](https://discovery.crmreplication.azure.net/swagger/ui/index#/Metadata/Metadata_GetEntities)|Obtener todas las entidades públicas exportables para la organización especificada|  
|relationships|[GET](https://discovery.crmreplication.azure.net/swagger/ui/index#/Metadata/Metadata_GetRelationships)|Obtener todas las relaciones exportables para la organización especificada|  
|hasorgacceptedprivacyterms|[GET](https://discovery.crmreplication.azure.net/swagger/ui/index#/Metadata/Metadata_HasOrgAcceptedPrivacyTerms)|Comprobar si la organización asociada ha aceptado los términos de privacidad|  
|acceptprivacyterms|[POST](https://discovery.crmreplication.azure.net/swagger/ui/index#/Metadata/Metadata_AcceptOrgPrivacyTerms)|Aceptar la organización especificada para acceso a datos|  
  
 **Operaciones con perfiles** (`[Organization-URI]/crm/exporter/`)  
  
|Recurso|Métodos|Descripción|  
|--------------|-------------|-----------------|  
|profiles|[GET](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_GetProfilesByOrganizationId), [POST](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_CreateProfile)|Obtener todos los perfiles de la organización especificada, crear un nuevo perfil de exportación|  
|profiles/{id}|[GET](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_GetProfileById), [PUT](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_UpdateProfile), [DELETE](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_DeleteProfileById)|Obtener, actualizar o eliminar un perfil concreto|  
|profiles/{id}/activate|[POST](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_Activate)|Activar un perfil, que inicia la replicación de los datos y metadatos asociados|  
|profiles/{id}/activatemetadata|[POST](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_ActivateMetadata)|Activar perfil para replicación de metadatos solo|  
|profiles/{id}/activatedata|[POST](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_ActivateData)|Activar perfil para replicación de datos solo|  
|profiles/{id}/deactivate|[POST](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_Deactivate)|Desactivar un perfil|  
|profiles/{id}/test|[GET](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_GetTestResultById)|Realizar operaciones de prueba en un perfil existente|  
|profiles/validate|[POST](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_ValidateBeforeProfileCreation)|Realizar operaciones de prueba en una descripción de perfil antes de crearla|  
|profiles/{id}/failures|[GET](https://discovery.crmreplication.azure.net/swagger/ui/index#/Profiles/Profiles_GetProfileFailuresInfoById)|Obtener la cadena de conexión a un blob que contiene detalles erróneos para un perfil determinado|  
  
### <a name="gain-access"></a>Obtener acceso  
Puesto que solo están autorizados los administradores del sistema de CDS for Apps a realizar operaciones de exportación de datos, estas API aplican autorización de autor de llamada mediante el uso de [tokens de seguridad](https://azure.microsoft.com/en-us/documentation/articles/active-directory-token-and-claims/) de Azure Active Directory ([AAD](https://azure.microsoft.com/en-us/services/active-directory/)). El fragmento de código siguiente demuestra cómo generar dicho token para una aplicación web mediante el nombre y la contraseña del administrador.   Debe reemplazar el `AppId`, `crmAdminUser` y `crmAdminPassword` con los valores adecuados al servicio. Este método se puede usar para desarrollo y prueba, pero deben usarse medios más seguros para producción, como el uso del Almacén de claves de Azure.  
  
```csharp  
  
//Reference Azure AD authentication Library (ADAL)    
using Microsoft.IdentityModel.Clients.ActiveDirectory;  
   . . .  
    string yourAppClientID = "[app-associated-GUID]";   //Your AAD-registered AppId   
    string crmAdminUser = "admin1@contoso.com";  //Your CRM administrator user name  
    string crmAdminPassword = "Admin1Password";  //Your CRM administrator password;   
    //For interactive applications, there are overloads of AcquireTokenAsync() which prompt for password.   
    var authParam = AuthenticationParameters.CreateFromResourceUrlAsync(new   
        Uri("https://discovery.crmreplication.azure.net/crm/exporter/aad/challenge")).Result;  
    AuthenticationContext authContext = new AuthenticationContext(authParam.Authority, false);  
    string token = authContext.AcquireTokenAsync(authParam.Resource, yourAppClientID,   
        new UserCredential(crmAdminUser, crmAdminPassword)).Result.AccessToken;  
  
```  
  
Para instrucciones sobre cómo obtener un `AppId`, consulte [Autorizar acceso a aplicaciones web mediante OAuth 2.0 y Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-protocols-oauth-code/). Para obtener más información sobre la seguridad de usuarios de Azure, consulte [Escenarios de autenticación para Azure AD](https://azure.microsoft.com/en-us/documentation/articles/active-directory-authentication-scenarios/).  
  
### <a name="error-handling-and-failure-processing"></a>Gestión de errores y procesamiento de errores  
 Una vez que un perfil está correctamente configurado, el proceso de sincronización suele ser muy fiable. Sin embargo, si un registro no se sincroniza, se aplica el procesamiento de errores siguiente:  
  
1. Después del intervalo de reintento configurado, se realiza otro intento de sincronizar el registro. Esto se repite hasta el número máximo configurado de reintentos.  
  
2. El registro se marca como procesado.  
  
3. Una entrada de registro de error correspondiente se escribe en el registro de errores.  
  
4. Se procesa el siguiente registro.  
  
Puesto que el registro está marcado como procesado, no se realiza ningún intento futuro de sincronizar el registro hasta su valor o esquema cambia. (Tenga en cuenta que al volver a escribir valores idénticos en una instancia de entidad también se marca como modificada.)  
  
Las entradas en el registro de errores son de solo escritura. Los éxitos o errores futuros durante la sincronización del mismo registro no producen la alteración de entradas pasadas para este registro. Por ejemplo, una entrada de error permanecerá en el registro de errores incluso después que el registro se haya sincronizado correctamente en algún ciclo de sincronización posterior.  
  
> [!CAUTION]
>  Esta lógica de procesamiento de errores está sujeta a modificaciones en versiones futuras de este servicio.  
  
Estas entradas de error se pueden recuperar a través de la solicitud [Obtener detalles de error de un perfil determinado](https://discovery.crmreplication.azure.net/swagger/ui/index). La respuesta devuelve un URI a un blob de Azure que contiene información de error.  Cada línea tiene los siguientes campos separados por comas (se agregan nuevas líneas por claridad):  
  
```  
  
Entity: <entity-name>,   
RecordId: <”N/A” | guid>,   
NotificationTime: <datetime>,   
ChangeType: <sync-type>,  
FailureReason: <description>  
  
```  
  
Por ejemplo:  
  
```  
  
Entity: lead,   
RecordId: N/A, NotificationTime: , ChangeType: Trigger Initial Export, FailureReason: There is already an object named 'hatest201_lead' in the database.  
Entity: account, RecordId: b2a19cdd-88df-e311-b8e5-6c3be5a8b200, NotificationTime: 8/31/2016 6:50:38 PM, ChangeType: New, FailureReason: Invalid object name 'dbo.hatest201_account'.  
```  
  
### <a name="see-also"></a>Vea también  
 [Administrar datos en Dynamics 365](/dynamics365/customer-engagement/developer/manage-data)   
 [Importar datos](import-data.md)
