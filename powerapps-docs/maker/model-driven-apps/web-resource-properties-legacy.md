---
title: Propiedades de recurso web para formularios principales de aplicaciones controladas por modelos en Power Apps | MicrosoftDocs
description: Comprender las propiedades de recurso web para formularios principales
Keywords: Formulario principal; propiedades de recurso web; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 04/03/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 82cd41ea-95b0-4606-9e7d-43eb5ce9ecd6
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7784c70c2559aeecb5fabb7f44efdfc644f55b33
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2867475"
---
# <a name="web-resource-properties-for-model-driven-app-forms"></a>Propiedades de recurso web para formularios de aplicaciones controladas por modelos

Puede agregar o editar recursos web en un formulario para aumentar su atractivo o utilidad para los usuarios de la aplicación. Los recursos web habilitados para formularios son imágenes o controles de archivos HTML.

> [!NOTE]
> Los recursos web de Silverlight están obsoletos y no funcionarán en el cliente de Interfaz unificada.

## <a name="access-web-resource-properties"></a>Acceder a propiedades de recurso web

Mientras visualiza un formulario:
- **Al agregar un recurso web**: seleccione la pestaña (por ejemplo, **General** o **Notas**) en la que desea insertarlo y en la pestaña **Insertar**, seleccione **Recurso web**.<br />![Insertar recurso de web](media/insert-web-resource.png)
- **Al editar un recurso web**: seleccione una pestaña de formulario y el recurso web que desee modificar y, a continuación, en la pestaña **Inicio**, seleccione **Cambiar propiedades**. <br />![Cambiar propiedades de recurso web](media/web-resource-change-properties.png)

Se abrirá el cuadro de diálogo **Agregar recurso web** o **Propiedades de recurso web**.

![Cuadro de diálogo Agregar recurso web](media/add-web-resource-dialog.png)

> [!IMPORTANT]
> Debe seleccionar la opción **Visible de forma predeterminada** para que el recurso web aparezca en el formulario y esté disponible para los usuarios.

## <a name="web-resource-properties"></a>Propiedades de recurso web

 El cuadro de diálogo **Agregar recurso web** o **Propiedades de recurso web** tendrá dos, a veces tres, fichas según el tipo de recurso web.

### <a name="general-tab"></a>Pestaña General

Estas propiedades definen el recurso web que se usará y cómo debe comportarse.

|Campo|Descripción|
|--|--|
|**Recurso de web**|*Requerido.* Busque un recurso web existente o cree uno nuevo. Use la vista **Recurso web habilitado para formularios** para incluir solo recursos web de HTML e imágenes que se puedan agregar como elementos visuales en un formulario.|
|**Nombre**|*Requerido.* Especifique un nombre para el control de recurso web que se agregará al formulario. Este valor identifica de forma exclusiva el control en el formulario.|
|**Etiqueta**|*Requerido.* Se genera automáticamente según el valor del campo **Nombre**. Especifique el texto localizable para el control de recurso web que se agregará al formulario. Seleccione **Mostrar etiqueta en el formulario** si desea que esté visible.|
|**Visible de forma predeterminada**|Mientras se habilita, el recurso web estará visible cuando se cargue el formulario. Si tiene una regla de negocio o script de formulario que mostrará el recurso web según sea necesario, desactive este campo. Más información: [Mostrar u ocultar elementos de formulario](visibility-options-legacy.md)|
|**Habilitar para móvil**|Seleccione esta opción para permitir que este recurso web sea visible en aplicaciones móviles.|

Según el tipo de recurso web que seleccione, establezca propiedades adicionales.

Para los recursos web de HTML verá los siguientes:

![Propiedades de recurso web de HTML](media/web-resource-general-html-properties.png)

|Campo|Descripción|
|--|--|
|**Parámetro personalizado (datos)**|Suelen ser los datos de configuración que se transferirán al recurso web de HTML como parámetro de cadena de consulta de `data`. Los scripts asociados a la página HTML pueden acceder a estos datos y usarlos para cambiar el comportamiento de la página.|
|**Restringir scripting entre marcos cuando sea posible**|Use esta opción si no confía plenamente en el contenido del recurso de web de HTML. Más información: [Documentación para desarrolladores: Seleccionar si se restringe el scripting entre marcos](/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form#select-whether-to-restrict-cross-frame-scripting)|
|**Pasar código tipo de objeto de registro e id. único como parámetros**|Los datos sobre el registro actual visible en el formulario se pueden transferir a la página del recurso web de HTML para que el script que se ejecuta en la página pueda acceder a los datos sobre el registro. Más información: <br />[Pasar parámetros a recursos web](#pass-parameters-to-web-resources)<br />[Documentación para desarrolladores: Transferir información contextual sobre el registro](/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form#pass-contextual-information-about-the-record)|

Para los recursos web de imagen tiene la opción de especificar el **Texto alternativo** que es importante para las tecnologías de ayuda que hacen la página accesible para todos.

<!-- TODO: Why are Custom Parameters available to pass to image web resources? -->

### <a name="formatting-tab"></a>Pestaña Formato

En la pestaña **Formato**, las opciones que se muestran varían en función del tipo de recurso web insertado y del contexto en que se inserta. Estas opciones incluyen especificar el número de columnas y filas mostradas, si se muestra un borde y el comportamiento de desplazamiento.

![Propiedades de formato de recurso web](media/web-resource-formatting-properties.png)

|Propiedad|Descripción|  
|--------------|-----------------|
|**Seleccione el número de columnas que ocupa el control**|Cuando la sección que contiene el recurso web tiene más de una columna, puede establecer que el campo ocupe hasta el número de columnas que tiene la sección.|  
|**Seleccione el número de filas que ocupa el control**|Puede controlar la altura del recurso web especificando varias filas o seleccionando **Expandir automáticamente para usar el espacio disponible** para permitir que la altura del recurso web se expanda según el espacio disponible.|  
|**Seleccione el tipo de desplazamiento para el IFrame**|Un recurso web HTML se agrega al formulario mediante un IFRAME.<br /><br /> - **Como sea necesario**: muestra barras de desplazamiento cuando el tamaño del recurso web es mayor que el espacio disponible.<br />- **Siempre**: siempre se muestran barras de desplazamiento.<br />- **Nunca**: nunca se muestran barras de desplazamiento.|  
|**Mostrar borde**|Muestra un borde alrededor del recurso web.|  


### <a name="dependencies-tab"></a>Pestaña Dependencias

Un recurso web pueden interactuar con los campos del formulario mediante el script. Si se quita un campo del formulario, el script del recurso web se puede interrumpir. Agregue campos a los que hagan referencia los scripts del recurso web en **Campos dependientes** para que no puedan quitarse accidentalmente.

![Propiedades de dependencia de recurso web](media/web-resource-dependency-properties.png)
  
<a name="BKMK_PassingParametersToWebResource"></a> 
 
## <a name="pass-parameters-to-web-resources"></a>Pasar parámetros a recursos web 

Un recurso web HTML puede aceptar que los parámetros se pasen como parámetros de cadena de consulta.  
  
La información del registro se puede pasar habilitando la opción **Pasar código tipo de objeto de registro e id. único como parámetros**. Si la información se escribe en el campo **Parámetro personalizado (datos)** se pasará mediante el parámetro de datos. Los valores que se pasan son:  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`data`|Este parámetro solo se pasa cuando se proporciona texto para **Parámetro personalizado (datos)**.|  
|`orglcid`|LCID de idioma predeterminado de la organización.|  
|`orgname`|El nombre de la organización.|  
|`userlcid`|LCID de idioma preferido del usuario|  
|`type`|**No usar.** El código de tipo de entidad. Este valor numérico puede ser diferente para las entidades personalizadas en distintas organizaciones. Utilice el nombre de tipo de entidad en su lugar.|  
|`typename`|Nombre del tipo de entidad.|  
|`id`|El valor de identificador del registro. Este parámetro no incluye un valor hasta que se guarda el registro de la entidad.|  
  
No se permite ningún otro parámetro y el recurso web no se abrirá si se usan otros parámetros. Si necesita pasar varios valores, el parámetro de datos puede sobrecargarse para incluir varios parámetros.

Más información: [Documentación para desarrolladores: Transferir información contextual sobre el registro](/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form#pass-contextual-information-about-the-record)

### <a name="see-also"></a>Vea también

[Crear o editar recursos web para extender una aplicación](create-edit-web-resources.md)<br />
[Utilizar el formulario principal y sus componentes](use-main-form-and-components.md)
