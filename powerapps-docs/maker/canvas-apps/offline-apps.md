---
title: Desarrollar aplicaciones de lienzo que puedan ejecutarse sin conexión | Microsoft Docs
description: Desarrolle aplicaciones de lienzo que puedan ejecutarse sin conexión para que los usuarios sean productivos, independientemente de la conexión.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/31/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1dbf192664f2c8a812650b487a9931de0160eeab
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74675532"
---
# <a name="develop-offline-capable-canvas-apps"></a>Desarrollo de aplicaciones de lienzo que puedan ejecutarse sin conexión

Los usuarios móviles a menudo necesitan ser productivos, incluso cuando tienen conectividad limitada. Al compilar una aplicación de lienzo, puede realizar estas tareas:

- Abra Power apps Mobile y ejecute aplicaciones sin conexión.
- Determinar si una aplicación está sin conexión, en línea o en una conexión de uso medido mediante el objeto de señal [conexión](../canvas-apps/functions/signals.md#connection).
- Usar [colecciones](../canvas-apps/create-update-collection.md) y aprovechar funciones como [LoadData y SaveData](../canvas-apps/functions/function-savedata-loaddata.md) para el almacenamiento de datos básico cuando esté sin conexión.

## <a name="limitations"></a>Límite

**LoadData** y **savedata** se combinan para formar un mecanismo sencillo para almacenar pequeñas cantidades de datos en un dispositivo local. Mediante el uso de estas funciones, puede agregar funcionalidades sin conexión sencillas a la aplicación.

Estas funciones están limitadas por la cantidad de memoria de la aplicación disponible, ya que operan en una colección en memoria. La memoria disponible puede variar en función del dispositivo, el sistema operativo, la memoria que usa Power apps Mobile y la complejidad de la aplicación en términos de pantallas y controles. Si almacena más de unos megabytes de datos, pruebe la aplicación con los escenarios esperados en los dispositivos en los que espera que se ejecute. Generalmente tendrá 30-70 megabytes de memoria disponible.

Las funciones tampoco resuelven automáticamente los conflictos de combinación cuando un dispositivo entra en línea. La configuración de los datos que se guardan y el modo de controlar la reconexión depende del creador al escribir expresiones.

Para las actualizaciones de funcionalidades sin conexión, vuelva a este tema y suscríbase al [blog de Power apps](https://powerapps.microsoft.com/blog/).

## <a name="overview"></a>Información general

Al diseñar escenarios sin conexión, primero debe considerar cómo funcionan las aplicaciones con los datos. Las aplicaciones de Power apps acceden principalmente a los datos a través de un conjunto de [conectores](../canvas-apps/connections-list.md) que proporciona la plataforma, como SharePoint, Office 365 y Common Data Service. También puede crear conectores personalizados que permiten a las aplicaciones tener acceso a cualquier servicio que proporcione un punto de conexión REST. Podría tratarse de una API web o un servicio como Azure Functions. Todos estos conectores usan HTTPS a través de Internet, lo que significa que los usuarios deben estar en línea para acceder a los datos y otras funcionalidades que ofrece un servicio.

![Aplicación de Power apps con conectores](./media/offline-apps/online-app.png)

### <a name="handling-offline-data"></a>Administrar datos sin conexión

En Power Apps, puede filtrar, buscar, ordenar, agregar y manipular los datos de una manera coherente independientemente del origen de datos. Los orígenes van desde las colecciones en memoria de la aplicación a las listas de SharePoint a las bases de datos SQL y Common Data Service. Debido a esta coherencia, puede redestinar fácilmente una aplicación para que use un origen de datos diferente. Lo que es más importante para los escenarios sin conexión, puede usar colecciones locales para la administración de datos sin apenas realizar cambios en la lógica de la aplicación. De hecho, las colecciones locales son el mecanismo principal para administrar datos sin conexión.

## <a name="build-an-offline-app"></a>Compilar una aplicación sin conexión

Para mantener el foco en los aspectos sin conexión del desarrollo de aplicaciones, en este tema se muestra un escenario sencillo centrado en Twitter. Creará una aplicación que le permite leer publicaciones de Twitter y enviar tweets mientras está sin conexión. Cuando la aplicación se conecta, la aplicación envía los tweets y vuelve a cargar los datos locales.

En un nivel alto, la aplicación realiza estas tareas:

- Cuando el usuario abre la aplicación:

  - Si el dispositivo está en línea, la aplicación captura los datos a través del conector de Twitter y rellena una colección con esos datos.
  - Si el dispositivo está sin conexión, la aplicación carga los datos de un archivo caché local mediante la función [**LoadData**](../canvas-apps/functions/function-savedata-loaddata.md) .
  - El usuario puede enviar tweets. Si la aplicación está en línea, envía los tweets directamente a Twitter y actualiza la memoria caché local.

- Cada cinco minutos mientras la aplicación está en línea:

  - La aplicación envía los tweets en la memoria caché local.
  - La aplicación actualiza la memoria caché local y la guarda mediante la función [**savedata**](../canvas-apps/functions/function-savedata-loaddata.md) .

### <a name="step-1-add-twitter-to-a-blank-phone-app"></a>Paso 1: agregar Twitter a una aplicación de teléfono en blanco

1. En Power apps Studio, seleccione **archivo** > **nuevo**.
1. En el icono **Aplicación vacía**, seleccione **Diseño de teléfono**.
1. En la pestaña **Vista**, seleccione **Orígenes de datos**.
1. En el panel **datos** , seleccione **Agregar origen de datos**.
1. Seleccione **nueva conexión** > **Twitter** > **crear**.
1. Escriba sus credenciales, cree la conexión y, a continuación, cierre el panel **datos** .

### <a name="step-2-collect-existing-tweets"></a>Paso 2: recopilar tweets existentes

1. En el panel **vista de árbol** , seleccione **aplicación**y, a continuación, establezca su propiedad **OnStart** en esta fórmula:

    ```powerapps-dot
    If( Connection.Connected,
        ClearCollect( LocalTweets, Twitter.SearchTweet( "PowerApps", {maxResults: 10} ) );
            Set( statusText, "Online data" ),
        LoadData( LocalTweets, "LocalTweets", true );
            Set( statusText, "Local data" )
    );
    SaveData( LocalTweets, "LocalTweets" );
    ```

    > [!div class="mx-imgBorder"]
    > ![fórmula para cargar tweets](./media/offline-apps/load-tweets.png)

1. En el panel de **vista de árbol** , seleccione el menú de puntos suspensivos para el objeto de **aplicación** y, a continuación, seleccione **Ejecutar OnStart** para ejecutar esa fórmula.

    > [!div class="mx-imgBorder"]
    > ![ejecutar la fórmula para cargar tweets](./media/offline-apps/load-tweets-run.png)

    > [!NOTE]
    > Las funciones **LoadData** y **savedata** pueden mostrar un error en Power apps Studio porque los exploradores no las admiten. Sin embargo, se realizarán normalmente después de implementar esta aplicación en un dispositivo.

Esta fórmula comprueba si el dispositivo está en línea:

- Si el dispositivo está en línea, la fórmula carga hasta 10 tweets con el término de búsqueda "PowerApps" en una colección **LocalTweets** .
- Si el dispositivo está sin conexión, la fórmula carga la memoria caché local desde un archivo llamado "LocalTweets" si está disponible.

### <a name="step-3-show-tweets-in-a-gallery"></a>Paso 3: Mostrar tweets en una galería

1. En la pestaña **Insertar** , seleccione **Galería** > **alto flexible en blanco**.

1. Establezca la propiedad **elementos** del control [**Galería**](controls/control-gallery.md) en `LocalTweets`.

1. En la plantilla Galería, agregue tres controles [**etiqueta**](controls/control-text-box.md) y establezca la propiedad **texto** de cada etiqueta en uno de estos valores:

    - `ThisItem.UserDetails.FullName & " (@" & ThisItem.UserDetails.UserName & ")"`
    - `Text(DateTimeValue(ThisItem.CreatedAtIso), DateTimeFormat.ShortDateTime)`
    - `ThisItem.TweetText`

1. Haga que el texto de la última etiqueta esté en negrita para que la galería se asemeje a este ejemplo.

    > [!div class="mx-imgBorder"]
    > ![galería que muestra tweets de ejemplo](./media/offline-apps/tweet-gallery.png)

### <a name="step-4-show-connection-status"></a>Paso 4: mostrar el estado de la conexión

1. En la galería, inserte una etiqueta y establezca su propiedad **color** en **rojo**.

1. Establezca la propiedad **texto** de la etiqueta más reciente en esta fórmula:

    `If( Connection.Connected, "Connected", "Offline" )`

Esta fórmula determina si el dispositivo está en línea. Si es así, la etiqueta muestra **conectado**; de lo contrario, se muestra **sin conexión**.

### <a name="step-5-add-a-box-to-compose-tweets"></a>Paso 5: agregar un cuadro para componer tweets

1. En la etiqueta conexión-estado, inserte un control [**entrada de texto**](controls/control-text-input.md) y cambie el nombre por **NewTweetTextInput**.

1. Establezca la propiedad **predeterminada** del cuadro de entrada de texto en `""`.

    > [!div class="mx-imgBorder"]
    > ![la galería sobre la información de estado y el cuadro de entrada de texto](./media/offline-apps/status-input.png)

### <a name="step-6-add-a-button-to-post-the-tweet"></a>Paso 6: agregar un botón para publicar el tweet

1. En el cuadro de entrada de texto, agregue un control de **botón** y establezca su propiedad **texto** en este valor:

    `"Tweet"`

1. Establezca la propiedad **alseleccionar** del botón en esta fórmula:

    ```powerapps-dot
    If( Connection.Connected,
        Twitter.Tweet( "", {tweetText: NewTweetTextInput.Text} ),
        Collect( LocalTweetsToPost, {tweetText: NewTweetTextInput.Text} );
            SaveData( LocalTweetsToPost, "LocalTweetsToPost" )
    );
    Reset( NewTweetTextInput );
    ```  

1. En la propiedad **OnStart** de la **aplicación**, agregue una línea al final de la fórmula:

    ```powerapps-dot
    If( Connection.Connected,
        ClearCollect( LocalTweets, Twitter.SearchTweet( "PowerApps", {maxResults: 100} ) );
            Set( statusText, "Online data" ),
        LoadData( LocalTweets, "LocalTweets", true );
            Set( statusText, "Local data" )
    );
    SaveData( LocalTweets, "LocalTweets" );
    LoadData( LocalTweetsToPost, "LocalTweetsToPost", true );  // added line
    ```

    > [!div class="mx-imgBorder"]
    > ![ejecutar la fórmula para cargar tweets con una línea sin comentarios](./media/offline-apps/load-tweets-save.png)

Esta fórmula determina si el dispositivo está en línea:

- Si el dispositivo está en línea, lo envía inmediatamente.
- Si el dispositivo está sin conexión, captura el tweet en una colección **LocalTweetsToPost** y lo guarda en el dispositivo.

A continuación, la fórmula restablece el texto en el cuadro de entrada de texto.

### <a name="step-7-check-for-new-tweets"></a>Paso 7: comprobar si hay nuevos tweets

1. En el lado derecho del botón, agregue un control **Timer** .

    > [!div class="mx-imgBorder"]
    > ![aplicaciones finales](./media/offline-apps/final-app.png)

1. Establezca la propiedad **duración** del temporizador en **300000**.

1. Establezca las propiedades **Inicio automático** y **repetir** del temporizador en **true**.

1. Establezca el **alfinalizartemporizador** del temporizador en esta fórmula:

    ```powerapps-dot
    If( Connection.Connected,
        ForAll( LocalTweetsToPost, Twitter.Tweet( "", {tweetText: tweetText} ) );
        Clear( LocalTweetsToPost );
        ClearCollect( LocalTweets, Twitter.SearchTweet( "PowerApps", {maxResults: 10} ) );
        SaveData( LocalTweets, "LocalTweets" );
   )
    ```

Esta fórmula determina si el dispositivo está en línea. Si es así, la aplicación Tweet todos los elementos de la colección **LocalTweetsToPost** y, a continuación, borra la colección.

## <a name="test-the-app"></a>Probar la aplicación

1. Abra la aplicación en un dispositivo móvil que esté conectado a Internet.

    Los tweets existentes aparecen en la galería y el estado muestra **conectado**.

1. Desconecte el dispositivo de Internet habilitando el modo de avión del dispositivo y deshabilitando Wi-Fi.

    La etiqueta estado muestra que la aplicación está **sin conexión**.

1. Mientras el dispositivo está sin conexión, escriba un Tweet que incluya **PowerApps**y, después, seleccione el botón **Tweet** .

    El tweet se almacena localmente en la colección **LocalTweetsToPost** .

1. Vuelva a conectar el dispositivo a Internet deshabilitando el modo de avión del dispositivo y habilitando Wi-Fi.

    En un plazo de cinco minutos, la aplicación envía el tweet, que aparece en la galería.

Esperamos que este artículo le dé una idea de las funcionalidades que Power apps tiene para compilar aplicaciones sin conexión. Como siempre, proporcione sus comentarios en nuestro [Foro](https://powerusers.microsoft.com/t5/PowerApps-Forum/bd-p/PowerAppsForum1) y comparta sus ejemplos de aplicaciones sin conexión en el blog de la [comunidad de Power apps](https://powerusers.microsoft.com/t5/PowerApps-Community-Blog/bg-p/PowerAppsBlog).