---
title: Pasar el registro actual como contexto de datos con una aplicación incrustada de lienzo | MicrosoftDocs
ms.custom: ''
ms.date: 12/17/2018
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

# <a name="pass-the-current-record-as-data-context-to-an-embedded-canvas-app"></a>Pasar el registro actual como contexto de datos a una aplicación incrustada de lienzo
En este tema se explica cómo agregar una aplicación incrustada de lienzo y pasar el registro actual (formulario principal) como contexto de datos a la aplicación incrustada de lienzo.

> [!NOTE]
> Esta característica está actualmente en vista previa. <br />
> [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)] 

Imagine que desea agregar una aplicación incrustada de lienzo en el formulario principal de una cuenta y pasar el registro de cuenta actual a la aplicación incrustada de lienzo. Para ello, siga estos pasos: 

1.  Inicie sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) y abra el editor de formularios para un formulario principal de una entidad, como la entidad contable. 
2.  Seleccione la sección del formulario donde desea que aparezca la aplicación incrustada de lienzo.
3.  Usando el panel del explorador de campos, agregue un campo obligatorio, como **Nombre de cuenta**.
      > [!IMPORTANT]
      > Use siempre un campo obligatorio que siempre tiene garantizado un valor. Si el campo no tiene un valor, su aplicación incrustada de lienzo no se actualizará como respuesta a cualquier cambio en los datos del formulario controlado por modelos de host.
4.  Con este campo seleccionado, en la pestaña **Inicio**, en el grupo **Editar**, haga clic en **Cambiar propiedades**.
5.  En el cuadro de diálogo **Propiedades de campo** , seleccione la pestaña **Controles** .
6.  En la pestaña **Controles** seleccione **Agregar control**.
7.  En el cuadro de diálogo **Agregar control** , en la lista de controles disponibles, seleccione **Aplicación de lienzo** y después seleccione **Agregar**.
8.  En el cuadro de diálogo **Propiedades de campo**, en la lista de controles seleccione **Aplicación de lienzo** y seleccione la opción **Web**.
9.  En la sección debajo de la lista de controles, la lista de propiedades disponible para el control de aplicaciones de lienzo se muestra.
     - La propiedad **Nombre de entidad** especifica la entidad que proporcionará los datos a la aplicación incrustada de lienzo. Se establecerá en la entidad que contiene el campo que se agregó en un paso anterior.
         - Tenga en cuenta que, aunque esta propiedad parece cambiable, cambiarla no tendrá ningún efecto en la aplicación incrustada de lienzo. Está previsto que solo sirva como referencia para usted.
     - La propiedad **Identificador de la aplicación** especifica el identificador de la aplicación incrustada de lienzo. Se generará y rellenará automáticamente en su lugar cuando se cree la aplicación de lienzo.
         - Tenga en cuenta que, los cambios efectuados en el valor **Identificador de la aplicación** rompen el vínculo entre el formulario controlado por modelos y la aplicación incrustada de lienzo.
10. Seleccione **Personalizar** para crear o editar la aplicación de lienzo. Esto abre PowerApps Studio en una nueva ficha.
       > [!NOTE]
       > Si abrir PowerApps Studio está bloqueado debido a un bloqueador de elementos emergentes de explorador web que debe habilitar el sitio de web.powerapps.com o temporalmente deshabilitar el bloqueador de elementos emergentes y después seleccionar **Personalizar** de nuevo.
11. En PowerApps Studio observe que hay un control **ModelDrivenFormIntegration** especial en el panel izquierdo. Este control es responsable de llevar datos contextuales del formulario controlado por modelos del host a la aplicación incrustada de lienzo.
12. Seleccione el control **Gallery1** y observe que la propiedad **Elementos** está establecida en **ModelDrivenFormIntegration.Data**.
      > [!NOTE]
      > ModelDrivenFormIntegration.Data es una lista de registros. En este ejemplo sólo tiene un registro. Para hacer referencia directamente el registro puede usar Primera función. Ejemplo: *First(ModelDrivenFormIntegration.Data).Name*.
13. En el panel de propiedades en la derecha, junto a **Campos**, seleccione **Editar**.
14. En el panel de datos, cambie el campo asignado al control **Title1** a **Nombre** u otro campo que tenga datos.
15. Observe que la galería muestra datos que se le pasan desde el formulario controlado por modelos a través del control de ModelDrivenFormIntegration. Cierra el panel de datos.
16. Seleccione la pestaña **Archivo** y, a continuación, seleccione **Configuración de la aplicación**.
17. En la pestaña **Configuración avanzada** , en la sección **Características experimentales** , establezca **Habilitar la experiencia de usuario de incrustar aplicaciones** en **Activar**.
18. Seleccione **Guardar**. 
19. Seleccione la pestaña **La nube**. Proporcione un nombre único para la aplicación y después seleccione **Guardar** en la parte inferior derecha. Tenga en cuenta lo siguiente: 
    -  Guardar una aplicación por primera vez publica automáticamente la aplicación.
      -  En las operaciones de guardar posteriores, seleccione **Publicar** y después seleccione **Publicar esta versión** para que los cambios pasen a estar disponibles.
20. En el menú, seleccione **Atrás** y seleccione la ficha del explorador que tiene el editor de formularios abierto. Observe que la propiedad **Identificador de la aplicación** del control de apliaciones de lienzo ahora tiene un valor automáticamente rellenado. Tenga en cuenta lo siguiente: 
    -   El editor de formularios tiene un vínculo directo con PowerApps Studio que se abrió en otra ficha del explorador en un paso anterior.
    -   El editor de formularios “escucha” para recibir el **Identificador de la aplicación** que se le envía.
    -   El **Identificador de la aplicación** se envía al editor de formularios cuando se guarda la aplicación.
21. En el cuadro de diálogo **Propiedades de campo** , seleccione la pestaña **Mostrar** .
22. Desactive **Mostrar etiqueta** en el formulario y seleccione **Aceptar**.
    -   Si ya tiene una aplicación de lienzo insertada en este formulario se muestra un mensaje que indica “solo una aplicación de lienzo se puede habilitar en un formulario.” Para agregar la aplicación nueva de lienzo primero debe [deshabilitar la aplicación incrustada actual de lienzo](embedded-canvas-app-guidelines.md#disable-an-embedded-canvas-app). Después, [habilite la nueva aplicación incrustada de lienzo](embedded-canvas-app-guidelines.md#enable-an-embedded-canvas-app).
23. En la pestaña **Inicio**, seleccione **Guardar** y, después, seleccione **Publicar**.

Tras agregar una aplicación incrustada de lienzo al formulario controlado por modelos, comparta la aplicación incrustada de lienzo con otros usuarios. Más información: [Compartir una aplicación incrustada de lienzo](share-embedded-canvas-app.md).

Cuando los usuarios abren una aplicación controlada por modelos (solo interfaz unificada) que incluya el formulario que ha modificado ven la aplicación incrustada de lienzo en el formulario. Cambiar el registro mostrado en el formulario principal cambia el contexto de datos que se pasa al formulario y la aplicación incrustada se actualiza para mostrar los datos relevantes.

Este tema le ha mostrado cómo empezar a insertar una aplicación de lienzo en un formulario controlado por modelos. Puede personalizar la aplicación incrustada de lienzo aún más para conectar datos e incorporarlos desde diversos orígenes de datos. Use las funciones de filtro, Buscar y búsqueda y el contexto pasados desde el formulario controlado por modelos de host para filtrar o para encontrar registros específicos en esos orígenes de datos. Use el editor de aplicaciones de lienzo WYSIWYG para diseñar fácilmente la interfaz para que cumpla los requisitos.

## <a name="see-also"></a>Vea también
[Insertar una aplicación de lienzo en un formulario controlado por modelos](embed-canvas-app-in-form.md) <br />
[Pasar una lista de registros relacionados como contexto de datos a una aplicación incrustada de lienzo](pass-related-embedded-canvas-app.md) <br />
[Compartir una aplicación incrustada de lienzo](share-embedded-canvas-app.md) <br />
[Directrices acerca de cómo trabajar con aplicaciones de lienzo incrustadas](embedded-canvas-app-guidelines.md)
