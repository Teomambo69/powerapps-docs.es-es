---
title: Crear y diseñar formularios de aplicaciones controladas por modelos | MicrosoftDocs
ms.custom: ''
ms.date: 12/06/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.assetid: 99c795e0-9165-4112-85b1-6b5e1a4aa5ec
caps.latest.revision: 33
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
# <a name="create-and-design-model-driven-app-forms"></a>Crear y diseñar formularios de aplicaciones controladas por modelos 

Con PowerApps, los formularios ofrecen la interfaz de usuario que emplean los usuarios para interactuar con los datos que necesitan para realizar su trabajo. Es importante que los formularios que usan los usuarios estén diseñados para permitirles buscar o especificar la información que necesitan de manera eficaz. 

En la solución predeterminada o en una solución no administrada, se pueden crear nuevos formularios o editar los formularios existentes de todas las entidades que admitan personalizaciones de formularios. En una solución no administrada, se pueden editar las propiedades administradas para una entidad personalizada no administrada creada para la solución.
Si está viendo una solución administrada, aquí no se pueden crear nuevos formularios ni editar los formularios existentes entre las entidades. Sin embargo, si las propiedades administradas de una entidad de la solución administrada están establecidas para admitir personalizaciones, se pueden agregar o editar formularios a esa entidad. 
  

<a name="BKMK_TypesOfForms"></a> 
## <a name="type-of-forms"></a>Tipos de formularios
Hay diferentes tipos de formularios y cada tipo tiene una funcionalidad o uso específico. Más información: [Tipo de formularios en PowerApps](types-forms.md).  

  
<a name="BKMK_FormDifferencesByEntity"></a>   
## <a name="updated-versus-classic-entities"></a>Actualización frente a entidades clásicas  
PowerApps ofrece diversas opciones para diseñar formularios. Con interfaz unificada, la mayoría de las entidades se actualizaron para adaptarse a la interfaz de dinámica. Las entidades actualizadas, igual que las entidades personalizadas, incluyen soporte para el cliente, flujos de proceso de negocio y reglas de negocio de Dynamics 365 for tablets. Al usar estas entidades, puede diseñar una vez e implementar en todos los clientes.  
  
Todavía existen varias entidades, referidas aquí como entidades clásicas, que mantienen la apariencia y las capacidades de las versiones anteriores. Estas entidades se utilizan menos a menudo. Aquí se enumeran:  
  
||||||  
|-|-|-|-|-|  
|Dirección|Artículo|Comentario de artículo|Operación de eliminación en masa|Conexión|  
|Descuento|Lista de descuentos|Ubicación de documentos|Datos adjuntos de correo electrónico|Seguimiento|  
|Objetivo|Métrica del objetivo|Importar archivo de origen|Producto de la factura|Producto del pedido|  
|Lista de precios|Elemento de cola|Producto de oferta|Campo Informe|Consulta de informe|  
|Vista guardada|Servicio|Actividad de servicio|Sitio de SharePoint|Ubicación|  
|Zona de ventas|Unidad|Unidad de venta|||  
  
## <a name="form-display-faq"></a>Preguntas frecuentes de visualización de formularios

### <a name="why-is-my-form-not-visible-in-the-form-selector-drop-down-in-my-app"></a>¿Por qué no el formulario no es visible en el desplegable selector de formularios de mi aplicación?
Un formulario puede no estar disponible porque no se ha agregado a la aplicación.
1. Abra la aplicación en el diseñador de aplicaciones.
2. En la área **Vista de la entidad** seleccione **Formularios** junto a la entidad.
3. En la pestaña **Componentes** compruebe los formularios principales que están incluidos en la aplicación. Compruebe que el formulario que desea mostrar esté comprobado. De lo contrario, selecciónelo, guárdelo y, a continuación publique la aplicación.

   > [!div class="mx-imgBorder"] 
   > ![](media/forms-included-in-app.png "Formularios incluidos con la aplicación")
   
### <a name="why-isnt-my-form-displayed-as-the-default-form-in-the-app"></a>¿Por qué mi formulario no se muestra como formulario predeterminado en la aplicación?
Un formulario se puede establecer como el formulario predeterminado a través de la configuración de orden de los formularios o cuando un usuario establece el formulario predeterminado como valor de personalización.
1. Abra el explorador de soluciones. Expanda la entidad que tiene que los formularios que desea ordenar y, a continuación seleccione **Formularios**.
2. En la barra de herramientas seleccione **Propiedades del formulario** > **Conjunto de formularios principal**. 

   > [!div class="mx-imgBorder"] 
   > ![](media/form-order-toolbar.png "Comando de la barra de herramientas Orden de los formularios")
   
3. Se muestra el orden de los formularios. Seleccione el formulario y utilice las flechas arriba y abajo para mover el formulario dentro del orden de los formularios. El formulario en la parte superior de la lista es el formulario predeterminado. 

   > [!div class="mx-imgBorder"] 
   > ![](media/form-order-dialog.png "Diálogo Orden de formularios")
   
4. Seleccione **Aceptar** para guardar los cambios del orden de formularios.
5. En la barra de herramientas del diseñador de formularios, seleccione **Publicar** para hacer que el orden de los formularios esté disponible en aplicaciones.
 
#### <a name="form-order-user-personalization-setting"></a>Valor de personalización del usuario del orden de formularios
Tenga en cuenta que, cuando un usuario de la aplicación cambia la selección de formularios en el desplegable del selector de formularios, dicho formulario se vuelve el formulario predeterminado para el usuario. Esta personalización invalida el formulario predeterminado especificado para la entidad en la aplicación.

   > [!div class="mx-imgBorder"] 
   > ![](media/change-form-user-setting.png "Valor de usuario para cambiar el formulario predeterminado")
   
### <a name="related-topics"></a>Temas relacionados  
    
[Asignar un orden de formularios](assign-form-order.md) <br />
[Controlar el acceso a los formularios](control-access-forms.md) <br />
[Cómo se presentan los formularios principales en los distintos clientes](main-form-presentations.md) <br />
