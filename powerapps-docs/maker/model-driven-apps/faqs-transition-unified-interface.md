---
title: 'Preguntas más frecuentes: Transición a la Interfaz unificada | MicrosoftDocs'
description: Preguntas más frecuentes relacionadas con el proceso de transición para desplazar usuarios del cliente web heredado a la Interfaz unificada.
ms.custom: ''
ms.date: 12/20/2019
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.author: haybass
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e06fa6901ec123307adaabdbbb6071e5a11c47cc
ms.sourcegitcommit: 41a78575a6533c45c7cf4c012f8ed30c4e43aae8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "2918130"
---
# <a name="faqs-transition-to-unified-interface"></a>Preguntas más frecuentes: Transición a la Interfaz unificada

Este tema proporciona respuestas a las preguntas más comunes sobre las opciones de transición para trasladar a usuarios del cliente web heredado a la Interfaz unificada.

### <a name="where-can-i-go-to-see-the-transition-dates-that-have-been-suggested-for-my-environments"></a>¿Dónde puedo ir para ver las fechas de transición que se han sugerido para mis entornos? 

Utilice el portal de transición para administrar la fecha de transición de su entorno: <https://runone.powerappsportals.com>.

### <a name="how-do-i-gain-access-to-the-portal"></a>¿Cómo accedo al portal?

Haga lo siguiente:
1. Visite <https://runone.powerappsportals.com>.
2. Inicie sesión con las credenciales de administración del inquilino que desea administrar.
3. Seleccione **Mis entornos** y revise todos los entornos que tengan aplicada una fecha sugerida.

### <a name="i-see-my-environment-has-a-date-suggested-for-transition-can-i-change-this-date"></a>Veo que mi entorno tiene una fecha sugerida para la transición. ¿Puedo cambiar esta fecha?

Sí, esto es posible si tiene el rol de **administrador global**, el **administrador de servicio de Dynamics 365** o el **administrador de Power Platform** para el inquilino. 

Las fechas asociadas a su entorno son una sugerencia que requiere aprobación para continuar. Apruebe si la fecha es adecuada para su organización.  

Para cambiar la fecha, seleccione el icono desplegable junto al entorno y vea el registro. Los roles de administrador de inquilinos podrán reprogramar la fecha de transición a una fecha anterior o posterior.

Para reprogramar a una fecha anterior, actualice la fecha existente a su opción preferida en la lista. También puede [cambiar manualmente](transition-web-app.md) si nuestras fechas no le resultan convenientes. 
 
Para programar una fecha posterior, seleccione el botón de reprogramar fecha de transición. Las fechas sugeridas estarán disponibles en el cuadro desplegable. Una vez aprobada, la fecha se actualizará en el portal según corresponda. A continuación, acepte la fecha actualizada si desea realizar la transición de su entorno. 
 
Los cambios de fecha se revisarán y otorgarán si la fecha es anterior al 1 de octubre de 2020. La fecha se actualizará en el portal una vez confirmada. 

> [!NOTE]
> Si tiene una transición aprobada y la fecha programada es en las próximas 48 horas, no podrá cambiar la fecha. Del mismo modo, no puede solicitar una fecha posterior al 1 de octubre de 2020, ya que el cliente web heredado ya no estará disponible.

### <a name="what-will-happen-if-i-dont-opt-in-and-approve-a-suggested-transition-date-for-my-environment"></a>¿Qué sucederá si no participo y apruebo una fecha de transición sugerida para mi entorno?

No se producirá ningún cambio en su entorno si no ha aprobado la fecha sugerida dentro del portal. Cuando pase la fecha sugerida, trataremos de proporcionarle otra fecha en el futuro para que la considere.  
 
> [!NOTE]
> Después del 1 de octubre de 2020, todos los entornos se actualizarán a la Interfaz unificada según la oleada de la versión de octubre de 2020.

### <a name="my-transition-date-is-within-48-hours-and-i-cant-change-the-date-within-the-portal-how-can-i-stop-the-transition-from-taking-place"></a>Mi fecha de transición es en las próximas 48 horas y no puedo cambiar la fecha dentro del portal. ¿Cómo puedo detener la transición?

La capacidad para cambiar la fecha de transición para un entorno está disponible solo hasta 48 horas antes de la transición. Para detener el proceso después de este período, plantee un caso de soporte técnico. 

> [!NOTE]
> No podemos garantizar que la transición pueda ser detenida si la solicitud se realiza después de que la fecha se haya bloqueado en el portal (48 horas o menos).

### <a name="i-have-environments-without-a-scheduled-date-can-i-update-these-to-include-a-date"></a>Tengo entornos sin una fecha programada. ¿Puedo actualizar estos para incluir una fecha?

Sí, si tiene un rol de **administrador global**, **administrador de servicio Dynamics 365** o **administrador de Power Platform** para el inquilino, seleccione el entorno y seleccione una fecha haciendo clic en el botón de reprogramar fecha de transición.

Actualizaremos el portal con la fecha para confirmar. También se enviarán correos electrónicos de notificación a los administradores de inquilinos globales cuando se aproxime la fecha de transición. Esto seguirá el procedimiento restante estándar detallado en este documento.

### <a name="is-there-a-recommended-checklist-i-should-run-through-before-transition"></a>¿Existe una lista de comprobación recomendada que debo ejecutar antes de la transición?

Consulte el contenido de soporte técnico disponible en el [sitio de la comunidad](https://community.dynamics.com/365/unified-interface/). También tenemos una [lista de comprobación de la transición](https://aka.ms/UIChecklist) para ayudarle a planear eficazmente. Revísela cuidadosamente para asegurarse de que está de acuerdo con la transición a la interfaz unificada.

### <a name="my-environment-has-been-transitioned-but-i-am-finding-blocking-issues-for-my-users-and-want-to-move-back-to-the-legacy-web-client-is-this-possible"></a>Se ha realizado la transición de su entorno, pero estoy teniendo problemas de bloqueo para mis usuarios y quiero volver al cliente web heredado. ¿Esto es posible?

Sí, aún podrá volver al cliente web heredado en un plazo de hasta 10 días después de la transición. Puede realizar el [cambio manualmente](https://docs.microsoft.com/power-platform/admin/enable-unified-interface-only) durante los primeros 4 días o después, presentar una solicitud de soporte técnico en canal habitual, ya que el cambio manual se deshabilitará. 

> [!NOTE]
> Los 10 días deberán ser antes de 1 de octubre de 2020 ya que el cliente web heredado ya no estará disponible a partir de esa fecha.

### <a name="i-want-to-transition-after-october-1-2020-is-that-possible"></a>Quiero realizar la transición después del 1 de octubre de 2020. ¿Es posible eso?

El cliente web heredado no estará disponible después de la oleada de la versión de octubre de 2020 para los usuarios finales. No tenemos la capacidad de aplazar la fecha más allá de ese período.

Si encuentra elementos de bloqueo, regístrelos mediante el proceso de soporte estándar cuanto antes.

### <a name="what-is-the-standard-reminder-procedure-throughout-this-process"></a>¿Cuál es el procedimiento de aviso estándar en este proceso?

La comunicación será en oleadas, al menos 30 días antes del plazo sugerido, pero puede iniciar sesión en el portal (<https://runone.powerappsportals.com>) en cualquier momento para ver el estado. Microsoft enviará la comunicación siguiente:

-   Mensaje inicial para cada entorno que tiene una fecha de transición sugerida.
-   Si ha aprobado la fecha, recibirá un mensaje recordatorio 2 días antes de que las fechas se bloqueen en el portal. 
-   El recordatorio final se enviará 2 días antes de la transición. Esto indicará que la fecha de transición está bloqueada y seguirá adelante con la transición.
-   Después de la transición, se enviará un mensaje de cierre para confirmar que el proceso se ha realizado correctamente (o si se produjo un problema)

Los mensajes se pueden ver con los canales siguientes:
-   Centro de mensajes en el inquilino de Microsoft 365. Suele ser visible para roles como administrador global, administrador de servicios, lector de mensajes de servicio.
-   Correo electrónico directo.  Los correos electrónicos se envían únicamente al rol de administrador del sistema para el entorno específico en cuestión, o las direcciones de correo electrónico que se hayan agregado a la pestaña “Notificación” en el portal de administración de entorno.

> [!NOTE]
> Recibirá un mensaje de correo electrónico para cada entorno donde su cuenta de usuario tenga el rol de administrador del sistema.

### <a name="i-have-requested-a-date-to-postpone-but-still-receiving-e-mails-and-message-center-posts-that-my-environment-is-set-to-transition-should-i-be-concerned"></a>He solicitado una fecha para posponer, pero sigo recibiendo correos electrónicos y el Centro de mensajes publica que mi entorno está establecido para transición. ¿Debería preocuparme?

Nuestra primera recomienda es consultar el portal de transición (<https://runone.powerappsportals.com/>) ya que ésta será única fuente fiable para todos sus entornos. Si se actualiza la fecha, es muy probable que nuestro sistema de comunicación envíe el mensaje antes de que actualicemos la lista de comunicaciones. 

Si la fecha en el portal no se actualiza con la nueva fecha, presente una solicitud de soporte técnico siguiendo el procedimiento estándar.

Solo se realizará la transición de las fechas aprobadas por el administrador. 

### <a name="if-i-already-have-an-environment-transitioned-to-unified-interface-will-i-still-be-able-to-switch-back-to-the-legacy-web-client-manually"></a>Si ya tengo un entorno que ha realizado la transición a la interfaz unificada, ¿podré volver al cliente web heredado manualmente?

Si el entorno transición ha realizado la transición hace al menos 4 días, intentaremos deshabilitar el cambio manual al antiguo cliente web. 

Si encuentra esta opción se ha deshabilitado y tiene necesidad de volver, presente una solicitud de soporte técnico en el canal habitual para su evaluación.

### <a name="is-there-a-specific-day-and-time-when-approved-transitions-will-take-place"></a>¿Hay un día y hora específicos en que se llevarán a cabo las transiciones aprobadas? 

No anticipamos tiempos de inactividad al crear esta transición. Sin embargo, solo haremos una transición un viernes, siguiendo los mismos plazos de mantenimiento descritos en nuestras políticas y comunicaciones estándar. Más información: [Escala de tiempo de mantenimiento ](https://docs.microsoft.com/power-platform/admin/policies-communications#maintenance-timeline)

### <a name="are-environments-from-all-data-centers-included-within-this-transition-service"></a>¿Se incluyen entornos de todos los centros de datos en este servicio de transición?

Actualmente, no se han incluido entornos de centros de datos específicos, como la nube de la comunidad gubernamental (GCC), en el portal. Proporcionaremos fechas de transición sugeridas para estos entornos antes de junio de 2020. Los clientes que desean cambiarse a la Interfaz unificada siempre pueden [cambiarse manualmente](/power-platform/admin/enable-unified-interface-only#how-to-enable-unified-interface-only-mode) en cualquier momento antes del 1 de octubre de 2020.


