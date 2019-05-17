---
title: Directrices acerca de cómo trabajar con aplicaciones de lienzo incrustadas | MicrosoftDocs
ms.custom: ''
ms.date: 01/07/2019
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

# <a name="guidelines-on-working-with-embedded-canvas-apps"></a>Directrices acerca de cómo trabajar con aplicaciones de lienzo incrustadas
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

En este tema se proporcionan directrices acerca de cómo trabajar con aplicaciones del lienzo incrustadas así como sugerencias útiles para solucionar los problemas que puede encontrar.

-   Las aplicaciones de lienzo incrustadas se admiten solo con aplicaciones controladas por modelos de interfaz unificada.
-   Puede habilitar solo una aplicación insertada del lienzo por formulario. 
     - Puede tener múltiples aplicaciones incrustadas del lienzo agregadas al formulario pero puede habilitar solo una a la vez.
     - Si intenta habilitar más de una aplicación insertada del lienzo en un formulario controlado por modelos, recibirá un mensaje “solo una aplicación del lienzo se puede habilitar en un formulario.”
     - Para habilitar o deshabilitar una aplicación incrustada del lienzo consulte [Habilitar una aplicación de lienzo incrustada](#enable-an-embedded-canvas-app) y [Deshabilitar una aplicación incrustada de lienzo](#disable-an-embedded-canvas-app).
-   Las aplicaciones incrustadas del lienzo se pueden crear, editar y reproducir solo a través del formulario controlado por modelos del host.
     - No puede crear una aplicación incrustada de lienzo directamente fuera del contexto de un formulario controlado por modelos.
     - De forma similar abrir una aplicación incrustada de lienzo para editarla o reproducirla fuera del contexto de un formulario controlado por modelos no es posible.

     > [!NOTE]
     > Aunque puede poder abrir una aplicación incrustada de lienzo fuera de una aplicación controlada por modelo, esto no es compatible.

-   Tenga en cuenta lo siguiente al usar un control de subcuadrícula para agregar una aplicación de lienzo incrustada a un formulario controlado por modelos.
     - Los datos (campos y valores) enviados a la aplicación incrustada del lienzo en tiempo de ejecución están determinados por la vista que se especifica como **Vista predeterminada** en la sección **origen de datos** de las propiedades del control de la subcuadrícula. Use solo los campos de la aplicación incrustada de lienzo incluidos en la vista o agréguelos a la vista si es necesario. Todos los campos no incluidos en la vista mostrarán valores vacíos en tiempo de ejecución. 
     - Los criterios de filtro para una vista no se usan en el momento de la creación. Por tanto, los datos que ve al crear aplicaciones incrustadas de lienzo no están filtrados, son simplemente una lista de los pocos registros superiores a los que tiene acceso. En el tiempo de ejecución, los criterios de filtrado de la vista se aplican como se prevé y solo se muestran los datos relevantes.
-   Si usa un control de campo para agregar una aplicación incrustada de lienzo a un formulario con control de modelo, siempre use un campo obligatorio que tiene garantizado siempre un valor. Si el campo no tiene un valor su aplicación incrustada de lienzo no se actualizará como respuesta a cualquier cambio en los datos del formulario controlado por modelos de host.
-   Publicar un formulario controlado por modelos tampoco publica la aplicación de lienzo incrustada.
     - Las aplicaciones incrustadas de lienzo tiene que publicarse independientemente del formulario controlado por modelos del host. Más información: [Publicación una aplicación](../canvas-apps/save-publish-app.md#publish-an-app).
-   Si abrir PowerApps Studio para crear o editar una aplicación incrustada de lienzo mediante el botón **Personalizar** en las propiedades del control de aplicaciones de la lona está bloqueado debido a un bloqueador de elementos emergentes de explorador web, debe habilitar el sitio de web.powerapps.com o temporalmente deshabilitar el bloqueador de elementos emergentes y después seleccionar **Personalizar** de nuevo.
-   Las aplicaciones incrustadas de lienzo no se muestran al crear un nuevo registro ya que necesitan que se les pase un contexto de registro.
-   El objeto de ModelDrivenFormIntegration.Data es de solo lectura. 
     - Para devolver datos por escrito debe usar el conector Common Data Service. Más información: [Common Data Service](/connectors/commondataservice/)
-   El objeto de ModelDrivenFormIntegration.Data es una lista de registros. 
     - Incluso el registro actual se pasa a la aplicación incrustada de lienzo mediante ModelDrivenFormIntegration.Data como una lista que contiene un solo registro.
     - Para hacer referencia directamente el registro puede usar [Primera función](../canvas-apps/functions/function-first-last.md). Ejemplo: First(ModelDrivenFormIntegration.Data).Name
-   Cambiar manualmente el identificador de la aplicación en las propiedades de control de la aplicación de lienzo debe ser evitado al máximo.
     - El identificador de la aplicación de la aplicación de lienzo se genera y se rellena automáticamente en su lugar. 
     - Si por alguna razón no necesita editarlo manualmente, debe asegurarse de que cualquier identificador de aplicación que use corresponde con una aplicación de lienzo *incrustada* y no solo a una aplicación independiente de lienzo. 
     - La aplicación incrustada de lienzo también debe haberse creado con el mismo contexto de datos que el formulario controlado por modelos va a enviar.
     - Una vez actualizado el identificador de la aplicación seleccione **Personalizar** para abrirlo en PowerApps Studio y establecer la conexión a la nueva aplicación.
     - Realice un pequeño cambio en la aplicación para ponerla en un estado sin guardar y a continuación, guarde y publique la aplicación.
- Cuando vea un formulario controlado por modelos con una aplicación incrustada de lienzo, si recibe un mensaje de error del estilo “no hemos encontrado la aplicación” asegúrese de que la aplicación incrustada de lienzo esté en la misma solución que el formulario controlado por modelos.
- Cuando se ve un formulario controlado por modelos con una aplicación incrustada de lienzo, si recibe un mensaje de error como “parece que no tiene acceso a la aplicación. Solicite al propietario que la comparta con usted” asegúrese de que el autor ha compartido la aplicación incrustada de lienzo con usted. Más información: [Compartir una aplicación incrustada de lienzo](share-embedded-canvas-app.md).

## <a name="enable-an-embedded-canvas-app"></a>Habilitar una aplicación incrustada de lienzo
1. Seleccione el control de subcuadrícula o el campo que está personalizado para mostrarse como una aplicación incrustada de lienzo.
2. En el diálogo **Propiedades de campo** (o **Establecer propiedades** para la subcuadrícula), seleccione la pestaña **Controles**.
3. En la lista de controles seleccione **Aplicación de lienzo** y seleccione la opción **Web** .
4. Seleccione **Aceptar**.

## <a name="disable-an-embedded-canvas-app"></a>Deshabilitar una aplicación incrustada de lienzo
1. Seleccione el control de subcuadrícula o el campo que está personalizado para mostrarse como una aplicación incrustada de lienzo.
2. En el diálogo **Propiedades de campo** (o **Establecer propiedades** para la subcuadrícula), seleccione la pestaña **Controles**.
3. En la lista de controles seleccione el control predeterminado y seleccione la opción **Web**.
4. Seleccione **Aceptar**.

## <a name="known-issues-and-limitations-with-embedded-canvas-apps"></a>Problemas y limitaciones conocidos con aplicaciones incrustadas de lienzo
- El control personalizado de aplicación de lienzo solo es compatible para usarlo con el tipo de cliente **Web** . Actualmente, no se admiten los tipos de cliente **Teléfono** y **Tableta** . Más información: [Utilizar controles personalizados para visualizaciones de datos de aplicaciones controladas por modelos](use-custom-controls-data-visualizations.md)
- Al crear un nuevo registro, una aplicación incrustada de lienzo de un formulario no se muestra incluso después de que se guarde el registro. 
-    El objeto ModelDrivenFormIntegration.Data no funciona actualmente con los controles de formulario de presentación y los controles de formulario de edición.
- No puede usar el privilegio **Aplicación de lienzo** en un rol de seguridad para conceder acceso a usuarios de la aplicación a una aplicación incrustada o independiente de lienzo. Para obtener más información sobre compartir una aplicación incrustada de lienzo, consulte: [Compartir una aplicación incrustada de lienzo](share-embedded-canvas-app.md).
- Si responde escribiendo los mismos datos que se muestran en el formulario controlado por modelos de host, el formulario seguirá mostrando datos antiguos hasta que se actualice. Una forma simple de hacer esto es usar el método [RefreshForm](embedded-canvas-app-actions.md).
- Si no ve IntelliSense en los [métodos para realizar acciones predefinidas](embedded-canvas-app-actions.md) en las aplicaciones de lienzo incrustadas que se crearon antes de que la funcionalidad estuviera disponible; guarde, cierre y vuelva a abrir la aplicación. 

## <a name="see-also"></a>Vea también
[Insertar una aplicación de lienzo en un formulario controlado por modelos](embed-canvas-app-in-form.md) <br />
[Pasar el registro actual como contexto de datos a una aplicación incrustada de lienzo](pass-current-embedded-canvas-app.md) <br />
[Pasar una lista de registros relacionados como contexto de datos a una aplicación incrustada de lienzo](pass-related-embedded-canvas-app.md) <br />
[Realice acciones predefinidas en el formulario de host desde una aplicación de lienzo insertada](embedded-canvas-app-actions.md) <br />
[Compartir una aplicación incrustada de lienzo](share-embedded-canvas-app.md)
