---
title: 'Tutorial: Crear extensión de flujo de trabajo (Common Data Service) | Microsoft Docs'
description: Este tutorial mostrará el proceso para ampliar el diseñador de flujos de trabajo para agregar actividades personalizadas y lógica mediante un ensamblado de flujo de trabajo.
ms.custom: ''
ms.date: 07/16/2019
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
ms.openlocfilehash: fc3f08ac3422a50c3e1580d923aa941bba253c23
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154908"
---
# <a name="tutorial-create-workflow-extension"></a>Tutorial: Crear extensión de flujo de trabajo

Este tutorial mostrará el proceso para ampliar el diseñador de flujos de trabajo para agregar actividades personalizadas y lógica mediante un ensamblado de flujo de trabajo, conocido a veces como actividad de flujo de trabajo. Las extensiones que cree de esta manera se pueden usar en un flujo de trabajo, una acción personalizada, o un diálogo.

Este tutorial usa un ejemplo muy sencillo para centrarse en los requisitos y el proceso para:

- Crear un proyecto de biblioteca de clases de Visual Studio
- Agregar una clase CodeActivity
- Definir parámetros de entrada y salida
- Adición de lógica de negocios
- Firmar y crear el ensamblado
- Registrar el ensamblado
- Probar el ensamblado
- Agregar el ensamblado a una solución

## <a name="prerequisites"></a>Requisitos previos

-  Una instancia y privilegios de administrador de Common Data Service
- Descripción de cómo configurar flujos de trabajo. Más información: [Flujos de trabajo de Common Data Service clásico](/flow/workflow-processes)
- Una aplicación basada en modelos que le permite editar cuentas.

## <a name="goal"></a>Objetivo

El siguiente ejemplo creará una actividad de flujo de trabajo personalizada simple que se puede usar en un flujo de trabajo, un diálogo, o un proceso de acción. Más información: [Configurar fases y pasos del flujo de trabajo](/flow/configure-workflow-steps)

Esta actividad de flujo de trabajo personalizada cumplirá los siguientes requisitos:

1. Aceptar un parámetro de entrada decimal
1. Generar un valor igual al parámetro de entrada más 10.

En un flujo de trabajo para la entidad **Cuenta** puede usarse de la forma siguiente para aumentar el valor de **Límite de crédito** mediante dos pasos:

![El objetivo de este tutorial](media/tutorial-create-workflow-activity-goal.png)

El paso 1 usa la actividad de flujo de trabajo personalizada **Ejemplo: Incrementar en 10** para aceptar el valor **Límite de crédito de la cuenta** e incrementarlo en 10.
El Paso 2 usa la acción **Actualizar registro** para actualizar el valor de **Límite de crédito de la cuenta** con el valor incrementado.

### <a name="step-1-get-incremented-account-credit-limit"></a>Paso 1: Obtener Límite de crédito de la cuenta incrementado

Cuando se agrega el primer paso, la actividad de flujo de trabajo personalizada estará disponible en un grupo **Ejemplo** y tendrá el nombre **Incrementar en 10**.

![El paso para incrementar en 10](media/tutorial-create-workflow-activity-increment-by-10-step.png)

Al configurar el primer paso haciendo clic en el botón **Establecer propiedades**, se requerirá la propiedad **Entrada decimal** y solo aceptará un valor decimal, como el atributo **Límite de crédito** de la entidad **Cuenta**.

![Establecer coma decimal](media/tutorial-create-workflow-activity-step1.png)

### <a name="step-2-set-new-account-credit-limit"></a>Paso 2: Establecer nuevo límite de crédito de la cuenta

En el segundo, una acción **Actualizar registro** asignará la salida del paso **Obtener Límite de crédito de la cuenta incrementado** para actualizar el valor del límite del **Crédito de la cuenta** con el valor incrementado.

![Actualizar el límite de crédito](media/tutorial-create-workflow-activity-step2.png)

## <a name="create-a-visual-studio-class-library-project"></a>Crear un proyecto de biblioteca de clases de Visual Studio

Este proyecto creará un ensamblado de flujo de trabajo simple que aumentará un valor decimal por 10.

1. Iniciar Visual Studio.
1. En el menú **Archivo**, haga clic en **Nuevo**, y haga clic en **Proyecto**.
1. Busque *Biblioteca de clases* y seleccione **Biblioteca de clases (.NET Framework)**.

    ![Buscar biblioteca de clases (.NET Framework)](media/create-new-class-library-project.png)

1. Haga clic en **Siguiente**.
1. Especificar un nombre y ubicación para la solución

    ![Configurar el nuevo diálogo de proyecto en Visual Studio 2019](media/configure-your-new-project.png)

    > [!NOTE]
    > Elija el nombre del proyecto que tenga sentido para el proyecto. En este ejemplo usaremos `SampleWorkflowActivity`.

1. Haga clic en **Crear**.
1. En el **Explorador de soluciones**, haga clic con el botón secundario en el proyecto y seleccione **Propiedades**. En la pestaña **Aplicación**, compruebe que **.NET Framework 4.6.2** se define como marco de trabajo de destino.

    ![establecer propiedades del proyecto](media/tutorial-create-workflow-activity-workflow-project.png)

1. En el **Explorador de soluciones**, haga clic con el botón secundario en el proyecto y seleccione **Administrar paquetes de NuGet**. .

    ![administrar paquetes nuget](media/tutorial-create-workflow-activity-manage-nuget-packages.png)

1. Busque el paquete [Microsoft.CrmSdk.Workflow NuGet](https://www.nuget.org/packages/Microsoft.CrmSdk.Workflow/) e instálelo.

    ![Instalar el paquete de NuGet de flujo de trabajo Microsoft.CrmSdk.Workflow](media/select-install-microsoft.crmsdk.workflow-nuget-package.png)

    > [!NOTE]
    > Asegúrese de que el paquete que instale es propiedad de [crmsdk](https://www.nuget.org/profiles/crmsdk). Este paquete incluirá el `Microsoft.Xrm.Workflow.dll` e incluirá una dependencia en el paquete [Microsoft.CrmSdk.CoreAssemblies](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreAssemblies/) para que también se incluya el ensamblado `Microsoft.Xrm.Sdk.dll` necesario. 

1. Debe hacer clic en **Acepto** en el diálogo **Aceptación de licencia**.

    ![Acepto el contrato de licencia](media/tutorial-create-workflow-activity-license-acceptance.png)

## <a name="rename-the-class-file"></a>Cambiar el nombre del archivo de clases

1. En el **Explorador de soluciones**, haga clic con el botón secundario en el archivo Class1.cs predeterminado y seleccione **Cambiar nombre**.

    ![Cambie el nombre del archivo Class1.cs](media/rename-class1-file.png)

    > [!NOTE]
    > Elija un nombre de clase que tenga sentido para la actividad. En este ejemplo, llamaremos a la clase `IncrementByTen`.

1. Seleccione **Sí** en el cuadro de diálogo que le pregunta si desea cambiar el nombre de la clase también.

    ![Seleccione Sí para cambiar el nombre de la clase también](media/rename-file-dialog.png)

1. Abra el archivo IncrementByTen.cs y agregue lo siguiente usando directivas:

    ```csharp
    using System.Activities;
    using Microsoft.Xrm.Sdk;
    using Microsoft.Xrm.Sdk.Workflow;
    ```

1. Haga que la clase herede de la clase [CodeActivity](/dotnet/api/system.activities.codeactivity) y asígnela un modificador de acceso público como se indica a continuación:

    ```csharp
    public class IncrementByTen: CodeActivity
        {

        }
    ```

1. Agregue el método **Execute** desde la clase `CodeActivity` mediante acciones rápidas de Visual Studio o manualmente:

    ![implementar interfaz codeactivity](media/tutorial-create-workflow-activity-implement-codeactivity-interface.png)

1. La clase ahora tiene esta apariencia:

    ```csharp
    public class IncrementByTen : CodeActivity
    {
        protected override void Execute(CodeActivityContext context)
        {
            throw new NotImplementedException();
        }
    }
    ```

## <a name="define-input-and-output-parameters"></a>Definir parámetros de entrada y salida

1. Agregue un conjunto de parámetros de entrada y de salida donde el valor el valor del parámetro de salida será el valor del parámetro de entrada incrementado en 10.

    ```csharp
    public class IncrementByTen : CodeActivity
    {
        [RequiredArgument]
        [Input("Decimal input")]
        public InArgument<decimal> DecInput { get; set; }

        [Output("Decimal output")]
        public OutArgument<decimal> DecOutput { get; set; }

        protected override void Execute(CodeActivityContext context)
        {
            
        }
    }
    ```

    > [!NOTE]
    > Observe cómo se utilizan [Atributos .NET](/dotnet/standard/attributes) para proporcionar metadatos sobre los parámetros en el ensamblado. Más información: [Agregar parámetros](workflow-extensions.md#add-parameters)

## <a name="add-your-business-logic"></a>Adición de lógica de negocios

Agregue la lógica en el método Execute para aplicar la lógica para aumentar el valor de entrada en 10.

```csharp
    protected override void Execute(CodeActivityContext context)
    {
      decimal input = DecInput.Get(context);
      DecOutput.Set(context, input + 10);
    }
```

## <a name="sign-and-build-the-assembly"></a>Firmar y crear el ensamblado

1. Los ensamblados de actividad personalizada de flujo de trabajo (y los complementos) se deben firmar. En las propiedades del proyecto, en la pestaña **Firma** seleccione **Firmar el ensamblado**. En **Elija un archivo de clave de alta seguridad**:, seleccione la opción **&lt;Nuevo...&gt;**.
    No es necesario establecer una contraseña a los efectos de este tutorial. Para este ejemplo hemos creado un nuevo archivo de clave de alta seguridad denominado `SampleWorkflowActivity.snk`

    ![firme el ensamblado](media/tutorial-create-workflow-activity-sign-assembly.png)

1. Cree la solución en modo de depuración y compruebe que el ensamblado `SampleWorkflowActivity.dll` está en la carpeta `/bin/Debug`.

> [!NOTE]
> Mientras desarrolla un ensamblado es válido usar la configuración de compilación de **Depuración**. Al implementar el ensamblado en un servidor de producción o en una solución, debe usar la configuración de compilación de **Versión**.

## <a name="register-your-assembly"></a>Registrar el ensamblado

Los ensamblados personalizados de actividades de flujo de trabajo se registran mediante la herramienta de registro de complementos. La herramienta proporciona una interfaz gráfica de usuario y admite el registro de ensamblajes que contienen complementos o actividades de flujo de trabajo personalizadas. Para obtener la herramienta de registro de complementos, consulte [Descargar herramientas de NuGet](../download-tools-nuget.md).

[!INCLUDE [cc-connect-plugin-registration-tool](../includes/cc-connect-plugin-registration-tool.md)]

### <a name="register-your-assembly"></a>Registrar el ensamblado

1. Seleccione **Registrar** > **Registrar nuevo ensamblado**

    ![comando registrar ensamblado](media/tutorial-create-workflow-activity-register-assembly.png)

1. En el cuadro de diálogo **Registrar nuevo ensamblado**, haga clic en el botón de puntos suspensivos (**…**) y vaya al `SampleWorkflowActivity.dll` en la carpeta `/bin/Debug`.

    ![cuadro de diálogo de registro de ensamblado](media/tutorial-create-workflow-activity-register-assembly-dialog.png)

    > [!NOTE]
    > Nota: Con Common Data Service se seleccionan las únicas opciones válidas para los pasos 3 y 4 y se deshabilitan las opciones no válidas.

1. Haga clic en **Registrar complementos seleccionados**. Debe ver un diálogo de confirmación.

    ![diálogo de complemento registrado](media/tutorial-create-workflow-activity-register-plug-in-dialog.png)

1. Haga clic en **Aceptar** para cerrar el diálogo **Registrar nuevo ensamblado**.

### <a name="configure-activity-names"></a>Configuración de nombres de actividades

1. En la lista de **Complementos registrados y actividades personalizadas del flujo de trabajo**, busque **(Assembly) SampleWorkflowActivity** y expándalo para mostrar el **(Workflow Activity) SampleWorkflow.Activity.IncrementByTen - Isolatable**.
1. Seleccione la **(Workflow Activity) SampleWorkflow.Activity.IncrementByTen - Isolatable** y en el área **Propiedades** edite las **Propiedades editables** usando los valores de la tabla siguiente:

    |Campo editable|Valor original|Valor nuevo|Descripción|
    |--|--|--|--|
    |Descripción||Devuelve el valor del parámetro de entrada más 10.|No es visible en la interfaz de usuario del diseñador de procesos, pero puede resultar útil al generar documentación de los datos extraídos de la entidad PluginType que almacena esta información.|
    |FriendlyName|un valor de GUID|IncrementByTen|Nombre descriptivo para el complemento.|
    |Nombre|SampleWorkflowActivity.IncrementByTen|Incrementar en 10|El nombre del menú representado|
    |WorkflowActivityGroupName|SampleWorkflowActivity (1.0.0.0)|Muestra|El nombre del submenú agregado al menú principal del diseñador del proceso de Common Data Service.|

    > [!NOTE]
    > Si el **Nombre** y **WorkflowActivityGroupName** están establecidas como null, la actividad personalizada no será visible en el diseñador de procesos.

1. Haga clic en el (icono) **Guardar** para guardar los cambios.

    ![Guarde las propiedades de actividad del flujo de trabajo](media/tutorial-create-workflow-activity-set-workflow-activity-properties.png)

## <a name="test-your-assembly"></a>Probar el ensamblado

Puede probar la nueva actividad de flujo de trabajo creando un proceso que la use. Use estos pasos para crear el proceso de flujo de trabajo descrito en la sección [Objetivo](#goal) anterior:

1. Abrir[Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)
1. Seleccione **Solución**.
1. Abra la solución **Editor predeterminados de CDS**.
1. En el menú, amplíe los **...** y elija **Cambiar a clásica**.
    
    ![Cambiar a la interfaz de usuario clásica](media/switch-to-classic-solution-ui.png)

1. Seleccione **Procesos** en la lista **Componentes**
1. Seleccione **Nuevo** y en el diálogo **Crear proceso** escriba lo siguiente:

    |Campo|Value|
    |--|--|
    |Nombre del proceso|Prueba de SampleWorkflowActivity.IncrementByTen|
    |Categoría|Flujo de trabajo|
    |Entidad|Cuenta|
    |Ejecutar este flujo de trabajo en segundo plano (recomendado)|anulada la selección|

    > [!NOTE]
    > La opción de **Ejecutar este flujo de trabajo en segundo plano** se ha vuelto a seleccionar para convertir esto en un flujo de trabajo ( sincrónico) en tiempo real. Esto facilitará las pruebas.

    ![Crear un proceso](media/tutorial-create-workflow-activity-test-activity-process.png)

1. Haga clic en **Aceptar**.
1. Aplique los cambios siguientes:

    |Campo|Value|
    |--|--|
    |Ámbito|Organización|
    |Iniciar cuando: Cambio en los campos de registro|seleccionada y el campo `name` especificado en el diálogo.|

    ![configuración de un flujo de trabajo de prueba](media/tutorial-create-workflow-activity-configuration-test-workflow.png)

    > [!NOTE]
    > Al configurar **Ámbito** como **Organización** se crea un flujo de trabajo que puede aplicar cualquier persona de la organización.

1. Agregue el siguiente **Paso**:

    ![Agregue el paso SampleWorkflowActivity.IncrementByTen](media/tutorial-create-workflow-activity-use-sample-step.png)

1. Establezca el paso **Descripción** como **Obtener Límite de crédito de la cuenta incrementado** y haga clic en **Establecer propiedades**.
1. Establezca el valor de la propiedad **Entrada decimal** como el Límite de crédito de la cuenta con un valor predeterminado de 0.

    ![Establezca la propiedad de entrada decimal](media/tutorial-create-workflow-activity-configure-first-step.png)

1. Haga clic en **Guardar y cerrar**.
1. Agregue un paso **Actualizar registro**:

    ![Agregue un paso Actualizar registro](media/tutorial-create-workflow-activity-add-update-record-step.png)

1. Haga clic en **Establecer propiedades** y establezca el valor del **Límite de crédito** como el valor del paso **Obtener Límite de crédito de la cuenta incrementado**.

    ![Establezca el valor del límite de crédito](media/tutorial-create-workflow-activity-set-credit-limit.png)

    Los pasos del flujos de trabajo deben tener un aspecto similar al siguiente:

    ![El flujo de trabajo completado](media/tutorial-create-workflow-activity-completed-workflow.png)

1. Haga clic en **Guardar y cerrar**.
1. Active el flujo de trabajo haciendo clic en **Activar** en el menú…

    ![comando activar flujo de trabajo](media/tutorial-create-workflow-activity-activate-command.png)

1. Y haga clic en **Activar** en el cuadro de diálogo **Confirmación de activación de proceso**.

    ![Diálogo Confirmación de activación de proceso](media/tutorial-create-workflow-activity-process-activate-confirmation-dialog.png)

1. Navegue a una aplicación basada en modelos y vea una lista de cuentas.
1. Seleccione una cuenta.
1. Editar el valor del campo **Nombre de cuenta**.
1. Guarde el registro de cuenta.
1. Compruebe que la cuenta que editó tiene un valor de **Límite de crédito** aumentado en 10.

    ![comprobar límite de crédito de la cuenta incrementado](media/tutorial-create-workflow-verify-credit-limit.png)

## <a name="add-your-assembly-to-a-solution"></a>Agregar el ensamblado a una solución

Para distribuir una actividad de flujo de trabajo personalizada en una solución, debe agregar el ensamblado registrado que lo contiene a una solución no administrada.

1. Abra la solución no administrada a la que desea agregar el ensamblado utilizando [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)
1. Seleccione **Agregar existentes** > **Otro** > **Ensamblado de complementos**

    ![Agregar ensamblado de complementos existente](media/add-existing-plugin-assembly.png)

1. Busque el ensamblado de complemento por nombre, en este caso 'SampleWorkflowActivity'.
1. Seleccione el ensamblado de complemento y seleccione **Agregar**.

### <a name="see-also"></a>Vea también

[Extensiones de flujo de trabajo](workflow-extensions.md)<br />
[Ejemplo: crear una actividad de flujo de trabajo personalizada](sample-create-custom-workflow-activity.md)<br />
[Ejemplo: actualizar el siguiente cumpleaños con una actividad de flujo de trabajo personalizada](sample-update-next-birthday-using-custom-workflow-activity.md)<br />
[Ejemplo: Calcular una puntuación de crédito con una actividad de flujo de trabajo personalizada](sample-calculate-credit-score-custom-workflow-activity.md)