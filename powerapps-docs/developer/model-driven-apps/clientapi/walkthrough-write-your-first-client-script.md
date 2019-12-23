---
title: 'Tutorial: Escribir el primer script de cliente en aplicaciones basadas en modelos| MicrosoftDocs'
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: conceptual
applies_to: Dynamics 365 (online)
ms.assetid: 73dfc13c-a18c-42fc-b511-a37896c2f893
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9b9936cccd243213f785cf65b7dc2d94cfaa1763
ms.sourcegitcommit: 64d816a759c5cc6343928d56a673812c3ea066c2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/06/2019
ms.locfileid: "2895134"
---
# <a name="walkthrough-write-your-first-client-script"></a>Tutorial: Escribir el primer script de cliente

Listo para escribir su primer script de cliente para ver las cosas en acción. Empecemos; lo haremos sencillo.

## <a name="objective"></a>Objetivo

Después de finalizar este tutorial, sabrá cómo utilizar el código JavaScript en aplicaciones basadas en modelos, lo que implica los pasos siguientes a un nivel alto:

- Escriba el código JavaScript para solucionar un problema del negocio
- Cargue el código JavaScript como un recursos web en aplicaciones basadas en modelos
- Asocie las funciones de JavaScript en el recursos web a los distintos eventos del lado del cliente en aplicaciones basadas en modelos.

Llamaremos su atención sobre hechos importantes durante el tutorial y proporcionaremos referencias a métodos reales según corresponda.

## <a name="step-1-write-your-custom-javascript-code"></a>Paso 1: Escribir el código JavaScript personalizado

El primer paso es identificar el problema del negocio que intenta abordar usando el scripting del cliente. Una vez que lo haya identificado, debe escribir el código JavaScript que contiene la lógica de negocios personalizada que trata su problema del negocio. 

Las aplicaciones basadas en modelo no proporcionan un editor de JavaScript. Por lo tanto, puede usar una herramienta de creación externa que proporciona características específicamente para la edición de archivos JavaScript, como [Notepad++](https://notepad-plus-plus.org/), [código de Visual Studio](https://code.visualstudio.com/docs/languages/javascript) o [Microsoft Visual Studio](https://docs.microsoft.com/scripting/javascript/).

Puede revisar el código de ejemplo completo que se utiliza en el tutorial más adelante en este tema.

Veamos el código detalladamente:
 
### <a name="detailed-code-explanation"></a>Explicación detallada del código

- **Defina el espacio de nombres**: el código comienza definiendo un espacio de nombres de su script personalizado. Como práctica recomendada, siempre debe crear bibliotecas JavaScript con espacio de nombres para evitar que sus funciones sean reemplazadas por funciones en otra biblioteca.

    ```JavaScript
    var Sdk = window.Sdk || {};
    ``` 
    En este caso, todas las funciones definidas en esta biblioteca se pueden usar como `Sdk.[functionName]`.

- **Definir variables globales**: la siguiente sección define algunas variables globales que se usan en el script. Tenga en cuenta que ya no es necesario pasar por el contexto de formulario para obtener el nombre del usuario. La información de contexto está ahora disponible de forma global mediante el método **Xrm.Utility.**[getGlobalContext](reference/xrm-utility/getGlobalContext.md).

    ```JavaScript
    // Define some global variables
    var myUniqueId = "_myUniqueId"; // Define an ID for the notification
    var currentUserName = Xrm.Utility.getGlobalContext().userSettings.userName; // get current user name
    var message = currentUserName + ": Your JavaScript code in action!";
    ```
- **Código que se ejecuta en el evento OnLoad**: esta sección contiene el código que se ejecutará cuando se cargue el formulario de cuenta. Por ejemplo, cuando se crea un nuevo registro de cuenta o al abrir un registro de cuenta existente.

    El código utiliza el objeto `executionContext`para obtener el objeto `formContext`. Cuando conectemos más adelante nuestro código al evento de formulario, no olvidaremos seleccionar la opción de pasar el [contexto de ejecución](clientapi-execution-context.md) a esta función. A continuación, mostramos una notificación de nivel de formulario mediante el método [setFormNotification](reference/formContext-ui/setFormNotification.md). A continuación, usamos el método **setTimeOut** para retardar la ejecución del método [clearFormNotification](reference/formContext-ui/clearFormNotification.md) para eliminar la notificación después de 5 segundos.

    ```JavaScript
    // Code to run in the form OnLoad event
    this.formOnLoad = function (executionContext) {
        var formContext = executionContext.getFormContext();

        // display the form level notification as an INFO
        formContext.ui.setFormNotification(message, "INFO", myUniqueId);
        
        // Wait for 5 seconds before clearing the notification
        window.setTimeout(function () { formContext.ui.clearFormNotification(myUniqueId); }, 5000);        
    }
    ```
- **Código que se ejecuta en el evento OnChange**: el código de esta sección se asociará al campo **Nombre de cuenta** en el formulario de cuenta para que se ejecute **solo** si cambia el valor del nombre de cuenta.

    El código realiza una búsqueda sin distinción entre mayúsculas y minúsculas de "Contoso" en el nombre de la cuenta y, si lo encuentra, establece automáticamente valores para algunos campos en el formulario de cuenta.

    ```JavaScript
    // Code to run in the attribute OnChange event 
    this.attributeOnChange = function (executionContext) {
        var formContext = executionContext.getFormContext();

        // Automatically set some field values if the account name contains "Contoso"
        var accountName = formContext.getAttribute("name").getValue();
        if (accountName.toLowerCase().search("contoso") != -1) {
            formContext.getAttribute("websiteurl").setValue("https://www.contoso.com");
            formContext.getAttribute("telephone1").setValue("425-555-0100");
            formContext.getAttribute("description").setValue("Website URL, Phone and Description set using custom script.");
        }
    }
    ```

- **Código que se ejecuta en el evento OnSave**: el código de esta sección muestra un cuadro de diálogo de alerta mediante el método [openAlertDialog](reference/xrm-navigation/openalertdialog.md). Este cuadro de diálogo muestra un mensaje con el botón **Aceptar**; el usuario puede cerrar la alerta haciendo clic en **Aceptar**.

    Tenga en cuenta que no estamos pasando el contexto de ejecución de esta función ya que no es necesario para ejecutar métodos **Xrm.Utility.***. 

    ```JavaScript
    // Code to run in the form OnSave event 
    this.formOnSave = function () {
        // Display an alert dialog
        Xrm.Navigation.openAlertDialog({ text: "Record saved." });
    }
    ```

## <a name="step-2-add-your-javascript-code-in-a-script-web-resource"></a>Paso 2: Agregar el código JavaScript en un recurso web del Script

Ahora que el código está listo, debe asociarlo a eventos en aplicaciones basadas en modelos. Puede utilizar [recursos web del Script](../script-jscript-web-resources.md) en aplicaciones basadas en modelos para cargar el script en su instancia de aplicaciones basadas en modelos y luego asociarla a eventos.

1. Vaya a su instancia de aplicaciones basadas en modelos en el explorador y vaya a **Configuración** > **Personalizaciones**.
2. En el área Personalización, seleccione **Personalización del sistema**.
3. En el explorador de soluciones en **Componentes**, elija **Recursos web**.  
4. Elija **Nuevo** para crear un recurso web.
5. En el nuevo diálogo de recurso web, especifique el **Nombre** y **Nombre para mostrar** para su recurso web. Por ejemplo: "mySampleScript.js" y script "Ejemplo: tutorial". 
6. Seleccione **Script (JScript)** de la lista desplegable **Tipo**. Puede cargar un archivo que contiene el código JavaScript seleccionando **Elegir archivo**, o seleccionar **Editor de texto** y luego pegar el código JavaScript en el editor.
    ![Crear recurso web](../media/clientapi_walkThrough-img1.png)
1. Elija **Guardar** para crear el recurso web que contiene el código JavaScript.
2. Elija **Publicar** para publicar su recurso web.

## <a name="step-3-associate-script-web-resource-to-a-form"></a>Paso 3: Asociar recurso web del Script a un formulario

Asocie el recurso web que contiene el código JavaScript a formularios de aplicaciones basadas en modelos para poder asociar funciones en su código con eventos. Puesto que el código JavaScript de este tutorial se dirige al registro de cuenta, asociaremos el recurso web al formulario de cuenta.

1. Vaya a su instancia de aplicaciones basadas en modelos en el explorador y vaya a **Ventas** > **Cuentas** o **Servicio** > **Cuentas**.
2. Abra un registro de cuenta y seleecione **Formulario** para abrir el editor de formularios.

    ![Abrir el editor de formularios](../media/clientapi_walkThrough-img2.png)
1. En el editor de formularios, seleccione **Propiedades del formulario**.
2. En el cuadro de diálogo **Propiedades del formulario**, en la pestaña **Eventos**, haga clic en **Agregar** para buscar y agregar su recurso web.

    ![Agregar](../media/clientapi_walkThrough-img3.png)
1. En el cuadro de diálogo siguiente, busque el nombre de su recurso web, selecciónelo y haga clic en **Agregar** para agregarlo como una biblioteca de JavaScript para el formulario de cuenta.

    ![Buscar registro](../media/clientapi_walkThrough-img4.png)

Esto hace que el recurso web esté disponible para su selección en la sección **Controladores de eventos** en el diálogo **Propiedades del formulario**. Recuerde que tenemos tres funciones en nuestro código JavaScript para asociarlas a eventos adecuados en el formulario.

1. En la sección **Controladores de eventos**, seleccione **Formulario** como en control y **OnLoad** como el **Evento**; haga clic en **Agregar** para agregar un controlador de eventos para el evento OnLoad.

   ![Formulario OnLoad](../media/clientapi_walkThrough-img5.png)
1. En el cuadro de diálogo **Propiedades del controlador**:   

    - Seleccione el nombre de su recursos web desde la lista desplegable **Biblioteca** y especifique **Sdk.formOnLoad** en el campo **Función**. El nombre de la función es [Namespace].[Function] desde el código JavaScript.
    - Seleccione **Pasar el contexto de ejecución como primer parámetro** para pasar el contexto de ejecución como parámetro a esta función. Si revisa la definición de función en el código, estamos pasando un objeto **executionContext** a nuestra defición de función, y seleccionando esta opción los conecta.
    
      ![Formulario OnLoad](../media/clientapi_walkThrough-img6.png)

1. Haga clic en **Aceptar** para volver el cuadro de diálogo **Propiedades del formulario**.
2. En la sección **Controladores de eventos**, seleccione esta vez **OnSave** como el **Evento** y haga clic en **Agregar** para agregar un controlador de eventos para el evento del formulario OnSave.

    ![Formulario OnSave](../media/clientapi_walkThrough-img7.png)

1. En el cuadro de diálogo **Propiedades del controlador**, seleccione el nombre de su recurso web desde la lista desplegable **Biblioteca** y especifique **Sdk.formOnSave** en el campo **Función**. Esta vez no pasaremos el contexto de ejecución a la función ya que el código de función **Sdk.formOnSave** no lo requiere.

    ![Formulario OnSave](../media/clientapi_walkThrough-img8.png)

1. Haga clic en **Aceptar** para volver el cuadro de diálogo **Propiedades del formulario**.
2. En la sección **Controladores de eventos**, seleccione **Nombre de cuenta** como el control y **OnChange** como el evento; haga clic en **Agregar** para agregar un controlador de eventos para el evento OnChange.

    ![Formulario OnSave](../media/clientapi_walkThrough-img9.png)

1. En el cuadro de diálogo **Propiedades del controlador**:   

    - Seleccione el nombre de su recursos web desde la lista desplegable **Biblioteca** y especifique **Sdk.attributeOnChange** en el campo **Función**.
    - Seleccione **Pasar el contexto de ejecución como primer parámetro** para pasar el contexto de ejecución como parámetro a esta función. Si revisa la definición de función en el código, estamos pasando un objeto **executionContext** a nuestra defición de función, y seleccionando esta opción los conecta.
    
      ![Atributo OnChange](../media/clientapi_walkThrough-img10.png) 
1. Haga clic en **Aceptar** para volver el cuadro de diálogo **Propiedades del formulario**.
2. Haga clic en **Aceptar** en el cuadro de diálogo **Propiedades del formulario** para volver al editor de formularios.
3. Haga clic en **Guardar** para guardar los cambios en el formulario.
4. Haga clic en **Publicar** para publicar los cambios del formulario.

¡Eso es! Ha completado los pasos para configurar el formulario de cuenta para usar la lógica de negocios personalizada especificada en el código JavaScript.

## <a name="test-your-javascript-code"></a>Pruebe el código JavaScript

Se recomienda que actualice el explorador para que se apliquen los cambios en su instancia de aplicaciones basadas en modelos. Para probar la lógica de negocios personalizada que configuró en este tutorial:

1. Inicie sesión en la instancia de aplicaciones basadas en modelos.
2. Vaya a **Cuentas**e intente abrir o crear una cuenta nueva. En este caso, se abrirá una cuenta existente para cargar el formulario de cuenta. Verá una notificación con su nombre de usuario que desaparecerá automáticamente en 5 segundos.

      ![Notificación en el nivel del formulario](../media/clientapi_walkThrough-img11.png)

1. Edite el nombre de la cuenta para agregar "Contoso" en el nombre y vaya al campo siguiente presionando TAB. Esto desencadenará el evento OnChange y actualizará automáticamente los campos **Teléfono**, **Sitio Web** y **Descripción** con el valor especificado en el código.

      ![Valores se establecen automáticamente](../media/clientapi_walkThrough-img12.png)

1. Por último, al hacer clic en **Guardar** se desencadenará el evento OnSave y aparecerá el diálogo de alerta con un mensaje que configuró en el código. Haga clic en **Aceptar** para cerrar la alerta.

      ![Diálogo de alerta](../media/clientapi_walkThrough-img13.png)

## <a name="complete-sample-code-used-in-the-walkthrough"></a>Complete el código de ejemplo que se utiliza en el tutorial

```JavaScript
// A namespace defined for the sample code
// As a best practice, you should always define 
// a unique namespace for your libraries
var Sdk = window.Sdk || {};
(function () {
    // Define some global variables
    var myUniqueId = "_myUniqueId"; // Define an ID for the notification
    var currentUserName = Xrm.Utility.getGlobalContext().userSettings.userName; // get current user name
    var message = currentUserName + ": Your JavaScript code in action!";

    // Code to run in the form OnLoad event
    this.formOnLoad = function (executionContext) {
        var formContext = executionContext.getFormContext();

        // display the form level notification as an INFO
        formContext.ui.setFormNotification(message, "INFO", myUniqueId);

        // Wait for 5 seconds before clearing the notification
        window.setTimeout(function () { formContext.ui.clearFormNotification(myUniqueId); }, 5000);
    }

    // Code to run in the attribute OnChange event 
    this.attributeOnChange = function (executionContext) {
        var formContext = executionContext.getFormContext();

        // Automatically set some field values if the account name contains "Contoso"
        var accountName = formContext.getAttribute("name").getValue();
        if (accountName.toLowerCase().search("contoso") != -1) {
            formContext.getAttribute("websiteurl").setValue("https://www.contoso.com");
            formContext.getAttribute("telephone1").setValue("425-555-0100");
            formContext.getAttribute("description").setValue("Website URL, Phone and Description set using custom script.");
        }
    }

    // Code to run in the form OnSave event 
    this.formOnSave = function () {
        // Display an alert dialog
        Xrm.Navigation.openAlertDialog({ text: "Record saved." });
    }
}).call(Sdk);
```
