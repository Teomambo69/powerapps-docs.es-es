---
title: Automatización de pruebas con la canalización de Azure mediante el editor clásico | Microsoft Docs
description: Describe cómo automatizar conjuntos de pruebas y casos mediante el editor clásico de la canalización de Azure.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/16/2020
ms.author: aheaney
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ecfeeb1f62032008d7ada618afb56e6da8589f40
ms.sourcegitcommit: 223c3d19ec4fbe43fcc7a16b76423c00f8602ecd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2020
ms.locfileid: "81490899"
---
# <a name="automate-tests-with-azure-pipeline-using-classic-editor"></a>Automatización de pruebas con la canalización de Azure mediante el editor clásico

En este artículo, aprenderá a configurar y ejecutar las pruebas de la aplicación Canvas compiladas en test Studio con el [editor clásico de Azure pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started/pipelines-get-started?view=azure-devops#define-pipelines-using-the-classic-interface) en [Azure DevOps Services](https://docs.microsoft.com/azure/devops/user-guide/what-is-azure-devops?view=azure-devops).

Puede usar un proyecto público en GitHub- [Microsoft/PowerAppsTestAutomation](https://github.com/microsoft/PowerAppsTestAutomation) para:

- Automatizar las operaciones de inicio de sesión en la aplicación.
- Abra un explorador en el agente de compilación y ejecute un conjunto de casos de prueba y conjuntos de pruebas.
- Vea el estado de la ejecución de pruebas en la canalización DevOps de Azure.

## <a name="prerequisites"></a>Requisitos previos

Antes de comenzar, debe completar los pasos siguientes:

- [Bifurcar](#step-1---fork-the-powerappstestautomation-project) el proyecto [Microsoft/PowerAppsTestAutomation](https://github.com/microsoft/PowerAppsTestAutomation) en github.

    > [!NOTE]
    > Las bifurcaciones públicas no se pueden convertir en privadas. Si desea crear un repositorio privado, [duplique el repositorio](https://help.github.com/github/creating-cloning-and-archiving-repositories/duplicating-a-repository).

- Cree un nuevo [*archivo URL de prueba. JSON*](#step-2---create-test-url-json-file) en el repositorio con las direcciones URL de prueba de la aplicación que desea ejecutar desde la canalización.

### <a name="step-1---fork-the-powerappstestautomation-project"></a>Paso 1: bifurcar el proyecto PowerAppsTestAutomation

Una [bifurcación](https://help.github.com/github/getting-started-with-github/fork-a-repo) es una copia de un repositorio. Al bifurcar un repositorio, puede realizar cambios sin que afecte al proyecto original.

1. Inicie sesión en [GitHub](https://github.com/).

1. Vaya al repositorio [Microsoft/PowerAppsTestAutomation](https://github.com/microsoft/PowerAppsTestAutomation) . También puede buscar **Microsoft/PowerAppsTestAutomation** en su lugar y, a continuación, seleccionar el repositorio:

    ![Buscar en GitHub](media/test-studio-classic-pipeline-editor/search-github.png)

1. Seleccionar **bifurcación**:

    ![Desvío](media/test-studio-classic-pipeline-editor/fork.png)

1. Seleccione dónde desea bifurcar:

    ![Cuenta de bifurcación](media/test-studio-classic-pipeline-editor/fork-account.png)

El repositorio bifurcado ahora estará disponible.

### <a name="step-2---create-test-url-json-file"></a>Paso 2: creación del archivo. JSON de la dirección URL de prueba

El archivo test URL. JSON contendrá las direcciones URL del conjunto de pruebas y del caso de prueba para validar la aplicación. Para recuperar las direcciones URL de los casos de prueba y del conjunto de pruebas de la aplicación, seleccione el [vínculo copiar reproducir](working-with-test-studio.md#playing-tests-in-a-browser) en test Studio.

Puede encontrar un archivo de ejemplo ```Samples/TestAutomationURLs.json``` en el repositorio que creó anteriormente.

1. Cree un nuevo archivo de ```TestURLs.json``` en el repositorio o use cualquier otro nombre de archivo. <br> El nombre de archivo y la ubicación se asignarán en las variables de canalización más adelante en el documento.

1. Copie el formato del archivo de ```Samples/TestAutomationURLs.json```.

1. Actualice la sección direcciones URL de prueba con las pruebas que desea validar en la aplicación.

1. Confirme los cambios en el repositorio:

    ![Actualización de JSON](media/test-studio-classic-pipeline-editor/json-update.png)

## <a name="create-a-pipeline"></a>Crear una canalización

1. Inicie sesión en la instancia de Azure DevOps.

1. Seleccione un proyecto existente o cree un nuevo proyecto.

1. Seleccione **canalizaciones** en el menú de la izquierda.

1. Seleccione **crear canalización**:

    ![Crear canalización](media/test-studio-classic-pipeline-editor/create-pipeline.png)

1. Seleccione **usar el editor clásico**:

    ![Editor clásico](media/test-studio-classic-pipeline-editor/use-classic-editor.png)

1. Seleccione GitHub como el origen.

1. Si es necesario, autorice la conexión de GitHub mediante OAuth o el uso de un token de acceso personal:

    ![Canalización: GitHub](media/test-studio-classic-pipeline-editor/pipeline-github.png)

1. Si es necesario, edite el nombre de la conexión.

1. Seleccione **...** (puntos suspensivos) en el lado derecho de la entrada del **repositorio** .

1. Escriba el nombre del proyecto en GitHub y, a continuación, **selecciónelo** :

    ![Seleccionar repositorio](media/test-studio-classic-pipeline-editor/select-repo.png)

1. Seleccione **Continuar**.

1. En la pantalla elegir una plantilla, seleccione **trabajo vacío**:

    ![Trabajo vacío](media/test-studio-classic-pipeline-editor/empty-job.png)

1. **Guarde** la canalización.

## <a name="add-tasks-to-the-pipeline"></a>Agregar tareas a la canalización

Ahora agregará nuevas tareas de trabajo y configurará las tareas para ejecutar las pruebas desde la canalización en esta secuencia:

1. [Configurar la resolución de pantalla mediante PowerShell.](#step-1---configure-screen-resolution-using-powershell)

1. [Restaure los paquetes NuGet para la solución PowerAppsTestAutomation.](#step-2---restore-nuget-packages)

1. [Compile la solución PowerAppsTestAutomation.](#step-3---build-the-powerappstestautomation-solution)

1. [Agregue pruebas de Visual Studio para Google Chrome.](#step-4---add-visual-studio-tests-for-google-chrome)

1. [Agregue las pruebas de Visual Studio para Mozilla Firefox.](#step-5---add-visual-studio-tests-for-mozilla-firefox)

### <a name="step-1---configure-screen-resolution-using-powershell"></a>Paso 1: configurar la resolución de pantalla mediante PowerShell

1. Seleccione **+** junto al *trabajo del agente 1*.

1. Busque **PowerShell**.

1. Seleccione **Agregar** para agregar una tarea de PowerShell al trabajo:

    ![PowerShell](media/test-studio-classic-pipeline-editor/powershell.png)

1. Seleccione la tarea. <br>
    También puede actualizar el nombre para mostrar para establecer la resolución de la *pantalla del agente en 1920 x 1080* o similar.

1. Seleccione **insertado** como tipo de script y escriba lo siguiente en la ventana de script:

    ```powershell
    # Set agent screen resolution to 1920x1080 to avoid sizing issues with Portal  
    Set-DisplayResolution -Width 1920 -Height 1080 -Force
    # Wait 10 seconds  
    Start-Sleep -s 10
    # Verify Screen Resolution is set to 1920x1080  
    Get-DisplayResolution
    ```

    ![Secuencia de comandos](media/test-studio-classic-pipeline-editor/script.png)

### <a name="step-2---restore-nuget-packages"></a>Paso 2: restauración de paquetes NuGet

1. Seleccione **+** junto al trabajo del agente 1.

1. Busque **NuGet**.

1. Seleccione Agregar para agregar una tarea de NuGet al trabajo.

1. Seleccione la tarea.
    <br> También puede actualizar el nombre para mostrar para **restaurar paquetes de NuGet** o similares.

1. Seleccione **...** (puntos suspensivos) en el campo de configuración **ruta de acceso al paquete de solución, packages. config o Project. JSON** .

1. Seleccione el archivo de solución PowerAppsTestAutomation. sln.

1. Seleccione **Aceptar**:

    ![Paquete NuGet](media/test-studio-classic-pipeline-editor/nuget.png)

### <a name="step-3---build-the-powerappstestautomation-solution"></a>Paso 3: compilar la solución PowerAppsTestAutomation

1. Seleccione **+** junto al trabajo del agente 1.

1. Busque **Visual Studio Build**.

1. Seleccione **Agregar** para agregar una tarea de compilación de Visual Studio al trabajo.

1. Seleccione la tarea.
    <br> También puede actualizar el nombre para mostrar para **compilar la solución de automatización de pruebas de Power apps** o similar.

1. Seleccione **...** (puntos suspensivos) en el campo configuración de **soluciones** .

1. Seleccione el archivo de solución PowerAppsTestAutomation. sln.

1. Seleccione **Aceptar**.

### <a name="step-4---add-visual-studio-tests-for-google-chrome"></a>Paso 4: agregar pruebas de Visual Studio para Google Chrome

1. Seleccione **+** junto al trabajo del agente 1.

1. Busque **Visual Studio test**.

1. Seleccione Agregar para agregar una tarea de prueba de Visual Studio al trabajo.

1. Seleccione la tarea.
    <br> También puede actualizar el nombre para mostrar para *ejecutar pruebas de automatización de prueba de Power apps a través de \$(BrowserTypeChrome)* o similar.

1. Quite las entradas predeterminadas en el campo de texto archivos de prueba y agregue lo siguiente:

    ```**\Microsoft.PowerApps.TestAutomation.Tests\bin\\Debug\Microsoft.PowerApps.TestAutomation.Tests.dll```

1. Escriba ```TestCategory=PowerAppsTestAutomation``` en el **campo criterios de filtro**de la prueba.

1. Seleccione **combinación de pruebas contiene pruebas de IU**.

    ![Chrome](media/test-studio-classic-pipeline-editor/chrome.png)

1. Seleccione **...** (puntos suspensivos) en el campo **archivo de configuración** .

1. Expanda **Microsoft. PowerApps. TestAutomation. tests**, seleccione el archivo **patestautomation. runsettings** y, a continuación, seleccione **Aceptar**:

    ![Configuración de ejecución](media/test-studio-classic-pipeline-editor/runsettings.png)

1. Copie lo siguiente en el campo **invalidar parámetros de serie de pruebas** .

    ```
    -OnlineUsername $(OnlineUsername) -OnlinePassword $(OnlinePassword) -BrowserType $(BrowserTypeChrome) -OnlineUrl $(OnlineUrl) -UsePrivateMode $(UsePrivateMode) -TestAutomationURLFilePath $(TestAutomationURLFilePath) -DriversPath $(ChromeWebDriver)
    ```

    > [!NOTE]
    > Aquí es donde se configuran las variables de la canalización, representadas anteriormente en forma de \$(VariableName).

1. Escriba **ejecutar pruebas de automatización de prueba de Power apps a través de \$(BrowserTypeChrome)** o similar en el campo título de la serie de pruebas.

    ![Ejecución de pruebas](media/test-studio-classic-pipeline-editor/test-run.png)

### <a name="step-5---add-visual-studio-tests-for-mozilla-firefox"></a>Paso 5: adición de pruebas de Visual Studio para Mozilla Firefox

1. Haga clic con el botón secundario en la tarea **Agregar pruebas de Visual Studio para Chrome** y seleccione **clonar tareas**.

1. Seleccione la tarea y actualice las siguientes áreas.

    1. **Título**: ejecutar pruebas de automatización de prueba de Power apps a través de la copia de \$(BrowserTypeFirefox)

    1.  **Reemplazar parámetros de serie de pruebas**

        ```
        -OnlineUsername $(OnlineUsername) -OnlinePassword $(OnlinePassword) -BrowserType $(BrowserTypeFirefox) -OnlineUrl $(OnlineUrl) -UsePrivateMode $(UsePrivateMode) -TestAutomationURLFilePath $(TestAutomationURLFilePath) -DriversPath $(GeckoWebDriver)
        ```

    1.  **Título**de la serie de pruebas: ejecutar pruebas de automatización de prueba de Power apps a través de \$(BrowserTypeFirefox)

## <a name="configure-pipeline-variables"></a>Configurar variables de canalización

Ahora configurará las variables de canalización definidas en las tareas que agregó [anteriormente](#add-tasks-to-the-pipeline).

1. Seleccione la pestaña **variables** .

2. Seleccione **Agregar** y repita este paso para configurar las siguientes variables:

| Nombre de variable             | Valor de la variable                                                                                                                 |
|---------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| BrowserTypeChrome         | Chrome                                                                                                                         |
| BrowserTypeFirefox        | Firefox                                                                                                                        |
| OnlineUrl                 | <https://make.powerapps.com>                                                                                                   |
| TestAutomationURLFilePath | ```$(Build.SourcesDirectory)\<test URL file>.json``` <br>**Nota:** Este es el archivo de [*archivo. JSON de las direcciones URL de prueba*](#step-2---create-test-url-json-file) que creó anteriormente.                      |
| UsePrivateMode            | true                                                                                                                           |
| OnlineUsername            | Escriba la dirección de correo electrónico del Azure Active Directory del contexto de usuario que iniciará sesión en la aplicación. Las pruebas se ejecutarán en el contexto de esta cuenta de usuario.\> |

1. Seleccione Agregar y escriba **OnlinePassword** en el nombre de la variable.

1. Compruebe la imagen de bloqueo para convertir esta variable en un secreto.

    ![Variables](media/test-studio-classic-pipeline-editor/variables.png)

1. **Guarde** las configuraciones de canalización.

## <a name="run-and-analyze-tests"></a>Ejecutar y analizar pruebas

Para validar que las pruebas se están ejecutando correctamente, seleccione **cola** y, a continuación, seleccione **Ejecutar**. El trabajo comenzará a ejecutarse.

![Ejecutar trabajo](media/test-studio-classic-pipeline-editor/run-job.png)

A medida que se ejecuta el trabajo, seleccione el trabajo para ver un estado detallado de cada una de las tareas en ejecución:

![Detalles del trabajo](media/test-studio-classic-pipeline-editor/job-details.png)

Una vez completado el trabajo, puede ver el resumen del trabajo de alto nivel y los errores o advertencias. Al seleccionar la pestaña prueba, puede ver detalles específicos de los casos de prueba que ha ejecutado.

En el ejemplo siguiente se indica que al menos uno de nuestros casos de prueba ha producido un error al ejecutar las pruebas con el explorador Chrome:

![Chrome: error](media/test-studio-classic-pipeline-editor/chrome-failed.png)

Seleccione prueba de **RunTestAutomation** para profundizar en los detalles sobre el caso de prueba que ha dado error. En la *pestaña datos adjuntos*, puede ver el Resumen de la ejecución de pruebas y los casos de prueba con errores o pasados en el conjunto de pruebas:

![Pestaña datos adjuntos](media/test-studio-classic-pipeline-editor/attachments-tab.png)

> [!NOTE]
> Si ejecuta un conjunto de pruebas, verá un resumen de los casos de prueba superados y con errores. Si ejecuta un caso de prueba, verá detalles específicos sobre el error con cualquier información de seguimiento, si está disponible.

## <a name="known-limitations"></a>Limitaciones conocidas

- No se admite la autenticación multifactor.

- Internet Explorer 11 y Microsoft Edge no son exploradores admitidos.

- El Resumen de la prueba informará de un único resultado de prueba por explorador. El resultado de la prueba contendrá 1 o más casos de prueba o resultados del conjunto de pruebas.   

- Cualquier proceso de autenticación que no sea Azure Active Directory flujo de inicio de sesión requiere la personalización del proceso de inicio de sesión en la solución **PowerAppsTestAutomation** .

### <a name="see-also"></a>Vea también

- [Información general de Test Studio](test-studio.md)
- [Trabajo con Test Studio](working-with-test-studio.md)