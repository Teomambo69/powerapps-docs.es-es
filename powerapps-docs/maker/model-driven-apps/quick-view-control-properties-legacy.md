---
title: Propiedades de los controles de vista rápida para formularios principales de aplicaciones controladas por modelos en Power Apps | MicrosoftDocs
description: Comprender las pPropiedades de los controles de vista rápida para formularios principales
Keywords: Propiedades de control de la vista rápida; Dynamics 365; Formularios principales
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 05/04/2020
ms.service: powerapps
ms.topic: article
ms.assetid: 68f68d5b-6c71-4b95-bb46-d48c59d9008e
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a76269092be62d2e8bb99138fb35b521cebb1f9c
ms.sourcegitcommit: 52b7f59e271437e86ffff226fb6c1982bf7f08b1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "3332450"
---
# <a name="model-driven-app-quick-view-control-properties"></a>Propiedades de los controles de vista rápida de aplicaciones controladas por modelos

Un control de vista rápida en un formulario de aplicación basada en modelos muestra datos de un registro seleccionado en una búsqueda en el formulario. Los datos que se muestran en el control se definen mediante un formulario de vista rápida. Los datos que se muestran no se pueden editar, pero cuando el campo principal se incluye en el formulario de vista rápida, se convierte en un vínculo para abrir el registro relacionado. Más información: [Crear y editar formularios de vista rápida](create-edit-quick-view-forms.md)  

> [!div class="mx-imgBorder"] 
> ![Formulario de vista rápida de contacto en el formulario de cuenta](media/quick-view-form-contact.png "Formulario de vista rápida de contacto en el formulario de cuenta")  

1.  Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  

2.  Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Formularios**.  

3.  Seleccione un formulario cuyo **Tipo** sea **Principal**.

4.  En el diseñador de formularios, seleccione **Agregar componente**.

5.  En el panel de navegación izquierdo, seleccione **Vista rápida**.

6.  En el cuadro de diálogo **Seleccionar formularios de vista rápida**, seleccione un campo **Buscar** incluido en el formulario y luego seleccione un formulario de vista rápida para las entidades relacionadas. Las entidades relacionadas que se muestran dependen del campo **Buscar** que elija.  

    > [!div class="mx-imgBorder"] 
    > ![Agregar un control de vista rápida](media/select-quick-view-form.png "Agregar un control de vista rápida a un formulario principal")

7.  Seleccione **Listo** para cerrar el cuadro de diálogo **Seleccionar formularios de vista rápida**. El formulario de vista rápida aparece en el formulario y las propiedades de la vista rápida aparecen en el panel Propiedades.

|Propiedad|Descripción|  
|--------------|-----------------|  
|**Etiqueta**|**Requerido**: etiqueta para mostrar para el formulario de vista rápida.|  
|**Nombre**|**Requerido**: nombre único para el formulario de vista rápida que se usa al hacerle referencia en los scripts.|  
|**Ocultar etiqueta**|Muestra la etiqueta en el formulario.| 
|**Formularios de vista rápida**|Enumera los formularios de vista rápida que seleccionó para las entidades relacionadas. 
|**Seleccionar formularios**|Seleccione o cambie los formularios de vista rápida seleccionados para las entidades relacionadas. Las entidades relacionadas que se muestran dependen del campo **Buscar** que elija.|  
|**Componentes**|Propiedades para configurar del componente. Un componente de control de vista rápida no tiene propiedades para configurar y, de forma predeterminada, se muestra si alguien está usando un navegador web, Dynamics 365 para teléfonos o Dynamics 365 para tabletas.

## <a name="quick-view-control-properties-in-classic-form-designer"></a>Propiedades de control de vista rápida en el diseñador de formularios clásico

1.  Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  

2.  Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Formularios**. 

3.  En la lista de formularios, abra el formulario de tipo **Principal**.

4.  En el menú de comandos, seleccione **Cambiar a clásico**.

5.  A continuación, en la pestaña **Insertar**, seleccione **Formulario de vista rápida** para ver las propiedades de control de vista rápida.

    > [!div class="mx-imgBorder"] 
    > ![quick-view-control](media/quick-view-control.png)
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|**Nombre**|**Requerido**: nombre único para el formulario de vista rápida que se usa al hacerle referencia en los scripts.|  
|**Etiqueta**|**Requerido**: etiqueta para mostrar para el formulario de vista rápida.|  
|**Mostrar etiqueta en el formulario**|Muestra la etiqueta en el formulario.|  
|**Campo de búsqueda**|Seleccione uno de los campos de búsqueda incluidos en el formulario.|  
|**Entidad relacionada**|Este valor depende de la opción de **Campo de búsqueda** que elija. Suele ser la entidad principal de la relación de entidad 1:N para la búsqueda.<br /><br /> Si la entidad incluye una búsqueda de **Cliente potencial** que pueda aceptar una cuenta o un contacto, en el campo **Formulario de vista rápida** puede elegir un formulario de vista rápida para la cuenta y el contacto cambiando este valor y después eligiendo otro formulario de vista rápida.|  
|**Formulario de vista rápida**|Si la **Entidad relacionada** tiene formularios de vista rápida puede seleccionarlos aquí. De lo contrario, seleccione **Nuevo** para crear uno.<br /><br /> Seleccione **Editar** para cambiar el formulario de vista rápida seleccionado.|  
|**Propiedades adicionales**|Puede especificar el estilo de representación predeterminado seleccionando la casilla.|

>[!NOTE] 
> Cuando agrega un campo de texto de varias líneas a un formulario de vista rápida, el formulario tendrá una altura de uno independientemente de cómo se establezca la altura de control del campo. Esto garantiza la representación adecuada del formulario mientras se mantiene la densidad. Observe que los campos de texto de varias líneas en otros tipos de formularios, como los formularios principales, funcionan de manera diferente a medida que el formulario se expande automáticamente en función de la cantidad de texto. 


## <a name="next-steps"></a>Pasos siguientes

[Utilizar el formulario Principal y sus componentes](use-main-form-and-components.md)
 
