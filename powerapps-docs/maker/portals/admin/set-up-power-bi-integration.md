---
title: Configuración de la integración de Power BI con el portal | MicrosoftDocs
description: Aprenda a configurar la integración de Power BI con el portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b6c71b87d32342e382a814e34a90c0cb7a9d7b67
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976148"
---
# <a name="set-up-power-bi-integration"></a>Configuración de la integración con Power BI

Power BI es una de las mejores herramientas para ofrecer información con visualización sencilla e interactiva. Para ver los paneles e informes de Power BI en páginas web de un portal, debe habilitar Power BI visualización desde el centro de administración de portales de PowerApps. También puede insertar paneles e informes creados en el nuevo área de trabajo de Power BI habilitando la integración del servicio Power BI Embedded.

> [!NOTE]
> - Debe tener una licencia de Power BI adecuada.
> - Para usar Power BI Embedded servicio, debe tener una licencia Power BI Embedded adecuada. Para obtener más información, consulte [licencias](https://docs.microsoft.com/power-bi/developer/embedded-faq#licensing).

## <a name="enable-power-bi-visualization"></a>Habilitar la visualización de Power BI

La habilitación de la visualización de Power BI permite insertar paneles e informes en páginas web en un portal mediante la etiqueta Liquid de powerbi.

1.  Abra el [centro de administración de portales de PowerApps](admin-overview.md).

2.  Vaya a **configuración de la integración de Power BI** > **Habilitar la visualización de Power BI**.

    > [!div class=mx-imgBorder]
    > ![Habilitar visualización de Power BI](../media/enable-power-bi-visualization.png "Habilitar Power BI visualización")

3.  Seleccione **Habilitar** en el mensaje de confirmación. Mientras se habilita Power BI visualización, el portal se reinicia y no estará disponible durante unos minutos. Aparece un mensaje cuando se habilita la visualización de Power BI.

Los personalizadores pueden usar la etiqueta Liquid de [powerbi](../liquid/portals-entity-tags.md#powerbi) para insertar Power BI paneles e informes en páginas web en un portal. Al incrustar el contenido de Power BI, los personalizadores pueden usar [parámetros de filtro](https://docs.microsoft.com/en-us/power-bi/service-url-filters) para crear vistas personalizadas. Más información: [etiqueta líquida de powerbi](../liquid/portals-entity-tags.md#powerbi)

### <a name="disable-power-bi-visualization"></a>Deshabilitar la visualización de Power BI

1.  Abra el [centro de administración de portales de PowerApps](admin-overview.md).

2.  Vaya a **configuración de la integración de Power BI** > **deshabilite la visualización de Power BI**.

    > [!div class=mx-imgBorder]
    > Deshabilitar la visualización de ![Power BI](../media/disable-power-bi-visualization.png "deshabilitar") la visualización Power BI

3. Seleccione **deshabilitar** en el mensaje de confirmación. Mientras Power BI visualización se deshabilita, el portal se reinicia y no estará disponible durante unos minutos. Aparece un mensaje cuando Power BI visualización está deshabilitada.

## <a name="enable-power-bi-embedded-service"></a>Habilitar servicio de Power BI Embedded

La habilitación del servicio de Power BI Embedded le permite insertar paneles e informes creados en el nuevo área de trabajo de Power BI. Los paneles e informes se insertan en las páginas web de un portal mediante la etiqueta Liquid de powerbi.

**Requisitos previos**: antes de habilitar el servicio Power BI Embedded, asegúrese de que ha creado los paneles e informes en el área de trabajo nueva en Power BI. Después de crear el área de trabajo, proporcione acceso de administrador al administrador global para que las áreas de trabajo se muestren en el centro de administración de portales de PowerApps. Para obtener más información sobre cómo crear nuevas áreas de trabajo y agregar acceso a ellas, consulte [crear nuevas áreas de trabajo en Power BI](https://docs.microsoft.com/en-us/power-bi/service-create-the-new-workspaces).

**Limitaciones del servicio Power BI Embedded**: para obtener información sobre las limitaciones, consulte [consideraciones y limitaciones](https://docs.microsoft.com/power-bi/developer/embed-service-principal#considerations-and-limitations).

> [!NOTE]
> Asegúrese de que la visualización de Power BI está habilitada para que funcione la etiqueta líquida de powerbi.

1. Abra el [centro de administración de portales de PowerApps](admin-overview.md).

2. Vaya a **configuración de la integración de Power BI** > **Habilitar el servicio de Power BI Embedded**.

    > [!div class=mx-imgBorder]
    > ![Habilitar servicio de Power BI Embedded](../media/enable-powerbi-embedded-button.png "habilitar") servicio de Power BI Embedded

3. En la ventana **Habilitar la integración de servicios de Power BI Embedded** , seleccione y mueva las áreas de trabajo de Power BI desde las que los paneles e informes deben mostrarse en el portal a la lista de áreas de **trabajo seleccionadas** .

    > [!div class=mx-imgBorder]
    > ![Seleccionar áreas de trabajo de Power BI](../media/enable-powerbi-embedded-window.png "seleccionar áreas de trabajo de Power BI")
    
    > [!NOTE]
    > Después de agregar áreas de trabajo a la lista de **áreas de trabajo seleccionadas** , las bases de datos y los informes se representan transcurridos unos minutos.
    

4. Seleccione **Habilitar**. Mientras se habilita Power BI Embedded servicio, el portal se reinicia y no está disponible durante unos minutos. Aparece un mensaje cuando se habilita el servicio de Power BI Embedded.

Ahora debe crear un grupo de seguridad y agregarlo a su cuenta de Power BI. Para obtener más información, consulte [Create Security Group y Add to Power BI Account](#create-security-group-and-add-to-power-bi-account).

### <a name="create-security-group-and-add-to-power-bi-account"></a>Crear grupo de seguridad y agregar a Power BI cuenta

Después de habilitar la integración del servicio Power BI Embedded, debe crear un grupo de seguridad en Azure Active Directory, agregarle un miembro y, a continuación, agregar el grupo de seguridad en Power BI a través del portal de administración de Power BI. Esto permite que los paneles e informes creados en nuevas áreas de trabajo de Power BI se muestren en el portal.

> [!NOTE]
> Debe iniciar sesión con la misma cuenta de administrador global que usó para habilitar el servicio de Power BI Embedded.

**Paso 1: crear un grupo de seguridad**

1. Inicie sesión en el [Azure portal](https://portal.azure.com) mediante una cuenta de administrador global para el directorio.

2. Seleccione **Azure Active Directory**, **grupos**y, a continuación, seleccione **nuevo grupo**.

3. En la página **Grupo** , escriba la siguiente información:

    - **Tipo de grupo**: seguridad.

    - **Nombre del grupo**: portal Power BI Embedded servicio.

    - **Descripción del grupo**: este grupo de seguridad se usa para la integración del portal y del servicio de Power BI Embedded.

    - **Tipo de pertenencia**: asignado.

      > [!div class=mx-imgBorder]
      > ![Crear grupo de seguridad para Power BI Embedded](../media/powerbi-embed-security-group.png "grupo de seguridad de creación de servicio para Power BI Embedded servicio")

4. Seleccione **Crear**.

**Paso 2: agregar un miembro de grupo**

**Requisito previo**: antes de agregar un miembro al grupo de seguridad, debe tener el identificador de la aplicación del portal. El identificador de la aplicación del portal está disponible en la pestaña **detalles del portal** del centro de administración de portales de [PowerApps](admin-overview.md).

1. Inicie sesión en el [Azure portal](https://portal.azure.com) mediante una cuenta de administrador global para el directorio.

2. Seleccione **Azure Active Directory**y, a continuación, seleccione **grupos**.

3. En la página **grupos-todos los grupos** , busque el **portal Power BI Embedded** grupo de servicios y selecciónelo.

    > [!div class=mx-imgBorder]
    > ![Busque y seleccione el grupo de seguridad de Power BI Embedded búsqueda de servicio](../media/search-security-group.png "y seleccione el grupo de seguridad de Power BI Embedded servicio") .

4. En la página de **información general del Portal Power BI Embedded servicio** , seleccione **miembros** en el área **administrar** .

5. Seleccione **Agregar miembros**y escriba el identificador de la aplicación del portal en el cuadro de texto.

6. Seleccione el miembro en el resultado de la búsqueda y, a continuación, elija **seleccionar**.

    > [!div class=mx-imgBorder]
    > ![Agregue un miembro en el grupo de seguridad para Power BI Embedded](../media/add-member-powerbi-embed.png "miembro agregar servicio en el grupo de seguridad para Power BI Embedded servicio")

**Paso 3: instalación de Power BI**

1. Inicie sesión en [Power BI](https://powerbi.microsoft.com) mediante una cuenta de administrador global para el directorio.

2. Seleccione **configuración** en la parte superior derecha del servicio Power BI y elija **portal de administración**.

    > [!div class=mx-imgBorder]
    > ![Seleccione portal de administración en servicio Power BI](../media/select-admin-portal.png "Seleccione portal de administración en servicio Power BI")

3. Seleccione **configuración de inquilino**.

4. En la sección **configuración del desarrollador** , seleccione **permitir que las entidades de servicio usen las API de Power BI**.

5. En el campo **grupos de seguridad específicos** , busque el **portal Power BI Embedded** grupo de servicios y selecciónelo.

    > [!div class=mx-imgBorder]
    > ![Agregar un grupo de seguridad en Power BI portal de administración](../media/add-sg-powerbi.png "Agregar grupo de seguridad en Power BI portal de administración")

6. Seleccione **aplicar**.

Los personalizadores ahora pueden usar la etiqueta Liquid de [powerbi](../liquid/portals-entity-tags.md#powerbi) para insertar Power BI paneles e informes de nuevas áreas de trabajo de Power BI en páginas web de un portal. Para usar Power BI Embedded servicio, el tipo de autenticación debe especificarse como **powerbiembedded**. Al incrustar el contenido de Power BI, los personalizadores pueden usar [parámetros de filtro](https://docs.microsoft.com/en-us/power-bi/service-url-filters) para crear vistas personalizadas. Más información: [etiqueta líquida de powerbi](../liquid/portals-entity-tags.md#powerbi).


### <a name="manage-the-power-bi-embedded-service"></a>Administrar el servicio de Power BI Embedded

1. Abra el [centro de administración de portales de PowerApps](admin-overview.md).

2. Vaya a **configuración de la integración de Power BI** > **administrar el servicio Power BI Embedded**.

    > [!div class=mx-imgBorder]
    > ![Administración]del servicio(../media/manage-powerbi-embedded-button.png "Power BI Embedded de administración") de Power BI Embedded

3. En la ventana de **integración del servicio de administración de Power BI Embedded** , quite o mueva las áreas de trabajo de Power BI desde las que los paneles e informes deben mostrarse en el portal a la lista de áreas de **trabajo seleccionadas** .

    > [!div class=mx-imgBorder]
    > ![Seleccionar áreas de trabajo de Power BI](../media/manage-powerbi-embedded-window.png "seleccionar áreas de trabajo de Power BI")
    
    > [!NOTE]
    > Después de quitar las áreas de trabajo de la lista de **áreas de trabajo seleccionadas** , puede tardar hasta 1 hora en reflejar los cambios. Hasta entonces, las bases de datos y los informes se representan en el portal sin problemas.

4. Seleccione **Guardar**.

### <a name="disable-the-power-bi-embedded-service"></a>Deshabilitar el servicio de Power BI Embedded

1.  Abra el [centro de administración de portales de PowerApps](admin-overview.md).

2.  Vaya a **configuración de la integración de Power BI** > **administrar el servicio Power BI Embedded**.

    > [!div class=mx-imgBorder]
    > ![Administración]del servicio(../media/manage-powerbi-embedded-button.png "Power BI Embedded de administración") de Power BI Embedded

3. En la ventana de **integración del servicio administrar Power BI Embedded** , seleccione **deshabilitar la integración del servicio de Power BI Embedded**.

    > [!div class=mx-imgBorder]
    > ![Deshabilitar Power BI Embedded servicio](../media/disable-powerbi-embedded-window.png "deshabilitar Power BI Embedded servicio")

4. Seleccione **Guardar**.

5. Seleccione **Aceptar** en el mensaje de confirmación. Mientras Power BI Embedded servicio se deshabilita, el portal se reinicia y no está disponible durante unos minutos. Aparece un mensaje cuando Power BI Embedded servicio está deshabilitado.

## <a name="privacy-notice"></a>Aviso de privacidad  

[!INCLUDE[cc_privacy_powerbi_tiles_dashboards](../../../includes/cc-privacy-powerbi-tiles-dashboards.md)]

### <a name="see-also"></a>Vea también

[etiqueta líquida de powerbi](../liquid/portals-entity-tags.md#powerbi)<br> 
[Agregar un informe o un panel de Power BI a una página web en el portal](add-powerbi-report.md)
