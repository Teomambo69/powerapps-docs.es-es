---
title: Insertar una aplicación de lienzo en un formulario controlado por modelos | MicrosoftDocs
ms.custom: ''
ms.date: 12/10/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.assetid: 00e62904-2ce9-4730-a113-02b1fedbf22e
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

# <a name="embed-a-canvas-app-on-a-model-driven-form"></a>Insertar una aplicación de lienzo en un formulario controlado por modelos

Las aplicaciones de lienzo permiten a proveedores fácilmente diseñar y crear diseños personalizados con diseñador de aplicaciones de lienzo WYSIWYG de poco código. Las aplicaciones de lienzo también permiten a los proveedores conectar y mostrar datos de más de 200 orígenes de datos en sus formularios.

> [!NOTE]
> Esta característica está actualmente en vista previa. <br />
> [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]

Con aplicaciones incrustadas de lienzo, los proveedores pueden aportar la fuerza de aplicaciones de lienzo a sus formularios controlados por modelos. Con aplicaciones incrustadas de lienzo, puede crear fácilmente áreas visuales completas en un formulario y mostrar datos pantalla de diversos orígenes directamente al lado de datos de Common Data Service.

   > [!div class="mx-imgBorder"] 
   > ![](media/embed-canvas-app-in-form.png "Aplicación de lienzo incrustada en un formulario de aplicaciones controlado por modelos")

Las aplicaciones de lienzo se insertan en formularios controlados por modelos igual que se agregan otros controles personalizados. Una aplicación incrustada de lienzo incluye capacidades completas de integración de datos que aportan datos contextuales del formulario controlado por modelos del host a la aplicación incrustada de lienzo.

Los pasos para insertar una aplicación de lienzo al formulario controlado por modelos varían en función del contexto de los datos que desea que el formulario controlado por modelos de host proporcione a la aplicación incrustada de lienzo.
-   Pase el registro actual como el contexto de datos. Más información: [Pasar el registro actual como contexto de datos con una aplicación incrustada de lienzo](pass-current-embedded-canvas-app.md)
-   Pase una lista de registros relacionados con el registro actual como contexto de datos. Más información: [Pasar una lista de registros relacionados como contexto de datos con una aplicación incrustada de lienzo](pass-related-embedded-canvas-app.md) 

<!-- After you have added an embedded canvas app to your model-driven form, learn how to share your embedded canvas app with other users (LINK TO ARTICLE #4).  -->

<!-- For things to keep in mind when working with embedded canvas apps and to help troubleshoot any issues you might encounter, see (LINK TO ARTICLE #5). -->

## <a name="see-also"></a>Vea también
[¿Qué son las aplicaciones de lienzo en PowerApps?](../canvas-apps/getting-started.md) <br />
[Agregar y configurar un control de aplicaciones de lienzo en PowerApps](../canvas-apps/add-configure-controls.md) <br />
[Información general sobre conectores de aplicaciones de lienzo para PowerApps](../canvas-apps/connections-list.md) 
