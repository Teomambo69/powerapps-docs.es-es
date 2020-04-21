---
title: Test Studio para la realización de pruebas de la aplicación de lienzo | Microsoft Docs
description: Describe cómo usar Test Studio con un ejemplo para probar la aplicación de lienzo.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/05/2020
ms.author: aheaney
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9e3192d6eda9730250e35b7ce6cd488b89037d43
ms.sourcegitcommit: 223c3d19ec4fbe43fcc7a16b76423c00f8602ecd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489051"
ms.PowerAppsDecimalTransform: true
---
# <a name="working-with-test-studio-experimental"></a>Trabajo con Test Studio (experimental)

En esta guía de inicio rápido, creará pruebas para una aplicación de lienzo denominada Kudos. También puede explorar y detectar conceptos de pruebas y aplicarlos a la escritura de pruebas para sus propias aplicaciones de lienzo. La aplicación Kudos de ejemplo forma parte de un conjunto de aplicaciones de participación de los empleados disponibles para su descarga desde [Kit de inicio de experiencia del empleado](https://powerapps.microsoft.com/en-us/blog/powerapps-employee-experience-starter-kit).

> [!NOTE]
> Esta característica aún es experimental y se recomienda usarla para escribir pruebas para aplicaciones que no sean de producción. Para obtener más información, vea [Características en versión preliminar y experimentales](working-with-experimental-preview.md).

## <a name="open-test-studio"></a>Apertura de Test Studio

No es necesario habilitar esto en la aplicación como otras características experimentales. Test Studio está disponible de forma predeterminada para todas las aplicaciones de lienzo.

1. Inicie sesión en [Power Apps](https://make.powerapps.com).

2. Cree una [nueva aplicación](get-started-test-drive.md) o [edite una existente](edit-app.md).

3. Guarde la aplicación en Power Apps para abrir Test Studio. 
    
    > [!NOTE]
    > Debe guardar la aplicación para poder escribir pruebas para ella.

4. En el panel de navegación de la izquierda, seleccione **Herramientas avanzadas**.

5. Seleccione **Abrir pruebas** para abrir Test Studio para esta aplicación. Se abrirá Test Studio en una nueva pestaña del explorador.

    ![Apertura de Test Studio](./media/working-with-test-studio/open-tests.png)

> [!NOTE]
> Las pruebas se publican y almacenan en el paquete de la aplicación. Exportar e importar un paquete de aplicación de lienzo en otro entorno también incluirá todas las definiciones de prueba, como conjuntos de pruebas y casos de prueba que haya creado. 

## <a name="create-a-test-suite"></a>Creación de un conjunto de pruebas

De forma predeterminada, en Test Studio se crean un conjunto de pruebas y un caso de prueba. Los conjuntos de pruebas se usan para organizar los casos de prueba. Una aplicación puede contener uno o más conjuntos de pruebas. Puede usar el conjunto y el caso de pruebas predeterminados para empezar a escribir las pruebas inmediatamente o crear un nuevo conjunto de pruebas.

1. Seleccione **Nuevo conjunto**.
2. Actualice el **Nombre y la descripción del conjunto de pruebas** seleccionando los campos en la cuadrícula principal.

    ![Nuevo conjunto de pruebas](./media/working-with-test-studio/new-test-suite.png)

## <a name="create-a-test-case"></a>Crear un caso de prueba

En función de cómo quiera organizar o agrupar las pruebas, puede crear varios casos de prueba en un conjunto de pruebas. Cada caso puede probar una característica específica o un subconjunto de funcionalidades de la aplicación.

1. Seleccione un conjunto de pruebas.
2. Seleccione **Nuevo caso** en el menú superior para crear un caso.
3. Actualice el **Nombre y la descripción del caso de prueba** seleccionando los campos en la cuadrícula principal.

 ![Nuevo caso de prueba](./media/working-with-test-studio/new-test-case.png)

## <a name="record-a-test-case"></a>Grabación de un caso de prueba

Un caso de prueba consta de pasos de prueba que contienen acciones. Las acciones de prueba se escriben con expresiones de Power Apps que realizan una tarea. Puede usar la grabadora para generar automáticamente los pasos de prueba a medida que interactúe con la aplicación. Después de grabar, puede actualizar el caso de prueba, agregar nuevos pasos, eliminar pasos y escribir aserciones de prueba para validar el resultado de la prueba.

> [!NOTE]
> Solo la aplicación publicada se reproduce en modo de grabación. Publique los cambios recientes en la aplicación antes de iniciar la grabación de un caso de prueba. Grabar sin publicar cambios recientes hace que la última versión publicada de la aplicación se reproduzca en modo de grabación.

1. Seleccione **Grabar** en el menú superior. Se abrirá la aplicación publicada con el modo de grabación en una nueva pestaña del explorador.

    > [!IMPORTANT]
    > La grabación en un caso de prueba existente invalida cualquier paso de prueba existente que ya esté presente.

    ![Grabación de pruebas](./media/working-with-test-studio/record-tests.png)

2. Interactúe con la aplicación. Las acciones se **graban** en el panel izquierdo.

3. Una vez completada la interacción, seleccione **Listo**. Opcionalmente, puede seleccionar **Cancelar** para volver a Test Studio sin que se graben las interacciones. 

    ![Guardar grabación](./media/working-with-test-studio/save-recording.png)

4. Vea los pasos de prueba y las expresiones que se generaron automáticamente en Test Studio.
5. Edite la descripción del paso en la cuadrícula principal, si es necesario. También puede actualizar las acciones del paso de prueba seleccionando la fórmula en la cuadrícula principal.

    ![Actualización de casos de prueba](./media/working-with-test-studio/update-test-case.png)

### <a name="add-test-steps-and-test-assertions"></a>Adición de pasos de prueba y prueba de aserciones

Cada caso de prueba debe tener un resultado esperado. En el ejemplo de Kudos, uno de los resultados esperados de enviar un Kudo es crear un nuevo registro en la base de datos de Common Data Service. Ahora actualizará el caso de prueba y agregará pasos de prueba adicionales para validar que un registro se ha creado correctamente.

Necesita los siguientes pasos para comprobar la creación correcta del registro:

- Inicialice una variable para el recuento de registros de Kudos en la base de datos al principio del caso de prueba.
- Inicialice una variable para el recuento de registros de Kudos en la base de datos al final del caso de prueba.
- Escriba una expresión de aserción de prueba para validarla incrementada en uno. Si el recuento no aumenta en uno, se produce un error en la aserción de prueba y en el caso de prueba.

Para agregar pasos de prueba y probar aserciones en la aplicación Kudos:

1. Seleccione el paso 1 o el paso sobre el que quiera insertar un nuevo paso. 

2. Seleccione **Insertar un paso anterior** en el menú superior o seleccione la opción en la fila activa. Esto crea un paso vacío.

    ![Insertar paso](./media/working-with-test-studio/insert-step-above.png)

    > [!NOTE]
    > Al seleccionar **Insertar paso anterior**, se agrega un nuevo paso en blanco sobre el paso actual. También puede usar las acciones **Assert**, **SetProperty**, **Select** o **Trace** en su lugar. Esto agrega el paso con la fórmula de acción correspondiente que se puede editar.

3. Actualice la descripción del paso. Por ejemplo, "recuento Kudo en la base de datos".

4. Escriba una expresión o fórmula en la entrada de acción para contar los registros de la base de datos antes de ejecutar la prueba.

    Puede usar cualquier expresión admitida. También puede consultar cualquier origen de datos, colecciones, variables o flujos de ejecución que contenga la aplicación, así como crear nuevas variables globales o colecciones para usarlas en las pruebas.

    ```Set(kudosBeforeTest; CountRows(Filter(Kudos; Receiver.Email = "someone@example.com")))```

5. Seleccione el paso 2 o el paso sobre el que quiera insertar un nuevo paso.

6. Seleccione **Insertar un paso anterior** en el menú superior o seleccione la opción en la fila activa. Esto crea un paso vacío.

7. Escriba una expresión o una fórmula en la entrada de acción para [Seguimiento](./functions/function-trace.md) y escriba el valor *kudosBeforeTest* en el registro de resultados de las pruebas.

    ```Trace("kudosBeforeTest : " & kudosBeforeTest);;```

    ![Kudos antes de la prueba](./media/working-with-test-studio/kudos-before-test.png)

8. Vaya a la parte inferior del caso de prueba e inserte un nuevo paso para contar los registros de la base de datos una vez completada la prueba.

    ```Set(kudosAfterTest; CountRows(Filter(Kudos; Receiver.Email = "someone@example.com")))```

9. Agregue un paso final para validar que el número de registros en la base de datos haya aumentado en 1 y escriba la siguiente acción de aserción para comprobarlo:

    ```Assert(kudosAfterTest = kudosBeforeTest + 1; "Kudos count incorrect. Expected : " & kudosBeforeTest + 1  & " Actual :" & kudosAfterTest)```

    ![Kudos después de la aserción de prueba](./media/working-with-test-studio/kudos-after-test-assert.png)

10. Guarde el caso de prueba en el menú de la parte superior derecha de Test Studio. 

## <a name="play-back-your-test"></a>Reproducción de la prueba

Puede reproducir la prueba grabada para validar la funcionalidad de la aplicación. Puede reproducir todas las pruebas dentro de un único conjunto de pruebas o un caso de prueba único. 

Antes de volver a reproducir la grabación con cambios recientes, debe publicar la aplicación:

![Reproducción sin publicación](./media/working-with-test-studio/publish-test-studio-changes.png)

> [!IMPORTANT]
> Si lo omite, la reproducción de la grabación no contendrá los cambios recientes de la prueba. El último caso o conjunto de pruebas publicado se reproducirá en la aplicación.

1. Haga clic en **Publicar**. Esto guarda y publica automáticamente la prueba.

    ![Publicar cambios](./media/working-with-test-studio/publish-button.png)

2. Seleccione un conjunto de pruebas o un caso de prueba único.

3. Haga clic en **Reproducir**. La aplicación publicada se abre en el modo de **Reproducción** y puede ver cómo los pasos de prueba se reproducen automáticamente. Una marca de verificación verde indica que el caso de prueba se ejecuta correctamente. Si se produce un error en un paso, se muestra un indicador de error rojo junto con un mensaje de error

    ![Modo de reproducción](./media/working-with-test-studio/play-mode.png)

4. Haga clic en Listo para volver a Test Studio.

### <a name="failed-assertion"></a>Error de aserción

En esta sección, cambiará la aserción de prueba para experimentar una prueba con errores:

1. Edite el paso de aserción seleccionando el cuadro de expresión.

2. Actualice ```+ 1``` a ```+ 2``` en la acción de prueba. Esto significa que la prueba espera que se creen 2 registros, lo cual es incorrecto. Si la prueba se realiza correctamente, solo se debe crear un registro en la base de datos.

    ```Assert(kudosAfterTest = kudosBeforeTest + 2; "Kudos count incorrect. Expected : " & kudosBeforeTest + 2  & " Actual :" & kudosAfterTest)```

    ![Actualización del recuento de aserciones](./media/working-with-test-studio/assert-count-update.png)

3. Seleccione **Publicar**.

4. Seleccione **Iniciar**.

5. Vea la reproducción de la prueba. Ahora se produce un error en el último paso y se muestra el mensaje proporcionado en el paso de aserción.  

    ![Error de reproducción](./media/working-with-test-studio/playback-error.png)

### <a name="playing-tests-in-a-browser"></a>Reproducción de pruebas en un explorador

Tiene la opción de copiar un vínculo para reproducir una prueba en un explorador independiente fuera de Test Studio. Esto ayuda a integrar las pruebas en la compilación continua y la canalización de versiones, como **Azure DevOps**.

Se conserva el vínculo de reproducción de la prueba seleccionada. No cambia para el conjunto de pruebas o el caso de prueba. Puede actualizar las pruebas sin necesidad de modificar los procesos de compilación y publicación.

Para reproducir pruebas en el explorador:

1. Seleccione un conjunto de pruebas o un caso de prueba en el panel derecho.

2. Haga clic en **Copiar vínculo de prueba**.

    ![Copia del vínculo de prueba](./media/working-with-test-studio/copy-play-link.png)

3. Si hay cambios no publicados, se le pedirá que publique las pruebas.

    ![Publicación antes de copiar el vínculo](./media/working-with-test-studio/publish-before-copy-link.png)

4. Puede omitir el proceso de publicación y copiar el vínculo de reproducción. Si se omite, no se reproducen nuevos cambios en las pruebas.

    ![Copia del vínculo de prueba](./media/working-with-test-studio/copy-play-link-ack.png)

5. Abra un navegador y pegue la URL en la barra de direcciones para reproducir la prueba.

6. Vea la reproducción de la prueba.

## <a name="processing-test-results"></a>Procesamiento de los resultados de pruebas

El panel de prueba visible al reproducir pruebas en Test Studio no es visible cuando se usa el explorador. Debido a esto, no puede determinar el paso de prueba específico que se ejecuta o si la prueba se supera o no.

Para determinar los resultados de las pruebas fuera de Test Studio, hay dos propiedades denominadas **OnTestCaseComplete** y **OnTestSuiteComplete** disponibles en el objeto de prueba que puede usar para procesar los resultados de las pruebas. Al integrar las pruebas en una canalización de versión y compilación continua como **Azure DevOps**, estas propiedades se pueden usar para determinar si debe continuar con la implementación de la aplicación.

La expresión especificada para estas propiedades se desencadena cuando se completa cada caso o conjunto. Puede personalizar estas propiedades para procesar y enviar los resultados de las pruebas a varios orígenes de datos o servicios como:

- SQL Server.
- Common Data Service.
- Power Automate.
- Correo electrónico con Office 365.

Esta configuración se aplica a todos los conjuntos de pruebas o casos de prueba de la aplicación. Una vez completados todos los conjuntos de pruebas o casos de prueba, los resultados de las pruebas y los mensajes de seguimiento contenidos en las pruebas están disponibles en los registros **TestCaseResult** y **TestSuiteResult**.

El registro **TestCaseResult** contiene las siguientes propiedades:

- *TestCaseName*: el nombre del caso de prueba.
- *TestCaseId*: el identificador del caso de prueba.
- *TestSuiteName*: el nombre del conjunto de pruebas al que pertenece el caso.
- *TestSuiteId*: el identificador del conjunto de pruebas al que pertenece el caso.
- *StartTime*: el tiempo de inicio de la ejecución de la prueba.
- *EndTime*: el tiempo de finalización de la ejecución de la prueba.
- *Traces*: el resultado de cualquier aserción de prueba y cualquier mensaje de la función de Seguimiento.
- *Success*: indica si el caso de prueba se ha completado correctamente.
- *TestFailureMessage*: si se produce un error en el caso, este es el mensaje de error.

El registro **TestSuiteResult** contiene las siguientes propiedades: 

- *TestSuiteName*: el nombre del conjunto de pruebas.
- *TestSuiteId*: el identificador del conjunto de pruebas.
- *StartTime*: el tiempo de inicio de la ejecución del conjunto de pruebas.
- *EndTime*: el tiempo de finalización de la ejecución del conjunto de pruebas.
- *TestsPassed*: el número de casos de prueba que se completaron correctamente en el conjunto.
- *TestsFailed*: el número de casos de prueba que no se completaron correctamente en el conjunto.

En esta guía de inicio rápido, creará dos entidades personalizadas en la base de datos Common Data Service para almacenar los resultados de pruebas mediante la personalización de las propiedades **OnTestCaseComplete** y **OnTestSuiteComplete**:

1. Haga clic en **Prueba** en el panel izquierdo o haga clic en **Vista** en el encabezado del conjunto.

    ![Conjunto de propiedades de prueba o vista](./media/working-with-test-studio/test-or-view-to-set-property.png)

2. Seleccione la acción **OnTestCaseComplete**.

3. Escriba una expresión para procesar los resultados de la prueba. En el ejemplo siguiente se guardan los resultados de cada caso de prueba en la entidad AppTestResults personalizada de Common Data Service. Los resultados de pruebas se pueden almacenar opcionalmente en SQL, SharePoint o cualquier otro origen de datos. Es posible que tenga que establecer o aumentar el campo de Seguimiento en el origen de datos según sea necesario.

    > [!NOTE]
    > Los ejemplos siguientes requieren una [conexión a Common Data Service](https://docs.microsoft.com/connectors/commondataservice/). Puede crear una [aplicación sencilla](data-platform-create-app.md) o [compilar una aplicación desde cero](data-platform-create-app-scratch.md) con Common Data Service. Consulte también la referencia de funciones de [Parche](./functions/function-patch.md) para obtener más información para modificar los registros de un origen de datos usado en los siguientes ejemplos.

    ```
    //Save to Common Data Service
    Patch(AppTestResults
    , Defaults(AppTestResults)
    , {
             TestPass: TestCaseResult.TestCaseName & ":" & Text(Now())
             ,TestSuiteId: TestCaseResult.TestSuiteId
             ,TestSuiteName: TestCaseResult.TestSuiteName
             ,TestCaseId: TestCaseResult.TestCaseId
             ,TestCaseName: TestCaseResult.TestCaseName
             ,StartTime: TestCaseResult.StartTime
             ,EndTime: TestCaseResult.EndTime
             ,TestSuccess: TestCaseResult.Success
             ,TestTraces: JSON(TestCaseResult.Traces)
             ,TestFailureMessage: TestCaseResult.TestFailureMessage
    }
    );
    ```
    ![OnTestCaseComplete example.png](./media/working-with-test-studio/ontestcasecomplete-example.png)

4. Seleccione la acción **OnTestCaseComplete**.

5. Escriba una expresión para procesar los resultados de la prueba. En el ejemplo siguiente se guardan los resultados de cada conjunto de pruebas en la entidad AppTestResults personalizada de Common Data Service. 

    ```
    //Save to Common Data Service
    Patch(AppTestSuiteResults
        , Defaults(AppTestSuiteResults)
        , {
             TestSuiteId: TestSuiteResult.TestSuiteId
             ,TestSuiteName: TestSuiteResult.TestSuiteName
             ,StartTime: TestSuiteResult.StartTime
             ,EndTime: TestSuiteResult.EndTime
             ,TestPassCount: TestSuiteResult.TestsPassed
             ,TestFailCount: TestSuiteResult.TestsFailed
        }
    );
    ```

    ![OnTestSuiteComplete example.png](./media/working-with-test-studio/ontestsuitecomplete-example.png)

Otro ejemplo de expresiones que podría usar en estas propiedades es:

- Envío de resultados a un flujo en Power Automate.

    ```MyTestResultsFlow.Run(JSON(TestCaseResult))```

- Envío por correo electrónico de los resultados:

    ```Office365.SendMailV2("someone@example.com"; "Test case results"; JSON(TestCaseResult; JSONFormat.IndentFour))```

- Recepción de una notificación de la aplicación del resultado de la prueba:

  Por ejemplo, reciba una notificación una vez que se complete la prueba al reproducirla en un explorador, fuera de Test Studio.

    ```
    Notify(TestCaseResult.TestCaseName & " : "
            & If( TestCaseResult.Success
                , " Passed"
                , TestCaseResult.TestFailureMessage)
            ,If(  TestCaseResult.Success
                , NotificationType.Success
                , NotificationType.Error)
    )
    ```

## <a name="test-functions"></a>Funciones de prueba

Además de las [funciones](formula-reference.md) disponibles en Power Apps, a continuación se indican las funciones comunes que se suelen usar al crear pruebas.

- [Seleccionar](./functions/function-select.md)
- [SetProperty](./functions/function-setproperty.md)
- [Declarar](./functions/function-assert.md)
- [Seguimiento](./functions/function-trace.md)

## <a name="next-steps"></a>Pasos siguientes

- [Automatización de pruebas con el editor clásico de canalización de Azure DevOps](test-studio-classic-pipeline-editor.md)