---
title: Cree aplicaciones web mediante la autenticación entre servidores (S2S) (Common Data Service para aplicaciones) | Microsoft Docs
description: Use la autenticación de servidor a servidor (S2S) para comunicarse con seguridad y sin fisuras con CDS for Apps con sus aplicaciones y servicios web. La autenticación S2S es la forma común que las aplicaciones registradas en Microsoft AppSource usan para tener acceso a los datos de CDS for Apps de sus suscriptores.
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
# <a name="build-web-applications-using-server-to-server-s2s-authentication"></a>Crear aplicaciones web mediante autenticación de servidor a servidor (S2S)

Use la autenticación de servidor a servidor (S2S) para comunicarse con seguridad y sin fisuras con Common Data Service (CDS) for Apps con sus aplicaciones y servicios web. La autenticación S2S es la forma común que las aplicaciones registradas en Microsoft AppSource usan para tener acceso a los datos de CDS for Apps de sus suscriptores.  

 La autenticación S2S significa que no necesita usar una licencia de usuario de PowerApps de pago al conectarse a los entornos de CDS for Apps. No hay cuota de licencia para la cuenta de *usuario de la aplicación* especial que usará con la autenticación S2S. Con autenticación de S2S se crea una cuenta especial de usuario no autorizada de la aplicación sin licencia e incluye información sobre la aplicación registrada con Azure Active Directory (Azure AD). En lugar de credenciales de usuario, la aplicación se autentica en función de una entidad de servicio identificada por un valor de Id de objeto de Azure AD que se almacena en el registro de usuario de la aplicación. El usuario de la aplicación se asocia con un rol de seguridad personalizado que controla las clases de datos y las operaciones que la aplicación está autorizada a realizar.  

 Todas las operaciones realizadas por la aplicación o servicio mediante S2S se realizarán como el usuario de la aplicación que usted proporciona en lugar de como el usuario que accede a la aplicación. Si desea que la aplicación realice operaciones de datos en nombre de un usuario específico, como la persona que está interactuando con la aplicación, puede aplicar suplantación cuando el rol de seguridad personalizado aplicado a la entidad de servicio de la aplicación tenga los privilegios necesarios. Más información: [Suplantar a otro usuario](impersonate-another-user.md)  

 Una aplicación web o un servicio que use autenticación S2S es responsable de controlar el acceso a los datos a los que tiene acceso. Esto se realiza normalmente mediante un proveedor OpenID Connect. Más información: <http://openid.net/connect/>.  

## <a name="server-to-server-authentication-scenarios"></a>Escenarios de autenticación de servidor a servidor  
 Hay dos escenarios en los que puede aplicar autenticación S2S.  


|   Escenario    |   Descripción  |
|---------------|---------------|
| Multiempresa  | Es el escenario más común y el que se usa para aplicaciones distribuidas mediante Microsoft AppSource.<br /><br /> Cada inquilino de CDS for Apps se asocia a un inquilino de Azure AD. Su aplicación o servicio web se registra con su inquilino de Azure AD.<br /><br /> En este escenario cualquier inquilino de CDS for Apps puede usar potencialmente la aplicación multiempresa después de conceder consentimiento para que la aplicación acceda a los datos en su inquilino.                                                           |
| Una sola empresa | Este escenario normalmente se aplica a entornos de CDS for Apps que desean desarrollar aplicaciones para su propio inquilino y no se proponen distribuirlas a otros entornos de CDS for Apps.<br /><br /> Una empresa puede crear una aplicación web o servicio para conectarse a todos los entornos de CDS for Apps para su inquilino.<br /><br /> En este escenario, su aplicación web o servicio solo podrá conectarse a entornos de CDS for Apps que usen el mismo inquilino de Azure AD. |

 Ambos escenarios tienen elementos comunes aunque hay algunas diferencias. Puesto que la multiempresa es el escenario más común, el contenido de [Usar autenticación multiempresa entre servidores](use-multi-tenant-server-server-authentication.md) describe cómo usar S2S en este escenario e incluye notas cuando las opciones para la configuración de una sola empresa sean diferentes. 

[Usar autenticación entre servidores de una sola empresa](use-single-tenant-server-server-authentication.md) proporciona una visión general de este escenario y hará referencia a los procedimientos descritos en el contenido de autenticación S2S multiempresa.  

### <a name="see-also"></a>Vea también  
  
[Usar autenticación multiempresa entre servidores](use-multi-tenant-server-server-authentication.md)<br/> 
[Usar autenticación entre servidores de una sola empresa](use-single-tenant-server-server-authentication.md)   
