---
title: Entidades de seguridad de campo (Common Data Service para aplicaciones) | Microsoft Docs
description: 'Obtenga información sobre el uso de las entidades de seguridad de campo para aplicar seguridad de nivel de campo, que limita el acceso del campo a determinados usuarios y equipos.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="field-security-entities"></a>Entidades de seguridad de campo

Use las entidades de seguridad de campo para aplicar seguridad de nivel de campo, que limita el acceso del campo a determinados usuarios y equipos. El ámbito de la seguridad de nivel de campo es global, lo cual significa que se aplica a todos los registros de la organización, independientemente del nivel jerárquico de la unidad de negocio al que pertenece el registro o el usuario. La seguridad de campo funciona en todos los Common Data Service para aplicaciones, incluido el cliente web, Microsoft Dynamics 365 for Outlook y Microsoft Dynamics. Se aplica a todos los componentes, como los servicios web, los informes, la búsqueda, el acceso sin conexión, las vistas filtradas, la auditoría y la detección de duplicados de CDS for Apps. Para esta versión, la seguridad de campo se puede aplicar a los campos personalizados y a muchos campos predefinidos (OOB).  
  
 Para obtener más información sobre cómo los campos protegidos cambian el comportamiento de los métodos, vea [Cómo se puede usar la seguridad de campos para controlar el acceso a los valores de campo Dynamics 365](/dynamics365/customer-engagement/developer/security-dev/use-field-security-control-access-field-values).  
  
> [!IMPORTANT]
>  Los perfiles de seguridad de nivel de campo impiden que los usuarios involuntarios obtengan acceso a los datos de CDS for Apps en función de las definiciones del perfil. Si los ACL de SQL Server están mal configurados o si existe un problema de inyección de SQL, los adversarios pueden obtener acceso directo a los datos de SQL Server omitiendo las restricciones de seguridad de nivel de campo. Para obtener más información, consulte [Información general sobre amenazas de seguridad de la aplicación web](https://msdn.microsoft.com/library/f13d73y6.aspx).  
  
<a name="bkmk_setup"></a>   

## <a name="set-up-and-use-field-security"></a>Configuración y seguridad de campo de uso  
 Para utilizar seguridad de campo, debe llevar a cabo lo siguiente:  
  
1. Crear un registro de perfil de seguridad de campo  
  
2. Agregar usuarios o equipos al perfil  
  
3. Busque un atributo que se pueda proteger en el nivel de campo  
  
4. Proteja el atributo, bien cuando cree el atributo o actualizando los metadatos del atributo  
  
5. Publicar las personalizaciones de atributos.  
  
6. Crear un registro de permisos de campo que defina qué acceso (creación, actualización, lectura) tendrá el perfil para el atributo personalizado  
  
   Para el código de ejemplo sobre cómo realizar estos pasos, vea [Ejemplo: Habilitar la seguridad de campo para una entidad](/dynamics365/customer-engagement/developer/sample-enable-field-security-entity).  
  
   Use los siguientes atributos de permisos de campo para definir si el perfil de seguridad de campo especificado puede crear, leer o actualizar un atributo. 
   Puede establecer o comparar el valor de estos atributos mediante la utilización del conjunto de opciones globales `field_security_permission_type`:  
  
-   `FieldPermission`.`CanCreate`  
  
-   `FieldPermission`.`CanRead`  
  
-   `FieldPermission`.`CanUpdate`  
  
> [!IMPORTANT]
>  Si usuarios de bajo nivel de privilegio reciben acceso de lectura a la entidad de perfil de seguridad de campo, pueden ver qué perfiles tienen otros usuarios y encontrar a otros usuarios con acceso a los atributos protegidos que les interesan. Puede usar posteriormente técnicas de ingeniería social para asignar un perfil con acceso a estos atributos protegidos.  
  
<a name="bkmk_whichattributes"></a>   

## <a name="which-attributes-can-be-secured"></a>¿Qué atributos se pueden proteger?  
 Para ver qué atributos se puede proteger, puede consultar los metadatos de la entidad para las siguientes propiedades:  
  
- <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.CanBeSecuredForCreate>  
  
- <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.CanBeSecuredForRead>  
  
- <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.CanBeSecuredForUpdate>  
  
  Hay algunas reglas adicionales que se aplican a determinados tipos de datos de atributo:  
  
- Los atributos booleanos se pueden proteger para crear y actualizar operaciones, pero no para leer.  
  
- Los atributos de conjunto de opciones se pueden proteger para crear, actualizar y leer cuando no se especifica un valor predeterminado.  
  
  Existen miles de atributos que pueden protegerse, por lo que hay dos formas más fáciles de búsqueda de esta información. Para ver los metadatos de las entidades de su organización, instale la solución Explorador de metadatos que se describe en [Exploración de los metadatos de su organización](/dynamics365/customer-engagement/developer/browse-your-metadata). También puede examinar la documentación de referencia para las entidades en la [Referencia de entidad](/dynamics365/customer-engagement/developer/about-entity-reference).  
  
<a name="bkmk_sharing"></a>   
## <a name="share-secured-fields"></a>Compartir campos protegidos  
 Puede compartir campos protegidos del mismo modo que puede compartir registros. Para ello, se puede crear, actualizar o eliminar un registro de `PrincipalObjectAttributeAccess` (uso compartido de campo) en el que podrá especificar al usuario o al equipo, a la entidad y los permisos.  
  
 En la siguiente tabla se enumeran los métodos correspondientes para proteger un campo en comparación con los necesarios para proteger un registro.  
  
|Uso compartido de registros|Uso compartido de acceso a campos|  
|--------------------|--------------------------|  
|Utilice el mensaje <xref:Microsoft.Crm.Sdk.Messages.GrantAccessRequest> para conceder acceso a los registros a un usuario o a un equipo.|Use el mensaje <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> o el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*> para conceder acceso seguro a campos a un usuario o equipo.|  
|Utilice el mensaje <xref:Microsoft.Crm.Sdk.Messages.ModifyAccessRequest> para actualizar el acceso a los registros a un usuario o a un equipo.|Use el mensaje <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> o el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> para actualizar el acceso seguro a campos de un usuario o equipo.|  
|Utilice el mensaje <xref:Microsoft.Crm.Sdk.Messages.RevokeAccessRequest> para quitar el acceso a los registros a un usuario o a un equipo.|Use el mensaje <xref:Microsoft.Xrm.Sdk.Messages.DeleteRequest> o el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Delete*> para quitar el acceso seguro a campos de un usuario o equipo.|  
  
### <a name="see-also"></a>Vea también  
 [El modelo de seguridad de Dynamics 365](security-model.md)   
 [Entidades de administración y seguridad](/dynamics365/customer-engagement/developer/administration-security-entities)   
 [Entidad FieldSecurityProfile](/reference/entities/fieldsecurityprofile.md)   
 [Entidad FieldPermission](/reference/entities/fieldpermission.md)   
 [Entidad PrincipalObjectAttributeAccess](/reference/entities/principalobjectattributeaccess.md)   
 [Cifrado de datos de nivel de campo](field-level-data-encryption.md)   
 [Ejemplo: Recuperar permisos de campo](/dynamics365/customer-engagement/developer/sample-retrieve-field-permissions)   
 [Ejemplo: Habilitar la seguridad de campo para una entidad](org-service/samples/enable-field-security-entity.md)   
 [Ejemplo: Recuperar los registros de uso compartido de campos](/dynamics365/customer-engagement/developer/sample-retrieve-field-sharing-records)