---
title: Cambiar iconos de entidades personalizadas de aplicaciones controladas por modelos en PowerApps | MicrosoftDocs
definition: Learn how to change the icon for a custom entity
ms.custom: ''
ms.date: 05/17/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 477f9792-8207-49ef-8968-45274b5355a8
caps.latest.revision: 19
ms.author: matp
manager: kvivek
tags:
  - Links to topic not migrated
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="change-model-driven-app-custom-entity-icons"></a>Cambiar iconos de entidades personalizadas de aplicaciones controladas por modelos 

Al crear una entidad personalizada, se le asigna automáticamente un icono predeterminado. Todas las entidades personalizadas usan el mismo icono de forma predeterminada. Use iconos personalizados para distinguir la apariencia de las entidades personalizadas. No puede modificar los iconos asignados a entidades del sistema.  
  
 Puede cargar tres tipos de iconos de entidades para cada entidad personalizada. 

|Tipo de icono  |Descripción  |
|---------|---------|
|**Icono Interfaz unificada**|Debe ser un icono escalable del gráfico vectorial (.svg) |
|**Icono en aplicación web**|Una imagen en formato .svg, .gif, .png, o .jpg, con un tamaño de16x16 píxeles.|
|**Icono para formularios de entidad**|Una imagen en formato .svg, .gif, .png, o .jpg, con un tamaño de 32x32 píxeles.|

> [!NOTE]
> El tamaño de todos los archivos de imágenes no puede superar los 10 kilobytes.
>
> Cuando se usa una imagen escalable del gráfico vectorial (.svg) como **Icono en aplicación web** o **Icono para formularios de entidad**, debe tener definido el tamaño predeterminado. Puesto que SVG es un documento XML, puede editar los valores de [ancho](https://developer.mozilla.org/docs/Web/SVG/Attribute/width) y [alto](https://developer.mozilla.org/docs/Web/SVG/Attribute/height) del elemento [svg](https://developer.mozilla.org/docs/Web/SVG/Element/svg) con un editor de texto para definir el tamaño predeterminado para la imagen.

Cada tipo de icono se almacena como un recurso web. Puede crear recursos web primero y después establecer los iconos para usarlos, o puede crear el nuevo recurso web dentro del cuadro de diálogo **Registro de búsqueda** seleccionando **Nuevo** mientras establece el valor. Más información: [Crear o editar recursos web para extender una aplicación web](create-edit-web-resources.md)

## <a name="set-the-icons-for-a-custom-entity"></a>Establezca los iconos para una entidad personalizada.

Debe usar el explorador de soluciones para establecer iconos de entidades.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="set-entity-icons"></a>Definir iconos de entidades

1. En la barra de comandos, seleccione **Actualizar iconos**.  
  
2. En el cuadro de diálogo **Seleccionar iconos nuevos**, en la pestaña **Cliente web**, bajo **Icono en aplicación web** o **Icono para formularios de entidad**, a la derecha de **Nuevo icono**, seleccione el botón **Examinar** ![Botón Búsqueda](media/lookup-button-4.gif).
3. Seleccione o cree el recurso web adecuado y después seleccione **Aceptar**. 
4. En la pestaña **Interfaz unificada**, haga igual para el campo **Nuevo icono**.
5. Seleccione **Aceptar** para cerrar el cuadro de diálogo **Seleccionar nuevos iconos**.
6. En la barra de comandos, en el menú **Archivo**, seleccione **Guardar**.  
7. Cuando haya completado los cambios, publíquelos. Seleccione **Publicar** en la barra de comandos mientras la entidad está seleccionada en el explorador de soluciones.
  
## <a name="community-tools"></a>Herramientas de la Comunidad

**[Iconator](https://www.xrmtoolbox.com/plugins/MscrmTools.Iconator/)** es una herramienta desarrollada por la comunidad XrmToolbox para Dynamics 365 Customer Engagement. Consulte el tema [Herramientas para desarrolladores de Common Data Service](https://docs.microsoft.com/dynamics365/customer-engagement/developer/developer-tools) para consultar las herramientas desarrolladas por la comunidad.

> [!NOTE]
> Las herramientas de la comunidad no son un producto de Microsoft y no se incluyen en el soporte técnico. Si tiene alguna duda relacionada con la herramienta, póngase en contacto con el Editor. Más información: [XrmToolBox](https://www.xrmtoolbox.com).

## <a name="next-steps"></a>Pasos siguientes  
[Crear una entidad](../common-data-service/create-edit-entities.md)<br />
[Editar una entidad](../common-data-service/edit-entities.md)
