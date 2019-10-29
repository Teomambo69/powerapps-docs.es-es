---
title: Crear y administrar páginas web | Microsoft Docs
description: Instrucciones para crear y administrar páginas web en el portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b62f6a811d2f2e6c5218ef601f18d69357d15ba9
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977022"
---
# <a name="create-and-manage-webpages"></a>Creación y administración de páginas web

Una página web es un documento que se identifica mediante una dirección URL única en un sitio Web. Es uno de los objetos principales del sitio web y crea una jerarquía del sitio web a través de relaciones de elementos primarios y secundarios con otras páginas Web.

> [!NOTE]
> Si personaliza el portal con PowerApps portales Studio, los usuarios del sitio web observarán un impacto en el rendimiento. Le recomendamos que realice los cambios durante las horas de poca actividad en un portal activo.

## <a name="create-webpage"></a>Crear página web

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en PowerApps Portals Studio.  

2.  En la barra de comandos, seleccione **nueva página** y elija una página en **diseños** o **diseños fijos**.

    > [!div class=mx-imgBorder]
    > ![crear una nueva página web](media/create-webpage.png "crear una nueva página web")

    > [!NOTE]
    > - La creación de una página con **diseños** le ofrece la flexibilidad de editar la página completa. **Diseños fijos** contiene las plantillas de página que se instalan como parte del aprovisionamiento del portal y las plantillas de página personalizadas que se crean mediante la [aplicación administración del portal](configure/configure-portal.md).
    > - En el caso de las páginas que se van a crear con la opción **layouts** , se instalará una nueva plantilla de página de **plantilla de Studio predeterminada** .

3.  En el panel Propiedades, en el lado derecho de la pantalla, escriba la siguiente información:

    - **Nombre**: nombre de la página. Este valor también se usa como título de la página.

    - **URL parcial**: el segmento de ruta de acceso de dirección URL que se usa para crear la dirección URL del portal de esta página.

    - **Plantilla**: plantilla de página que se usa para representar esta página en el portal. Si es necesario, puede elegir otra plantilla de la lista.

        > [!div class=mx-imgBorder]
        > Propiedades ![de página web](media/webpage-props.png "") propiedades de página web

Las páginas web que cree se agregan y su jerarquía se muestran en el panel **páginas** . Para ver el panel **páginas** **, seleccione páginas** ![iconos icono](media/pages-icon.png "páginas") icono en el toolbelt en el lado izquierdo de la pantalla.  

Supongamos que ha creado algunas páginas web para el portal. La jerarquía de páginas tiene el siguiente aspecto:

> [!div class=mx-imgBorder]
> ![](media/pages-pane.png "Panel páginas") del panel páginas  

El menú principal del sitio web se crea automáticamente en función de la jerarquía de las páginas Web. Se denomina menú **predeterminado** . También puede crear un menú personalizado para mostrarlo en el sitio Web. Más información: [Agregar un menú personalizado](compose-page.md#add-a-custom-menu)

> [!div class=mx-imgBorder]
> (media/website-navigation.png "navegación del sitio web") de ![navegación de sitios web]

Si está trabajando con un portal creado con el entorno de Dynamics 365 y desea que el menú sea el mismo que el de la jerarquía de páginas, debe seleccionar **predeterminado** en la lista de **menús de navegación** .

> [!div class=mx-imgBorder]
> Menú de ![navegación predeterminado](media/navigation-menu-default.png "menú") de navegación predeterminado

## <a name="manage-webpage"></a>Administrar Página Web

1.  [Edite el portal](manage-existing-portals.md#edit) para abrirlo en PowerApps Portals Studio.  

2.  En el panel de la izquierda de la pantalla **, seleccione páginas** de ![iconos]icono(media/pages-icon.png "páginas") del toolbelt.  

3.  Mantenga el puntero sobre la página que desea administrar y seleccione el botón de **puntos suspensivos** (...) de la página web que desea administrar. Como alternativa. puede hacer clic con el botón secundario en la página que desea administrar.

4.  Seleccione la acción necesaria en el menú contextual:

    - **Ocultar en el menú predeterminado**: oculte que la página se muestre en el mapa del sitio mediante el menú predeterminado.

    - **Mostrar en el menú predeterminado**: muestra la página en el mapa del sitio a través del menú predeterminado.

    - **Agregar una página secundaria**: agregar una página secundaria a la página seleccionada. La página secundaria hereda la plantilla de página de su página primaria.

    - **Establecer como página principal**: establezca la página como la Página principal. La dirección URL de la nueva página principal se establece en la raíz del sitio web y la dirección URL de la página antigua se actualiza en consecuencia.

    - **Subir**: mueve la página hacia arriba en la jerarquía.

    - **Bajar**: mueve la página hacia abajo en la jerarquía.

        > [!NOTE]
        > El movimiento de una página hacia arriba o hacia abajo se admite entre las páginas del mismo nivel.

    - **Promocionar subpágina**: reduce la sangría y convierte la página secundaria en el nivel de la página anterior de la jerarquía.

    - **Crear subpágina**: aumente la sangría y convierta la página en una página secundaria de la página anterior de la jerarquía.

    - **Eliminar**: elimina la página.

        > [!div class=mx-imgBorder]
        > páginas web ![administrar opciones](media/webpage-manage-options.png "Página Web administrar opciones")  





