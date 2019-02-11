---
title: Integración de datos en Common Data Service for Apps
description: Integración de datos de varios orígenes en Common Data Service for Apps
author: sabinn-msft
ms.service: powerapps
ms.topic: how-to
ms.component: cds
ms.date: 1/31/2019
ms.author: sabinn
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: 8723021a59ca1ecbbdff41ddfa793684fe1ee970
ms.sourcegitcommit: 47a4218445e5715bc1f7bf7bd8735b2a42c33935
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2019
ms.locfileid: "55514039"
---
# <a name="integrate-data-into-common-data-service-for-apps"></a>Integración de datos en Common Data Service for Apps

<!--note from editor: the style guide says not to use "the" in front of Common Data Service for Apps, so I'm removing that.-->

El integrador de datos (para administradores) es un servicio de integración de punto a punto que se usa para integrar datos en Common Data Service for Apps. Admite la integración de datos de varios orígenes, por ejemplo, Dynamics 365 for Finance and Operations, Dynamics 365 for Sales y SalesForce (versión preliminar), SQL (versión preliminar), en Common Data Service for Apps. También admite la integración de datos en Dynamics 365 for Finance and Operations y Dynamics 365 for Sales. Este servicio ha estado disponible con carácter general desde julio de 2017.  

Comenzamos con aplicaciones propias; por ejemplo, Dynamics 365 for Finance and Operations y Dynamics 365 for Sales. Con la Ayuda de Power Query o conectores basados en M, ahora podemos admitir orígenes adicionales como SalesForce (versión preliminar) y SQL (versión preliminar), y esto se extenderá a más de 20 orígenes en un futuro próximo. 

> [!div class="mx-imgBorder"]
> ![Origen de datos al destino](media/data-integrator/DataIntegratorP2P-new.PNG "Data source to destination")

> [!TIP]
> Consulte el blog [Data Integrator Updates – New features with an intuitive user interface providing a fluent experience](https://powerapps.microsoft.com/blog/data-integrator-updates-new-features-with-an-intuitive-user-interface-providing-a-fluent-experience/) (Actualizaciones del integrador de datos: nuevas características con una interfaz de usuario intuitiva que proporciona una experiencia fluida).

## <a name="how-can-you-use-the-data-integrator-for-your-business"></a>¿Cómo puede usar el integrador de datos para su empresa?

El integrador de datos (para administradores) también admite escenarios de integración basados en procesos como Prospect to Cash (Cliente potencial a cliente) que proporcionan sincronización directa entre Dynamics 365 for Finance and Operations y Dynamics 365 for Sales. Las plantillas de Prospect to Cash (Cliente potencial a cliente) que están disponibles con la característica de integración de datos permiten el flujo de datos para cuentas, contactos, productos, presupuestos, pedidos y facturas de venta entre Finance and Operations y Sales. Mientras los datos fluyen entre Finance and Operations y Sales, puede realizar actividades de ventas y marketing en Sales, y controlar el cumplimiento de pedidos mediante la administración de inventario de Finance and Operations. 

> [!div class="mx-imgBorder"]
> ![Prospect to Cash](media/data-integrator/ProspectToCash631.png "Prospect to Cash")

La integración de Prospect to Cash (Cliente potencial a cliente) permite a los vendedores controlar y supervisar sus procesos de ventas con los puntos fuertes de Dynamics 365 for Sales, mientras que todos los aspectos de cumplimiento y facturación se realizan mediante las completas funciones de Finance and Operations. Con la integración de Prospect to Cash (Cliente potencial a cliente) de Microsoft Dynamics 365, obtendrá el potencial combinado de ambos sistemas. 

Vea el vídeo [Prospect to cash integration](https://www.youtube.com/watch?v=AVV9x5x-XCg) (Integración de cliente potencial a cliente)

Para obtener más información sobre la integración de Prospect to Cash, vea la documentación sobre la [Solución Prospect to Cash](https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/sales-marketing/prospect-to-cash).

También se admite la [integración de Field Service](https://docs.microsoft.com/dynamics365/unified-operations/supply-chain/sales-marketing/field-service-work-order) y la [integración de PSA (Project Service Automation)](https://docs.microsoft.com/dynamics365/unified-operations/financials/project-management/psa-integration?toc=/fin-and-ops/toc.json) en Dynamics 365 for Finance and Operations.

## <a name="data-integrator-platform"></a>Plataforma de integración de datos

El integrador de datos (para administradores) consta de la plataforma de integración de datos, plantillas integradas proporcionadas por nuestros equipos de aplicación (por ejemplo, Dynamics 365 for Finance and Operations y Dynamics 365 for Sales) y plantillas personalizadas creadas por nuestros clientes y asociados. Hemos creado una plataforma independiente de la aplicación que se puede escalar entre diversos orígenes. En el núcleo, puede crear conexiones (a puntos de conexión de integración), elegir una de las plantillas personalizables con asignaciones predefinidas (que puede personalizar aún más) y crear y ejecutar el proyecto de integración de datos.  

Las plantillas de integración actúan como un plano con entidades predefinidas y asignaciones de campos para permitir el flujo de datos desde el origen al destino. También proporciona la capacidad de transformar los datos antes de importarlos. En muchos casos, el esquema entre las aplicaciones de origen y destino puede ser muy diferente, y una plantilla con entidades predefinidas y asignaciones de campos actúa como un punto de partida excelente para un proyecto de integración.  

> [!div class="mx-imgBorder"]
> ![Plataforma de integración de datos](media/data-integrator/DIPlatform.PNG "Data Integration platform")

## <a name="how-to-set-up-a-data-integration-project"></a>Cómo configurar un proyecto de integración de datos

Hay tres pasos principales:

1. Crear una conexión (proporcionar credenciales para los orígenes de datos).

2. Crear un conjunto de conexiones (identifique los entornos para las conexiones que creó en el paso anterior).

3. Crear un proyecto de integración de datos mediante una plantilla (cree o use asignaciones predefinidas para una o más entidades).

Después de crear un proyecto de integración, tendrá la opción de ejecutarlo manualmente y también de configurar una actualización basada en una programación para el futuro. En el resto de este artículo se amplían estos tres pasos.

### <a name="how-to-create-a-connection"></a>Cómo crear una conexión

Antes de poder crear un proyecto de integración de datos, debe proporcionar una conexión para cada sistema con el que pretenda trabajar en el portal de Microsoft PowerApps. Considere estas conexiones como los puntos de integración.

**Para crear una conexión**

1. Vaya a [PowerApps](https://web.powerapps.com).

2. En Datos, haga clic en **Conexiones** y después en **Nueva conexión**.

3. Puede seleccionar una conexión de la lista de conexiones o buscar la suya.

    > [!div class="mx-imgBorder"] 
    > ![Creación de la conexión](media/data-integrator/CreateConnection780.png "Create connection")

4. Una vez que seleccione la conexión, haga clic en **Crear**. Después, se le pedirán las credenciales.

5. Después de proporcionar la credenciales, la conexión aparecerá en la lista de conexiones.

    > [!div class="mx-imgBorder"] 
    > ![Lista de conexiones](media/data-integrator/CreateConnection1780.png "Connection list")

> [!NOTE]
> Asegúrese de que la cuenta que especifique para cada conexión tenga acceso a las entidades para las aplicaciones correspondientes. Además, la cuenta para cada conexión puede estar en un inquilino diferente. 

### <a name="how-to-create-a-connection-set"></a>Cómo crear un conjunto de conexiones

Los conjuntos de conexiones son una colección de dos conexiones, los entornos para las conexiones, información de asignación de la organización y las claves de integración que se pueden reutilizar entre los proyectos. Puede empezar a usar un conjunto de conexiones para el desarrollo y después cambiar a otro para producción. Una fragmento de información clave que se almacena con un conjunto de conexiones son las asignaciones de unidades organizativas; por ejemplo, las asignaciones entre la entidad jurídica (o de empresa) de Finance and Operations y las unidades organizativas o de negocio de Dynamics 365 for Sales. Puede almacenar varias asignaciones de la organización en un conjunto de conexiones.

**Para crear un conjunto de conexiones**

1. Vaya al [Centro de administración de PowerApps](https://admin.powerapps.com).

2. Haga clic en la pestaña **Integración de datos** en el panel de navegación de la izquierda.

3. Haga clic en la pestaña **Conjuntos de conexiones** y en **Nuevo conjunto de conexiones**.

4. Proporcione un nombre para el conjunto de conexiones.
  
    > [!div class="mx-imgBorder"] 
    > ![Crear conjunto de conexiones](media/data-integrator/CreateConnectionSet1780.png "Create connection set")
  
5. Elija las conexiones que creó anteriormente y seleccione el entorno adecuado.

6. Repita los pasos eligiendo la próxima conexión (piense en estos elementos como el origen y el destino sin un orden específico).

7. Especifique la organización para la asignación de unidad de negocio (si va a integrar entre los sistemas de Finance and Operations y Sales).
  
    > [!NOTE]
    > Puede especificar varias asignaciones para cada conjunto de conexiones.
  
8. Una vez completados todos los campos, haga clic en **Crear**.

9. Verá el conjunto de conexiones que acaba de crear en la página de la lista Conjuntos de conexiones.
    
    > [!div class="mx-imgBorder"] 
    > ![Lista de conjuntos de conexiones](media/data-integrator/CreateConnectionSet2780.png "Connection set list")

El conjunto de conexiones está listo para usarse en diversos proyectos de integración.

### <a name="how-to-create-a-data-integration-project"></a>Cómo crear un proyecto de integración de datos

Los proyectos permiten el flujo de datos entre sistemas. Un proyecto contiene asignaciones para una o más entidades. Las asignaciones indican qué campos se asignan a otros campos.

<a name="CreateProject">

**Para crear un proyecto de integración de datos**

1. Vaya al [Centro de administración de PowerApps](https://admin.powerapps.com).

2. Haga clic en la pestaña **Integración de datos** del panel de navegación de la izquierda.

3. En la pestaña **Proyectos**, haga clic en **Nuevo proyecto** en la esquina superior derecha.

    > [!div class="mx-imgBorder"] 
    > ![Creación de un proyecto](media/data-integrator/CreateNewProject780.png "Create project")

4. Proporcione un nombre para el proyecto de integración.

5. Seleccione una de las plantillas disponibles (o [cree una propia](#how-to-customize-or-create-your-own-template)). En este caso, se traslada la entidad Productos desde Finance and Operations a Sales.

    > [!div class="mx-imgBorder"] 
    > ![Selección de la plantilla para crear un proyecto](media/data-integrator/CreateNewProjectSelectTemplate780.png "Select template to create new project")

6. Haga clic en **Siguiente** y elija un conjunto de conexiones que haya creado anteriormente (o [cree uno](#how-to-create-a-connection-set)).

7. Para asegurarse de que ha elegido el correcto, confirme los nombres de la conexión y el entorno.

    > [!div class="mx-imgBorder"] 
    > ![Creación de un conjunto de conexiones](media/data-integrator/CreateNewProjectSelectConnectionSet780.png "Create a new connection set")

8. Haga clic en **Siguiente** y, después, elija la entidad jurídica para las asignaciones de unidad de negocio.

    > [!div class="mx-imgBorder"] 
    > ![Creación de una asignación de entidad jurídica](media/data-integrator/CreateNewProjectLegalEntityMapping780.png "Create new legal entity mapping")

9. Revise y acepte el aviso de privacidad y consentimiento en la pantalla siguiente.

10. Continúe para crear el proyecto y, después, ejecútelo.

    > [!div class="mx-imgBorder"] 
    > ![Ejecución del proyecto](media/data-integrator/RunProject780.png "Run project")

    En esta pantalla verá varias pestañas, **Programación** e **Historial de ejecuciones**, junto con varios botones: **Agregar tarea**, **Actualizar entidades** y **Consulta avanzada**, que se describirán más adelante en este artículo.

### <a name="execution-history"></a>Historial de ejecuciones

En el Historial de ejecuciones se muestra el historial de las ejecuciones de todos los proyecto con el nombre del proyecto, la marca de tiempo de cuándo se ejecutó el proyecto y el estado de ejecución, junto con el número de operaciones upsert y errores.

-   Ejemplo de historial de ejecuciones de proyectos.

    > [!div class="mx-imgBorder"] 
    > ![Historial de ejecuciones de proyectos](media/data-integrator/ExecutionHistorySuccessFailures4780.png "Project execution history")

-   Ejemplo de ejecución correcta, en el que se muestra el estado como finalizado con \# de operación upsert. (Actualización o inserción es una lógica para actualizar el registro si ya existe, o bien para insertar uno nuevo).

    > [!div class="mx-imgBorder"] 
    > ![Ejecución correcta](media/data-integrator/ExecutionHistorySuccess2780.png "Execution success")

-   Para los errores de ejecución, puede explorar en profundidad para ver la causa principal.

    Este es un ejemplo de un error con errores de validación del proyecto. En este caso, el error de validación del proyecto se debe a que faltan campos de origen en las asignaciones de entidad.

    > [!div class="mx-imgBorder"] 
    > ![Error del historial de ejecuciones](media/data-integrator/ExecutionHistoryFailures3780.png "Execution history failure")

-   Si la ejecución del proyecto está en estado de "ERROR", volverá a intentar la ejecución en la siguiente ejecución programada.

-   Si la ejecución del proyecto está en el estado de "ADVERTENCIA", tendrá que solucionar los problemas en el origen. Volverá a intentar la ejecución en la siguiente ejecución programada.

    En cualquier caso, también podría optar por "volver a ejecutar la ejecución" manualmente.

> [!NOTE]
> Cada vez que ejecute un proyecto, de forma programada o manual, genera un registro detallado que muestra el nombre del proyecto, una marca de tiempo con la última actualización y el estado. Puede ver esto en el historial de ejecución de cada proyecto. El historial de ejecución del proyecto se mantiene durante 45 días; después, se purga automáticamente.


### <a name="how-to-set-up-a-schedule-based-refresh"></a>Cómo configurar una actualización basada en una programación

En la actualidad se admiten dos tipos de ejecuciones y operaciones de escritura:

-   Operaciones de escritura manuales (ejecutar y actualizar el proyecto manualmente)

-   Operaciones de escritura basadas en una programación (actualización automática)

Después de crear un proyecto de integración, tendrá la opción de ejecutarlo manualmente o de configurar operaciones de escritura basadas en una programación, lo que permite configurar la actualización automática para los proyectos.

**Para configurar operaciones de escritura basadas en una programación**

1. Vaya al [Centro de administración de PowerApps](https://admin.powerapps.com).

2. Puede programar los proyectos de dos maneras diferentes.<br>

    Seleccione el proyecto y haga clic en la pestaña **Programación**, o bien haga clic en el botón de puntos suspensivos situado junto al nombre del proyecto para iniciar el programador desde la página de la lista de proyectos.

    > [!div class="mx-imgBorder"] 
    > ![Operaciones de escritura basadas en una programación](media/data-integrator/Schedulebasedwrites780.png "Schedule-based writes")

3. Seleccione **Repetir cada** y cuando haya completado todos los campos, haga clic en **Guardar programación**.

    > [!div class="mx-imgBorder"] 
    > ![Operaciones de escritura basadas en una programación](media/data-integrator/Schedulebasedwrites1780.png "Schedule-based writes")

Puede establecer una frecuencia muy repetida de un minuto o hacer que se repita un número determinado de horas, días, semanas o meses. Tenga en cuenta que la próxima actualización no se iniciará hasta que la tarea del proyecto anterior termine de ejecutarse.

Tenga en cuenta también que, en Notificaciones, puede elegir notificaciones de alerta basadas en correo electrónico, lo que le alertaría sobre las ejecuciones de trabajos que se han completado con advertencias o que no se han podido completar debido a errores. Puede proporcionar varios destinatarios, incluidos grupos separados por comas.

> [!div class="mx-imgBorder"] 
> ![Notificación por correo electrónico](media/data-integrator/EmailNotification780.png "Email notification")

> [!NOTE]
> - Actualmente se admite la programación de 50 proyectos de integración en cualquier momento por cada inquilino adquirido. No obstante, puede crear varios proyectos y ejecutarlos de forma interactiva.
Para los inquilinos de prueba, tenemos una limitación adicional: solo se ejecutarán para las primeras 50 ejecuciones de un proyecto programado.
> - Aunque se admiten proyectos de programación que se vayan a ejecutar cada minuto, tenga en cuenta que esto puede suponer un gran esfuerzo para las aplicaciones y, a su vez, afectar al rendimiento general. Recomendamos a los usuarios probar las ejecuciones de proyecto en condiciones de carga reales y optimizar el rendimiento con actualizaciones menos frecuentes.
En entornos de producción, se recomienda no ejecutar más de 5 proyectos por minuto por inquilino.
> - Cada vez que ejecute un proyecto, de forma programada o manual, genera un registro detallado que muestra el nombre del proyecto, una marca de tiempo con la última actualización y el estado. Puede ver esto en el historial de ejecución de cada proyecto. El historial de ejecución del proyecto se mantiene durante 45 días; después, se purga automáticamente.

## <a name="customizing-projects-templates-and-mappings"></a>Personalización de proyectos, plantillas y asignaciones 

Una plantilla se usa para crear un proyecto de integración de datos. Una plantilla facilita el movimiento de datos lo que, a su vez, ayuda a los usuarios empresariales o administradores a agilizar la integración de los datos desde los orígenes al destino y reduce el costo y la carga generales. Los usuarios empresariales o los administradores pueden empezar con una plantilla integrada publicada por Microsoft o su asociado, y después personalizarla aún más antes de crear un proyecto. Luego, pueden guardar el proyecto como una plantilla y compartirla con la organización o crear un proyecto. 

Una plantilla proporciona el origen, el destino y la dirección del flujo de datos. Recuérdelo cuando personalice o cree su propia plantilla.  

Puede personalizar los proyectos y las plantillas de las maneras siguientes:

-   Personalizar asignaciones de campos.

-   Personalizar una plantilla mediante la adición de la entidad que elija.

### <a name="how-to-customize-field-mappings"></a>Cómo personalizar las asignaciones de campos

**Para crear un conjunto de conexiones**

1. Vaya al [Centro de administración de PowerApps](https://admin.powerapps.com).

2. Seleccione el proyecto para el que quiera personalizar las asignaciones de campos y, después, haga clic en la flecha situada entre los campos de origen y destino.

    > [!div class="mx-imgBorder"] 
    > ![Asignación de campos](media/data-integrator/FieldMapping780.png "Field mapping")

3. Esto le llevará a la pantalla de asignación, donde puede agregar una asignación nueva si hace clic en **Agregar asignación** en la esquina superior derecha o selecciona **Customize existing mappings** (Personalizar las asignaciones existentes) en la lista desplegable.

    > [!div class="mx-imgBorder"] 
    > ![Personalización de la asignación de campos](media/data-integrator/FieldMappingCustomize780.png "Field mapping customize")

4. Una vez que haya personalizado las asignaciones de campos, haga clic en **Guardar**.

### <a name="how-to-create-your-own-template"></a>Creación de una plantilla propia 

**Creación de una plantilla propia mediante la modificación de las plantillas existentes**

1. Vaya al [Centro de administración de PowerApps](https://admin.powerapps.com).

2. Identifique el origen, el destino y la dirección del flujo de la plantilla nueva.

3. Para crear un proyecto, elija una plantilla existente que coincida con la elección del origen, el destino y la dirección de flujo.

<!--note from editor: Didn't we create the project in step 3? Step 4 tells us to create the project.-->

4. Cree el proyecto después de elegir la conexión adecuada.

5. Antes de guardar o ejecutar el proyecto, en la esquina superior derecha, haga clic en **Agregar tarea**.

    > [!div class="mx-imgBorder"] 
    > ![Personalización de la plantilla](media/data-integrator/CustomizeTemplate780.png "Customize template")

    Esto abrirá el cuadro de diálogo **Agregar tarea**.

6. Proporcione un nombre de tarea descriptivo y agregue las entidades de origen y destino que prefiera.

    > [!div class="mx-imgBorder"] 
    > ![Agregar tarea para personalizar la plantilla](media/data-integrator/CustomizeTemplateAddtask75.png "Customize template add task")

7. En la lista desplegable se muestran todas las entidades de origen y destino.

    > [!div class="mx-imgBorder"] 
    > ![Agregar tarea para personalizar la plantilla](media/data-integrator/CustomizeTemplateAddtask175.png "Customize template add task")

    En este caso, se ha creado una tarea para sincronizar la entidad Usuario de SalesForce con la entidad Usuarios de Common Data Service for Apps.

    > [!div class="mx-imgBorder"] 
    > ![Agregar tarea para personalizar la plantilla](media/data-integrator/CustomizeTemplateAddtask275.png "Customize template add task")

8. Una vez creada la tarea, verá que la tarea nueva aparece en la lista y puede eliminar la tarea original.

    > [!div class="mx-imgBorder"] 
    > ![Agregar tarea para personalizar la plantilla](media/data-integrator/CustomizeTemplateAddtask3780.png "Customize template add task")

9. Acaba de crear una plantilla, en este caso una plantilla para extraer datos de la entidad Usuario de SalesForce a Common Data Service. Haga clic en **Guardar** para guardar la personalización.

10. Siga los pasos para personalizar las asignaciones de campos para esta plantilla nueva. Puede ejecutar este proyecto o guardarlo como una plantilla desde la **Lista de proyectos**.

    > [!div class="mx-imgBorder"] 
    > ![Personalizar plantilla Guardar como plantilla](media/data-integrator/CustomizeTemplateSaveAsTemplate780.png "Customize template save as template")

11. Proporcione un nombre y una descripción, y compártalo con otros usuarios de la organización.

    > [!div class="mx-imgBorder"] 
    > ![Personalizar plantilla Guardar como plantilla](media/data-integrator/CustomizeTemplateSaveAsTemplate175.png "Customize template save as template")

**Creación de una plantilla propia a partir de plantillas en blanco**

1. Vaya al [Centro de administración de PowerApps](https://admin.powerapps.com).
2. Cree un proyecto de integración de datos. Haga clic en la pestaña **Integración de datos** del panel de navegación de la izquierda.
3. Seleccione **Nuevo proyecto** y proporcione un nombre al proyecto. Por ejemplo, "proyecto Demo_crearPlantillaPropia".
4. En la página de lista **Seleccionar una plantilla**, elija una plantilla genérica en blanco. 
   En este ejemplo, elija la plantilla **Sales to Fin and Ops** (De Sales a Finance y Operations), ya que deseamos mover datos de Dynamics 365 for Finance and Operations a Dynamics 365 for Sales.
    
    > [!div class="mx-imgBorder"] 
    > ![](media/create-data-integration-project.png "Creación de un proyecto de integración de datos")

4. Siga los pasos del 6 al 9 de <a href="#CreateProject">aquí</a> para terminar de crear un proyecto de integración de datos. Seleccione **Guardar**.

5. Verá la página de tareas que está vacía, ya que es una plantilla en blanco sin tareas. Seleccione **Agregar tarea** para seleccionar una entidad de la lista desplegable y agregue una nueva tarea.
   En este caso, con fines de demostración, crearemos una tarea **Activities Sales to Fin and Ops** (De Activities Sales a Finance y Operations) seleccionando la entidad **Actividades** para Dynamics 365 for Finance and Operations y Dynamics 365 for Sales. Seleccione **Crear**.

    > [!div class="mx-imgBorder"] 
    > ![](media/activities-sales-fin-opps-task.png "Tarea ActivitiesSales to Fin and Ops (De Activities Sales a Finance y Operations)")

6. Verá que se ha agregado una nueva tarea **Activities Sales to Fin and Ops** (De Activities Sales a Finance and Operations). Seleccione **Guardar** para guardar los cambios.

    > [!div class="mx-imgBorder"] 
    > ![](media/new-task-added.png "Nueva tarea agregada")

7. Se crea el proyecto. Seleccione **Guardar como plantilla** en la página de lista **Proyectos**.

    > [!div class="mx-imgBorder"] 
    > ![](media/save-as-template.png "Guardar como plantilla")

8. Proporcione un nombre y una descripción y, a continuación, seleccione **Guardar**. Además, seleccione **Compartir con todos los usuarios de la organización** para compartir esta plantilla.

    > [!div class="mx-imgBorder"] 
    > ![](media/save-describe-share.png "Guardar proyecto como plantilla")

Verá la plantilla recién creada en la página de lista **Plantillas**.

> [!div class="mx-imgBorder"] 
> ![](media/newly-created-template.png "Plantilla recién creada")

Además, después de crear un proyecto de integración, cuando se elige **seleccionar una plantilla**, verá la plantilla recién creada como parte de la lista **Seleccionar una plantilla**.

> [!div class="mx-imgBorder"] 
> ![](media/new-data-integration-project.png "Nuevo proyecto de integración de datos")


## <a name="advanced-data-transformation-and-filtering"></a>Transformación de datos avanzada y filtrado 

Con la compatibilidad de Power Query, ahora proporcionamos filtrado avanzado y transformación de datos de los datos de origen. Power Query permite a los usuarios cambiar la forma de los datos para ajustarlos a sus necesidades, con una experiencia del usuario atractiva, fácil de usar y sin código. Puede activar esta opción en cada proyecto. 

### <a name="how-to-enable-advanced-query-and-filtering"></a>Cómo habilitar la consulta avanzada y el filtrado

**Para configurar el filtrado avanzado y la transformación de datos**

1. Vaya al [Centro de administración de PowerApps](https://admin.powerapps.com).

2. Seleccione el proyecto donde quiera habilitar las consultas avanzadas y, después, haga clic en **Consulta avanzada**.

    > [!div class="mx-imgBorder"] 
    > ![Selección de Consulta avanzada](media/data-integrator/EnablePQ1780.png "Select Advanced Query")

3. Obtendrá una advertencia en la que se indica que habilitar la consulta avanzada es una operación unidireccional y no se puede deshacer. Haga clic en **Aceptar** para continuar y, después, haga clic en la flecha de asignación del origen y el destino.

    > [!div class="mx-imgBorder"] 
    > ![Advertencia](media/data-integrator/EnablePQ275.png "Warning")

4. Ahora se le presentará la página de asignación de entidades que ya conoce con un vínculo para iniciar Consulta avanzada y filtrado.

    > [!div class="mx-imgBorder"] 
    > ![Consulta avanzada y filtrado](media/data-integrator/EnablePQ3780.png "Advanced Query and Filtering")

5. Haga clic en **para vincular** para abrir la interfaz de usuario de Consulta avanzada y filtrado, que le ofrece datos de los campos de origen en columnas de estilo de Microsoft Excel.

    > [!div class="mx-imgBorder"] 
    > ![Consulta avanzada y filtrado](media/data-integrator/EnablePQ4780.png "Advanced Query and Filtering")

6. En el menú superior, tiene varias opciones para transformar los datos como **Agregar columna condicional**, **Duplicar columna** y **Extraer**.

    > [!div class="mx-imgBorder"] 
    > ![Agregar columna](media/data-integrator/EnablePQAddColumn75.png "Add column")

7. También puede hacer clic con el botón derecho en cualquier columna para ver más opciones, como **Quitar columnas**, **Quitar duplicados** y **Dividir columna**.

    > [!div class="mx-imgBorder"] 
    > ![Clic con el botón derecho en la columna](media/data-integrator/EnablePQAddColumn180.png "Right-click column")

8. También puede filtrar si hace clic en cada columna y usa filtros similares a los de Excel.

    > [!div class="mx-imgBorder"] 
    > ![Habilitar el filtrado](media/data-integrator/EnablePQFiltering80.png "Enable filtering")

<!--note from editor: I don't see an "otherwise" in the screenshot. I see "else".-->

9. Se pueden conseguir transformaciones de valor predeterminado mediante la columna condicional. Para ello, en la lista desplegable **Agregar columna**, seleccione **Agregar columna condicional** y escriba el nombre de la nueva columna. Rellene **Entonces** y **En caso contrario** con lo que deba ser el valor predeterminado, y use cualquier campo y valor para **Si** y **es igual a**.

    > [!div class="mx-imgBorder"] 
    > ![Agregar columna condicional](media/data-integrator/EnablePQDefaultValueTransforms2780.png "Add conditional column")

10. Observe la cláusula **each** en el editor *fx*, en la parte superior.

    > [!div class="mx-imgBorder"] 
    > ![Editor FX](media/data-integrator/EnablePQDefaultValueTransforms2780.png "fx editor")

11. Corrija la cláusula **each** en el editor *fx* y haga clic en **Aceptar**.

    > [!div class="mx-imgBorder"] 
    > ![Corrección de la cláusula each](media/data-integrator/EnablePQDefaultValueTransforms5780.png "Fix the each clause")

<!--note from editor: The sentence that starts with "Additionally" is confusing - not sure where the "same steps" fit in.-->

12. Cada vez que realiza un cambio, se aplica un paso. Puede ver los pasos aplicados en el panel de la derecha (desplácese hacia la parte inferior para ver el último paso). Puede deshacer un paso en caso de que lo tenga que modificar. Además, puede ir al editor avanzado si hace clic con en el botón derecho en **QrySourceData** en el panel de la izquierda, en la parte superior para ver el lenguaje M que se ejecuta en segundo plano, con los mismos pasos.

    > [!div class="mx-imgBorder"] 
    > ![Editor avanzado](media/data-integrator/EnablePQDefaultValueTransforms4780.png "Advanced editor")

13. Haga clic en **Aceptar** para cerrar la interfaz de Consulta avanzada y filtrado y, después, en la página de tareas de asignación, seleccione la columna recién creada como origen para crear la asignación correspondiente.

    > [!div class="mx-imgBorder"] 
    > ![Selección de la nueva columna](media/data-integrator/EnablePQDefaultValueTransforms6780.png "Pick new column")

Para obtener más información sobre Power Query, vea la [documentación de Power Query](https://docs.microsoft.com/power-query/).
