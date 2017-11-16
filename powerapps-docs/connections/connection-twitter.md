---
title: "Introducción a la conexión de Twitter | Microsoft Docs"
description: "Consulte como conectar a Twitter a través de algunos ejemplos paso a paso y examine todas las funciones."
services: 
suite: powerapps
documentationcenter: 
author: archnair
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 07/12/2017
ms.author: archanan
ms.openlocfilehash: f99c293184a33ea204f21462badb5e6eb498ee40
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="connect-to-twitter-from-powerapps"></a>Conectar al Twitter desde PowerApps
![Twitter](./media/connection-twitter/twittericon.png)

Twitter le permite enviar tweets y obtener tweets, cronologías, amigos y seguidores desde su cuenta de Twitter.

Puede mostrar esta información en una etiqueta en la aplicación. Por ejemplo, puede agregar un cuadro de texto de entrada, pedir al usuario que escriba en algún tweet y, después, agregar un botón que "publique" el tweet. Puede usar métodos similares para obtener o buscar un tweet y mostrar el texto de un control en un control de galería o etiqueta en la aplicación.

En este tema se muestra cómo utilizar la conexión de Twitter, cómo usar la conexión de Twitter en una aplicación y cómo enumerar las funciones disponibles.

&nbsp;

[!INCLUDE [connection-requirements](../../includes/connection-requirements.md)]

## <a name="connect-to-twitter"></a>Conexión a Twitter
1. Abra PowerApps, seleccione **Nuevo** y cree una **aplicación vacía**. Elija el diseño de teléfono o tableta. El diseño de tableta le ofrece más área de trabajo:  
   
   ![Abra una aplicación en blanco](./media/connection-twitter/blank-app.png)
2. En el panel derecho, pulse o haga clic en la pestaña **Datos** y, después, en **Agregar origen de datos**.
3. Seleccione **Conexión nueva** y, después, **Twitter**:  
   
    ![Conexión a Twitter](./media/connection-twitter/addconnection.png)
   
    ![Conexión a Twitter](./media/connection-twitter/add-twitter.png)
4. Seleccione **Conectar**, escriba sus credenciales de inicio de sesión de Twitter y seleccione **Autorizar aplicación**.
5. Seleccione **Agregar origen de datos**. La conexión aparecerá bajo **Orígenes de datos**:  
    ![Cerrar el panel de opciones](./media/connection-twitter/twitterdatasource.png)

La conexión de Twitter se ha creado y se ha agregado a la aplicación. Ahora, está lista para utilizarse.

## <a name="use-the-twitter-connection-in-your-app"></a>Usar la conexión de Twitter en la aplicación
### <a name="show-a-timeline"></a>Mostrar una cronología
1. En el menú **Insertar**, seleccione **Galería** y agregue cualquiera de las galerías **con texto**.
2. Vamos a mostrar algunas cronologías:  
   
   * Para mostrar la cronología del usuario actual, establezca la propiedad **[Elementos](../controls/properties-core.md)** de la galería en las fórmulas siguientes:
     
       `Twitter.HomeTimeline().TweetText`  
       `Twitter.HomeTimeline({maxResults:3}).TweetText`  
   * Para mostrar la cronología de otro usuario, establezca la propiedad **[Elementos](../controls/properties-core.md)** de la galería en las fórmulas siguientes:  
     
       `Twitter.UserTimeline( *TwitterHandle* ).TweetText`
     
       Introduzca un identificador de Twitter con dobles comillas o un valor equivalente. Por ejemplo, escriba `"satyanadella"` o `"powerapps"` directamente en la expresión de la fórmula.
   * Agregue un control de entrada de texto denominado **Tweep** y establezca su propiedad predeterminada en `Tweep.Text`. En el cuadro de texto Tweep, escriba un identificador de Twitter como `satyanadella` (sin las comillas y sin el símbolo @).
     
       En el control de galería, establezca la propiedad Elementos en la fórmula siguiente:  
     
       `Twitter.UserTimeline(Tweep.Text, {maxResults:5}).TweetText`
     
       El control de galería muestra automáticamente los tweets del identificador de Twitter que ha escrito.
     
     **Sugerencia** Algunas de estas fórmulas utilizan el argumento **maxResults** para mostrar el número *x* de tweets más recientes en una cronología.
3. Establezca la propiedad **Elementos** de la galería en `Twitter.HomeTimeline()`.
   
    Con la galería seleccionada, el panel derecho muestra opciones para esa galería.
4. Seleccione **TweetText** en la primera lista, seleccione **TweetedBy** en la segunda lista y seleccione **CreatedAt** en la tercera lista.
   
    La galería ahora muestra los valores de las propiedades que haya elegido.

### <a name="show-followers"></a>Mostrar seguidores
1. Con una galería **Con texto**, vamos a mostrar algunos seguidores:  
   
   * Para mostrar los seguidores del usuario actual, establezca la propiedad **[Elementos](../controls/properties-core.md)** de la galería en la siguiente fórmula:  
     
       `Twitter.MyFollowers()`  
       `Twitter.MyFollowers({maxResults:3})`
   * Para mostrar los seguidores de otro usuario, establezca la propiedad **[Elementos](../controls/properties-core.md)** de la galería en la siguiente fórmula:  
     
       `Twitter.Followers( *TwitterHandle* )`
     
       Introduzca un identificador de Twitter con dobles comillas o un valor equivalente. Por ejemplo, escriba `"satyanadella"` o `"powerapps"` directamente en la expresión de la fórmula.
   * Agregue un control de entrada de texto denominado **Tweep** y establezca su propiedad predeterminada en `Tweep.Text`. En el cuadro de texto Tweep, escriba un identificador de Twitter como `satyanadella` (sin las comillas y sin el símbolo @).
     
       En el control de galería, establezca la propiedad Elementos en la fórmula siguiente:  
     
       `Twitter.Followers(Tweep.Text, {maxResults:5})`
     
       El control de galería muestra automáticamente quién está siguiendo el identificador de Twitter que ha escrito.
     
     **Sugerencia** Algunas de estas fórmulas utilizan el argumento **maxResults** para mostrar el número *x* de tweets más recientes en una cronología.
2. Establezca la propiedad **Elementos** de la galería en `Twitter.MyFollowers()`.
   
    Con la galería seleccionada, el panel derecho muestra opciones para esa galería.
3. Seleccione **NombreUsuario** en la segunda lista y **NombreCompleto** en la tercera.
   
    La galería ahora muestra los valores de las propiedades que haya elegido.

### <a name="show-followed-users"></a>Mostrar usuarios seguidos
1. Con una galería **Con texto**, vamos a mostrar algunos usuarios seguidos:  
   
   * Para mostrar los usuarios a los que está siguiendo el usuario actual, establezca la propiedad **[Elementos](../controls/properties-core.md)** de la galería en la siguiente fórmula:  
     
       `Twitter.MyFollowing()`  
       `Twitter.MyFollowing({maxResults:3})`
   * Para mostrar los usuarios a los que está siguiendo otro usuario, establezca la propiedad **[Elementos](../controls/properties-core.md)** de la galería en la siguiente fórmula:
     
       `Twitter.Following( *TwitterHandle* )`
     
       Introduzca un identificador de Twitter con dobles comillas o un valor equivalente. Por ejemplo, escriba `"satyanadella"` o `"powerapps"` directamente en la expresión de la fórmula.
   * Agregue un control de entrada de texto denominado **Tweep** y establezca su propiedad predeterminada en `Tweep.Text`. En el cuadro de texto Tweep, escriba un identificador de Twitter como `satyanadella` (sin las comillas y sin el símbolo @).
     
       En el control de galería, establezca la propiedad Elementos en la fórmula siguiente:  
     
       `Twitter.Following(Tweep.Text, {maxResults:5})`
     
       El control de galería muestra automáticamente los otros identificadores que está siguiendo.
     
     Con la galería seleccionada, el panel derecho muestra opciones para esa galería.
2. Seleccione **Descripción** en la lista **Cuerpo1**, **NombreUsuario** en la lista **Título1** y **NombreCompleto** en la lista **Subtítulo1**.
   
    La galería ahora muestra los valores de las propiedades que haya elegido.

### <a name="show-information-about-a-user"></a>Mostrar información sobre un usuario
Agregue una etiqueta y luego establezca su propiedad **[Texto](../controls/properties-core.md)** en una de estas fórmulas:  

* `twitter.User( *TwitterHandle* ).Description`
* `twitter.User( *TwitterHandle* ).FullName`
* `twitter.User( *TwitterHandle* ).Location`
* `twitter.User( *TwitterHandle* ).UserName`
* `twitter.User( *TwitterHandle* ).FollowersCount`
* `twitter.User( *TwitterHandle* ).FriendsCount`
* `twitter.User( *TwitterHandle* ).Id`
* `twitter.User( *TwitterHandle* ).StatusesCount`

Introduzca un identificador de Twitter con dobles comillas o un valor equivalente. Por ejemplo, escriba `"satyanadella"` o `"powerapps"` directamente en la expresión de la fórmula.

O bien, puede utilizar un control de texto de entrada para escribir un identificador de Twitter, tal y como se dispone a lo largo de este tema.

### <a name="search-tweets"></a>Buscar tweets
1. Agregue una galería **Con texto** y establezca su propiedad **[Elementos](../controls/properties-core.md)** en la siguiente fórmula:  
   
    `Twitter.SearchTweet( *SearchTerm* ).TweetText`
   
    Escriba un *término de búsqueda* entre comillas dobles o haciendo referencia a un valor equivalente. Por ejemplo, escriba `"PowerApps"` o `"microsoft"` directamente en la fórmula.
   
    O bien, puede utilizar un control **Entrada de texto** para escribir un término de búsqueda, tal y como se dispone a lo largo de este tema.
   
    **Sugerencia** Muestre los cinco primeros resultados mediante maxResults:  
   
    `Twitter.SearchTweet(SearchTerm.Text, {maxResults:5}).TweetText`
2. Establezca la propiedad **Elementos** de la galería en `Twitter.SearchTweet(SearchTerm.Text, {maxResults:5})`.
   
    Con la galería seleccionada, el panel derecho muestra opciones para esa galería.
3. Seleccione **TweetText** en la primera lista, **TweetedBy** en la segunda lista y **CreatedAt** en la tercera lista.
   
    La galería ahora muestra los valores de las propiedades que haya elegido.

### <a name="send-a-tweet"></a>Enviar un tweet
1. Agregue un control de entrada de texto y cambie su nombre a **MyTweet**.
2. Agregue un botón y establezca su propiedad **[AlSeleccionar](../controls/properties-core.md)** en esta fórmula:  
    `Twitter.Tweet({tweetText: MyTweet.Text})`
3. Presione F5 o seleccione el botón Vista previa (![](./media/connection-twitter/preview.png)). Escriba algún texto en **MyTweet** y seleccione el botón para enviar en un tweet el texto que ha escrito.
4. Presione Esc para volver al área de trabajo predeterminada.

## <a name="view-the-available-functions"></a>Visualización de las funciones disponibles
Esta conexión incluye las siguientes funciones:

| Nombre de la función | Descripción |
| --- | --- |
| [UserTimeline](connection-twitter.md#usertimeline) |Recupera una colección de los tweets más recientes enviados por el usuario especificado. |
| [HomeTimeline](connection-twitter.md#hometimeline) |Recupera los tweets y retweets más recientes enviados por mí y mis seguidores. |
| [SearchTweet](connection-twitter.md#searchtweet) |Recupera una colección de tweets pertinentes que coinciden con una consulta especificada. |
| [Seguidores](connection-twitter.md#followers) |Recupera los usuarios que siguen al usuario especificado. |
| [MyFollowers](connection-twitter.md#myfollowers) |Recupera los usuarios que me siguen. |
| [Siguiendo](connection-twitter.md#following) |Recupera los usuarios a los que está siguiendo el usuario especificado. |
| [Siguiendo](connection-twitter.md#myfollowing) |Recupera los usuarios a los que estoy siguiendo. |
| [Usuario](connection-twitter.md#user) |Recupera los detalles sobre el usuario especificado (ejemplo: nombre de usuario, descripción, número de seguidores, etc.). |
| [Tweet](connection-twitter.md#tweet) |El tweet |
| [OnNewTweet](connection-twitter.md#onnewtweet) |Desencadena un flujo de trabajo cuando se envía un nuevo tweet que coincide con la consulta de búsqueda. |

### <a name="usertimeline"></a>UserTimeline
Obtener cronología del usuario: recupera una colección de los tweets más recientes enviados por el usuario especificado.

#### <a name="input-properties"></a>Propiedades de entrada
| Nombre | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| NombreUsuario |string |yes |Identificador de Twitter |
| maxResults |integer |no |Número máximo de tweets que se van a recuperar, por ejemplo, {maxResults:5} |

#### <a name="output-properties"></a>Propiedades de salida
| Nombre de la propiedad | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| TweetText |string |Sí | |
| TweetId |string |No | |
| CreatedAt |string |No | |
| RetweetCount |integer |Sí | |
| TweetedBy |string |Sí | |
| MediaUrls |array |No | |

### <a name="hometimeline"></a>HomeTimeline
Obtener la cronología de inicio: recupera los tweets y retweets más recientes enviados por mí y mis seguidores.

#### <a name="input-properties"></a>Propiedades de entrada
| Nombre | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| maxResults |integer |no |Número máximo de tweets que se van a recuperar, por ejemplo, {maxResults:5} |

#### <a name="output-properties"></a>Propiedades de salida
| Nombre de la propiedad | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| TweetText |string |Sí | |
| TweetId |string |No | |
| CreatedAt |string |No | |
| RetweetCount |integer |Sí | |
| TweetedBy |string |Sí | |
| MediaUrls |array |No | |

### <a name="searchtweet"></a>SearchTweet
Buscar tweet: recupera una colección de tweets pertinentes que coinciden con una consulta especificada.

#### <a name="input-properties"></a>Propiedades de entrada
| Nombre | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| searchQuery |string |yes |Texto de consulta (puede usar cualquiera de los operadores de consulta admitidos por Twitter: http://www.twitter.com/search) |
| maxResults |integer |no |Número máximo de tweets que se van a recuperar, por ejemplo, {maxResults:5} |

#### <a name="output-properties"></a>Propiedades de salida
| Nombre de la propiedad | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| TweetText |string |Sí | |
| TweetId |string |No | |
| CreatedAt |string |No | |
| RetweetCount |integer |Sí | |
| TweetedBy |string |Sí | |
| MediaUrls |array |No | |

### <a name="followers"></a>Seguidores
Obtener seguidores: recupera los usuarios que siguen al usuario especificado.

#### <a name="input-properties"></a>Propiedades de entrada
| Nombre | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| NombreUsuario |string |yes |Identificador de Twitter del usuario |
| maxResults |integer |no |Número máximo de usuarios que se van a recuperar, por ejemplo, {maxResults:5} |

#### <a name="output-properties"></a>Propiedades de salida
| Nombre de la propiedad | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| FullName |string |Sí | |
| Ubicación |string |Sí | |
| Identificador |integer |No | |
| NombreUsuario |string |Sí | |
| FollowersCount |integer |No | |
| Descripción |string |Sí | |
| StatusesCount |integer |No | |
| FriendsCount |integer |No | |

### <a name="myfollowers"></a>MyFollowers
Obtener mis seguidores: recupera los usuarios que me siguen.

#### <a name="input-properties"></a>Propiedades de entrada
| Nombre | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| maxResults |integer |no |Número máximo de usuarios que se van a recuperar, por ejemplo, {maxResults:5} |

#### <a name="output-properties"></a>Propiedades de salida
| Nombre de la propiedad | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| FullName |string |Sí | |
| Ubicación |string |Sí | |
| Identificador |integer |No | |
| NombreUsuario |string |Sí | |
| FollowersCount |integer |No | |
| Descripción |string |Sí | |
| StatusesCount |integer |No | |
| FriendsCount |integer |No | |

### <a name="following"></a>Siguiendo
Obtener seguimiento: recupera los usuarios a los que está siguiendo el usuario especificado.

#### <a name="input-properties"></a>Propiedades de entrada
| Nombre | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| NombreUsuario |string |yes |Identificador de Twitter del usuario |
| maxResults |integer |no |Número máximo de usuarios que se van a recuperar, por ejemplo, {maxResults:5} |

#### <a name="output-properties"></a>Propiedades de salida
| Nombre de la propiedad | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| FullName |string |Sí | |
| Ubicación |string |Sí | |
| Identificador |integer |No | |
| NombreUsuario |string |Sí | |
| FollowersCount |integer |No | |
| Descripción |string |Sí | |
| StatusesCount |integer |No | |
| FriendsCount |integer |No | |

### <a name="myfollowing"></a>Siguiendo
Obtener mi seguimiento: recupera los usuarios a los que estoy siguiendo.

#### <a name="input-properties"></a>Propiedades de entrada
| Nombre | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| maxResults |integer |no |Número máximo de usuarios que se van a recuperar, por ejemplo, {maxResults:5} |

#### <a name="output-properties"></a>Propiedades de salida
| Nombre de la propiedad | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| FullName |string |Sí | |
| Ubicación |string |Sí | |
| Identificador |integer |No | |
| NombreUsuario |string |Sí | |
| FollowersCount |integer |No | |
| Descripción |string |Sí | |
| StatusesCount |integer |No | |
| FriendsCount |integer |No | |

### <a name="user"></a>Usuario
Obtener usuario: recupera los detalles sobre el usuario especificado (ejemplo: nombre de usuario, descripción, número de seguidores, etc.).

#### <a name="input-properties"></a>Propiedades de entrada
| Nombre | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| NombreUsuario |string |yes |Identificador de Twitter del usuario |

#### <a name="output-properties"></a>Propiedades de salida
| Nombre de la propiedad | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| FullName |string |Sí | |
| Ubicación |string |Sí | |
| Identificador |integer |No | |
| NombreUsuario |string |Sí | |
| FollowersCount |integer |No | |
| Descripción |string |Sí | |
| StatusesCount |integer |No | |
| FriendsCount |integer |No | |

### <a name="tweet"></a>El tweet
Enviar un nuevo tweet: Tweet

#### <a name="input-properties"></a>Propiedades de entrada
| Nombre | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| tweetText |string |no |Texto que se va a enviar, por ejemplo, {tweetText: "hola"} |
| cuerpo |string |no |Elementos multimedia que se van a publicar |

#### <a name="output-properties"></a>Propiedades de salida
| Nombre de la propiedad | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| TweetId |string |Sí | |

### <a name="onnewtweet"></a>OnNewTweet
Cuando aparece un nuevo tweet: desencadena un flujo de trabajo cuando se envía un nuevo tweet que coincide con la consulta de búsqueda.

#### <a name="input-properties"></a>Propiedades de entrada
| Nombre | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| searchQuery |string |yes |Texto de consulta (puede usar cualquiera de los operadores de consulta admitidos por Twitter: http://www.twitter.com/search) |

#### <a name="output-properties"></a>Propiedades de salida
| Nombre de la propiedad | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| value |array |No | |

## <a name="helpful-links"></a>Vínculos útiles
Consulte todas las [conexiones disponibles](../connections-list.md).  
Aprenda a [agregar conexiones](../add-manage-connections.md) a sus aplicaciones.

