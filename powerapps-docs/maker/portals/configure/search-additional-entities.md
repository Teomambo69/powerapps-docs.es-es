---
title: Búsqueda global de entidades adicionales en el portal de Power Apps | MicrosoftDocs
description: Aprenda cómo funciona la búsqueda global de entidades adicionales en un portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/28/2020
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: e1091709e096d7b7b53c5f4e02f4b84d15cd952e
ms.sourcegitcommit: 8dd68565e03a4e66db1f8937630fa4c52eb93871
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "3321309"
---
# <a name="walkthrough-configuring-additional-entitiesforglobalsearch"></a>Tutorial: Configuración de entidades adicionales para la búsqueda global  

## <a name="overview"></a>Información general

Puede habilitar entidades adicionales para la funcionalidad de búsqueda. Configurar la búsqueda de entidades adicionales requiere acciones adicionales, que se describen en este artículo.

Las siguientes consideraciones se aplican al configurar entidades adicionales para la búsqueda global:

- Asegúrese de que la [configuración del sitio](#site-setting-for-additional-entities) para la búsqueda de entidades adicionales está habilitada.
- Cree una vista llamada **Búsqueda de portal** para cualquier entidad adicional para la que desee habilitar la búsqueda. Más información: [campos de búsqueda en la búsqueda global](search.md#fields-searchable-in-global-search)
- Asegúrese de que se crea un **Permiso de entidad** para proporcionar privilegios de lectura y el alcance adecuado para que los registros se muestren en los resultados de búsqueda.
- Asocie el permiso de la entidad con los **roles web** requeridos.
- Los permisos de entidad deben estar asociados con el **rol web anónimo** si desea permitir la búsqueda anónima de una entidad.
- Configure una [página de resultados de búsqueda](#results-page-for-additional-entities) para mostrar los resultados de búsqueda.

La configuración explícita explicada anteriormente asegura que ningún registro estará disponible accidentalmente a través de la búsqueda global.

### <a name="site-setting-for-additional-entities"></a>Configuración del sitio para entidades adicionales

La configuración del sitio **Búsqueda/Habilitar entidades adicionales** es necesaria para configurar entidades adicionales para la búsqueda.

> [!IMPORTANT]
> **Búsqueda/Habilitar entidades adicionales** es explícitamente para habilitar la búsqueda de entidades adicionales. La configuración principal del sitio de búsqueda **Buscar/Habilitado** debe establecerse en **verdadero** cuando se usa la funcionalidad de búsqueda.

También puede configurar otros ajustes del sitio relacionados, similares a la configuración de búsqueda para las entidades predeterminadas. Por ejemplo, puede usar la configuración **Búsqueda/Filtros** para configurar entidades adicionales y agregar una opción de filtro desplegable a la búsqueda global. Más información: [Configuración del sitio](search.md#related-site-settings)

### <a name="results-page-for-additional-entities"></a>Página de resultados para entidades adicionales

La página de resultados de búsqueda se configura a través de un **Marcador de sitio** llamado ```<entitylogicalname>_SearchResultPage```.

Por ejemplo, si el nombre lógico de su entidad es *nwind_products*, el marcador del sitio será ```nwind_products_SearchResultPage```. El valor del marcador del sitio es la página que desea abrir cuando se selecciona ese resultado de búsqueda. De forma predeterminada, se pasa un id. de registro en el parámetro de cadena de consulta *id.* para la página de resultados de búsqueda.

Asegúrese de que su página de resultados de búsqueda tenga un formulario de entidad o tenga lógica escrita para mostrar los detalles del resultado de búsqueda.

## <a name="walkthrough---configure-search-for-additional-entities-with-sample-database"></a>Tutorial: configurar la búsqueda de entidades adicionales con una base de datos de ejemplo

El siguiente tutorial explica cómo habilitar la búsqueda de la entidad **Productos del pedido** en la base de datos de ejemplo **Northwind**, disponible con Common Data Service.

Para obtener más información sobre bases de datos de ejemplo, vea [Instalar la base de datos y aplicaciones de Northwind Traders](../../canvas-apps/northwind-install.md).

> [!TIP]
> Puede seguir el tutorial con una entidad de su elección reemplazando el nombre de entidad *nwind_products* con el nombre lógico de su entidad.

## <a name="step-1-add-or-update-search-site-settings"></a>Paso 1: Agregar o actualizar la configuración del sitio de búsqueda

1. Inicie sesión en [Power Apps](https://make.powerapps.com).

1. Asegúrese de estar en el entorno apropiado donde existe su portal.

1. Seleccione **Aplicaciones** en el panel de navegación izquierdo y localice la aplicación basada en modelo **Administración del portal**.  

    ![Administración del portal](media/search-additional-entities/portal-management.png "Administración del portal")

    >[!NOTE]
    > La aplicación Administración del portal podría llamarse **Portales de Dynamics 365** si se encuentra en un entorno donde están instaladas las aplicaciones de Dynamics 365.

1. Seleccione para abrir la aplicación **Administración del portal** y luego vaya a **Configuraciones del sitio** en el panel de navegación izquierdo.

1. Cree una nueva configuración, **Búsqueda/Habilitar entidades adicionales** y establezca su valor en **verdadero**.

    ![Configuración del sitio para Habilitar entidades adicionales](media/search-additional-entities/enableadditionalentitiessearch-sitesetting.png "Configuración del sitio para Habilitar entidades adicionales")

1. Cree o actualice la configuración de **búsqueda/filtros** y agregue el valor **Productos: nwind_products**.

    ![Configuración del sitio de búsqueda/filtros](media/search-additional-entities/search-filters.png "Configuración del sitio de búsqueda/filtros")

## <a name="step-2-create-or-verify-the-portal-search-view"></a>Paso 2: cree o verifique la vista de búsqueda del portal

> [!NOTE]
> Los siguientes pasos requieren la instalación de la [solución Northwind Traders](../../canvas-apps/northwind-install.md). Si desea usar otra entidad, use la solución adecuada o use la solución predeterminada.

1. Vaya a [Power Apps](https://make.powerapps.com) y seleccione **Soluciones** en el panel de navegación izquierdo.

1. Seleccione **Northwind Traders**.

    ![Seleccionar solución](media/search-additional-entities/select-solution.png "Seleccionar solución")

1. Busque la entidad **Producto del pedido**.

    ![Entidad Producto de pedido](media/search-additional-entities/order-product.png "Entidad Producto de pedido")

1. Seleccione la entidad **Producto del pedido** y luego seleccione **Vistas**.

    ![Vistas](media/search-additional-entities/views.png "Vistas")

1. Asegúrese de que ve **Búsqueda de portal** en la lista de vistas.

    ![Vista Búsqueda del portal](media/search-additional-entities/portal-search.png "Vista Búsqueda del portal")

    Si la vista Búsqueda del portal aún no existe, seleccione **Agregar vista**, ingrese el nombre como **Búsqueda del portal** y luego seleccione **Crear**.

    ![Agregar una vista](media/search-additional-entities/add-view.png "Agregar una vista")

    ![Agregar la vista Búsqueda del portal](media/search-additional-entities/portal-search-view.png "Agregar la vista Búsqueda del portal")

1. Asegúrese de agregar las columnas apropiadas a la vista para la búsqueda.

    ![Agregar columnas](media/search-additional-entities/add-columns.png "Agregar columnas")

1. Si editó la vista, asegúrese de seleccionar **Guardar** y después **Publicar** antes de continuar.

    ![Guardar y publicar](media/search-additional-entities/save-publish.png "Guardar y publicar la vista")

## <a name="step-3-create-entity-permissions"></a>Paso 3: Crear permisos de entidad

1. Inicie sesión en [Power Apps](https://make.powerapps.com).

1. Seleccione **Aplicaciones** en el panel de navegación izquierdo y luego seleccione para abrir la aplicación basada en modelo **Administración del portal**.  

1. Seleccione **Permisos de entidad** en el panel de navegación izquierdo.

1. Seleccione **Nuevo**.

    ![Nuevo registro de permiso de entidad](media/search-additional-entities/new-entity-permission.png "[Nuevo registro de permiso de entidad")

1. Escriba el nombre **Productos Northwind, Lectura completa** y luego seleccione el **Alcance** apropiado y el privilegio **Lectura**.

    Para este ejemplo, se proporciona el alcance **Global** para la entidad **nwind_products**.

    ![Alcance y permisos de lectura](media/search-additional-entities/scope-read.png "Alcance y permisos de lectura")

1. Seleccione **Guardar y cerrar**.

1. Seleccione y abra **Productos Northwind, Lectura completa**.

1. Desplácese hacia abajo hasta la sección **Roles web** y luego seleccione **Agregar rol web existente**.

    ![Agregar un rol web existente](media/search-additional-entities/add-existing-web-role.png "Agregar un rol web existente")

1. Busque **Usuarios autenticados** y seleccione **Agregar**:

    ![Agregar usuarios autenticados](media/search-additional-entities/add-authenticated-users.png "Agregar usuarios autenticados")

## <a name="step-4-add-a-webpage"></a>Paso 4: Agregar una página web

1. Vaya a [Power Apps](https://make.powerapps.com) y seleccione **Aplicaciones** en el panel de navegación izquierdo.

1. Seleccione **Más comandos** (...) para el portal y luego seleccione **Editar** para abrir el portal en Power Apps Studio.

1. Seleccione **Nueva pagina** en el menú de la esquina superior izquierda y luego seleccione el diseño **En blanco** para la página.

    ![Nueva página](media/search-additional-entities/new-page.png "Nueva página")

1. Ingrese **Productos de pedido** como nombre de la página web. Esta página se configurará como la página de resultados de búsqueda.

1. Seleccione **Componentes** en el panel de navegación izquierdo y luego agregue un componente **Formulario** a esta página web.

    ![Agregar un componente de formulario](media/search-additional-entities/form-component.png "Agregar un componente de formulario")

1. Seleccione la opción **Utilizar existente** en el lado derecho de su espacio de trabajo, elija el formulario **Ver productos** para la entidad **nwind_products** y luego establezca **Modo** en **Solo lectura**.

    ![Establecer el modo](media/search-additional-entities/mode.png "Establecer el modo")

## <a name="step-5-add-a-site-marker-for-the-search-results-details-page"></a>Paso 5: Agregar un marcador de sitio para la página de detalles de resultados de búsqueda

1. Inicie sesión en [Power Apps](https://make.powerapps.com).

1. Seleccione **Aplicaciones** en el panel de navegación izquierdo y elija la aplicación basada en modelo **Administración del portal** para abrirla.  

1. Seleccione **Marcador de sitio** en el panel de navegación de la izquierda.

1. Seleccione **Nuevo** y luego cree un nuevo marcador de sitio utilizando los siguientes detalles:

    - **Nombre:** **nwind_products_SearchResultPage**
    - **Página**: **Productos de pedido**
    
    ![Nuevo marcador de sitio](media/search-additional-entities/new-site-marker.png "Nuevo marcador de sitio")

## <a name="step-6-rebuild-the-search-index"></a>Paso 6: Volver a generar el índice de búsqueda

1. Explore su portal utilizando una cuenta de usuario que tenga asignado el rol web Administrador.

1. Agregue la URL en la barra de direcciones con **/_services /about** y luego seleccione **Entrar**.

   ![Página _services_about](media/search-additional-entities/services-about.png "Página _services_about")

1. Seleccione [Borrar caché](https://docs.microsoft.com/powerapps/maker/portals/admin/clear-server-side-cache).

1. Después de borrar la caché, seleccione [Reconstruir índice de búsqueda](search.md#rebuild-full-search-index).

## <a name="step-7-verify-that-global-search-works-with-the-custom-entity"></a>Paso 7: Verificar que la búsqueda global funcione con la entidad personalizada

1. Navegue hasta el portal con un usuario que tenga asignado el **rol web**  *Autenticado*.

1. Vaya a la barra de herramientas de búsqueda o la página de búsqueda y busque un registro conocido.

   Por ejemplo, use la palabra clave de búsqueda **Sopa de almejas Northwind** para mostrar resultados asociados con la entidad **nwind_products**.

   ![Resultado de la búsqueda](media/search-additional-entities/search-results.png "Resultado de la búsqueda")

## <a name="next-steps"></a>Pasos siguientes

[Quitar una entidad de búsqueda global](search.md#remove-an-entity-from-global-search)

### <a name="see-also"></a>Vea también

[Configuración del sitio relacionada con la búsqueda](search.md#related-site-settings)