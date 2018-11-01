---
title: Controlar el acceso a formularios de aplicaciones controladas por modelos en PowerApps | MicrosoftDocs
description: Aprenda a controlar el acceso a los formularios principales
ms.custom: ''
ms.date: 06/27/2018
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
ms.assetid: 15d123e0-b604-45dd-ab34-0b37787a04bb
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="control-access-to-model-driven-app-forms"></a>Controlar el acceso a formularios de aplicaciones controladas por modelos

 Hay dos formas para controlar el acceso a los formularios principales:  
  
- **Desactivar un formulario principal**  
  
     Puede establecer un estado activo o inactivo para los formularios principales. Esta característica se incluyó inicialmente para administrar los nuevos formularios incluidos cuando las organizaciones de Dynamics 365 Customer Engagement realizaban una actualización, pero se puede usar para impedir que los usuarios puedan usar formularios principales.   
  
- **Asignar roles de seguridad al formulario principal**  
  
     Use este método para poner un formulario principal a disposición de grupos específicos.  
  
 Diferentes personas de la organización pueden interactuar con los mismos datos de maneras distintas. Los administradores pueden depender de la capacidad de buscar rápidamente información en un registro y el personal de servicio podría necesitar un formulario que simplifique la entrada de datos. Puede satisfacer distintos requisitos mediante la asignación de formularios a los roles de seguridad a los que pertenecen los distintos grupos de usuarios.  
  
 Para conocer los procedimientos paso a paso, consulte [Assign security roles to forms](https://docs.microsoft.com/dynamics365/customer-engagement/admin/assign-security-roles-form).  
  
 Si tiene más de un formulario principal o móvil definido para una entidad, puede seleccionar los formularios que podrán utilizar los usuarios en función de sus roles de seguridad. Dado que cada entidad debe poder mostrar un formulario para cualquier usuario, al menos un formulario debe designarse como formulario de "reserva" (un formulario visible para los usuarios cuyos roles de seguridad no tienen ningún formulario explícitamente asignado).  
  
> [!NOTE]
>  Los formularios de creación rápida y de vista rápida no se pueden asignar a roles de seguridad.  
  
 En el editor de formularios o desde la cuadrícula de formularios puede asignar roles de seguridad a un formulario. No obstante, mientras haya solo un formulario para la entidad, no podrá desactivar la opción **Habilitado para reserva** en el cuadro de diálogo **Asignar roles de seguridad**. En este caso, aunque haya asignado roles de seguridad al formulario, cualquier persona asociada a un rol de seguridad que no incluyó podrá ver el formulario debido a que está habilitado para reserva.  
  
 Después de crear un segundo formulario principal o móvil para la entidad, podrá desactivar la opción **Habilitado para reserva** para uno de ellos. El sistema siempre garantizará que al menos un formulario esté habilitado para reserva.  
  
 Si tiene más de un formulario principal, puede especificar que un orden de formularios para controlar el formulario que podrá ver un usuario sea aquel que ve de forma predeterminada. Si hay más de un formulario que pueden usar, puede cambiar los formularios y aquel que elija será su formulario predeterminado hasta que elija otro. Esta preferencia se almacena en el explorador. Si usa un equipo o un explorador diferente, verá el formulario predeterminado original.  
  
## <a name="strategies-to-manage-the-fallback-form"></a>Estrategias para administrar el formulario de reserva  
 Algunas estrategias para administrar el formulario de reserva son:  
  
<a name="BKMK_DoNotUseMultipleForms"></a>   
### <a name="all-users-view-the-same-form"></a>Todos los usuarios ven el mismo formulario  
 Si no requiere formularios múltiples para una entidad, no necesita un formulario de reserva.  
  
<a name="BKMK_Contingecyform"></a>   
### <a name="create-a-contingency-form"></a>Crear un formulario de contingencia  
 Si usa formularios basados en roles porque desea limitar la información que los usuarios pueden ver o editar, considere la posibilidad de crear un formulario que muestre la información mínima. A continuación, en el cuadro **Asignar roles de seguridad**, seleccione **Mostrar solo a estos roles de seguridad determinados**, pero no seleccione ningún rol excepto el de administrador del sistema y seleccione **Habilitado para reserva**. El resultado es que este formulario nunca lo verá nadie excepto el administrador del sistema y cualquier usuario cuyos roles de seguridad no se hayan asociado a un determinado formulario. Podría incluir un recurso web HTML en el formulario con la información sobre los motivos de mostrar poca información en el formulario y un vínculo a información sobre cómo solicitar que se le agregue a un rol de seguridad asociado a un formulario o incluir un nuevo rol de seguridad para un formulario.  
  
> [!NOTE]
>  No se puede incluir un recurso web en un encabezado o pie de página de formulario.  
  
<a name="BKMK_CreateGenericForm"></a>   
## <a name="create-a-generic-form"></a>Crear un formulario genérico  
 Si usa formularios basados en roles para proporcionar una experiencia personalizada en función del rol de un usuario, puede establecer el formulario menos especializado como formulario de reserva y configurarlo para que todo el mundo pueda verlo. A continuación, cree formularios personalizados para roles de seguridad específicos y configúrelos para que se muestren únicamente a los roles de seguridad que los necesiten. No habilite estos formularios para reserva. Por último, en la lista **Formularios**, utilice el diálogo **Orden de los formularios** para especificar los formularios que desee mostrar clasificándolos del más exclusivo al menos exclusivo. El formulario de reserva estará en la parte inferior de la lista. Con esta estrategia, los usuarios que vean el formulario personalizado para su rol como formulario predeterminado, todavía podrán usar el selector de formulario para seleccionar el formulario más común si lo desean. Cualquier formulario que seleccionen se mantendrá como su formulario predeterminado hasta que seleccionen otro.  
  
<a name="BKMK_UseFormScripting"></a>   
## <a name="use-form-scripting"></a>Usar el scripting de formularios  

 Por último, en la aplicación web es posible, aunque no se recomienda, que un desarrollador use scripts en el evento Onload del formulario para usar la colección [Xrm.Page.ui.formSelector.items](http://go.microsoft.com/fwlink/p/?LinkID=513300) para consultar los formularios disponibles y usar el método de navegación para dirigir a los usuarios a un determinado formulario. Recuerde que el [método de navegación](http://go.microsoft.com/fwlink/p/?LinkID=513301) provocará que el formulario se cargue de nuevo (y el evento Onload se produzca de nuevo). Su lógica del controlador de eventos debe comprobar siempre alguna condición antes de que use el método de navegación para evitar un bucle sin fin o la restricción innecesaria de las opciones de los usuarios para desplazarse entre los formularios.  
  
 Este método no funcionará en Dynamics 365 for tablets porque no existen formularios múltiples disponibles para seleccionar.  

### <a name="next-steps"></a>Pasos siguientes  

[Asignar roles de seguridad a formularios](https://docs.microsoft.com/dynamics365/customer-engagement/admin/assign-security-roles-form)
