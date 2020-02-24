---
title: Adición de una actividad de cita, correo electrónico, llamada telefónica, notas o tareas a la escala de tiempo en una aplicación basada en modelo | Microsoft Docs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 02/13/2020
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 91da88baa13204f8538ba3eb673a515e539f7fa7
ms.sourcegitcommit: eda3382ade50efe66611518c8f36e3a2ada7a91d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2020
ms.locfileid: "77282519"
---
# <a name="add-an-appointment-email-phone-call-note-or-task-activity-to-the-timeline"></a>Agregue una actividad de cita, correo electrónico, llamada telefónica, nota o tarea a la escala de tiempo. 


Agregue **Actividades** al muro de la **Escala de tiempo** para realizar un seguimiento de todas las comunicaciones con un cliente o un contacto. Por ejemplo, puede tomar notas, agregar publicaciones, agregar una tarea, enviar un correo electrónico, agregar detalles de llamada telefónica o fijar citas. El sistema automáticamente agrega una marca de tiempo a cada actividad y muestra quién la creó. Usted y otras personas de su equipo pueden desplazarse por las actividades para ver el historial mientras trabajan con un cliente. 

- Las actividades que agregue desde un registro aparecen en el muro de la **escala de tiempo** del registro. 
- Si está configurado el campo **Referente a** de una actividad, la actividad aparece en el registro con el que está asociada. 
- También puede elegir el panel de filtro para filtrar las actividades por tipo de registro y fecha. 
- Cuando se crea una nueva actividad, obtendrá una notificación sobre **lo que se perdió** en el muro de la **escala de tiempo**.
- Se mostrará un mensaje de correo electrónico con una imagen adjunta insertada con el cuerpo del correo electrónico.

  > [!div class="mx-imgBorder"]
  > ![Vista de escala de tiempo de las actividades en Power Apps](media/TimelineViewOfActivity.png "Vista de escala de tiempo de las actividades en Power Apps")


Leyenda:

  1. Buscar registros
  2. Tomar notas
  3. Agregar información y actividades
  4. Filtrar
  5. Más comandos
  6. Estado de la actividad
  7. Iconos de actividad
  8. Fecha y hora
 
## <a name="add-an-activity-from-the-nav-bar"></a>Adición de una actividad desde la barra de navegación
 
La forma más rápida de agregar una actividad es usar el acceso directo en la barra de navegación y, a continuación, vincularla a un registro. Por ejemplo, puede crear una actividad de llamada telefónica y, luego, vincularla a un contacto en el sistema mediante el campo **Referente a**.

1. En la barra de navegación superior, seleccione **Nuevo** ![botón Crear registro](media/create-record-button.png "Botón Crear registro") > **Actividades** > elija el tipo de actividad que quiere agregar.

   > [!div class="mx-imgBorder"]
   > ![Acceso directo para agregar una actividad en Power Apps](media/add_new_activity_from_nav.gif "Acceso directo para agregar una actividad en Power Apps")  
 
3. Rellene la información necesaria. Use el campo **Referente a** para asociar la actividad a un registro.

4. Cuando haya terminado, seleccione **Guardar y cerrar** o **Guardar y crear nuevo**. 

## <a name="add-an-activity-from-within-a-record"></a>Adición de una actividad desde un registro

También puede abrir un registro y, a continuación, agregar una actividad a este. 

   > [!div class="mx-imgBorder"]
   > ![Acceso directo para agregar una actividad en Power Apps](media/add_new_activity_from_record.gif "Acceso directo para agregar una actividad en Power Apps") 


### <a name="add-a-phone-call"></a>Adición de una llamada telefónica  
  
1. Abra el registro al que desea agregar la actividad. Por ejemplo, abra un registro de contacto.
  
2. En la sección **Escala de tiempo**, seleccione **Agregar información y actividades** ![Agregar actividades](media/add-activity-button.png "Botón Agregar actividades") > **Llamada de teléfono**. 


   > [!div class="mx-imgBorder"]
   > ![Adición de una actividad de teléfono en Power Apps](media/addphonecall.png "Adición de una actividad de teléfono en Power Apps")
  
3. Rellene el **Asunto** de la llamada.

     En el área **Descripción**, escriba un resumen de la conversación con el cliente. 
  
     El campo **Llamar a** se rellena automáticamente con el registro al que agregó la actividad de llamada telefónica. Puede seleccionar un registro diferente si es necesario.  
  
4. De forma predeterminada, la dirección se establece en **Saliente**. Puede cambiarla a **Entrante** seleccionando **Saliente**.
  
5. Cuando haya terminado de rellenar el formulario, seleccione **Guardar y cerrar** para guardar la actividad de llamada de teléfono.  
  
### <a name="add-a-task"></a>Adición de una tarea  
  
1. Abra el registro al que desea agregar la actividad. Por ejemplo, abra un registro de contacto.
  
2. En la sección **Escala de tiempo**, seleccione **Agregar información y actividades** ![Agregar actividades](media/add-activity-button.png "Botón Agregar actividades") > **Tarea**.
  
3. El campo **Propietario** se establece en el usuario actual de forma predeterminada. Si desea volver a asignar la tarea, seleccione el icono de búsqueda y, a continuación, seleccione otro usuario o equipo.  
  
4. Cuando haya terminado de rellenar la información de la tarea, seleccione **Guardar y cerrar** para guardar la información. 
  
### <a name="add-an-email"></a>Adición de correo electrónico  

Para agregar una actividad de correo electrónico a un registro, primero debe guardar el registro al que está agregando la actividad.  
  
1. Abra el registro al que desea agregar la actividad. Por ejemplo, abra un registro de contacto.
  
2. En la sección **Escala de tiempo**, seleccione **Agregar información y actividades** ![Agregar actividades](media/add-activity-button.png "Botón Agregar actividades") > **Correo electrónico**. 

3. Rellene el asunto del correo electrónico y use el espacio proporcionado para escribir el correo electrónico.
  
4. Para agregar datos adjuntos al correo electrónico, guárdelo. A continuación, en la barra de comandos, seleccione **Adjuntar archivo** > **Elegir archivo** y seleccione el archivo que quiera adjuntar al correo electrónico.

   > [!NOTE]
   > Se mostrará un mensaje de correo electrónico con una imagen adjunta insertada con el cuerpo del correo electrónico.
  
5. Para usar una plantilla en el cuerpo del correo electrónico, seleccione **Insertar plantilla** en la barra de comandos y después seleccione la plantilla. Para obtener más información sobre cómo insertar una plantilla de correo electrónico, vea [Inserción de una plantilla de correo electrónico](insert-email-template.md). 
  
6. Cuando haya terminado de redactar el correo electrónico, en la barra de comandos seleccione **Enviar**. 


#### <a name="list-emails-in-a-conversation-view"></a>Enumeración de los correos electrónicos de una vista de conversación

1. Para enumerar los correos electrónicos en una vista de conversación, vaya a **Configuración** > **Configuración de personalización**.

   > [!div class="mx-imgBorder"]
   > ![Establecimiento de las opciones personales](media/emailsettings1.png "Establecer las opciones personales")

2. en la pestaña **Correo electrónico** y seleccione **Mostrar correo electrónico como conversación en la escala de tiempo**. Para obtener más información sobre la configuración personal, vea [Establecer las opciones personales](https://docs.microsoft.com/powerapps/user/set-personal-options#email-tab-options). Una vez que haya habilitado esta configuración, puede abrir cualquier formulario que tenga una escala de tiempo y los correos electrónicos se agruparán en conversaciones con el correo electrónico más reciente en la parte superior.
   
   > [!div class="mx-imgBorder"]
   > ![Establecimiento de las opciones personales en el correo electrónico](media/emailsettings2.png "Establecimiento de las opciones personales en el correo electrónico")

  
### <a name="add-an-appointment"></a>Adición de una cita  

Para agregar una actividad de cita a un registro, primero debe guardar el registro al que está agregando la actividad de la cita.  

> [!NOTE]
> No se admiten las citas periódicas en la aplicación Dynamics 365 para Outlook, en la aplicación Dynamics 365 para teléfonos ni al ejecutar el cliente web de aplicaciones basadas en modelo en el explorador web del teléfono móvil.
  
1. Abra el registro al que desea agregar la actividad. Por ejemplo, abra un registro de contacto.
  
2.  En la sección **Escala de tiempo**, seleccione **Agregar información y actividades** ![Agregar actividades](media/add-activity-button.png "Botón Agregar actividades") > **Cita**.  
  
3. Rellene el **Asunto** de la cita y establezca la **Hora de inicio** y la **Hora de finalización**.
  
4. Cuando haya terminado de rellenar los detalles de la cita, seleccione **Guardar y cerrar** para guardar la cita.

### <a name="add-notes"></a>Agregar notas

También puede agregar notas fácilmente en el área de actividades.
  
1. Abra el registro al que desea agregar la actividad. Por ejemplo, abra un registro de contacto.
  
2. En la sección **Escala de tiempo**, seleccione el área **Escriba una nota**.

3. Agregue un título para la nota y agregue los detalles.

4. Para agregar datos adjuntos a la nota, seleccione **Agregar un archivo adjunto**.

3. Cuando haya terminado, seleccione **Agregar nota** para guardarla.

   > [!div class="mx-imgBorder"]
   > ![Adición de una nota](media/addnote.png "Adición de una nota")

> [!NOTE]
> También puede agregar una nota seleccionando **Agregar información y actividades** ![Agregar actividades](media/add-activity-button.png "Botón Agregar actividades") > **Nota**.

#### <a name="edit-or-delete-a-note"></a>Edición o eliminación de una nota

- Para editar o eliminar la nota una vez creada, selecciónela y elija **Editar esta nota** o **Eliminar nota**. 

  > [!div class="mx-imgBorder"]
  > ![Actualización de una nota](media/addnote2.png "Actualización de una nota")

### <a name="add-a-post"></a>Adición de una publicación 

1. Abra el registro al que desea agregar la publicación. Por ejemplo, abra un registro de contacto.

2. En la sección **Escala de tiempo**, seleccione **Agregar información y actividades** ![Agregar actividades](media/add-activity-button.png "Botón Agregar actividades") > **Publicación**. 

3. Escriba los detalles de la publicación en el campo de texto.

4. Cuando haya terminado, seleccione **Agregar** para guardar la publicación.

   > [!div class="mx-imgBorder"]
   > ![Actualización de una publicación](media/post.png "Adición de una publicación")
  
  Una vez que guarde la publicación, aparecerá en la parte superior del muro de la escala de tiempo.
  
## <a name="refresh-the-timeline"></a>Actualización de la escala de tiempo 

Puede actualizar el muro de la escala de tiempo para ver la información más actualizada.

En la sección **Escala de tiempo**, seleccione ![botón Más ](media/MoreButton.png "Botón Más") y luego **Actualizar escala de tiempo**.

  > [!div class="mx-imgBorder"]
  > ![Actualización de la escala de tiempo](media/refresh.png "Actualización de la escala de tiempo")


## <a name="use-the-filter-pane"></a>Uso del panel de filtros

Filtre rápidamente las actividades, notas o publicaciones del muro de la escala de tiempo por tipo de registro o tipo de actividad y fecha con el panel de filtro. Puede seleccionar varios filtros y opciones de filtro a la vez. Puede ver la fecha de vencimiento, la fecha de modificación o el estado de la actividad, así como filtrar por estas opciones.

- En la sección **Escala de tiempo**, seleccione **Abrir el panel de filtros** y seleccione cómo quiere filtrar las actividades.

  > [!div class="mx-imgBorder"]
  > ![Panel de filtro en la escala de tiempo](media/timeline-filter2.png "Panel de filtro de la escala de tiempo") ![Panel de filtro en la escala de tiempo](media/timeline-filter5.png "Panel de filtro de la escala de tiempo")


## <a name="manage-activities"></a>Administración de actividades
Administre actividades directamente desde el muro de la escala de tiempo, incluida la asignación de una actividad a otra persona, la eliminación o el cierre de una actividad, la adición de una actividad a una cola, la apertura un registro asociado o la edición de notas y publicaciones.

  ![Opciones de la barra de comandos de la escala de tiempo](media/timeline-options1.png "Opciones de la barra de comandos de la escala de tiempo") ![Opciones de la barra de comandos de la escala de tiempo](media/timeline-options2.png "Opciones de la barra de comandos de la escala de tiempo") ![Opciones de la barra de comandos de la escala de tiempo](media/timeline-options3.png "Opciones de la barra de comandos de la escala de tiempo") ![Opciones de la barra de comandos de la escala de tiempo](media/timeline-options4.png "Opciones de la barra de comandos de la escala de tiempo")

## <a name="see-also"></a>Vea también

[Configurar el control de escala de tiempo](../maker/model-driven-apps/set-up-timeline-control.md)

[Preguntas más frecuentes para el control de escala de tiempo](../maker/model-driven-apps/faqs-timeline-control.md)

[Preguntas frecuentes sobre las actividades y el muro de escala de tiempo](faq-for-timeline-and-activity.md)

[Sección Escala de tiempo en la aplicación Centro de servicio al cliente](https://docs.microsoft.com/dynamics365/customer-service/customer-service-hub-user-guide-basics#timeline)
