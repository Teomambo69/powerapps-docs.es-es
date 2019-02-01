---
title: Compartir una aplicación incrustada de lienzo | MicrosoftDocs
ms.custom: ''
ms.date: 01/07/2019
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
  - PowerApps maker portal impact
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="share-an-embedded-canvas-app"></a>Compartir una aplicación incrustada de lienzo
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

En este tema se explica cómo compartir una aplicación incrustada de lienzo que ha creado ya.

Una vez que haya creado y haya agregado una aplicación incrustada de lienzo a un formulario controlado por modelos deberá realizar pasos para garantizar que todos los usuarios que tienen acceso al formulario controlado por modelos también accedan a la aplicación de lienzo y los datos que usa. Consulte las directrices siguientes:
-   Comparta la aplicación incrustada de lienzo con todos los usuarios de su organización o usuarios del grupo de seguridad o específicos. Más información: [Compartir una aplicación](../canvas-apps/share-app.md#share-an-app).
-   Asegúrese de que los usuarios tienen permisos adecuados para cualquier entidad de Common Data Service que su aplicación incrustada de lienzo use. Más información: [Administrar permisos de entidades](../canvas-apps/share-app.md#manage-entity-permissions)
-   Asegúrese de que los usuarios tienen permisos adecuados para datos de cualquier servicio de nube que su aplicación incrustada de lienzo use, como SharePoint o OneDrive. Los pasos para compartir son específicos para cada servicio en la nube y salen de alcance de PowerApps.

> [!NOTE]
> Actualmente no puede usar el privilegio **Aplicación de lienzo** en un rol de seguridad para conceder acceso a usuarios de aplicaciones a una aplicación incrustada o independiente de lienzo.

Las aplicaciones de lienzo incrustadas también reconocen las soluciones. De forma predeterminada se crean aplicaciones incrustadas de lienzo en la misma solución que el formulario controlado por modelos. Para mover la aplicación incrustada de lienzo de un entorno a otras aplicaciones de lienzo incrustadas de exportación e importación como parte de una solución igual que como cualquier otro componente.

## <a name="see-also"></a>Vea también
[Insertar una aplicación de lienzo en un formulario controlado por modelos](embed-canvas-app-in-form.md) <br />
[Pasar el registro actual como contexto de datos a una aplicación incrustada de lienzo](pass-current-embedded-canvas-app.md) <br />
[Pasar una lista de registros relacionados como contexto de datos a una aplicación incrustada de lienzo](pass-related-embedded-canvas-app.md) <br />
[Directrices acerca de cómo trabajar con aplicaciones de lienzo incrustadas](embedded-canvas-app-guidelines.md)
