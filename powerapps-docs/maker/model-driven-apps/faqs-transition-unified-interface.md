---
title: 'Preguntas más frecuentes: Transición a interfaz unificada | MicrosoftDocs'
description: Preguntas más frecuentes relacionadas con el proceso de transición automática para mover usuarios del cliente web heredado a la interfaz unificada.
ms.custom: ''
ms.date: 11/04/2019
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
ms.openlocfilehash: 373201de630b46adc80b25eed10686da9112bad6
ms.sourcegitcommit: c094590862142155cbafa91c6ee0ade975c82083
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2019
ms.locfileid: "2769460"
---
# <a name="faqs-unified-interface-transition"></a>Preguntas más frecuentes: Transición a interfaz unificada

En este tema se proporcionan respuestas a las preguntas más comunes sobre el proceso de transición para mover usuarios del cliente web heredado a la interfaz unificada.

### <a name="where-can-i-go-to-see-the-transition-dates-that-have-been-assigned-to-my-environments"></a>¿Dónde puedo ir para ver las fechas de transición que se han asignado a mis entornos? 

Use el portal de transición automática para administrar la fecha de transición de su entorno: <https://runone.powerappsportals.com>.

### <a name="how-do-i-gain-access-to-the-portal"></a>¿Cómo accedo al portal?

Haga lo siguiente:
1. Visite <https://runone.powerappsportals.com>.
2. Inicie sesión con las credenciales de administración del inquilino que desea administrar.
3. Seleccione **Mis entornos**, y revise todos los entornos que tienen una fecha de destino asignada.

### <a name="i-see-my-environment-has-a-date-for-auto-transition-can-i-change-this-date"></a>Veo que mi entorno tiene una fecha para transición automática. ¿Puedo cambiar esta fecha?

Sí, esto es posible si tiene el rol **Administrador global** o **Administrador de servicio** para el inquilino. Para cambiar la fecha, seleccione el icono desplegable junto al entorno y vea el registro. Los roles de administración de inquilinos podrán enviar una solicitud de excepción para una fecha anterior o posterior de transición.

- Por una fecha anterior de transición, actualice la fecha existente a su opción preferida en la lista. Esto no requiere aprobación. También puede cambiar manualmente si nuestras fechas no le resultan convenientes.

- Por una fecha de transición posterior, puede enviar una solicitud de excepción. Las fechas sugeridas estarán disponibles en el cuadro desplegable. Una vez aprobada, la fecha se actualizará en el portal en consecuencia.

Puede solicitar un total de dos excepciones por entorno. Las excepciones se conceden en función de la justificación de negocio además de la fecha propuesta seleccionada. La fecha se actualizará en el portal una vez confirmada.

> [!NOTE]
> Si la transición programada es en 48 horas, no podrá cambiar la fecha. Asimismo, no puede solicitar una fecha después del 1 de octubre de 2020 ya que el cliente web heredado ya no estará disponible.

### <a name="my-auto-transition-date-is-within-48-hours-and-i-cant-change-the-date-within-the-portal-how-can-i-stop-transition-taking-place"></a>La fecha de transición automática es en 48 horas y no puedo cambiar la fecha en el portal. ¿Cómo puedo impedir que se realice la transición?

La capacidad para cambiar la fecha de transición para un entorno está disponible solo hasta 48 horas antes de la transición. Para detener el proceso después de este período, plantee un caso de soporte técnico. 

> [!NOTE]
> No podemos garantizar que la transición pueda ser detenida si la solicitud se realiza después de que la fecha se haya bloqueado en el portal (48 horas o menos).

### <a name="i-have-environments-without-a-target-auto-transition-date-can-i-update-these-to-include-a-date"></a>Tengo entornos sin una fecha de transición automática de destino. ¿Puedo actualizar estos para incluir una fecha?

Sí, si tiene **Administrador global** o **Administrador de servicio** para el inquilino, seleccione el entorno, envíe una solicitud de excepción y actualice con el plazo de tiempo propuesto con la lista de fecha de destino. 

Actualizaremos el portal con la fecha para confirmar. También se enviarán correos electrónicos de notificación a los administradores de inquilinos globales cuando se aproxime la fecha de transición. Esto seguirá el procedimiento restante estándar detallado en este documento.

### <a name="is-there-a-recommended-checklist-i-should-run-through-before-transition"></a>¿Existe una lista de comprobación recomendada que debo ejecutar antes de la transición?

Consulte el contenido de soporte técnico disponible en el [sitio de la comunidad](https://community.dynamics.com/365/unified-interface/). También tenemos una [lista de comprobación de la transición](https://aka.ms/UIChecklist) para ayudarle a planear eficazmente. Revísela cuidadosamente para asegurarse de que está de acuerdo con la transición a la interfaz unificada.

### <a name="my-environment-has-been-transitioned-but-i-am-finding-blocking-issues-for-my-users-and-wish-to-move-back-to-the-legacy-web-client-is-this-possible"></a>Mi entorno ha realizado la transición, pero estoy encontrando problemas de bloqueo para mis usuarios y deseo volver al cliente web heredado. ¿Esto es posible?

Sí, aún podrá volver al cliente web heredado en un plazo de hasta 10 días después de la transición. Puede realizar el [cambio manualmente](https://docs.microsoft.com/power-platform/admin/enable-unified-interface-only) durante los primeros 4 días o después, presentar una solicitud de soporte técnico en canal habitual, ya que el cambio manual se deshabilitará. 

> [!NOTE]
> Los 10 días deberán ser antes de 1 de octubre de 2020 ya que el cliente web heredado ya no estará disponible a partir de esa fecha.

### <a name="i-want-to-transition-after-october-1-2020-is-that-possible"></a>Quiero realizar la transición después del 1 de octubre de 2020. ¿Es posible eso?

El cliente web heredado no estará disponible a partir del 1 de octubre de 2020. No podemos retrasar la transición más allá de esa fecha.

Si encuentra elementos de bloqueo, regístrelos mediante el proceso de soporte estándar cuanto antes.

### <a name="what-is-the-standard-reminder-procedure-throughout-this-process"></a>¿Cuál es el procedimiento de aviso estándar en este proceso?

Microsoft enviará la comunicación siguiente:

-   Mensaje inicial para cada entorno que tiene una fecha de transición asignada
-   Mensaje de recordatorio 2 días antes de que las fechas se bloqueen en el portal
-   El aviso final para indicar que la fecha de transición está bloqueada y seguir adelante.
-   Mensaje de cierre por confirmar el éxito (o si se ha producido un problema)

Los mensajes se pueden ver con los canales siguientes:
-   Centro de mensajes en el inquilino de Microsoft 365. Suele ser visible para roles como administrador global, administrador de servicios, lector de mensajes de servicio.
-   Correo electrónico directo.  Los correos electrónicos se envían únicamente al rol de administrador del sistema para el entorno específico en cuestión, o las direcciones de correo electrónico que se hayan agregado a la pestaña “Notificación” en el portal de administración de entorno.

> [!NOTE]
> Recibirá un mensaje de correo electrónico para cada entorno donde su cuenta de usuario tenga el rol de administrador del sistema.

### <a name="i-have-requested-a-date-to-postpone-but-still-receiving-e-mails-and-message-center-posts-that-my-environment-is-set-to-transition-should-i-be-concerned"></a>He solicitado una fecha para posponer, pero sigo recibiendo correos electrónicos y el Centro de mensajes publica que mi entorno está establecido para transición. ¿Debería preocuparme?

Nuestra primera recomienda es consultar el portal de transición (<https://runone.powerappsportals.com/>) ya que ésta será única fuente fiable para todos sus entornos. Si se actualiza la fecha, es muy probable que nuestro sistema de comunicación envíe el mensaje antes de que actualicemos la lista de comunicaciones. 

Si la fecha en el portal no se actualiza con la nueva fecha, presente una solicitud de soporte técnico siguiendo el procedimiento estándar.

### <a name="if-i-already-have-an-environment-transitioned-to-unified-interface-will-i-still-be-able-to-switch-back-to-the-legacy-web-client-manually"></a>Si ya tengo un entorno que ha realizado la transición a la interfaz unificada, ¿podré volver al cliente web heredado manualmente?

Si el entorno transición ha realizado la transición hace al menos 4 días, intentaremos deshabilitar el cambio manual al antiguo cliente web. 

Si encuentra esta opción se ha deshabilitado y tiene necesidad de volver, presente una solicitud de soporte técnico en el canal habitual para su evaluación.

### <a name="is-there-a-specific-day-and-time-when-automatic-transitions-will-take-place"></a>¿Hay un día y una hora específicos en que ocurrirán las transiciones automáticas? 

No anticipamos tiempos de inactividad al crear esta transición. Sin embargo, solo realizaremos una transición automática el viernes, y siguiendo las mismas escala de tiempo de mantenimiento que se indican en nuestras directivas y comunicaciones estándar. Más información: [Escala de tiempo de mantenimiento](https://docs.microsoft.com/power-platform/admin/policies-communications#maintenance-timeline)




