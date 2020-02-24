---
title: Habilitar modo de mantenimiento para un portal | MicrosoftDocs
description: Aprenda a habilitar el modo de mantenimiento con el portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/11/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 2731c421b9c8c7bc509352dc050ffc133451bc83
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978081"
---
# <a name="maintenance-mode-for-a-portal"></a>Modo de mantenimiento para un portal

Puede haber momentos en que la página web esté en mantenimiento programado o no está funcionando debido a interrupción temporal. Cuando un cliente tiene acceso a la página web durante mantenimiento, puede experimentar un comportamiento impredecible y falta de disponibilidad intermitente. 

Como administrador del portal, puede configurar el portal para mostrar un mensaje adecuado a los clientes cada vez que una actividad de mantenimiento se produzca (por ejemplo, "Se están actualizando paquetes de la solución.") Puede aprovechar esta capacidad habilitando el modo de mantenimiento en el portal. Cuando se habilita el modo de mantenimiento, se muestra un mensaje y los clientes no pueden examinar páginas web excepto la página `<portal URL>/_services/about`.

> [!div class=mx-imgBorder]
> ![Página del modo de mantenimiento predeterminado](../media/default-maint-page.png "Página del modo de mantenimiento predeterminado")

## <a name="enable-maintenance-mode"></a>Habilitar modo de mantenimiento

Puede habilitar el modo de mantenimiento en el portal para proporcionar un mensaje consistente, en lugar de tratar un comportamiento impredecible cuando la página web esté en mantenimiento programado. Esto le proporcionará una mejor experiencia a los usuarios del portal.

1. Abra [Centro de administración de Portales de Power Apps](admin-overview.md).

3. Vaya a **Acciones del portal** > **Habilitar modo de mantenimiento**.

    > [!div class=mx-imgBorder]
    > ![Habilitar modo de mantenimiento](../media/enable-maint-mode-button.png "Habilitar modo de mantenimiento")

4. En la ventana **Habilitar modo de mantenimiento**, especifique los valores siguientes:
    - **Seleccione la página que se usará cuando el modo de mantenimiento esté habilitado**: Seleccione uno de los siguientes valores:

        - **Página predeterminada**: Seleccione esta opción si desea que la página predeterminada se muestra cuando se habilite el modo de mantenimiento. Esta opción se encuentra seleccionada de forma predeterminada.

        - **Página personalizada**: Seleccione esta opción si desea que la página HTML personalizada se muestra cuando se habilite el modo de mantenimiento.

    - **Dirección URL de página personalizada**: Este campo se habilita solo cuando selecciona la opción para mostrar una página HTML personalizada. Debe asegurarse de que la dirección URL de la página que proporciona es accesible públicamente. Si no se puede acceder a la página HTML especificada, la página predeterminada se muestra con una nota a los administradores.

        > [!NOTE]
        > La página de mantenimiento personalizado usa IFrame para mostrar la página. Por lo tanto, la página no debe contener el encabezado de respuesta `x-frame-options:SAMEORIGIN`. de lo contrario la página no se cargará.

5. Seleccione **Habilitar**. Mientras está habilitado el modo de mantenimiento, se reinicia el portal y no está disponible durante unos minutos. 

    > [!div class=mx-imgBorder]
    > ![Habilitar configuración del modo de mantenimiento](../media/enable-maint-mode.png "Habilitar configuración del modo de mantenimiento")

## <a name="configure-or-disable-maintenance-mode"></a>Configurar o deshabilitar el modo de mantenimiento

Después de habilitar el modo de mantenimiento para el portal, puede actualizar la configuración del modo de mantenimiento y seleccionar una página diferente.

También puede elegir deshabilitar el modo de mantenimiento en el portal cuando el mantenimiento programado de la página web se completa. Los usuarios del portal ahora pueden explorar y obtener acceso a todas las páginas web como de costumbre.

1. Abra [Centro de administración de Portales de Power Apps](admin-overview.md).

2. Vaya a **Acciones del portal** > **Configurar o deshabilitar modo de mantenimiento**.

    > [!div class=mx-imgBorder]
    > ![Configurar modo de mantenimiento](../media/configure-maint-mode-button.png "Configurar modo de mantenimiento")

3. Modificar la configuración como sea necesario y seleccione **Actualizar**. Por ejemplo, es posible que elija mostrar la página predeterminada si ha seleccionado la opción de mostrar la página personalizada anteriormente.

4. Para deshabilitar el modo de mantenimiento, seleccione **Deshabilitar**. Mientras se actualizado o deshabilitado el modo de mantenimiento, se reinicia el portal y no está disponible durante unos minutos.

    > [!div class=mx-imgBorder]
    > ![Actualizar configuración del modo de mantenimiento](../media/configure-maint-mode.png "Actualizar configuración del modo de mantenimiento")

