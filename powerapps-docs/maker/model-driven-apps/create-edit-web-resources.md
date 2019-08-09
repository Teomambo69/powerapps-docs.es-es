---
title: Crear o editar recursos web de aplicaciones controladas por modelos en PowerApps | MicrosoftDocs
description: Aprenda a crear o editar un recurso web.
ms.custom: ''
ms.date: 06/02/2018
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
ms.assetid: ef4ba8df-9ba9-4066-b40d-def9761c7de2
caps.latest.revision: 21
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-or-edit-model-driven-app-web-resources-to-extend-an-app"></a>Crear o editar recursos web de aplicaciones controladas por modelos para ampliar una aplicación

Los programadores usan recursos web normalmente para extender la aplicación utilizando archivos que se usan en el desarrollo web. Los usuarios de la aplicación es posible que necesiten administrar los recursos web proporcionados por un programador o un diseñador.  

> [!TIP]
> Para obtener información detallada de los recursos web, consulte [Documentación para desarrolladores: Recursos Web para Customer Engagement](/dynamics365/customer-engagement/developer/web-resources).<br /> Para obtener información sobre las dependencias de recursos web agregadas a PowerApps, consulte [Documentación para desarrolladores: Dependencias de recursos web](/dynamics365/customer-engagement/developer/web-resources)
   
<a name="BKMK_WhatAreWebResources"></a>

## <a name="what-are-web-resources"></a>¿Qué son los recursos web?  

Los recursos web son archivos virtuales almacenados en el sistema. Cada recurso web tiene un nombre único que se pueda usar en una dirección URL para recuperar el archivo. Piense en ellos de esta manera: Si tuviera acceso al servidor web real que ejecuta la aplicación web, podría copiar los archivos a ese sitio web. Pero con la mayoría de los servicios online no puede hacerlo.  En su lugar, puede usar recursos web para cargar archivos al sistema y luego hacer referencia a ellos por nombre como si los hubiera copiado como archivos en el servidor web.  
  
Por ejemplo, si crea una página HTML como un recurso web llamado "new_myWebResource.htm", podría abrir esa página en un explorador que use una dirección URL como ésta:  
 
`<base URL>/WebResources/new_myWebResource.htm`
  
donde *\<base URL>* es la parte de la dirección URL se usa para ver aplicaciones que finalizan en `dynamics.com`. Puesto que el recurso web son datos del sistema, sólo los usuarios con licencia de la organización pueden tener acceso a ellos de esta forma. Normalmente, recursos web se incluyen en formularios en lugar de hacer referencia a ellos directamente. El uso más común consiste en proporcionar bibliotecas de JavaScript para scripts de formularios.  
    
Puesto que los recursos web son datos del sistema y son compatibles con las soluciones, puede moverlos a distintas organizaciones exportándolos como parte de una solución e importando la solución a otra organización. Debe usar el explorador de soluciones para trabajar con recursos web.
  
## <a name="open-solution-explorer"></a>Abra el explorador de soluciones

La parte del nombre de cualquier recurso web que crea es el prefijo de personalización. Esto se establece en función del editor de soluciones para la solución en la que trabaja. Si le interesa el prefijo de personalización, asegúrese de que está trabajando en una solución no administrada donde el prefijo de personalización es el que desea para este recurso web. Más información: [Cambiar el prefijo del editor de soluciones](../common-data-service/change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-web-resources"></a>Ver recursos web

Con el explorador de soluciones abierto, en **Componentes** seleccione **Recursos web**.

![Ver recursos web](media/view-web-resources-solution-explorer.png)

<a name="BKMK_CreateAndEditWebResources"></a>

## <a name="create-or-edit-web-resources"></a>Crear o editar recursos web  

Mientras [visualiza recursos web](#view-web-resources), seleccione **Nuevo** para crear un nuevo recurso web o bien haga doble clic en un recurso web existente para editarlo.

![Formulario Nuevo recurso web](media/new-web-resource-form.png)

Complete el formulario para crear o editar el recurso web:
  
|Campo|Descripción|  
|-----------|-----------------|  
|**Nombre**|*Requerido*. Este es el nombre único para este recurso web. No se puede cambiar una vez guardado el recurso web.<br />&bull; Este nombre solo puede incluir letras, números, puntos y caracteres de barra diagonal (“/”) no consecutivos.<br /> &bull; El prefijo de personalización del editor de soluciones se antepondrá al nombre del recurso web.|  
|**Nombre para mostrar**|El nombre que se muestra si ve una lista de recursos web.|  
|**Descripción**|Una descripción del recurso web.|  
|**Tipo**|*Requerido*. Este es el tipo de recurso web. No se puede cambiar una vez guardado el recurso web.|  
|**Editor de texto**|Cuando el tipo de recurso web representa un tipo de archivo de texto, seleccione este botón para abrir una página para modificar el contenido mediante el editor de texto.<br />Más información: [Usar el editor de texto adecuadamente](#use-the-text-editor-appropriately)| 
|**Idioma**|Permite la selección de un idioma diferente. Esta opción sólo etiqueta el registro que almacena los datos del recurso web. No modifica el comportamiento del recurso web.|  
|**Cargar archivo**|Seleccione el botón **Examinar...** para elegir el archivo que se debe cargar como recurso web.<br />&bull; Puede cargar un archivo al crear un nuevo recurso web o para sobrescribir un recurso web existente.<br />&bull; La extensión del nombre de archivo debe coincidir con extensiones permitidas.<br />&bull;De forma predeterminada el archivo de tamaño máximo que se puede cargar como recurso web es 5 MB. Este valor se puede editar en Dynamics 365 Customer Engagement mediante **Configuración del sistema** > **pestaña Correo electrónico** > **Establecer límite de tamaño para archivos adjuntos**. Más información: [Cuadro de diálogo Configuración del sistema: pestaña Correo electrónico](https://docs.microsoft.com/dynamics365/customer-engagement/admin/system-settings-dialog-box-email-tab) |  
|**Dirección URL**|Una vez guardado el recurso web, se mostrará aquí la dirección URL del recurso web. Seleccione este vínculo para ver el recurso web en el explorador.|  
  
Después de haber agregado los cambios, elija **Guardar** y luego en **Publicar**.  

> [!NOTE]
> Los cambios en un recurso web no serán visibles en la aplicación hasta que se publique.
  
<a name="BKMK_UsingTextEditor"></a>
   
### <a name="use-the-text-editor-appropriately"></a>Use el editor de texto adecuadamente

El editor de texto proporcionado en la aplicación para los recursos web se debe usar sólo para ediciones simples de archivos de texto. Puede usarlo para crear y modificar los recursos web HTML, pero solo deberá modificar recursos web HTML creados mediante el editor de texto. El editor de texto está diseñado para contenido HTML muy sencillo. 

> [!IMPORTANT]
> Si el contenido de un recurso web HTML no se ha creado mediante el editor de texto, no use el editor de texto para editarlo.  
> El editor de texto usa un control que modifica el código fuente HTML de una forma que permite que sea editado. Estos cambios pueden hacer que la página se comporte de forma diferente en el explorador y hacer que código más sofisticado deje de funcionar. Al abrir un recurso web HTML con el editor de texto y guardarlo sin realizar ningún cambio pueden dañar algunos recursos web HTML.  Más información: [Documentación para desarrolladores: Usar el editor de texto para recursos web de HTML](/dynamics365/customer-engagement/developer/webpage-html-web-resources#use-the-text-editor-for-html-web-resources)
  
Se recomienda usar un editor externo para editar archivos de texto y volver a guardarlos localmente antes de cargarlos con el botón **Cargar archivo**. De esta manera puede mantener una copia del recurso web si necesita volver a una versión anterior. Puede usar un editor simple como Bloc de notas, pero se recomienda encarecidamente un editor de texto con funciones más avanzadas. [Visual Studio Community](https://www.visualstudio.com/vs/community/) y [Visual Studio Code](https://code.visualstudio.com/) son gratuitas y proporcionan eficaces capacidades para editar los archivos basados en texto que usan los recursos web basados.  

<a name="BKMK_CreateAndEditFormWebResources"></a>
 
## <a name="create-and-edit-a-web-resource-on-a-form"></a>Crear y editar un recurso web en un formulario

Puede agregar o editar recursos web en un formulario para aumentar su atractivo o utilidad para los usuarios. 

> [!NOTE]
> No se puede incluir un recurso web en un encabezado o pie de página de formulario.  

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="navigate-to-a-form"></a>Desplazarse a un formulario
Con el explorador de soluciones abierto, en **Componentes**, expanda **Entidades** y, a continuación, expanda la entidad con la que desea trabajar.

Elija **Formularios**, en la lista localice un formulario de tipo Principal y, a continuación, haga doble clic o pulse en la entrada para abrir y editar el formulario.

### <a name="add-or-edit-web-resource-in-a-form"></a>Agregar o editar un recurso web en un formulario

Consulte [Propiedades de recurso web](web-resource-properties-legacy.md) para obtener información acerca de las propiedades que puede establecer para los recursos web en un formulario.

### <a name="preview"></a>Vista previa

Para obtener una vista previa de cómo aparecerá el formulario principal y cómo funcionarán los eventos:
- En la ficha **Inicio**, seleccione **Vista previa** y, a continuación, seleccione **Formulario de creación**, **Formulario de actualización** o **Formulario de sólo lectura**.
- Para cerrar el formulario Vista previa, en el menú **Archivo**, seleccione **Cerrar**.

### <a name="save"></a>Guardar

Cuando haya terminado de modificar el formulario, en la pestaña **Inicio**, seleccione **Guardar y cerrar** para cerrar el formulario. 

### <a name="publish"></a>Publicación

Cuando haya completado las personalizaciones, publíquelas:
- Para publicar las personalizaciones únicamente para el componente que está editando actualmente, en la barra de navegación o en el panel de navegación, elija la entidad en la que ha estado trabajando, y seleccione **Publicar**.
- Para publicar personalizaciones de todos los componentes no publicados a la vez, en el Panel de navegación, seleccione **Entidades** y, en la barra de herramientas **Acciones**, seleccione **Publicar todas las personalizaciones**.
   
  
### <a name="see-also"></a>Vea también  

[Propiedades de recurso web](web-resource-properties-legacy.md) <br /> 
[Crear y diseñar formularios](create-design-forms.md) <br />
[Conocer los componentes de las aplicaciones basadas en modelos](model-driven-app-components.md) <br /> 
[Documentación para desarrolladores: Recursos web para Customer Engagement](/dynamics365/customer-engagement/developer/web-resources)
