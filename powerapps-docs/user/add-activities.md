---
title: Adición de una actividad de cita, correo electrónico, llamada telefónica, notas o tareas a la escala de tiempo en una aplicación basada en modelo | Microsoft Docs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/03/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: dee8b918efc60fed57cc6d8ca407e6cafe2b8060
ms.sourcegitcommit: bee698ca0d11524377b67813a65e1a022d08c05e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73609900"
---
# <a name="add-an-appointment-email-phone-call-note-or-task-activity-to-the-timeline"></a>Agregue una actividad de cita, correo electrónico, llamada telefónica, nota o tarea a la escala de tiempo. 


Agregue **Actividades** al muro de la **Escala de tiempo** para realizar un seguimiento de todas las comunicaciones con un cliente o un contacto. Por ejemplo, puede tomar notas, agregar publicaciones, agregar una tarea, enviar un correo electrónico, agregar detalles de llamada telefónica o fijar citas. El sistema automáticamente agrega una marca de tiempo a cada actividad y muestra quién la creó. Usted y otras personas de su equipo pueden desplazarse por las actividades para ver el historial mientras trabajan con un cliente. 

- Las actividades que agregue desde un registro aparecen en el muro de la **escala de tiempo** del registro. 
- Si está configurado el campo **Referente a** de una actividad, la actividad aparece en el registro con el que está asociada. 
- También puede elegir el panel de filtro para filtrar las actividades por tipo de registro y fecha. 
- Cuando se crea una nueva actividad, obtendrá una notificación sobre **lo que se perdió** en el muro de la **escala de tiempo**.
- Se mostrará un mensaje de correo electrónico con una imagen adjunta insertada con el cuerpo del correo electrónico.

  > [!div class="mx-imgBorder"]
  > ![Vista de escala de tiempo de las actividades en PowerApps](media/TimelineViewOfActivity.png "Vista de escala de tiempo de las actividades en PowerApps")  
 
## <a name="add-an-activity-from-the-nav-bar"></a>Adición de una actividad desde la barra de navegación
 
La forma más rápida de agregar una actividad es usar el acceso directo en la barra de navegación y, a continuación, vincularla a un registro. Por ejemplo, puede crear una actividad de llamada telefónica y, luego, vincularla a un contacto en el sistema mediante el campo **Referente a**.

1. En la barra de navegación, seleccione el ![botón de crear registro](media/create-record-button.png "Botón crear registro")de signo **más** y, a continuación, seleccione **actividades**. 

   > [!div class="mx-imgBorder"]
   > ![Acceso directo para agregar una actividad en PowerApps](media/QuickCreate.png "Acceso directo para agregar una actividad en PowerApps")  
 
2. Elija el tipo de actividad que desea agregar.

3. Rellene la información necesaria. Use el campo **Referente a** para asociar la actividad a un registro.

4. Cuando termine,seleccione **Guardar**.

 
## <a name="add-a-phone-call"></a>Adición de una llamada telefónica  
  
1. Abra el registro al que desea agregar la actividad. Por ejemplo, un registro de contacto.
  
2. En el muro de la **escala de tiempo**, seleccione **signo más** > **Llamada de teléfono**. 


   > [!div class="mx-imgBorder"]
   > ![Agregar una actividad de teléfono en PowerApps](media/addphonecall.png "Agregar una actividad de teléfono en PowerApps")
  
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


    > [!NOTE]
    > Para enumerar los correos electrónicos en una vista de conversación, vaya a **configuración** > **configuración de personalización** > pestaña **correo electrónico** y, a continuación, seleccione **Mostrar correo electrónico como conversación en escala de tiempo**. Para obtener más información sobre la configuración personal, consulte [set personal Options](https://docs.microsoft.com/powerapps/user/set-personal-options#email-tab-options). Una vez habilitada, puede abrir cualquier formulario que tenga una escala de tiempo y los correos electrónicos se agruparán en subprocesos de conversación con el correo electrónico más reciente en la parte superior.

   > [!div class="mx-imgBorder"]
   > ![Establecer opciones personales](media/emailsettings1.png "Establecer las opciones personales")
   
    > [!div class="mx-imgBorder"]
    > ![Establecer correo electrónico de opciones personales](media/emailsettings2.png "Establecer opciones personales para el correo electrónico")

  
## <a name="add-an-appointment"></a>Adición de una cita  

Para agregar una actividad de cita a un registro, primero debe guardar el registro al que está agregando la actividad.  

> [!NOTE]
> No se admiten citas recurrentes en la aplicación Dynamics 365 para Outlook, Dynamics 365 para teléfonos y, al ejecutar el cliente web de aplicaciones controladas por modelos en el explorador Web del teléfono móvil.
  
1. Abra el registro al que desea agregar la actividad. Por ejemplo, un registro de contacto.
  
2. En el muro de la **escala de tiempo**, seleccione **signo más** > **Cita**.  
  
3. Use la información sobre herramientas para completar la información requerida.
  
4. Cuando haya terminado de rellenar el formulario, seleccione **Guardar** para guardar la cita.

## <a name="add-notes"></a>Agregar notas

También puede agregar notas fácilmente en el área de actividades.
  
1. Abra el registro al que desea agregar la actividad. Por ejemplo, un registro de contacto.
  
2. En el muro de la **escala de tiempo**, empiece a escribir sus notas. Use **Agregar un archivo adjunto** para agregar datos adjuntos a la nota.

3. Cuando haya terminado de rellenar el formulario, seleccione **Agregar nota** para guardar la nota.


> [!NOTE]
> También puede agregar una nota con el **signo más** en la sección superior del muro de la **escala de tiempo**.

   > [!div class="mx-imgBorder"]
   > ![Agregar una nota](media/addnote.png "Agregar una nota")

Una vez que se haya agregado la nota, puede eliminarla o editarla.


> [!div class="mx-imgBorder"]
> ![Actualizar una nota](media/addnote2.png "Actualizar una nota")

## <a name="add-a-post"></a>Adición de una publicación 

1. Abra el registro al que desea agregar la publicación. Por ejemplo, un registro de contacto.

2. En el muro de la **escala de tiempo**, seleccione **signo más** > **Publicación**. 

3. Escriba su publicación en el campo de texto 

4. Cuando haya terminado de rellenar el formulario, seleccione **Agregar** para guardar la publicación.

> [!div class="mx-imgBorder"]
> ![Actualizar una publicación](media/post.png "Adición de una publicación")
  
  Una vez que guarde la publicación, aparecerá en la parte superior del muro de la escala de tiempo.
  
## <a name="refresh-the-timeline"></a>Actualización de la escala de tiempo 

Puede actualizar el muro de la escala de tiempo para ver la información más actualizada.

En el muro de la **escala de tiempo** , seleccione el ![botón más](media/MoreButton.png "Botón más") y, a continuación, seleccione **Actualizar escala de tiempo**.

> [!div class="mx-imgBorder"]
> ![Actualización de la escala de tiempo](media/refresh.png "Actualización de la escala de tiempo")


## <a name="use-the-filter-pane"></a>Uso del panel de filtros

Filtre rápidamente las actividades, notas o publicaciones del muro de la escala de tiempo por tipo de registro o tipo de actividad y fecha con el panel de filtro. Puede seleccionar varios filtros y opciones de filtro al mismo tiempo. Puede filtrar y ver la fecha de vencimiento de la actividad, la fecha de modificación o el estado de la actividad.

- En el plano de la **escala de tiempo** , seleccione Abrir el icono de embudo del **Panel de filtros** .

> [!div class="mx-imgBorder"]
> ![Panel de filtro de la escala de tiempo](media/filterpane.png "Panel de filtro de la escala de tiempo")


## <a name="manage-activities"></a>Administración de actividades
Administre actividades directamente desde el muro de la escala de tiempo, incluida la asignación de una actividad a otra persona, la eliminación o el cierre de una actividad, la adición de una actividad a una cola, la apertura un registro asociado o la edición de notas y publicaciones.


> [!div class="mx-imgBorder"]
> ![Administrar Activities. png](media/ManageActivities.png "ManageActivities. png")



