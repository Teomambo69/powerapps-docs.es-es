---
title: Creación o edición de recursos web de aplicaciones controladas por modelos en PowerApps | Microsoft Docs
description: Información sobre cómo crear o editar un recurso web
ms.custom: ''
ms.date: 06/02/2018
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
ms.assetid: ef4ba8df-9ba9-4066-b40d-def9761c7de2
caps.latest.revision: 21
ms.author: matp
manager: kvivek
ms.openlocfilehash: 8d9414ba4c900f98ac26010e4e6d7240b336e2d7
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39710906"
---
# <a name="create-or-edit-model-driven-app-web-resources-to-extend-an-app"></a>Creación o edición de recursos web de aplicaciones controladas por modelos para ampliar una aplicación

Los recursos web los utilizan normalmente los desarrolladores para ampliar una aplicación con archivos que se usan en el desarrollo web. Los usuarios de la aplicación tienen que administrar los recursos web que proporcionen un desarrollador o diseñador.  

> [!TIP]
> Para ver una explicación detallada de los recursos web, consulte [Documentación para desarrolladores: Recursos web para Customer Engagement](/dynamics365/customer-engagement/developer/web-resources).<br /> Si quiere obtener información sobre las dependencias de recursos web agregados en PowerApps, consulte [Documentación para desarrolladores: Dependencias de recursos web](/dynamics365/customer-engagement/developer/web-resources).
   
<a name="BKMK_WhatAreWebResources"></a>

## <a name="what-are-web-resources"></a>¿Qué son los recursos web?  

Los recursos web son archivos virtuales almacenados en el sistema. Cada recurso web tiene un nombre único que puede usarse en una URL para recuperar el archivo. Imagíneselos de esta forma: si tuviera acceso al servidor web real que ejecuta la aplicación web, podría copiar los archivos en dicho sitio. Sin embargo, no puede hacer esto con la mayoría de los servicios en línea.  En su lugar, puede usar los recursos web para cargar archivos en el sistema y, a continuación, hacer referencia a ellos por su nombre, como si los hubiera copiado como archivos en el servidor web.  
  
Por ejemplo, si crea una página HTML como un recurso web denominado "nuevo_miRecursoWeb.htm", podría abrir la página en un explorador a través de una URL similar a la siguiente:  
 
`<base URL>/WebResources/new_myWebResource.htm   `
  
donde *\<URL base >* es la parte de la URL que se utiliza para ver las aplicaciones que terminan en `dynamics.com`. Dado que el recurso web son datos en el sistema, solo los usuarios con licencia de su organización pueden acceder a ellos de este modo. Normalmente, los recursos web están incluidos en los formularios y no hay que hacer referencia a ellos directamente. El uso más común es proporcionar bibliotecas de JavaScript a los scripts de formulario.  
    
Como los recursos web son datos en el sistema y compatibles con las soluciones, puede moverlos a distintas organizaciones exportándolos como parte de una solución e importando dicha solución en otra organización. Debe usar el Explorador de soluciones para trabajar con recursos web.
  
## <a name="open-solution-explorer"></a>Apertura del Explorador de soluciones

Parte del nombre de cualquier recurso web que se crea es el prefijo de personalización. Esto se establece en función del editor de soluciones de la solución en la que está trabajando. Si le interesa el prefijo de personalización, asegúrese de que está trabajando en una solución no administrada, donde el prefijo de personalización es lo que necesita para este recurso web. Más información: [Cambio del prefijo del editor de soluciones](../common-data-service/change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-web-resources"></a>Visualización de recursos web

Con el Explorador de soluciones abierto, en **Componentes**, seleccione **Recursos web**.

![Visualización de recursos web](media/view-web-resources-solution-explorer.png)

<a name="BKMK_CreateAndEditWebResources"></a>

## <a name="create-or-edit-web-resources"></a>Creación o edición de recursos web  

Mientras [visualiza recursos web](#view-web-resources), seleccione **Nuevo** para crear un recurso web o haga doble clic en uno existente para editarlo.

![Nuevo formulario de recursos web](media/new-web-resource-form.png)

Complete el formulario para crear o editar el recurso web:
  
|Campo|Descripción|  
|-----------|-----------------|  
|**Nombre**|*Obligatorio*. El nombre único de este recurso web. No puede cambiarlo después de guardar el recurso web.<br />&bull; Este nombre solo puede incluir letras, números, puntos y caracteres de barra diagonal no consecutivos ("/").<br /> &bull; El prefijo de personalización del editor de la solución se antepone al nombre del recurso web.|  
|**Nombre para mostrar**|El nombre mostrado si ve una lista de recursos web.|  
|**Description**|Una descripción del recurso web.|  
|**Tipo**|*Obligatorio*. Este es el tipo de recurso web. No puede cambiarlo después de guardar el recurso web.|  
|**Editor de texto**|Cuando el tipo de recurso web representa un tipo de archivo de texto, seleccione este botón para abrir una página para editar el contenido con el editor de texto.<br />Más información: [Uso adecuado del editor de texto](#use-the-text-editor-appropriately)| 
|**Idioma**|Permite seleccionar un idioma. Esta opción simplemente etiqueta el registro que almacena los datos del recurso web. No cambia su comportamiento.|  
|**Cargar archivo**|Seleccione el botón **Examinar...** para elegir un archivo con el fin de cargarlo como recurso web.<br />&bull; Puede cargar un archivo al crear un recurso web o para sobrescribir uno existente.<br />&bull; La extensión de nombre de archivo del archivo debe coincidir con las extensiones permitidas.<br />&bull; De forma predeterminada, el tamaño máximo del archivo que se puede cargar como recursos web es de 5 MB. Este valor puede modificarse en Dynamics 365 for Customer Engagement mediante la pestaña **Configuración del sistema** > **Correo electrónico**. Luego, seleccione **Establecer límite de tamaño para archivos adjuntos**. Más información: [Cuadro de diálogo Configuración del sistema - pestaña Correo electrónico](https://docs.microsoft.com/dynamics365/customer-engagement/admin/system-settings-dialog-box-email-tab) |  
|**URL**|Después de guardar el recurso web, la URL del recurso web se muestra aquí. Seleccione este vínculo para ver el recurso web en el explorador.|  
  
Después de haber agregado los cambios, elija **Guardar** y, a continuación, **Publicar**.  

> [!NOTE]
> Los cambios realizados en un recurso web no estarán visibles en la aplicación hasta que la publique.
  
<a name="BKMK_UsingTextEditor"></a>
   
### <a name="use-the-text-editor-appropriately"></a>Uso adecuado del editor de texto

El editor de texto proporcionado en la aplicación para los recursos web solo debe usarse para realizar cambios sencillos de archivos de texto. Puede usarlo para crear y editar recursos web HTML, pero solo se deben editar los recursos web HTML que se crearon con el editor de texto. El editor de texto está diseñado para contenido HTML muy sencillo. 

> [!IMPORTANT]
> Si el contenido de un recurso web HTML no se ha creado con el editor de texto, no use el editor de texto para editarlo.  
> El editor de texto utiliza un control que modifica el código fuente HTML para que pueda editarse. Estos cambios pueden provocar que la página se comporte de manera diferente en el explorador y hacer que el código más sofisticado deje de funcionar. Si abre un recurso web HTML con el editor de texto y lo guarda sin realizar ningún cambio, se pueden dañar algunos recursos web HTML.  Más información: [Documentación para desarrolladores: Use el editor de texto de los recursos web HTML](/dynamics365/customer-engagement/developer/webpage-html-web-resources#use-the-text-editor-for-html-web-resources)
  
Se recomienda usar un editor externo para editar archivos de texto y, a continuación, guardarlos localmente antes de cargarlos con el botón **Cargar archivo**. De este modo, puede conservar una copia del recurso web si tiene que volver a una versión anterior. Puede usar un editor sencillo como el Bloc de notas, pero se recomienda uno que tenga funcionalidades más avanzadas. [Visual Studio Community](https://www.visualstudio.com/vs/community/) y [Visual Studio Code](https://code.visualstudio.com/) son gratuitos y proporcionan funcionalidades eficaces para editar los archivos de texto que utilizan los recursos web.  

<a name="BKMK_CreateAndEditFormWebResources"></a>
 
## <a name="create-and-edit-a-web-resource-on-a-form"></a>Creación y edición de recursos web en un formulario

Puede agregar o editar recursos web en un formulario con el fin de que sea más atractivo o útil para los usuarios. 

> [!NOTE]
> No puede incluir un recurso web en un encabezado o pie de página.  

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="navigate-to-a-form"></a>Desplazamiento a un informe
Con el Explorador de soluciones abierto, en **Componentes**, expanda **Entidades** y, a continuación, expanda la entidad con la que desea trabajar.

En la lista, elija **Formularios**, busque un formulario de tipo Principal y, a continuación, pulse o haga doble clic en la entrada para abrir y editar el formulario.

### <a name="add-or-edit-web-resource-in-a-form"></a>Adición o edición de recursos web en un formulario

Consulte [Propiedades de recurso web](web-resource-properties-legacy.md) para obtener información de las propiedades que puede establecer para los recursos web de un formulario.

### <a name="preview"></a>Vista previa

Para obtener una vista previa de cómo se mostrará el formulario principal y cómo funcionarán los eventos:
- En la pestaña **Inicio**, seleccione **Vista previa** y, a continuación, elija **Crear formulario**, **Actualizar formulario** o **Formulario de solo lectura**.
- Para cerrar el formulario de vista previa, en el menú **Archivo**, seleccione **Cerrar**.

### <a name="save"></a>Guardar

Cuando termine de editar el formulario, en la pestaña **Inicio**, seleccione **Guardar y cerrar** para cerrar el formulario. 

### <a name="publish"></a>Publicar

Cuando haya completado las personalizaciones, publíquelas:
- Si quiere publicar personalizaciones únicamente para el componente que está editando actualmente, en el panel de navegación, seleccione la entidad con la que ha estado trabajando y, a continuación, seleccione **Publicar**.
- Si el objetivo es publicar de una vez personalizaciones para todos los componentes sin publicar, en el panel de navegación, seleccione **Entidades** y, a continuación, en la barra de herramientas **Acciones**, seleccione **Publicar todas las personalizaciones**.
   
  
### <a name="see-also"></a>Vea también  

[Propiedades de recurso web](web-resource-properties-legacy.md) <br /> 
[Creación y diseño de formularios](create-design-forms.md) <br />
[Introducción a la personalización](getting-started-customization.md) <br /> 
[Documentación para desarrolladores: Recursos web para Customer Engagement](/dynamics365/customer-engagement/developer/web-resources)
