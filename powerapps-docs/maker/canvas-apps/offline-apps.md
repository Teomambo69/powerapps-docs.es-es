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
ms.openlocfilehash: f9922c64769aeacd9b9b65cc3039b091ac7fe353
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61538412"
ms.PowerAppsDecimalTransform: true
---
# <a name="develop-offline-capable-canvas-apps"></a>Desarrollo de aplicaciones de lienzo que puedan ejecutarse sin conexión

Uno de los escenarios más comunes a los que se enfrenta como desarrollador de aplicaciones móviles es posibilitar que sus usuarios puedan ser productivos cuando no hay conectividad o bien esta es limitada. PowerApps tiene un conjunto de características y comportamientos que le ayudarán a desarrollar aplicaciones de lienzo que puedan ejecutarse sin conexión. Podrá:

* Iniciar PowerApps Mobile cuando esté sin conexión.
* Ejecutar aplicaciones que desarrolle cuando esté sin conexión.
* Determinar si una aplicación está sin conexión, en línea o en una conexión de uso medido mediante el objeto de señal [conexión](../canvas-apps/functions/signals.md#connection).
* Usar [colecciones](../canvas-apps/create-update-collection.md) y aprovechar funciones como [LoadData y SaveData](../canvas-apps/functions/function-savedata-loaddata.md) para el almacenamiento de datos básico cuando esté sin conexión.

## <a name="limitations"></a>Limitaciones

**LoadData** y **SaveData** se combinan para formar un mecanismo sencillo para almacenar pequeñas cantidades de datos en un dispositivo local. Mediante el uso de estas funciones, puede agregar capacidades sin conexión sencillas a la aplicación.  

Estas funciones están limitadas por la cantidad de memoria de la aplicación disponible, ya que operan en una colección en memoria. Memoria disponible puede variar en función del dispositivo, el sistema operativo, la memoria que usa PowerApps Mobile y la complejidad de la aplicación en cuanto a las pantallas y controles. Si almacena más de unos cuantos megabytes de datos, pruebe la aplicación con los escenarios esperados en los dispositivos en el que se espera que se ejecute. Por lo general debería tener entre 30 y 70 MB de memoria disponible.  

Las funciones también no resuelven automáticamente los conflictos de combinación cuando un dispositivo se vuelve a la conectividad de sin conexión: configuración en los datos que se guardan y cómo controlar la reconexión es hasta el fabricante al escribir expresiones.

Estamos trabajando para ampliar las funcionalidades para escenarios sin conexión. Permanezca atento aquí y en el [blog de PowerApps](https://powerapps.microsoft.com/blog/) para ver las actualizaciones cuando están disponibles.

## <a name="how-to-build-offline-capable-apps"></a>Cómo crear aplicaciones que puedan ejecutarse sin conexión

Lo primero que hay que pensar en escenarios sin conexión es cómo trabajan las aplicaciones con los datos. Las aplicaciones en PowerApps tienen acceso a los datos principalmente a través de un conjunto de [conectores](../canvas-apps/connections-list.md) que proporciona la plataforma, como SharePoint, Office 365 y Common Data Service. También puede crear conectores personalizados que permiten a las aplicaciones tener acceso a cualquier servicio que proporcione un punto de conexión REST. Podría tratarse de una API web o un servicio como Azure Functions. Todos estos conectores usan HTTPS a través de Internet, lo que significa que los usuarios deben estar en línea para acceder a los datos y otras funcionalidades que ofrece un servicio.

![Aplicación de PowerApps con conectores](./media/offline-apps/online-app.png)

### <a name="handling-offline-data"></a>Administrar datos sin conexión
Uno de los aspectos más interesantes de PowerApps es su conjunto de funcionalidades y fórmulas que le permiten filtrar, buscar y ordenar, agregar y manipular los datos de una manera coherente independientemente del origen de datos. Estos orígenes varían desde colecciones en memoria en la aplicación a listas de SharePoint, bases de datos SQL o Common Data Service. Esta coherencia permite redirigir fácilmente una aplicación para que use un back-end diferente. Lo más importante es que, en este caso, también permite usar colecciones locales para la administración de datos sin realizar apenas cambios en la lógica de la aplicación. De hecho, las colecciones locales son el mecanismo principal para administrar datos sin conexión.

## <a name="building-an-offline-twitter-app"></a>Crear una aplicación de Twitter sin conexión
Para centrarnos en los aspectos del desarrollo de aplicaciones sin conexión, mostraremos un sencillo escenario centrado en Twitter. Vamos a crear una aplicación que permite leer entradas de Twitter y enviar tweets mientras está sin conexión. Cuando la aplicación se conecta, la aplicación envía los tweets y vuelve a cargar los datos locales.

De forma general, la aplicación hace lo siguiente:

1. En el inicio de la aplicación (en función de la propiedad **OnVisible** de la primera pantalla):

   * Si el dispositivo está en línea, se accede directamente al conector de Twitter para recuperar los datos y se rellena una colección con esos datos.
   * Si el dispositivo está sin conexión, se cargan los datos desde un archivo de caché local mediante [LoadData](../canvas-apps/functions/function-savedata-loaddata.md).
   * Se permite al usuario enviar tweets; si está en línea, se envían directamente a Twitter y se actualiza la memoria caché local.
2. Cada 5 minutos, en está en línea:

   * Se envían los tweets que tenemos en la memoria caché local.
   * Se actualiza la memoria caché local y se guarda con [SaveData](../canvas-apps/functions/function-savedata-loaddata.md).

### <a name="step-1-create-a-new-phone-app"></a>Paso 1: Crear una nueva aplicación de teléfono
1. Abra PowerApps Studio.
2. Pulse o haga clic en **Nuevo** > **Aplicación en blanco** > **Diseño de teléfono**.

    ![Aplicación en blanco, diseño de teléfono](./media/offline-apps/blank-app.png)

### <a name="step-2-add-a-twitter-connection"></a>Paso 2: Agregar una conexión de Twitter

1. Pulse o haga clic en **Contenido** > **Orígenes de datos**; a continuación, elija **Agregar origen de datos** en el panel **Orígenes de datos**.

2. Pulse o haga clic en **Nueva conexión**, seleccione **Twitter** y pulse o haga clic en **Crear**.

3. Escriba sus credenciales y cree la conexión.

    ![Agregar una conexión de Twitter](./media/offline-apps/twitter-connection.png)

### <a name="step-3-load-tweets-into-a-localtweets-collection-on-app-startup"></a>Paso 3: Cargar tweets en la colección LocalTweets en el inicio de la aplicación
Seleccione la propiedad **AlEstarVisible** de **Pantalla1** en la aplicación y copie en ella la siguiente fórmula:

```powerapps-comma
If( Connection.Connected;
    ClearCollect( LocalTweets; Twitter.SearchTweet( "PowerApps"; {maxResults: 100} ) );;
        UpdateContext( {statusText: "Online data"} );
    LoadData(LocalTweets; "Tweets"; true);;
        UpdateContext( {statusText: "Local data"} )
);;
LoadData( LocalTweetsToPost; "LocalTweets"; true );;
SaveData( LocalTweets; "Tweets" )
```

![Fórmula para cargar tweets](./media/offline-apps/load-tweets.png)

Esta fórmula comprueba si el dispositivo está en línea:

* Si el dispositivo está en línea, se cargan en la colección **LocalTweets** hasta 100 tweets con el término de búsqueda "PowerApps".
* Si el dispositivo está sin conexión, se carga la memoria caché local desde un archivo denominado "Tweets", si está disponible.

### <a name="step-4-add-a-gallery-and-bind-it-to-the-localtweets-collection"></a>Paso 4: Agregue una galería y enlazarla a la colección LocalTweets

1. Inserta una nueva galería de altura flexible: **Insertar** > **galería** > **altura flexible en blanco**.

2. Establezca la propiedad **Items** en **LocalTweets**.

3. Agregue cuatro controles **Label** para mostrar los datos de cada tweet y establezca sus propiedades **Texto** en:
   * **ThisItem.TweetText**
   * **ThisItem.UserDetails.FullName & " \@" & ThisItem.UserDetails.UserName**
   * **"RT: " & ThisItem.RetweetCount**
   * **Text(DateTimeValue(ThisItem.CreatedAtIso); DateTimeFormat.ShortDateTime)**
4. Agregue un control **Imagen** y establezca la propiedad **Image** en **ThisItem.UserDetails.ProfileImageUrl**.

### <a name="step-5-add-a-connection-status-label"></a>Paso 5: Agregar una etiqueta de estado de conexión
Inserte un nuevo control **Label** y establezca su propiedad **Texto** en la fórmula siguiente:

```If( Connection.Connected; "Connected"; "Offline" )```

Esta fórmula comprueba si el dispositivo está en línea. Si lo está, el texto de la etiqueta es "Conectado", en caso contrario es "Sin conexión".

### <a name="step-6-add-a-text-input-to-compose-new-tweets"></a>Paso 6: Agregar una entrada de texto para redactar nuevos tweets

1. Inserte un nuevo control **Entrada de texto** denominado "NewTweetTextInput".

2. Establezca la propiedad **Reset** de la entrada de texto a **resetNewTweet**.

### <a name="step-7-add-a-button-to-post-the-tweet"></a>Paso 7: Agregue un botón para enviar el tweet
1. Agregue un control **Botón** y establezca la propiedad **Texto** en "Tweet".
2. Establezca la propiedad **AlSeleccionar** en la fórmula siguiente:

    ```powerapps-comma
    If( Connection.Connected;
        Twitter.Tweet( ""; {tweetText: NewTweetTextInput.Text} );
        Collect( LocalTweetsToPost; {tweetText: NewTweetTextInput.Text} );;
            SaveData( LocalTweetsToPost; "LocalTweetsToPost" )
    );;
    UpdateContext( {resetNewTweet: true} );;
    UpdateContext( {resetNewTweet: false} )
    ```  

Esta fórmula comprueba si el dispositivo está en línea:

* Si el dispositivo está en línea, envía el tweet inmediatamente.
* Si el dispositivo está sin conexión, captura el tweet en la colección **LocalTweetsToPost** y la guarda en la aplicación.

A continuación, la fórmula restablece el texto en el cuadro de texto.

### <a name="step-8-add-a-timer-to-check-for-tweets-every-five-minutes"></a>Paso 8: Agregar un temporizador para comprobar los tweets cada cinco minutos
Agregue un nuevo control **Temporizador**:

* Establezca la propiedad **Duration** en 300 000.

* Establezca la propiedad **AutoStart** en true.

* Establezca **OnTimerEnd** en la fórmula siguiente:

    ```powerapps-comma
    If( Connection.Connected;
        ForAll( LocalTweetsToPost; Twitter.Tweet( ""; {tweetText: tweetText} ) );;
        Clear( LocalTweetsToPost);;
        Collect( LocalTweetsToPost; {tweetText: NewTweetTextInput.Text} );;
        SaveData( LocalTweetsToPost; "LocalTweetsToPost" );;
        UpdateContext( {statusText: "Online data"} )
    )
    ```

Esta fórmula comprueba si el dispositivo está en línea. Si es así, la aplicación envía los tweets de todos los elementos de la colección **LocalTweetsToPost**. A continuación, borra la colección.

Ahora que la aplicación está terminada, comprobemos su aspecto antes de comenzar con las pruebas. A la izquierda, la aplicación está conectada; y a la derecha, está sin conexión, con un tweet listo para su envío cuando esté en línea nuevo.

![Aplicación finalizada con los modos en línea y sin conexión](./media/offline-apps/finished-app.png)

## <a name="testing-the-app"></a>Probar la aplicación
Para probar la aplicación, siga estos pasos:

1. Ejecute PowerApps en un dispositivo móvil que esté en línea. Debe ejecutar la aplicación estando en línea al menos una vez para que la aplicación pueda descargarse en el dispositivo.
2. Inicie la aplicación de Twitter.
3. Observe que se cargan los tweets y que muestra el estado **Conectado**.
4. Cierre PowerApps completamente.
5. Establezca el dispositivo en modo de avión para asegurarse de que está sin conexión.
6. Ejecute PowerApps. Ahora puede ejecutar la aplicación de Twitter sin conexión y tener acceso a cualquier otra aplicación que ya haya ejecutado en este dispositivo mientras estaba en línea (es decir, PowerApps oculta las aplicaciones que aún no se ha descargado en el dispositivo).
7. Vuelva a ejecutar la aplicación.
8. Observe que refleja correctamente el estado de conexión, con un estado de **Sin conexión**.
9. Escriba un nuevo tweet. Se almacenará localmente en la colección **LocalTweetsToPost**.
10. Salga del modo avión. Después de que se active el temporizador, la aplicación envía el tweet.

Esperamos que este artículo le haya proporcionado una idea de las funcionalidades que tiene PowerApps para la creación de aplicaciones sin conexión. Como siempre, proporcione sus comentarios en nuestro [foro](https://powerusers.microsoft.com/t5/PowerApps-Forum/bd-p/PowerAppsForum1) y comparta sus ejemplos de aplicaciones sin conexión en el [Blog de la Comunidad de PowerApps](https://powerusers.microsoft.com/t5/PowerApps-Community-Blog/bg-p/PowerAppsBlog).

