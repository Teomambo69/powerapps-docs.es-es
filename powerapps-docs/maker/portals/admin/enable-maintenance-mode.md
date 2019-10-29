---
title: Habilitar el modo de mantenimiento para un portal | MicrosoftDocs
description: Obtenga información acerca de cómo habilitar el modo de mantenimiento con el portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: e53380c39257645e9056a271226b6f7ef8c8c721
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976079"
---
# <a name="maintenance-mode-for-a-portal"></a>Modo de mantenimiento para un portal

Puede haber ocasiones en las que el sitio web esté bajo mantenimiento programado o que esté inactivo debido a una interrupción temporal. Cuando un cliente tiene acceso al sitio web durante el mantenimiento, puede experimentarse un comportamiento impredecible y una falta de disponibilidad intermitente. 

Como administrador del portal, puede configurar el portal para mostrar un mensaje adecuado a los clientes cada vez que se esté realizando una actividad de mantenimiento (por ejemplo, "se están actualizando los paquetes de la solución"). Puede aprovechar esta capacidad habilitando el modo de mantenimiento en el portal. Cuando el modo de mantenimiento está habilitado, se muestra un mensaje y los clientes tienen restringido el examen de las páginas web, excepto la página `<portal URL>/_services/about`.

> [!div class=mx-imgBorder]
> Página modo de mantenimiento ![predeterminado]página(../media/default-maint-page.png "modo de mantenimiento predeterminado")

## <a name="enable-maintenance-mode"></a>Activación del modo de mantenimiento

Puede habilitar el modo de mantenimiento en el portal para proporcionar un mensaje coherente, en lugar de tratar con un comportamiento imprevisible cuando el sitio web está bajo mantenimiento programado. Esto proporcionará una mejor experiencia para los usuarios del portal.

1. Abra el [centro de administración de portales de PowerApps](admin-overview.md).

3. Vaya a **acciones del Portal** > **Habilitar el modo de mantenimiento**.

    > [!div class=mx-imgBorder]
    > ![Habilitar]modo de mantenimiento(../media/enable-maint-mode-button.png "Habilitar modo de mantenimiento")

4. En la ventana **Habilitar modo de mantenimiento** , escriba los valores siguientes:
    - **Seleccionar la página que se va a usar cuando esté habilitado el modo de mantenimiento**: Seleccione uno de los siguientes valores:

        - **Página predeterminada**: Seleccione este valor si desea que se muestre la página predeterminada cuando está habilitado el modo de mantenimiento. De forma predeterminada, esta opción está seleccionada.

        - **Página personalizada**: Seleccione este valor si desea que se muestre una página HTML personalizada cuando se habilita el modo de mantenimiento.

    - **Dirección URL de la página personalizada**: este campo solo está habilitado cuando se selecciona la opción para mostrar una página HTML personalizada. Debe asegurarse de que la dirección URL de la página que proporcione es accesible públicamente. Si no se puede tener acceso a la página HTML especificada, se muestra la página predeterminada con una nota para los administradores.

5. Seleccione **Habilitar**. Mientras se habilita el modo de mantenimiento, el portal se reinicia y no está disponible durante unos minutos. 

    > [!div class=mx-imgBorder]
    > ![Habilitar la configuración del modo de mantenimiento](../media/enable-maint-mode.png "Habilitar la configuración del modo de mantenimiento")

## <a name="configure-or-disable-maintenance-mode"></a>Configurar o deshabilitar el modo de mantenimiento

Después de habilitar el modo de mantenimiento para el portal, puede actualizar la configuración del modo de mantenimiento y elegir otra página.

También puede deshabilitar el modo de mantenimiento en el portal cuando se complete el mantenimiento programado de su sitio Web. Los usuarios del portal ahora pueden examinar y tener acceso a todas las páginas web como de costumbre.

1. Abra el [centro de administración de portales de PowerApps](admin-overview.md).

2. Vaya a **acciones del Portal** > **configurar o deshabilitar el modo de mantenimiento**.

    > [!div class=mx-imgBorder]
    > ![Configurar]el modo de mantenimiento(../media/configure-maint-mode-button.png "configurar el modo de mantenimiento")

3. Modifique la configuración según sea necesario y seleccione **Actualizar**. Por ejemplo, puede optar por Mostrar la página predeterminada si ha seleccionado Mostrar la página personalizada anteriormente.

4. Para deshabilitar el modo de mantenimiento, seleccione **deshabilitar**. Mientras se está actualizando o deshabilitando el modo de mantenimiento, el portal se reinicia y no está disponible durante unos minutos.

    > [!div class=mx-imgBorder]
    > ![Actualizar configuración del modo]de mantenimiento(../media/configure-maint-mode.png "Actualizar configuración de modo de mantenimiento")

