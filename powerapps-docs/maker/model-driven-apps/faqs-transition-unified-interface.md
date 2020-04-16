---
title: 'Preguntas más frecuentes: Transición a la Interfaz unificada | MicrosoftDocs'
description: Preguntas más frecuentes relacionadas con el proceso de transición para desplazar usuarios del cliente web heredado a la Interfaz unificada.
ms.custom: ''
ms.date: 03/04/2020
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
ms.openlocfilehash: 13bf17886ab44fb14f1b510615d538a48d8090fc
ms.sourcegitcommit: 310dd3dc68ffebe6a416450836ac0ba988b84fb4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "3162139"
---
# <a name="faqs-transition-to-unified-interface"></a>Preguntas más frecuentes: Transición a la Interfaz unificada

Este tema proporciona respuestas a las preguntas más comunes sobre Interfaz unificada y sobre la transición del cliente web heredado a Interfaz unificada.

## <a name="faqs-unified-interface-and-legacy-web-client"></a>Preguntas frecuentes: Interfaz unificada y cliente web heredado

### <a name="why-should-i-move-to-unified-interface"></a>¿Por qué debería pasar a Interfaz unificada?

La visión de Microsoft de un lugar de trabajo productivo requiere una interfaz moderna que incluya las características y mejoras contenidas en Interfaz unificada, que proporciona una experiencia de usuario más consistente, un rendimiento mejorado y una mayor eficiencia del usuario. Para obtener más información, consulte [Cuaderno de estrategias de Interfaz unificada.](https://docs.microsoft.com/powerapps/maker/model-driven-apps/unified-interface-playbook)

### <a name="are-my-isvs-compatible"></a>¿Son compatibles mis ISV?

Los ISV han sido notificados para tomar medidas en la transición a Interfaz unificada. Póngase en contacto con su ISV directamente con respecto a su escala de tiempo para la compatibilidad con Interfaz unificada.

### <a name="what-is-the-retraining-effort"></a>¿Cuál es el esfuerzo de reciclaje?

Desde el punto de vista tecnológico, la capacitación debe ser mínima, ya que la lógica y el esquema de su negocio no cambian. La nueva formación debe centrarse en las novedades dentro de la navegación y el aspecto general. Es posible que se requiera aprendizaje adicional si ha tomado la decisión comercial de alterar el diseño para optimizar las nuevas capacidades y características.

### <a name="will-i-need-to-re-create-my-solution-customizations"></a>¿Tendré que volver a crear las personalizaciones de mi solución?

No, no debería tener que volver a crear ninguna personalización, siempre que haya seguido la [Guía para desarrolladores de Common Data Service](/powerapps/developer/common-data-service/overview) y actualizado cualquier cambio. Sin embargo, puede haber nuevas oportunidades para asumir nuestras últimas inversiones que podrían conducir a modificaciones de personalización.

### <a name="how-long-will-it-take-to-transitionwhat-is-the-work-effort"></a>¿Cuánto tiempo llevará la transición / cuál es el esfuerzo de trabajo?

El esfuerzo de trabajo aquí variará según la complejidad de su entorno. Recomendamos comenzar con una aplicación piloto / modelo POC para comenzar las pruebas. A partir de ahí, puede trabajar con la empresa para planificar un despliegue completo de Interfaz unificada. Vea el [Cuaderno de estrategias de Interfaz unificada](https://docs.microsoft.com/powerapps/maker/model-driven-apps/unified-interface-playbook) y [lista de verificación de planificación](https://aka.ms/UIChecklist) para obtener orientación adicional sobre cómo comenzar y nuestras [notas del producto](https://download.microsoft.com/download/A/F/3/AF3D45A7-4F38-41BE-8956-1DF7A4A5AFDB/approaching-unified-interface-transition.pdf).

### <a name="where-can-i-find-public-information-about-the-unified-interface-direction"></a>¿Dónde puedo encontrar información pública sobre la dirección de Interfaz unificada?

La dirección estratégica de Interfaz unificada ya está en el dominio público a través de eventos como:
- [MBAS: BRK2073 Microsoft Power Apps : Ejecute una interfaz de usuario: el futuro del lienzo, basado en modelos y Interfaz unificada en Power Apps](https://powerusers.microsoft.com/t5/MBAS-Gallery/Microsoft-PowerApps-Run-one-UI-the-future-of-canvas-model-driven/td-p/301580)
- [Mejores prácticas de implementación de BRK3031 para Dynamics 365: Haciendo el cambio a Interfaz unificada moderna](https://powerusers.microsoft.com/t5/Microsoft-Business-Applications/Implementation-Best-Practices-for-Dynamics-365-Making-the-move/m-p/299928)


### <a name="as-an-on-premises-customer-looking-to-move-to-the-cloud-what-is-the-best-approach-to-adopt-unified-interface"></a>Como cliente local que busca moverse a la nube, ¿cuál es el mejor enfoque para adoptar Interfaz unificada?

Se recomienda encarecidamente planificar su traslado a Interfaz unificada al mismo tiempo que migra a la nube. Comience a probar su cliente web heredado dentro de Interfaz unificada y una vez migrado, confirme la compatibilidad de Interfaz unificada antes de su versión para su comunidad de usuarios. Esto reducirá el esfuerzo de aprendizaje y permitirá a los usuarios adoptar algunas de las nuevas características y capacidades que ofrece Interfaz unificada. Para obtener más información, hable con su representante de Microsoft.

### <a name="when-will-isvs-be-notified-of-the-need-to-move-to-unified-interface"></a>¿Cuándo se notificará a los ISV la necesidad de pasar a Interfaz unificada?

Los ISV han sido notificados para tomar medidas en la transición a Interfaz unificada. Póngase en contacto con su ISV directamente con respecto a su escala de tiempo para la compatibilidad con Interfaz unificada.

### <a name="how-are-language-translations-handled"></a>¿Cómo se gestionan las traducciones de idiomas?

El proceso para la traducción de idiomas no cambia principalmente, con la excepción del mapa del sitio. Las áreas, grupos y subáreas del mapa del sitio se localizan en el editor del mapa del sitio.

### <a name="i-dont-have-budget-or-resources-to-do-a-project-is-the-deadline-a-fixed-date"></a>No tengo presupuesto ni recursos para hacer un proyecto. ¿La fecha límite es una fecha fija?

Estamos centrados en alejarnos del cliente web heredado antes del 1 de diciembre de 2020. Recomendamos realizar algunas pruebas lo antes posible para comprender la complejidad del proyecto para que su organización sea compatible. En la mayoría de los casos, no se debe requerir un rediseño extenso para avanzar rápidamente y comenzar a ver el beneficio del usuario. Póngase en contacto con Microsoft para proporcionar cualquier comentario que pueda detener su transición creando un caso de soporte.

### <a name="were-working-on-transitioning-to-unified-interface-but-have-hit-some-issues-how-can-we-report-to-microsoft"></a>Estamos trabajando en la transición a Interfaz unificada, pero hemos tenido algunos problemas; ¿Cómo podemos informar a Microsoft?

Revise nuestros [recursos](https://community.dynamics.com/365/unified-interface/) para ayudarle con la orientación y registrar un caso de soporte siguiendo su procedimiento estándar. También puede notificar a su partner, representante de Microsoft o al equipo de FastTrack (si corresponde).

### <a name="when-should-i-start-moving-to-unified-interface"></a>¿Cuándo debo comenzar a pasarme a Interfaz unificada?

Puede pasarse de inmediato; ya tenemos muchos clientes en transición en producción a Interfaz unificada. Comience su prueba lo antes posible. Acceda a nuestro sitio de la comunidad: <https://community.dynamics.com/365/unified-interface/> para ver contenido útil. Use el procedimiento de Soporte estándar para registrar cualquier problema.

### <a name="what-are-the-risks-associated-with-moving-to-unified-interface"></a>¿Cuáles son los riesgos asociados con mudarse a Interfaz unificada?

Vemos un riesgo en permanecer en el cliente web heredado porque nuestra inversión y dirección estratégica está en Interfaz unificada. Si planea comenzar la transición ahora, revise nuestro [sitio de la comunidad](https://community.dynamics.com/365/unified-interface/) y [guías de inicio rápido](https://docs.microsoft.com/powerapps/maker/model-driven-apps/transition-web-app-existing). Esto lo ayudará a identificar vacíos (si los hay) y a tener un plan para solucionarlos antes de realizar una implementación completa.

### <a name="i-have-a-new-feature-idea-for-unified-interface-where-do-i-log-it"></a>Tengo una nueva idea de función para Interfaz unificada; ¿dónde la registro?

Visita nuestro portal de ideas (<https://powerusers.microsoft.com/t5/PowerApps-Ideas/idb-p/PowerAppsIdeas>), seleccione **Sugerir una idea** y etiquete el elemento con la categoría "Interfaz unificada".

### <a name="is-there-any-supporting-content-to-help-me-plan-and-execute-my-transition-to-unified-interface"></a>¿Hay algún contenido de apoyo que me ayude a planificar y ejecutar mi transición a Interfaz unificada?

Sí, tenemos un nuevo grupo comunitario (<https://community.dynamics.com/365/unified-interface/>) que proporciona contenido útil, un foro interactivo y blog para ver las últimas actualizaciones e información sobre Interfaz unificada.

### <a name="how-does-this-move-impact-on-premises-customer-and-what-will-happen-when-the-web-client-is-deprecated-do-web-client-forms-become-unsupported"></a>¿Cómo afecta este movimiento al cliente local y qué sucederá cuando el cliente web quede en desuso (los formularios del cliente web dejan de ser compatibles)?

Este anuncio solo está vigente para clientes en línea actualmente. Continuaremos brindando soporte al cliente web heredado para implementaciones locales.

### <a name="is-the-timeline-applicable-for-customers-using-government-community-cloud-gcc-and-other-data-centers-such-as-china"></a>¿Es aplicable la línea de tiempo para los clientes que usan Government Community Cloud (GCC) y otros centros de datos como China?

Planeamos lanzar actualizaciones de Interfaz unificada a estos centros de datos como parte del programa de lanzamiento estándar.

### <a name="what-action-should-i-take-as-a-unified-service-desk-customer-who-is-still-on-the-web-client"></a>¿Qué medidas debo tomar como cliente de Unified Service Desk que todavía está en el cliente web?

Los clientes de Unified Service Desk, que todavía están en el cliente web necesitan migrar sus configuraciones del cliente web a Interfaz unificada. Esto requerirá actualizarse a las últimas versiones de [Unified Service Desk](https://docs.microsoft.com/dynamics365/unified-service-desk/download-unified-service-desk?view=dynamics-usd-4.1) (componentes del cliente y del servidor). Tenemos un [asistente de migración](https://docs.microsoft.com/dynamics365/unified-service-desk/admin/migration-steps-web-client-unified-interface-configuration?view=dynamics-usd-4.1) para ayudar con este esfuerzo.

### <a name="are-there-any-other-deprecations-that-i-should-plan-for"></a>¿Hay otras obsolescencias para las que debería prepararme?

Revise nuestro [página de notificación de desuso](https://docs.microsoft.com/power-platform/important-changes-coming) para identificar si hay otras áreas que también requieren planificación.

### <a name="where-can-i-find-further-information-on-the-transition-service"></a>¿Dónde puedo encontrar más información sobre el servicio de transición?

Para ayudar a acelerar el impulso para la transición, proporcionamos una fecha objetivo sugerida para que los entornos pasen del cliente web heredado a Interfaz unificada a través de nuestro servicio de transición. Los clientes deberán aprobar la fecha anterior a cualquier acción y luego recibirán una serie de mensajes recordatorios de comunicación a medida que se acerque la fecha. Las fechas también se pueden reprogramar si no son adecuadas para el negocio hasta la fecha límite del 1 de diciembre de 2020. Para obtener más información, vea la sección siguiente.


## <a name="faqs-transitioning-to-unified-interface"></a>Preguntas frecuentes: Transición a Interfaz unificada

### <a name="where-can-i-go-to-see-the-transition-dates-that-have-been-suggested-for-my-environments"></a>¿Dónde puedo ir para ver las fechas de transición que se han sugerido para mis entornos? 

Utilice el portal de transición para administrar la fecha de transición de su entorno: <https://runone.powerappsportals.com>.

### <a name="how-do-i-gain-access-to-the-portal"></a>¿Cómo accedo al portal?

Haga lo siguiente:
1. Visite <https://runone.powerappsportals.com>.
2. Inicie sesión con las credenciales de administración del inquilino que desea administrar.
3. Seleccione **Mis entornos** y revise todos los entornos que tengan aplicada una fecha sugerida.

### <a name="i-see-my-environment-has-a-date-suggested-for-transition-can-i-change-this-date"></a>Veo que mi entorno tiene una fecha sugerida para la transición. ¿Puedo cambiar esta fecha?

Sí, esto es posible si tiene el rol de **administrador global**, el **administrador de servicio de Dynamics 365** o el **administrador de Power Platform** para el inquilino. 

Las fechas asociadas a su entorno son una sugerencia que requiere aprobación para continuar. Aprobar si la fecha funciona para su organización.  

Para cambiar la fecha, seleccione el icono desplegable junto al entorno y vea el registro. Los roles de administrador de inquilinos podrán reprogramar la fecha de transición a una fecha anterior o posterior.

Para reprogramar a una fecha anterior, actualice la fecha existente a su opción preferida en la lista. También puede [cambiar manualmente](transition-web-app.md) si nuestras fechas no le resultan convenientes. 
 
Para programar una fecha posterior, seleccione el botón de reprogramar fecha de transición. Las fechas sugeridas estarán disponibles en el cuadro desplegable. Una vez aprobada, la fecha se actualizará en el portal según corresponda. Acepte la fecha actualizada si desea que su entorno se transite. 
 
Los cambios de fecha serán revisados y concedidos si la fecha es anterior al 1 de diciembre de 2020. La fecha se actualizará en el portal una vez confirmada. 

> [!NOTE]
> Si tiene una transición aprobada y la fecha programada es en las próximas 48 horas, no podrá cambiar la fecha. Del mismo modo, no puede solicitar una fecha posterior al 1 de diciembre de 2020, ya que el cliente web heredado ya no estará disponible.

### <a name="what-will-happen-if-i-dont-opt-in-and-approve-a-suggested-transition-date-for-my-environment"></a>¿Qué sucederá si no participo y apruebo una fecha de transición sugerida para mi entorno?

No se producirá ningún cambio en su entorno si no ha aprobado la fecha sugerida dentro del portal. Cuando pase la fecha sugerida, trataremos de proporcionarle otra fecha en el futuro para que la considere.  
 
> [!NOTE]
> Después del 1 de diciembre de 2020, todos los entornos se actualizarán a Interfaz unificada.

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

Sí, aún podrá volver al cliente web heredado en un plazo de hasta 10 días después de la transición. Puede hacer el [cambio manualmente](https://docs.microsoft.com/power-platform/admin/enable-unified-interface-only) durante los primeros 10 días o elevar una [solicitud de soporte estándar](https://admin.powerplatform.microsoft.com/support?referer=mbssupport) y configurar el tipo de problema para que sea "Transición del cliente web heredado a Interfaz unificada" ya que el cambio manual quedará deshabilitado. 

> [!NOTE]
> Los 10 días deben ser anteriores al 1 de diciembre de 2020 ya que el cliente web heredado ya no estará disponible después de esa fecha.

### <a name="i-want-to-transition-after-december-1-2020-is-that-possible"></a>Quiero hacer la transición después del 1 de diciembre de 2020. ¿Es posible eso?

El cliente web heredado no estará disponible después del 1 de diciembre de 2020. No tenemos la capacidad de aplazar la fecha más allá de ese período.

Si encuentra elementos de bloqueo, regístrelos mediante el proceso de soporte estándar cuanto antes.

### <a name="what-is-the-standard-reminder-procedure-throughout-this-process"></a>¿Cuál es el procedimiento de aviso estándar en este proceso?

La comunicación será en oleadas, al menos 30 días antes de la período de tiempo sugerido, pero puede iniciar sesión en el portal (<https://runone.powerappsportals.com>) en cualquier momento para ver el estado. Microsoft enviará la comunicación siguiente:

-    Mensaje inicial para cada entorno que tiene una fecha de transición sugerida.
-    Si ha aprobado la fecha, recibirá un mensaje recordatorio dos días antes de que las fechas estén bloqueadas en el portal. 
-    El recordatorio final se enviará dos días antes de la transición. Esto indicará que la fecha de transición está bloqueada y seguirá adelante con la transición.
-    Después de la transición, se enviará un mensaje de cierre para confirmar que el proceso se ha realizado correctamente (o si se produjo un problema)

Los mensajes se pueden ver con los canales siguientes:
-    Centro de mensajes en el inquilino de Microsoft 365. Suele ser visible para roles como administrador global, administrador de servicios, lector de mensajes de servicio.
-    Correo electrónico directo.  Los correos electrónicos se envían únicamente al rol de administrador del sistema para el entorno específico en cuestión, o las direcciones de correo electrónico que se hayan agregado a la pestaña “Notificación” en el portal de administración de entorno.

> [!NOTE]
> Recibirá un mensaje de correo electrónico para cada entorno donde su cuenta de usuario tenga el rol de administrador del sistema.

### <a name="i-have-requested-a-date-to-postpone-but-still-receiving-e-mails-and-message-center-posts-that-my-environment-is-set-to-transition-should-i-be-concerned"></a>He solicitado una fecha para posponer, pero sigo recibiendo correos electrónicos y el Centro de mensajes publica que mi entorno está establecido para transición. ¿Debería preocuparme?

Nuestra primera recomendación es verificar el portal de transición (<https://runone.powerappsportals.com/>) ya que será la única fuente de verdad para todos sus entornos. Si se actualiza la fecha, es muy probable que nuestro sistema de comunicación envíe el mensaje antes de que actualicemos la lista de comunicaciones. 

Si la fecha en el portal no se actualiza con la nueva fecha, presente una solicitud de soporte técnico siguiendo el procedimiento estándar.

Solo se realizará la transición de las fechas aprobadas por el administrador. 

### <a name="if-i-already-have-an-environment-transitioned-to-unified-interface-will-i-still-be-able-to-switch-back-to-the-legacy-web-client-manually"></a>Si ya tengo un entorno que ha realizado la transición a la interfaz unificada, ¿podré volver al cliente web heredado manualmente?

Si el entorno transición ha realizado la transición hace al menos 10 días, intentaremos deshabilitar el cambio manual al antiguo cliente web. 

Si encuentra que se ha deshabilitado y tiene un requisito para volver a cambiar, eleve una [solicitud de soporte estándar](https://admin.powerplatform.microsoft.com/support?referer=mbssupport) y configure el tipo de problema como "Transición del cliente web heredado a Interfaz unificada".

### <a name="is-there-a-specific-day-and-time-when-approved-transitions-will-take-place"></a>¿Hay un día y hora específicos en que se llevarán a cabo las transiciones aprobadas?

No anticipamos tiempos de inactividad al crear esta transición. Sin embargo, solo haremos una transición un viernes, siguiendo los mismos plazos de mantenimiento descritos en nuestras políticas y comunicaciones estándar. Más información: [Escala de tiempo de mantenimiento ](https://docs.microsoft.com/power-platform/admin/policies-communications#maintenance-timeline)

### <a name="are-environments-from-all-data-centers-included-within-this-transition-service"></a>¿Se incluyen entornos de todos los centros de datos en este servicio de transición?

Actualmente, no se han incluido entornos de centros de datos específicos, como la nube de la comunidad gubernamental (GCC), en el portal. Proporcionaremos fechas de transición sugeridas para estos entornos antes de junio de 2020. Los clientes que quieran mudarse a Interfaz unificada siempre pueden [cambiar manualmente](/power-platform/admin/enable-unified-interface-only#how-to-enable-unified-interface-only-mode) en cualquier momento antes del 1 de diciembre de 2020.


