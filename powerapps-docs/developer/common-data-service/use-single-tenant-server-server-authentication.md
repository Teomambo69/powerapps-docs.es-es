---
title: Usar autenticación entre servidores de una sola empresa (Common Data Service para aplicaciones) | Microsoft Docs
description: <Description>
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
# <a name="use-single-tenant-server-to-server-authentication"></a>Usar autenticación entre servidores de una sola empresa


El escenario entre servidores de una sola empresa suele aplicarse a organizaciones empresariales que tienen varios entornos de Common Data Service (CDS) para aplicaciones utilizando Servicios de federación de Active Directory (AD FS) para autenticación. Sin embargo, también lo pueden aplicar entornos cuando la aplicación no se distribuirá a otros entornos.  
  
 Una empresa puede crear una aplicación web o servicio para conectarse a todos los entornos de CDS for Apps para el inquilino único.  
  
## <a name="differences-from-multi-tenant-scenario"></a>Diferencias con el escenario multiempresa  
 Crear una aplicación o un servicio web para autenticación entre servidores de una sola empresa es similar a lo que se usa para una organización multiempresa, aunque hay algunas diferencias importantes.  
  
-   Puesto que todas las organizaciones se encuentran en la misma empresa, no es necesario que un administrador de inquilinos conceda consentimiento. La aplicación ya está registrada en el inquilino.  
  
-   Tiene la posibilidad de usar certificados en lugar de claves si lo prefiere.  
  
### <a name="see-also"></a>Vea también  
 [Usar autenticación multiempresa entre servidores](use-multi-tenant-server-server-authentication.md)   
 [Crear aplicaciones web mediante autenticación de servidor a servidor (S2S)](build-web-applications-server-server-s2s-authentication.md)

<!--

 Can this scenario be hightlighted here: https://crmtipoftheday.com/767/server-to-server-authentication-is-here/

-->