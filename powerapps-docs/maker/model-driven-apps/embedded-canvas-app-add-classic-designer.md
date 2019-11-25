---
title: Agregar una aplicación de lienzo incrustada en un formulario basado en modelos | MicrosoftDocs
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
ms.openlocfilehash: d6881aaa3a55f16324e5d995e70be1e186a816bf
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759400"
---
# <a name="add-an-embedded-canvas-app-on-a-model-driven-form"></a>Agregar una aplicación de lienzo incrustada en un formulario basado en modelos
En este tema se explica cómo insertar una nueva aplicación de lienzo en un formulario basado en modelos.

Imagine que desee crear una nueva aplicación de lienzo e incrustarla en un formulario principal para la entidad de cuentas. Para ello, siga estos pasos: 

1.  Inicie sesión en [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
2.  [Creación o edición del formulario principal](create-and-edit-forms.md) de una entidad, entidad Cuentas en nuestro ejemplo. 
3.  En la barra de comandos, seleccione **Cambiar a clásico** para abrir el formulario en el diseñador de formularios clásico.
4.  En el diseñador de formularios clásicos, seleccione la sección del formulario donde desea que aparezca la aplicación incrustada de lienzo.
5.  Usando el panel de campos, agregue un campo obligatorio, como **Nombre de cuenta**.
      > [!IMPORTANT]
      > Use siempre un campo obligatorio que siempre tiene garantizado un valor. Si el campo no tiene un valor, su aplicación incrustada de lienzo no se actualizará como respuesta a cualquier cambio en los datos del formulario controlado por modelos de host.
6.  Con este campo seleccionado, en la pestaña **Inicio**, en el grupo **Editar**, haga clic en **Cambiar propiedades**.
7.  En el cuadro de diálogo **Propiedades de campo** , seleccione la pestaña **Controles** .
8.  En la pestaña **Controles** seleccione **Agregar control**.
9.  En el cuadro de diálogo **Agregar control** , en la lista de controles disponibles, seleccione **Aplicación de lienzo** y después seleccione **Agregar**.
10. En el cuadro de diálogo **Propiedades de campo**, en la lista de controles seleccione **Aplicación de lienzo** y seleccione la opción **Web**.
11. En la sección debajo de la lista de controles, la lista de propiedades disponible para el control de aplicaciones de lienzo se muestra.
     - La propiedad **Nombre de entidad** especifica la entidad que proporcionará los datos a la aplicación incrustada de lienzo. Se establecerá en la entidad que contiene el campo que se agregó en un paso anterior.
         - Tenga en cuenta que, aunque esta propiedad parece cambiable, cambiarla no tendrá ningún efecto en la aplicación incrustada de lienzo. Está previsto que solo sirva como referencia para usted.
     - La propiedad **Identificador de la aplicación** especifica el identificador de la aplicación incrustada de lienzo. Se generará y rellenará automáticamente en su lugar cuando se cree la aplicación de lienzo.
         - Tenga en cuenta que, los cambios efectuados en el valor **Identificador de la aplicación** rompen el vínculo entre el formulario controlado por modelos y la aplicación incrustada de lienzo.
12. Seleccione **Personalizar** para crear o editar la aplicación de lienzo. Esto abre PowerApps Studio en una nueva pestaña.
       > [!NOTE]
       > Si abrir PowerApps Studio está bloqueado debido a un bloqueador de elementos emergentes de explorador web, debe habilitar el sitio de make.powerapps.com o temporalmente deshabilitar el bloqueador de elementos emergentes y después seleccionar **Personalizar** de nuevo.
13. En PowerApps Studio, observe que hay un control **ModelDrivenFormIntegration** especial en el panel izquierdo. Este control es responsable de llevar datos contextuales del formulario controlado por modelos del host a la aplicación incrustada de lienzo.
14. Observe que un [control de formulario de la aplicación de lienzo](../canvas-apps/controls/control-form-detail.md) se agregó automáticamente a la aplicación de lienzo incrustada y muestra los datos que se le pasan desde el formulario basado en modelos de host mediante el control de ModelDrivenFormIntegration. 
15. Seleccione la pestaña **Vista** y, a continuación seleccione **Orígenes de datos**. Observe que un origen de datos para la entidad principal del formulario basado en modelos host, Cuentas en este caso, se agregó automáticamente a la aplicación de lienzo incrustada.
16. Seleccione el control **Form1** y observe que la propiedad **DataSource** está establecida en **Cuentas**.
17. Con el control **Form1** aún seleccionado, observe que la propiedad **Item** está establecida en **ModelDrivenFormIntegration.Item**.
    > [!NOTE]
    > La aplicación de lienzo incrustada tiene acceso total al registro desde el formulario basado en modelos host mediante ModelDrivenFormIntegration.Item. Por ejemplo, para obtener el valor de un campo con el nombre **accountnumber** y el nombre para mostrar **Número de cuenta**, puede usar **ModelDrivenFormIntegration.Item.accountnumber** o **ModelDrivenFormIntegration.Item.'Número de cuenta'**.
18. En el panel de propiedades en la derecha, junto a **Campos**, seleccione **Editar campos**.
19. Seleccione **+ Agregar campo** para agregar otro campo al formulario de aplicación de lienzo o para reorganizar campos existentes mediante arrastrar y colocar. Cierre el panel de datos cuando termine de agregar y reorganizar campos.
20. Seleccione la pestaña **Archivo** y, a continuación, seleccione **Guardar**.
21. Seleccione la pestaña **La nube**. Proporcione un nombre único para la aplicación y después seleccione **Guardar** en la parte inferior derecha. Tenga en cuenta lo siguiente: 
    -  Guardar una aplicación por primera vez publica automáticamente la aplicación.
      -  En las operaciones de guardar posteriores, seleccione **Publicar** y después seleccione **Publicar esta versión** para que los cambios pasen a estar disponibles.
22. En el menú, seleccione **Atrás**.
23. Seleccione la pestaña del explorador que tiene el diseñador de formularios clásico abierto. Observe que la propiedad **Identificador de la aplicación** del control de apliaciones de lienzo ahora tiene un valor automáticamente rellenado.
    > [!NOTE]
    > - El diseñador de formularios tiene un vínculo directo con PowerApps Studio que se abrió en otra pestaña del explorador en un paso anterior.
    > - El diseñador de formularios escucha para recibir el Identificador de la aplicación que se le envía. 
    > - El Identificador de la aplicación se envía al diseñador de formularios cuando se guarda la aplicación.
24. En el cuadro de diálogo **Propiedades de campo** , seleccione la pestaña **Mostrar** .
25. Desactive **Mostrar etiqueta** en el formulario y seleccione **Aceptar**.
    -   Si ya tiene una aplicación de lienzo insertada en este formulario se muestra un mensaje que indica “solo una aplicación de lienzo se puede habilitar en un formulario.” Para agregar la aplicación nueva de lienzo primero debe [deshabilitar la aplicación incrustada actual de lienzo](embedded-canvas-app-guidelines.md#disable-an-embedded-canvas-app). Después, [habilite la nueva aplicación incrustada de lienzo](embedded-canvas-app-guidelines.md#enable-an-embedded-canvas-app).
26. En la pestaña **Inicio**, seleccione **Guardar** y, después, seleccione **Publicar**.

Tras agregar una aplicación incrustada de lienzo al formulario controlado por modelos, comparta la aplicación incrustada de lienzo con otros usuarios. Más información: [Compartir una aplicación incrustada de lienzo](share-embedded-canvas-app.md).

Cuando los usuarios abren una aplicación controlada por modelos (solo interfaz unificada) que incluya el formulario que ha modificado ven la aplicación incrustada de lienzo en el formulario. Cambiar el registro mostrado en el formulario principal cambia el contexto de datos que se pasa al formulario y la aplicación incrustada se actualiza para mostrar los datos relevantes.

Este tema le ha mostrado cómo empezar a insertar una aplicación de lienzo en un formulario controlado por modelos. Puede personalizar la aplicación incrustada de lienzo aún más para conectar datos e incorporarlos desde diversos orígenes de datos. Use las funciones de filtro, Buscar y búsqueda y el contexto pasados desde el formulario controlado por modelos de host para filtrar o para encontrar registros específicos en esos orígenes de datos. Use el editor de aplicaciones de lienzo WYSIWYG para diseñar fácilmente la interfaz para que cumpla los requisitos.

## <a name="see-also"></a>Vea también
[Insertar una aplicación de lienzo en un formulario controlado por modelos](embed-canvas-app-in-form.md) <br />
[Editar una aplicación de lienzo incrustada en un formulario basado en modelos](embedded-canvas-app-edit-classic-designer.md) <br />
[Personalizar el tamaño y orientación de la pantalla de una aplicación de lienzo insertada en un formulario basado en modelos](embedded-canvas-app-customize-screen.md) <br />
[Realice acciones predefinidas en el formulario de host desde una aplicación de lienzo insertada](embedded-canvas-app-actions.md) <br />
[Propiedades y acciones del control ModelDrivenFormIntegration](embedded-canvas-app-properties-actions.md) <br />
[Compartir una aplicación incrustada de lienzo](share-embedded-canvas-app.md) <br />
[Directrices acerca de cómo trabajar con aplicaciones de lienzo incrustadas](embedded-canvas-app-guidelines.md) <br />
[Migrar aplicaciones de lienzo insertadas en formularios basados en modelos creados mediante la versión de vista previa pública a la más reciente](embedded-canvas-app-migrate-from-preview.md) <br />
