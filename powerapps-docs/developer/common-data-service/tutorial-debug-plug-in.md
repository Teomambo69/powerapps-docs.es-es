---
title: 'Tutorial: Depurar un complemento (Common Data Service) | Microsoft Docs'
description: 'Este tutorial es el segundo de una serie que le muestra cómo trabajar con los complementos. '
ms.custom: ''
ms.date: 1/28/2019
ms.reviewer: pehecke
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
# <a name="tutorial-debug-a-plug-in"></a>Tutorial: Depurar un complemento

Este tutorial es el segundo de una serie que le muestra cómo trabajar con los complementos. 

- [Tutorial: Escribir y registrar un complemento](tutorial-write-plug-in.md)
- Tutorial: Depurar un complemento (este tutorial)
- [Tutorial: Actualizar un complemento](tutorial-update-plug-in.md)

Para una explicación detallada de los conceptos relacionados y la información técnica, consulte:

- [Use complementos para ampliar los procesos de negocio](plug-ins.md)
- [Escribir un complemento](write-plug-in.md)
- [Registrar un complemento](register-plug-in.md)
- [Depuración de complementos](debug-plug-in.md)


## <a name="goal"></a>Objetivo

Puesto que el complemento se ejecuta en un servidor remoto, no puede adjuntar un depurador al proceso. El generador de perfiles de complementos captura un perfil de un complemento que se ejecuta y permite reproducir la ejecución del complemento utilizando Visual Studio localmente.



## <a name="prerequisites"></a>Requisitos previos

- Se aplican todos los requisitos previos para [Tutorial: Escribir y registrar un complemento](tutorial-write-plug-in.md). Vea [Requisitos previos:](tutorial-write-plug-in.md#prerequisites).
- Si no ha completado el tutorial anterior, puede usar los pasos generales siguientes con otro complemento registrado.

## <a name="install-plug-in-profiler"></a>Instalar generador de perfiles de complementos

1. Si la herramienta de registro de complementos no está instalada y abierta aún, siga los pasos en [Tutorial: Escribir y registrar un complemento](tutorial-write-plug-in.md) para abrirla. Complete la sección [Conectar con la herramienta de registro de complementos](tutorial-write-plug-in.md#connect-using-the-plug-in-registration-tool).
1. En la herramienta de registro de complementos, haga clic en **Instalar generador de perfiles**.

    ![Instale el generador de perfiles](media/tutorial-debug-plug-in-install-profiler.md.png)

1. Esto instalará una nueva solución administrada con el nombre Generador de perfiles de complementos en su entorno de Common Data Service. Esto llevará un minuto o dos para completar.

## <a name="start-profiling"></a>Iniciar generación de perfiles

1. En la herramienta de registro de complementos, seleccione el paso **(Step) BasicPlugin.FollowupPlugin: Creación de cuenta** que registró antes y haga clic en **Iniciar generación de perfiles**.

    ![Iniciar generación de perfiles](media/tutorial-debug-plug-in-start-profiling.png)

1. En el diálogo **Configuración de generador de perfiles** acepte la configuración predeterminada y haga clic en **Aceptar** para cerrar el cuadro diálogo.

    ![foo](media/tutorial-debug-plug-in-profiler-settings.png)


Formar obtener más información acerca cómo ejecutar el generador de perfiles, consulte [Ejecute el generador de perfiles de complementos desde una ventana del símbolo del sistema](#run-profiler-standalone).

## <a name="capture-a-profile"></a>Capturar un perfil

1. En la aplicación basada en modelos, cree una nueva cuenta para desencadenar el complemento. Esto capturará una instancia del complemento que se ejecuta y lo mantendrá como registro del perfil en el sistema.
1. En la herramienta de registro de complementos, haga clic en **Depurar**.

    ![Haga clic en Depurar](media/tutorial-debug-plug-in-capture-profile-debug.png)

1. En el diálogo **Reproducir ejecución de complementos** , en la pestaña **Configuración** , haga clic en el icono ![Comando Seleccionar perfil](media/tutorial-debug-plug-in-select-profile-command.png) para abrir el diálogo **Seleccionar perfil de CRM**.
1. En el diálogo **Seleccionar perfil de CRM**, seleccione el perfil donde **Nombre de tipo** es igual a **BasicPlugin.FollowupPlugin** y representa el perfil capturado cuando desencadenó por última vez el complemento.

    ![Diálogo Seleccionar perfil de CRM](media/tutorial-debug-plug-in-select-profile-dialog.png)

## <a name="debug-your-plug-in"></a>Depure el complemento.

1. En el diálogo **Reproducir ejecución de complementos** , en la pestaña **Configuración** , en la sección **Especificar ensamblado** , haga clic en el botón de puntos suspensivos (**…**) y elija la ubicación de `BasicPlugin.dll`.

    ![Reproducir ejecución de complementos](media/tutorial-debug-plug-in-replay-plug-in-execution.png)

1. En el proyecto de Visual Studio, establezca un punto de interrupción en la clase de complemento.

    ![Establezca un punto de interrupción](media/tutorial-debug-plug-in-set-break-point.png)

1. En el proyecto de Visual Studio, seleccione **Depurar** > **Asociar al proceso…**.

    ![Comando Asociar al proceso](media/tutorial-debug-plug-in-attach-to-process.png)

1. Seleccione el proceso **PluginRegistration.exe** y haga clic en **Asociar**.

    ![Diálogo Asociar al proceso](media/tutorial-debug-plug-in-attach-to-process-dialog.png)

    > [!NOTE]
    > Debe ver que la herramienta de registro de complementos ahora está ejecutando en modo de depuración.

1. En el diálogo **Reproducir ejecución de complementos**, haga clic en el botón **Iniciar la ejecución**.

    ![Iniciar ejecución](media/tutorial-debug-plug-in-replay-plug-in-execution-debug.png)

1. En el proyecto de Visual Studio, debe ver que el código está en pausa en el punto de interrupción establecido anteriormente. 

    ![Pulsa del punto de interrupción](media/tutorial-debug-plug-in-breakpoint-hit.png)

1. Ahora puede recorrer el código a depurar.


## <a name="repeat"></a>Repetir

Para repetir, en el proyecto de Visual Studio seleccione **Depurar** > **Volver a asociar** para procesar y en el diálogo **Reproducir ejecución de complementos** haga clic en **Iniciar ejecución** de nuevo.

## <a name="stop-profiling"></a>Detener la creación de perfiles

1. Cierre el diálogo **Reproducir ejecución de complementos**
1. En la herramienta de registro de complementos, haga clic en **Detener la creación de perfiles**.

    ![Detener la creación de perfiles](media/tutorial-debug-plug-in-stop-profiling.png)

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre tareas comunes que hará con los complementos, continúe con [Tutorial: Actualizar un complemento](tutorial-update-plug-in.md)

Si no sigue con el tutorial siguiente debe anular el registro del ensamblado de BasicPlugin que creó en este paso. Vea [Anular registro de ensamblado, complemento, y paso](tutorial-update-plug-in.md#unregister-assembly-plug-in-and-step) para obtener instrucciones.

<a name="run-profiler-standalone"></a>

## <a name="run-the-plug-in-profiler-from-a-command-prompt-window"></a>Ejecutar el generador de perfiles de complementos desde una ventana de símbolo del sistema

 Aunque a menudo es preferible ejecutar el generador de perfiles de forma interactiva desde la herramienta de registro de complementos, el generador de perfiles se puede ejecutar desde una ventana del símbolo del sistema de la herramienta. Esto resulta útil para obtener el registro del perfil de complementos del servidor de un cliente de aplicaciones [!INCLUDE[pn_dynamics_crm](../../includes/pn-dynamics-crm.md)] para depurar un complemento con errores. Un programador puede usar dicho registro para reproducir la ejecución del complemento en la herramienta de registro de complementos y depurar el complemento mediante [!INCLUDE[pn_Visual_Studio](../../includes/pn-visual-studio.md)].

### <a name="procedure-run-the-plug-in-profiler-from-a-command-prompt"></a>Procedimiento: Ejecutar el generador de perfiles de complementos desde el símbolo del sistema

1. Abra una ventana del símbolo del sistema y establezca el directorio de trabajo en la carpeta donde descargó la herramienta de registro de complementos `PluginRegistration.exe`.
2. Escriba este comando para ver los parámetros de tiempo de ejecución disponibles: `PluginProfiler.Debugger.exe /?`.  
3. Revise la lista de parámetros compatibles y vuelva a ejecutar el programa PluginProfiler.Debugger.exe con los parámetros apropiados. 