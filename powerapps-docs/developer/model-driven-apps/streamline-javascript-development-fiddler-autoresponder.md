---
title: Desarrollo de recursos web de script script mediante Fiddler AutoResponder (aplicaciones basadas en modelos) | Microsoft Docs
description: Obtenga información sobre cómo configurar y utilizar AutoResponder en Fiddler para la depuración local de recursos de web JavaScript.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5c2a4a12834cbaabbe9d44639b73025f2380c4dd
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754561"
---
# <a name="script-web-resource-development-using-fiddler-autoresponder"></a>Desarrollo de recursos web de script con Fiddler AutoResponder

Al desarrollar y depurar recursos web de JavaScript, puede usar AutoResponder en [Telerik Fiddler](https://www.telerik.com/fiddler) para reemplazar el contenido de un recurso web con el contenido de un archivo local en lugar de cargarlo en su instancia de aplicaciones basadas en modelos y publicarlo cada vez. Use los pasos siguientes para configurar AutoResponder en Fiddler.

## <a name="install-and-configure-fiddler"></a>Instale y configure Fiddler

1. [Descargar](https://www.telerik.com/download/fiddler) e instalar Fiddler.
1. Abra Fiddler y en la barra de menú, vaya a **herramientas**y seleccione **opciones**.
2. Seleccione la pestaña **HTTPS** en el cuadro de diálogo y active las casillas **capturar CONEXIONES HTTPS** y **Descifrar tráfico HTTPS** para que el tráfico HTTPS se capture y, después, se descifre.<br />
 ![Active las casillas marcadas en la ficha HTTP](media/fiddler-https-options.png "SActive las casillas marcadas en la ficha HTTP")</br>
3. Haga clic en **Aceptar** para cerrar el cuadro de diálogo.

> [!NOTE]
> Si es la primera vez que va a habilitar esta configuración, Fiddler le pedirá que instale un certificado. Instale el certificado y reinicie Fiddler para que la nueva configuración tenga efecto.<br />
> Si ha ejecutado Fiddler anteriormente y obtiene un error `NET::ERR_CERT_AUTHORITY_INVALID`, en la pestaña **HTTPS**, haga clic en el botón **acciones** y elija **restablecer todos los certificados**. Esto también hará que se presenten varias solicitudes para que los nuevos certificados estén instalados.

## <a name="configure-autoresponder"></a>Configurar AutoResponder

1. Abra la página en la instancia de Dynamics 365 que desea depurar.
2. Inicie la captura de seguimiento de Fiddler haciendo clic en el botón **captura** de la esquina inferior izquierda.
   ![Haga clic en el botón de captura para iniciar la captura de tráfico HTTPS](media/fiddler-start-capturing.png "CHaga clic en el botón de captura para iniciar la captura de tráfico HTTPS")</br>

   > [!NOTE]
   > Si desea capturar tráfico HTTPS solo de un determinado host, en la ficha **filtros**, en el área **host**, en el menú desplegable **- ningún filtro de Host-** seleccione **Mostrar solo los siguientes hosts** en el menú y escriba la lista de dominios cuyo tráfico desea ver, separados por puntos y comas. Más información: [Referencia de filtros](https://docs.telerik.com/fiddler/KnowledgeBase/Filters).
   > ![Filtrar el tráfico que se muestra en la interfaz de usuario de Fiddler](media/fiddler-filter-traffic.png "FFiltrar el tráfico que se muestra en la interfaz de usuario de Fiddler")

3. Realice cualquier operación necesaria para cargar el script que prueba. Puede detener la captura, haciendo clic en el mismo botón **captura** de nuevo.
4. Seleccione las sesiones de registro de seguimiento en el panel izquierdo y busque el archivo para el que desee configurar AutoResponder.<br /> Por ejemplo, si el código que desea depurar está en un recurso web de JavaScript denominado `new_testscript.js`, utilice el botón **buscar** para abrir el cuadro de diálogo **buscar sesiones** y buscar el nombre del recurso Web. <br />![Encuentre una sesión en fiddler](media/fiddler-find-sessions.PNG)<br />Verá las filas que coinciden con sus criterios de búsqueda resaltadas en el panel izquierdo.
5. Seleccione dicha fila. En el panel derecho, seleccione la pestaña **AutoResponder**. <br /> ![Seleccionar la pestaña AutoResponder](media/fiddler-auto-responder.png)
6. En la pestaña **AutoResponder**, seleccione las casillas **habilitar reglas** y **acceso directo de solicitudes no coincidentes**.<br />
   ![Active las dos casillas resaltadas](media/fiddler-select-checkbox.png "SActive las dos casillas resaltadas")<br />
7. Asegúrese de tener aún la sesión relacionada con el archivo de destino seleccionada y haga clic en el botón **Agregar regla** de la sección **AutoResponder**. Esto agrega una nueva entrada en la tabla de reglas.<br />
   ![Agregar nueva regla](media/fiddler-add-rule.png "AAgregar nueva regla")
8. Cuando se selecciona la regla, el **Editor de reglas** de la parte inferior tiene la fila superior rellenada con la dirección URL de sesión relacionada con el archivo y con un prefijo de cadena del tipo `EXACT:`.<br />
   A continuación, puede editar la cadena que debe coincidir para simplificarla. Con recursos web, la dirección URL contendrá valores generados en la dirección URL o en una cadena de la consulta para asegurarse de que la última versión publicada se incluye en la respuesta. Probablemente verá que el valor `EXACT` tendrá un aspecto como el siguiente:<br />
    ```
    EXACT:https://<org URL>/%7B636556138760000160%7D/WebResources/new_testscript.js?    ver=-1229805553
    ```<br />
    You can simplify this to remove the generated values and use this instead:<br />
    ```
    /WebResources/new_testscript.js
    ```<br />
   The bottom row is left blank. Type the path to your local file on your disk on this bottom row and <strong>Save</strong>.<br />
   ![Add path to your local file in Rule editor](media/fiddler-save-rule.png "Add path to your local file in Rule editor")<br />

 

 
By following the above steps, Fiddler is configured to listen to the requests and responds with the local file instead of passing the request over the network.

## Update and test your code

1. Apply changes to your local file.
2. Start Fiddler trace capture again and go back to your browser and hard reload the page with empty cache.
3. In the browser developer tools you can see that the file that is now received will be the local one.
4. Continue repeating this process while updating your code until you get the results you require.


## See Also

[Web resources](web-resources.md)<br />
[Client scripting using JavaScript](client-scripting.md)
