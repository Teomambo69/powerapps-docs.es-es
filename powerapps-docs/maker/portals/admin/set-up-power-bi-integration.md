---
title: Configurar la integración de Power BI con el portal | MicrosoftDocs
description: Aprenda a configurar la integración de Power BI con el portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 18ae2abded4208a3caf2e02408c4cf0eef7af09f
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978653"
---
# <a name="set-up-power-bi-integration"></a>Configurar integración de Power BI

Power BI es una de las mejores herramientas para ofrecer ideas con visualización básica e interactiva. Para ver los paneles e informes de Power BI en las páginas web de un portal, debe habilitar la visualización de Power BI desde el Ccentro de administración de portales de Power Apps. También puede insertar paneles e informes creados en el nuevo espacio de trabajo de Power BI habilitando la integración con el servicio Power BI Embedded.

> [!NOTE]
> - Debe tener una licencia adecuada de Power BI.
> - Para usar el servicio Power BI Embedded, debe tener una licencia adecuada de Power BI Embedded. Para obtener más información, vea el tema sobre [Licencias](https://docs.microsoft.com/power-bi/developer/embedded-faq#licensing).

## <a name="enable-power-bi-visualization"></a>Habilitar visualización de Power BI

Habilitar la visualización de Power BI permite insertar paneles e informes en las páginas web en un portal utilizando la etiqueta powerbi Liquid.

1.  Abra [Centro de administración de Portales de Power Apps](admin-overview.md).

2.  Vaya a **Configurar la integración de Power BI** > **Habilitar la visualización de Power BI**.

    > [!div class=mx-imgBorder]
    > ![Habilitar visualización de Power BI](../media/enable-power-bi-visualization.png "Habilitar visualización de Power BI")

3.  Seleccione **Habilitar** en el mensaje de confirmación. Mientras la visualización de Power BI está siendo activada, el portal se reiniciará y no estará disponible durante unos minutos. Aparece un mensaje cuando la visualización de Power BI está habilitada.

Los personalizadores pueden usar la etiqueta Liquid [powerbi](../liquid/portals-entity-tags.md#powerbi) para insertar los paneles e informes de Power BI en las páginas web en un portal. A medida que insertan contenido de Power BI, los personalizadores pueden usar [parámetros de filtros](https://docs.microsoft.com/power-bi/service-url-filters) para crear vistas personalizadas. Más información: [etiqueta powerbi de Liquid](../liquid/portals-entity-tags.md#powerbi)

### <a name="disable-power-bi-visualization"></a>Deshabilitar visualización de Power BI

1.  Abra [Centro de administración de Portales de Power Apps](admin-overview.md).

2.  Vaya a **Configurar la integración de Power BI** > **Deshabilitar la visualización de Power BI**.

    > [!div class=mx-imgBorder]
    > ![Deshabilitar visualización de Power BI](../media/disable-power-bi-visualization.png "Deshabilitar visualización de Power BI")

3. Seleccione **Deshabilitar** en el mensaje de confirmación. Mientras la visualización de Power BI está siendo desactivada, el portal se reiniciará y no estará disponible durante unos minutos. Aparece un mensaje cuando la visualización de Power BI está deshabilitada.

## <a name="enable-power-bi-embedded-service"></a>Habilitar el servicio Power BI Embedded

Habilitar el servicio Power BI Embedded le permite insertar paneles e informes creados en el nuevo espacio de trabajo de Power BI. Los paneles e informes se insertan en las páginas web en un portal utilizando la etiqueta powerbi Liquid.

**Requisitos previos**: Para habilitar el servicio Power BI Embedded, asegúrese de que ha creado los paneles e informes en el nuevo espacio de trabajo de Power BI. Después de crear el espacio de trabajo, proporcione acceso de administración al administrador global para que los espacios de trabajo se muestren en el Centro de administración de portales de Power Apps. Para obtener más información sobre la creación de nuevos espacios de trabajo y agregar acceso a ellos, consulte [Crear nuevos espacios de trabajo en Power BI](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces).

**Limitaciones del servicio Power BI Embedded**: Para obtener información sobre limitaciones, consulte [Consideraciones y limitaciones](https://docs.microsoft.com/power-bi/developer/embed-service-principal#considerations-and-limitations).

> [!NOTE]
> Asegúrese de que la visualización de Power BI está habilitada para que funcione la etiqueta powerbi Liquid.

1. Abra [Centro de administración de Portales de Power Apps](admin-overview.md).

2. Vaya a **Configurar la integración de Power BI** > **Habilitar servicio Power BI Embedded**.

    > [!div class=mx-imgBorder]
    > ![Habilitar el servicio Power BI Embedded](../media/enable-powerbi-embedded-button.png "Habilitar el servicio Power BI Embedded")

3. En la ventana **Habilitar integración de Power BI Embedded**, seleccione y mueva los espacios de trabajo de Power BI desde los cuales deben mostrarse paneles e informes en el portal a la lista **Espacios de trabajo seleccionados**.

    > [!div class=mx-imgBorder]
    > ![Seleccionar áreas de trabajo de Power BI](../media/enable-powerbi-embedded-window.png "Seleccionar áreas de trabajo de Power BI")
    
    > [!NOTE]
    > Después de agregar espacios de trabajo a la lista **Espacios de trabajo seleccionados**, las bases de datos y los informes se generan después de unos minutos.
    

4. Seleccione **Habilitar**. Mientras está habilitado el servicio de Power BI Embedded, el portal se reinicia y no está disponible durante unos minutos. Aparece un mensaje cuando el servicio de Power BI Embedded está habilitado.

Debe ahora crear un grupo de seguridad, y agregarlo a su cuenta de Power BI. Para obtener más información, consulte [Crear grupo de seguridad y agregarlo a la cuenta de Power BI](#create-security-group-and-add-to-power-bi-account).

### <a name="create-security-group-and-add-to-power-bi-account"></a>Crear grupo de seguridad y agregarlo a la cuenta de Power BI

Después de habilitar la integración del servicio Power BI Embedded, debe crear un grupo de seguridad en Azure Active Directory, agregarle un miembro y, a continuación, agregar el grupo de seguridad de Power BI a través del portal de administración de Power BI. Esto permite a los paneles e informes creados en nuevos espacios de trabajo de Power BI mostrarse en el portal.

> [!NOTE]
> Debe iniciar sesión con la misma cuenta de administrador global que usó para habilitar el servicio Power BI Embedded.

**Paso 1: Crear un grupo de seguridad**

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com) usando una cuenta de administrador global cuenta para el directorio.

2. Seleccione **Azure Active Directory**, **Grupos** y **Nuevo grupo**.

3. En la página **Grupo**, especifique la siguiente información:

    - **Tipo de grupo**: Seguridad.

    - **Nombre de grupo**: servicio Power BI Embedded del portal.

    - **Descripción del grupo**: Este grupo de seguridad se usa para integración del servicio Power BI Embedded.

    - **Tipo de la suscripción**: Asignado.

      > [!div class=mx-imgBorder]
      > ![Creación del grupo de seguridad para el servicio Power BI Embedded](../media/powerbi-embed-security-group.png "Creación del grupo de seguridad para el servicio Power BI Embedded")

4. Seleccione **Crear**.

**Paso 2: Agregar un miembro del grupo**

**Requisitos previos**: Antes de agregar un integrante al grupo de seguridad, debe tener el identificador de aplicación del portal con usted. El id. de aplicación del portal está disponible en la pestaña **Detalles del portal** en el [Centro de administración de portales de Power Apps](admin-overview.md).

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com) usando una cuenta de administrador global cuenta para el directorio.

2. Seleccione **Azure Active Directory** y luego seleccione **Grupos** .

3. En la página **Grupos - todos los grupos**, busque el grupo **Servicio Power BI Embedded del portal** y selecciónelo.

    > [!div class=mx-imgBorder]
    > ![Buscar y seleccionar el grupo de seguridad para el servicio Power BI Embedded](../media/search-security-group.png "Buscar y seleccionar el grupo de seguridad para el servicio Power BI Embedded")

4. En la página **Información general sobre el servicio Power BI Embedded** del portal, seleccione **Miembros** del área **Administrar**.

5. Seleccione **Agregar integrantes**, y escriba el identificador de la aplicación del portal en el cuadro de texto.

6. Seleccione el integrante de los resultados de búsqueda, y después elija **Seleccionar**.

    > [!div class=mx-imgBorder]
    > ![Agregar integrante al grupo de seguridad para el servicio Power BI Embedded](../media/add-member-powerbi-embed.png "Agregar integrante al grupo de seguridad para el servicio Power BI Embedded")

**Paso 3: configuración de Power BI**

1. Inicie sesión en [Power BI](https://powerbi.microsoft.com) usando una cuenta de administrador global cuenta para el directorio.

2. Seleccione **Configuración** en la parte superior derecho del servicio de Power BI y elija **Portal de administración**.

    > [!div class=mx-imgBorder]
    > ![Seleccionar Portal de administración en servicio Power BI](../media/select-admin-portal.png "Seleccionar Portal de administración en servicio Power BI")

3. Seleccione **Configuración de inquilino**.

4. En la sección **Configuración de desarrollador**, seleccione **Permitir que las entidades de seguridad de servicio usen API de Power BI**.

5. En el campo **Grupos de seguridad específicos**, busque el grupo **Servicio Power BI Embedded** del portal y selecciónelo.

    > [!div class=mx-imgBorder]
    > ![Agregar grupo de seguridad en portal de administración de Power BI](../media/add-sg-powerbi.png "Agregar grupo de seguridad en portal de administración de Power BI")

6. Seleccione **Aplicar**.

Los personalizadores pueden ahora usar la etiqueta Liquid [powerbi](../liquid/portals-entity-tags.md#powerbi) para insertar los paneles e informes de Power BI desde nuevos espacios de Power BI en las páginas web de un portal. Para usar el servicio Power BI Embedded, el tipo de autenticación debe especificarse como **powerbiembedded**. A medida que insertan contenido de Power BI, los personalizadores pueden usar [parámetros de filtros](https://docs.microsoft.com/power-bi/service-url-filters) para crear vistas personalizadas. Más información: [etiqueta powerbi de Liquid](../liquid/portals-entity-tags.md#powerbi).


### <a name="manage-the-power-bi-embedded-service"></a>Administrar el servicio Power BI Embedded

1. Abra [Centro de administración de Portales de Power Apps](admin-overview.md).

2. Vaya a **Configurar la integración de Power BI** > **Administrar servicio Power BI Embedded**.

    > [!div class=mx-imgBorder]
    > ![Administrar el servicio Power BI Embedded](../media/manage-powerbi-embedded-button.png "Administrar el servicio Power BI Embedded")

3. En la ventana **Administrar integración del servicio Power BI Embedded**, elimine y mueva los espacios de trabajo de Power BI desde los cuales deben mostrarse paneles e informes en el portal a la lista **Espacios de trabajo seleccionados**.

    > [!div class=mx-imgBorder]
    > ![Seleccionar áreas de trabajo de Power BI](../media/manage-powerbi-embedded-window.png "Seleccionar áreas de trabajo de Power BI")
    
    > [!NOTE]
    > Después de quitar los espacios de trabajo de la lista **Espacios de trabajo seleccionados**, puede tardar hasta 1 hora en reflejarse los cambios. Hasta entonces, las bases de datos y los informes se generan en el portal sin ningún problema.

4. Seleccione **Guardar**.

### <a name="disable-the-power-bi-embedded-service"></a>Deshabilitar el servicio Power BI Embedded

1.  Abra [Centro de administración de Portales de Power Apps](admin-overview.md).

2.  Vaya a **Configurar la integración de Power BI** > **Administrar servicio Power BI Embedded**.

    > [!div class=mx-imgBorder]
    > ![Administrar el servicio Power BI Embedded](../media/manage-powerbi-embedded-button.png "Administrar el servicio Power BI Embedded")

3. En la ventana **Administrar integración del servicio Power BI Embedded**, seleccione **Deshabilitar integración del servicio Power BI Embedded**.

    > [!div class=mx-imgBorder]
    > ![Deshabilitar servicio Power BI Embedded](../media/disable-powerbi-embedded-window.png "Deshabilitar servicio Power BI Embedded")

4. Seleccione **Guardar**.

5. En el mensaje de confirmación, seleccione **Aceptar**. Mientras está deshabilitado el servicio de Power BI Embedded, el portal se reinicia y no está disponible durante unos minutos. Aparece un mensaje cuando el servicio de Power BI Embedded está deshabilitado.

## <a name="privacy-notice"></a>Aviso de privacidad  

[!INCLUDE[cc_privacy_powerbi_tiles_dashboards](../../../includes/cc-privacy-powerbi-tiles-dashboards.md)]

### <a name="see-also"></a>Vea también

[etiqueta powerbi de Liquid](../liquid/portals-entity-tags.md#powerbi)<br> 
[Agregar un informe o un panel de Power BI a una página web en un portal](add-powerbi-report.md)
