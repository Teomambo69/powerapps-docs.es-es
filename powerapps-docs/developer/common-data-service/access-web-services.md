---
title: Acceso a servicios web externos (Common Data Service para aplicaciones) | MicrosoftDocs
description: Aprenda a obtener acceso a un servicio web desde un complemento o una actividad de flujo de trabajo.
ms.custom: ''
ms.date: 2/6/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: pehecke
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# Acceso a servicios web externos

Los complementos y las actividades personalizadas de flujo de trabajo que se ejecutan en un espacio aislado pueden obtener acceso a la red con los protocolos HTTP y HTTPS. Esta funcionalidad proporciona soporte para obtener acceso a los servicios web populares como sitios sociales, fuentes de noticias, servicios web, etc. Las siguientes restricciones de acceso web se aplican a esta funcionalidad de espacios aislados.  
  
- Solo se admiten los protocolos HTTP y HTTPS.
- El acceso a localhost (bucle invertido) no está permitido.
- Las direcciones IP no se pueden usar. Debe usar una dirección web con nombre que requiera resolución de nombres DNS.
- La autenticación anónima es compatible y se recomienda. No existen ninguna disposición para preguntar los credenciales al usuario que inició la sesión o guardar dichos credenciales.

Otros métodos de acceso a los servicios web incluyen el uso de webhooks y [!INCLUDE [pn_azure_service_bus](../../includes/pn_azure_service_bus.md)]. Consulte los vínculos proporcionados más abajo para obtener más información sobre estos temas.

## Vea también

[[Complementos](plug-ins.md)](plug-ins.md)<br />
[[Extensiones de flujo de trabajo](workflow/workflow-extensions.md)](workflow/workflow-extensions.md)<br />
[[Integración de Azure](azure-integration.md)](azure-integration.md)<br />
[[Utilizar WebHooks](use-webhooks.md)](use-webhooks.md)<br />
[[Ejemplo: acceso web desde un complemento de espacio aislado](org-service/samples/web-access-plugin.md)](org-service/samples/web-access-plugin.md)
