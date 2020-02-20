---
title: Adición de una actividad de cita, correo electrónico, llamada telefónica, notas o tareas a la escala de tiempo en una aplicación basada en modelo | Microsoft Docs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 02/03/2020
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1a721f5dfa0a07d270e6b1d9d310236bebb21023
ms.sourcegitcommit: c5b9bdf820c7d60f00bf1b16d9e9f7d046fd7252
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2020
ms.locfileid: "76973397"
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

1. En la barra de navegación, seleccione el **signo más** ![botón Crear registro](media/create-record-button.png "Botón Crear registro") y luego **Actividades**. 

   > [!div class="mx-imgBorder"]
   > ![Acceso directo para agregar una actividad en Power Apps](media/QuickCreate.png "Acceso directo para agregar una actividad en Power Apps")  
 
2. Elija el tipo de actividad que desea agregar.

3. Rellene la información necesaria. Use el campo **Referente a** para asociar la actividad a un registro.

4. Cuando termine,seleccione **Guardar**.

 
## <a name="add-a-phone-call"></a>Adición de una llamada telefónica  
  
1. Abra el registro al que desea agregar la actividad. Por ejemplo, un registro de contacto.
  
2. En el muro de la **escala de tiempo**, seleccione **signo más** > **Llamada de teléfono**. 


   > [!div class="mx-imgBorder"]
   > ![Adición de una actividad de teléfono en Power Apps](media/addphonecall.png "Adición de una actividad de teléfono en Power Apps")
  
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
  
5. Para usar una plantilla en el cuerpo del correo electrónico, seleccione **Insertar plantilla** en la barra de comandos y después seleccione la plantilla. Para obtener más información sobre cómo insertar una plantilla de correo electrónico, vea [Inserción de una plantilla de correo electrónico](insert-email-template.md). 
  
6. Cuando haya terminado de rellenar el formulario, seleccione **Enviar**. 



### <a name="list-emails-in-a-conversation-view"></a>Enumeración de los correos electrónicos de una vista de conversación

Para enumerar los correos electrónicos de una vista de conversación, vaya a la pestaña **Configuración** > **Configuración de personalización** > **Correo electrónico** y después seleccione **Show email as a conversation on Timeline** (Mostrar correo electrónico como conversación en la escala de tiempo). Para obtener más información sobre la configuración personal, vea [Establecer las opciones personales](https://docs.microsoft.com/powerapps/user/set-personal-options#email-tab-options). Una vez que haya habilitado esta configuración, puede abrir cualquier formulario que tenga una escala de tiempo y los correos electrónicos se agruparán en conversaciones con el correo electrónico más reciente en la parte superior.

   > [!div class="mx-imgBorder"]
   > ![Establecimiento de las opciones personales](media/emailsettings1.png "Establecer las opciones personales")
   
   > [!div class="mx-imgBorder"]
   > ![Establecimiento de las opciones personales en el correo electrónico](media/emailsettings2.png "Establecimiento de las opciones personales en el correo electrónico")

  
## <a name="add-an-appointment"></a>Adición de una cita  

Para agregar una actividad de cita a un registro, primero debe guardar el registro al que está agregando la actividad.  

> [!NOTE]
> No se admiten las citas periódicas en la aplicación Dynamics 365 para Outlook, en la aplicación Dynamics 365 para teléfonos ni al ejecutar el cliente web de aplicaciones basadas en modelo en el explorador web del teléfono móvil.
  
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
   > ![Adición de una nota](media/addnote.png "Adición de una nota")

Una vez que se haya agregado la nota, puede eliminarla o editarla. Seleccione la nota o mantenga el puntero sobre la nota para ver los iconos de edición y eliminación.


> [!div class="mx-imgBorder"]
> ![Actualización de una nota](media/addnote2.png "Actualización de una nota")

## <a name="add-a-post"></a>Adición de una publicación 

1. Abra el registro al que desea agregar la publicación. Por ejemplo, un registro de contacto.

2. En el muro de la **escala de tiempo**, seleccione **signo más** > **Publicación**. 

3. Escriba su publicación en el campo de texto 

4. Cuando haya terminado de rellenar el formulario, seleccione **Agregar** para guardar la publicación.

> [!div class="mx-imgBorder"]
> ![Actualización de una publicación](media/post.png "Adición de una publicación")
  
  Una vez que guarde la publicación, aparecerá en la parte superior del muro de la escala de tiempo.
  
## <a name="refresh-the-timeline"></a>Actualización de la escala de tiempo 

Puede actualizar el muro de la escala de tiempo para ver la información más actualizada.

En el muro de la **escala de tiempo**, seleccione ![botón Más ](media/MoreButton.png "Botón Más") y luego **Actualizar escala de tiempo**.

> [!div class="mx-imgBorder"]
> ![Actualización de la escala de tiempo](media/refresh.png "Actualización de la escala de tiempo")


## <a name="use-the-filter-pane"></a>Uso del panel de filtros

Filtre rápidamente las actividades, notas o publicaciones del muro de la escala de tiempo por tipo de registro o tipo de actividad y fecha con el panel de filtro. Puede seleccionar varios filtros y opciones de filtro a la vez. Puede ver la fecha de vencimiento, la fecha de modificación o el estado de la actividad, así como filtrar por estas opciones.

- En el muro de la **escala de tiempo**, seleccione el icono de embudo **Abrir panel de filtro**.


![Panel de filtro en la escala de tiempo](media/timeline-filter2.png "Panel de filtro de la escala de tiempo") ![Panel de filtro en la escala de tiempo](media/timeline-filter5.png "Panel de filtro de la escala de tiempo")


## <a name="manage-activities"></a>Administración de actividades
Administre actividades directamente desde el muro de la escala de tiempo, incluida la asignación de una actividad a otra persona, la eliminación o el cierre de una actividad, la adición de una actividad a una cola, la apertura un registro asociado o la edición de notas y publicaciones.

  ![Opciones de la barra de comandos de la escala de tiempo](media/timeline-options1.png "Opciones de la barra de comandos de la escala de tiempo") ![Opciones de la barra de comandos de la escala de tiempo](media/timeline-options2.png "Opciones de la barra de comandos de la escala de tiempo") ![Opciones de la barra de comandos de la escala de tiempo](media/timeline-options3.png "Opciones de la barra de comandos de la escala de tiempo") ![Opciones de la barra de comandos de la escala de tiempo](media/timeline-options4.png "Opciones de la barra de comandos de la escala de tiempo")

## <a name="see-also"></a>Vea también

[Configurar el control de escala de tiempo](../maker/model-driven-apps/set-up-timeline-control.md)

[Preguntas más frecuentes para el control de escala de tiempo](../maker/model-driven-apps/faqs-timeline-control.md)

[Preguntas frecuentes sobre las actividades y el muro de escala de tiempo](faq-for-timeline-and-activity.md)

[Sección Escala de tiempo en la aplicación Centro de servicio al cliente](https://docs.microsoft.com/dynamics365/customer-service/customer-service-hub-user-guide-basics#timeline)
