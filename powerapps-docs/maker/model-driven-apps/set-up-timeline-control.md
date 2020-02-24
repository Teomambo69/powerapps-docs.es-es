---
title: Configurar el control de escala de tiempo (sección) en PowerApps | MicrosoftDocs
description: Aprender a configurar el control de escala de tiempo (sección) en PowerApps
ms.date: 02/03/2020
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
ms.openlocfilehash: 8afb5427a74b879b0e407b1038705a0bbc15920b
ms.sourcegitcommit: c5b9bdf820c7d60f00bf1b16d9e9f7d046fd7252
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2020
ms.locfileid: "3013122"
---
# <a name="set-up-timeline-section-control"></a>Configurar la sección de escala de tiempo (control)

Las actividades que utiliza en Escala de tiempo para realizar un seguimiento de todas sus comunicaciones con un cliente o contacto se pueden personalizar de acuerdo con los requisitos de su empresa u organización.

  > [!div class="mx-imgBorder"]
  > ![Vista de escala de tiempo de actividades en PowerApps](../../user/media/TimelineViewOfActivity.png "Vista de escala de tiempo de actividades en PowerApps")

  1. Buscar registros
  2. Tomar notas
  3. Agregar datos y actividades
  4. Filter
  5. Más comandos
  6. Estado de la actividad
  7. Iconos de actividad
  8. Fecha y hora

Para obtener más información, vea [Agregar una cita, correo electrónico, llamada de teléfono, nota o actividad de tarea a la línea de tiempo ](../../user/add-activities.md).

La personalización se categoriza en las siguientes áreas:

- Módulo
- Tipo de actividad
- Campo

## <a name="customize-modules"></a>Personalizar módulos

Los módulos son Actividades, Publicaciones y Notas. Como personalizador, puede elegir qué módulos desea mostrar a los usuarios según los requisitos de su empresa.

1.  Inicie sesión en el entorno de `https://<YourOrgURL>.dynamics.com/apps`.

2.  Abra una aplicación basada en modelo y en la barra de comandos, seleccione **Configuración** ![Configuración](../model-driven-apps/media/powerapps-gear.png "Configuración") > **Configuración avanzada**.

3.  Vaya a **Personalizaciones** > **Personalización** > **Personalización del sistema**. La página del explorador de soluciones se abre en una nueva ventana del navegador. 

4.  Expanda **Entidades** en **Componentes** en el panel de la solución predeterminada.

5.  Seleccione una entidad y seleccione **Formularios**. Por ejemplo, seleccione la entidad **Cuenta**.

6.  Selecciona el registro **Cuenta para experiencia interactiva** que es un tipo de formulario **Principal**. El formulario **Cuenta para experiencia interactiva** se abre en una nueva ventana del navegador.

   > [!div class=mx-imgBorder] 
   > ![Seleccione el formulario de entidad con experiencia interactiva en el nombre](media/account-interactive-experience.png "Seleccione el formulario de entidad con experiencia interactiva en el nombre")

   Para la Interfaz unificada, debe usar el nombre del formulario que tiene `<Entity> for Interactive experience`. Los nombres de los formularios para otras entidades son los siguientes:

   | Entidad | Nombre |
   |--------------------------|----------------------------------|
   | Cuenta | Cuenta para experiencia interactiva |
   | Caso | Caso para experiencia interactiva |
   | Contacto | Contacto para experiencia interactiva |

7.  Haga doble clic en el campo **Pestañas de conversación**en la sección **Escala de tiempo**. Se muestra el diálogo **Propiedades de la pestaña Actividades**.

    > [!div class=mx-imgBorder] 
    > ![Haga doble clic en el campo del panel de redes sociales](media/timeline-conversation-tabs-field.png "Haga doble clic en el campo del panel de redes sociales")   

8.  Seleccione la opción **Mostrar lo seleccionado** para el campo **Mostrar estos módulos** en el contenedor **Filtrado por**.

9.  Seleccione los módulos que desea mostrar a los usuarios. Seleccione solo los módulos que necesita su organización.

10. Especifique lo siguiente en el contenedor **Opciones adicionales**.


    | Campo/opción | Descripción | Valor |
    |------------------------------------------|--------------------------------------------------------------|---------------------------|
    | Módulo predeterminado para la experiencia de creación | Seleccione el módulo para el que desea la experiencia de creación predeterminada en la escala de tiempo. <br><br> El valor predeterminado es **Notas**.  | Notas |
    | Mostrar panel de filtro | Seleccione la casilla si desea mostrar el icono de filtro para los usuarios. Si deja la casilla vacía, no habrá filtros para los usuarios. |  |
    | Expandir panel del filtro de forma predeterminada | Seleccione la casilla, de forma predeterminada, si desea mostrar el panel de filtro en el modo expandido. |
    | Sort | Seleccione el orden de clasificación en función del cual se muestran los registros en la escala de tiempo. La ordenación se basa en el campo que elija para Actividades. Si no existe un campo para la publicación, las notas o la actividad, la ordenación se realiza en función del campo **Última actualización**. <br><br> El criterio de ordenación predeterminado es **Descendente**.  <br><br> **Nota:** cambiar el orden de clasificación no cambiará la propiedad de tiempo visualizada en el control de la escala de tiempo. Para personalizar el formulario de tarjeta de escala de tiempo, consulte [Personalizar el formulario de tarjeta](#customize-the-card-form).  | Descendente |
    | Número de resultados | El número máximo de registros que se muestran en la escala de tiempo antes de seleccionar la opción **Más**. Cada vez que selecciona la opción **Más**, la escala de tiempo muestra el número configurado de registros. Puede configurar un valor de 1 a 50. <br><br> El valor predeterminado es **10**. | 10 |

    > [!div class=mx-imgBorder] 
    > ![Configurar módulo de escala de tiempo](media/timeline-module.png "configurar módulo de escala de tiempo")

11. Seleccione **Aceptar** y, a continuación, **Guardar**.

12. Seleccione **Publicar** para publicar las personalizaciones.

## <a name="customize-activity"></a>Personalizar actividad

Como personalizador, puede elegir qué entidades desea mostrar actividades a los usuarios según los requisitos de su empresa. Para un mejor rendimiento, seleccione solo las actividades que son específicas de la empresa y anule la selección de las actividades que no se utilizan.

1.  Inicie sesión en el entorno de `https://<YourOrgURL>.dynamics.com/apps`.

2.  Abra una aplicación basada en modelo y en la barra de comandos, seleccione **Configuración** ![Configuración](../model-driven-apps/media/powerapps-gear.png "Configuración") > **Configuración avanzada**.

3.  Vaya a **Personalizaciones** > **Personalización** > **Personalización del sistema**. La página del explorador de soluciones se abre en una nueva ventana del navegador.  

4.  Expanda **Entidades** en **Componentes** en el panel de la solución predeterminada.

5.  Seleccione una entidad y seleccione **Formularios**. Por ejemplo, seleccione la entidad **Cuenta**.

6.  Selecciona el registro **Cuenta para experiencia interactiva** que es un tipo de formulario **Principal**. El formulario **Cuenta para experiencia interactiva** se abre en una nueva ventana del navegador.

    > [!div class=mx-imgBorder] 
    > ![Seleccione el formulario de entidad con experiencia interactiva en el nombre](media/account-interactive-experience.png "Seleccione el formulario de entidad con experiencia interactiva en el nombre")

    Para la Interfaz unificada, debe usar el nombre del formulario que tiene `<Entity> for Interactive experience`. Los nombres de los formularios para otras entidades son los siguientes:

    | Entidad | Nombre |
    |--------------------------|----------------------------------|
    | Cuenta | Cuenta para experiencia interactiva |
    | Caso | Caso para experiencia interactiva |
    | Contacto | Contacto para experiencia interactiva |

7.  Haga doble clic en el campo **Pestañas de conversación**en la sección **Escala de tiempo**. Se muestra el diálogo **Propiedades de la pestaña Actividades**.

    > [!div class=mx-imgBorder] 
    > ![Haga doble clic en el campo del panel de redes sociales](media/timeline-conversation-tabs-field.png "Haga doble clic en el campo del panel de redes sociales") 

8.  Seleccione la opción **Mostrar lo seleccionado** para el campo **Mostrar estas actividades** en el contenedor **Filtrado por**.

9.  Seleccione las actividades que desea mostrar a los usuarios.

10. Seleccione una opción de la lista para la opción **Ordenar escala de tiempo por** en el contenedor **Datos**. Por ejemplo, seleccione la opción **Última actualización**.

11. Especifique lo siguiente en el contenedor **Opciones adicionales**.
    
    | Campo/opción | Descripción |Valor |
    |------------------------------------------|------------------------------------------------------------|-------------------|
    | Mostrar encabezado de actividad con |  Los valores posibles son **Formato predeterminado** y **Etiquetas de campo**. <br><br> **Nota:** <ul><li> Si selecciona **Formato predeterminado**, siempre debe seleccionar **Campos predeterminados** para el campo **Mostrar actividades con**. <br> ![Formato predeterminado y campos predeterminados](media/default-format-default-fields.png "Formato predeterminado y campos predeterminados") </li> <li> Si selecciona **Etiquetas de campo**, puede seleccionar **Campos predeterminados** o **Formulario de tarjeta** para el campo **Mostrar actividades con**. <br> ![Etiquetas de campo e inicio predeterminado](media/field-label-card-form.png "Formato predeterminado y campos predeterminados") </li> <li> Cuando selecciona **Formato predeterminado** y selecciona **Formulario de tarjeta** para el campo **Mostrar actividades con**, el sistema ignora el valor **Formulario de tarjeta** y utiliza **Campos predeterminados** para mostrar las actividades. </li> <ul>| Formato predeterminado |
    | Crear actividades con | Seleccione cómo desea que los usuarios creen actividades. Los valores posibles son **Creación rápida de formulario** y **Formulario principal**. | Creación rápida de formulario |
    | Mostrar actividades con | Seleccione cómo desea mostrar las actividades. Los valores posibles son **Campos predeterminados** y **Formulario de tarjeta**.  Si selecciona **Formulario de tarjeta**, debe seleccionar un formulario de tarjeta para la actividad.  | |
    | Seleccionar actividad | Seleccione una actividad de la lista.  <br><br> **Nota:** Este campo aparece solo cuando selecciona **Formulario de tarjeta** para el campo **Mostrar actividades con**.| Correo |
    | Seleccionar formulario de tarjeta | Seleccione un formulario de tarjeta de la lista.  <br><br> **Nota:** Este campo aparece solo cuando selecciona **Formulario de tarjeta** para el campo **Mostrar actividades con**. | Formulario de tarjeta de correo electrónico |

    > [!div class=mx-imgBorder] 
    > ![Personalizar módulo de escala de tiempo](media/timeline-activity1.png "Personalizar módulo de escala de tiempo")

12. Seleccione **Aceptar** y, a continuación, **Guardar**.

13. Seleccione **Publicar** para publicar las personalizaciones.

Dado que el ejemplo considerado en este procedimiento es **Cuenta**, veamos la actividad **Correo electrónico** en el **Escala de tiempo** de una página de cuenta.

   | Campo | Valor |
   |---------------------------|---------------------------|
   | Mostrar encabezado de actividad con | Formato predeterminado |
   | Mostrar actividades con | Campos predeterminados |

   > [!div class=mx-imgBorder] 
   > ![Actividad de correo electrónico en escala de tiempo](media/timeline-email-activity1.png "Actividad de correo electrónico en escala de tiempo")

   Los campos predeterminados para una actividad de correo electrónico en el modo contraído contienen lo siguiente:

   1. Correo electrónico de \<propietario\>
   2. Asunto
   3. Descripción
   4. Estado de la actividad
   5. Fecha y hora

Después de modificar el formulario **Tarjeta de correo electrónico** (de la entidad **Correo electrónico**) y actualizar las opciones en el formulario **Cuenta para experiencia interactiva** en la entidad **Cuenta**, puede ver los cambios.

   | Campo | Valor |
   |---------------------------|---------------------------|
   | Mostrar encabezado de actividad con | Etiquetas de campo |
   | Mostrar actividades con | Formulario de tarjeta |
   | Seleccionar actividad | Correo |
   | Seleccionar formulario de tarjeta | Formulario de tarjeta de correo electrónico |

   > [!div class=mx-imgBorder] 
   > ![Actividad de correo electrónico en escala de tiempo](media/timeline-email-activity2.png "Actividad de correo electrónico en escala de tiempo")

   Los campos predeterminados para una actividad de correo electrónico en el modo contraído contienen lo siguiente:

   1. \<Nombre\> del propietario
   2. Prioridad
   3. Descripción
   4. Estado de la actividad

La cadena predeterminada para las actividades es la siguiente:

| Actividad | Campos predeterminados | Imagen |
|----------------|--------------------------------|------------------------------|
| Cita | `Appointment from <Owner Name>`| ![Cita](media/appointment.png "Cita") |
| Correo | `Email from <Owner Name>` | ![Correo electrónico](media/email.png "Correo") |
| Llamada de teléfono | `Phone Call from <Owner Name>` <br> Cuando el agente inicia una llamada.| ![Llamada de teléfono](media/phonecall-owner.png "Llamada de teléfono") | 
| | `Phone Call from <Contact>` <br> Cuando el cliente inicia una llamada. | ![Llamada de teléfono](media/phonecall-contact.png "Llamada de teléfono") |
| Tarea | `Task modified by <Owner Name>` | ![Tarea](media/task.png "Tarea") |
| Nota | `Note modified by <Owner Name>` | ![Nota](media/note.png "Nota") |
| Publicación | `Post by <Owner Name>` | ![Publicación](media/post.png "Publicación") |

## <a name="customize-field-sections"></a>Personalizar secciones de campo

En la sección de la escala de tiempo, los usuarios ven una tarjeta para cada actividad (en función de las actividades habilitadas). Cada tarjeta muestra ciertos campos en el modo contraído y expandido. Por ejemplo, vea tarjeta de actividad **Correo electrónico** en modo contraído, modo de desplazamiento y modo expandido. 

**Modo contraído de tarjeta de correo electrónico**: De forma predeterminada, las tarjetas de actividad están en modo contraído.


   > [!div class=mx-imgBorder] 
   > ![Tarjeta de escala de tiempo en modo contraído](media/email.png "Tarjeta de escala de tiempo en modo contraído")

**Modo de desplazamiento de tarjeta de correo electrónico**: Cuando pasa el cursor puede ver algunos comandos que son específicos de cada uno de los tipos de tarjeta de actividad.

   > [!div class=mx-imgBorder] 
   > ![Tarjeta de escala de tiempo en modo contraído](media/email-hover.png "Tarjeta de escala de tiempo en modo contraído")

**Modo expandido de tarjeta de escala de tiempo**: Cuando selecciona la tarjeta, se expande con algunos comandos específicos de cada tipo de tarjeta de actividad.

   > [!div class=mx-imgBorder] 
   > ![Tarjeta de escala de tiempo en modo expandido](media/email-expanded.png "Tarjeta de escala de tiempo en modo expandido")

En la tarjeta, si desea mostrar los campos que son importantes para su negocio, puede personalizar los campos. Además, puede mover los campos de una sección a otra, por ejemplo, desde la sección **Encabezado** a la sección **Detalle**. Para obtener más información, consulte [Personalizar el formulario de tarjeta](#customize-the-card-form).

### <a name="customize-the-card-form"></a>Personalizar el formulario de tarjeta

Cualquier formulario de tarjeta tiene las siguientes secciones:

   | Anotación de sección | Nombre de sección | Mostrar columnas |
   |------------------------------|--------------------------------------|---------------------------------------|
   | A | Franja de colores | La sección Franja de colores nunca se muestra al usuario. |
   | B | Encabezado | Los campos 1 y 2 se muestran al usuario. |
   | C | Detalles | Los campos 3, 4 y 5 se muestran al usuario cuando los campos 3 y 4 se muestran en el modo contraído y el campo 5 se muestra en el modo expandido. |
   | E | Pie de página | La sección pie de página nunca se muestra al usuario. |

Por ejemplo, vea **Formulario de correo electrónico**.

**Pantalla de configuración de correo electrónico**

   > [!div class=mx-imgBorder] 
   > ![Configuración de tarjeta de correo electrónico](media/customize-field-email.png "Configuración de tarjeta de correo electrónico")

**Modo contraído de la tarjeta de correo electrónico**

Los campos **1** y **2** de la sección **Encabezado** y los campos **3** y **4** de la sección **Detalles** se muestran en el modo contraído.

   > [!div class=mx-imgBorder] 
   > ![Tarjeta de correo electrónico en modo contraído](media/email-card-collapsed.png "Tarjeta de correo electrónico en modo contraído")

**Modo de desplazamiento de tarjeta de correo electrónico**

Los campos **1** y **2** de la sección **Encabezado** y los campos **3** y **4** de la sección **Detalles** se muestran en el modo de desplazamiento.

   > [!div class=mx-imgBorder] 
   > ![Tarjeta de correo electrónico en modo contraído](media/email-card-hover.png "Tarjeta de correo electrónico en modo contraído")

**Modo expandido de la tarjeta de correo electrónico**

El campo **5** de la sección **Detalles** se muestra en el modo expandido.

   > [!div class=mx-imgBorder] 
   > ![Tarjeta de correo electrónico en modo expandido](media/email-card-expanded.png "Tarjeta de correo electrónico en modo expandido")

Para personalizar el formulario de tarjeta, siga estos pasos:

1.  Inicie sesión en el entorno de `https://<YourOrgURL>.dynamics.com/apps`.

2.  Abra una aplicación basada en modelo y en la barra de comandos seleccione **Configuración** ![Configuración](../model-driven-apps/media/powerapps-gear.png "Configuración") > **Configuración avanzada**.

3.  Vaya a **Personalizaciones** > **Personalización** > **Personalización del sistema**. La página del explorador de soluciones se abre en una nueva ventana del navegador.  

4.  Expanda **Entidades** en **Componentes** en el panel de la solución predeterminada.

5.  Seleccione una entidad y seleccione **Formularios**. Por ejemplo, seleccione la entidad **Correo electrónico**.

6.  Selecciona el registro **Formulario de tarjeta de correo electrónico** de la lista. El **Formulario de tarjeta de correo electrónico** se abre en una nueva ventana del navegador.

7.  Agregar, mover o eliminar los campos. Para más información, consulte [Agregar, configurar, mover o eliminar campos de un formulario](add-move-or-delete-fields-on-form.md).

   En este procedimiento, modificaremos **Tarjeta de correo electrónico**. 

   > [!div class=mx-imgBorder] 
   > ![Configuración de tarjeta de correo electrónico](media/customize-field-email1.png "Configuración de tarjeta de correo electrónico")

   En la sección **Encabezado**, el campo **Creado el** es reemplaza con **Prioridad**.

   Del mismo modo, en la sección **Detalles**, el campo **Prioridad** se elimina y el campo **Asunto** se mueve hacia arriba.

8.  Seleccione **Aceptar** y, a continuación, **Guardar**.

9.  Seleccione **Publicar** para publicar las personalizaciones.

Ahora, puede ver los cambios en el control **Escala de tiempo**. En el modo contraído, puede ver los cambios realizados en la tarjeta.

   > [!div class=mx-imgBorder] 
   > ![Configuración de tarjeta de correo electrónico](media/email2.png "Configuración de tarjeta de correo electrónico")

> [!Note]
> Si un campo no tiene ningún valor, en la tarjeta, el valor del campo permanece vacío. 

## <a name="enable-custom-activity-in-timeline"></a>Habilitar actividad personalizada en la escala de tiempo

Mientras crea una entidad personalizada, es posible que desee mostrar la entidad personalizada como una actividad para sus usuarios en la escala de tiempo. Para mostrar la entidad personalizada como una actividad, debe habilitar ciertas opciones durante la creación de una entidad personalizada.

> [!Note]
> Asegúrese de habilitar la entidad personalizada como actividad antes de crear la entidad. Después de crear la entidad personalizada, no puede habilitar la entidad como una actividad y mostrarla a sus usuarios en el control **Escala de tiempo**.

Para habilitar una actividad personalizada en la línea de tiempo, siga estos pasos.

[Paso 1: Crear una entidad](#step-1-create-an-entity)

[Paso 2: Agregar entidad a la aplicación basada en modelos](#step-2-add-entity-to-the-model-driven-app)

### <a name="step-1-create-an-entity"></a>Paso 1: Crear una entidad

Puede crear una entidad en [modo clásico](#classic-mode) o [Power Apps](#powerapps). 

#### <a name="classic-mode"></a>Modo clásico

1.  Inicie sesión en el entorno de `https://<YourOrgURL>.dynamics.com/apps`.

2.  Abra una aplicación basada en modelo y en la barra de comandos seleccione **Configuración** ![Configuración](../model-driven-apps/media/powerapps-gear.png) > **Configuración avanzada**.

3.  Vaya a **Personalizaciones** > **Personalización** > **Personalización del sistema**. La página del explorador de soluciones se abre en una nueva ventana del navegador.  

4.  Seleccione **Entidades** en **Componentes** en el panel de la solución predeterminada.

5.  Seleccione **Nueva** para crear una entidad. Se muestra una nueva ventana del navegador.

6. Introduzca los campos obligatorios como se describe en el tema [Crear una entidad](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/customize/create-entities). 

   > [!Note]
   > El tema [Crear una entidad](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/customize/create-entities) es incluso aplicable a las aplicaciones basadas en modelos de Dynamics 365.

7. Seleccione las áreas donde desee mostrar la entidad personalizada.

8. Desplácese hacia abajo hasta la sección **Comunicación y colaboración** y seleccione las opciones requeridas.

9. Desplácese hacia abajo hasta la sección **Servicios de datos** y seleccione la casilla **Permitir creación rápida**. Esta opción le permite abrir la entidad en un formulario de creación rápida.

10. Desplácese hasta la sección **Definición de entidad** y seleccione la casilla **Definir como entidad de actividad**. Esta opción habilita la entidad como una actividad. 

    > [!Note]
    > Solo durante la creación de la entidad, puede habilitar esta opción. Una vez que se crea la entidad, no puede actualizar esta casilla.

11. Asegúrese de que la casilla **Mostrar en los menús de actividades** también está seleccionada.

    > [!Note]
    > Esta opción garantiza que la actividad aparezca en menú de control **Escala de tiempo**.

    > [!div class=mx-imgBorder] 
    > ![Mostrar actividad](media/display-activity-classicmode.png "Mostrar actividad")

12. Seleccione **Guardar**.

13. Seleccione **Publicar** para publicar las personalizaciones.

#### <a name="powerapps"></a>PowerApps

Siga el tema [Crear una entidad personalizada](../common-data-service/data-platform-create-entity.md) para crear una entidad utilizando PowerApps.

Después del paso 3 en [Crear una entidad](../common-data-service/data-platform-create-entity.md#create-an-entity), antes de guardar y crear la entidad, asegúrese de realizar lo siguiente:

1. Expanda **Más valores** > **Tipo de entidad y titularidad**.

2. Selecciona la opción **Entidad de actividad** de la lista desplegable **Elegir tipo de entidad**.

3. Asegúrese de que la casilla **Mostrar en los menús de actividades** está seleccionada.

4. Expanda **Crear y actualizar configuraciones**.

5. Seleccione la casilla **Habilitar formularios de creación rápida**.

    > [!div class=mx-imgBorder] 
    > ![Mostrar actividad](media/display-activity-pa.png "Mostrar actividad")

6. Seleccione cualquier otra opción requerida y luego seleccione **Crear**.

### <a name="step-2-add-entity-to-the-model-driven-app"></a>Paso 2: Agregar entidad a la aplicación basada en modelos

Después de crear la entidad y habilitarla como actividad, debe agregar la entidad a la aplicación basada en modelos.

1. Inicie sesión en el entorno de `https://<YourOrgURL>.dynamics.com/apps`.

2. Seleccione los puntos suspensivos (**...**) en una ventana de la aplicación basado en modelos. Por ejemplo, ventana de la aplicación **Centro de servicio al cliente**.

3. Seleccione **ABRIR EN DISEÑADOR APLICACIONES**. El Diseñador de aplicaciones se abre en una nueva pestaña.

4. Busque la entidad personalizada que creó en **Vista de entidad** en el área del lienzo.

5. Seleccione **Formularios**. La opción se muestra en el panel de componentes.

6. Seleccione la casilla en el área **Formularios de creación rápida**. Esta opción utiliza el formulario de creación rápida cuando el usuario selecciona el botón **+** en el control **Escala de tiempo**.

    > [!div class=mx-imgBorder] 
    > ![Mostrar actividad](media/app-designer-activity.png "Mostrar actividad")

7. Seleccione **Guardar**.

8. Seleccione **Publish**.

## <a name="enable-custom-activities-in-timeline-for-mobile-client"></a>Habilitar actividades personalizadas en la línea de tiempo para el cliente móvil

Cuando tiene actividades personalizadas que desea mostrar a los usuarios que usan dispositivos móviles, debe habilitarlas. Siga estos pasos para habilitarlas.

### <a name="enable-for-mobile"></a>Habilitar para móvil 

1.  Inicie sesión en el entorno de `https://<YourOrgURL>.dynamics.com/apps`.

2. Abra una aplicación basada en modelo y en la barra de comandos seleccione **Configuración** ![Configuración](../model-driven-apps/media/powerapps-gear.png) > **Configuración avanzada**.

3.  Vaya a **Personalizaciones** > **Personalización** > **Personalización del sistema**. La página del explorador de soluciones se abre en una nueva ventana del navegador.  

4.  Expanda **Entidades** en **Componentes** en el panel de la solución predeterminada.

5.  Seleccione una entidad de la lista. Por ejemplo, Cuenta.

6.  Desplácese hacia abajo hasta la sección **Outlook y Mobile** y seleccione la casilla para las siguientes opciones:

    -   Habilitar para dispositivos móviles (según sus requisitos)
    -   Solo lectura en dispositivos móviles (según sus requisitos)

7.  Seleccione **Guardar**.

8.  Seleccione **Publicar** para publicar las personalizaciones.

### <a name="select-the-modules-to-display"></a>Seleccione los módulos que desea mostrar

Después de seleccionar las opciones **Habilitar para dispositivos móviles** y **Solo lectura en dispositivos móviles** (según su requisito) para una entidad, debe seleccionar el módulo para mostrar en la escala de tiempo. Seleccione **Mostrar todo** si quiere mostrar todos los módulos o seleccione **Mostrar lo seleccionado** si desea mostrar uno o más módulos según los requisitos de su empresa. Si elige **Mostrar lo seleccionado**, seleccione los módulos que desea mostrar.
Siga los pasos 1-8 descritos en la sección [Personalizar módulos](#customize-modules) y luego guarde y publique las personalizaciones.

   > [!div class=mx-imgBorder] 
   > ![Seleccione los módulos de escala de tiempo que desea mostrar](media/timeline-activity.png "Seleccione los módulos de escala de tiempo que desea mostrar")

## <a name="enable-or-disable-rich-text-editor-for-notes-in-timeline"></a>Habilitar deshabilitar el editor de texto enriquecido para notas en la escala de tiempo

El editor de texto enriquecido permite a los usuarios crear contenido completo y bien formateado para las notas con énfasis. El editor incluye características comunes de procesador de textos. Para obtener más información, consulte [Tomar notas](https://docs.microsoft.com/dynamics365/customer-service/customer-service-hub-user-guide-basics#take-a-note).

De forma predeterminada, la característica está habilitada. Si desea deshabilitarla y habilitarla más tarde para sus usuarios, siga los pasos:

1.  Inicie sesión en el entorno de `https://<YourOrgURL>.dynamics.com/apps`.

2. Abra una aplicación basada en modelos y luego, en la barra de comandos, seleccione **Configuración** ![Configuración](../model-driven-apps/media/powerapps-gear.png) > **Administración** > **Configuración del sistema**.

3. En el diálogo **Configuración del sistema**, en la pestaña **General**, desplácese hacia abajo y seleccione o anule la selección de la casilla para el campo **Use texto enriquecido para que sea más fácil dar formateo a las notas creadas en Escala de tiempo.** .

4. Seleccione **Aceptar**.

    > [!div class=mx-imgBorder] 
    > ![Habilitar editor de texto enriquecido](media/timeline-note-enable-rich-text-editor.png "Habilitar editor de texto enriquecido")

El editor de texto enriquecido está habilitado o deshabilitado para sus usuarios en función de la selección de la casilla de verificación. 

## <a name="see-also"></a>Vea también

[Preguntas frecuentes para control de escala de tiempo](faqs-timeline-control.md)

[Sección de escala de tiempo en la aplicación del Centro de servicios al cliente](https://docs.microsoft.com/dynamics365/customer-service/customer-service-hub-user-guide-basics#timeline)

[Agregar una cita, correo electrónico, llamada de teléfono, nota o actividad de tarea a la escala de tiempo](../../user/add-activities.md)
