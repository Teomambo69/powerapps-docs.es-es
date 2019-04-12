---
title: Propiedades de iFrame para formularios principales de aplicaciones controladas por modelos en PowerApps | MicrosoftDocs
description: Comprender las propiedades de iFrame para formularios principales
Keywords: Formulario principal; propiedades de iFrame; Dynamics 365
author: Mattp123
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.author: matp
manager: kvivek
ms.date: 06/18/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 1b7e6a0c-18a9-47e2-aa7d-0cffb8c93b19
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="iframe-properties-for-model-driven-app-main-forms"></a>Propiedades de iFrame para formularios principales de aplicaciones controladas por modelos

Puede agregar los iFrame a un formulario para integrar contenido de otro sitio web en un formulario. 

Para ver las propiedades de IFrame, siga estos pasos.

1.  Iniciar sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

2.  Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Formularios**. 

3. En la lista de formularios, abra un formulario de tipo **Principal**. Luego en la pestaña **Insertar**, seleccione IFRAME para ver propiedades de IFRAME.

![iframe-properties](media/iframe-properties.png)


> [!NOTE]
> Los formularios no están diseñados para mostrarse en un iFrame.  
  
|Ficha|Propiedad|Descripción|  
|---------|--------------|-----------------|  
|**Generales**|**Nombre**|**Requerido**: nombre único para el iFrame. El nombre solo puede contener caracteres alfanuméricos y de subrayado.|  
||**Dirección URL**|**Requerido**: dirección URL de la página que se mostrará en el iFrame.|  
||**Pasar código tipo de objeto de registro e id. único como parámetros**|Los datos de la organización, el usuario y el registro se pueden pasar al iFrame. Más información: [Transferir parámetros a iFrames](iframe-properties-legacy.md#BKMK_PassParametersToIFRAMEs)|  
||**Etiqueta**|**Requerido**: etiqueta para mostrar para el iFrame.|  
||**Mostrar etiqueta en el formulario**|Si la etiqueta debe mostrarse.|  
||**Restringir scripting entre marcos cuando sea posible**|Se considera un riesgo de seguridad permitir que las páginas de un sitio web distinto interactúen con la aplicación Dynamics 365 mediante scripts. Use esta opción para limitar el scripting entre marcos en las páginas de las que no tiene el control.<br /><br />|  
||**Visible de forma predeterminada**|Mostrar el iFrame es opcional y se puede controlar mediante scripts. Más información: [Opciones de visibilidad](visibility-options-legacy.md)|
||**Habilitar para móvil**|Seleccione en la casilla para habilitar el iFrame para móviles.|  
|**Formato**|**Seleccione el número de columnas que ocupa el control**|Cuando la sección que contiene los iFrame tiene más de una columna puede establecer el campo para ocupar hasta el número de columnas que tiene la sección.|  
||**Seleccione el número de filas que ocupa el control**|Puede controlar el alto de los iFrame especificando el número de filas que ocupa el control.|  
||**Expandir automáticamente para usar el espacio disponible**|En lugar de establecer el alto mediante un número de filas, puede permitir que el alto del iFrame se expanda el espacio disponible.|  
||**Seleccione el tipo de desplazamiento para el iFrame**|Tiene tres opciones:<br /><br /> - **Como sea necesario**: muestra barras de desplazamiento cuando el tamaño del iFrame es mayor que el espacio disponible.<br />- **Siempre**: siempre se muestran barras de desplazamiento.<br />- **Nunca**: nunca se muestran barras de desplazamiento.|  
||**Mostrar borde**|Muestra un borde alrededor del iFrame.|  
|**Dependencias**|**Campos dependientes**|Un iFrame pueden interactuar con los campos del formulario mediante el script. Si se quita un campo del formulario, el script del iFrame se puede interrumpir. Agregue campos a los que hagan referencia los scripts de los iFrame en **Campos dependientes** para que no puedan quitarse accidentalmente.|  
  
## <a name="pass-parameters-to-iframes"></a>Pasar parámetros a iFrame  
 La información del registro se puede pasar habilitando la opción **Pasar código tipo de objeto de registro e id. único como parámetros**. Los valores que se pasan son:  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`orglcid`|LCID de idioma predeterminado de la organización.|  
|`orgname`|El nombre de la organización.|  
|`userlcid`|LCID de idioma preferido del usuario|  
|`type`|Código de tipo de entidad. Este valor puede ser diferente para las entidades personalizadas en distintas organizaciones. Use `typename` en su lugar.|  
|`typename`|Nombre del tipo de entidad.|  
|`id`|El valor de identificador del registro. este parámetro no incluye un valor hasta que se guarda el registro de la entidad.|  

## <a name="next-steps"></a>Pasos siguientes

[Utilizar el formulario Principal y sus componentes](use-main-form-and-components.md)
