---
title: Depurar actividades de flujo de trabajo (Common Data Service) | Microsoft Docs
description: Describe cómo depurar actividades de flujo de trabajo mediante la herramienta de registro de complementos.
ms.custom: ''
ms.date: 06/21/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="debug-workflow-activities"></a>Depurar actividades de flujo de trabajo

Puesto que las extensiones personalizadas del flujo de trabajo son ensamblados de .NET Framework puede depurarlas con métodos muy similares a cómo se depuran los complementos. 

## <a name="use-the-plug-in-registration-tool"></a>Uso de la herramienta de registro de complementos

La herramienta de registro de complementos (PRT) es una de las herramientas que se puede descargar de NuGet. Más información: [Herramientas de descarga de NuGet](../download-tools-nuget.md).

Una vez que ha descargado la PRT, haga clic en `PluginRegistration.exe` para ejecutarlo.

## <a name="install-profiler"></a>Instale el generador de perfiles

Desde la PRT puede instalar la solución de generador de perfiles haciendo clic en el botón **Instalar el generador de perfiles**.

![El botón de instalación del generador de perfiles en la herramienta de registro de complementos](../media/tutorial-debug-plug-in-install-profiler.md.png)

Esta solución agrega la capacidad de capturar el contexto que se pasa a la actividad de flujo de trabajo y permite una reproducción que puede usar para depurar la lógica del código localmente con Visual Studio.

Cuando el **generador de perfiles de complemento** está instalado para su instancia Common Data Service, lo verá en PRT en la parte inferior de la lista **Complementos registrados y actividades personalizadas del flujo de trabajo**.

![Generador de perfiles de complementos en la herramienta de registro de complementos](media/Plug-in-Profiler.png)

## <a name="profile-a-workflow-activity"></a>Generar un prefil de una actividad de flujo de trabajo

Para generar un perfil de una actividad de flujo de trabajo, haga clic con el botón secundario en **Generador de perfiles de complementos** y seleccione **Iniciar flujo de trabajo de generar perfiles**.

![Iniciar flujo de trabajo de generar perfiles](media/Start-profiling-workflow.png)

Se abrirá el diálogo **Configuración del generador de perfiles** que proporcionará las siguientes opciones:

![cuadro de diálogo de configuración del generador de perfiles](media/profiler-settings.png)

|Campo|Descripción|
|--|--|
|**Flujo de trabajo**|Seleccione la acción de flujo de trabajo o la acción personalizada que contiene la actividad de flujo de trabajo que desea depurar.|
|**Pasos**|Seleccione los pasos específicos dentro de esa acción de flujo de trabajo o personalizada que desea depurar.|
|**Especificar almacenamiento del perfil**|Se recomienda que elija **Persistir en entidad**.|
|**Establecer configuración del generador de perfiles**|Si está trabajando con un sistema donde el flujo de trabajo se ejecuta con frecuencia, puede reducir el impacto del rendimiento eligiendo limitar el número de perfiles que se capturan.|
|**Incluir configuración segura**|Esto proporciona la opción de evitar ver potencialmente datos confidenciales que se pueden pasarse como configuración segura.|

Haga clic en **Aceptar** para guardar la configuración.

> [!NOTE]
> En el momento de redactarse este texto puede ver el error siguiente:
> 
> ![Error al definir los valores del generador de perfiles de actividad de flujo de trabajo](media/error-setting-profiler-settings-workflow-activity.png)
> 
> Los detalles de este error incluirán el mensaje: `Automatic workflow cannot be published if no activation parameters have been specified.`
> 
> La configuración del generador de perfiles se guardó correctamente. El error ocurre porque el proceso de generación perfiles de una actividad personalizada de flujo de trabajo creará una copia del flujo de trabajo y deshabilitará el flujo de trabajo original y la copia. Será necesario configurar de nuevo la copia cuyo perfil se ha generado y activarla para capturar un perfil.  Consulte los siguientes pasos para obtener más información.

## <a name="capture-a-profile"></a>Capturar un perfil

Cuando un perfil para un flujo de trabajo que contiene una actividad personalizada de flujo de trabajo está configurado, una copia del flujo de trabajo original se crea y tendrá el texto `(Profiled)` anexado al nombre. El original y copia de los flujos de trabajo se desactivan.

> [!NOTE]
> A menos que esté trabajando en la solución del sistema **Predeterminado**, no puede ver el flujo de trabajo copiado porque se agrega a esa solución. Para ver el flujo de trabajo copiado en la solución en la que está trabajando, necesita hacer clic en **Agregar existente** y agregar esta copia a la solución.

Los flujos de trabajo desactivados deben tener un aspecto similar al siguiente:

![Flujo de trabajo copiado en el Explorador de soluciones](media/copied-workflow-solution-explorer.png)

Cuando se copia el flujo de trabajo, parte de la configuración se pierde. Si intenta activar el flujo de trabajo copiado, recibirá el siguiente error: `An automatic process cannot be activated if no activation parameters have been specified. Add activation parameters, and then activate. ...`

Esto significa que tiene que configurar de nuevo las propiedades **Iniciar cuando** del flujo de trabajo. En este caso, deseamos establecer el flujo de trabajo para que se inicie cuando el campo **Nombre de cuenta** cambie:

![Iniciar cuando el campo cambia de valor](media/start-when-field-changes.png)

Haga clic en el botón **Seleccionar** para elegir el campo **Nombre de cuenta**.

![Cuadro de diálogo de selección de campo Iniciar cuando el campo cambia de valor](media/start-when-field-change-field-select-dialog.png)

El flujo de trabajo copiado del perfil también se cambiará a un flujo de trabajo de segundo plano (asincrónico). Será más fácil comprobar un flujo de trabajo en tiempo real (forma sincrónica), por lo que en la barra de menús haga clic en **Convertir en un flujo de trabajo en tiempo real**.

Guarde el flujo de trabajo copiado del perfil y actívelo.

En una aplicación con conexión con la instancia de Common Data Service, o con los servicios web, actualice el valor **Nombre de cuenta** de una entidad de cuenta. Esto capturará una instancia del contexto pasada a la actividad personalizada de flujo de trabajo y la persistirá como un registro del perfil en el sistema.

> [!TIP]
> Si el flujo de trabajo es asincrónico, asegúrese de que finalice antes de avanzar al paso siguiente. Vaya a Configuración > Trabajos del sistema y compruebe que el flujo de trabajo se realizó correctamente.

## <a name="stop-profiling"></a>Detener el generar perfiles

Una vez que haya capturado el perfil necesitará depurarlo, debe detener el generar perfiles del complemento.  

Para detener el generar perfiles, anule el registro del flujo de trabajo mediante PRT.

![Detener el flujo de trabajo de generar perfiles](media/stop-profiling.png)

Esto eliminará la copia del flujo de trabajo que se creó.

> [!IMPORTANT]
> El flujo de trabajo que se copió seguirá estando desactivado. Deberá reactivarlo manualmente si desea que se aplique.

## <a name="debug-your-assembly"></a>Depurar el ensamblado.

1. En el PRT, haga clic en **Reproducir ejecución de complementos**.
1. En el **diálogo Reproducir ejecución de complementos**, en la pestaña **Configuración**, haga clic en el botón Descargar para seleccionar un **Perfil**.

    ![Diálogo Reproducir ejecución de complementos](media/replay-plugin-execution-dialog.png)

    > [!NOTE]
    > Las pestañas **Configuración no segura**, **Configuración segura**, Y **Configuración** no se usan para la depuración de la actividad de flujo de trabajo. Se usan solo para complementos.

1. En el diálogo **Seleccionar perfil de CRM**, elija el perfil más reciente que representa el que acaba de generar.

    ![Seleccione el perfil que acaba de generar](media/select-profile-from-crm-dialog.png)

    > [!NOTE]
    > Puede administrar perfiles capturados en la aplicación web **Dynamics 365 - custom** navegando a **Configuración** > **Extensiones** > **Perfiles de complementos**.

1. Haga clic en **Seleccionar** para cerrar el cuadro de diálogo.
1. En el campo **Ubicación de ensamblado**, haga clic en las elipses (**...**) para agregar la ubicación del ensamblado que contiene la actividad de flujo de trabajo que está depurando.
1. Abra el proyecto de actividad de flujo de trabajo en Visual Studio.
1. Agregue un punto de pausa a una línea en el método `Execute` de la actividad de su flujo de trabajo.

    ![Establezca un punto de interrupción](media/set-breakpoint-in-workflow-activity.png)

1. Del menú **Depurar**, seleccione **Asociar al proceso…**.
1. Busque en el proceso `PluginRegistration.exe`.

    > [!TIP]
    > El filtro de búsqueda le ayudará a encontrarlo más rápido. El identificador del proceso (PID) asignado al proceso será distinto para cada sesión. El PID se muestra en el diálogo **Reproducir ejecución de complementos** en **Seguimientos de complementos**.

    ![Adjuntar Visual Studio para procesar diálogo](media/visual-studio-attach-to-process-dialog.png)

1. Haga clic en **Adjuntar** para adjuntar su depurador Visual Studio a la aplicación de PRT que ejecutará la reproducción de proceso.
1. En el diálogo **Reproducir ejecución de complementos** de PRT, haga clic en el botón **Iniciar la ejecución**.

Debe ahora poder repasar el código y depurar la actividad de flujo de trabajo mediante Visual Studio.



### <a name="more-information"></a>Más información

[Depuración de complementos](../debug-plug-in.md)<br />
[Tutorial: Depurar un complemento](../tutorial-debug-plug-in.md)
