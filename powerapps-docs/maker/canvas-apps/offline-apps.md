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
ms.openlocfilehash: 8004a39e83ea3615ce8a77637a9f5c0271b67781
ms.sourcegitcommit: 157ab15738e2d0d1bf9097bbb7b9e3d9c29a4015
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2019
ms.locfileid: "66265699"
ms.PowerAppsDecimalTransform: true
---
# <a name="develop-offline-capable-canvas-apps"></a>Desarrollo de aplicaciones de lienzo que puedan ejecutarse sin conexión

Los usuarios móviles a menudo necesitan ser productivo incluso cuando tienen limitado o sin conexión. Al compilar una aplicación de lienzo, puede realizar estas tareas:

- Abra PowerApps Mobile y ejecutar aplicaciones sin conexión.
- Determinar si una aplicación está sin conexión, en línea o en una conexión de uso medido mediante el objeto de señal [conexión](../canvas-apps/functions/signals.md#connection).
- Usar [colecciones](../canvas-apps/create-update-collection.md) y aprovechar funciones como [LoadData y SaveData](../canvas-apps/functions/function-savedata-loaddata.md) para el almacenamiento de datos básico cuando esté sin conexión.

## <a name="limitations"></a>Limitaciones

**LoadData** y **SaveData** se combinan para formar un mecanismo sencillo para almacenar pequeñas cantidades de datos en un dispositivo local. Mediante el uso de estas funciones, puede agregar capacidades sin conexión sencillas a la aplicación.

Estas funciones están limitadas por la cantidad de memoria de la aplicación disponible, ya que operan en una colección en memoria. Memoria disponible puede variar en función del dispositivo, el sistema operativo, la memoria que usa PowerApps Mobile y la complejidad de la aplicación en cuanto a las pantallas y controles. Si almacena más de unos cuantos megabytes de datos, pruebe la aplicación con los escenarios esperados en los dispositivos en el que se espera que se ejecute. Generalmente tendrá 70-30 megabytes de memoria disponible.

Las funciones también no resuelven automáticamente los conflictos de combinación cuando un dispositivo está en línea. Configuración en los datos que se guardan y cómo controlar la reconexión es hasta el fabricante al escribir expresiones.

Para obtener actualizaciones de capacidades sin conexión, vuelva a este tema y suscribirse a la [blog de PowerApps](https://powerapps.microsoft.com/blog/).

## <a name="overview"></a>Información general

Al diseñar escenarios sin conexión, primero debe considerar cómo sus aplicaciones funcionan con datos. Aplicaciones en PowerApps principalmente a los datos mediante un conjunto de [conectores](../canvas-apps/connections-list.md) que ofrece la plataforma, como SharePoint, Office 365 y Common Data Service. También puede crear conectores personalizados que permiten a las aplicaciones tener acceso a cualquier servicio que proporcione un punto de conexión REST. Podría tratarse de una API web o un servicio como Azure Functions. Todos estos conectores usan HTTPS a través de Internet, lo que significa que los usuarios deben estar en línea para acceder a los datos y otras funcionalidades que ofrece un servicio.

![Aplicación de PowerApps con conectores](./media/offline-apps/online-app.png)

### <a name="handling-offline-data"></a>Administrar datos sin conexión

En PowerApps, puede filtrar, buscar, ordenar, agregar y manipular los datos de una manera coherente independientemente del origen de datos. Estos orígenes varían desde colecciones en memoria en la aplicación a listas de SharePoint para las bases de datos SQL y Common Data Service. Debido a esta coherencia, puede redirigir fácilmente una aplicación para usar un origen de datos diferente. Lo más importante para escenarios sin conexión, puede usar colecciones locales para la administración de datos casi sin cambios en la lógica de la aplicación. De hecho, las colecciones locales son el mecanismo principal para administrar datos sin conexión.

## <a name="build-an-offline-app"></a>Compilar una aplicación sin conexión

Para mantener el foco en los aspectos del desarrollo de aplicaciones sin conexión, en este tema se muestra un sencillo escenario centrado en Twitter. Va a crear una aplicación que le permite leer entradas de Twitter y enviar tweets mientras está sin conexión. Cuando la aplicación se conecta, la aplicación envía los tweets y vuelve a cargar los datos locales.

En un nivel alto, la aplicación lleva a cabo estas tareas:

- Cuando el usuario abre la aplicación:

  - Si el dispositivo está en línea, la aplicación captura los datos a través del conector de Twitter y rellena una colección con esos datos.
  - Si el dispositivo está sin conexión, la aplicación carga los datos de un archivo de caché local mediante el uso de la [ **LoadData** ](../canvas-apps/functions/function-savedata-loaddata.md) función.
  - El usuario puede enviar tweets. Si la aplicación está en línea, envía los tweets directamente a Twitter y actualiza la caché local.

- Cada cinco minutos, mientras la aplicación está en línea:

  - La aplicación envía los tweets en la memoria caché local.
  - La aplicación actualiza la caché local y se guarda con el [ **SaveData** ](../canvas-apps/functions/function-savedata-loaddata.md) función.

### <a name="step-1-add-twitter-to-a-blank-phone-app"></a>Paso 1: Adición de Twitter a una aplicación de teléfono en blanco

1. En PowerApps Studio, seleccione **archivo** > **New**.
1. En el icono **Aplicación vacía**, seleccione **Diseño de teléfono**.
1. En la pestaña **Vista**, seleccione **Orígenes de datos**.
1. En el **datos** panel, seleccione **agregar origen de datos**.
1. Seleccione **nueva conexión** > **Twitter** > **crear**.
1. Escriba sus credenciales, crear la conexión y, a continuación, cierre el **datos** panel.

### <a name="step-2-collect-existing-tweets"></a>Paso 2: Recopilar tweets existentes

1. En el **vista de árbol** panel, seleccione **aplicación**y, a continuación, establezca su **OnStart** propiedad en esta fórmula:

    ```powerapps-comma
    If( Connection.Connected;
        ClearCollect( LocalTweets; Twitter.SearchTweet( "PowerApps"; {maxResults: 10} ) );;
            Set( statusText; "Online data" );
        LoadData( LocalTweets; "LocalTweets"; true );;
            Set( statusText; "Local data" )
    );;
    SaveData( LocalTweets; "LocalTweets" );;
    ```

    > [!div class="mx-imgBorder"]
    > ![Fórmula para cargar tweets](./media/offline-apps/load-tweets.png)

1. En el **vista de árbol** panel, seleccione el menú de puntos suspensivos de la **aplicación** objeto y, a continuación, seleccione **ejecutar OnStart** para ejecutar esa fórmula.

    > [!div class="mx-imgBorder"]
    > ![Ejecute la fórmula para cargar tweets](./media/offline-apps/load-tweets-run.png)

    > [!NOTE]
    > El **LoadData** y **SaveData** funciones podrían mostrar un error en PowerApps Studio, ya que los exploradores no las admiten. Sin embargo, realizará con normalidad después de implementar esta aplicación en un dispositivo.

Esta fórmula comprueba si el dispositivo está en línea:

- Si el dispositivo está en línea, la fórmula de carga hasta 10 tweets con el término de búsqueda "PowerApps" en un **LocalTweets** colección.
- Si el dispositivo está sin conexión, la fórmula carga la memoria caché local desde un archivo denominado "LocalTweets" Si está disponible.

### <a name="step-3-show-tweets-in-a-gallery"></a>Paso 3: Mostrar los tweets en una galería

1. En el **insertar** ficha, seleccione **galería** > **altura flexible en blanco**.

1. Establecer el **elementos** propiedad de la [ **galería** ](controls/control-gallery.md) control `LocalTweets`.

1. En la plantilla de la galería, agregue tres [ **etiqueta** ](controls/control-text-box.md) controles y establezca el **texto** propiedad de cada etiqueta en uno de estos valores:

    - `ThisItem.UserDetails.FullName & " (@" & ThisItem.UserDetails.UserName & ")"`
    - `Text(DateTimeValue(ThisItem.CreatedAtIso); DateTimeFormat.ShortDateTime)`
    - `ThisItem.TweetText`

1. Poner el texto en la última etiqueta en negrita para que la galería es similar a este ejemplo.

    > [!div class="mx-imgBorder"]
    > ![Galería que muestra los tweets de ejemplo](./media/offline-apps/tweet-gallery.png)

### <a name="step-4-show-connection-status"></a>Paso 4: Mostrar el estado de conexión

1. En la galería, insertar una etiqueta y, a continuación, establezca su **Color** propiedad **rojo**.

1. Establezca la etiqueta más reciente **texto** propiedad en esta fórmula:

    `If( Connection.Connected; "Connected"; "Offline" )`

Esta fórmula determina si el dispositivo está en línea. Si es así, la etiqueta muestra **conectado**; en caso contrario, muestra **Offline**.

### <a name="step-5-add-a-box-to-compose-tweets"></a>Paso 5: Agregue un cuadro para redactar tweets

1. En la etiqueta de estado de la conexión, inserte un [ **entrada de texto** ](controls/control-text-input.md) controlar y cámbiele el nombre **NewTweetTextInput**.

1. Establezca el cuadro de entrada de texto **predeterminado** propiedad `""`.

    > [!div class="mx-imgBorder"]
    > ![Galería de la información de estado y el cuadro de texto](./media/offline-apps/status-input.png)

### <a name="step-6-add-a-button-to-post-the-tweet"></a>Paso 6: Agregue un botón para enviar el tweet

1. En el cuadro de entrada de texto, agregue un **botón** y establezca su **texto** este valor para propiedad:

    `"Tweet"`

1. Establezca el botón **OnSelect** propiedad en esta fórmula:

    ```powerapps-comma
    If( Connection.Connected;
        Twitter.Tweet( ""; {tweetText: NewTweetTextInput.Text} );
        Collect( LocalTweetsToPost; {tweetText: NewTweetTextInput.Text} );;
            SaveData( LocalTweetsToPost; "LocalTweetsToPost" )
    );;
    Reset( NewTweetTextInput );;
    ```  

1. En el **OnStart** propiedad para el **aplicación**, agregue una línea al final de la fórmula:

    ```powerapps-comma
    If( Connection.Connected;
        ClearCollect( LocalTweets; Twitter.SearchTweet( "PowerApps"; {maxResults: 100} ) );;
            Set( statusText; "Online data" );
        LoadData( LocalTweets; "LocalTweets"; true );;
            Set( statusText; "Local data" )
    );;
    SaveData( LocalTweets; "LocalTweets" );;
    LoadData( LocalTweetsToPost; "LocalTweetsToPost"; true );;  // added line
    ```

    > [!div class="mx-imgBorder"]
    > ![Ejecute la fórmula para cargar tweets con la línea de marca de comentario](./media/offline-apps/load-tweets-save.png)

Esta fórmula determina si el dispositivo está en línea:

- Si el dispositivo está en línea, envía el tweet inmediatamente.
- Si el dispositivo está desconectado, captura el tweet en un **LocalTweetsToPost** colección y lo guarda en el dispositivo.

A continuación, la fórmula restablece el texto en el cuadro de entrada de texto.

### <a name="step-7-check-for-new-tweets"></a>Paso 7: Busque nuevos tweets

1. En el lado derecho del botón, agregue un **temporizador** control.

    > [!div class="mx-imgBorder"]
    > ![Aplicaciones finales](./media/offline-apps/final-app.png)

1. Establecer el temporizador **duración** propiedad **300000**.

1. Establecer el temporizador **AutoStart** y **repita** propiedades a **true**.

1. Establecer el temporizador **OnTimerEnd** en esta fórmula:

    ```powerapps-comma
    If( Connection.Connected;
        ForAll( LocalTweetsToPost; Twitter.Tweet( ""; {tweetText: tweetText} ) );;
        Clear( LocalTweetsToPost );;
        ClearCollect( LocalTweets; Twitter.SearchTweet( "PowerApps"; {maxResults: 10} ) );;
        SaveData( LocalTweets; "LocalTweets" );;
   )
    ```

Esta fórmula determina si el dispositivo está en línea. Si es así, la aplicación envía los tweets todos los elementos de la **LocalTweetsToPost** colección y, a continuación, borra la colección.

## <a name="test-the-app"></a>Probar la aplicación

1. Abra la aplicación en un dispositivo móvil que está conectado a Internet.

    Tweets existentes aparecen en la galería y se muestra el estado **conectado**.

1. Desconectar el dispositivo de Internet mediante la habilitación del modo avión del dispositivo y deshabilitación de wi-fi.

    La etiqueta de estado muestra que la aplicación está **Offline**.

1. Mientras el dispositivo está sin conexión, escribir un tweet que incluya **PowerApps**y, a continuación, seleccione el **Tweet** botón.

    El tweet se almacena localmente en el **LocalTweetsToPost** colección.

1. Volver a conectar el dispositivo a Internet mediante la deshabilitación del modo avión del dispositivo y habilitar wi-fi.

    Dentro de cinco minutos, la aplicación envía el tweet, que aparece en la galería.

Esperamos que este artículo le haya proporcionado una idea de las funcionalidades que tiene PowerApps para la creación de aplicaciones sin conexión. Como siempre, proporcione sus comentarios en nuestro [foro](https://powerusers.microsoft.com/t5/PowerApps-Forum/bd-p/PowerAppsForum1) y comparta sus ejemplos de aplicaciones sin conexión en el [Blog de la Comunidad de PowerApps](https://powerusers.microsoft.com/t5/PowerApps-Community-Blog/bg-p/PowerAppsBlog).