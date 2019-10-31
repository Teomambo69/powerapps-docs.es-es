---
title: Creación y administración de las páginas web | Microsoft Docs
description: Instrucciones para crear y administrar páginas web en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 09/16/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="create-and-manage-webpages"></a>Crear y administrar páginas web

[!include[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Una página web es un documento que se identifica mediante una dirección URL única en una página web. Es uno de los objetos básicos de la página web y construye una jerarquía de la página web a través de relaciones primarias y secundarias a otras páginas web.

> [!NOTE]
> Si personaliza el portal usando el diseñador del portal, los usuarios del sitio web observarían un impacto en el rendimiento. Se recomienda realizar los cambios en horas de poca actividad en un portal en directo.

## <a name="create-webpage"></a>Crear página web

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en el diseñador del portal.  

2.  En la barra de comandos, seleccione **Nueva página** y seleccione la plantilla de página.

    > [!div class=mx-imgBorder]
    > ![crear una nueva página web](media/create-webpage.png "Crear una nueva página web")

3.  En el panel de propiedades de la derecha de la pantalla, introduzca la siguiente información:

    - **Nombre**: Nombre de la página. Este valor también se usa como el título de la página.

    - **Dirección URL parcial**: El segmento de dirección URL utilizado para crear la dirección URL de portal de esta página.

    - **Plantilla**: La plantilla de página que se usará para representar esta página en el portal. Si procede, puede elegir otra plantilla de la lista.

        > [!div class=mx-imgBorder]
        > ![propiedades de página web](media/webpage-props.png "Propiedades de página web")

Las páginas web que crea se agregan y su jerarquía se muestra en el panel **Páginas**. Para ver el panel **Páginas**, seleccione **Páginas** ![icono de páginas](media/pages-icon.png "Icono de páginas")”) del toolbelt en el lateral izquierdo de la pantalla.  

Supongamos que ha creado algunas páginas web para el portal. La jerarquía de páginas es como se indica a continuación:

> [!div class=mx-imgBorder]
> ![panel de páginas](media/pages-pane.png "Panel de páginas")  

El menú principal en el sitio web se crea automáticamente basándose en la jerarquía de las páginas web. Se llama menú **Predeterminado**. También puede crear un menú personalizado para mostrar en la página web. Más información: [Agregar un menú personalizado](compose-page.md#add-a-custom-menu)

> [!div class=mx-imgBorder]
> ![navegación de sitio web](media/website-navigation.png "Navegación de sitio web")

Si trabaja con portales de Dynamics 365, y desea que el menú sea el mismo que la jerarquía de páginas, deberá seleccionar **Predeterminado** en la lista **Menú de exploración**.

> [!div class=mx-imgBorder]
> ![Menú de exploración predeterminado](media/navigation-menu-default.png "Menú de exploración predeterminado")

## <a name="manage-webpage"></a>Administrar página web

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en el diseñador del portal.  

2.  Seleccione **Páginas** ![icono de páginas](media/pages-icon.png "Icono de páginas") del toolbelt en el lateral izquierdo de la pantalla.  

3.  Desplácese sobre la página que desea administrar y seleccione el botón **Puntos suspensivos** (…) para la página web que desea administrar. Alternativamente puede hacer clic con el botón secundario en la página que desea administrar.

4.  Seleccione la acción requerida en el menú contextual:

    - **Ocultar en menú predeterminado**: Oculta la página en el mapa del sitio a través del menú predeterminado.

    - **Mostrar en menú predeterminado**: Muestra la página en el mapa del sitio a través del menú predeterminado.

    - **Agregar una página secundaria**: Agrega una página secundaria a la página seleccionada. La página secundaria hereda la plantilla de página de la página principal.

    - **Establecer como página principal**: Establece la página como página principal. La dirección URL de la nueva página principal se establece como la raíz de la página web y la dirección URL de la antigua página se actualiza en consecuencia.

    - **Subir**: Sube la página en la jerarquía.

    - **Bajar**: Baja la página en la jerarquía.

        > [!NOTE]
        > Subir o bajar una página es posible entre las páginas del mismo nivel.

    - **Promover subpágina**: Reduce la sangría y convierte la página secundaria en el nivel de la página anterior de la jerarquía.

    - **Crear subpágina**: Aumenta la sangría y convierte la página en secundaria de la página anterior de la jerarquía.

    - **Eliminar**: Eliminación de la página.

        > [!div class=mx-imgBorder]
        > ![opciones de administración de página web](media/webpage-manage-options.png "Opciones de administración de página web")  





