---
title: Propiedades de los controles de vista rápida para formularios principales de aplicaciones controladas por modelos en PowerApps | MicrosoftDocs
description: Comprender las pPropiedades de los controles de vista rápida para formularios principales
Keywords: Propiedades de control de la vista rápida; Dynamics 365; Formularios principales
author: Mattp123
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.author: matp
manager: kvivek
ms.date: 06/06/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 68f68d5b-6c71-4b95-bb46-d48c59d9008e
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="model-driven-app-quick-view-control-properties"></a>Propiedades de los controles de vista rápida de aplicaciones controladas por modelos

Un control de vista rápida en un formulario de aplicación basada en modelos muestra datos de un registro seleccionado en una búsqueda en el formulario. Los datos que se muestran en el control se definen mediante un formulario de vista rápida. Los datos que se muestran no se pueden editar, pero cuando el campo principal se incluye en el formulario de vista rápida, se convierte en un vínculo para abrir el registro relacionado. Más información: [Crear y editar formularios de vista rápida](create-edit-quick-view-forms.md)  

> [!div class="mx-imgBorder"] 
> ![Formulario de vista rápida de contacto en el formulario de cuenta](media/quick-view-form-contact.png "Formulario de vista rápida de contacto en el formulario de cuenta")  

Puede acceder a las **Propiedades de controles de vista rápida** desde el sitio de PowerApps. 
1.  Iniciar sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  


2.  Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Formularios**. 

3. En la lista de formularios, abra el formulario de tipo **Principal**. A continuación, en la pestaña **Insertar**, seleccione **Formulario de vista rápida** para ver las propiedades de control de vista rápida.

    ![quick-view-control](media/quick-view-control.png)
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|**Nombre**|**Requerido**: nombre único para el formulario de vista rápida que se usa al hacerle referencia en los scripts.|  
|**Etiqueta**|**Requerido**: etiqueta para mostrar para el formulario de vista rápida.|  
|**Mostrar etiqueta en el formulario**|Muestra la etiqueta en el formulario.|  
|**Campo de búsqueda**|Seleccione uno de los campos de búsqueda incluidos en el formulario.|  
|**Entidad relacionada**|Este valor depende de la opción de **Campo de búsqueda** que elija. Suele ser la entidad principal de la relación de entidad 1:N para la búsqueda.<br /><br /> Si la entidad incluye una búsqueda de **Cliente potencial** que pueda aceptar una cuenta o un contacto, en el campo **Formulario de vista rápida** puede elegir un formulario de vista rápida para la cuenta y el contacto cambiando este valor y después eligiendo otro formulario de vista rápida.|  
|**Formulario de vista rápida**|Si la **Entidad relacionada** tiene formularios de vista rápida puede seleccionarlos aquí. De lo contrario, seleccione **Nuevo** para crear uno.<br /><br /> Seleccione **Editar** para cambiar el formulario de vista rápida seleccionado.|  
|**Propiedades adicionales**|Puede especificar el estilo de representación predeterminado seleccionando la casilla.|

## <a name="next-steps"></a>Pasos siguientes

[Utilizar el formulario Principal y sus componentes](use-main-form-and-components.md)
 
