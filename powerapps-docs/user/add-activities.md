---
title: Adición de una actividad de cita, correo electrónico, llamada telefónica, notas o tareas a la escala de tiempo en una aplicación basada en modelo | Microsoft Docs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 11/26/2018
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 308e36938c673a5f6ba83be02591a7199af20432
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2019
ms.locfileid: "61529571"
---
# <a name="add-an-appointment-email-phone-call-note-or-task-activity-to-the-timeline"></a>Agregue una actividad de cita, correo electrónico, llamada telefónica, nota o tarea a la escala de tiempo. 

Agregue **Actividades** al muro de la **Escala de tiempo** para realizar un seguimiento de todas las comunicaciones con un cliente o un contacto. Por ejemplo, puede tomar notas, agregar publicaciones, agregar una tarea, enviar un correo electrónico, agregar detalles de llamada telefónica o fijar citas. El sistema automáticamente agrega una marca de tiempo a cada actividad y muestra quién la creó. Usted y otras personas de su equipo pueden desplazarse por las actividades para ver el historial mientras trabajan con un cliente. 

- Las actividades que agregue desde un registro aparecen en el muro de la **escala de tiempo** del registro. 
- Si está configurado el campo **Referente a** de una actividad, la actividad aparece en el registro con el que está asociada. 
- También puede elegir el panel de filtro para filtrar las actividades por tipo de registro y fecha. 
- Cuando se crea una nueva actividad, obtendrá una notificación sobre **lo que se perdió** en el muro de la **escala de tiempo**.

  > [!div class="mx-imgBorder"]
  > ![Vista de la escala de tiempo de actividades en PowerApps](media/TimelineViewOfActivity.png "Timeline view of activities in PowerApps")  
 
## <a name="add-an-activity-from-the-nav-bar"></a>Adición de una actividad desde la barra de navegación
 
La forma más rápida de agregar una actividad es usar el acceso directo en la barra de navegación y, a continuación, vincularla a un registro. Por ejemplo, puede crear una actividad de llamada telefónica y, luego, vincularla a un contacto en el sistema mediante el campo **Referente a**.

1. En la barra de navegación, seleccione el **signo más** ![botón Crear registro](media/create-record-button.png "Create record button") y, a continuación, seleccione **Actividades**. 

   > [!div class="mx-imgBorder"]
   > ![Acceso directo para agregar una actividad en PowerApps](media/QuickCreate.png "Shortcut to add an activity in PowerApps")  
 
2. Elija el tipo de actividad que desea agregar.

3. Rellene la información necesaria. Use el campo **Referente a** para asociar la actividad a un registro.

4. Cuando termine,seleccione **Guardar**.

 
## <a name="add-a-phone-call"></a>Adición de una llamada telefónica  
  
1. Abra el registro al que desea agregar la actividad. Por ejemplo, un registro de contacto.
  
2. En el muro de la **escala de tiempo**, seleccione **signo más** > **Llamada de teléfono**. 


   > [!div class="mx-imgBorder"]
   > ![Adición de una actividad de teléfono en PowerApps](media/addphonecall.png "Add a phone activity in PowerApps")
  
3. Rellene el **Asunto** de la llamada.

     En el área **Notas**, escriba un resumen de la conversación con el cliente. 
  
     El campo **Llamar a** se rellena automáticamente con el registro al que agregó la actividad de llamada telefónica. Puede seleccionar un registro diferente si es necesario.  
  
4. De forma predeterminada, la dirección se establece en **Saliente**. Puede cambiarla a **Entrante** seleccionando **Saliente**. 
  
5. Cuando haya terminado de rellenar el formulario, seleccione **Guardar** para guardar la actividad.  
  
## <a name="add-a-task"></a>Adición de una tarea  
  
1. Abra el registro al que desea agregar la actividad. Por ejemplo, un registro de contacto.
  
2. En el muro de la **escala de tiempo**, seleccione **signo más** > **Tarea**.
  
3. El campo **Propietario** se establece en el usuario actual de forma predeterminada. Si desea volver a asignar la tarea, seleccione el icono de búsqueda y, a continuación, seleccione otro usuario o equipo.  
  
4. Cuando haya terminado de rellenar el formulario, seleccione **Guardar** para guardar la actividad. 
  
## <a name="add-an-email"></a>Adición de correo electrónico  

Para agregar una actividad de correo electrónico a un registro, primero debe guardar el registro al que está agregando la actividad.  
  
1. Abra el registro al que desea agregar la actividad. Por ejemplo, un registro de contacto.
  
2. En el muro de la **escala de tiempo**, seleccione **signo más** > **Correo electrónico**. 

3. Rellene el asunto del correo electrónico y use el espacio proporcionado para escribir el correo electrónico.
  
4. Para agregar datos adjuntos al correo electrónico, guárdelo. A continuación, en la sección **Datos adjuntos**, seleccione **+** para agregar datos adjuntos.  
  
5. Para usar una plantilla para el cuerpo del correo electrónico, en la barra de comandos, haga clic en **Insertar plantilla** y, a continuación, seleccione la plantilla.   
  
6. Cuando haya terminado de rellenar el formulario, seleccione **Enviar**. 
  
## <a name="add-an-appointment"></a>Adición de una cita  

Para agregar una actividad de cita a un registro, primero debe guardar el registro al que está agregando la actividad.  
  
1. Abra el registro al que desea agregar la actividad. Por ejemplo, un registro de contacto.
  
2. En el muro de la **escala de tiempo**, seleccione **signo más** > **Cita**.  
  
3. Use la información sobre herramientas para completar la información requerida.
  
4. Cuando haya terminado de rellenar el formulario, seleccione **Guardar** para guardar la cita.

## <a name="add-notes"></a>Agregar notas

También puede agregar notas fácilmente en el área de actividades.
  
1. Abra el registro al que desea agregar la actividad. Por ejemplo, un registro de contacto.
  
2. En el muro de la **escala de tiempo**, empiece a escribir sus notas. Use **Agregar un archivo adjunto** para agregar datos adjuntos a la nota.

3. Cuando haya terminado de rellenar el formulario, seleccione **Agregar nota** para guardar la nota.

   > [!div class="mx-imgBorder"]
   > ![Agregar una nota](media/addnote.png "Add a note")

Una vez que se haya agregado la nota, puede eliminarla o editarla. También puede agregar una nota con el **signo más** en la sección superior del muro de la **escala de tiempo**.


> [!div class="mx-imgBorder"]
> ![Actualizar una nota](media/addnote2.png "Update a note")

## <a name="add-a-post"></a>Adición de una publicación 

1. Abra el registro al que desea agregar la publicación. Por ejemplo, un registro de contacto.

2. En el muro de la **escala de tiempo**, seleccione **signo más** > **Publicación**. 

3. Escriba su publicación en el campo de texto 

4. Cuando haya terminado de rellenar el formulario, seleccione **Agregar** para guardar la publicación.

> [!div class="mx-imgBorder"]
> ![Actualizar una publicación](media/post.png "Add a post")
  
  Una vez que guarde la publicación, aparecerá en la parte superior del muro de la escala de tiempo.
  
## <a name="refresh-the-timeline"></a>Actualización de la escala de tiempo 

Puede actualizar el muro de la escala de tiempo para ver la información más actualizada.

En el muro de la **escala de tiempo**, seleccione ![botón Más ](media/MoreButton.png "More button") y, a continuación, seleccione **Actualización de escala de tiempo**.

> [!div class="mx-imgBorder"]
> ![Actualización de la escala de tiempo](media/refresh.png "Refresh the Timeline")


## <a name="use-the-filter-pane"></a>Uso del panel de filtros

Filtre rápidamente las actividades, notas o publicaciones del muro de la escala de tiempo por tipo de registro o tipo de actividad y fecha con el panel de filtro.

1. En el muro de la **escala de tiempo**, seleccione ![botón Más ](media/MoreButton.png "More button") y, a continuación, seleccione **Abrir panel de filtro**.

> [!div class="mx-imgBorder"]
> ![Panel de filtro de la escala de tiempo ](media/filterpane.png "Filter pane in the Timeline")

2. Cuando haya terminado la visualización de la información filtrada, para borrar el filtro, seleccione el icono de embudo **Borrar todos los filtros**. Así se restablecerá el filtro y aparecerá toda la información en el muro de la escala de tiempo.

> [!div class="mx-imgBorder"]
> ![Restablecer el filtro](media/resetfilter.png "Reset the filter")

## <a name="manage-activities"></a>Administración de actividades
Administre actividades directamente desde el muro de la escala de tiempo, incluida la asignación de una actividad a otra persona, la eliminación o el cierre de una actividad, la adición de una actividad a una cola, la apertura un registro asociado o la edición de notas y publicaciones.


> [!div class="mx-imgBorder"]
> ![Administrar activities.png](media/ManageActivities.png "ManageActivities.png")



