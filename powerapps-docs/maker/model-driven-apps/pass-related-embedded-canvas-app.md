---
title: Pasar una lista de registros relacionados como contexto de datos con una aplicación incrustada de lienzo | MicrosoftDocs
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
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8f359a11f55008d6f2c19575872decdd43b09e27
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "2873834"
---
# <a name="pass-a-list-of-related-records-as-data-context-to-an-embedded-canvas-app"></a>Pasar una lista de registros relacionados como contexto de datos a una aplicación incrustada de lienzo
> [!IMPORTANT]
> Las aplicaciones de lienzo incrustadas en formularios basados en modelos ahora están fuera de vista previa y disponibles en general. Los pasos que aparecen a continuación están obsoletos y son aplicables únicamente a la versión pública de vista previa de las aplicaciones de lienzo insertadas en los formularios basados en modelos.
> Para la lista actualizada de pasos para la última versión, vea: [Agregar una aplicación de lienzo incrustada en un formulario basado en modelos](embedded-canvas-app-add-classic-designer.md)

En este tema se explica cómo agregar una aplicación incrustada de lienzo y pasar una lista de registros relacionados al registro actual (formulario principal) como contexto de datos a la aplicación incrustada de lienzo.

Digamos que desea agregar una aplicación incrustada de lienzo en el formulario principal de una cuenta y pasar una lista de contactos relacionados con el registro de cuenta actual a la aplicación incrustada de lienzo. Para ello, siga estos pasos:

1.  Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) y abra el editor de formularios para un formulario principal de una entidad, como la entidad contable.
2.  Seleccione la sección del formulario donde desea que aparezca la aplicación incrustada de lienzo.
3.  Con la sección seleccionada, en la ficha **Insertar**, en el grupo **Control**, haga clic en **Subcuadrícula**.
4.  En el cuadro de diálogo **Establecimiento de propiedades**, seleccione la pestaña **Mostrar** y, a continuación en el cuadro **Nombre** escriba un nombre para el control de cuadrícula.
5.  En la sección **origen de datos** , seleccione **Entidad** y la **Vista predeterminada** correspondientes a la lista de registros que desea que pasar como el contexto de datos para la aplicación incrustada de lienzo.
6. Seleccione la pestaña **Controles** y seleccione **Agregar control...**.
7. En el cuadro de diálogo **Agregar control** , en la lista de controles disponibles, seleccione **Aplicación de lienzo** y después seleccione **Agregar**.
8. En el cuadro de diálogo **Establecer propiedades**, en la lista de controles seleccione **Aplicación de lienzo** y seleccione la opción **Web**.
9. En la sección debajo de la lista de controles, consulte la lista de propiedades correspondiente al control de aplicaciones de lienzo y tenga en cuenta lo siguiente:
     - La propiedad **Nombre de entidad** especifica la entidad que proporcionará los datos a la aplicación incrustada de lienzo. Se establecerá en la entidad seleccionada anteriormente.
         -  Aunque esta propiedad parece cambiable, cambiarla no tendrá ningún efecto en la aplicación incrustada de lienzo. Está previsto que solo sirva como referencia para usted.
     -  La propiedad **Ver nombre** especifica la vista de la entidad que se usará para filtrar los datos proporcionados a la aplicación incrustada de lienzo. Se establecerá en la **Vista predeterminada** seleccionada anteriormente.
         -  Los datos (campos y valores) enviados a la aplicación incrustada de lienzo en tiempo de ejecución están determinados en función de esta vista. Use solo los campos de la aplicación de lienzo incluidos en la vista o agréguelos a la vista si es necesario. Todos los campos no incluidos en la vista muestran valores vacíos en tiempo de ejecución.
         -  Los criterios de filtro para una vista no se usan en el momento de la creación. Por tanto, los datos que ve al crear aplicaciones incrustadas de lienzo no están filtrados, son simplemente una lista de los pocos registros superiores a los que tiene acceso. En el tiempo de ejecución, los criterios de filtrado de la vista se aplican como se prevé, por tanto, los usuarios solo ven los datos relevantes.
     -  La propiedad **Identificador de la aplicación** especifica el identificador de la aplicación incrustada de lienzo. Se genera y rellena automáticamente en su lugar cuando crea la aplicación de lienzo.
         -  Tenga en cuenta que, cualquier cambio efectuado en el valor Identificador de la aplicación rompe el vínculo entre el formulario controlado por modelos y la aplicación incrustada de lienzo.
10. Seleccione el botón **Personalizar** para crear o editar la aplicación de lienzo. Esto abre Power Apps Studio en una nueva pestaña del explorador.
     > [!IMPORTANT]
     > Si abrir Power Apps Studio está bloqueado debido a un bloqueador de elementos emergentes de explorador web, debe habilitar el sitio de make.powerapps.com o temporalmente deshabilitar el bloqueador de elementos emergentes y después seleccionar **Personalizar** de nuevo. 
11. En Power Apps Studio, observe que hay un control **ModelDrivenFormIntegration** en el panel izquierdo. Este control es responsable de llevar datos contextuales del formulario controlado por modelos del host a la aplicación incrustada de lienzo. 
12. Seleccione el control **Gallery1** y observe que la propiedad **Elementos** está establecida en **ModelDrivenFormIntegration.Data**.
13. En el panel de propiedades en la derecha, junto a **Campos**, seleccione **Editar**.
14. En el panel de datos, cambie el campo asignado al control **Title1** por **Nombre completo** u otro campo que tenga datos.
15. Observe que la galería muestra datos que se le pasan desde el formulario controlado por modelos a través del control **ModelDrivenFormIntegration**. Cierra el panel de datos.
16. Seleccione la pestaña **Archivo** y, a continuación, seleccione **Configuración de la aplicación**.
17. En la pestaña **Configuración avanzada** , en la sección **Características experimentales** , establezca **Habilitar la experiencia de usuario de incrustar aplicaciones** en **Activar**.
18. Seleccione **Guardar**. 
19. Seleccione la pestaña **La nube**, proporcione un nombre único para la aplicación y después seleccione **Guardar** en la parte inferior derecha. Tenga en cuenta lo siguiente: 
    -  Guardar una aplicación por primera vez publica automáticamente la aplicación. 
      -  En las operaciones de guardar posteriores, tiene que seleccionar **Publicar** y después **Publicar esta versión** para que los cambios pasen a estar disponibles.
20. Seleccione **Atrás** y seleccione la ficha del explorador que tiene el editor de formularios abierto. 
21. Observe que la propiedad **Identificador de la aplicación** del control de **aplicaciones de lienzo** ahora tiene un valor automáticamente rellenado. Tenga en cuenta lo siguiente: 
     -  El editor de formularios tiene un vínculo directo con Power Apps Studio que se abrió en otra pestaña del explorador en un paso anterior.
     -  El editor de formularios ha estado escuchando para recibir el Identificador de la aplicación que se le va a enviar.
     -  El identificador de la Aplicación se le suministró cuando la aplicación se guardó.
22. En el cuadro de diálogo **Establecer las propiedades** , seleccione la pestaña **Mostrar** , desactive **Mostrar etiqueta en el formulario**y, a continuación seleccione **Aceptar**.
     - Si ya tiene una aplicación de lienzo insertada en este formulario se muestra un mensaje que indica “solo una aplicación de lienzo se puede habilitar en un formulario.” Para agregar la aplicación nueva de lienzo primero debe [deshabilitar la aplicación incrustada actual de lienzo](embedded-canvas-app-guidelines.md#disable-an-embedded-canvas-app). Después, [habilite la nueva aplicación incrustada de lienzo](embedded-canvas-app-guidelines.md#enable-an-embedded-canvas-app).
23. En la pestaña **Inicio**, seleccione **Guardar** y, después, seleccione **Publicar**.

Tras agregar una aplicación incrustada de lienzo al formulario controlado por modelos, comparta la aplicación incrustada de lienzo con otros usuarios. Más información: [Compartir una aplicación incrustada de lienzo](share-embedded-canvas-app.md).

Cuando los usuarios abren una aplicación controlada por modelos (solo interfaz unificada) que incluya el formulario que ha modificado ven la aplicación incrustada de lienzo en el formulario. Cambiar el registro mostrado en el formulario principal cambia el contexto de datos que se pasa al formulario y la aplicación incrustada se actualiza para mostrar los datos relevantes.

Este tema le ha mostrado cómo empezar a insertar una aplicación de lienzo en el formulario controlado por modelos. Puede personalizar la aplicación incrustada de lienzo aún más para conectar datos e incorporarlos desde diversos orígenes de datos. Use las funciones de filtro, Buscar y búsqueda y el contexto pasados desde el formulario controlado por modelos de host para filtrar o para encontrar registros específicos en esos orígenes de datos. Use el editor de aplicaciones de lienzo WYSIWYG para diseñar fácilmente la interfaz para que cumpla los requisitos.

## <a name="see-also"></a>Vea también
[Insertar una aplicación de lienzo en un formulario controlado por modelos](embed-canvas-app-in-form.md) <br />
[Agregar una aplicación de lienzo incrustada en un formulario basado en modelos](embedded-canvas-app-add-classic-designer.md) <br />
[Editar una aplicación de lienzo incrustada en un formulario basado en modelos](embedded-canvas-app-edit-classic-designer.md) <br />
[Personalizar el tamaño y orientación de la pantalla de una aplicación de lienzo insertada en un formulario basado en modelos](embedded-canvas-app-customize-screen.md) <br />
[Realice acciones predefinidas en el formulario de host desde una aplicación de lienzo insertada](embedded-canvas-app-actions.md) <br />
[Propiedades y acciones del control ModelDrivenFormIntegration](embedded-canvas-app-properties-actions.md) <br />
[Compartir una aplicación incrustada de lienzo](share-embedded-canvas-app.md) <br />
[Directrices acerca de cómo trabajar con aplicaciones de lienzo incrustadas](embedded-canvas-app-guidelines.md) <br />
[Migrar aplicaciones de lienzo insertadas en formularios basados en modelos creados mediante la versión de vista previa pública a la más reciente](embedded-canvas-app-migrate-from-preview.md) <br />
