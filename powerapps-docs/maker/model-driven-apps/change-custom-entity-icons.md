---
title: Cambiar iconos de entidad personalizada de la aplicación basados en modelos en PowerApps | Microsoft Docs
definition: Learn how to change the icon for a custom entity
ms.custom: ''
ms.date: 05/17/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: c625ac14905e49879eb6dc93eff706a7dab18433
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39711570"
---
# <a name="change-model-driven-app-custom-entity-icons"></a>Cambiar iconos de entidad personalizada de la aplicación basados en modelos 

Al crear una entidad personalizada, se asigna automáticamente un icono predeterminado. Todas las entidades personalizadas usan el mismo icono de forma predeterminada. Use iconos personalizados para diferenciar el aspecto de sus entidades personalizadas. No puede modificar los iconos asignados a las entidades del sistema.  
  
 Puede cargar tres tipos de iconos de entidad para cada entidad personalizada. 

|Tipo de icono  |Descripción  |
|---------|---------|
|**Icono de interfaz unificada**|Debe ser un icono de gráfico vectorial escalable (.svg) |
|**Icono en la aplicación web**|Una imagen en formato .svg, .gif, .png o .jpg, con un tamaño de 16x16 píxeles.|
|**Icono de formularios de entidad**|Una imagen en formato .svg, .gif, .png o .jpg, con un tamaño de 32x32 píxeles.|

> [!NOTE]
> Todos los archivos de imagen deben tener un tamaño no superior a 10 kilobytes.
>
> Cuando use una imagen de gráfico vectorial escalable (.svg) como **icono en la aplicación web** o **icono de formularios de entidad**, debe tener establecido el tamaño predeterminado. Puesto que SVG es un documento XML, puede editar los valores [ancho](https://developer.mozilla.org/docs/Web/SVG/Attribute/width) y [alto](https://developer.mozilla.org/docs/Web/SVG/Attribute/height) del elemento [svg](https://developer.mozilla.org/docs/Web/SVG/Element/svg) con un editor de texto para definir el tamaño predeterminado para la imagen.

Cada tipo de icono se almacena como recurso web. Puede crear los recursos web primero y, a continuación,establecer los iconos para usarlos, o bien puede crear el nuevo recurso web en el cuadro de diálogo **Buscar registro** seleccionando **Nuevo** mientras se establece el valor. Más información: [Crear o editar recursos web para ampliar una aplicación](create-edit-web-resources.md)

## <a name="set-the-icons-for-a-custom-entity"></a>Establezca los iconos para una entidad personalizada.

Debe usar el Explorador de soluciones para establecer iconos de entidad.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="set-entity-icons"></a>Establecer iconos de entidad

1. En la barra de comandos, seleccione **Actualizar iconos**.  
  
2. En el cuadro de diálogo **Seleccionar iconos nuevos**, en la pestaña **Cliente web**, en **Icono en la aplicación web** o **Icono de formularios de entidad**, a la derecha de **Nuevo icono**, seleccione el botón **Examinar** y el ![botón Buscar](media/lookup-button-4.gif).
3. Seleccione o cree el recurso web adecuado y, a continuación, seleccione **Aceptar**. 
4. En la pestaña **Interfaz unificada**, haga lo mismo para el campo **Nuevo icono**.
5. Seleccione **Aceptar** para cerrar el cuadro de diálogo **Seleccionar iconos nuevos**
6. En la barra de comandos, en el menú **Archivo**, seleccione **Guardar**.  
7. Cuando haya completado los cambios, publíquelos. Seleccione **Publicar** en la barra de comandos mientras se selecciona la entidad en el Explorador de soluciones.
  
## <a name="community-tools"></a>Herramientas de la comunidad

**[Iconator](https://www.xrmtoolbox.com/plugins/MscrmTools.Iconator/)** es una herramienta que la comunidad de XrmToolBox desarrolló para Dynamics 365 Customer Engagement. Consulte el tema [Herramientas para desarrolladores de Common Data Service para aplicaciones](https://docs.microsoft.com/dynamics365/customer-engagement/developer/developer-tools) para ver las herramientas desarrolladas de la comunidad.

> [!NOTE]
> Las herramientas de la comunidad no son un producto de Microsoft y no se incluyen en el soporte técnico. Si tiene preguntas sobre la herramienta, póngase en contacto con el editor. Más información: [XrmToolBox](https://www.xrmtoolbox.com).

## <a name="next-steps"></a>Pasos siguientes  
[Crear una entidad](../common-data-service/create-edit-entities.md)<br />
[Editar una entidad](../common-data-service/edit-entities.md)
