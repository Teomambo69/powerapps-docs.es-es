---
title: Directrices acerca de cómo trabajar con aplicaciones de lienzo incrustadas | MicrosoftDocs
ms.custom: ''
ms.date: 08/19/2019
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
ms.openlocfilehash: 42882b630cfe34cc17e310b32c9c072f0c2d5d8a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2758476"
---
# <a name="guidelines-on-working-with-embedded-canvas-apps"></a>Directrices acerca de cómo trabajar con aplicaciones de lienzo incrustadas
En este tema se proporcionan directrices acerca de cómo trabajar con aplicaciones del lienzo incrustadas así como sugerencias útiles para solucionar los problemas que puede encontrar.

-   Las aplicaciones de lienzo incrustadas se admiten solo con aplicaciones controladas por modelos de interfaz unificada.
-   Puede habilitar solo una aplicación insertada del lienzo por formulario. 
     - Puede tener múltiples aplicaciones incrustadas del lienzo agregadas al formulario pero puede habilitar solo una a la vez.
     - Si intenta habilitar más de una aplicación insertada del lienzo en un formulario controlado por modelos, recibirá un mensaje “solo una aplicación del lienzo se puede habilitar en un formulario.”
     - Para habilitar o deshabilitar una aplicación incrustada del lienzo consulte [Habilitar una aplicación de lienzo incrustada](#enable-an-embedded-canvas-app) y [Deshabilitar una aplicación incrustada de lienzo](#disable-an-embedded-canvas-app).
-   Cuando agrega una aplicación de lienzo incrustada a un formulario basado en modelos, use siempre un campo obligatorio que tiene garantizado siempre un valor. Si el campo no tiene un valor su aplicación incrustada de lienzo no se actualizará como respuesta a cualquier cambio en los datos del formulario controlado por modelos de host.
-   Publicar un formulario controlado por modelos tampoco publica la aplicación de lienzo incrustada.
     - Las aplicaciones incrustadas de lienzo tiene que publicarse independientemente del formulario controlado por modelos del host. Más información: [Publicación una aplicación](../canvas-apps/save-publish-app.md#publish-an-app).
-   Si abre PowerApps Studio para crear o editar una aplicación incrustada de lienzo mediante el botón **Personalizar** en las propiedades del control de aplicaciones de la lona está bloqueado debido a un bloqueador de elementos emergentes de explorador web, debe habilitar el sitio de make.powerapps.com o temporalmente deshabilitar el bloqueador de elementos emergentes y después seleccionar **Personalizar** de nuevo.
-   Las aplicaciones incrustadas de lienzo no se muestran al crear un nuevo registro ya que necesitan que se les pase un contexto de registro.
-   El objeto de ModelDrivenFormIntegration.Item es de solo lectura. 
     - Para devolver datos por escrito debe usar el conector Common Data Service. Más información: [Common Data Service](/connectors/commondataservice/)
-   Las aplicaciones incrustadas del lienzo se pueden crear solo a través del formulario controlado por modelos del host. 
    - Agregar aplicaciones de lienzo existentes como incrustadas en formularios basados en modelos no se admite actualmente.
    - En una futura actualización se proporcionará soporte para incrustar una aplicación de lienzo existente en un formulario basado en modelos mediante el identificador de la aplicación.
- Cuando vea un formulario controlado por modelos con una aplicación incrustada de lienzo, si recibe un mensaje de error del estilo “no hemos encontrado la aplicación” asegúrese de que la aplicación incrustada de lienzo esté en la misma solución que el formulario controlado por modelos.
- Cuando se ve un formulario controlado por modelos con una aplicación incrustada de lienzo, si recibe un mensaje de error como “parece que no tiene acceso a la aplicación. Solicite al propietario que la comparta con usted” asegúrese de que el autor ha compartido la aplicación incrustada de lienzo con usted. Más información: [Compartir una aplicación incrustada de lienzo](share-embedded-canvas-app.md).
- Ya no es posible agregar una aplicación de lienzo en el control de subcuadrícula.
    - En el lanzamiento de vista previa, los creadores pudieron agregar una aplicación de lienzo en un control de subcuadrícula. Con la incrustación de aplicaciones de lienzo en formularios basados en modelo ahora disponible de manera generalizada, la adición de una aplicación de lienzo incrustada en un formulario basado en modelo se simplifica al campo. 
    - Esto hace que sea más fácil para los creadores ya que no tienen que decidir de antemano si pasan el registro (formulario principal) como el contexto de datos o una lista de registros relacionados con el registro actual (formulario principal). 
    - Los creadores siempre empiezan con un campo y pueden tener acceso tanto al registro actual (formulario principal) como a una lista de registros relacionados con el registro actual (formulario principal).
    - Para obtener acceso a la lista de registros relacionados en la aplicación de lienzo, los creadores pueden usar el conector de Common Data Service y la función [Filtro](../canvas-apps/functions/function-filter-lookup.md) con la funcionalidad [Mejorar la experiencia de orígenes de datos y vistas de Common Data Service](https://powerapps.microsoft.com/blog/improved-data-source-selection-and-common-data-service-views/) habilitada en la aplicación de lienzo.  
    Por ejemplo, para tener acceso a la vista *Contactos activos* de la entidad *Contactos*, los creadores pueden usar: *Filter(Contacts, 'Contacts (Views)'.'Active Contacts')*.
    - Las aplicaciones de lienzo existentes que usen el control de subcuadrícula continuarán funcionando. Sin embargo, se recomienda migrar estas aplicaciones para usar un campo en su lugar. Más información: [Migrar aplicaciones de lienzo insertadas en formularios basados en modelos que usan una lista de registros relacionados con el registro actual (formulario principal)](embedded-canvas-app-migrate-from-preview.md#migrating-embedded-canvas-apps-on-model-driven-forms-that-use-a-list-of-records-related-to-the-current-main-form-record).

## <a name="enable-an-embedded-canvas-app"></a>Habilitar una aplicación incrustada de lienzo
1. Seleccione el campo que está personalizado para mostrarse como una aplicación incrustada de lienzo.
2. En el diálogo **Propiedades de campo**, seleccione la pestaña **Controles**.
3. En la lista de controles seleccione **Aplicación de lienzo** y seleccione la opción **Web** .
4. Seleccione **Aceptar**.

## <a name="disable-an-embedded-canvas-app"></a>Deshabilitar una aplicación incrustada de lienzo
1. Seleccione el campo que está personalizado para mostrarse como una aplicación incrustada de lienzo.
2. En el diálogo **Propiedades de campo**, seleccione la pestaña **Controles**.
3. En la lista de controles seleccione el control predeterminado y seleccione la opción **Web**.
4. Seleccione **Aceptar**.

## <a name="known-issues-and-limitations-with-embedded-canvas-apps"></a>Problemas y limitaciones conocidos con aplicaciones incrustadas de lienzo
- El control personalizado de aplicación de lienzo solo es compatible para usarlo con el tipo de cliente **Web** . Actualmente, no se admiten los tipos de cliente **Teléfono** y **Tableta** .
- El control ModelDrivenFormIntegration no proporciona un valor para campos de una entidad relacionada. 
  - Por ejemplo, cuando el control ModelDrivenFormIntegration está conectado a la entidad Cuentas, el uso de *ModelDrivenFormIntegration.Item.’Primary Contact’.’Full Name’* no devolverá un valor. 
  - Para obtener acceso a campos de una entidad relacionada, los creadores puede usar cualquiera de las expresiones enumeradas aquí:
    - *LookUp(Accounts, Account = GUID(First(ModelDrivenFormIntegration.Data).ItemId)).'Primary Contact'.'Full Name'*  
      - *ItemId* está vacío en el momento de creación pero tendrá un valor en tiempo de ejecución.
    - *LookUp(Accounts, Account = ModelDrivenFormIntegration.Item.Account).'Primary Contact'.'Full Name'* (Esta expresión es más fácil de leer, pero la anterior tendrá un comportamiento ligeramente mejor.)
- No puede usar el privilegio **Aplicación de lienzo** en un rol de seguridad para conceder acceso a usuarios de la aplicación a una aplicación incrustada o independiente de lienzo. Para obtener más información sobre compartir una aplicación incrustada de lienzo, consulte: [Compartir una aplicación incrustada de lienzo](share-embedded-canvas-app.md).
- Si responde escribiendo los mismos datos que se muestran en el formulario controlado por modelos de host, el formulario seguirá mostrando datos antiguos hasta que se actualice. Una forma simple de hacer esto es usar el método [RefreshForm](embedded-canvas-app-actions.md#refreshformshowprompt).

## <a name="see-also"></a>Vea también
[Insertar una aplicación de lienzo en un formulario controlado por modelos](embed-canvas-app-in-form.md) <br />
[Agregar una aplicación de lienzo incrustada en un formulario basado en modelos](embedded-canvas-app-add-classic-designer.md) <br />
[Editar una aplicación de lienzo incrustada en un formulario basado en modelos](embedded-canvas-app-edit-classic-designer.md) <br />
[Personalizar el tamaño y orientación de la pantalla de una aplicación de lienzo insertada en un formulario basado en modelos](embedded-canvas-app-customize-screen.md) <br />
[Realice acciones predefinidas en el formulario de host desde una aplicación de lienzo insertada](embedded-canvas-app-actions.md) <br />
[Propiedades y acciones del control ModelDrivenFormIntegration](embedded-canvas-app-properties-actions.md) <br />
[Compartir una aplicación incrustada de lienzo](share-embedded-canvas-app.md) <br />
[Migrar aplicaciones de lienzo insertadas en formularios basados en modelos creados mediante la versión de vista previa pública a la más reciente](embedded-canvas-app-migrate-from-preview.md) <br />
