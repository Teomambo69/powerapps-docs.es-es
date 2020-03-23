---
title: Configurar propiedades de encabezado en el diseñador de formularios | MicrosoftDocs
ms.custom: ''
ms.date: 09/30/2019
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 67173c01bc6a96f0ada55c62688db76ca0af0596
ms.sourcegitcommit: 6cffa70358fd2e388d64a01f906c8c196fbbdefb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/17/2020
ms.locfileid: "3069691"
---
# <a name="configure-header-properties-in-the-form-designer"></a>Configurar propiedades de encabezado en el diseñador de formularios

Los creadores pueden controlar la densidad de encabezados de formularios basados en modelo para que se ajusten a las necesidades de cualquiera que utilice el formulario.

## <a name="high-density-header"></a>Encabezado de alta densidad

El encabezado del formulario de alta densidad garantiza que la información clave esté siempre visible para los usuarios. Con el encabezado de alta densidad, el título del registro nunca se trunca. Incluso los títulos de registro largos se muestran en varias líneas. De forma similar, el encabezado de alta densidad también garantiza que hasta cuatro valores de campo sean directamente visibles en el encabezado y nunca se trunquen u oculten.  

Para asegurarse de que la información clave estén siempre es visible, el marco de trabajo muestra valores de campo de sólo lectura y los usuarios no pueden editar directamente los valores de campo del encabezado. Tampoco se permiten visualizaciones como componentes personalizados o recursos web.

Cuando un formulario no especifica la densidad del encabezado o cuando se crea un nuevo formulario, el marco de trabajo adopta de manera predeterminada el encabezado de alta densidad.

> [!div class="mx-imgBorder"] 
> ![Encabezado de formulario de alta densidad](media/form-header-high-density.png "Encabezado de formulario de alta densidad")
    
## <a name="low-density-header"></a>Encabezado de baja densidad
El encabezado de formulario de baja densidad permite a los usuarios editar directamente los valores de campo del encabezado. También permiten visualizaciones como componentes personalizados y recursos web.  
  
No obstante, a menudo tienen el inconveniente de que se trunque o no esté visible información clave. El encabezado de baja densidad trunca el título del registro así como valores de campo que se muestran en el encabezado. A menudo solo uno o dos campos son directamente visibles en el encabezado y el resto se desbordan y se muestran en un control flotante que requiere un clic adicional.

> [!div class="mx-imgBorder"] 
> ![Encabezado de formulario de baja densidad](media/form-header-low-density.png "Encabezado de formulario de baja densidad")

### <a name="configuring-header-density"></a>Configurar densidad de encabezado

Para configurar la densidad del encabezado de un formulario basado en modelo, siga estos pasos:
1.  Abra el diseñador de formularios para [crear o editar un formulario](create-and-edit-forms.md).
2.  Seleccione el encabezado del formulario seleccionando el encabezado en la vista previa de formularios o mediante la [vista de árbol](using-tree-view-on-form.md).
3.  En el panel de propiedades, seleccione **Alta densidad** para usar el encabezado de formulario de alta densidad o desactívelo para usar el encabezado de formulario de baja densidad.
4.  En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** para guardar y hacer que los cambios sean visibles para los usuarios.

> [!NOTE]
> Utilice el nuevo de diseñador de formularios. El diseñador de formularios clásico no ofrece la posibilidad de configurar la densidad de encabezado.

## <a name="header-flyout"></a>Control flotante de encabezado
Se muestra el control flotante de encabezado cuando los usuarios seleccionan el botón de contenido adicional en el encabezado del formulario. También permite a los usuarios editar valores de campo y también muestra visualizaciones como componentes personalizados o recursos web que forman parte del encabezado de formulario.

El comportamiento del control de flotante de encabezado cambia en función de la configuración densidad de encabezado.

### <a name="high-density-header-flyout"></a>Control flotante de encabezado de alta densidad
Con un encabezado de formulario de alta densidad el control flotante de encabezado muestra todos los campos de encabezado incluidos los cuatro campos que se muestran directamente en el encabezado. El marco de trabajo muestra de forma predeterminada el control flotante de encabezado cuando se usa el encabezado de alta densidad. Los creadores pueden controlar la visibilidad del control flotante de encabezado con un encabezado de alta densidad.

> [!div class="mx-imgBorder"] 
> ![Control flotante de encabezado de alta densidad](media/form-header-flyout-high-density.png "Control flotante de encabezado de alta densidad")

### <a name="low-density-header-flyout"></a>Control flotante de encabezado de baja densidad
Con un encabezado de formulario de baja densidad el control flotante de encabezado muestra sólo campos de desbordamiento, como campos que el formulario no puede mostrar directamente en el encabezado con el ancho del formulario. El control flotante de encabezado también se muestra o se oculta automáticamente en función del número de campos en el encabezado y el ancho del formulario. Los creadores no pueden controlar la visibilidad del control flotante de encabezado cuando se usa un encabezado de baja densidad.

> [!div class="mx-imgBorder"] 
> ![Control flotante de encabezado de baja densidad](media/form-header-flyout-low-density.png "Control flotante de encabezado de baja densidad")

### <a name="show-or-hide-the-header-flyout"></a>Mostrar u ocultar el control flotante del encabezado
Para mostrar u ocultar el control flotante de encabezado para un formulario basado en modelo, siga estos pasos:

1.  Abra el diseñador de formularios para [crear o editar un formulario](create-and-edit-forms.md).
2.  Seleccione el encabezado del formulario en la vista previa de formularios o utilice la [vista de árbol](using-tree-view-on-form.md) para seleccionarlo.
3.  En el panel de la propiedad, seleccione **Alta densidad** para usar un encabezado de formulario de alta densidad. 
4.  En el panel de propiedades, seleccione **Mostrar control flotante del encabezado** para hacer que el control de encabezado sea visible o desactívelo para ocultar el control flotante de encabezado.
5.  En la barra de comandos, seleccione **Guardar** para guardar el formulario o seleccione **Publicar** para guardar y hacer que los cambios sean visibles para los usuarios.

> [!NOTE]
> - Utilice el nuevo de diseñador de formularios. El diseñador de formularios clásico no ofrece la posibilidad de mostrar u ocultar el control flotante de encabezado.   
> - La visibilidad del control flotante de encabezado solo se pueden controlar cuando se usa un encabezado de formulario de alta densidad. Cuando se utiliza un encabezado de baja densidad, el control flotante de encabezado se muestra o se oculta automáticamente en función del número de campos en el encabezado y el ancho del formulario.
> - Una imagen de una entidad se mostrará en el encabezado solo si el atributo **Imagen principal** se define para la entidad y se habilita la propiedad de formulario **Mostrar imagen en el formulario**. Más información: [Campos de imagen](../common-data-service/types-of-fields.md#image-fields). <br />
    Los programadores pueden especificar una imagen para una entidad mediante el [atributo EntityMetadata.PrimaryImageAttribute](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.metadata.entitymetadata.primaryimageattribute?view=dynamics-general-ce-9). 


## <a name="form-designer-messages-related-to-form-headers"></a>Mensajes del diseñador de formularios relacionados con encabezados de formulario
Cuando se editan formularios con el diseñador de formularios nuevo o clásico, es posible que vea algunos mensajes relacionados con los encabezados del formulario. Debajo puede encontrar los detalles de cada mensaje y por qué lo está viendo.

### <a name="weve-upgraded-your-form-to-show-a-high-density-header-that-displays-more-data-you-can-edit-this-setting-in-the-properties-of-the-header"></a>Hemos actualizado el formulario para mostrar un encabezado de alta densidad que muestra más datos. Puede editar este valor en las propiedades del encabezado. 
Este mensaje se muestra en el diseñador de formularios cuando un creador crea un nuevo formulario principal (incluso mediante Guardar como acción) o edita un formulario principal que no se ha configurado previamente para la densidad de encabezado.  
  
El marco de trabajo utiliza de manera predeterminada el encabezado de alta densidad y este mensaje ayuda a los creadores a ser más conscientes de ese comportamiento. Los creadores pueden reemplazar el valor predeterminado del marco de trabajo en cualquier momento configurando manualmente la densidad del encabezado de formulario como se indicó antes.

### <a name="this-form-isnt-using-high-density-header-access-the-setting-in-the-header-properties-high-density-header-helps-display-more-data"></a>Este formulario no utiliza el encabezado de alta densidad, acceda al valor en las propiedades del encabezado. El encabezado de alta densidad ayuda a mostrar más datos. 
Este mensaje se muestra en el diseñador de formularios cuando un creador abre un formulario principal para editar que está configurado para usar el encabezado de baja densidad. 

El mensaje ayuda a incrementar el conocimiento sobre el encabezado de alta densidad y sus beneficios.

### <a name="field-moved-to-header-flyout-the-header-supports-displaying-up-to-four-read-only-field-values-the-field-field-display-name-will-now-only-be-available-from-the-flyout"></a>Campo movido a control flotante de encabezado: El encabezado admite mostrar hasta cuatro valores de campo de sólo lectura. El campo *nombre para mostrar del campo* ahora solo estará disponible desde el control flotante.
Este mensaje se muestra en el diseñador de formularios cuando un formulario usa el encabezado de alta densidad con el control flotante de encabezado visible.  
  
El encabezado de alta densidad muestra valores de solo lectura de los primeros cuatro campos del encabezado. Cuando los creadores agregan un campo en el encabezado en las cuatro posiciones superiores, hace que un campo existente que se mostraba directamente en el encabezado pase a estar extendido y sea visible solo en el control flotante de encabezado.      

El mensaje informa al creador del cambio y confirma si continuar con la acción.

### <a name="header-field-limit-exceeded-the-header-supports-displaying-up-to-four-read-only-field-values-remove-unused-fields-to-add-more"></a>Superado límite de campo de encabezado: El encabezado permite mostrar hasta cuatro valores de campo de sólo lectura. Quite campos no utilizados para agregar más. 
Este mensaje se muestra en el diseñador de formularios cuando un formulario usa el encabezado de alta densidad con el control flotante de encabezado oculto.  
  
El encabezado de alta densidad muestra valores de solo lectura de hasta cuatro campos en el encabezado. Puesto que el control flotante de encabezado está oculto, los usuarios no podrán ver los campos adicionales.  

El mensaje informa al creador que ya hay cuatro campos en el encabezado y evita agregar campos adicionales en el encabezado que los usuarios no podrán ver.

### <a name="header-does-not-display-custom-components-the-header-supports-displaying-up-to-four-read-only-field-values-remove-the-custom-component-from-the-field-before-adding-it-to-the-header"></a>El encabezado no muestra componentes personalizados: El encabezado permite mostrar hasta cuatro valores de campo de sólo lectura. Quite el componente personalizado del campo antes de agregarlo al encabezado.  
Este mensaje se muestra en el diseñador de formularios cuando un formulario usa el encabezado de alta densidad con el control flotante de encabezado oculto.  
  
El encabezado de alta densidad muestra valores de solo lectura de campos en el encabezado. Puesto que el control flotante de encabezado está oculto, los usuarios no podrán ver ningún componente personalizado asociada a los campos del encabezado.  

El mensaje informa al creador que está intentando agregar un campo con un componente personalizado asociada al encabezado y debe quitar el componente personalizado antes de agregar el campo al encabezado. Esto se debe a que los usuarios no podrán ver el componente personalizado en el encabezado.

### <a name="header-displays-read-only-field-values-the-header-supports-displaying-up-to-four-read-only-field-values-to-provide-editability-to-the-user-add-the-field-to-a-section-in-the-form"></a>El encabezado muestra valores de campo de solo lectura: El encabezado permite mostrar hasta cuatro valores de campo de sólo lectura. Para proporcionar funciones de edición al usuario, agregue campo a una sección del formulario.  
Este mensaje se muestra en el diseñador de formularios cuando un formulario usa el encabezado de alta densidad con el control flotante de encabezado oculto.  
  
El encabezado de alta densidad muestra valores de solo lectura de campos en el encabezado. Puesto que el control flotante de encabezado está oculto, los usuarios no podrán editar los valores de campo.  
  
El mensaje informa al creador de que los campos agregados al encabezado serán de solo lectura y que los campos que deseen que los usuarios editen también se deben agregar a una sección del formulario.

### <a name="header-field-values-are-not-editable-moving-a-field-from-the-body-to-the-header-will-display-as-a-read-only-value-to-maintain-editability-copy-the-field-to-the-header"></a>Los valores de campo del encabezado no se pueden editar: Si mueve un campo del cuerpo al encabezado se mostrará como valor de sólo lectura. Para mantener la capacidad de edición, copie el campo al encabezado.  
Este mensaje se muestra en el diseñador de formularios solo para formularios que usan un encabezado de alta densidad con el control flotante de encabezado oculto.  
  
El encabezado de alta densidad muestra valores de solo lectura de campos en el encabezado. Puesto que el control flotante de encabezado está oculto, los usuarios no podrán editar los valores de campo.  

El mensaje informa al creador de que está intentando mover un campo del cuerpo del formulario al encabezado del formulario. Si l hace, lo convertirá en de sólo lectura. Da al creador la opción de mover el campo al encabezado o de agregar una copia del campo al encabezado. Si mueve el campo al encabezado hará que el campo no esté disponible en la ubicación original en el cuerpo del formulario para que los usuarios lo editen. Si agrega una copia del campo al encabezado se quedará el campo en la ubicación original tal como está, garantizando que los usuarios puedan continuar para editándolo en el cuerpo del formulario.

### <a name="form-headers-now-default-to-high-density-to-display-more-data-use-the-new-form-designer-to-edit-header-density"></a>Los encabezados del formulario se establecen de forma predeterminada ahora como de alta densidad para mostrar más datos. Use el nuevo diseñador de formularios para editar la densidad de encabezado.  
Este mensaje se muestra en el diseñador de formularios clásico cuando un creador abre un formulario principal para editar y está configurado para usar el encabezado de baja densidad.  
  
Este mensaje ayuda a aumentar el conocimiento sobre el encabezado de alta densidad y sus beneficios y que los creadores deben usar el nuevo diseñador de formularios para configurar la densidad de encabezado.  

Este mensaje se muestra en el diseñador de formularios clásico cuando un creador abre un formulario principal para editar y está configurado para usar el encabezado de baja densidad. 

El mensaje ayuda a aumentar el conocimiento sobre el encabezado de alta densidad y sus beneficios y que los creadores deben usar el nuevo diseñador de formularios para configurar la densidad de encabezado.  

### <a name="this-form-is-using-high-density-header-for-the-best-authoring-experience-with-this-form-use-the-new-form-designer"></a>Este formulario usa el encabezado de alta densidad. Para obtener la mejor experiencia de creación con este formulario, use el nuevo diseñador de formularios. 
Este mensaje se muestra en el diseñador de formularios clásico cuando un creador abre un formulario principal para editar y está configurado para usar el encabezado de alta densidad.  
  
El diseñador de formularios clásico no proporciona una experiencia de creación WYSIWYG. Tampoco detecta ni previene o advierte a los creadores de las implicaciones de cambios que realizan en el encabezado del formulario. Por ejemplo, cuando edita un formulario que está usando el encabezado de alta densidad con el control flotante de encabezado oculto, el diseñador de formularios clásico no evita que los creadores agreguen más de cuatro campos al encabezado aunque este campo no estará disponible a los usuarios.  
  
El mensaje informa al creadores que cuando edite un formulario que está usando el encabezado de alta densidad deben usar el nuevo diseñador de formularios. Esto ayuda a garantizar que el creador conoce el impacto de sus cambios en el encabezado del formulario.

## <a name="see-also"></a>Vea también
[Información general del diseñador de formularios controlado por modelos](form-designer-overview.md)  
[Crear, editar o configurar formularios usando el diseñador de formularios](create-and-edit-forms.md)  
[Agregar, configurar, mover o eliminar campos de un formulario](add-move-or-delete-fields-on-form.md)  
[Agregar, configurar, mover o eliminar componentes de un formulario](add-move-configure-or-delete-components-on-form.md)  
[Agregar, configurar, mover o eliminar secciones de un formulario](add-move-or-delete-sections-on-form.md)  
[Agregar, configurar, mover o eliminar pestañas de un formulario](add-move-or-delete-tabs-on-form.md)  
[Agregar y configurar un componente de subcuadrícula en un formulario](form-designer-add-configure-subgrid.md)  
[Agregar y configurar un componente de vista rápida en un formulario](form-designer-add-configure-quickview.md)  
[Configurar un componente de búsqueda en un formulario](form-designer-add-configure-lookup.md)  
[Use la vista de árbol del diseñador de formularios](using-tree-view-on-form.md)  
[Crear y editar campos](../common-data-service/create-edit-field-portal.md)  
