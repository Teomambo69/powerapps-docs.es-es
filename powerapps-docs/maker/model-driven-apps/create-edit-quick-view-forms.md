---
title: Crear o editar formularios de vista rápida de aplicaciones controladas por modelos en Power Apps | MicrosoftDocs
description: Aprenda a crear o editar un formulario de vista rápida.
ms.custom: ''
ms.date: 03/13/2020
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
ms.assetid: 9b101734-cc11-4d05-bd45-eb611eae9931
caps.latest.revision: 14
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1e94b836fc7718f3aa259b677edc58419c98af06
ms.sourcegitcommit: 9f2694bd14d70798310b89a4673672c1bfad989d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/26/2020
ms.locfileid: "3167122"
---
# <a name="create-a-model-driven-app-quick-view-form-to-view-information-about-a-related-entity"></a>Crear un formulario de vista rápida de una aplicación controlada por modelos para ver información sobre una entidad relacionada

En este tema aprenderá a crear un formulario de vista rápida y a agregar un control de vista rápida a un formulario principal. 

Un formulario de vista rápida se puede agregar a otro formulario como un control de vista rápida. Proporciona una plantilla para ver información sobre un registro de entidad relacionada dentro de un formulario de otro registro de entidad. Esto significa que los usuarios de la aplicación no necesitan navegar a otro registro para ver la información que necesitan para realizar su trabajo.  
  
 Los controles de vista rápida están asociados a un campo de búsqueda que se incluye en un formulario. Si el valor del campo de búsqueda no está configurado, el control de vista rápida no estará visible. Los datos de los controles de vista rápida no se pueden editar y formularios de vista rápida no admiten scripts de formularios.  
  
 Dado que los formularios de vista rápida se ven mediante un control de vista rápida en un formulario, no incluyen las áreas de encabezado, pie de página y navegación. Los roles de seguridad no se pueden asignar a formularios de vista rápida ni se pueden activar o desactivar.  
  
<a name="BKMK_CreateQFV"></a>   
## <a name="create-a-quick-view-form"></a>Crear un formulario de vista rápida  
 Puede crear formularios de vista rápida mediante el editor de formularios de forma similar al proceso de creación de otros formularios. Los formularios de vista rápida son de solo lectura. Úselos para crear formularios solo con fines de lectura.  
  
1. Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  

2. Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Formularios**. 
  
3. En la barra de herramientas seleccione **Agregar formulario** > **Formulario de vista rápida**.  
  
5. En el panel **Formulario**, escriba un **Nombre para mostrar** y una **Descripción** para distinguir este formulario de vista rápida de cualquier otro.  
  
6. En el diseñador de formularios arrastre los campos que desee del **Explorador de campos** a la sección del formulario.

    > [!IMPORTANT]
    > Los campos obligatorios no se pueden eliminar de un formulario. Si agrega un campo Requerido al formulario y desea eliminarlo, debe eliminar el formulario y luego volver a crearlo. Cuando establece la propiedad Obligatorio para un campo, no se puede guardar un registro sin datos en este campo.

7. Para guarda el formulario, elija **Guardar**.  

8. Seleccione **Publicar** para ver el nuevo formulario en la aplicación. <!-- Which app? What does Publish do?-->
  
<a name="BKMK_EditQVF"></a>   
## <a name="edit-a-quick-view-form"></a>Editar un formulario de vista rápida  
 Los formularios de vista rápida tienen un diseño simplificado porque se han diseñado para visualizarse en una sección del formulario. Solo está disponible una pestaña de una sola columna. Solo puede agregar secciones, campos, subcuadrículas y espaciadores adicionales de una sola columna.   
  
  > [!IMPORTANT]
  > No se pueden eliminar los campos obligatorios. Si agrega un campo Obligatorio al formulario, no puede eliminarlo. Si no desea el campo del formulario, debe eliminar todo el formulario y volver a crearlo.
  
 Cuando edite un formulario de vista rápida, debe publicar los cambios antes de que estén visible en la aplicación.  
  
<a name="BKMK_AddQVF"></a>   
## <a name="add-a-quick-view-control-to-a-main-form"></a>Agregar un control de vista rápida a un formulario principal  
 Los formularios de vista rápida pueden agregarse solo a un formulario principal donde exista un campo de búsqueda que tenga como destino la entidad del formulario de vista rápida.  
  
1.  Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  

2.  Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Formularios**.  

3. Seleccione un formulario cuyo **Tipo** sea **Principal**.

4. En diseñador de formularios, desde el panel Componentes, seleccione **Vista rápida**.  
  
5.  En el cuadro de diálogo **Seleccionar formularios de vista rápida**, seleccione el campo **Buscar** y luego seleccione el valor del campo de búsqueda. Más información: [Propiedades de control de vista rápida](quick-view-control-properties-legacy.md).  

    > [!div class="mx-imgBorder"] 
    > ![Agregar un control de vista rápida](media/add-quick-view-control.png "Agregar un control de vista rápida a un formulario principal")

6.  Seleccione **Listo** para cerrar el cuadro de diálogo **Seleccionar formularios de vista rápida**. El formulario de vista rápida aparece en el formulario.

7.  Para guarda el formulario, elija **Guardar**.  

## <a name="next-steps"></a>Pasos siguientes   
 [Crear y diseñar formularios](create-design-forms.md)   
 [Crear o editar formularios de creación rápida](create-edit-quick-create-forms.md)
