---
title: Preguntas más frecuentes para el control de escala de tiempo (sección) en Power Apps | MicrosoftDocs
description: Preguntas más frecuentes para el control de escala de tiempo (sección) en Power Apps
ms.date: 03/10/2020
ms.service: powerapps
author: kabala123
ms.assetid: 7F495EE1-1208-49DA-9B02-17855CEB2FDF
ms.author: kabala
manager: shujoshi
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b3dfc60d7c34ca91257d9aaa1b5979d894268866
ms.sourcegitcommit: 3c6c5594b73abd5ff438d50f3b579d56cef7241c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "3285988"
---
# <a name="faqs-for-timeline-control"></a>Preguntas más frecuentes para control de escala de tiempo

## <a name="why-do-i-receive-the-message-records-could-not-be-loaded-because-of-unexpected-error"></a>¿Por qué recibo el mensaje "No se pudieron cargar registros debido a un error inesperado"?

La sección **Escala de tiempo** recupera datos y se muestra en las tarjetas de formulario. De forma predeterminada, la escala de tiempo recupera datos para las 10 entidades de actividad estándar, que son:

-    Correo
-    Tarea
-    Resolución de incidentes
-    Fax
-    Cierre de oportunidad
-    Carta
-    Cita
-    Llamada de teléfono

Cuando realice los siguientes procedimientos como administrador, los usuarios verán un error en tiempo de ejecución:

**Procedimiento**
-    Crear cualquier actividad personalizada adicional
-    Habilitar actividades personalizadas para dispositivos móviles
-    Seleccionar un **formulario de tarjeta** para todas las actividades personalizadas 

**Error:** No se pudieron cargar registros debido a un error inesperado.

   > [!div class="mx-imgBorder"] 
   > ![No se pudieron cargar registros debido a un error inesperado.](media/timeline-error1.png "No se pudieron cargar registros debido a un error inesperado.")

Este error se produce porque el número de entidades de actividad para la recuperación de datos ha superado el límite máximo de 10.

   > [!div class="mx-imgBorder"] 
   > ![El número de entidades de vínculos en la consulta superó el límite máximo](media/timeline-error2.png "[El número de entidades de vínculos en la consulta superó el límite máximo")

### <a name="workaround"></a>Solución alternativa

Para solucionar el problema, debe reducir el número de entidades a 10 o menos. Para ello, siga los pasos que se indican a continuación.

1.  Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

2.  Abra una aplicación basada en modelo y en la barra de comandos seleccione **Configuración** ![Configuración](../model-driven-apps/media/powerapps-gear.png) > **Configuración avanzada**.

3.   Vaya a **Personalizaciones** > **Personalización** > **Personalización del sistema**. La página del explorador de soluciones se abre en una nueva ventana del navegador.

4.   Expanda **Entidades** en **Componentes** en el panel de la solución predeterminada.

5.   Seleccione una entidad y seleccione **Formularios**. Por ejemplo, seleccione la entidad **Cuenta**.

6.   Selecciona el registro **Cuenta para experiencia interactiva** que es un tipo de formulario **Principal**. El formulario **Cuenta para experiencia interactiva** se abre en una nueva ventana del navegador.

      > [!div class="mx-imgBorder"] 
      > ![Seleccione el formulario de entidad con experiencia interactiva en el nombre](media/account-interactive-experience.png "Seleccione el formulario de entidad con experiencia interactiva en el nombre")

      Para la Interfaz unificada, debe usar el nombre del formulario que tiene `<Entity> for Interactive experience`.

7.    Haga doble clic en el campo **Pestañas de conversación**en la sección **Escala de tiempo**. Se muestra el diálogo **Propiedades de la pestaña Actividades**.

      > [!div class="mx-imgBorder"] 
      > ![Haga doble clic en el campo del panel de redes sociales](media/timeline-conversation-tabs-field.png "Haga doble clic en el campo del panel de redes sociales")  

8.    Seleccione la opción **Mostrar lo seleccionado** para el campo **Mostrar estas actividades** en el contenedor **Filtrado por**.

9.    Seleccione las actividades que desea mostrar a los usuarios.

10.    Seleccione **Aceptar** y, a continuación, **Guardar**.

11.    Seleccione **Publicar** para publicar las personalizaciones.


## <a name="why-i-cant-assign-or-delete-an-activity-from-the-timeline"></a>¿Por qué no puedo asignar o eliminar una actividad de la escala de tiempo?

Si utiliza la regla **HideCustomActions** para ocultar botones, como **Asignar** y **Eliminar** en la definición de la barra de comandos de la cinta de opciones, los botones que estén presentes en el control de la escala de tiempo no funcionarán. Los botones en la barra de comandos son los mismos que los botones en el control de la escala de tiempo; por lo tanto, cuando un usuario selecciona el botón **Asignar** o **Eliminar** en el control de la escala de tiempo, aparece un mensaje de error.

**No tiene permiso para realizar esta acción. Póngase en contacto con el administrador del sistema.**

Para mitigar el problema, muestre los botones en las definiciones de la barra de comandos.


## <a name="why-my-users-see-different-activities-and-records-in-their-my-activities-stream-in-the-dashboard"></a>¿Por qué mis usuarios ven actividades y registros diferentes en su secuencia Mis actividades en el panel?

La secuencia **Mis actividades** en el panel muestra los registros y las actividades que son propiedad de un usuario determinado. Por ejemplo, el usuario **A** ve registros y actividades que son propiedad de **A** y el usuario **B** ve registros y actividades que son propiedad de **B**.


## <a name="why-my-agents-see-the-filter-pane-even-when-the-expand-filter-pane-by-default-check-box-is-cleared"></a>¿Por qué mis agentes ven el panel de filtro incluso cuando la casilla de verificación Expandir panel de filtro de forma predeterminada está desactivada?

Cuando la línea de tiempo se muestra en más de una columna, el panel de filtro se muestra como una columna junto a los registros de la línea de tiempo. Aunque haya despejado la casilla de verificación **Expandir panel de filtro por defecto** en las configuraciones de línea de tiempo, el panel de filtro siempre se mostrará a sus agentes.

## <a name="see-also"></a>Vea también

[Configurar control de escala de tiempo](set-up-timeline-control.md)

[Sección de escala de tiempo en la aplicación del Centro de servicios al cliente](https://docs.microsoft.com/dynamics365/customer-service/customer-service-hub-user-guide-basics#timeline)

[Agregar una cita, correo electrónico, llamada de teléfono, nota o actividad de tarea a la escala de tiempo](../../user/add-activities.md)
