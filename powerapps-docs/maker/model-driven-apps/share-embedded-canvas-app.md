---
title: Compartir una aplicación incrustada de lienzo | MicrosoftDocs
ms.custom: ''
ms.date: 06/25/2019
ms.reviewer: ''
ms.service: powerapps
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
[Agregar una aplicación de lienzo incrustada en un formulario basado en modelos](embedded-canvas-app-add-classic-designer.md) <br />
[Editar una aplicación de lienzo incrustada en un formulario basado en modelos](embedded-canvas-app-edit-classic-designer.md) <br />
[Personalizar el tamaño y orientación de la pantalla de una aplicación de lienzo insertada en un formulario basado en modelos](embedded-canvas-app-customize-screen.md) <br />
[Realice acciones predefinidas en el formulario de host desde una aplicación de lienzo insertada](embedded-canvas-app-actions.md) <br />
[Propiedades y acciones del control ModelDrivenFormIntegration](embedded-canvas-app-properties-actions.md) <br />
[Directrices acerca de cómo trabajar con aplicaciones de lienzo incrustadas](embedded-canvas-app-guidelines.md) <br />
[Migrar aplicaciones de lienzo insertadas en formularios basados en modelos creados mediante la versión de vista previa pública a la más reciente](embedded-canvas-app-migrate-from-preview.md) <br />
