---
title: Control de acceso a formularios de aplicaciones basadas en modelos en PowerApps | Microsoft Docs
description: Obtenga información sobre cómo controlar el acceso a los formularios principales.
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
tags: ''
ms.openlocfilehash: a895bd9ea0257585f942840924a7044a4dcc23fb
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39699309"
---
# <a name="control-access-to-model-driven-app-forms"></a>Control de acceso a formularios de aplicaciones basadas en modelos

 El acceso a los formularios principales se puede controlar de dos formas:  
  
- **Desactivar un formulario principal**  
  
     Puede establecer un estado activo o inactivo en formularios principales. Esta característica se incluyó principalmente para administrar nuevos formularios incluidos cuando las organizaciones de Dynamics 365 Customer Engagement actualizan, pero se puede usar para impedir que los usuarios puedan usar cualquier formulario principal.   
  
- **Asignar roles de seguridad al formulario principal**  
  
     Use esta opción para poner el formulario principal a disposición de grupos específicos.  
  
 Diferentes personas de su organización pueden interactuar con los mismos datos de maneras diferentes. Los administradores pueden depender de la capacidad de examinar información de un registro, y el personal de servicio puede necesitar un formulario que optimice la entrada de datos. Puede establecer distintos requisitos mediante la asignación de formularios a los roles de seguridad a los que pertenecen distintos grupos de usuarios.  
  
 Para conocer los procedimientos detallados, vea [Asignar roles de seguridad a los formularios](https://docs.microsoft.com/dynamics365/customer-engagement/admin/assign-security-roles-form).  
  
 Cuando haya más de un formulario principal o móvil definido para una entidad, puede seleccionar qué formularios podrán usar los usuarios según sus roles de seguridad. Dado que cada entidad debe tener la capacidad de mostrar un formulario para cualquier usuario, al menos se debe designar un formulario como un formulario "de reserva", es decir, un formulario visible para los usuarios cuyos roles de seguridad no tienen ningún formulario asignado explícitamente.  
  
> [!NOTE]
>  Los formularios de creación rápida y vista rápida no se pueden asignar a los roles de seguridad.  
  
 En el editor de formulario o en la cuadrícula de formularios puede asignar roles de seguridad a un formulario. Sin embargo, si hay solo un formulario para la entidad, no podrá desactivar la opción **Enabled for fallback** (Habilitado para reserva) en el cuadro de diálogo **Asignar roles de seguridad**. En este caso, aunque haya asignado los roles de seguridad al formulario, cualquier persona asociada a un rol de seguridad que no incluyó todavía podrá ver el formulario porque está habilitado para reserva.  
  
 Después de crear un segundo formulario principal o móvil para la entidad, podrá desactivar la opción **Enabled for fallback** (Habilitado para reserva) para uno de ellos. El sistema se asegurará de que siempre haya al menos un formulario habilitado para reserva.  
  
 Cuando haya más de un formulario principal, puede especificar un orden de formulario que controlará qué formulario verán de forma predeterminada las personas con permisos para ver los formularios. Si hay más de un formulario que pueden usar, pueden cambiar los formularios, y el formulario que elijan será el predeterminada hasta que elijan otro distinto. Esta preferencia se almacena en su explorador. Si usan un equipo o explorador diferente, verán el formulario predeterminado original.  
  
## <a name="strategies-to-manage-the-fallback-form"></a>Estrategias para administrar el formulario de reserva  
 Las estrategias para administrar el formulario de reserva incluyen las siguientes:  
  
<a name="BKMK_DoNotUseMultipleForms"></a>   
### <a name="all-users-view-the-same-form"></a>Todos los usuarios ven el mismo formulario  
 Si no se requieren varios formularios para una entidad, no es necesario un formulario de reserva.  
  
<a name="BKMK_Contingecyform"></a>   
### <a name="create-a-contingency-form"></a>Crear un formulario de contingencia  
 Si usa formularios basados en roles porque quiere restringir la información que los usuarios pueden ver o editar, considere la posibilidad de crear un formulario que muestre un mínimo de información. Después, en el cuadro de diálogo **Asignar roles de seguridad**, seleccione **Display only to these selected security roles** (Mostrar solo a estos roles de seguridad seleccionados), pero no seleccione ningún rol, salvo Administrador del sistema, y seleccione **Enabled for fallback** (Habilitado para reserva). El resultado es que este formulario nunca podrá verlo nadie, salvo el administrador del sistema y cualquier persona cuyos roles de seguridad no se han asociado con un formulario específico. Podría incluir un recurso web HTML en el formulario con información sobre por qué es visible en el formulario y un vínculo a información sobre cómo solicitar que se agregue a un rol de seguridad que está asociado con un formulario o que se incluya un nuevo rol de seguridad para un formulario.  
  
> [!NOTE]
>  No puede incluir un recurso web en un encabezado o pie de página.  
  
<a name="BKMK_CreateGenericForm"></a>   
## <a name="create-a-generic-form"></a>Crear un formulario genérico  
 Si usa formularios basados en roles para proporcionar una experiencia personalizada basada en un rol de usuario, puede establecer su formulario menos especializado como reserva y configurarlo para mostrarlo a todos los usuarios. Después, cree formularios personalizados para roles de seguridad específicos y configure dichos formularios para que se muestren solo a los roles de seguridad que los necesiten. No habilite estos formularios para reserva. Por último, en la lista **Formularios**, use el cuadro de diálogo **Orden de los formularios** para especificar qué formularios mostrar ordenándolos de más exclusivos a menos. El formulario de reserva estará en la parte inferior de la lista. Esta estrategia hará que las personas vean el formulario personalizado para su rol como el predeterminado, aunque pueden seguir usando el selector de formularios para seleccionar el formulario más común, si así lo desean. Cualquier formulario que seleccionen se convertirá en el predeterminado hasta que elijan otro distinto.  
  
<a name="BKMK_UseFormScripting"></a>   
## <a name="use-form-scripting"></a>Usar scripting de formulario  

 Por último, en la aplicación web es posible, pero no recomendable, que un desarrollador use scripts en el evento Onload del formulario para usar la [colección Xrm.Page.ui.formSelector.items](http://go.microsoft.com/fwlink/p/?LinkID=513300) para consultar los formularios disponibles y usar el método de navegación para remitir a los usuarios a un formulario específico. Recuerde que el [método de navegación](http://go.microsoft.com/fwlink/p/?LinkID=513301) hará que el formulario se vuelva a cargar y que se vuelva a producir el evento Onload. La lógica del controlador de eventos debe comprobar siempre alguna condición antes de usar el método de navegación para evitar un bucle sin fin o innecesariamente restringir las opciones de los usuarios para navegar entre formularios.  
  
 Este enfoque no funcionará en Dynamics 365 para tabletas porque varios formularios no están disponibles para su selección.  

### <a name="next-steps"></a>Pasos siguientes  

[Asignar roles de seguridad a los formularios](https://docs.microsoft.com/dynamics365/customer-engagement/admin/assign-security-roles-form)
