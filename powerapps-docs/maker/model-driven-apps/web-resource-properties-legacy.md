---
title: Propiedades de recursos web para formularios principales de aplicaciones controladas por modelos en PowerApps | Microsoft Docs
description: Información sobre las propiedades de recurso web para formularios principales
Keywords: Main form; Web resource properties; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/27/2018
ms.service: crm-online
ms.topic: article
ms.assetid: 82cd41ea-95b0-4606-9e7d-43eb5ce9ecd6
ms.openlocfilehash: a08ca32b1d300d4302064940e65fd1d067c3ade6
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39710399"
---
# <a name="web-resource-properties-for-model-driven-app-forms"></a>Propiedades de recursos web para formularios de aplicaciones controladas por modelos

Puede agregar o editar recursos web en un formulario con el fin de que sea más atractivo o útil para los usuarios de la aplicación. Los recursos web habilitados para formularios son imágenes o controles de archivos HTML.

> [!NOTE]
> Los recursos web de Silverlight están en desuso y no funcionarán en el cliente de interfaz unificada.

## <a name="access-web-resource-properties"></a>Acceso a las propiedades de recurso web

Al visualizar un formulario:
- **Al agregar un recurso web:**: seleccione la pestaña (por ejemplo, **General** o **Notas**) en la que desea insertarlo y, a continuación, en la pestaña **Insertar**, elija **Recurso web**.<br />![Insertar recurso web](media/insert-web-resource.png)
- **Al editar un recurso web**: seleccione una pestaña del formulario y el recurso web que desee editar, y, a continuación, en la pestaña **Inicio**, elija **Cambiar propiedades**. <br />![Cambio de las propiedades de recurso web](media/web-resource-change-properties.png)

Se abrirán los cuadros de diálogo **Agregar recurso web** o **Propiedades de recurso web**.

![Cuadro de diálogo Agregar recurso web](media/add-web-resource-dialog.png)


## <a name="web-resource-properties"></a>Propiedades de recurso web

 Los cuadros de diálogo **Agregar recurso web** o **Propiedades de recurso web** tendrán dos (a veces, tres) pestañas según el tipo de recurso web.

### <a name="general-tab"></a>Pestaña General

Estas propiedades definen el recurso web que se usará y cómo debe comportarse.

|Campo|Descripción|
|--|--|
|**Recurso web**|*Obligatorio*. Busque un recurso web existente o cree uno. Use la vista **Form Enabled Web Resource** (Recurso web habilitado para formularios) para incluir solo los recursos web de imagen y HTML que se pueden agregar como elementos visuales en un formulario.|
|**Nombre**|*Obligatorio*. Especifique un nombre para el control de recursos web que se agregará al formulario. Este valor identifica el control en el formulario.|
|**Etiqueta**|*Obligatorio*. Se genera automáticamente según el valor del campo **Nombre**. Especifique texto localizable para el control de recursos web que se agregará al formulario. Seleccione **Mostrar etiqueta en el formulario** si desea hacerlo visible.|
|**Visible de forma predeterminada**|Aunque esta opción está habilitada, el recurso web estará visible cuando se cargue el formulario. Si tiene un script de formulario o regla de negocio que mostrará el recurso web según sea necesario, desactive este campo. Más información: [Visualización u ocultación de los elementos de formulario](visibility-options-legacy.md)|
|**Habilitar para móvil**|Seleccione esta opción para permitir que este recurso web esté visible en las aplicaciones móviles.|

Según el tipo de recurso web que seleccione, establezca propiedades adicionales.

Para los recursos web HTML, verá las siguientes:

![Propiedades de recursos web HTML](media/web-resource-general-html-properties.png)

|Campo|Descripción|
|--|--|
|**Parámetros personalizados (datos)**|Normalmente, los datos de configuración se pasarán al recurso web HTML como un parámetro de cadena de consulta `data`. Los scripts asociados a la página HTML pueden acceder a estos datos y usarlos para cambiar el comportamiento de la página.|
|**Restringir scripting entre marcos cuando sea posible**|Use esta opción si no confía plenamente en el contenido del recurso web HTML. Más información: [Documentación para desarrolladores: Selección de si restringe el scripting entre marcos](/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form#select-whether-to-restrict-cross-frame-scripting)|
|**Pasar código tipo de objeto de registro e id. único como parámetros**|Los datos sobre el registro actual visible en el formulario pueden pasarse a la página de recursos web HTML para que el script que se ejecuta en la página pueda acceder a los datos sobre el registro. Más información: <br />[Transmisión de parámetros a recursos web](#pass-parameters-to-web-resources)<br />[Documentación para desarrolladores: Transmisión de información contextual sobre el registro](/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form#pass-contextual-information-about-the-record)|

Con los recursos web de imagen tiene la opción de especificar **texto alternativo**, que es importante para las tecnologías de ayuda que facilitan que la página sea accesible para todo el mundo.

<!-- TODO: Why are Custom Parameters available to pass to image web resources? -->

### <a name="formatting-tab"></a>Pestaña Formato

En la pestaña **Formato**, las opciones que se muestran varían según el tipo de recurso web insertado y el contexto donde se inserta. Algunas de estas opciones son especificar el número de filas y columnas para mostrar, determinar si se muestra un borde y el comportamiento de desplazamiento.

![Propiedades de formato de recursos web](media/web-resource-formatting-properties.png)

|Propiedad|Descripción|  
|--------------|-----------------|
|**Seleccione el número de columnas que ocupa el control**|Cuando la sección que contiene el recurso web tiene más de una columna, puede establecer el campo para ocupar hasta el número de columnas que tenga la sección.|  
|**Seleccione el número de filas que ocupa el control**|Puede controlar la altura del recurso web especificando un número de filas, o bien seleccione **Expandir automáticamente para usar el espacio disponible.** para permitir que la altura de los recursos web se expanda al espacio disponible.|  
|**Seleccione el tipo de desplazamiento para el elemento IFRAME**|Un recurso web HTML se agrega al formulario mediante un elemento IFRAME.<br /><br /> - **Como sea necesario**: muestra las barras de desplazamiento cuando el tamaño del recurso web es mayor que el disponible.<br />- **Siempre**: siempre se muestran las barras de desplazamiento.<br />- **Nunca**: nunca se muestran barras de desplazamiento.|  
|**Mostrar borde**|Muestra un borde alrededor del recurso web.|  


### <a name="dependencies-tab"></a>Pestaña Dependencias

Un recurso web puede interactuar con los campos del formulario mediante scripts. Si se quita un campo del formulario, se puede dañar el script del recurso web. Agregue todos los campos a los que hacen referencia los scripts del recurso web en los **campos dependientes** para que no se puedan quitar por accidente.

![Propiedades de dependencia de recursos web](media/web-resource-dependency-properties.png)
  
<a name="BKMK_PassingParametersToWebResource"></a> 
 
## <a name="pass-parameters-to-web-resources"></a>Transmisión de parámetros a recursos web 

Un recurso web HTML puede aceptar parámetros que se pasarán como parámetros de cadena de consulta.  
  
La información sobre el registro puede pasarse al habilitar la opción **Pasar código tipo de objeto de registro e id. único como parámetros**. Si se escribe información en el campo **Parámetro personalizado (datos)**, se pasará con el parámetro de datos. Los valores pasados son los siguientes:  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`data`|Este parámetro solo se pasa cuando se proporciona el texto para **Parámetro personalizado (datos)**.|  
|`orglcid`|El LCID del idioma predeterminado de la organización.|  
|`orgname`|El nombre de la organización.|  
|`userlcid`|El LCID del idioma preferido del usuario.|  
|`type`|**No use este parámetro**. El código de tipo de entidad. Este valor numérico puede ser diferente para las entidades personalizadas en distintas organizaciones. En su lugar, use el nombre del tipo de entidad.|  
|`typename`|El nombre del tipo de entidad.|  
|`id`|El valor de identificador del registro. Este parámetro no tiene ningún valor hasta que se guarda el registro de entidad.|  
  
No se permiten otros parámetros, ya que no se abriría el recurso web. Si necesita pasar varios valores, se puede sobrecargar el parámetro de datos para incluir más parámetros en él.

Más información: [Documentación para desarrolladores: Transmisión de información contextual sobre el registro](/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form#pass-contextual-information-about-the-record)

### <a name="see-also"></a>Vea también

[Crear o editar recursos web para ampliar una aplicación](create-edit-web-resources.md)<br />
[Utilizar el formulario principal y sus componentes](use-main-form-and-components.md)
